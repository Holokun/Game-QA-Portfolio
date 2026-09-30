# Deepward — TestRail AI Test Case Generation Evaluation

## Executive Summary

This case study evaluates TestRail AI as a test-design assistant for **Deepward**, a PC action shooter in early playtest. The experiment began with a 30-minute exploratory testing session. The observed gameplay rules were then converted into structured draft requirements and supplied to TestRail AI.

TestRail AI generated **28 test cases**. After manual QA review:

| Review outcome | Cases | Percentage |
|---|---:|---:|
| Accepted without changes | 23 | 82.1% |
| Accepted after editing | 2 | 7.1% |
| Rejected | 3 | 10.7% |
| **Usable after review** | **25** | **89.3%** |

The result demonstrates that AI can produce a strong first draft from structured requirements, but it cannot be treated as the source of truth. Human review prevented two incorrect expected results, removed duplicate and low-value coverage, and identified a case that lacked enough game-specific context.

> **Conclusion:** TestRail AI was effective as a test-case drafting accelerator. Human QA judgment remained essential for validating game behavior, deciding test value, and assessing coverage.

---

## Project Context

| Item | Details |
|---|---|
| Product | Deepward |
| Platform | PC, Windows 11 |
| Build | V0.1.7 BETA — Early Playtest Build |
| Experiment date | September 28, 2026 |
| Testing approach | Black-box exploratory and functional testing |
| AI tool evaluated | TestRail AI test-case generation |
| Human reviewer | Vadim Lebedev |

The source information was based on observed behavior rather than an official game design specification. Requirements were therefore written as draft validation targets, with unclear behavior separated into clarification items instead of being presented as confirmed rules.

## Objective

The experiment was designed to answer four questions:

1. Can TestRail AI convert structured gameplay requirements into usable test cases?
2. How much of the generated output can be accepted without modification?
3. What kinds of errors require human intervention?
4. Does a high acceptance rate also mean that the generated suite has sufficient coverage?

## Experiment Workflow

```text
30-minute exploratory session
            ↓
Raw gameplay observations and candidate defects
            ↓
ChatGPT-assisted requirement structuring
            ↓
Human clarification and requirement review
            ↓
TestRail AI test-case generation
            ↓
Human QA review: accept, edit, or reject
            ↓
25 retained cases exported from TestRail
```

This was an **AI-assisted QA pipeline**, not an isolated evaluation of TestRail AI. AI was used in both requirement preparation and test generation, while the tester remained responsible for observation, clarification, validation, and final acceptance.

## Input Quality and Controls

The TestRail AI input contained:

- **31 gameplay requirements**;
- **2 unresolved clarification items**;
- **3 candidate defects**, explicitly marked as defects rather than expected behavior;
- instructions not to invent undocumented rules;
- consistent terminology for the three Player Characters (PCs);
- requests for positive, negative, boundary, state-transition, and persistence coverage where appropriate.

These controls were intended to reduce hallucinated behavior and keep the generated cases traceable to observed mechanics.

## Results

### Review Metrics

- **Unchanged acceptance rate:** 23 / 28 = **82.1%**
- **Edited rate:** 2 / 28 = **7.1%**
- **Rejected rate:** 3 / 28 = **10.7%**
- **Usable-case rate after review:** 25 / 28 = **89.3%**
- **Cases requiring human intervention:** 5 / 28 = **17.9%**

The current CSV export contains all **25 retained cases**, which matches the accepted-plus-edited total.

### Retained Coverage by Area

| Functional area | Retained cases |
|---|---:|
| Abilities and stamina recovery | 2 |
| Level and resource recovery | 2 |
| Healing and potions | 4 |
| Character switching and state reset | 5 |
| Death and expedition state | 2 |
| Movement and sliding | 2 |
| Perks and progression | 8 |
| **Total** | **25** |

The retained suite covers positive behavior, negative conditions, cooldowns, state transitions, persistence, and progression. Examples include switching back before and after cooldown, healing with zero potions, restoring resources after level completion, preserving permanent death across levels, and perk persistence between sessions.

## Human Review Findings

### Edited Cases

Two cases contained an **incorrect expected result** and were corrected during review:

1. **Resource Recovery During Game Pause**
2. **Healing Attempt with Zero Potions**

These were logic errors rather than formatting problems. Both cases appeared complete and professionally written, but a plausible-looking expected result did not accurately reflect the intended game behavior.

This is the experiment's most important risk finding: an incorrect expected result can cause correct behavior to be reported as a defect or a genuine defect to be marked as a pass.

### Rejected Cases

Three generated cases were rejected for different reasons:

| Rejection reason | Cases | QA significance |
|---|---:|---|
| Unnecessary case | 1 | A technically valid case may still have low testing value. |
| Missing game-specific context | 1 | Generic assumptions are unsafe when the game rule is not sufficiently defined. |
| Duplicate coverage | 1 | Rewording an existing scenario increases maintenance without increasing coverage. |

The review demonstrates that test-case quality is not determined by structure alone. A useful case must also be correct, relevant, non-duplicative, and worth its execution and maintenance cost.

## What TestRail AI Did Well

- Converted structured requirements into readable, executable test cases.
- Produced clear steps and expected results for most scenarios.
- Generated useful state-transition and persistence coverage.
- Covered several negative and boundary conditions.
- Reduced the effort of starting from an empty test suite.
- Produced an **89.3% usable-case rate after review** in this experiment.

## Where Human QA Was Essential

- Verifying expected behavior against the tester's understanding of the game.
- Correcting plausible but inaccurate expectations.
- Rejecting duplicate and low-value cases.
- Recognizing when the AI lacked Deepward-specific context.
- Separating candidate defects from expected behavior.
- Evaluating risk, execution value, and maintainability.
- Identifying important tests that were not generated at all.

## Coverage Observation

A high acceptance rate does **not** prove complete coverage. For example, the retained CSV does not contain explicit cases for the crosshair feedback requirements, even though those requirements were included in the source document.

This does not automatically mean TestRail AI failed—the relevant cases may have been rejected or excluded for another reason—but it identifies a coverage question that must be checked manually. The next evaluation should map every retained test case back to its source requirement and record requirements with no coverage.

## Limitations

- The requirements were derived from exploratory observations, not official developer specifications.
- This was one generation run against one feature set, so the percentages should not be generalized to every project.
- The rejected case contents were not retained in the current CSV export; only their review reasons were recorded.
- Test-generation time and manual editing time were not measured, so this experiment does not claim a quantified time saving.
- Acceptance rate measures output quality, not completeness of coverage or defect-detection effectiveness.
- The retained cases have not yet been evaluated here through a complete execution cycle.

## Portfolio Takeaway

This experiment demonstrates an end-to-end AI-assisted QA workflow:

- exploratory product investigation;
- conversion of observations into structured requirements;
- careful separation of requirements, unknowns, and candidate defects;
- AI-assisted test generation;
- critical human review of every generated case;
- quantitative evaluation of AI output;
- analysis of AI failure modes and remaining coverage risk.

The strongest result is not simply that TestRail AI generated 28 cases. It is that the output was reviewed as QA work rather than accepted as AI content: **23 cases were accepted, 2 logic errors were corrected, and 3 unsuitable cases were rejected**.

## Recommended Next Experiment

1. Create a requirement-to-test traceability matrix.
2. Identify requirements and risk areas missing from the generated suite.
3. Execute the 25 retained cases and record pass/fail results and discovered defects.
4. Measure generation, review, editing, and manual authoring time.
5. Compare two equivalent inputs:
   - raw human-written observations sent directly to TestRail AI;
   - the same observations structured and clarified with ChatGPT first.
6. Compare acceptance rate, incorrect expectations, duplicates, missing coverage, and total review effort.

## Project Evidence

- [Exploratory testing notes](../exploratory-test.md)
- [Structured requirements supplied to TestRail AI](../deepward-draft-requirements-for-testrail-ai-v4.md)
- [TestRail export containing the 25 retained cases](../deepward_playtest_testRailAi.csv)
- [Candidate defects discovered during exploration](../Bug-reports/bugs.md)

