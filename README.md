# Terraformer 🌍🤖

> **Terraform your legacy codebase into an AI-native ecosystem.**

**Terraformer** is the reference implementation of the **AI-Native Transformation Protocol (ANTP)**.
It acts as a meta-engine that analyzes existing "human-only" software projects and automatically generates the necessary configurations, documentation, and agent definitions to transform them into "AI-Ready" environments.

## 📖 The Philosophy

Traditional software projects are built on "Context Debt"—implicit knowledge that only humans understand. When we introduce AI (like GitHub Copilot) to these environments, it fails to understand the full picture, leading to hallucinations and poor quality code.

**Terraformer aims to solve this by refactoring the *project context* itself, not just the code.**

## 🏗 The AI Integration Stack (L1-L4)

Terraformer analyzes your repository and generates the **AI Integration Stack**, consisting of four layers:

| Layer | Name | Description | Output Artifacts |
| :--- | :--- | :--- | :--- |
| **L1** | **Constitution** | Defines the project's laws and coding standards. | `.github/copilot-instructions.md`, `.cursorrules` |
| **L2** | **Templates** | Standardizes repetitive workflows. | `*.prompt` (Prompt Files) |
| **L3** | **Knowledge** | Converts implicit knowledge into explicit, machine-readable formats. | `docs/llms.txt` (Markdown Context) |
| **L4** | **Agents** | Defines specialized roles to prevent "Generalist AI" issues. | Custom Agent Definitions / MCP Configs |

## 👥 The Specialized Six (Agent Roles)

Terraformer enforces the **Anti-Generalist Principle**: prohibiting the use of "do-it-all" AI. Instead, it defines strict roles for AI-Human pair programming.

### A. Management & Maintenance Layer
1.  **@Architect:** Manages architecture and impact analysis. **Holds authority for spec changes.**
2.  **@BusinessAnalyst:** Translates vague requirements into structured specifications (User Stories).
3.  **@QualityGuard:** Enforces the Constitution (L1) and reviews code.
4.  **@Librarian:** Maintains context freshness and syncs code with L3 documents.
5.  **@Gardener:** Autonomously handles technical debt, dependency updates, and refactoring.

### B. Execution Layer
6.  **@Developer:**
    * **Role:** Pure coding based on specs from @Architect/@BusinessAnalyst.
    * **Strict Constraint:** **NO authority to change specifications.** Must escalate issues back to @Architect if implementation conflicts with the plan.

## 🚀 Getting Started

*(Coming Soon: Instructions on how to run the Terraformer meta-prompt against your repo)*

## 📄 Project Charter

For a detailed explanation of the protocol and objectives, please refer to the [Project Charter](./docs/PROJECT_CHARTER.md).

---

Based on the **AI-Native Transformation Protocol (ANTP) v1.3**.
