# Delegation and continuation record

Use the project's existing location and format. If none exists, a small `docs/work/<task-name>.md` is a default only when a durable record is warranted and local writing is authorized. For read-only requests keep the record in the response or an allowed scratch location.

Record:
- Goal and requested artifact; investigation/proposal/execution boundary.
- Authorized scope and side effects, explicit approval conditions, relevant constraints.
- Acceptance criteria and evidence appropriate to each criterion.
- Tasks with IDs, owners, dependencies, file/artifact ownership, status, retry budget, explicitly requested model/reasoning, and runtime confirmation when exposed.
- Decisions with reasons and unresolved assumptions.
- Outputs with paths, reviewed revision/state, verification commands or source evidence, limitations.
- Next action and blockers for continuation.

Dispatch only relevant sections and source paths, not the entire conversation. For a worker's return require findings or artifact, actual changes, evidence, uncertainties, and blockers. Reviewers get the requirements and artifact, not instructions to endorse the implementer's conclusions.

At resumption, verify that referenced files, revisions, and services still match the record. Reuse completed work with valid evidence; investigate drift rather than redispatching everything. Do not erase records automatically at completion. Personal memory updates require their own authorization.
