<!-- This document is generated/updated by the sync-doc workflow -->

# Glossary & Ubiquitous Language

## Key Concepts

| Term                    | Definition                                                                                                                                        |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Context Debt**        | Implicit knowledge causing AI failures. The gap between what humans know and what is written down.                                                |
| **ANTP**                | AI-Native Transformation Protocol. A 4-layer framework (Constitution, Skills, Knowledge, Agents) to transform legacy projects.                    |
| **Handoffs**            | A mechanism (often YAML property) for defining workflow transitions and responsibility transfers between agents.                                  |
| **Specification Drift** | The phenomenon where AI "fixes" code to make it work without updating the corresponding documentation or specifications, leading to a disconnect. |
| **{{TECH_STACK}}**      | A template placeholder used in agent/skill definitions that is replaced with the actual project technology stack during generation.               |
| **Anti-Generalist**     | The principle that generic AI coding assistants should not be trusted with architectural decisions. Specialized agents must be used.              |
| **Anti-Drift Lock**     | The rule that `@Developer` cannot change specifications and must escalate to `@Architect` if a discrepancy is found.                              |
| **Prototype Mode**      | A mode where strictness is relaxed (e.g., `@Developer` skips spec checks) for rapid prototyping or idea validation.                               |
| **Meta-Engine**         | A system that generates configuration for another system (e.g., GitHub Copilot) rather than executing runtime code itself.                        |

## Domain Terminology

| Term                 | Definition                                                                             |
| -------------------- | -------------------------------------------------------------------------------------- |
| **L1: Constitution** | The immutable rules and behavioral guardrails for all agents (defined in `AGENTS.md`). |
| **L2: Skills**       | Standardized Operating Procedures (SOPs) encapsulated as prompt files (e.g., `/plan`). |
| **L3: Knowledge**    | The explicit context map of the project (e.g., `agents-docs/`).                        |
| **L4: Agents**       | Specialized personas with defined roles and authorities (e.g., `@Architect`).          |

## Acronyms

| Acronym  | Full Name                         | Description                                                                  |
| -------- | --------------------------------- | ---------------------------------------------------------------------------- |
| **ANTP** | AI-Native Transformation Protocol | The core framework implemented by Terraformer.                               |
| **SOP**  | Standard Operating Procedure      | A step-by-step guide for a specific task, implemented as a Skill.            |
| **CoT**  | Chain of Thought                  | A prompting technique encouraging step-by-step reasoning.                    |
| **ADR**  | Architecture Decision Record      | A document capturing an important architectural decision (e.g., in `docs/`). |
