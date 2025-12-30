[← Back to Workflow](./workflow.md)

# Feature Task Details

## Task List

1. [Spec Creation & Agreement](#1-spec-creation--agreement)
2. [Define Exit Criteria](#2-define-exit-criteria)
3. [Design](#3-design)
4. [Update Sanity Checklist](#4-update-sanity-checklist)
5. [Create Test Spec](#5-create-test-spec)
6. [Implementation & Tests](#6-implementation--tests)
7. [Run Sanity Tests](#7-run-sanity-tests)
8. [Run Feature Check](#8-run-feature-check)
9. [Verify Exit Criteria](#9-verify-exit-criteria)

---

### 1. Spec Creation & Agreement

**Deliverable**: Updated Specification (Git)

**Goal**: Clarify the requirements of the feature and form a common understanding within the team.

**Activities**:

- Clarify the purpose and background of the feature.
- Identify user stories and requirements.
- Create/Update specifications.
  - **Template**: [Specification Template](../templates/artifacts/specification.template.md)
- Reach agreement with the Product Owner.
- Manage specifications in Git.

**Checkpoints**:

- [ ] Verify using [Specification Template](../templates/artifacts/specification.template.md).
- [ ] See Issue Template for sign-off criteria.

---

### 2. Define Exit Criteria

**Deliverable**: Exit Criteria Document (Issue/Project Management Tool)

- **Template**: [Define Exit Criteria](../templates/issues/task_define_exit_criteria.md)

**Goal**: Clarify the criteria for story completion and ensure quality.

**Activities**:

- Define completion criteria based on specifications.
- List validation items.
- Create Exit Criteria document.

**Checkpoints**:

- [ ] Verify using [Define Exit Criteria](../templates/issues/task_define_exit_criteria.md).

### 3. Design

**Deliverable**: Updated Design Document (Git)

**Goal**: Clarify implementation direction and ensure quality and maintainability.

**Activities**:

- Technical design based on specifications.
- Architecture design.
- Interface design.
- Data model design.
- Design review.
- Team consensus.
- **Template**: [Design Template](../templates/artifacts/design.template.md)

**Important Notes**:

- If there are ambiguities or defects in the spec, **always confirm instead of guessing**.
- If spec revision or doc improvement is needed, **create a ticket**.

**Checkpoints**:

- [ ] Verify using [Design Template](../templates/artifacts/design.template.md).
- [ ] See Issue Template for review criteria.

---

### 4. Update Sanity Checklist

**Deliverable**: Updated Sanity Test Items

**Goal**: Keep the checklist up-to-date for easy system-wide checks before release.

**Activities**:

- Add/Update check items based on spec/design.
- Review existing items (remove obsolete, modify content).
- Update the checklist file.
  - **File**: `docs/tests/sanity.md`
  - **Issue Template**: [Update Sanity Checklist](../templates/issues/task_update_sanity_checklist.md)
- Commit to Git.

**Checkpoints**:

- [ ] Verify using [Update Sanity Checklist](../templates/issues/task_update_sanity_checklist.md).

---

### 5. Create Test Spec

**Deliverable**: Feature Implementation Verification Items (Issue)

**Goal**: Clarify criteria to judge the completion of feature implementation.

**Activities**:

- Create check items based on spec/design.
  - **Template**: [Test Spec](../templates/artifacts/test_spec.template.md)
  - **Issue Template**: [Create Test Spec](../templates/issues/task_create_test_spec.md)
- Define normal and abnormal test cases.
- Define boundary value tests.

**Checkpoints**:

- [ ] Verify using [Create Test Spec](../templates/issues/task_create_test_spec.md).

---

### 6. Implementation & Tests

**Deliverable**: Source Code, Test Code (Git)

**Goal**: Implement functionality based on design and ensure quality.

**Activities**:

- Implementation based on design.
- Creation of unit tests.
  - **Template**: [Implementation Task](../templates/issues/task_implementation.md)
- Code review.
- Continuous Integration.

**Implementation Principles**:

- **Large volume**: Split tickets appropriately.
- **Splitting tickets**: Consider introducing skeleton classes first.
- **Breaking changes**: Create a feature branch (never leave main branch in broken state).

**Checkpoints**:

- [ ] Verify using [Implementation Task](../templates/issues/task_implementation.md).

---

### 7. Run Sanity Tests

**Deliverable**: Sanity Test Results (Issue)

**Goal**: Perform a quick system-wide check to ensure no regression.

**Activities**:

- Operation check based on updated Sanity Checklist.
  - **Checklist**: `docs/tests/sanity.md`
- Record results (Ticket Comment).
  - **Template**: [Sanity Test Task](../templates/issues/task_test_sanity.md)

**Checkpoints**:

- [ ] Verify using [Sanity Test Task](../templates/issues/task_test_sanity.md).

---

### 8. Run Feature Check

**Deliverable**: Feature Implementation Verification Results (Issue)

**Goal**: Confirm the completion of feature implementation.

**Activities**:

- Operation check based on created check items.
- Record results (Ticket Comment).
  - **Template**: [Functional Test Task](../templates/issues/task_test_functional.md)

**Checkpoints**:

- [ ] Verify using [Functional Test Task](../templates/issues/task_test_functional.md).

---

### 9. Verify Exit Criteria

**Deliverable**: Verification Record on Project Management Tool

**Goal**: Confirm that the story meets the completion criteria.

**Activities**:

- Final check based on Exit Criteria document.
  - **Template**: [Verify Exit Criteria](../templates/issues/task_verify_exit_criteria.md)
- Verification of all deliverables.
- Record confirmation results as a comment on the ticket.

**Checkpoints**:

- [ ] Verify using [Verify Exit Criteria](../templates/issues/task_verify_exit_criteria.md).
