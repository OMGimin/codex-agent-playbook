# Backend contracts and change safety

Use for API, persistence, or external-service changes whose boundaries need explicit design. Start from the existing implementation and expected load; select only checks relevant to the change. This reference does not authorize migrations or production operations.

## Inputs and decisions

Identify callers, authentication and authorization boundaries, data ownership, existing contracts, deployment constraints, and failure reports. Choose architecture from these constraints; a monolith, queue, cache, or service split needs a task-specific reason.

- API: specify input validation, permissions, response/error shapes, pagination, and compatibility for affected operations. Use the project's machine-readable contract format where available.
- External calls: define timeout ownership, bounded retries/backoff, and whether retries are safe. For side effects, establish idempotency and behavior after an ambiguous response before retrying.
- Persistence: identify transaction boundaries, uniqueness/concurrency constraints, and what happens on partial failure.
- Data changes: when applicable, plan compatible schema rollout, backfill, reconciliation, and recovery. Distinguish code rollback from restoring data; do not assume one reverses the other.
- Observability: identify the evidence needed to diagnose user-visible failures, such as correlation IDs and stable error codes. Keep credentials and unnecessary personal data out of logs. Add tracing infrastructure only when justified.
- Performance: use a relevant workload and baseline. Do not invent universal latency, availability, or traffic targets.

## Return and verify

Use the existing project format or a compact table:

| Boundary | Required behavior | Failure/compatibility risk | Verification |
|---|---|---|---|
| Affected API or data operation | Contract and authorized outcome | Timeout, duplicate, denied access, partial write, or older caller | Relevant test or observed evidence |

For implementation, return changed contracts and code, actual checks, migration implications, and remaining risks. For design-only work, return the proposed contract and verification plan without claiming execution. Exercise applicable denial, duplicate/retry, and partial-failure paths; a successful happy-path response alone does not establish data safety.

Adapted from Agency Agents' Backend Architect; provenance and MIT notice are retained in this skill's LICENSE and the repository's THIRD_PARTY_NOTICES.md.
