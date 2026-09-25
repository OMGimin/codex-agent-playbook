---
name: systematic-debugging
description: Investigate bugs, failed tests, build failures, and unexpected software behavior through reproduction, evidence, and hypothesis testing before applying a targeted fix.
---

# Systematic Debugging

Separate the symptom, expected behavior, actual behavior, and environment. Inspect relevant recent changes and user work before modifying anything. A runtime/tool failure is not automatically a product defect.

Before applying a fix in a Git repository, check branch and user changes. Preserve the implementation safeguard: do not begin implementation on main/master without explicit consent for that branch. General bug-fix authorization does not supply branch-specific consent. Read-only investigation can continue while that decision is pending. If isolation is needed, use using-git-worktrees with its existing consent rules.

## Investigate and test

1. Read errors and logs; reproduce with the smallest safe inputs. If intermittent, record conditions and gather evidence rather than pretending reproduction succeeded.
2. Trace the relevant data and control flow. Use [root-cause-tracing.md](root-cause-tracing.md) for deeper stacks and [condition-based-waiting.md](condition-based-waiting.md) for timing problems.
3. State a specific hypothesis and the observation that would refute it. Compare relevant working behavior and dependency/configuration differences.
4. Test one hypothesis at a time with a minimal, reversible in-scope experiment. Capture only necessary diagnostic data; never dump full environments, credentials, cookies, tokens, or private payloads.
5. Apply a targeted fix only when supported by evidence. Use test-driven-development when a meaningful automated regression test is feasible; otherwise record an appropriate reproduction/check and its limits.
6. Reproduce the original scenario and check affected neighboring behavior. Use verification-before-completion before claiming success.

Use [defense-in-depth.md](defense-in-depth.md) when additional validation addresses demonstrated risks; it is not permission for unrelated hardening. Preserve user data, saves, unrelated changes, and applicable read-only constraints. A clearly labeled mitigation may be useful while root cause remains uncertain, but must not be reported as a proven root-cause fix.

## Failed attempts and preserved escalation safeguard

Do not stack speculative fixes. After a failed fix, inspect new evidence and revisit the hypothesis. Preserve the existing explicit safeguard: after three failed fixes on the same issue, discuss the approach with the user before attempting another fix. Do not reset the count by renaming the task or switching agents. Complete independent investigation or unrelated authorized work while this decision is pending.

Repeated failure is evidence to reconsider assumptions, environment, test validity, and architecture; it does not prove that the architecture is wrong. If an external dependency blocks reproduction, report the limitation and continue justified independent work. Do not expand scope, destructively reset data, or claim the issue fixed to bypass a blocker.
