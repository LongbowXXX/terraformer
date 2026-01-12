# AGENTS.md - Terraformer

> A Meta-Engine that transforms legacy codebases into AI-Native environments by implementing the AI-Native Transformation Protocol (ANTP v1.4).

This file provides context and instructions for AI coding agents working on this project.

## 1. Executive Summary

**Purpose**: Eliminate "Context Debt" in legacy projects by generating specialized AI agents and standardized procedures (SOPs).

**Type**: Meta-Engine / Code Generator (Prompt-based, no runtime code)

**Status**: Beta (ANTP v1.4)

## 2. Architecture & Tech Stack

→ **Details**: [docs/architecture/overview.md](./docs/architecture/overview.md), [docs/architecture/tech-stack.md](./docs/architecture/tech-stack.md)

| Category      | Technology               | Purpose                   |
| ------------- | ------------------------ | ------------------------- |
| Runtime       | VS Code + GitHub Copilot | Execution environment     |
| Configuration | Markdown + YAML          | Agent/Command definitions |

### Core Patterns

- **Four-Layer Stack (ANTP)**: L1 Constitution → L2 Commands → L3 Knowledge → L4 Agents
- **Anti-Generalist Principle**: `@Developer` has zero spec authority; must escalate

## 3. Directory Structure

→ **Details**: [docs/architecture/directory-structure.md](./docs/architecture/directory-structure.md)

```
terraformer/
├── .github/
│   ├── agents/                     # Agent Definitions (Target Project & Source)
│   ├── prompts/                    # Command Entry Points (Target Project & Source)
│   └── skills/                     # Skill Implementations (Detailed Command Logic)
├── docs/                           # Project-specific docs (architecture, features, specs)
├── knowledge/                      # Universal guidelines & templates
└── AGENTS.md                       # This file (L1: Constitution & L3: Knowledge Hub)
```

> **Note on Directory Structure**:
> In this source repository, `.github/agents/` contains the default agent definitions and `.github/prompts/` contains all available commands.
> When Terraformer is installed in a **Target Project**, these definitions are copied or referenced.

## 4. Key Concepts (Ubiquitous Language)

→ **Details**: [docs/glossary.md](./docs/glossary.md)

This section defines the core terminology used across the project. For the full list of definitions, please refer to the detailed Glossary document linked above.

| Term             | Definition                                            |
| ---------------- | ----------------------------------------------------- |
| **Context Debt** | Implicit knowledge causing AI failures                |
| **ANTP**         | AI-Native Transformation Protocol (4-layer framework) |

## 5. Entry Points & Key Flows

→ **Details**: [docs/architecture/key-flows.md](./docs/architecture/key-flows.md)

| Command              | Purpose                          |
| -------------------- | -------------------------------- |
| `/terraform-context` | Generate `AGENTS.md`             |
| `@Architect`         | Design authority                 |
| `@Developer`         | Implementation (no spec changes) |

## 6. Development Rules

→ **Details**: [docs/rules/coding-conventions.md](./docs/rules/coding-conventions.md), [docs/architecture/constraints.md](./docs/architecture/constraints.md)

### 🔍 Dynamic Context Protocol (Research Phase)

**CRITICAL INSTRUCTION FOR ALL AGENTS:**
The context provided in this file (`AGENTS.md`) is a **summary index**. It does NOT contain all the details needed for your tasks.
**Before starting any task, you MUST:**

1.  **Search**: Use your available tools to perform **keyword/regex searches** or **semantic searches** to find specific documentation in `docs/` or `knowledge/` relevant to the user's request.
    - _Example_: If the user asks about "Testing", search for and read documents related to testing instructions.
    - _Example_: If the user asks for a "Review", search for and read review guidelines.
2.  **Follow Links**: Since `AGENTS.md` serves as a summary index and provides links to important files and folders, you MUST follow these links to obtain detailed information.
3.  **Read**: Load the content of these detailed documents into your context.
4.  **Cross-Reference**: Do NOT rely on assumptions. Always verify against the official documentation found.

### Must Follow

- `@Developer` must **immediately escalate** spec gaps (Anti-Drift Lock)
- All Agents must follow [**Sequential Inquiry**](./knowledge/guidelines/prompting/sequential-inquiry.md) protocol when gathering information: Ask questions one by one, not in bulk.

### Must Avoid

- `@Developer` making specification changes
- Generic AI interactions without role assignment

### Role Enforcement & Access Control

- **Strict Role Gating**: When a skill file (`.github/skills/*/SKILL.md`) contains `<stopping_rules>`, agents MUST check if their `ACTIVE_AGENT_ID` matches the `<required_agent>`. If they do not match, the agent MUST immediately ABORT all processing and return only the `<refusal_message>`. Any attempt to "read ahead" or "judge the content first" is a SEVERE VIOLATION of the Specialization Principle.

### Escalation Path for Role Mismatch

When an agent encounters a role mismatch due to `<stopping_rules>`, the agent MUST:

1.  **Stop**: Do not process any further instructions from the skill file.
2.  **Inform**: Output the `<refusal_message>` defined in the skill file.
3.  **Guide**: Advise the user on which role (`@Agent`) is required to execute the task.
    - _Example_: "This task requires the `@Architect` role. Please switch to Architect mode and retry."

### Role Declaration Protocol

At the start of any task involving a skill file, agents SHOULD explicitly declare their role to ensure clarity and prevent role drift:

1.  **Declare**: State the current `ACTIVE_AGENT_ID` (e.g., "I am operating as `@Debugger`.").
2.  **Verify**: Confirm that the task falls within the agent's defined responsibilities.
3.  **Proceed or Escalate**: If the task is within scope, proceed. Otherwise, escalate or refuse as per the Escalation Path.

### Agent/Command Maintenance

- When adding or updating Agents or Commands, please ensure to check the latest specifications at the URLs below.
  - https://code.visualstudio.com/docs/copilot/customization/prompt-files
  - https://code.visualstudio.com/docs/copilot/customization/custom-agents

### Artifact-Centric Workflow (Spec-Driven L4)

**Role**: "1 Command = 1 Artifact"
All agents MUST output their work as persistent Markdown artifacts in `docs/specs/[FeatureName]/`. Conversations are ephemeral; artifacts are eternal.

**Pipeline**:

1.  **Requirements**: `/bsa-requirements` -> `docs/specs/[Feature]/requirements.md`
2.  **Design**: `/arc-design` -> `docs/specs/[Feature]/design.md`
3.  **Plan**: `/arc-plan` -> `docs/specs/[Feature]/implementation_plan.md`
4.  **Implementation**: `/dev-implement` -> Code (src/...)

**Context Hygiene**:

- Agents should only read the artifacts relevant to their phase.
- Do NOT rely on chat history for critical specifications.

### Language Guidelines

- **Documentation**: All documents managed in git must be written in English.
- **Chat Interaction**: Interact with the user in their preferred language.

## 7. Testing

→ **Details**: [docs/rules/testing.md](./docs/rules/testing.md)

Manual verification via test projects; automated CI planned.

## 8. Quick Reference

### Agents (The Specialized Team)

| Agent              | Authority      | Constraint                         | Commands                                           |
| ------------------ | -------------- | ---------------------------------- | -------------------------------------------------- |
| `@Architect`       | Design & Specs | —                                  | `/arc-plan`, `/arc-design`                         |
| `@BusinessAnalyst` | Requirements   | No code                            | `/bsa-requirements`                                |
| `@QualityGuard`    | Enforcer       | Review only                        | `/qua-audit`, `/qua-test-spec`, `/qua-sanity-test` |
| `@Librarian`       | Keeper         | Docs only; no behavior changes     | `/lib-doc-sync`, `/lib-release-new-version`        |
| `@Gardener`        | Maintainer     | Refactors only; no feature changes | `/gar-refactor`                                    |
| `@Debugger`        | Bug Analysis   | Must escalate spec bugs            | `/dbg-debug`                                       |
| `@Developer`       | **None**       | Must escalate blockers             | `/dev-test`, `/dev-implement`                      |

### Commands

| Command                      | Purpose                             |
| ---------------------------- | ----------------------------------- |
| `/bsa-requirements`          | PRD & User Story generation         |
| `/arc-design`                | System design & diagrams            |
| `/arc-plan`                  | Impact analysis & planning          |
| `/gar-refactor`              | Safe refactoring                    |
| `/dev-test`                  | TDD-based test generation           |
| `/dev-implement`             | Implementation from specs           |
| `/qua-review`                | General code review                 |
| `/dbg-debug`                 | Root cause analysis & fix           |
| `/lib-doc-sync`              | Documentation sync                  |
| `/lib-check-doc-consistency` | Verify doc consistency              |
| `/arc-create-custom-prompt`  | Create custom command prompt        |
| `/arc-create-custom-agent`   | Create custom agent (.agent.md)     |
| `/arc-vscode-tasks`          | Generate .vscode/tasks.json         |
| `/arc-vscode-settings`       | Generate .vscode/settings.json      |
| `/arc-vscode-extensions`     | Generate .vscode/extensions.json    |
| `/qua-audit-spec`            | Audit spec documents (Spec Linter)  |
| `/qua-test-spec`             | Generate Test Specs                 |
| `/qua-audit`                 | Code Review & Security Audit        |
| `/bsa-brainstorm`            | Brainstorming & Spec consultation   |
| `/arc-discover-specs`        | Reverse-engineer specs from code    |
| `/qua-sanity-test`           | Generate sanity test checklist      |
| `/lib-release-new-version`   | Manual/Automated release management |
| `/dev-ask-architect`         | Ask Architect for clarification     |

---

## 📚 Detailed Documentation Index

| Topic                 | Link                                                                                   |
| --------------------- | -------------------------------------------------------------------------------------- |
| Architecture & Design | [docs/architecture/overview.md](./docs/architecture/overview.md)                       |
| Directory Structure   | [docs/architecture/directory-structure.md](./docs/architecture/directory-structure.md) |
| Coding Conventions    | [docs/rules/coding-conventions.md](./docs/rules/coding-conventions.md)                 |
| Key Flows & Use Cases | [docs/architecture/key-flows.md](./docs/architecture/key-flows.md)                     |
| Tech Stack            | [docs/architecture/tech-stack.md](./docs/architecture/tech-stack.md)                   |
| Testing Strategy      | [docs/rules/testing.md](./docs/rules/testing.md)                                       |
| Constraints & Gotchas | [docs/architecture/constraints.md](./docs/architecture/constraints.md)                 |

## 9. Knowledge Base

→ **Details**: [knowledge/](./knowledge/)

| Topic                        | Link                                                                                                                         |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| PR Creation Guidelines       | [knowledge/guidelines/pr-creation-guidelines.md](./knowledge/guidelines/pr-creation-guidelines.md)                           |
| Debugging Guidelines         | [knowledge/guidelines/debugging.md](./knowledge/guidelines/debugging.md)                                                     |
| Prompting Techniques         | [knowledge/guidelines/prompting/README.md](./knowledge/guidelines/prompting/README.md)                                       |
| Software Review Perspectives | [knowledge/guidelines/software-review.md](./knowledge/guidelines/software-review.md)                                         |
| XML Structured Prompting     | [knowledge/guidelines/prompting/xml-structured-prompting.md](./knowledge/guidelines/prompting/xml-structured-prompting.md)   |
| Specification Guidelines     | [knowledge/guidelines/specification-guidelines.md](./knowledge/guidelines/specification-guidelines.md)                       |
| Role-Based Stopping Rules    | [knowledge/guidelines/prompting/role-based-stopping-rules.md](./knowledge/guidelines/prompting/role-based-stopping-rules.md) |
| Workflow (AI Collaboration)  | [knowledge/workflows/workflow.md](./knowledge/workflows/workflow.md)                                                         |

---

_Context map for AI coding agents - Terraformer (ANTP v1.4)_
