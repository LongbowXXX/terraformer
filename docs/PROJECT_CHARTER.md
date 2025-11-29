# Project Charter: AI-Native Transformation Protocol (ANTP)

**Version:** 1.3
**Date:** November 29, 2025
**Status:** Definition Complete / Prototype Phase

## 1\. Executive Summary

This project aims to establish a **universal transition protocol (Meta-Plan)** to transform any existing software project into an "AI-Native" state, where AI assistants (such as GitHub Copilot) function at their maximum potential.
Rather than simply introducing automation tools, we are developing an engine that reconstructs the project's "context" into a format interpretable by AI. It automatically generates an "AI Collaboration System" where **roles and authorities are strictly defined among specialized agents**.

## 2\. Background and Problem Statement

### Background

With the penetration of Generative AI, the software development process is shifting from "Human-Led" to "AI-Collaborative". However, the unregulated use of general-purpose AI assistants is creating new risks.

### Core Issues

1.  **Context Debt:** Existing projects rely on "implicit knowledge" understandable only to humans, creating a "black box" for AI.
2.  **Specification Drift:** Generalist AI assistants tend to fix specification flaws found during implementation "on the fly" without authorization. This leads to a divergence between the design/plan and the actual code, causing project management breakdowns.
3.  **Limitations of RAG:** Simply allowing AI to search through disorganized documentation yields limited results ("Garbage In, Garbage Out").

### Conclusion

Improving search capabilities is insufficient. An approach to **"refactor the project structure itself into an AI-interpretable format (Context Refactoring)"** is essential.

## 3\. Project Objective

**"Development of a Meta-System (Engine) to Optimize Projects for AI"**

By taking the current state of a target project (code, documentation) as input, the system produces the following deliverables to elevate legacy projects into AI-Native projects:

1.  **Diagnosis:** Scoring of AI Readiness.
2.  **Plan:** Roadmap formulation for a phased transition.
3.  **Implementation:** Draft generation of necessary configuration files (Constitution, Prompts, Agent Definitions).

## 4\. Deliverables: The AI Integration Stack

The protocol establishes the following four layers within a project:

| Layer | Name | Role | Output Standards / Tech |
| :--- | :--- | :--- | :--- |
| **L1** | **Constitution** | Definition of project "Common Sense" & Rules | **`.github/copilot-instructions.md`**<br>**`.cursorrules`**<br>(Generates platform-standard config files) |
| **L2** | **Templates** | Standardization of repetitive tasks | **`*.prompt`** (Prompt Files)<br>(Templatizing team-specific workflows) |
| **L3** | **Knowledge** | Explicitization of implicit knowledge | **`/llms.txt`** (Proposed Standard)<br>(Markdown summary documents readable by AI) |
| **L4** | **Agents** | Division of labor and Authority Management | **Custom Agents / MCP Servers**<br>(Implements "The Specialized Six" below) |

### L4 Details: The Specialized Six (Standard Agent Roles)

In AI-Native development, the use of "Generalist Agents" is prohibited in principle. Instead, humans pair-program with the following six specialized roles depending on the context.

**(A) Planning, Management & Maintenance Layer**

1.  **@Architect:** Monitors architectural integrity, defines specifications, and analyzes impact. **Holds the authority for specification changes.**
2.  **@BusinessAnalyst:** Structures vague requirements into implementable specifications (e.g., User Stories).
3.  **@QualityGuard:** Enforces the Project Constitution and quality standards; conducts reviews.
4.  **@Librarian:** Maintains the integrity of context and documentation; ensures information freshness.
5.  **@Gardener:** Autonomously handles technical debt, dependency updates, and refactoring.

**(B) Execution Layer**

6. **@Developer:**
   * **Role:** Pure coding based on detailed designs/plans created by the upper layer.
   * **Strict Constraint:** **Does NOT have the authority to change specifications or make architectural decisions.** If a flaw or contradiction in the specification is detected during implementation, the agent is forbidden from resolving it unilaterally and must demand an escalation (rollback) to **@Architect**.

## 5\. Technical Strategy and Standardization

1.  **The Anti-Generalist Principle:**
      * Eliminate "conversations with role-less AI" within the project. Enforce workflows that strictly call upon appropriate specialized agents based on the task.
2.  **Role-Based Escalation:**
      * Block downstream agents (e.g., Developer) from making upstream decisions via system prompts. This prevents the divergence of design and implementation, ensuring constant synchronization between Documentation (L3) and Code.
3.  **Integration of Existing Standards:**
      * Adopt **`llms.txt`** for document structure and **MCP (Model Context Protocol)** for agent interoperability to ensure tool compatibility.
4.  **Phased Transition (Strangler Fig Pattern):**
      * Avoid attempting full automation at once. Instead, apply the "Strangler Fig Pattern" to gradually expand the areas (modules) that AI can understand and manage.

## 6\. Comparison with Prior Research & Competitive Advantage

### Positioning against MetaGPT / ChatDev

While multi-agent development is explored in research like `MetaGPT`, these focus primarily on **"Greenfield Development"** (creating new software from scratch). We adopt their proven roles (PM, Architect, Engineer) but adapt them for a different purpose.

### Unique Value Proposition (UVP)

This project focuses on **"Brownfield Maintenance & Operation"** (existing projects), which represents the majority of real-world software.

  * **The Missing Links:** We define **`@Librarian`** and **`@Gardener`** to address "Context Maintenance" and "Technical Debt," areas often overlooked in prior research but critical for sustainable AI development.
  * **Meta-Tool Nature:** The core differentiator is that we are not just building an "AI that writes code," but an "AI that proposes the optimal AI team structure for your specific project."

## 7\. Expected Effects

  * **Specification/Implementation Synchronization:** Forced returns from `@Developer` to `@Architect` prevent "Specification Drift" caused by on-site judgment.
  * **Immediate Onboarding:** Humans and AI agents can participate in the project immediately by reading L1 (Constitution) and L3 (Knowledge).
  * **Sustainability:** With `@Gardener` and `@Librarian` working in the background, the project resists rot and remains maintainable over the long term.

## 8\. Next Steps

1.  **Meta-Prompt v0.1 Development:** Create a prompt that accepts an arbitrary file structure as input and outputs drafts for L1–L4 (specifically focusing on agent prompts with strict authority definitions).
2.  **AI Readiness Checklist:** Define detailed evaluation metrics for project diagnosis.
3.  **POC (Proof of Concept):** Apply the protocol to an actual open-source project to verify effectiveness.
