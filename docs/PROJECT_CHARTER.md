# Project Charter: AI-Native Transformation Protocol (ANTP)

**Version:** 1.4.1
**Date:** December 10, 2025
**Status:** Prototype Phase (Roles & Skills Architecture Implemented)

## 1. Executive Summary

This project aims to establish a **universal transition protocol (Meta-Plan)** to transform any existing software project into an "AI-Native" state.
In ANTP v1.4, we evolve beyond simple role definitions. We introduce the **"Roles & Skills Architecture,"** where AI agents are not only assigned specific responsibilities (Roles) but are also equipped with standardized procedural knowledge (Skills/SOPs). This ensures a high-quality, autonomous **"AI Collaboration System"** generated automatically for any legacy codebase.

> [!IMPORTANT]  
> **Before you start coding**, please read the [AI Literacy Guide](../knowledge/guidelines/ai-literacy/) to understand how to collaborate safely with AI agents.

## 2. The AI-Native Manifesto

We respect the values of Agile development, but as we welcome AI agents as members of our team, we declare a shift to the following new values (Paradigm Shift).

### 1. Machine-Readable Context over Human-Only Documentation

**Traditional Value:** Documentation is for humans to read, and kept to a minimum to avoid slowing down development.

**Our Value:** Documentation is **"execution code (context) for AI agents"**. Since relying on AI to "read between the lines" risks hallucination, we define **"Quality"** as maintaining structured, explicit documentation (Markdown/XML), even if it seems redundant to humans.

### 2. Verified Specifications over Trial-and-Error Coding

**Traditional Value:** "Working software" is the primary measure of progress, and the correct solution is found while building.

**Our Value:** Since AI can generate code instantly, coding itself is no longer the bottleneck. **"Verified Specifications"** are the true measure of progress. We enforce **"No Spec, No Code"** to prevent rapid rework.

### 3. Explicit Written Protocols over Synchronous Conversation

**Traditional Value:** Individuals and interactions over processes and tools (sharing tacit knowledge face-to-face).

**Our Value:** AI cannot participate in water cooler chats. We consider only information recorded as **"Explicit Context"** to be the Single Source of Truth, rather than resolving issues through dialogue alone. Asynchronous and text-based communication enables collaboration with AI.

### 4. Spec-Level Feedback over Code-Level Feedback

**Traditional Value:** Write code, then test and get feedback (Fail Fast in Code).

**Our Value:** Provide feedback on the "Plan" or "Spec" stage (**Fail Fast in Spec**). However, we do not require perfection in the specs (**Good Enough is Better Than Perfect**). Given the high speed of AI implementation, humans should review the **"Implementation Plan"** primarily to align on direction, avoiding excessive time spent on details before generating code.

## 3. Background and Problem Statement

### Background

As Generative AI becomes integral to development, simply assigning a persona (e.g., "You are an Architect") is insufficient. Without explicit procedural guidance, the quality of AI output varies significantly, and project-specific workflows are often ignored.

### Solved & Remaining Challenges (v1.4 Focus)

1.  **Procedural Drift (New):** Agents may understand _what_ to do but often forget _how_ to do it correctly (e.g., skipping step-by-step reasoning or ignoring output formats).
2.  **Role-Capability Mismatch:** A "Senior Engineer" agent without access to specific testing or refactoring methodologies is prone to hallucination or low-quality output.
3.  **Context Debt:** The persistent issue of implicit knowledge hindering AI understanding.

## 4. Project Objective

**"To develop a Meta-Engine that generates the optimal 'AI Organization Chart' and 'Standard Operating Procedures (SOPs)'."**

By analyzing a target project, Terraformer provides a complete package:

1.  **The Agents (Roles):** Specialized personas with strict authority boundaries (`.agent.md`).
2.  **The Skills (SOPs):** Standardized thinking processes for specific tasks (`.prompt.md`).

## 5. Deliverables: The AI Integration Stack

The protocol establishes four integrated layers within a project:

| Layer  | Name             | Role                                                                             | Implementation                |
| :----- | :--------------- | :------------------------------------------------------------------------------- | :---------------------------- |
| **L1** | **Constitution** | Project Rules & Laws                                                             | `AGENTS.md`                   |
| **L2** | **Skills**       | **(New)** Standardized Task Procedures<br>(e.g., Planning, Testing, Refactoring) | `.github/prompts/*.prompt.md` |
| **L3** | **Knowledge**    | Explicit Context Map                                                             | `docs/*`                      |
| **L4** | **Agents**       | Specialized Roles with Authority                                                 | `.github/agents/*.agent.md`   |

## 6. Architecture: Roles & Skills Matrix

In ANTP v1.4, each L4 Agent is generated with specific L2 Skills "injected" into their system instructions.

### A. Management Layer (Authority Holders)

1.  **@Architect (The Designer)**
    - **Authority:** Sole power to decide specs and design.
    - **Equipped Skill:** **`/plan`** (Implementation plans), **`/design`** (System design), **`/vscode-tasks`**, **`/vscode-settings`**, **`/vscode-extensions`**, **`/discover-specs`** (Reverse-engineer specs).
2.  **@BusinessAnalyst (The Translator)**
    - **Authority:** Requirement definition.
    - **Equipped Skill:** **`/requirements`** (Convert vague requests into User Stories), **`/brainstorm`** (Brainstorming & Spec consultation).
3.  **@QualityGuard (The Enforcer)**
    - **Authority:** Code review and merge approval.
    - **Equipped Skill:** **`/audit`** (Security & Quality checklist), **`/test-spec`** (Test Plan generation), **`/audit-spec`** (Specification Linter), **`/sanity-test`** (Sanity Test generation).
4.  **@Librarian (The Keeper)**
    - **Authority:** Documentation synchronization.
    - **Equipped Skill:** **`/doc-sync`** (Detect diffs between Code and Docs), **`/check-doc-consistency`** (Verify doc consistency).
5.  **@Gardener (The Maintainer)**
    - **Authority:** Tech debt removal.
    - **Equipped Skill:** **`/refactor`** (Safe structural improvements without logic changes).
6.  **@Debugger (The Hunter)**
    - **Authority:** Root cause analysis and fix planning.
    - **Equipped Skill:** **`/debug`** (Scientific method for bug hunting).

### B. Execution Layer (Restricted)

7.  **@Developer (The Implementer)**
    - **Authority:** Implementation ONLY (Strictly prohibited from changing specs).
    - **Equipped Skill:** **`/test`** (Test Code implementation), **`/implement`** (Implementation from specs).
    - **Constraint:** Must escalate to `@Architect` (using `/plan`) if implementation is blocked.

## 7. Development Modes

To balance the need for high-quality production code with the reality of rapid experimentation, ANTP v1.4 supports two distinct development modes.

### A. Standard Mode (Default)

- **Philosophy:** "Slow is Smooth, Smooth is Fast."
- **Process:** Strict adherence to the Roles & Skills Matrix. No code without specs.
- **Goal:** Maintainability, Security, and Long-term Stability.

### B. Prototype Mode (Opt-in)

- **Philosophy:** "Move Fast and Break Things (Temporarily)."
- **Process:** Explicitly requested by the user. `@Developer` can implement without formal specs. `@QualityGuard` relaxes checks.
- **Goal:** Idea Validation, PoC, Temporary Solutions.
- **Constraint:** Code MUST be marked as `/* PROTOTYPE */` and is considered technical debt that must be paid down (refactored/rewritten) before production use.

## 8. Technical Strategy: Skill Injection Mechanism

The Terraformer Engine bootstraps the project using the following logic:

1.  **Context Generation:** Executes `/terraform-context` to generate `AGENTS.md`, creating a high-density map of the project.
2.  **Skill Scanning:** Scans the user's `.github/prompts/` to detect existing know-how (Prompt Files).
3.  **Template Expansion:** Automatically generates missing standard skills (Plan, Refactor, Test) from built-in templates.
4.  **Dynamic Injection:** When generating Agent definitions (`.agent.md`), the engine injects instructions such as _"When performing this task, you MUST follow the procedure defined in `#skill-name`."_

This allows users to acquire a **"Team of Agents equipped with Senior Engineer thought processes"** simply by running `/terraformer` (after context generation).

## 9. Expected Effects

- **Quality Homogenization:** Regardless of who operates the AI, common procedures (Skills) are applied, stabilizing output quality.
- **Rapid Onboarding:** New members can start immediately by relying on `@Architect` to plan and `@Developer` to implement using the correct procedures.
- Maintainability: Workflows can be updated simply by editing the "Skill Files" (`.prompt.md`) rather than modifying complex Agent prompts.

## 10. Documentation & Traceability

To ensure that AI and human collaboration is effective and auditable, we enforce strict documentation standards and follow the [Standard Workflow](../knowledge/workflows/workflow.md).

### Documentation Portability Strategy

To maximize the reusability of the AI-Native Transformation Protocol across different projects, we enforce a strict separation of documentation assets:

1.  **Universal Knowledge (`knowledge/`)**:

    - **Purpose**: "Write Once, Run Anywhere".
    - **Content**: General guidelines (AI Literacy, Prompting Techniques), Templates, and Workflow definitions.
    - **Benefit**: Can be copied directly to any new project without modification.

2.  **Project-Specific Assets (`docs/`)**:
    - **Purpose**: "Context for _this_ project".
    - **Content**: Architecture overview, Domain glossary, Feature specifications, and Local rules.
    - **Benefit**: Keeps the core protocol clean and separates "Methodology" from "Implementation".

### Standardized Templates

We use standard templates (e.g., `knowledge/templates/artifacts/specification.template.md`, `knowledge/templates/agents/review_report.template.md`) for all key deliverables.

- **Consistency**: Ensures all agents and humans provide the same level of detail.
- **Evidence**: Acts as a permanent record of decisions and agreements.
- **Quality**: Enforces a "checklist" approach to ensure no sections are missed.

### Traceability

We maintain explicit links between documents (e.g., Specification links to Requirements).

- **Impact Analysis**: Allows us to see which specs are affected if a requirement changes.
- **Verification**: Ensures every requirement has a corresponding spec and test.
- **Auditability**: Provides a clear chain of custody from idea to implementation.

## 11. Roadmap

1.  **Validation:** Field testing of `handoffs` and Prompt File integration in VS Code environments.
2.  **Skill Library Expansion:** Develop extended skill templates (Release, Debug, Security Audit).
3.  **CI/CD Integration:** Research workflows to automatically trigger `@QualityGuard` within GitHub Actions.

## 12. AI Collaboration Policy

Since we utilize AI, it is currently difficult to completely eliminate hallucinations.
However, requiring perfect human review for all AI outputs contradicts the goal of using AI to improve efficiency and ease of work.
We recommend working with the policy: **"Good Enough is Better Than Perfect!"**

1.  **Hallucination Tolerance:** We accept a certain degree of hallucination if it does not constitute a critical issue.
2.  **Transparency:** AI-generated documentation must include a tag indicating "AI Generated" to warn users of potential hallucinations.
3.  **Quality Expectations:**
    - **Code:** Quality is assured to a certain extent through automated testing.
    - **Documentation:** Rigorous quality assurance is difficult. We should treat the AI as a "junior" employee with a few years of experience—minor mistakes should be forgiven with a laugh.
    - **Philosophy:** "Let him who has never made a mistake cast the first stone at the AI."
