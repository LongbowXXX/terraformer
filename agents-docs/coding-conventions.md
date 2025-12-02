<!-- This document is generated/updated by the sync-doc workflow -->

# Design Principles and Coding Conventions

## Design Principles

1.  **AI-Native First**: All configuration must be optimized for consumption by LLMs (clear context, structured data).
2.  **Anti-Generalist Principle**: Agents must have clearly defined scopes. `@Developer` must never make specification decisions.
3.  **Context Over Code**: The value of Terraformer is in the _context_ it provides (L3), not just the prompts (L2).
4.  **Immutable Constitution**: The L1 Constitution is the supreme law. It cannot be overridden by L2 or L4.

## Adopted Design Patterns

- **Persona Pattern**: Encapsulating capabilities and constraints into "Agents" (e.g., `@Architect`).
- **Chain of Thought (CoT)**: Prompts are designed to encourage step-by-step reasoning (e.g., `/plan` requires Impact Analysis before Implementation).
- **Template Method**: Using Jinja2/Liquid templates to generate specific agent instances from generic definitions.

## Naming Conventions

- **Agent Files**: `.github/agents/[role].agent.md` (e.g., `architect.agent.md`)
- **Skill Files**: `.github/prompts/[skill].prompt.md` (e.g., `plan.prompt.md`)
- **Template Files**: `.github/templates/[name].template.md`
- **Slash Commands**: `/command-name` (kebab-case)
- **Agent Handles**: `@AgentName` (PascalCase)

## Code Style

- **Markdown**: GitHub Flavored Markdown (GFM).
- **Frontmatter**: YAML format for metadata (version, description, handoffs).
- **Placeholders**: `{{VARIABLE_NAME}}` for template substitution.

## Testing Policy

- **Prompt Testing**: Verify that prompts yield consistent results across different LLM models (if applicable).
- **Integration Testing**: Verify that generated agents correctly reference their skills and follow the Constitution.
- **Manual Verification**: Use the `/test` skill to generate verification steps for any changes.
