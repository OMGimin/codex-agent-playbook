# Proportionate boundary validation

Adapted from obra/superpowers under MIT; see LICENSE in this skill directory.

After tracing invalid state, identify the boundaries where validation prevents a demonstrated failure. Typical candidates are public input, domain invariants, and operations with filesystem or service side effects. Add checks only where they protect a meaningful contract; do not duplicate every check at every layer automatically.

For filesystem containment, resolve paths and compare path components using the platform's path semantics. A string prefix alone cannot distinguish a permitted directory from a sibling with a similar name. Preserve the sandbox and require applicable authorization before destructive operations.

Test the invalid case and a valid neighboring case. Record what each check establishes. Multiple checks can reduce risk; they do not prove that every future failure is impossible. Any additional hardening remains subject to task scope.
