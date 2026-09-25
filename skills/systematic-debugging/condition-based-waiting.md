# Condition-based waiting

Adapted from obra/superpowers under MIT; see LICENSE in this skill directory.

For asynchronous tests, prefer the test framework's condition or event assertion over an arbitrary sleep. Re-read current state on each check, set a bounded timeout, and report the condition that failed. Choose a polling interval appropriate to the system; no single interval suits every runtime.

Illustrative sequence:

1. Trigger the operation in an authorized isolated fixture.
2. Wait until the required observable state is reached or the timeout expires.
3. Assert the behavior and clean up the fixture.

If testing timing itself, such as debounce or throttling, use supported fake timers or a documented timing interval. Waiting for an unrelated event does not test a timing contract. No project-specific TypeScript imports or external helper scripts are required by this reference.
