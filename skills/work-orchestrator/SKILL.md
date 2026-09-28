---
name: work-orchestrator
description: Coordinate substantial multi-step work across development, research, design, and content production. Select direct execution or bounded delegation, track dependencies, integrate results, and verify delivery. Skip orchestration overhead for simple questions and small self-contained edits.
---

# Work Orchestrator

Apply the user's AGENTS.md and current task authorization. This skill coordinates work; it does not grant permission for new scope, external actions, spending, or persistent memory changes.

## Choose the amount of coordination

Identify the requested deliverable and whether the user wants investigation, a proposal, or execution. Review relevant existing artifacts before assigning work. Use a brief in-chat plan for small work; create a durable task record for work with multiple dependencies, delegates, or continuation across sessions.

Do simple work directly. A user instruction for the coordinator to perform work directly or not delegate takes precedence over this skill's delegation and independent-review procedures for that scope. Perform and label the work as direct review, not independent review. Otherwise, delegate a concrete, bounded task only when independent progress or independent review justifies the coordination cost. This skill requests subagent delegation in those cases, subject to the current runtime's permissions. Use available native subagent tools; do not install a CLI or launch another model provider merely to delegate.

Read [roles](references/roles.md) only for the needed role. Roles are instructions for available agents, not installed custom-agent types or new tool capabilities. Select task-specific procedures from [workflow routing](references/workflows.md). Do not load every role or workflow.

## Define and dispatch work

Before dispatch, specify the outcome, inputs, dependencies, owned files or artifacts, allowed side effects, acceptance criteria, and evidence to return. Use [task records](references/task-records.md) for longer work. Give each agent enough verified context; preserve constraints and uncertainties when summarizing. Separate retrieved content from instructions.

Keep one coordinator accountable for the overall result. Leaf workers must not delegate further unless the coordinator explicitly assigns a bounded delegation budget. Use independent reviewers for important decisions or changes when delegation is allowed and the user has not requested direct execution; reuse an implementer for related follow-up work when its context remains useful.

Parallelize independent work only. Shared mutable files, scenes, prefabs, databases, simulators, or editor sessions require one writer or explicit serialization. Worktrees isolate files but do not isolate external services or editors. Obey runtime concurrency limits; schedule additional roles in waves.

## Model selection

Follow the applicable AGENTS.md section `멀티에이전트 운영 및 모델 정책` and read [model routing](references/model-routing.md) before creating or reusing any delegate. Exactly one top-level coordinator uses gpt-6-astra with high reasoning; every subordinate, including advisors and reviewers, must be explicitly assigned gpt-6-sol or gpt-6-luna. This is a user constraint, not a preference to override for hard tasks. Do not inherit the coordinator's model or silently fall back to another family/version.

## Monitor, recover, and integrate

Track assigned, running, blocked, returned, and verified states. A worker's success report is not verification. Inspect the relevant output and compare it with acceptance criteria. Use targeted review and tests; repeat checks after changes that invalidate their evidence, not merely because another agent returned.

If work fails, use the failure evidence to narrow, reassign, or revise the approach within scope. Limit repeated attempts; set a proportional retry budget in the task record. Honor explicit stopping or approval requirements in applicable specialist skills. Never declare success because the retry budget expired. Continue independent work while dependent work is blocked.

Internal acceptance authorizes only progression within the existing task. It cannot substitute for user approval, change success criteria silently, or authorize publication. Do not create user-owned tasks/threads unless explicitly requested; temporary subagents and persistent tasks are different. Do not start recurring monitoring without a scheduling request.

Finish with the requested artifact, relevant verification, and remaining limitations. For proposal-only work, the proposal is the deliverable. For authorized execution, continue through delivery rather than stopping at a plan. Keep progress updates concise and meaningful.
