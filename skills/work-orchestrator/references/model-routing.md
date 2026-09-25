# Model routing

AGENTS.md rule 15 is the common authority. This reference specifies dispatch mechanics, not new permissions.

- One top-level coordinator: `gpt-6-astra`, reasoning `high`.
- All subordinate implementers, researchers, reviewers, council advisors, and authorized child coordinators: explicitly select `gpt-6-sol` or `gpt-6-luna`.
- Use Sol for implementation, complex analysis, and consequential review; Luna for narrow tasks with clear checks. Choose a supported reasoning effort appropriate to the task. No subordinate Astra, Terra, GPT-5, or other implicit fallback.

## Before each dispatch or reuse

Check that the runtime exposes the requested model and permits its selection. Pass the exact model ID explicitly. For native `spawn_agent`, model overrides require `fork_turns: "none"` or a supported positive turn count; do not use an omitted/default or `"all"` full-history fork that inherits the parent. Prefer `"none"` with a self-contained brief.

For an existing delegate, check its task ownership and the record of an explicit allowed model request accepted by the tool. Compare actual runtime identity if exposed; absent identity alone does not invalidate an accepted request. If the selection was inherited, has no accepted explicit request record, or conflicts with an exposed identity, do not reactivate it unless a safe supported model change is accepted and recorded. A permitted replacement is allowed only if useful. This includes reviewers created before this policy.

If the user explicitly requests a separate subordinate task/thread, specify the allowed model in the creation tool as well. This policy does not authorize creating user-owned tasks without an explicit request. Root vs. subordinate is determined by the assignment, not its display name.

Include the allowed subordinate models in briefs when further delegation is explicitly allowed. Keep leaf agents from delegating otherwise. Track requested model, reasoning effort, and tool-confirmed runtime identity separately; do not invent verification if the tool exposes no identity field. An explicit accepted model parameter is sufficient to proceed under this policy, but records the request, not an independent runtime attestation. Lack of a separate identity field is a reporting limitation, not a stop condition. If acceptance is ambiguous, check status before proceeding or creating a duplicate.

If selection is unavailable, the request is rejected, or exposed runtime identity violates the allowed models, withhold that delegation, report the constraint, and continue useful direct work; do not launch a default-model worker. Resolve difficulty by decomposition, supported Sol reasoning, or the existing coordinator's direct judgment. Only an explicit user instruction can create a model exception. A reviewer cannot grant one.

Markdown does not switch the current coordinator. If it is not known to be Astra/high, disclose that limitation instead of claiming compliance. No automatic configuration change, recursive task creation, or additional Astra coordinator is implied.
