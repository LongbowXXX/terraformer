# Project Charter: AI-Native Transformation Protocol (ANTP)

**Version:** 1.4
**Date:** November 30, 2025
**Status:** Prototype Phase (Roles & Skills Architecture Implemented)

## 1. Executive Summary

This project aims to establish a **universal transition protocol (Meta-Plan)** to transform any existing software project into an "AI-Native" state.
In ANTP v1.4, we evolve beyond simple role definitions. We introduce the **"Roles & Skills Architecture,"** where AI agents are not only assigned specific responsibilities (Roles) but are also equipped with standardized procedural knowledge (Skills/SOPs). This ensures a high-quality, autonomous **"AI Collaboration System"** generated automatically for any legacy codebase.

## 2. Background and Problem Statement

### Background

As Generative AI becomes integral to development, simply assigning a persona (e.g., "You are an Architect") is insufficient. Without explicit procedural guidance, the quality of AI output varies significantly, and project-specific workflows are often ignored.

### Solved & Remaining Challenges (v1.4 Focus)

1.  **Procedural Drift (New):** Agents may understand _what_ to do but often forget _how_ to do it correctly (e.g., skipping step-by-step reasoning or ignoring output formats).
2.  **Role-Capability Mismatch:** A "Senior Engineer" agent without access to specific testing or refactoring methodologies is prone to hallucination or low-quality output.
3.  **Context Debt:** The persistent issue of implicit knowledge hindering AI understanding.

## 3. Project Objective

**"To develop a Meta-Engine that generates the optimal 'AI Organization Chart' and 'Standard Operating Procedures (SOPs)'."**

By analyzing a target project, Terraformer provides a complete package:

1.  **The Agents (Roles):** Specialized personas with strict authority boundaries (`.agent.md`).
2.  **The Skills (SOPs):** Standardized thinking processes for specific tasks (`.prompt.md`).

## 4. Deliverables: The AI Integration Stack

The protocol establishes four integrated layers within a project:

| Layer  | Name             | Role                                                                             | Implementation                    |
| :----- | :--------------- | :------------------------------------------------------------------------------- | :-------------------------------- |
| **L1** | **Constitution** | Project Rules & Laws                                                             | `.github/copilot-instructions.md` |
| **L2** | **Skills**       | **(New)** Standardized Task Procedures<br>(e.g., Planning, Testing, Refactoring) | `.github/prompts/*.prompt.md`     |
| **L3** | **Knowledge**    | Explicit Context Map                                                             | `llms.txt`                        |
| **L4** | **Agents**       | Specialized Roles with Authority                                                 | `.github/agents/*.agent.md`       |

## 5. Architecture: Roles & Skills Matrix

In ANTP v1.4, each L4 Agent is generated with specific L2 Skills "injected" into their system instructions.

### A. Management Layer (Authority Holders)

1.  **@Architect (The Designer)**
    - **Authority:** Sole power to decide specs and design.
    - **Equipped Skill:** **`/plan`** (Break down requirements into implementation plans & file impact lists).
2.  **@BusinessAnalyst (The Translator)**
    - **Authority:** Requirement definition.
    - **Equipped Skill:** **`/requirements`** (Convert vague requests into User Stories).
3.  **@QualityGuard (The Enforcer)**
    - **Authority:** Code review and merge approval.
    - **Equipped Skill:** **`/audit`** (Security & Quality checklist execution).
4.  **@Librarian (The Keeper)**
    - **Authority:** Documentation synchronization.
    - **Equipped Skill:** **`/doc-sync`** (Detect diffs between Code and Docs).
5.  **@Gardener (The Maintainer)**
    - **Authority:** Tech debt removal.
    - **Equipped Skill:** **`/refactor`** (Safe structural improvements without logic changes).

### B. Execution Layer (Restricted)

6.  **@Developer (The Implementer)**
    - **Authority:** Implementation ONLY (Strictly prohibited from changing specs).
    - **Equipped Skill:** **`/test`** (TDD-based test generation and verification).
    - **Constraint:** Must escalate to `@Architect` (using `/plan`) if implementation is blocked.

## 6. Technical Strategy: Skill Injection Mechanism

The Terraformer Engine bootstraps the project using the following logic:

1.  **Skill Scanning:** Scans the user's `.github/prompts/` to detect existing know-how (Prompt Files).
2.  **Template Expansion:** Automatically generates missing standard skills (Plan, Refactor, Test) from built-in templates.
3.  **Dynamic Injection:** When generating Agent definitions (`.agent.md`), the engine injects instructions such as _"When performing this task, you MUST follow the procedure defined in `#skill-name`."_

This allows users to acquire a **"Team of Agents equipped with Senior Engineer thought processes"** simply by running `/terraformer`.

## 7. Expected Effects

- **Quality Homogenization:** Regardless of who operates the AI, common procedures (Skills) are applied, stabilizing output quality.
- **Rapid Onboarding:** New members can start immediately by relying on `@Architect` to plan and `@Developer` to implement using the correct procedures.
- **Maintainability:** Workflows can be updated simply by editing the "Skill Files" (`.prompt.md`) rather than modifying complex Agent prompts.

## 8. Roadmap

1.  **Validation:** Field testing of `handoffs` and Prompt File integration in VS Code environments.
2.  **Skill Library Expansion:** Develop extended skill templates (Release, Debug, Security Audit).
3.  **CI/CD Integration:** Research workflows to automatically trigger `@QualityGuard` within GitHub Actions.
