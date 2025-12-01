# Terraformer - Copilot Instructions

## Project Overview

Terraformer is a **Meta-Engine** that transforms legacy codebases into AI-Native environments by generating specialized AI agents and skills. It implements the **AI-Native Transformation Protocol (ANTP v1.4)**.

**Core Philosophy:** Legacy code is a "hostile planet" that needs terraforming—we make implicit context explicit and machine-readable to eliminate "Context Debt."

## Architecture: ANTP Four-Layer Stack

| Layer                | Purpose                        | Location                          |
| -------------------- | ------------------------------ | --------------------------------- |
| **L1: Constitution** | Immutable project rules        | `.github/copilot-instructions.md` |
| **L2: Skills**       | Standardized procedures (SOPs) | `.github/prompts/*.prompt.md`     |
| **L3: Knowledge**    | Explicit context map           | `AGENTS.md`                       |
| **L4: Agents**       | Specialized AI roles           | `.github/agents/*.agent.md`       |

## Key Components

### Prompt Files (The Engine)

- **`/terraformer`** - Main engine that generates 6 agents + 3 skills for target projects
- **`/terraform-context`** - Generates `AGENTS.md` context map

### Agent Templates (`.github/templates/`)

Six specialized roles with strict authority boundaries:

- **Management Layer:** `@Architect`, `@BusinessAnalyst`, `@QualityGuard`, `@Librarian`, `@Gardener`
- **Execution Layer:** `@Developer` (implementation only, NO spec authority)

### Skill Templates (`.github/templates/skills/`)

- `plan.prompt.template.md` - Impact analysis & implementation planning
- `refactor.prompt.template.md` - Safe structural improvements
- `test.prompt.template.md` - TDD-based verification

## Critical Design Decisions

### Anti-Generalist Principle

The `@Developer` agent is **strictly prohibited** from changing specifications. When encountering a spec gap:

1. **STOP immediately** - Do not improvise
2. **Escalate** to `@Architect` via handoff mechanism
3. This prevents "Specification Drift" where code diverges from documentation
4. **EXCEPTION**: If the user explicitly requests **"Prototype Mode"**, this restriction is lifted. The Developer may implement directly, but must mark code as `/* PROTOTYPE */`.

### Template Variable System

All templates use `{{TECH_STACK}}` placeholder, replaced during generation based on target project analysis.

### Handoffs Mechanism

Agent YAML frontmatter includes `handoffs:` property to create UI buttons for workflow transitions (e.g., Architect → Developer, Developer → Architect escalation).

## Development Workflow

### To Test Changes

1. Copy `.github/` contents to a test project
2. Open test project in VS Code with GitHub Copilot
3. Invoke `/terraformer` in Copilot Chat
4. Verify generated agents and skills match target project's tech stack

### File Modification Guidelines

- **Templates:** Modify `{{TECH_STACK}}` sections to support new frameworks
- **Prompts:** Edit `.prompt.md` files to refine generation logic
- **Agents:** Include appropriate `handoffs:` for workflow transitions

## Code Conventions

### YAML Frontmatter (Agent/Prompt Files)

```yaml
---
name: agent-name
description: Brief description with {{TECH_STACK}}
handoffs:
  - label: Button Text
    agent: target_agent
    prompt: "Context message"
    send: false
---
```

### Documentation Structure

- `docs/PROJECT_CHARTER.md` - ANTP protocol definition and vision
- `docs/DEVELOPMENT_CONTEXT.md` - ADR and technical decisions (this is the AI context source)
- `README.md` - User-facing quickstart guide
