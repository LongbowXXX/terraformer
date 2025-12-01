---
description: Maintain and update project documentation for LLMs
---

# Project Documentation Maintenance Assistant

You are an expert in maintaining software project architecture documentation.
Leverage Antigravity tools to efficiently understand the project and create/update comprehensive and accurate documentation.

## Objective

In large-scale projects, to ensure AI agents correctly understand the design and make appropriate modifications, maintain the following documentation:

1.  **Architecture Overview** - System composition and design philosophy
2.  **Directory Structure Guide** - Responsibilities and dependencies of each module
3.  **Design Principles and Patterns** - Coding conventions and design patterns
4.  **Key Flows Explanation** - Processing flows of important use cases
5.  **Tech Stack and Dependencies** - Technologies used and external integrations
6.  **Testing Strategy and Guide** - Test configuration, execution methods, and best practices
7.  **Technical Constraints and Gotchas** - Performance, security, and known issues

## Execution Steps

### Step 1: Project Analysis

First, use the following tools to grasp the overall picture of the project:

1.  **Identify Entry Points**
    -   Use `list_dir` to check files in the root directory.
    -   Look for main files like `main.py`, `index.ts`, `App.tsx`.
    -   Use `view_file` to read package manager settings (`package.json`, `pyproject.toml`, `pom.xml`, etc.).

2.  **Understand Directory Structure**
    -   Use `list_dir` recursively (or on major subdirectories) to understand the structure.
    -   Identify the roles of `src/`, `lib/`, `tests/`, etc.

3.  **Check Dependencies**
    -   Identify frameworks and libraries from configuration files or import statements in source code.
    -   Look for traces of integration with external services (API, database, etc.).

4.  **Check Existing Documentation**
    -   Use `list_dir` to search for `docs/` or `agents-docs/`.
    -   Use `view_file` to read `README.md`, `ARCHITECTURE.md`.

### Step 2: Documentation Generation

Create the following documents in the `agents-docs/` directory.
Use the `write_to_file` tool. If the directory does not exist, it will be created automatically.

Always add the following comment to the beginning of each document:

```markdown
<!-- This document is generated/updated by the sync-doc workflow -->
```

#### 1. `agents-docs/architecture.md` - Architecture Overview

```markdown
<!-- This document is generated/updated by the sync-doc workflow -->

# Architecture Overview

## System Overview

[Project purpose and overall picture]

## Key Components

[Major elements constituting the system and their responsibilities]

## Architecture Diagram

[Component diagram or sequence diagram using Mermaid, etc.]

## Data Flow

[How data flows within the system]

## Design Background and Rationale

[Why this architecture was chosen]
```

#### 2. `agents-docs/directory-structure.md` - Directory Structure Guide

```markdown
<!-- This document is generated/updated by the sync-doc workflow -->

# Directory Structure Guide

## Overall Configuration

[Overview of the directory tree]

## Responsibilities of Each Directory

### `/src/components/`

- **Role**: [Description]
- **Key Files**: [List]
- **Dependencies**: [Relationship with other modules]

[Describe similarly for each directory]

## Module Dependency Diagram

[Visualize dependencies using Mermaid]

## Layer Structure

[Presentation layer, business logic layer, data access layer, etc.]
```

#### 3. `agents-docs/coding-conventions.md` - Design Principles and Patterns

```markdown
<!-- This document is generated/updated by the sync-doc workflow -->

# Design Principles and Coding Conventions

## Design Principles

[SOLID principles, DRY, YAGNI, etc., principles emphasized in the project]

## Adopted Design Patterns

[Factory, Strategy, Observer, etc., patterns actually used]

## Naming Conventions

- File names: [Rule]
- Class names: [Rule]
- Function names: [Rule]
- Variable names: [Rule]

## Code Style

[Formatter, linter settings and conventions]

## Testing Policy

[How to write tests, coverage goals, etc.]
```

#### 4. `agents-docs/key-flows.md` - Key Flows Explanation

```markdown
<!-- This document is generated/updated by the sync-doc workflow -->

# Key Feature Flows

## Entry Point

[Application startup flow and initialization process]

## Use Case 1: [Feature Name]

### Overview

[What the feature does]

### Sequence Diagram

[Sequence diagram using Mermaid]

### Related Files

- `path/to/file1.py` - [Role]
- `path/to/file2.py` - [Role]

### Processing Flow

1. [Step 1]
2. [Step 2]
   ...

[Describe similarly for other major use cases]
```

#### 5. `agents-docs/tech-stack.md` - Tech Stack and Dependencies

```markdown
<!-- This document is generated/updated by the sync-doc workflow -->

# Tech Stack and Dependencies

## Major Tech Stack

- **Language**: [Version]
- **Framework**: [Name and Version]
- **Database**: [Type and Version]

## Major Dependencies

| Library | Version | Usage |
| ------- | ------- | ----- |
| [Name]  | [Version] | [Description] |

## Integration with External Services

- **[Service Name]**: [Usage and API Endpoint]

## Development Tools

- Build Tool: [Name]
- Test Framework: [Name]
- CI/CD: [Name]
```

#### 6. `agents-docs/testing.md` - Testing Strategy and Guide

```markdown
<!-- This document is generated/updated by the sync-doc workflow -->

# Testing Strategy and Guide

## Test Configuration

[Structure of test directory and placement of test files]

## Types of Tests

### Unit Tests

[Unit testing policy, usage of mocks/stubs]

### Integration Tests

[Scope and execution method of integration tests]

### E2E Tests

[Target and execution method of end-to-end tests]

## Test Execution Method

[Test commands, environment settings, execution in CI/CD]

## Coverage Goals

[Coverage target values and measurement methods]

## Test Data Management

[Creation and management of fixtures and test data]

## Testing Best Practices

[Naming conventions, how to write test cases, notes]

## Common Testing Issues and Solutions

[Problems encountered during test execution and troubleshooting]
```

#### 7. `agents-docs/constraints-and-gotchas.md` - Technical Constraints and Gotchas

```markdown
<!-- This document is generated/updated by the sync-doc workflow -->

# Technical Constraints and Gotchas

## Performance Requirements

[Requirements for response time, throughput, etc.]

## Security Considerations

[Authentication, authorization, data protection, etc.]

## Known Technical Debt

[Parts requiring refactoring and reasons]

## Common Troubles and Solutions

[Problems likely to be encountered during development and their solutions]

## Constraints

[Technical limitations, license constraints, etc.]
```

### Step 3: Consistency Check with Implementation

Verify that the generated documentation matches the implementation:

1.  **Check against Code**
    -   Use `view_file` to check the generated documentation and compare it with the actual file structure and code.

2.  **Check Recency**
    -   Confirm that recent changes are reflected in the documentation.

3.  **Evaluate Completeness**
    -   Confirm that all major features are covered.

### Step 4: Maintenance Guidelines Proposal

Propose the following to prevent documentation from diverging from implementation:

1.  **Timing of Documentation Updates**
2.  **Review Process**
3.  **Automation Proposals**

## Output Format

Finally, create/update the following deliverables:

1.  Each documentation file under `agents-docs/`
2.  Summary of execution results (which files were updated, issues found, etc.)

## Usage Example

```
/sync-doc
```

When this workflow is executed, Antigravity will systematically analyze the project and automatically generate/update the necessary documentation in the `agents-docs/` directory.
