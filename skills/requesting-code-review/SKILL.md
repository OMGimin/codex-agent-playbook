---
name: requesting-code-review
description: Review meaningful software changes against requirements, correctness, security, and maintainability. Use independent review for important changes and proportionate direct review for small low-risk edits. Review does not authorize merge or deployment.
---

# Requesting Code Review

Follow AGENTS.md rule 15 and [model routing](../work-orchestrator/references/model-routing.md) before dispatch or reuse. Every subordinate must explicitly use `gpt-6-sol` or `gpt-6-luna`; never inherit Astra or promote a reviewer/advisor to Astra because the task is difficult.

Identify requested behavior, project constraints, changed files, and the current revision or working-tree state. Include uncommitted changes when they are the work under review.

If the user requests the coordinator's direct review or prohibits delegation, review directly regardless of change size and do not claim independence. Otherwise, for important, complex, or cross-cutting changes, this skill requests a bounded independent reviewer subagent when available and allowed. Small low-risk edits can use direct review. If independence is unavailable, report direct review accurately.

Use [code-reviewer.md](code-reviewer.md) to provide requirements, artifact scope, change state, relevant context, and available verification. Reviewers inspect evidence and may challenge the plan as well as the implementation. They do not edit files, switch branches, or spawn further reviewers by default.

## Findings and completion

- Prioritize reproducible defects, missing requirements, security issues, and consequential regressions.
- Separate confirmed defects, hypotheses, and optional improvements. No issue quota or first-pass rejection.
- Resolve material issues within scope and re-review affected portions. Re-run checks invalidated by changes.
- Explain justified disagreement with evidence; neither implementer nor reviewer is automatically correct.
- Report blockers and missing evidence; continue independent tasks without marking required unverified behavior as passed.

Return findings, inspected change state, evidence and limits, and technical readiness for the requested milestone. Internal acceptance is not user permission to merge, publish, or expand scope. Use finishing-a-development-branch only when branch integration/finalization is requested.
