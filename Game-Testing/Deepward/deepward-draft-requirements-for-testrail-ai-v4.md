# DEEPWARD — Draft Gameplay Requirements for TestRail AI

## Purpose

This document is a **draft requirements source** for generating test cases in TestRail AI.

The requirements below are based only on behavior observed during exploratory testing and subsequent tester clarification.

Where behavior is based on observation rather than formal developer specifications, TestRail AI should generate validation tests without assuming undocumented implementation details.

### Instructions for TestRail AI

- Generate test cases only from the requirements listed below.
- Do not invent game rules that are not described here.
- Treat items in **Open Questions / Clarifications Needed** as unresolved.
- Do not treat the **Known Candidate Defects** section as expected behavior.
- Include positive, negative, boundary, state-transition, and persistence/state-recovery tests where the requirement supports them.
- Prefer clear preconditions, steps, and expected results.
- If a requirement is ambiguous, create a clarification item instead of assuming the intended behavior.

## Terminology

- **PC = Player Character**
- In this document, **PC** means a playable character controlled by the player.
- Use **PC** consistently in generated test cases when referring to one of the three playable characters.

---

# 1. Targeting and Crosshair

## REQ-TGT-001 — Crosshair feedback on enemies

When the player's crosshair is aimed at an enemy, the crosshair becomes red.

## REQ-TGT-002 — Crosshair feedback on light-source objects

When the player's crosshair is aimed at objects related to lighting/light sources, the crosshair becomes red.

Observed evidence labels:
- `target-common`
- `target-on-light`

---

# 2. Player Characters (PCs) and PC Switching

## REQ-CHAR-001 — Three Player Characters (PCs)

Three Player Characters (PCs) are available during gameplay.

## REQ-CHAR-002 — PC selection keys

The active PC can be switched using the corresponding keyboard number keys:

- `1`
- `2`
- `3`

## REQ-CHAR-003 — Switch-back cooldown

After switching away from a PC, that previous PC has a cooldown of exactly 3 seconds.

During this 3-second cooldown, the player cannot switch back to that PC.

## REQ-CHAR-004 — Previous PC ammunition recovery

After switching away from a PC:

- the previous PC's ammunition enters a recovery/reload state;
- the ammunition is restored to maximum;
- a blinking reload/recovery symbol appears to the right of that PC's icon.

## REQ-CHAR-005 — PC state after switching during slide or jump

If the player switches to another PC while the current PC is sliding or jumping, the PC that was switched away from is standing.

When the player later switches back to that previous PC, that PC is also standing rather than continuing the previous slide or jump.

---

# 3. Abilities and Cooldowns

## REQ-ABL-001 — PC abilities

Each PC has an ability.

## REQ-ABL-002 — Ability cooldown duration

Each ability has its own cooldown duration.

## REQ-ABL-003 — Cooldown recovery while inactive

Ability cooldowns continue recovering even when the player is currently controlling another PC.

---

# 4. Stamina

## REQ-STM-001 — Stamina recovery while inactive

A PC's stamina gradually recovers even when the player is currently controlling another PC.

---

# 5. Healing and Potions

## REQ-HEAL-001 — Healing requires held input

Using a healing potion takes time.

The player must continuously hold the healing input for several seconds to start/complete the health recovery process.

## REQ-HEAL-002 — Potion reuse cooldown

There is a short cooldown between potion uses.

## REQ-HEAL-003 — No healing when potion count is zero

If the number of available healing potions is `0`, the player cannot heal using a potion.

## REQ-HEAL-004 — Health restoration during an active level

During an active level, healing potions are the only observed way to restore lost HP.

No other health-restoration method has been observed during an active level.

## REQ-HEAL-005 — No health restoration after potions are exhausted

If the player's healing-potion count reaches `0` during a level, the player cannot restore lost HP until the level is completed.

## REQ-HEAL-006 — Potion replenishment

Healing potions are replenished when the player completes a level.

No method for replenishing healing potions during an active level has been observed.

---

# 6. Level Completion and Resource Restoration

## REQ-LVL-001 — Resource restoration after completing a level

After completing a level, the following are restored:

- HP;
- sanity;
- stamina;
- ammunition;
- abilities;
- healing potions.

---

# 7. PC Death and Expedition State

## REQ-DEATH-001 — Permanent death during an expedition

A PC can die permanently during a level.

## REQ-DEATH-002 — No resurrection on later levels of the same expedition

A PC who dies permanently cannot be resurrected on subsequent levels.

## REQ-DEATH-003 — New expedition restores PCs

At the beginning of a new expedition/game, all PCs are alive again.

---

# 8. Perks and Progression

## REQ-PERK-001 — Perk selection after level completion

After completing a level, the player receives one perk selection.

The player chooses one perk from three randomly offered perks.

## REQ-PERK-002 — Perk reroll

The player has one reroll that replaces/rerolls all three offered perks.

## REQ-PERK-003 — Perks can accumulate

Previously acquired perks remain active when additional perks are obtained.

The UI can show multiple owned perks at the same time.

## REQ-PERK-004 — Team perks

Some perks are classified as **Team Perks**.

A Team Perk applies to the team rather than being limited to one specific PC.

Examples visible in the observed perk UI include:

- Vitality;
- Iron Mind;
- Quick Hands;
- Endurance;
- Quick Recovery.

## REQ-PERK-005 — PC-specific perks

Some perks are associated with a specific PC rather than the whole team.

For example, the observed **Groundbreaker** perk is associated with the PC **Bruno**.

## REQ-PERK-006 — Perks persist after permanent PC death

Acquired perks do not disappear when a PC permanently dies.

## REQ-PERK-007 — Perks persist across levels and expeditions

Once a perk has been acquired, it remains active on later levels and in later expeditions.

Starting a new expedition does not reset acquired perks.

## REQ-PERK-008 — Perks persist between game sessions

Acquired perks persist after closing and relaunching the game.

The observed persistence is stored locally and remains until the local game data is removed, such as by reinstalling/resetting the game installation or its saved progression data.

## REQ-PERK-009 — Perk rank progression

Perks can have rank/tier indicators such as `I` and `II`.

After the player has acquired rank `I` of a perk, the same rank `I` cannot be acquired again.

A higher rank, such as `II`, can become available later.

This means perk progression uses higher-rank versions rather than repeated acquisition of the exact same rank.

---

# 9. Movement

## REQ-MOVE-001 — Slide input

Pressing the crouch input while running causes the active PC to slide.

---

# 10. Open Questions / Clarifications Needed

The exact PC-switch cooldown is now confirmed as 3 seconds.

## CLAR-001 — Maximum perk rank

It is currently unknown whether every perk supports multiple ranks.

It is also unknown what the maximum rank is for each perk.

Do not invent a maximum rank.

## CLAR-002 — Perk effect scaling between ranks

It is currently unknown exactly how a perk's numerical effect changes between ranks.

For example, it has not been verified whether rank `II` doubles the effect of rank `I`.

Do not assume a `×2` scaling rule unless it is confirmed through further testing or formal requirements.

---

# 11. Known Candidate Defects — Do NOT Treat as Requirements

The following behaviors were observed as possible defects and should be tested separately.

## CANDIDATE-BUG-001 — First standing kick may not consume stamina

Professional report: [BUG-DW-001](Bug-reports/BUG-DW-001-first-kick-no-stamina-cost.md)

Observed behavior:

The first standing kick did not consume stamina.

This requires reproduction and verification before being treated as a confirmed defect.

## CANDIDATE-BUG-002 — Repeated kick input may consume stamina without executing kicks

Professional report: [BUG-DW-002](Bug-reports/BUG-DW-002-kick-input-drains-extra-stamina.md)

Observed behavior:

The player can rapidly spam the kick input.

During rapid input:

- stamina can be consumed very quickly;
- many kick inputs may be registered;
- only a small number of actual kick actions/animations occur.

Example observation:

Approximately 20 kick inputs were made, while only about 2 kicks were visibly executed, but stamina was still depleted rapidly.

This requires focused testing of:

- input buffering;
- stamina deduction timing;
- kick cooldown/state validation;
- behavior during the kick animation.

## CANDIDATE-BUG-003 — Potion can be used at full HP

Professional report: [BUG-DW-003](Bug-reports/BUG-DW-003-potion-consumed-at-full-health.md)

Observed behavior:

A healing potion can be used while the active PC already has full HP.

Clarification/testing is required to determine:

- whether the potion is consumed;
- whether this is intended design;
- whether any effect occurs at full HP.

---

# 12. Suggested TestRail AI Generation Scope

For the first generated suite, create test cases for these feature groups:

1. PC switching
2. PC switch cooldown
3. Ammunition recovery after switching
4. Ability cooldown recovery
5. Stamina recovery
6. Healing input behavior
7. Potion cooldown
8. Zero-potion behavior
9. Health restoration when potions are exhausted
10. Potion replenishment after level completion
11. Level-completion resource restoration
12. Permanent PC death
13. PC state at new expedition
14. Perk selection and reroll
15. Team perks
16. PC-specific perks
17. Perk accumulation
18. Perk persistence across levels
19. Perk persistence across expeditions
20. Perk persistence after game restart
21. Perk rank progression from `I` to higher ranks
22. Prevention of reacquiring the same perk rank
23. Slide behavior
24. PC state when switching during slide/jump
25. Crosshair color/state feedback

For each applicable requirement, generate:

- normal/positive tests;
- negative tests;
- boundary tests;
- state-transition tests;
- repeated-input tests;
- persistence/recovery tests.

Do not generate expected outcomes for unresolved clarification items.
