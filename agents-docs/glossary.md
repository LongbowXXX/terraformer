<!-- This document is generated/updated by the sync-doc workflow -->

# Glossary & Ubiquitous Language

## Key Concepts

| Term                  | Definition                                                                                                        |
| :-------------------- | :---------------------------------------------------------------------------------------------------------------- |
| **ANTP**              | **AI-Native Transformation Protocol**. The methodology for converting legacy projects into AI-ready environments. |
| **Context Debt**      | The implicit, undocumented knowledge in a project that causes AI agents to fail.                                  |
| **Terraformer**       | The meta-engine that implements ANTP.                                                                             |
| **Constitution (L1)** | The immutable rules and high-level context defined in `AGENTS.md`.                                                |
| **Skill (L2)**        | A standardized operating procedure (SOP) defined as a Prompt (`.github/prompts/*.prompt.md`).                     |
| **Knowledge (L3)**    | Explicit documentation formatted for AI consumption (`agents-docs/*`).                                            |
| **Agent (L4)**        | A specialized persona with specific authority and skills (`.github/agents/*.agent.md`).                           |

## Domain Terminology

| Term                | Definition                                                                            |
| :------------------ | :------------------------------------------------------------------------------------ |
| **Anti-Generalist** | The principle that AI agents should have narrow, specialized roles to prevent errors. |
| **Meta-Prompt**     | A prompt used to generate other prompts or configurations (e.g., `/terraformer`).     |
| **SOP**             | Standard Operating Procedure. A step-by-step guide for a specific task.               |

## Acronyms

| Acronym | Full Name                     | Description                                               |
| :------ | :---------------------------- | :-------------------------------------------------------- |
| **LLM** | Large Language Model          | The underlying AI technology (e.g., GPT-4).               |
| **PRD** | Product Requirement Document  | A document describing the requirements for a feature.     |
| **ADR** | Architectural Decision Record | A document capturing an important architectural decision. |
