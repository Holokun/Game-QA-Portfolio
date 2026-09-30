# BUG-DW-001 — First Standing Kick Does Not Consume Stamina

| Field | Value |
|---|---|
| Status | New |
| Severity | Major |
| Priority | High |
| Component | Combat / Kick / Stamina |
| Type | Functional, resource management |
| Build | V0.1.7 BETA — Early Playtest Build |
| Platform | PC, Windows 11 Pro for Workstations 25H2 |
| Input | Keyboard and mouse |
| Reproducibility | Not formally measured |

## Summary

The first kick performed while the Player Character (PC) is standing plays the kick animation but does not deduct the expected stamina cost.

## Preconditions

- An active level has started.
- The PC is alive and standing.
- The PC has enough stamina to perform a kick.
- No kick animation is currently playing.

## Steps to Reproduce

1. Start or load an active level.
2. Ensure the PC is standing and note the current stamina value.
3. Press `Q` once to perform a kick.
4. Observe the kick animation and stamina bar.

## Expected Result

The PC performs one kick animation and the defined stamina cost is deducted once when the kick is accepted.

## Actual Result

The first standing kick animation plays, but the stamina value does not decrease.

## User Impact

The player can perform a stamina-based combat action without paying its resource cost. This creates inconsistent combat rules and may provide an unintended advantage.

## Evidence

- Recorded as `CANDIDATE-BUG-001` in the [structured requirements source](../deepward-draft-requirements-for-testrail-ai-v4.md#candidate-bug-001--first-standing-kick-may-not-consume-stamina).
- Original observation is referenced in the [exploratory session](../exploratory-test.md#candidate-defects-raised).
- Dedicated reproduction media: **not captured**.

## Recommended Follow-up Coverage

- Repeat the first kick with each available PC.
- Compare standing, walking, running, and airborne states.
- Verify whether later kicks deduct stamina correctly.
- Confirm whether starting a new level or expedition resets the behavior.
