# BUG-DW-002 — Repeated Kick Input Consumes Stamina Without Matching Actions

| Field | Value |
|---|---|
| Status | New |
| Severity | Major |
| Priority | High |
| Component | Combat / Kick / Input handling |
| Type | Functional, input queue, resource management |
| Build | V0.1.7 BETA — Early Playtest Build |
| Platform | PC, Windows 11 Pro for Workstations 25H2 |
| Input | Keyboard and mouse |
| Reproducibility | Not formally measured |

## Summary

Repeatedly pressing the kick key during the active kick animation deducts stamina for inputs that do not produce corresponding kick actions.

## Preconditions

- An active level has started.
- The PC is alive, standing, and has enough stamina for several kicks.
- No kick animation is currently playing.

## Steps to Reproduce

1. Start or load an active level.
2. Ensure the PC is standing and note the current stamina value.
3. Press `Q` five times within approximately one second.
4. Count the kick animations that play.
5. Observe the total stamina deducted.

## Expected Result

Only the first valid input is accepted while the kick animation is active. One kick animation plays and stamina is deducted once. Further kick input becomes available after the current animation or action cooldown ends.

## Actual Result

Approximately one kick animation plays, but stamina is deducted for the additional `Q` inputs. Rapid input can drain the stamina bar even though the PC performs far fewer kicks than the number of stamina deductions.

## User Impact

Normal rapid input can unintentionally remove most or all stamina, leaving the player unable to perform other stamina-dependent actions. The visible action count and resource consumption do not match.

## Evidence

- Recorded as `CANDIDATE-BUG-002` in the [structured requirements source](../deepward-draft-requirements-for-testrail-ai-v4.md#candidate-bug-002--repeated-kick-input-may-consume-stamina-without-executing-kicks).
- Original observation is referenced in the [exploratory session](../exploratory-test.md#candidate-defects-raised).
- Dedicated reproduction media: **not captured**.

## Recommended Follow-up Coverage

- Repeat with different input frequencies and each available PC.
- Compare the number of accepted kicks with the number of stamina deductions.
- Test while moving, jumping, sliding, and at low stamina.
- Verify behavior at different frame-rate limits.
