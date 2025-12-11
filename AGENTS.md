# AGENTS.md - Terraformer

> A Meta-Engine that transforms legacy codebases into AI-Native environments by implementing the AI-Native Transformation Protocol (ANTP v1.4).

This file provides context and instructions for AI coding agents working on this project.

## 1. Executive Summary

**Purpose**: Eliminate "Context Debt" in legacy projects by generating specialized AI agents and standardized procedures (SOPs).

**Type**: Meta-Engine / Code Generator (Prompt-based, no runtime code)

**Status**: Beta (ANTP v1.4)

## 2. Architecture & Tech Stack

→ **Details**: [agents-docs/architecture.md](./agents-docs/architecture.md), [agents-docs/tech-stack.md](./agents-docs/tech-stack.md)

| Category      | Technology               | Purpose                 |
| ------------- | ------------------------ | ----------------------- |
| Runtime       | VS Code + GitHub Copilot | Execution environment   |
| Configuration | Markdown + YAML          | Agent/Skill definitions |

### Core Patterns

- **Four-Layer Stack (ANTP)**: L1 Constitution → L2 Skills → L3 Knowledge → L4 Agents
- **Anti-Generalist Principle**: `@Developer` has zero spec authority; must escalate

## 3. Directory Structure

→ **Details**: [agents-docs/directory-structure.md](./agents-docs/directory-structure.md)

```
terraformer/
├── .github/
│   ├── prompts/                    # Engine (/terraformer, /terraform-context)
│   └── templates/                  # Agent & Skill templates
├── docs/                           # PROJECT_CHARTER.md, DEVELOPMENT_CONTEXT.md
├── agents-docs/                    # AI-oriented documentation
├── knowledge/                      # Reusable knowledge & techniques (e.g., prompting)
└── AGENTS.md                       # This file (L1: Constitution & L3: Knowledge Hub)
```

## 4. Key Concepts (Ubiquitous Language)

→ **Details**: [agents-docs/glossary.md](./agents-docs/glossary.md)

This section defines the core terminology used across the project. For the full list of definitions, please refer to the detailed Glossary document linked above.

| Term             | Definition                                            |
| ---------------- | ----------------------------------------------------- |
| **Context Debt** | Implicit knowledge causing AI failures                |
| **ANTP**         | AI-Native Transformation Protocol (4-layer framework) |

## 5. Entry Points & Key Flows

→ **Details**: [agents-docs/key-flows.md](./agents-docs/key-flows.md)

| Command              | Purpose                          |
| -------------------- | -------------------------------- |
| `/terraformer`       | Generate agents and skills       |
| `/terraform-context` | Generate `AGENTS.md`             |
| `@Architect`         | Design authority                 |
| `@Developer`         | Implementation (no spec changes) |

## 6. Development Rules

→ **Details**: [agents-docs/coding-conventions.md](./agents-docs/coding-conventions.md), [agents-docs/constraints-and-gotchas.md](./agents-docs/constraints-and-gotchas.md)

### 🔍 Dynamic Context Protocol (Research Phase)

**CRITICAL INSTRUCTION FOR ALL AGENTS:**
The context provided in this file (`AGENTS.md`) is a **summary index**. It does NOT contain all the details needed for your tasks.
**Before starting any task, you MUST:**

1.  **Search**: Use your available tools to perform **keyword/regex searches** or **semantic searches** to find specific documentation in `agents-docs/` or `knowledge/` relevant to the user's request.
    - _Example_: If the user asks about "Testing", search for and read documents related to testing instructions.
    - _Example_: If the user asks for a "Review", search for and read review guidelines.
2.  **Read**: Load the content of these detailed documents into your context.
3.  **Cross-Reference**: Do NOT rely on assumptions. Always verify against the official documentation found.

### Must Follow

- `@Developer` must **immediately escalate** spec gaps (Anti-Drift Lock)

### Must Avoid

- `@Developer` making specification changes
- Generic AI interactions without role assignment

### Agent/Skill Maintenance

- When adding or updating Agents or Skills, please ensure to check the latest specifications at the URLs below.
  - https://code.visualstudio.com/docs/copilot/customization/prompt-files
  - https://code.visualstudio.com/docs/copilot/customization/custom-agents

### Language Guidelines

- **Documentation**: All documents managed in git must be written in English.
- **Chat Interaction**: Interact with the user in their preferred language.

## 7. Testing

→ **Details**: [agents-docs/testing.md](./agents-docs/testing.md)

Manual verification via test projects; automated CI planned.

## 8. Quick Reference

### Agents (The Specialized Team)

| Agent              | Authority      | Constraint              |
| ------------------ | -------------- | ----------------------- |
| `@Architect`       | Design & Specs | —                       |
| `@BusinessAnalyst` | Requirements   | No code                 |
| `@QualityGuard`    | Merge Approval | —                       |
| `@Librarian`       | Documentation  | —                       |
| `@Gardener`        | Refactoring    | —                       |
| `@Debugger`        | Bug Analysis   | Must escalate spec bugs |
| `@Developer`       | **None**       | Must escalate blockers  |

### Skills

| Skill                    | Purpose                            |
| ------------------------ | ---------------------------------- |
| `/requirements`          | PRD & User Story generation        |
| `/design`                | System design & diagrams           |
| `/plan`                  | Impact analysis & planning         |
| `/refactor`              | Safe refactoring                   |
| `/test`                  | TDD-based test generation          |
| `/implement`             | Implementation from specs          |
| `/review`                | General code review                |
| `/debug`                 | Root cause analysis & fix          |
| `/doc-sync`              | Documentation sync                 |
| `/check-doc-consistency` | Verify doc consistency             |
| `/create-custom-prompt`  | Create custom skill prompt         |
| `/vscode-tasks`          | Generate .vscode/tasks.json        |
| `/vscode-settings`       | Generate .vscode/settings.json     |
| `/vscode-extensions`     | Generate .vscode/extensions.json   |
| `/audit-spec`            | Audit spec documents (Spec Linter) |
| `/test-spec`             | Generate Test Specs                |
| `/audit`                 | Code Review & Security Audit       |
| `/brainstorm`            | Brainstorming & Spec consultation  |

---

## 📚 Detailed Documentation Index

| Topic                 | Link                                                                               |
| --------------------- | ---------------------------------------------------------------------------------- |
| Architecture & Design | [agents-docs/architecture.md](./agents-docs/architecture.md)                       |
| Directory Structure   | [agents-docs/directory-structure.md](./agents-docs/directory-structure.md)         |
| Coding Conventions    | [agents-docs/coding-conventions.md](./agents-docs/coding-conventions.md)           |
| Key Flows & Use Cases | [agents-docs/key-flows.md](./agents-docs/key-flows.md)                             |
| Tech Stack            | [agents-docs/tech-stack.md](./agents-docs/tech-stack.md)                           |
| Testing Strategy      | [agents-docs/testing.md](./agents-docs/testing.md)                                 |
| Constraints & Gotchas | [agents-docs/constraints-and-gotchas.md](./agents-docs/constraints-and-gotchas.md) |

## 9. Knowledge Base

→ **Details**: [knowledge/](./knowledge/)

| Topic                        | Link                                                                                     |
| ---------------------------- | ---------------------------------------------------------------------------------------- |
| PR Creation Guidelines       | [knowledge/pr-creation-guidelines.md](./knowledge/pr-creation-guidelines.md)             |
| Prompting Techniques         | [knowledge/prompting-techniques.md](./knowledge/prompting-techniques.md)                 |
| Software Review Perspectives | [knowledge/software-review-perspectives.md](./knowledge/software-review-perspectives.md) |
| XML Structured Prompting     | [knowledge/xml-structured-prompting.md](./knowledge/xml-structured-prompting.md)         |
| Specification Guidelines     | [knowledge/specification-guidelines.md](./knowledge/specification-guidelines.md)         |

---

_Context map for AI coding agents - Terraformer (ANTP v1.4)_
