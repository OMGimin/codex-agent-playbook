---
name: verification-before-completion
description: Check that completion and correctness claims have evidence valid for the current artifact state. Use before reporting software or substantial artifact work complete; distinguish verified, failed, and unverified outcomes without redundant rechecks.
---

# Verification Before Completion

Match important completion claims to evidence appropriate to the requested deliverable. Apply AGENTS.md and explicit project acceptance criteria. Scale verification to impact and uncertainty.

## Evidence validity

1. Identify the requirement and the observation that would establish it.
2. Inspect the artifact, source, or command output, including actual results and exit codes.
3. Check that evidence matches the current files, revision, configuration, environment, and relevant time window.
4. Reuse valid evidence. Repeat affected checks after meaningful changes, failures, stale external facts, or unresolved concerns; do not rerun an unchanged expensive check merely because it ran in a previous message.
5. Report passed, failed, and unverified outcomes, explaining consequential gaps.

## Appropriate checks

- Software: behavioral tests, relevant integration checks, builds/type checks, and original failure reproduction. Build success alone does not prove runtime behavior.
- UI/apps: actual interactions and visual checks on relevant browsers/devices; screenshots alone cannot prove persistence, permissions, or lifecycle behavior.
- Unity/games: separate compilation, EditMode/PlayMode, builds, save compatibility, and playtest observations. License failure blocks a runtime check; it is not itself a compilation defect.
- Research/news: sources, dates, provenance, and support for consequential claims. Copies of one report are not independent corroboration.
- Documents/media: content, completeness, rendering, and use in the requested format. A prompt is not a finished image or video.

Use isolated authorized verification. Do not reset user data, revert user changes, or contact people just to obtain evidence without permission. Review-only work stays read-only.

A delegate report is an input, not automatic proof; inspect relevant artifacts. Never invent independent validation, claim an unrun test passed, or call partial checks comprehensive. If required checks are blocked, deliver useful work with its true status and remaining actions. A proposal-only task ends with the requested proposal, not implementation.
