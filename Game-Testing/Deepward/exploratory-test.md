# Deepward — Exploratory Testing Session Notes

## Session Charter

Explore the core gameplay loop and build an initial model of character switching, resources, healing, death, perks, movement, and targeting behavior. Record confirmed observations, unclear behavior, and candidate defects for later formalisation.

| Item | Details |
|---|---|
| Duration | 30 minutes |
| Method | Black-box exploratory testing |
| Platform | PC, keyboard and mouse |
| Build | V0.1.7 BETA — Early Playtest Build |
| Tester | Vadim Lebedev |

## Observed Gameplay Behavior

### Targeting

1. The crosshair becomes red when aimed at an enemy.
2. The crosshair also becomes red when aimed at some light-source objects.

Evidence:

- [Crosshair in its normal state](Evidence/screenshots/2026-09-27/target-common.png)
- [Crosshair aimed at a light-source object](Evidence/screenshots/2026-09-27/target-on-light.png)

### Player Characters and Switching

3. Three Player Characters (PCs) are available and mapped to the number keys `1`, `2`, and `3`.
4. After switching away from a PC, that PC cannot be selected again for approximately three seconds.
5. Switching away from a PC starts ammunition recovery. The PC's ammunition returns to maximum and a blinking recovery indicator appears beside the portrait.
6. An inactive PC continues to recover stamina.
7. Ability cooldowns also continue while that PC is inactive.
8. Switching away while sliding or jumping resets the previous PC to a standing state.
9. Switching back to that PC does not resume the interrupted slide or jump.

### Healing and Resources

10. Healing requires the player to hold `H` continuously for several seconds.
11. A short cooldown occurs between potion uses.
12. Healing cannot begin when the potion count is zero.
13. During an active level, potions were the only observed way to restore HP.
14. Completing a level restores HP, sanity, stamina, ammunition, ability availability, and healing potions.

### Death and Expedition State

15. PC death is permanent for the remainder of the current expedition.
16. A dead PC does not return on later levels of the same expedition.
17. Starting a new expedition restores all PCs.

### Perks and Progression

18. Completing a level presents one perk choice from three random options.
19. The player receives one reroll for the three offered perks.
20. Perks accumulate and persist after a PC dies.
21. Perks were observed to persist across expeditions and game sessions.

### Movement

22. Pressing crouch while running triggers a slide.

## Candidate Defects Raised

- [BUG-DW-001 — First standing kick does not consume stamina](Bug-reports/BUG-DW-001-first-kick-no-stamina-cost.md)
- [BUG-DW-002 — Repeated kick input consumes stamina without matching actions](Bug-reports/BUG-DW-002-kick-input-drains-extra-stamina.md)
- [BUG-DW-003 — Healing potion is consumed at full HP](Bug-reports/BUG-DW-003-potion-consumed-at-full-health.md)

## Session Outcome

The session produced enough information to prepare 31 draft gameplay requirements and run an AI-assisted test-design experiment in TestRail. Observations were treated as provisional until clarified; candidate defects were kept separate from expected behavior.
