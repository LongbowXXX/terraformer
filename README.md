# Terraformer 🌍🤖

> **Terraform your legacy codebase into an AI-Native ecosystem.**

**Terraformer** is the reference implementation of the **AI-Native Transformation Protocol (ANTP)**.
It acts as a meta-engine that analyzes existing "human-only" software projects and automatically generates the necessary configurations to transform them into "AI-Ready" environments where humans and AI agents can collaborate seamlessly.

## 🌟 The Problem: Context Debt

Traditional projects rely on implicit knowledge ("Context Debt") that only humans understand. When generic AI assistants are introduced, they fail due to a lack of context, leading to:
* **Hallucinations:** AI guessing business rules.
* **Specification Drift:** AI fixing code "on the fly" without updating docs.
* **Low Quality:** Inconsistent coding styles and security gaps.

## 🚀 The Solution: ANTP v1.4 (Roles & Skills)

Terraformer implements the **Roles & Skills Architecture**. It doesn't just give you a generic chatbot; it builds a **specialized AI team** equipped with **standard operating procedures (SOPs)**.

| Component | Function | Implementation |
| :--- | :--- | :--- |
| **L4: Agents** | Specialized Roles with Authority | `.github/agents/*.agent.md` |
| **L2: Skills** | Standardized Procedures (SOPs) | `.github/prompts/*.prompt.md` |
| **L3: Knowledge** | Explicit Context Map | `llms.txt` |
| **L1: Constitution** | Immutable Rules | `.github/copilot-instructions.md` |

## 🛠️ How to Use (Installation)

No complex installation required. Terraformer leverages the native configuration features of GitHub Copilot (VS Code).

### 1. Install to your project
Copy the `.github` folder from this repository to the root of your target project.

```bash
# Clone Terraformer
git clone [https://github.com/your-org/terraformer.git](https://github.com/your-org/terraformer.git)

# Copy the configuration engine to your legacy project
cp -r terraformer/.github/prompts ./my-legacy-project/.github/
cp -r terraformer/.github/templates ./my-legacy-project/.github/
````

### 2\. Generate Your AI Team (L4 & L2)

1.  Open your project in **VS Code** (ensure GitHub Copilot Chat extension is active).
2.  Open `README.md` or key source files to provide context.
3.  Type **`/terraformer`** in the Copilot Chat.
4.  Terraformer will analyze your project and generate:
      * **6 Agent Definitions** (e.g., `architect.agent.md`) customized for your tech stack.
      * **3 Standard Skills** (`plan.prompt.md`, `refactor.prompt.md`, etc.).
5.  Save the outputs to `.github/agents/` and `.github/prompts/`.

### 3\. Generate Context Map (L3)

1.  Type **`/terraform-context`** in the Chat.
2.  Terraformer will generate a high-density `llms.txt`.
3.  Save it to the project root.

## 👥 The Specialized Six (Agents & Skills)

Once generated, you can invoke these agents via `@Name`. They come equipped with specialized skills (`#skill`).

| Agent | Role | Authority | Equipped Skill |
| :--- | :--- | :--- | :--- |
| **@Architect** | **Decision Maker** | ✅ Design & Specs | `#plan` (Impact Analysis & Planning) |
| **@BusinessAnalyst** | **Translator** | ✅ Requirements | `#requirements` (User Story Gen) |
| **@QualityGuard** | **Enforcer** | ✅ Merge Approval | `#audit` (Code Review Checklist) |
| **@Librarian** | **Keeper** | ✅ Documentation | `#doc-sync` (Doc Consistency Check) |
| **@Gardener** | **Maintainer** | ✅ Refactoring | `#refactor` (Safe Refactoring) |
| **@Developer** | **Implementer** | ❌ **No Spec Changes** | `#test` (TDD & Verification) |

> **The Anti-Generalist Principle:** `@Developer` is strictly prohibited from changing specifications. If a blocker is found, it must escalate to `@Architect`.

## 📄 Documentation

  * [Project Charter (ANTP v1.4)](https://www.google.com/search?q=./docs/PROJECT_CHARTER.md) - The core philosophy.
  * [Development Context (ADR)](https://www.google.com/search?q=./docs/DEVELOPMENT_CONTEXT.md) - Architecture decisions.

-----

Powered by **ANTP v1.4** | *Making human-only projects habitable for AI.*
