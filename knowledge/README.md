# Knowledge Templates

This directory categorizes templates based on their usage in the [Standard Workflow](./workflows/workflow.md).

## Directory Structure

### 1. [Workflow Templates](./workflows/templates/)

Templates for **Process Management** (GitHub Issues).
These are used to create tickets that track work, progress, and decisions.

- **Location**: `knowledge/workflows/templates/`
- **Usage**: Copy content into GitHub Issue description.
- **Examples**:
  - `issue_requirement.md`: For Requirement Definition Issues.
  - `issue_design.md`: For Design Discussion Issues.
  - `test_sanity.md`: For reporting Sanity Test Results in an Issue.

### 2. [Artifact Templates](./templates/)

Templates for **Product Artifacts** (Git Assets).
These are used to create persistent files in the repository (`docs/`).

- **Location**: `knowledge/templates/`
- **Usage**: Copy content into a new `.md` file in `docs/` or `src/` and commit to Git.
- **Examples**:
  - `specification.template.md`: For creating `docs/specs/[feature]/spec.md`.
  - `design.template.md`: For creating `docs/specs/[feature]/design.md`.
  - `test_spec.template.md`: For creating `docs/specs/[feature]/test-specs/spec.md`.

### 3. [Guidelines](./guidelines/)

Guides and rules that define **"How we work"** in this project.
Refer to these documents for standards on quality, reviewing, and AI collaboration.

- **Location**: `knowledge/guidelines/`
- **Key Documents**:
  - `adoption-guide.md`: How to introduce Terraformer to a project.
  - `debugging.md`: The scientific method for debugging.
  - `pr-creation-guidelines.md`: Standards for submitting Pull Requests.
  - `software-review.md`: Checking points for code review.
  - `specification-guidelines.md`: How to write unambiguous specifications.
