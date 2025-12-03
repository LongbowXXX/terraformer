<!-- This document is generated/updated by the sync-doc workflow -->

# Glossary & Ubiquitous Language

## Key Concepts

| Term             | Definition                                                                                                         |
| ---------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Context Debt** | The implicit knowledge in a project (business rules, unwritten conventions) that causes AI to hallucinate or fail. |
| **ANTP**         | **AI-Native Transformation Protocol**. The methodology for converting legacy projects into AI-ready ecosystems.    |
| **Meta-Engine**  | A system (like Terraformer) that generates other systems (Agents/Skills) rather than running directly.             |
| **Constitution** | Refers to `AGENTS.md`. The immutable set of rules and context that governs the AI team.                            |

## Domain Terminology

| Term         | Definition                                                                                                              |
| ------------ | ----------------------------------------------------------------------------------------------------------------------- |
| **Agent**    | A specialized persona (e.g., `@Architect`) defined by a `.agent.md` file. It has specific authority and constraints.    |
| **Skill**    | A standardized procedure (SOP) defined by a `.prompt.md` file (e.g., `/plan`). It is a tool the agent can use.          |
| **Template** | A blueprint file (`.template.md`) used by Terraformer to generate the actual Agent or Skill files for a user's project. |
| **Prompts**  | The executable instructions that drive Copilot.                                                                         |

## Acronyms

| Acronym | Full Name                     | Description                                                        |
| ------- | ----------------------------- | ------------------------------------------------------------------ |
| **SOP** | Standard Operating Procedure  | A step-by-step guide for a specific task (implemented as a Skill). |
| **ADR** | Architectural Decision Record | A document capturing an important architectural decision.          |
| **LLM** | Large Language Model          | The underlying AI technology (e.g., GPT-4).                        |
