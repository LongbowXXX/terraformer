# Terraformer 🌍🤖

> **Terraform your legacy codebase into an AI-Native ecosystem.**

**Terraformer** is the reference implementation of the **AI-Native Transformation Protocol (ANTP)**.
It acts as a meta-engine that analyzes existing "human-only" software projects and automatically generates the necessary configurations to transform them into "AI-Ready" environments where humans and AI agents can collaborate seamlessly.

## 🌟 The Problem: Context Debt

Traditional projects rely on implicit knowledge ("Context Debt") that only humans understand. When generic AI assistants are introduced, they fail due to a lack of context, leading to:

- **Hallucinations:** AI guessing business rules.
- **Specification Drift:** AI fixing code "on the fly" without updating docs.
- **Low Quality:** Inconsistent coding styles and security gaps.

## 🚀 The Solution: ANTP v1.4 (Roles & Skills)

Terraformer implements the **Roles & Skills Architecture**. It doesn't just give you a generic chatbot; it builds a **specialized AI team** equipped with **standard operating procedures (SOPs)**.

| Component            | Function                         | Implementation                    |
| :------------------- | :------------------------------- | :-------------------------------- |
| **L1: Constitution** | Immutable Rules                  | `.github/copilot-instructions.md` |
| **L2: Skills**       | Standardized Procedures (SOPs)   | `.github/prompts/*.prompt.md`     |
| **L3: Knowledge**    | Explicit Context Map             | [`AGENTS.md`](./AGENTS.md)        |
| **L4: Agents**       | Specialized Roles with Authority | `.github/agents/*.agent.md`       |

## 🛠️ How to Use (Installation)

No complex installation required. Terraformer leverages the native configuration features of GitHub Copilot (VS Code).

### 1. Install to your project

Copy the `.github` folder from this repository to the root of your target project.

```bash
# Clone Terraformer
git clone https://github.com/LongbowXXX/terraformer.git

# Copy the configuration engine to your legacy project
cp -r terraformer/.github/prompts ./my-legacy-project/.github/
cp -r terraformer/.github/templates ./my-legacy-project/.github/
```

### 2. Generate Context Map (L3)

1.  Type **`/terraform-context`** in the Chat.
2.  Terraformer will generate a high-density `AGENTS.md`.
3.  Save it to the project root.

### 3. Generate Your AI Team (L4 & L2)

1.  Open your project in **VS Code** (ensure GitHub Copilot Chat extension is active).
2.  Open `AGENTS.md` (generated in step 2) to provide context.
3.  Type **`/terraformer`** in the Copilot Chat.
4.  Terraformer will analyze your project and **generate or update**:
    - **Agent Definitions** (e.g., `architect.agent.md`) customized for your tech stack.
    - **Standard Skills** (`plan.prompt.md`, `refactor.prompt.md`, etc.).
5.  Save the outputs to `.github/agents/` and `.github/prompts/`.
    - *Note: You can re-run `/terraformer` at any time to update your agents and skills if the project context changes.*

## 👥 The Specialized Agents (Agents & Skills)

Once generated, you can invoke these agents via `@Name`. They come equipped with specialized skills (`#skill`).

| Agent                | Role               | Authority              | Equipped Skill                       |
| :------------------- | :----------------- | :--------------------- | :----------------------------------- |
| **@Architect**       | **Decision Maker** | ✅ Design & Specs      | `/plan` (Impact Analysis & Planning) |
| **@BusinessAnalyst** | **Translator**     | ✅ Requirements        | `/requirements` (User Story Gen)     |
| **@QualityGuard**    | **Enforcer**       | ✅ Merge Approval      | `/audit` (Code Review Checklist)     |
| **@Librarian**       | **Keeper**         | ✅ Documentation       | `/doc-sync` (Doc Consistency Check)  |
| **@Gardener**        | **Maintainer**     | ✅ Refactoring         | `/refactor` (Safe Refactoring)       |
| **@Debugger**        | **Bug Hunter**     | ✅ Bug Analysis        | `/debug` (Root Cause Analysis)       |
| **@Developer**       | **Implementer**    | ❌ **No Spec Changes** | `/test` (TDD & Verification)         |

> **The Anti-Generalist Principle:** `@Developer` is strictly prohibited from changing specifications. If a blocker is found, it must escalate to `@Architect`.

### ⚡ Prototype Mode (Speed > Strictness)

For rapid prototyping or idea validation, you can explicitly request **"Prototype Mode"**.

> "Build a prototype for [Feature] (Prototype Mode)"

In this mode:
- `@Developer` skips formal spec checks.
- `@QualityGuard` relaxes review criteria.
- Generated code is marked with `/* PROTOTYPE */` and is **not production-ready**.

## 📄 Documentation

- [Project Charter (ANTP v1.4)](./docs/PROJECT_CHARTER.md) - The core philosophy.
- [Development Context (ADR)](./docs/DEVELOPMENT_CONTEXT.md) - Architecture decisions.
- [AI-Oriented Docs](./agents-docs/) - Detailed documentation for AI agents and developers.
- [Context Map for Agents](./AGENTS.md) - High-density project summary for AI coding agents.

## 🤖 Meet Our Mascot: ANTP-Bot ("Ant")

Terraformer isn't just a tool; it's a mission to cultivate legacy code.
Our mascot, **ANTP-Bot** (affectionately known as **"Ant"**), embodies this mission.

![ANTP-Bot Mascot](./mascot.png)

> ANTP-Bot, a diligent robotic ant, is shown using its terraforming tool to convert barren, wired ground into flourishing digital circuits and greenery. Its backpack is loaded with blueprints for a better future.

Just like a colony of ants working together to build complex structures, the ANTP (AI-Native Transformation Protocol) agents coordinate to transform your project into a thriving AI-Native ecosystem.

---

Powered by **ANTP v1.4** | _Making human-only projects habitable for AI._
