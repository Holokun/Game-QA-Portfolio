# Deepward — PC Game QA Case Study

## Overview

This project documents a focused black-box QA exercise performed on **Deepward**, an early-playtest PC action shooter. The work covers exploratory testing, feature analysis, professional defect reporting, structured requirements, TestRail AI evaluation, and test-coverage analysis.

The case study is complete at the **exploration and test-design stage**. The generated TestRail suite was reviewed but not executed as a formal regression cycle.

## Project Snapshot

| Item | Details |
|---|---|
| Platform | PC |
| Game build | V0.1.7 BETA — Early Playtest Build |
| Test environment | Windows 11 Pro for Workstations, version 25H2 |
| Test period | September 2026 |
| Primary session | 30-minute exploratory test session |
| Approach | Black-box, exploratory, functional, negative, boundary, and state-transition analysis |
| Test-management tool | TestRail |

Full hardware and software details: [Test Environment](Environment.md)

## Portfolio Results

| Result | Value |
|---|---:|
| Exploratory sessions documented | 1 |
| Gameplay requirements prepared | 31 |
| TestRail AI cases generated | 28 |
| Cases retained after QA review | 25 |
| Cases accepted unchanged | 23 |
| Cases corrected by the tester | 2 |
| Cases rejected by the tester | 3 |
| Usable-case rate after review | 89.3% |
| Professional bug reports | 3 |
| Critical / Major / Minor bugs | 0 / 3 / 0 |

> The 25 retained cases were designed and reviewed; a complete formal execution cycle was not recorded for this case study.

## Key Deliverables

### Test Design and AI Evaluation

- [TestRail AI experiment report](AI-Experiments/TestRail-AI-Test-Case-Generation-Experiment.md)
- [Requirements used for generation](deepward-draft-requirements-for-testrail-ai-v4.md)
- [TestRail CSV export — 25 retained cases](deepward_playtest_testRailAi.csv)
- [Requirements-to-tests traceability matrix](Traceability-Matrix.md)

### Exploratory Testing and Defects

- [Exploratory session notes](exploratory-test.md)
- [Bug report summary](Bug-reports/bugs.md)
- [BUG-DW-001 — First standing kick does not consume stamina](Bug-reports/BUG-DW-001-first-kick-no-stamina-cost.md)
- [BUG-DW-002 — Repeated kick input consumes stamina without matching actions](Bug-reports/BUG-DW-002-kick-input-drains-extra-stamina.md)
- [BUG-DW-003 — Healing potion is consumed at full HP](Bug-reports/BUG-DW-003-potion-consumed-at-full-health.md)

### Product Analysis and Evidence

- [Feature map](feature-map.md)
- [UI documentation](UI/)
- [Evidence catalogue](Evidence/README.md)
- [Test summary and project closure](Test-Summary-Report.md)

## Skills Demonstrated

- Exploratory test-session design and note-taking
- Gameplay rule discovery
- Positive, negative, boundary, and state-transition test design
- Risk-based review of AI-generated test cases
- Professional bug reporting
- Requirements clarification and separation of defects from expected behavior
- Traceability and coverage-gap analysis
- Test evidence organisation
- Git-based portfolio documentation

## Main Finding

TestRail AI produced a high proportion of usable first drafts, but human QA review was necessary. Five of 28 generated cases required intervention: two contained incorrect expected results, while three were rejected for duplicate coverage, insufficient game-specific context, or low testing value.

The experiment supports using AI as a **test-design assistant**, not as the authority on expected product behavior.
