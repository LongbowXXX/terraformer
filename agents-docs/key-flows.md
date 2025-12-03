<!-- This document is generated/updated by the sync-doc workflow -->

# Key Feature Flows

## Entry Point

The primary entry point for using Terraformer is the **GitHub Copilot Chat** interface in VS Code.

## Use Case 1: Initial Setup (Terraforming)

### Overview

Transforming a legacy project into an AI-Ready environment by generating the initial configuration.

### Sequence Diagram

```mermaid
sequenceDiagram
    participant User
    participant Copilot
    participant Terraformer as /terraformer

    User->>Copilot: /terraformer
    Copilot->>Terraformer: Invoke Skill
    Terraformer->>Terraformer: Analyze Project Structure
    Terraformer->>Terraformer: Detect Tech Stack
    Terraformer->>User: Generate Agents & Skills
    User->>User: Save files to .github/
```

### Related Files

- `.github/prompts/terraformer.prompt.md` - The meta-skill logic.
- `.github/templates/*.template.md` - The blueprints used for generation.

### Processing Flow

1.  User runs `/terraformer`.
2.  The skill analyzes the workspace to identify languages and frameworks.
3.  It reads the templates from `.github/templates/`.
4.  It populates the templates with project-specific context.
5.  It outputs the content for `AGENTS.md`, `.github/agents/*`, and `.github/prompts/*`.

## Use Case 2: Feature Implementation

### Overview

Implementing a new feature using the specialized agent team.

### Sequence Diagram

```mermaid
sequenceDiagram
    participant User
    participant Arch as @Architect
    participant Dev as @Developer
    participant QG as @QualityGuard

    User->>Arch: "I need feature X"
    Arch->>Arch: /plan (Impact Analysis)
    Arch->>User: Proposed Spec & Plan
    User->>Arch: Approve
    User->>Dev: "Implement feature X based on plan"
    Dev->>Dev: /implement
    Dev->>User: Code Changes
    User->>QG: /audit
    QG->>User: Review Report
```

### Related Files

- `.github/prompts/plan.prompt.md`
- `.github/prompts/implement.prompt.md`
- `.github/prompts/audit.prompt.md`

### Processing Flow

1.  **Planning**: `@Architect` uses `/plan` to create a detailed implementation plan.
2.  **Implementation**: `@Developer` uses `/implement` to write code. **Constraint**: Cannot change specs.
3.  **Review**: `@QualityGuard` uses `/audit` to verify the implementation against the plan and coding standards.

## Use Case 3: Extending the Environment (Customization)

### Overview

Creating project-specific skills to handle unique workflows or requirements not covered by the standard ANTP set.

### Sequence Diagram

```mermaid
sequenceDiagram
    participant User
    participant Arch as @Architect
    participant FileSys as File System

    User->>Arch: /create-custom-prompt
    Arch->>User: "What is the goal of this prompt?"
    User->>Arch: "Automate database migration scripts"
    Arch->>Arch: Analyze Goal & Infer Settings
    Arch->>User: Propose Prompt Content
    User->>Arch: Approve
    Arch->>FileSys: Create .github/prompts/migration.prompt.md
    User->>User: Use /migration
```

### Related Files

- `.github/templates/skills/create-custom-prompt.prompt.template.md`

### Processing Flow

1.  **Initiation**: User invokes `/create-custom-prompt`.
2.  **Interview**: `@Architect` interviews the user to understand the specific need.
3.  **Generation**: The agent generates a new `.prompt.md` file following best practices.
4.  **Usage**: The new skill becomes immediately available to the team (e.g., `/migration`).
