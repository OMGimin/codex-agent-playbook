---
name: project-shaping
description: Shape a new project or substantial change into a scoped outcome, requirements, alternatives, and an executable plan across software, apps, games, research, and content. Do not impose a design ceremony on clear small tasks.
---

# Project Shaping

Use the user's AGENTS.md for autonomy, questions, and approvals. Inspect relevant existing code, documents, decisions, and dependencies before proposing a new structure. Preserve unrelated intent and behavior.

## Establish the outcome

Determine the audience or user, desired result, constraints, existing assets, non-goals, and how success will be checked. Obtain information from context and authorized investigation first. State consequential assumptions. Ask only for essential missing information or decisions that materially change the result and cannot reasonably be inferred.

Compare alternatives only when they affect scope, feasibility, usability, cost, or maintenance. Include improving what exists as an option before recommending replacement. Explain why a recommendation fits; do not promise perfection or treat a preference as an error.

## Produce a proportionate specification and plan

For small changes, a short statement of behavior and verification is enough. For substantial projects, use existing project documents or a concise local design/plan with:
- Desired outcome, users, scope, constraints, non-goals.
- Relevant current state and dependencies.
- Chosen approach, meaningful alternatives, and decision rationale.
- Behavior, interfaces, edge cases, and acceptance criteria.
- Independently useful increments, task dependencies, expected artifacts, and verification.
- Risks, provisional values, open questions, and the next evidence needed.

Do not require all future implementation code in the plan. Specify contracts and examples where ambiguity would cause rework. Mark real unknowns and define how to resolve them; do not invent certainty to fill a template. Avoid task splits made only to meet a fixed time estimate.

For substantial game mechanics, read [game design](references/game-design.md) for rule and playtest templates. For games, separate fun hypotheses from validated behavior. For research and content, define source/date coverage and audience rather than imposing software tests. For apps, include target devices, lifecycle, offline behavior, packaging, and distribution only as relevant.

## Handoff and scope

Check that requirements map to deliverables and verification; resolve contradictions before dependent work. If the user requested a proposal or plan only, deliver it and stop at that boundary. If implementation is already authorized, proceed within its scope without asking for a redundant plan approval. Explicit review-before-execution requirements remain binding; silence is not approval.

Use `work-orchestrator` for substantial execution or delegation. A plan is not permission to publish, merge, spend, expand scope, or relax existing project safeguards. Record material design changes and verify that dependent work remains consistent.
