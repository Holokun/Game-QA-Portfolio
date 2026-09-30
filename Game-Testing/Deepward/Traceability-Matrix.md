# Deepward — Requirements-to-Tests Traceability Matrix

## Purpose

A traceability matrix connects each requirement to the test cases that verify it. It makes missing coverage visible and prevents a large test count from being mistaken for complete coverage.

Status definitions:

- **Covered** — at least one retained case directly verifies the requirement.
- **Partial** — a retained case touches the behavior but does not fully verify the requirement.
- **Gap** — no matching retained case was found in the CSV export.

## Matrix

| Requirement | Behavior | Retained TestRail case(s) | Status |
|---|---|---|---|
| REQ-TGT-001 | Crosshair becomes red on enemies | None | **Gap** |
| REQ-TGT-002 | Crosshair becomes red on light-source objects | None | **Gap** |
| REQ-CHAR-001 | Three PCs are available | C3845 — Basic PC Switching Functionality | Covered |
| REQ-CHAR-002 | PCs are selected with keys 1, 2, and 3 | C3845 — Basic PC Switching Functionality | Covered |
| REQ-CHAR-003 | Three-second switch-back cooldown | C3846, C3847 | Covered |
| REQ-CHAR-004 | Inactive PC ammunition recovery | None | **Gap** |
| REQ-CHAR-005 | Slide/jump state resets after switching | C3848, C3849 | Covered |
| REQ-ABL-001 | PCs have abilities | C3837 uses an ability but does not validate ability availability across PCs | Partial |
| REQ-ABL-002 | Abilities have cooldown durations | C3837 waits for a cooldown but does not validate individual durations | Partial |
| REQ-ABL-003 | Cooldown continues while a PC is inactive | C3837 — Ability Cooldown Persistence During Inactivity | Covered |
| REQ-STM-001 | Stamina recovers while a PC is inactive | C3838 — Stamina Recovery During Inactivity | Covered |
| REQ-HEAL-001 | Healing requires held input | C3841 — Continuous Hold Input for Healing | Covered |
| REQ-HEAL-002 | Potion reuse cooldown | C3842 — Potion Reuse Cooldown Enforcement | Covered |
| REQ-HEAL-003 | No healing with zero potions | C3843 — Healing Attempt with Zero Potions | Covered |
| REQ-HEAL-004 | Health restoration during an active level | None directly validates successful HP restoration | **Gap** |
| REQ-HEAL-005 | No restoration after potions are exhausted | C3843 — Healing Attempt with Zero Potions | Covered |
| REQ-HEAL-006 | Potions replenish after level completion | C3839 — Full Resource Restoration on Level Completion | Covered |
| REQ-LVL-001 | Resources restore after level completion | C3839 — Full Resource Restoration on Level Completion | Covered |
| REQ-DEATH-001 | PC death is permanent during an expedition | C3850 — PC Permanent Death During Expedition | Covered |
| REQ-DEATH-002 | No resurrection on later expedition levels | C3851 — Persistence of PC Death Across Expedition Levels | Covered |
| REQ-DEATH-003 | New expedition restores all PCs | C3845 assumes all PCs are available but does not directly verify restoration | Partial |
| REQ-PERK-001 | One of three perks can be selected | C3854 — Standard Choice Presentation | Covered |
| REQ-PERK-002 | One perk reroll is available | C3855 — Perk Selection Reroll Functionality | Covered |
| REQ-PERK-003 | Perks can accumulate | C3861 — Perk Accumulation Limit | Covered |
| REQ-PERK-004 | Team perks apply to the team | C3856 — Team Perk Application | Covered |
| REQ-PERK-005 | PC-specific perks apply to one PC | C3857 — PC-Specific Perk Application | Covered |
| REQ-PERK-006 | Perks survive permanent PC death | C3858 — Expedition Persistence | Covered |
| REQ-PERK-007 | Perks persist across levels and expeditions | C3858 — Expedition Persistence | Covered |
| REQ-PERK-008 | Perks persist between game sessions | C3859 — Session Restart Persistence | Covered |
| REQ-PERK-009 | Perks rank up and leave the selection pool | C3860 — Perk Rank Up and Exclusion | Covered |
| REQ-MOVE-001 | Crouching while running triggers a slide | C3852, C3853 | Covered |

## Coverage Summary

| Status | Requirements |
|---|---:|
| Covered | 24 |
| Partial | 3 |
| Gap | 4 |
| **Total** | **31** |

The matrix shows why the 89.3% usable-case rate is not the same as complete requirement coverage. Four requirements have no retained test, while three have only partial coverage.
