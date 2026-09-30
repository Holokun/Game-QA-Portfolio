# BUG-DW-003 — Healing Potion Is Consumed at Full HP

| Field | Value |
|---|---|
| Status | New |
| Severity | Major |
| Priority | Medium |
| Component | Healing / Inventory / Player resources |
| Type | Functional, negative testing |
| Build | V0.1.7 BETA — Early Playtest Build |
| Platform | PC, Windows 11 Pro for Workstations 25H2 |
| Input | Keyboard and mouse |
| Reproducibility | Not formally measured |

## Summary

The player can complete the healing action and consume a potion while the active Player Character (PC) already has full HP.

## Preconditions

- An active level has started.
- The active PC is at full HP.
- At least one healing potion is available.
- The healing action is not on cooldown.

## Steps to Reproduce

1. Start or load an active level.
2. Confirm that the active PC has full HP.
3. Note the current potion count.
4. Press and hold `H` until the healing action completes.
5. Observe the animation, HP, and potion count.

## Expected Result

Healing does not start while the PC is at full HP. No healing animation completes and the potion count remains unchanged.

## Actual Result

The healing animation completes and one potion is removed even though the PC is already at full HP and receives no health benefit.

## User Impact

The player can accidentally lose a limited healing resource without receiving any benefit, reducing the chance of surviving later encounters.

## Evidence

- Recorded as `CANDIDATE-BUG-003` in the [structured requirements source](../deepward-draft-requirements-for-testrail-ai-v4.md#candidate-bug-003--potion-can-be-used-at-full-hp).
- Original observation is referenced in the [exploratory session](../exploratory-test.md#candidate-defects-raised).
- Dedicated reproduction media: **not captured**.

## Recommended Follow-up Coverage

- Repeat with each available PC and different potion counts.
- Test at one point below maximum HP and at maximum HP.
- Verify whether pressing or holding `H` changes the result.
- Confirm behavior before and after level completion.
