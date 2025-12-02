# Glossary & Ubiquitous Language

This document defines the core concepts, terminology, and shared understanding (Ubiquitous Language) for the Terraformer project. It serves as the **L3: Knowledge** layer in the ANTP framework.

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

## Domain Model

(Placeholder for future domain model diagrams or descriptions)

## Business Rules

- **AI-First**: All features must be designed with AI agents as primary users/maintainers.
- **Explicit over Implicit**: All context must be explicitly documented.
