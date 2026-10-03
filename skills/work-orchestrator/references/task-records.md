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


## Compact dispatch and return

Use these fields inside the existing task record or tool message, not a mandatory new file for every worker. Omit irrelevant fields; preserve identifiers, scope, ownership, and acceptance criteria when compressing context.

Dispatch:
- Task ID and requested outcome; current artifact/revision and relevant source paths.
- Allowed changes and owned files/resources; dependencies and actions outside scope.
- Acceptance criteria and evidence to return; applicable model selection from model-routing.

Return:
- Task ID and status: returned, blocked, or needs clarification; this is not coordinator verification.
- Short findings/change summary and detailed artifact paths with reviewed revision/state.
- Actual evidence, failed or unrun checks, assumptions, and unresolved dependencies.
- Side effects already performed and whether retrying could duplicate them.

Keep detailed results in artifacts and send relevant summaries plus paths. Do not force a fixed token cap that drops required context or append whole prior conversations.

## Recover from incomplete or conflicting returns

- Error/timeout: inspect state and side effects before retrying; an absent response does not prove no action happened.
- Partial result: request the missing required fields or artifact sections, not an automatic full rerun.
- Contradiction: compare source evidence and artifact versions; resolve the decisive difference rather than voting by confidence.
- Invalid evidence: narrow the check or perform it directly when permitted. Never manufacture a passing result or silently change acceptance criteria.

Apply the existing retry and approval safeguards. Continue independent work and use direct execution when appropriate. No fallback grants a new model, publication, deletion, or spending permission; no unanswered approval becomes consent. Record only the failure evidence needed for recovery, not secrets or full private payloads.

Handoff and recovery examples are adapted from Agency Agents' handoff templates and Multi-Agent Systems Architect; associated MIT notice is retained in this skill's LICENSE.
