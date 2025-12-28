<!-- This document is generated/updated by the sync-doc workflow -->

# Design Principles and Coding Conventions

## Design Principles

- **Anti-Generalist Principle**: AI agents must have narrow, well-defined responsibilities. No agent should be a "jack of all trades".
- **Documentation IS Code**: Natural language specs are the "High-Level Source Code" of the system. They must be versioned, reviewed, and debugged just like software.
- **Fail Fast in Spec**: Catch bugs in the requirement phase (cheap) rather than in the code phase (expensive).
- **Explicit Context Over Implicit Knowledge**: All rules must be written down in `knowledge/` or `docs/`. Do not assume the AI knows your preferences.
- **Single Source of Truth**: `AGENTS.md` is the single entry point that orchestrates the entire system.

## Adopted Design Patterns

- **Roles & Skills Architecture**: Decoupling the "Who" (Agent) from the "How" (Skill).
- **Meta-Prompting**: Using prompts to generate other prompts (e.g., `/terraformer`, `/create-custom-prompt`).
- **XML Structured Prompting**: Using XML tags to structure prompt files for better machine readability.

## Naming Conventions

### File Names

- **Prompts (Skills)**: `kebab-case.prompt.md` (e.g., `terraform-context.prompt.md`)
- **Agents**: `PascalCase.agent.md` (e.g., `Architect.agent.md`) - _Note: The file extension is important for VS Code recognition._
- **Documentation**: `kebab-case.md` (e.g., `coding-conventions.md`)

### Workflow Names

- **Slash Commands**: `/command-name` (e.g., `/sync-doc`, `/plan`).

## Code Style (Prompt Engineering)

- **Frontmatter**: All prompt files must start with YAML frontmatter defining `name`, `description`, etc.
- **XML Structure**: Use `<system>`, `<user>`, `<instruction>` tags to clearly delimit sections.
- **Variables**: Use `{{ variable_name }}` syntax for template placeholders (Liquid-style).

## Testing Policy

- **Prompt Validation**: New prompts should be tested against a set of "golden queries" to ensure they don't hallucinate.
- **Prototype Mode**: Use "Prototype Mode" to bypass strict specification checks for rapid iteration.

## Documentation Maintenance (Sync-Doc Guidelines)

To prevent documentation from diverging from the codebase:

1.  **Timing**: Run `/sync-doc` (or manually check) whenever:
    - A new Agent or Skill is added.
    - A major refactoring changes the directory structure.
    - A new external integration is added.
2.  **Review Process**:
    - Documentation changes should be included in the same PR as the code changes.
    - Use `@Librarian` or `/check-doc-consistency` to detect drift.
3.  **Automation**:
    - Future: Add a CI check that runs a "doc-coverage" tool.
