# Deliverables List

[← Back to Workflow](./workflow.md)

In this project, we strictly separate "GitHub Issues (Process/Log)" and "Git Repository (Product Assets)" depending on the nature of the deliverable.

## Management Principles

- **Issue**: The history of "Why it happened", discussions, temporary check results, work logs. (Flow)
- **Git**: The definition of "What it is", specifications, designs, code, persistent documentation. (Stock)

## Deliverables Matrix

| Phase              | Deliverable Name               | Location  | Template                       | Description                                                                                       |
| :----------------- | :----------------------------- | :-------- | :----------------------------- | :------------------------------------------------------------------------------------------------ |
| **1. Requirement** | Requirement Definition (Issue) | Issue     | `issue_requirement.md`         | Purpose, Context, Scope, and discussion/agreement on Acceptance Criteria.                         |
| **2. Design**      | Design Discussion Record       | Issue     | `issue_design.md`              | Architecture selection, trade-off considerations, design review history.                          |
|                    | **Functional Spec**            | **Git**   | `specification.template.md`    | Confirmed functional specifications. Reflects Issue discussions and must be kept up-to-date.      |
|                    | **Technical Design**           | **Git**   | `design.template.md`           | Confirmed system design, API definitions, DB schema, etc.                                         |
|                    | **Test Spec**                  | **Git**   | `test_spec.template.md`        | Functional test cases (procedures/expected results). Saved in `docs/specs/[Feature]/test-specs/`. |
| **3. Impl**        | Source Code                    | Git       | N/A                            | Product code under `src/`.                                                                        |
|                    | Test Code                      | Git       | N/A                            | Automated test code under `tests/`.                                                               |
|                    | Pull Request                   | Git (PR)  | `pull_request.md`              | Code change proposals, reviews, CI results.                                                       |
|                    | **Sanity Checklist**           | **Git**   | `sanity_checklist.template.md` | Project-wide master list of sanity test items.                                                    |
| **4. Verify**      | Sanity Test Result             | Issue     | `test_sanity.md`               | Results executed based on the list in Git.                                                        |
|                    | Functional Test Result         | Issue     | `test_functional.md`           | Results executed based on test cases in Git.                                                      |
|                    | **Exit Criteria Check**        | Issue     | `issue_exit_criteria.md`       | Final check to see if release criteria are met.                                                   |
| **5. Release**     | Release Notes                  | Git (Rel) | N/A                            | Summary of changes per version.                                                                   |
|                    | CHANGELOG.md                   | Git       | N/A                            | History file.                                                                                     |

## Persistence of Artifacts

Although Issues are searchable after being closed, the "Source of Truth" for the project must always be reflected in Git.
For example, if a "Specification Change" is discussed in an Issue, the discussion remains in the Issue, but the **Decision must be merged into the Specification (`docs/specs/`) on Git**.
AI supports this "Distillation of information from Issue to Git".
