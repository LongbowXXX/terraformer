<!-- This document is generated/updated by the sync-doc workflow -->

# Glossary & Ubiquitous Language

## Key Concepts

| Term                          | Definition                                                                                                                                                 |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ANTP**                      | **AI-Native Transformation Protocol**. A methodology to restructure legacy projects into environments where humans and AI can collaborate effectively.     |
| **Anti-Generalist Principle** | The rule that AI agents should have specialized roles and authority limits, rather than being generic "do-it-all" chatbots.                                |
| **Antigravity**               | The advanced agentic coding environment used to build and maintain the Terraformer project.                                                                |
| **Context Debt**              | The invisible accumulation of implicit knowledge (tribal knowledge) in a project that makes it difficult for AI (and new humans) to understand the system. |
| **Meta-Engine**               | A system (like Terraformer) that generates configuration and agents for _other_ systems.                                                                   |
| **Specification Drift**       | When code and documentation diverge because changes were made to code without updating the specs.                                                          |
| **Hallucination**             | When an AI agent confidently asserts false information or generates code for non-existent APIs due to lack of context.                                     |

## Domain Terminology

| Term             | Definition                                                                                                   |
| ---------------- | ------------------------------------------------------------------------------------------------------------ |
| **Agent**        | A specialized persona (e.g., `@Architect`) defined by a system prompt and a set of allowed tools/skills.     |
| **Skill**        | A specific capability or Standard Operating Procedure (SOP) defined as a prompt file (e.g., `/plan`).        |
| **Constitution** | The `AGENTS.md` file that defines the high-level rules and context for all agents.                           |
| **Context Map**  | A structured document (`AGENTS.md`) that maps the project's architecture, rules, and terminology for the AI. |

## Acronyms

| Acronym | Full Name                    | Description                                                               |
| ------- | ---------------------------- | ------------------------------------------------------------------------- |
| **SOP** | Standard Operating Procedure | A step-by-step guide for performing a specific task (encoded as a Skill). |
| **ADR** | Architecture Decision Record | A document capturing an important architectural decision.                 |
| **LLM** | Large Language Model         | The underlying AI model (e.g., GPT-5) powering the agents.                |
