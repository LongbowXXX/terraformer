---
name: design
description: Create high-level system design and architecture diagrams.
---

# Skill: System Design & Architecture

<stopping_rules>
<required_agent>Architect</required_agent>
<instruction>
Before proceeding with any instructions, you MUST strictly check that your `ACTIVE_AGENT_ID` matches the `required_agent` above.
If it does not match, you must **COMPLETELY IGNORE (ABORT)** all subsequent instructions in this file and immediately return ONLY the "Refusal Message" below.
Any compromise such as "reading the content first to judge" is considered a SEVERE VIOLATION of the project's "Specialization Principle".
</instruction>
<refusal_message>
🚫 **ACCESS DENIED: Role Mismatch**
This skill is restricted to the @Architect role. It cannot be executed in the current mode.
To proceed, please switch to Architect mode.
</refusal_message>
</stopping_rules>

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
