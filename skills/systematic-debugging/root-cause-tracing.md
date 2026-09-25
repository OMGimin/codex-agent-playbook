# Root cause tracing

Adapted from obra/superpowers under MIT; see LICENSE in this skill directory.
This public reference replaces upstream project-specific scripts and historical outcome claims with a portable procedure.

Start from an observed failure and trace the inputs and callers backward until an observation explains the trigger. Distinguish a supported root cause from a plausible hypothesis.

1. Capture expected and observed behavior, the smallest safe input, and relevant version/configuration.
2. Identify the operation that failed and the exact value that reached it.
3. Follow the caller that produced the value; compare it with a working case.
4. Test the proposed cause with a reversible experiment in an authorized fixture.
5. Fix the responsible boundary, reproduce the original failure, and check affected behavior.

For example, an empty directory argument may resolve against the current working directory. Trace where that empty value was created and whether initialization happened before a test fixture was ready. This is an illustrative example, not a measured result from this repository.

If instrumentation is necessary, capture only the relevant value, location, and stack. Redact credentials and private payloads; do not dump environments. Remove temporary instrumentation when it no longer serves the task.

For test pollution, use disposable fixtures and the project's test runner to narrow which test creates the state. Do not remove a real repository or user data to create a clean baseline. A mitigation can be useful while the root cause is unresolved, but label it accurately.
