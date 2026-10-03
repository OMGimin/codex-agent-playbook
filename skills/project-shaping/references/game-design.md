# Playable rules and testable design hypotheses

Use for a new gameplay loop or a consequential mechanic change. Inspect existing design, playable behavior, save assumptions, and target platform. A small adjustment needs only the affected rule, rationale, and check; do not restart the entire game design process.

## Specify the player decision

Connect actions, feedback, risk, and reward in the relevant moment-to-moment or session loop. Include long-term progression only if the game needs it. Do not add daily rewards, monetization, or retention systems by default.

For a substantial mechanic, record:

- Purpose and player experience hypothesis.
- Inputs/triggers, state transitions, outputs, and feedback.
- Success/failure conditions and consequences.
- Boundary cases: simultaneous events, minimum/maximum resources, interruption, and save/load where relevant.
- Tuning variables, provisional values, rationale, and what observation would change them.
- Dependencies and intended interactions with other systems.

For interacting mechanics, use a small table of relevant pairs: interaction, intended outcome, exploit/failure risk, and test. Do not enumerate unrelated system pairs to fill a template.

## Resolve uncertainty

Choose a paper model, spreadsheet, small playable slice, or direct playtest according to the uncertainty. A numeric simulation can reveal economy loops but does not establish enjoyment. Mark untested values as provisional rather than inventing balanced numbers.

Before a playtest, state the question, scenario, and observable evidence. Afterwards separate observation from interpretation and proposed adjustment:

| Question | Scenario | Observation | Interpretation | Next change/check |
|---|---|---|---|---|
| Can players understand this choice? | Relevant playable situation | What actually happened | Hypothesis explaining it | Smallest informative follow-up |

Return an implementable rule, dependencies, acceptance checks, and unresolved experience hypotheses. Preserve design revisions and rationale in the existing document system. Do not force ScriptableObjects, class-length limits, fixed success percentages, or a particular engine architecture.

Adapted from Agency Agents' Game Designer; retain the associated MIT notice when copying this skill.
