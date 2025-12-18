---
description: Simulate a new developer applying the project and identify improvements (Experience Audit).
---

This workflow simulates the experience of a developer adopting this project to ensure usability and accuracy of documentation.
It checks for broken installation paths, workflow inconsistencies, and prompt logic gaps.

## 1. Preparation

1.  Create a timestamped report file: `agents-artifacts/reports/simulation_report_[YYYYMMDD].md`.
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

1.  Read `AGENTS.md` (The Constitution) and `knowledge/workflow/workflow.md` (The Process).
2.  **Verify**:
    - Do all Roles mentioned in `AGENTS.md` appear in `workflow.md`?
    - Do all phases in `workflow.md` assign a specific Agent/Skill?
3.  **Report**: Log discrepancies to the report file.
    - _Example_: "@Debugger is in AGENTS.md but missing from Verification Phase in workflow.md".

## 4. Scenario Simulation (Mental Walkthrough)

Perform a "Mental Walkthrough" for the following scenarios. Read the relevant Prompt Files (`.github/prompts/*.prompt.md` or templates) to verify logic.

### Scenario A: New Feature

1.  **Requirement**: Check `requirements` skill.
    - Does it have a clear output template?
2.  **Design**: Check `design` skill.
    - Does it link to the correct architectural docs?
3.  **Implementation**: Check `implement` skill.
    - Does it strictly forbid spec changes (if required by `AGENTS.md`)?

### Scenario B: Specification Change

1.  **Trigger**: Simulate a Developer encountering a spec gap.
2.  **Escalation**: Check `AGENTS.md` rules.
    - Is there a clear prohibition ("Anti-Drift Lock") against on-the-fly changes?
    - Who is the authority? (@Architect).
3.  **Process**:
    - Does the workflow support returning to the "Design Phase"?

### Scenario C: Bug Fix

1.  **Debugging**: Check `debug` skill.
    - Does it require a reproduction step before fixing?
    - Where is the output saved (Artifacts vs Docs)?

### Scenario D: Refactoring (@Gardener)

1.  **Safety**: Check `refactor` skill.
    - Does it explicitly forbid business logic changes?
    - Does it mention updating documentation if the structure changes?

### Scenario E: Documentation Sync (@Librarian)

1.  **Drift Detection**: Check `check-doc-consistency` skill.
    - Does it trace links from `README.md` throughout the project?
    - Can it detect if `agents-docs/directory-structure.md` is outdated compared to the actual file tree?

**Report**: Log any friction points or ambiguity found during this walkthrough to the report file.

## 5. Finalize

1.  Summarize the top 3 critical issues found in the "Executive Summary" of the report.
2.  Suggest an `implementation_plan` if critical fixes are needed.
