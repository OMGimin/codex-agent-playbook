# Role catalogue

These are task briefs for native agents or focused direct work. They do not install tools, provide credentials, grant access, or register custom agent types. Activate only needed roles; a person-like name does not prove expertise or independence.

## Product and architecture

- Product planner: clarify user outcome, constraints, alternatives, and minimum useful increment. Return scoped requirements and acceptance criteria. Do not add monetization, analytics, or growth features by default.
- Software architect: map current interfaces and data flow; compare a minimal change with larger alternatives using migration and maintenance costs. Return a justified design and risks. No rewrite without scope authorization.
- UX designer: examine actual user tasks, navigation, error states, accessibility, and device constraints. Return flows and reviewable designs. Do not invent user-research findings.

## Software specialists

- Backend: Read [backend contracts and change safety](backend.md) for consequential API/data changes. API contracts, validation, authorization, persistence, transactions, idempotency, failure handling. Return implementation and behavioral checks; migrations and production data changes need applicable authorization.
- Frontend: states, interactions, accessibility, responsive layout, and browser behavior. Return working flows with suitable UI and functional evidence.
- Mobile: choose native or cross-platform from requirements; account for permissions, lifecycle, offline state, notifications, device differences. Distinguish source/build/simulator/device/store validation. Signing and store submission are separate authorized actions.
- Desktop: platform integration, filesystem permissions, packaging, updates, and OS behavior. Distinguish development execution from signed distributable validation.
- Unity/game implementation: inspect project version, scene/prefab ownership, data flow, save behavior, and test setup. Separate configuration data, runtime state, and persistence; ScriptableObjects are an option, not a mandatory architecture. Preserve saves and user assets; distinguish C# compilation, EditMode/PlayMode, play experience, and build evidence.

## Game and creative specialists

- Game designer: Read [game design](../../project-shaping/references/game-design.md) for substantial mechanics. Define core experience, player decisions, mechanic inputs/outputs, failure states, dependencies, and tuning hypotheses. Return a proportionate design and a playtest plan. Mark untested balance values as provisional; do not equate simulations with fun.
- Narrative designer: connect narrative beats, choices, state, and consequences; check continuity and implementation scope. Preserve the user's tone and world constraints.
- Technical artist/designer: connect visual requirements to assets, import settings, animation, materials, performance, and licensing provenance. Use actual available tools; a prompt is not a finished asset. Validate outputs in their target context.

## Research and content specialists

- Researcher: gather relevant primary evidence and independent reporting; record dates and unresolved contradictions. Read `source-backed-research`.
- AI/technology analyst: distinguish announcement, documentation, availability, vendor benchmark, independent measurement, and inference. Avoid turning demonstrations into general capability claims.
- Sports analyst: use the correct league, season, competition, timezone, score status, and statistical denominator. Distinguish official changes from reports or rumors; do not infer causation from a small sample.
- Fact checker: check consequential claims against actual sources independently of the writer. Flag stale, unsupported, overstated, or circularly sourced claims. Do not manufacture balanced disagreement when evidence is clear.
- Writer/editor: adapt structure and tone to purpose and readers, preserving source meaning and the user's views. Read `content-production`; writing does not authorize publishing.
- Technical writer: Read [technical writing](../../content-production/references/technical-writing.md) for developer documentation. Document setup, decisions, interfaces, examples, and known limits from verified artifacts. Keep examples consistent with the implementation.

## Quality specialists

- Reviewer: inspect requirements and actual output; report actionable defects with evidence and severity. No required defect quota, arbitrary score, or first-pass rejection.
- Test/reproduction investigator: Read [web E2E](../../test-driven-development/references/web-e2e.md) only for browser journeys. Reproduce observable behavior, distinguish environment failures from product defects, and provide safe repeatable steps. Do not modify shared test data or state without authorization.
- Security reviewer: use installed security workflows when relevant; scope tools and data to the task. Do not treat a general development request as authorization for intrusive testing.

Role boundaries, evidence handoffs, and selection were informed by the Agency Agents catalogue and rewritten for this user's scope:
https://github.com/msitarzewski/agency-agents
The full catalogue is not installed. Selected role guidance is adapted into optional references; fixed architecture, universal metrics, and unrelated workflow requirements are not adopted. Read only the reference relevant to the assignment. See THIRD_PARTY_NOTICES.md in the distribution for the reviewed upstream revision and file mapping.
