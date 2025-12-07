<!-- This document is generated/updated by the sync-doc workflow -->

# Design Principles and Coding Conventions

## Design Principles

- **Anti-Generalist Principle**: AI agents must have narrow, well-defined responsibilities. No agent should be a "jack of all trades".
- **Explicit Context Over Implicit Knowledge**: All rules must be written down in `knowledge/` or `agents-docs/`. Do not assume the AI knows your preferences.
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
