<!-- This document is generated/updated by the sync-doc workflow -->

# Design Principles and Coding Conventions

## Design Principles

### 1. The Anti-Generalist Principle

We do not believe in "One AI to rule them all."

- **Rule**: Agents must have specialized roles and clear boundaries.
- **Example**: `@Developer` is strictly prohibited from making specification decisions. If a requirement is unclear, it MUST escalate to `@Architect` or `@BusinessAnalyst`.

### 2. Context Debt Elimination

The primary cause of AI failure is lack of context.

- **Rule**: All implicit knowledge must be made explicit in `AGENTS.md` or `agents-docs/`.
- **Practice**: Never "fix it in chat." If the AI needs context, update the documentation first.

### 3. Text-as-Software

We treat Prompts and Documentation as code.

- **Rule**: All prompts and agents are version-controlled.
- **Practice**: Use Semantic Versioning for the protocol (ANTP v1.4).

## Naming Conventions

### Files

- **Prompts (Skills)**: `kebab-case.prompt.md` (e.g., `plan.prompt.md`)
- **Agents**: `snake_case.agent.md` (e.g., `quality_guard.agent.md`)
- **Templates**: `filename.template.md` (e.g., `architect.agent.template.md`)
- **Documentation**: `kebab-case.md` (e.g., `directory-structure.md`)

### Variables (in Templates)

- **Format**: `{{VARIABLE_NAME}}`
- **Common Variables**:

  - `{{PROJECT_NAME}}`: The name of the project.

## Code Style (Markdown/Prompts)

- **Frontmatter**: Use YAML frontmatter for metadata (description, version).
- **Sections**: Use clear H1/H2 headers to structure instructions.
- **Directives**: Use blockquotes (`>`) or bold text for critical instructions.
- **Examples**: Always provide few-shot examples in prompts to guide the AI.

## Testing Policy

Since this is a prompt-based system:

- **Verification**: Manual verification using "Test Projects" (applying Terraformer to a dummy project).
- **Regression**: Check if new prompts cause hallucinations or degradation in output quality.
