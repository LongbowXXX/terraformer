---
description: Simulate a new developer applying the project and identify improvements (Experience Audit).
---

This workflow simulates the experience of a developer adopting this project to ensure usability and accuracy of documentation.
It checks for broken installation paths, workflow inconsistencies, and prompt logic gaps.

## 1. Preparation

1.  Create a timestamped report file: `docs/specs/reports/simulation_report_[YYYYMMDD].md`.
    - Initialize it with a Header and "Executive Summary" section (to be filled at the end).
    - Create a "1. Project Overview & Installation" section.

## 2. ROOT README & Installation Check

1.  Read `README.md`.
2.  Extract the **Installation Commands** (e.g., `git clone`, `cp`, `npm install`).
3.  **Verify**: explicitly check if the source files/folders referenced in the commands actually exist in the current workspace.
    - _Example_: If `cp folder/foo .` is requested, check if `folder/foo` exists.
4.  **Report**: Log the findings to the report file.
    - ✅ PASS: Command references valid paths.
    - ❌ FAIL: Path [X] does not exist. (Propose Fix)

## 3. Workflow & Roles Consistency Check

1.  Read `AGENTS.md` (The Constitution) and `knowledge/workflows/workflow.md` (The Process).
2.  **Verify**:
    - Do all Roles mentioned in `AGENTS.md` appear in `workflow.md`?
    - Do all phases in `workflow.md` assign a specific Agent/Skill?
3.  **Report**: Log discrepancies to the report file.
    - _Example_: "@Debugger is in AGENTS.md but missing from Verification Phase in workflow.md".

## 4. Scenario Simulation (Mental Walkthrough)

Perform a "Mental Walkthrough" for the following scenarios.
**CRITICAL**: Do NOT check against a static list. You must **Dynamically Trace** the path from Workflow to Skill to Template.

### Verification Loop (For Each Step)

1.  **Discovery**: Read `knowledge/workflows/workflow.md` (and `AGENTS.md`) to identify the **Rule** and **Skill**.
2.  **Trace**: Read the **Skill Prompt** (e.g., `.github/prompts/*.prompt.md`) to find the referenced **Template**.
3.  **Existence Check**: Verify that the specific Template file exists at the path referenced in the Prompt.
4.  **Usability Check (Worker's Perspective)**: Read the Template content.
    - **Clarity**: Is it clear what to fill in?
    - **Consistency**: Does it align with the Skill's instructions?
    - **Placeholders**: Are `{{PLACEHOLDER}}` markers intuitive?
    - **Links**: Do references to Guidelines work?

### Scenario A: New Feature

1.  **Instruction**: Simulate the **Feature Story** flow defined in `knowledge/workflows/workflow.md`.
2.  **Meta-Check**: Dynamically identify every Task and Artifact required by the WBS in the workflow.
3.  **Action**: For each identified step, trace the Skill to its Template and verify consistent existence and usability.

### Scenario B: Specification Change

1.  **Instruction**: Simulate a specification change request during implementation.
2.  **Meta-Check**: Consult `AGENTS.md` and `workflow.md` for "Drift Prevention" rules.
3.  **Action**: Verify if the workflow effectively prohibits unauthorized changes and provides a restart path.

### Scenario C: Bug Fix

1.  **Instruction**: Simulate the **Bug Fix Story** flow defined in `knowledge/workflows/workflow.md`.
2.  **Meta-Check**: Verify that the templates discovered via the `debug` skill enforce the **Scientific Method** (Observation -> Hypothesis -> Experiment).

### Scenario D: Refactoring (@Gardener)

1.  **Instruction**: Simulate a Refactoring task using the `refactor` skill.
2.  **Meta-Check**: Verify that the skill prompt instructions explicitly forbid business logic changes.

## 5. Finalize

1.  Summarize the top 3 critical issues found in the "Executive Summary" of the report.
2.  Suggest an `implementation_plan` if critical fixes are needed.
