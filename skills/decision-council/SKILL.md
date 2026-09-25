---
name: decision-council
description: Pressure-test consequential decisions with multiple independent perspectives and an evidence-based synthesis. Use for meaningful tradeoffs such as major redesigns or strategic direction, not routine facts, small edits, or ordinary debugging.
---

# Decision Council

Follow AGENTS.md rule 15 and [model routing](../work-orchestrator/references/model-routing.md) before dispatch or reuse. Every subordinate must explicitly use `gpt-6-sol` or `gpt-6-luna`; never inherit Astra or promote a reviewer/advisor to Astra because the task is difficult.

Frame the decision, current evidence, user constraints, alternatives, reversibility, and what remains uncertain. First resolve facts through authorized investigation when they could decide the issue. Do not convene a council merely because five roles are available.

## Choose perspectives and depth

Use the smallest useful set of perspectives, typically two or three. For a consequential decision with several distinct risks, use up to these five:
- Red team: plausible failure modes, early warning signals, and mitigations.
- First principles: assumptions, constraints, and whether the problem is framed correctly.
- Alternatives: options with materially different costs or benefits, including retaining the current approach.
- Outside perspective: relevant analogous cases and where the analogy fails.
- Execution feasibility: dependencies, resources, reversibility, and the smallest informative experiment.

These are analytical lenses, not five permanent managers. If the user requests direct execution or prohibits delegation, apply the useful lenses yourself and label the result single-agent analysis; this overrides the advisor-subagent procedure. Otherwise, when native delegation is available and authorized, this skill requests bounded read-only advisor subagents; obey current slot and model limits. If unavailable or disproportionate, conduct a clearly labeled single-agent analysis rather than claiming independent review.

Give each advisor the same factual brief without other advisors' initial conclusions. Require recommendation, evidence, assumptions, unknowns, and what would change the recommendation. Do not infer correctness from confidence labels or votes.

## Synthesize and stop

Compare supporting evidence and tradeoffs; preserve meaningful dissent. One targeted follow-up on a decisive disagreement may help. Do not run forced debate, repeated voting, or automatic deep escalation when no new evidence is likely. Prefer a small experiment when discussion cannot resolve an empirical question.

Deliver the recommendation, alternatives, key assumptions, unresolved risks, and next step. Respect an informed user choice unless important new evidence appears. Advice does not expand execution authority. Do not spend money, change scope, override explicit gates, or publish merely because advisors agree.

For project continuation, record the decision in existing project notes only when writing is in scope. Do not create a personal learning journal or persistent cross-project memory automatically.

The five lenses are inspired by TorpedoD's claude-council; this is a locally rewritten lightweight workflow, not an installation of its CLI, scripts, or approval escalation:
https://github.com/TorpedoD/claude-council
