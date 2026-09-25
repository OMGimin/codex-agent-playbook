# Workflow routing

Select the smallest workflow that produces the requested result. Available skills are capabilities, not a mandatory sequence.

| Situation | Procedure |
|---|---|
| New project or consequential redesign | `project-shaping`; use `decision-council` only if meaningful alternatives need independent challenge |
| Approved software implementation | Read repository conventions, implement a usable increment, test and review proportionally |
| Reproducible bug or unexpected behavior | `systematic-debugging`; preserve its explicit escalation safeguards |
| Testable behavior or regression | `test-driven-development` according to its applicability |
| Important code change | `requesting-code-review`; review the actual change state |
| Research or current news | `source-backed-research`; use connected/read-only tools and `agent-reach` only if separately installed and its platform adapters help |
| Article, report, explanation | `content-production`; source research only when needed |
| Tool-specific artifact | Use the relevant installed Unity, Figma, document, spreadsheet, image, or video skill |
| Completion claim | `verification-before-completion` when applicable; select evidence appropriate to the artifact |

## Software boundaries

Inspect existing Git state and user changes. Do not begin implementation on main/master without the explicit consent retained from the prior implementation workflow. For existing isolated checkouts, reuse them. Invoke `using-git-worktrees` only if isolation is requested or genuinely needed; preserve its consent and baseline-failure rules. A document or news task does not require Git, worktrees, or commits.

Use the project's commands, versions, and package manager. Choose technology from product constraints and existing code, not from a role's favorite stack. Do not automatically add dependencies, rewrite architecture, or commit after every small step because a template suggests it.

Use `finishing-a-development-branch` when integration or branch finalization is part of the task. Preserve its merge, push, discard, and cleanup safeguards. For a local edit request, deliver the verified diff without forcing a merge/PR menu. Scope authorization and applicable safeguards still govern all external actions.

## Other activity boundaries

Research does not authorize contacting sources, posting, or changing accounts. Article drafting does not authorize publication. A request to operate a project during this task does not create a background service or recurring automation.

Record project state in the project's existing documentation system when writing is authorized. Do not silently convert task records into personal cross-project memory or upload them to Notion or another service.
