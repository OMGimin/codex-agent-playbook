# Reliable browser journey tests

Use when browser integration is the meaningful risk: navigation, user-visible state, or interactions across application boundaries. Prefer unit/API tests for behavior they establish sufficiently. Use the existing runner; do not install Playwright or Cypress merely because this reference mentions them.

## Test design

- Name the user journey and observable outcome. Avoid reproducing implementation details in assertions.
- Prefer accessible roles/labels, with stable test IDs where necessary. Avoid selectors dependent on incidental DOM nesting.
- Wait for the relevant condition, response, or state transition rather than a fixed sleep or unrelated global network-idle condition.
- Give each parallel test isolated data and ownership. Seed through authorized fixtures or APIs when appropriate; test the login UI separately rather than repeating it in every scenario.
- Verify the real result: a filled form or success banner may need a response or persisted-state assertion. Screenshots establish visual state, not persistence by themselves.
- Clean up only test-owned state in an authorized environment. Never use production data or shared accounts as disposable fixtures.

## Failures and evidence

Capture enough failure evidence to distinguish selector/waiting/fixture/environment problems from a product regression. Depending on the runner, use traces, screenshots, console/network errors, and the test state. Redact secrets and private payloads; full logs are not automatically appropriate artifacts.

A retry pass is evidence of possible flakiness, not proof that the original failure is fixed. Investigate before attributing the cause. Repeat runs when intermittent behavior warrants it; do not require ten passes for every change. Do not remove release-blocking tests or relax gates without applicable authorization.

Return the tested journey, environment/browser, data isolation approach, observed assertions, failure artifacts, and untested scope. After a fix, rerun the original failure and affected neighboring checks. Use the project's actual commands and addresses, not assumed helper scripts or localhost ports.

Adapted from Agency Agents' Test Automation Engineer; retain the associated MIT notice when copying this skill.
