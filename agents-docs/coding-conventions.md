<!-- This document is generated/updated by the sync-doc workflow -->

# Design Principles and Coding Conventions

## Design Principles

1.  **Anti-Generalist Principle**:

    - AI Agents must have specialized roles.
    - `@Developer` is strictly prohibited from making specification changes without `@Architect` approval.
    - This prevents "Specification Drift" where AI fixes code but breaks business logic.

2.  **Explicit Context**:

    - Do not rely on implicit knowledge. All context must be explicitly documented in `AGENTS.md` or `agents-docs/`.

3.  **DRY (Don't Repeat Yourself)**:

    - Avoid duplicating information across prompts. Reference shared documentation in `agents-docs/` instead.

## Documentation Policy

- **Transparency**: All AI-generated documentation MUST include a generation tag at the top of the file to warn users of potential hallucinations.
  - Format: `<!-- This document is generated and updated by [source] -->` (e.g., `.github/prompts/doc-sync.prompt.md` or `@AgentName`).

4.  **Human-in-the-Loop**:
    - All AI-generated code must be reviewed by a human (or `@QualityGuard`).

## Adopted Design Patterns

- **Meta-Prompting**: Using prompts to generate other prompts (e.g., `/terraformer`).
- **Chain of Thought**: Encouraging agents to plan before executing (`/plan`).
- **Role-Based Access Control (RBAC)**: Simulating authority levels via prompt instructions.

## Naming Conventions

- **Agents**: PascalCase with `@` prefix (e.g., `@Architect`, `@QualityGuard`).
- **Skills**: kebab-case with `/` prefix (e.g., `/plan`, `/doc-sync`).
- **Agent Files**: `[agent-name].agent.md` (e.g., `architect.agent.md`).
- **Skill Files**: `[skill-name].prompt.md` (e.g., `plan.prompt.md`).
- **Documentation**: kebab-case (e.g., `coding-conventions.md`).

## Code Style

- **Format**: GitHub Flavored Markdown (GFM).
- **Language**: English (US) for all documentation and comments.
- **Diagrams**: Mermaid.js for all diagrams.

## Testing Policy

- **Prompt Testing**: Prompts are tested by running them against reference projects and verifying the output.
- **Regression Testing**: Ensure new skills do not break existing agent behaviors.
