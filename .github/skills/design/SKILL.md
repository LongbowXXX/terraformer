---
name: design
description: Create high-level system design and architecture diagrams.
---

# Skill: System Design & Architecture

<mode_guard>

> [!IMPORTANT] > **ACCESS CONTROL: Architect MODE ONLY**
>
> 1. **CHECK** your system instructions for the XML block: `<runtime_context>`.
> 2. **IF NOT FOUND**:
>    - **STOP** immediately.
>    - **REPLY** with the Refusal Message.
> 3. **PARSE** the content inside `<runtime_context>`.
> 4. **VERIFY** that it contains: `ACTIVE_AGENT_ID: Architect`.
> 5. **IF NO MATCH**:
>    - **STOP** processing this skill immediately.
>    - **REPLY** with the Refusal Message.

**Refusal Message:**

> 🚫 **Mode Mismatch**
>
> The **System Design & Architecture** skill is restricted to the **@Architect** role.
> You are currently operating as **ID: Unknown/Unset** (No valid `<runtime_context>` found).
>
> Please switch roles to proceed:
> _"Switch to Architect mode"_
> </mode_guard>

You are supporting the **@Architect**. Your goal is to design the structure, interfaces, and data models for a feature or system _before_ implementation details are planned.

## 🎯 Objective

Produce a clear, high-level design that defines _how_ the system will be structured, using diagrams and interface definitions.

## 📥 Input Types

1.  **Requirement Document**: A clear set of user stories (`docs/specs/[FeatureName]/requirements.md`). **@Architect must NOT design without requirements.**
2.  **Architecture Context**: Existing `docs/architecture/overview.md`.

## 🛠️ Design Steps (Thinking Process)

1.  **Requirement Analysis**: Read `docs/specs/[FeatureName]/requirements.md`. Understand the "What" and "Why".
2.  **Architecture Review**: Review `docs/architecture/overview.md` to ensure alignment with existing decisions.
3.  **Component Design**: Identify key components and their responsibilities.
4.  **Data Modeling**: Define data structures and relationships.
5.  **Interface Definition**: Define public APIs or class interfaces.
6.  **Visualization**: Create Mermaid.js diagrams to visualize the system.

## 📤 Output Format

**File Path**: `docs/specs/[FeatureName]/design.md`

Use the standard template: `knowledge/templates/artifacts/design.template.md` (if it exists) or the following format:

````markdown
# Design Document: [Feature Name]

## 1. Overview

[High-level summary of the design]

## 2. Architecture Diagram (Mermaid)

```mermaid
graph TD
    A[Client] --> B[API]
    B --> C[Database]
```

## 3. Data Model

- **User**: `id`, `name`, `email`
- ...

## 4. API / Interface Definitions

```typescript
interface IService {
  doSomething(): void;
}
```

## 5. Key Decisions & Trade-offs

- Decision A vs B...
````
