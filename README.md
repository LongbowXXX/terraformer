# Terraformer 🌍🤖

> **Terraform your legacy codebase into an AI-Native ecosystem.**

**Terraformer** is the reference implementation of the **AI-Native Transformation Protocol (ANTP)**.
It acts as a meta-engine that analyzes existing "human-only" software projects and automatically generates the necessary configurations to transform them into "AI-Ready" environments where humans and AI agents can collaborate seamlessly.

> [!IMPORTANT]
> Terraformer introduction video in Japanese.

https://github.com/user-attachments/assets/79119803-cb99-452f-894c-f973e5915877

## 🌟 The Problem: Context Debt

Traditional projects rely on implicit knowledge ("Context Debt") that only humans understand. When generic AI assistants are introduced, they fail due to a lack of context, leading to:

- **Hallucinations:** AI guessing business rules.
- **Specification Drift:** AI fixing code "on the fly" without updating docs.
- **Low Quality:** Inconsistent coding styles and security gaps.

## 🚀 The Solution: ANTP v1.4 (Roles & Skills)

Terraformer implements the **Roles & Skills Architecture**. It doesn't just give you a generic chatbot; it builds a **specialized AI team** equipped with **standard operating procedures (SOPs)**.

| Component            | Function                         | Implementation                    |
| :------------------- | :------------------------------- | :-------------------------------- |
| **L1: Constitution** | Immutable Rules                  | [`AGENTS.md`](./AGENTS.md)        |
| **L2: Skills**       | Standardized Procedures (SOPs)   | `.github/prompts/*.prompt.md`     |
| **L3: Knowledge**    | Explicit Context Map             | [`agents-docs/*`](./agents-docs/) |
| **L4: Agents**       | Specialized Roles with Authority | `.github/agents/*.agent.md`       |

## 🔄 The Paradigm Shift: From Agile to Document-Driven

To make AI collaboration effective, we must invert traditional Agile values.

| Traditional Agile (Human-Centric)       | ANTP / AI-Native (Agent-Centric)        | Why?                                                                                  |
| :-------------------------------------- | :-------------------------------------- | :------------------------------------------------------------------------------------ |
| **Tacit Knowledge** (Oral tradition)    | **Explicit Context** (Machine-readable) | AI cannot hear what you say in standups. It only knows what is written.               |
| **Working Software** over Documentation | **Documentation IS the Code**           | Natural language specs are the "High-Level Source Code" that AI compiles into syntax. |
| **Fail Fast in Code**                   | **Fail Fast in Spec**                   | Coding is cheap/instant. Debugging vague requirements is expensive.                   |

In this paradigm, **Documentation is not a chore; it is the source code.**

## 🛠️ How to Use (Installation)

No complex installation required. Terraformer leverages the native configuration features of GitHub Copilot (VS Code).

### 1. Install to your project

Copy the `.github` folder from this repository to the root of your target project.

```bash
# Clone Terraformer
git clone https://github.com/LongbowXXX/terraformer.git

# Copy the configuration engine to your legacy project
cp -r terraformer/.github/prompts ./my-legacy-project/.github/
cp -r terraformer/.github/template-* ./my-legacy-project/.github/
cp -r terraformer/knowledge ./my-legacy-project/
```

### Alternative: Install via Copilot Chat

If you are using GitHub Copilot Chat, you can ask it to install Terraformer for you. Paste the following prompt into the Chat:

> Check the latest release on https://github.com/LongbowXXX/terraformer/releases.
> Download the Source code (zip) of the latest version.
> Unzip it and copy the `.github` folder and `knowledge` folder to the root of this project.
> **IMPORTANT**: Ensure you do NOT create nested folders (e.g., `.github/.github`). The contents should be directly in `.github` and `knowledge` at the project root.
> Clean up the downloaded zip and extracted folder after copying.

_The era of humans typing commands is over! 😜🚀_

### 2. Generate Context Map (L3)

1.  Type **`/terraform-context`** in the Chat.
    - _Tip: You can specify a language: `/terraform-context Japanese`_
2.  Terraformer will generate a high-density `AGENTS.md`.
3.  Save it to the project root.

### 3. Generate Your AI Team (L4 & L2)

1.  Open your project in **VS Code** (ensure GitHub Copilot Chat extension is active).
2.  Open `AGENTS.md` (generated in step 2) to provide context.
3.  Type **`/terraformer`** in the Copilot Chat.
    - _Tip: You can specify a language: `/terraformer Japanese`_
4.  Terraformer will analyze your project and **generate or update**:
    - **Agent Definitions** (e.g., `architect.agent.md`) customized for your tech stack.
    - **Standard Skills** (`plan.prompt.md`, `refactor.prompt.md`, etc.).
5.  Save the outputs to `.github/agents/` and `.github/prompts/`.
    - _Note: You can re-run `/terraformer` at any time to update your agents and skills if the project context changes._

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

### 🧩 Extensibility (Custom Skills)

Terraformer is designed to be **extensible**. You are not limited to the default skills.
Use **`/create-custom-prompt`** to generate project-specific skills (e.g., `/migration`, `/deploy`, `/api-gen`) tailored to your unique workflow.

### ⚡ Prototype Mode (Speed > Strictness)

For rapid prototyping or idea validation, you can explicitly request **"Prototype Mode"**.

> "Build a prototype for [Feature] (Prototype Mode)"

In this mode:

- `@Developer` skips formal spec checks.
- `@QualityGuard` relaxes review criteria.
- Generated code is marked with `/* PROTOTYPE */` and is **not production-ready**.

## 📚 Universal Knowledge (`knowledge/`)

This directory contains universally available knowledge and templates that do not depend on a specific project.
It provides resources such as:

- **Prompting Techniques**: Best practices for interacting with AI agents.
- **Review Guidelines**: Standardized perspectives for code reviews.
- **Templates**: Reusable patterns for documentation and workflows.
- **AI Literacy**: Resources to make _humans_ AI-Ready and effective at using AI agents.
- **XML Structured Prompting**: Comprehensive guide on using XML tags for better LLM control.
- **Specification Guidelines**: Synergizing Gherkin behavior and Mermaid diagrams for unambiguous specs.
- **Workflow**: Standardized [Collaboration Process](./knowledge/workflow/workflow.md) for Agents and Humans.

## 📄 Documentation

- [Project Charter (ANTP v1.4)](./docs/PROJECT_CHARTER.md) - The core philosophy.
- [Development Context (ADR)](./docs/DEVELOPMENT_CONTEXT.md) - Architecture decisions.
- [AI-Oriented Docs](./agents-docs/) - Detailed documentation for AI agents and developers.
- [Context Map for Agents](./AGENTS.md) - High-density project summary for AI coding agents.

## 📓 Interactive Guide (Google NotebookLM)

We have published a Google NotebookLM workspace pre-loaded with this repository.
**Note: The content inside this Notebook is in Japanese.**

You can use it to:

- Ask questions about the project using the Chat interface.
- Listen to / Watch the generated introductory content (Audio Overview).

> [!IMPORTANT]  
> 🔗 [Open Google NotebookLM](https://notebooklm.google.com/notebook/19713d26-a3bd-4f4f-9bb7-78c52829c660)

## 🤖 Meet Our Mascot: ANTP-Bot ("Ant")

Terraformer isn't just a tool; it's a mission to cultivate legacy code.
Our mascot, **ANTP-Bot** (affectionately known as **"Ant"**), embodies this mission.

![ANTP-Bot Mascot](./mascot.png)

> ANTP-Bot, a diligent robotic ant, is shown using its terraforming tool to convert barren, wired ground into flourishing digital circuits and greenery. Its backpack is loaded with blueprints for a better future.

Just like a colony of ants working together to build complex structures, the ANTP (AI-Native Transformation Protocol) agents coordinate to transform your project into a thriving AI-Native ecosystem.

---

Powered by **ANTP v1.4** | _Making human-only projects habitable for AI._
