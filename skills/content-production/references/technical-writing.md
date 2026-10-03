# Technical documentation from working artifacts

Use for setup guides, API documentation, migration notes, and developer tutorials. Choose the document's job before its format: tutorial teaches through an example, how-to completes a task, reference specifies a contract, explanation develops understanding. Link between these when helpful; a small README can contain several clearly separated purposes.

## Build the document

Inspect the relevant version, code, commands, configuration, and existing docs. Identify the reader's starting point and desired result. Use available artifacts before asking an author to explain them.

- Setup/how-to: prerequisites, working directory, commands, expected result, and likely failure/recovery steps. Name placeholders and avoid real credentials.
- API reference: inputs, authentication/authorization, response/error shapes, pagination or rate limits where applicable, and a representative example consistent with the implementation.
- Migration: affected versions, compatibility, ordered actions, validation, and recovery limitations. Distinguish reversible configuration changes from irreversible data changes.
- Explanation: the problem, chosen approach, alternatives that mattered, and consequences; do not present inferred history as an actual design decision.

Keep executable examples distinct from intentionally incomplete illustrations. Prefer one useful end-to-end example over several unverified fragments. Do not introduce a docs framework, analytics, recurring schedule, or publication merely to document a feature.

## Verify and return

Run executable examples in a suitable authorized environment when feasible. Check results against the documented output, version, links, and prerequisite assumptions. If execution is unavailable, label what was inspected and what remains untested. Do not run destructive examples against real data for verification.

Return the requested document, the implementation/version it describes, actual validation, and remaining gaps. Use a compact record where useful:

| Reader task | Document/example | Implementation reference | Evidence or limitation |
|---|---|---|---|
| First successful operation | Setup and minimal example | Version and relevant interface | Observed result or unrun check |

Adapted from Agency Agents' Technical Writer; retain the associated MIT notice when copying this skill.
