---
name: test-driven-development
description: Use test-first development for meaningful automated behavior checks in software features, regression fixes, and refactoring. Select proportionate alternatives for prose, visual assets, trivial edits, and unavailable test environments.
---

# Test-Driven Development

Apply project-specific testing requirements and the user's scope. Use TDD when a repeatable automated test protects meaningful behavior: API contracts, validation, state transitions, calculations, persistence, and regressions.

Before implementation in a Git repository, inspect branch and user changes. Preserve the existing implementation safeguard: do not begin on main/master without explicit consent for that branch. A general feature request is not branch-specific consent. For isolation use using-git-worktrees and its existing consent rules; no Git ceremony is needed outside repository work.

Do not add tests merely to mirror implementation or prove a document contains a phrase. For low-risk text/configuration edits, visual assets, or disposable prototypes, choose proportionate inspection, validation, or smoke checks. Explain consequential testing limitations. Explicit project testing requirements cannot be silently waived.

## Red, green, refactor

1. Define the observable result independently of the implementation. Read [writing-good-tests.md](writing-good-tests.md) when designing nontrivial tests.
2. Write a minimal behavior or regression test and execute it against pre-change behavior. Confirm the intended failure; distinguish product defects from broken fixtures or environment errors.
3. Implement the smallest in-scope change that satisfies the requirement.
4. Run the test and relevant neighboring checks. Inspect outputs and exit status.
5. Refactor within scope while checks stay green. Broaden validation when impact or failures justify it.

Preserve existing or supplied code; never delete it to reenact test-first development. When safe, demonstrate the regression on an isolated pre-fix copy. Do not revert user edits or mutate shared state to manufacture a red test. If red was not observed, state what the test actually established.

Use authorized isolated fixtures. Do not alter production data, saves, or destructive migrations to obtain evidence without permission. When execution is blocked, continue independent justified work, identify the missing check, and never claim a passing test. Use systematic-debugging for unexpected failures and verification-before-completion for completion claims.
