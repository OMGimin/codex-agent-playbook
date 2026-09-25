---
name: finishing-a-development-branch
description: Use when implementation is complete, all tests pass, and you need to decide how to integrate the work
---

# Finishing a Development Branch

## Overview

**Core principle:** Verify tests → Detect environment → Resolve authorized action → Execute within scope → Clean up only verified targets.

**Announce at start:** "I'm using the finishing-a-development-branch skill to complete this work."

## Step 1: Verify Tests

Run the project's full test suite (`npm test` / `cargo test` / `pytest` / `go test ./...`).

**If tests fail**, report the failures and stop — the menu comes after a green suite:

```
Tests failing (<N> failures). Must fix before completing:

[Show failures]
```

**If tests pass:** continue to Step 2.

## Step 2: Detect Environment

```bash
GIT_DIR=$(cd "$(git rev-parse --git-dir)" 2>/dev/null && pwd -P)
GIT_COMMON=$(cd "$(git rev-parse --git-common-dir)" 2>/dev/null && pwd -P)
# Capture now, while still inside the workspace — Step 5 changes directory
# before cleanup (Step 6) needs this value
WORKTREE_PATH=$(git rev-parse --show-toplevel)
```

This determines which menu to show and how cleanup works:

| State | Menu | Cleanup |
|-------|------|---------|
| `GIT_DIR == GIT_COMMON` (normal repo) | Standard 3 options | No worktree to clean up |
| `GIT_DIR != GIT_COMMON`, named branch | Standard 3 options | Provenance-based (see Step 6) |
| `GIT_DIR != GIT_COMMON`, detached HEAD | Reduced 2 options (no merge) | Externally managed — leave in place |

## Step 3: Determine Base Branch

Resolve the base branch only for an action that needs it, such as merging or choosing a PR target. Reuse an explicitly selected base for the same scope after checking current repository state. Do not ask for a base for push-only or keep-as-is requests. If the integration action is unspecified, offer Step 4's menu first and resolve only the selected action's required targets.

Use the task context and repository evidence to establish the intended base; a branch's upstream alone is not proof of its original base or intended PR target. If a required base remains unresolved, ask before merging or creating the PR. Verification of an already authorized target is not a new approval request.

## Step 4: Resolve the Authorized Action

Apply AGENTS.md approval reuse: if the user has already explicitly selected the action for the same repository, branch, remote/base, and scope, execute that action without another menu or confirmation. Recheck current state for material changes; ask only when a necessary target remains unresolved or the authorization no longer covers the action. A push-only request does not authorize creating a PR or merging. Do not infer integration approval from implementation approval. The exact `discard` confirmation below remains required for destruction.

Only when the integration action is unspecified, present the appropriate concise menu and wait for the user's choice.

**Normal repo and named-branch worktree — offer these 3 options:**

```
Implementation complete. What would you like to do?

1. Merge back to <base-branch> locally
2. Push and create a Pull Request
3. Keep the branch as-is (I'll handle it later)

Which option?
```

**Detached HEAD — offer these 2 options:**

```
Implementation complete. You're on a detached HEAD (externally managed workspace).

1. Push as new branch and create a Pull Request
2. Keep as-is (I'll handle it later)

Which option?
```

Keep these menu choices concise and use the user's language. Do not repeat a menu for an already authorized action. Discarding work is available only in response to an explicit discard request (see below), never as an inferred next step.

## Step 5: Execute Choice

### Option 1: Merge Locally

```bash
# Get main repo root for CWD safety
MAIN_ROOT=$(git -C "$(git rev-parse --git-common-dir)/.." rev-parse --show-toplevel)
cd "$MAIN_ROOT"

# Merge first — verify success before removing anything
git checkout <base-branch>
git pull
git merge <feature-branch>

# Verify tests on merged result
<test command>
```

If tests fail on the merged result: stop, leave the worktree and branch in
place, and investigate — nothing has been pushed, so the merge is local
and recoverable.

Once the merged result is green, apply Step 6. Delete only the authorized feature branch after it is fully merged and no preserved worktree has it checked out. If cleanup is withheld because ownership or authorization is unverified, preserve that worktree and its checked-out branch and report the remaining cleanup:

```bash
git branch -d <feature-branch>
```

### Option 2: Push and Create PR

```bash
git push -u origin <feature-branch>
# From a detached HEAD, name the new branch on the remote:
# git push origin HEAD:refs/heads/<new-branch>
```

Then create the pull/merge request against <base-branch> with the forge's
tooling — its CLI if one is available, or the creation URL most forges
print when you push — following the repo's PR template and conventions if
present, and report the URL to your human partner.

Keep the worktree — your human partner iterates on PR feedback there.

### Option 3: Keep As-Is

Report: "Keeping branch <name>. Worktree preserved at <path>."

### If your human partner asks to discard the work

This path exists only as a response to an explicit request to throw the
work away. Confirm first:

```
This will permanently delete:
- Branch <name>
- All commits: <commit-list>
- Worktree at <path>

Type 'discard' to confirm.
```

Wait for that exact confirmation. When it arrives:

```bash
MAIN_ROOT=$(git -C "$(git rev-parse --git-common-dir)/.." rev-parse --show-toplevel)
cd "$MAIN_ROOT"
```

Then apply Step 6 and force-delete only the exact confirmed branch. If the worktree must be preserved, do not force branch deletion past that constraint; report what remains:

```bash
git branch -D <feature-branch>
```

## Step 6: Cleanup Workspace

**Runs for Option 1 and confirmed discards.** Options 2 and 3 always
preserve the worktree. Both callers have already changed directory to the
main repo root — worktree removal must run from outside the worktree —
and use the `GIT_DIR`/`GIT_COMMON`/`WORKTREE_PATH` values captured in
Step 2, from before that directory change.

**If `GIT_DIR == GIT_COMMON`:** Normal repo, no worktree to clean up. Done.

**Verify provenance and scope before removal:** Match the task's creation record to the resolved absolute `WORKTREE_PATH`, repository/common Git directory, current branch or detached commit, and `git worktree list --porcelain`. Check current modified and untracked files with `git -C "$WORKTREE_PATH" status --porcelain -uall` before attempting removal. Ensure this exact worktree is within the authorized cleanup scope. Being under `.worktrees/` or `worktrees/` does not establish ownership.

For a manually created worktree whose creation by this task and cleanup authority are verified, remove only that exact target from outside its directory:

```bash
git worktree remove "$WORKTREE_PATH"
```

For a host-managed workspace, use its documented cleanup mechanism only if that exact action is authorized; otherwise preserve it. If provenance, registration, or cleanup authority is unknown or inconsistent, preserve the workspace and explain the unresolved cleanup. Do not prune unrelated registrations or delete other worktrees as incidental cleanup.

**If the pre-removal check finds modified/untracked files, or removal is refused** (`contains modified or untracked files`): the
worktree holds files that exist nowhere else — uncommitted plans, notes,
or scratch work. Never `--force` on your own initiative. Show your human
partner what is at stake and ask:

```bash
git -C "$WORKTREE_PATH" status --porcelain -uall
```

```
Worktree removal refused — these files were never committed:

<file list>

1. Commit them to <branch> before cleanup
2. Move them into <main repo root>
3. Delete them (unrecoverable)

Which?
```

Carry out the choice, then remove the worktree.

A successful merge or PR does not establish workspace ownership. Preserved workspaces and branches are an explicit remaining item, not permission to force cleanup.

## Quick Reference

| Option | Merge | Push | Keep Worktree | Cleanup Branch |
|--------|-------|------|---------------|----------------|
| 1. Merge locally | yes | - | Preserve unless Step 6 permits removal | Only fully merged authorized branch, not checked out in a preserved worktree |
| 2. Create PR | - | yes | yes | - |
| 3. Keep as-is | - | - | yes | - |
| Discard (explicit request + exact confirmation) | - | - | Step 6 applies | Only exact confirmed branch if cleanup constraints permit |

## Common Rationalizations

| Excuse | Reality |
|--------|---------|
| "Tests passed earlier this session" | Run the suite on the tree you are about to integrate. A green run only proves the tree it ran on. |
| "They obviously want it merged" | Do not infer integration approval. Reuse an explicit selection for unchanged targets and scope; otherwise present the menu. |
| "They seem done with this feature — I'll offer to discard it" | The menu is complete as written. Discard happens only when your human partner asks for it in so many words. |
| "'Yeah, get rid of it' counts as confirmation" | Only the typed word `discard` authorizes deletion. |
| "The PR is up, so the worktree is clutter now" | PR feedback gets fixed in that worktree. It stays until the work lands. |
| "This other worktree looks stale — I'll clean it too" | Remove only the exact authorized worktree with verified provenance; directory names prove nothing. Preserve unknown worktrees and unrelated registrations. |
| "Removal refused — `--force` is just finishing the cleanup" | The refusal means files exist only in that worktree. `--force` destroys them permanently. Show your human partner and ask. |
| "The merged-result failure is probably flaky" | A failing merged result stops everything. Branch and worktree stay put while you investigate. |
| "The base branch is obviously main" | Confirm the fork point or ask. Merging into the wrong base is expensive to undo. |
| "The push was rejected — force-push will fix it" | A rejected push means the remote moved. Investigate; force-push only on your human partner's explicit request. |
