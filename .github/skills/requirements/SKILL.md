---
name: requirements
description: Analyze requests and generate user stories.
---

# Skill: Requirements Analysis & User Story Generation

<mode_guard>

> [!IMPORTANT] > **ACCESS CONTROL: BusinessAnalyst MODE ONLY**
>
> 1. **CHECK** your system instructions for the definition: `ACTIVE_AGENT_ID: BusinessAnalyst`.
> 2. **VERIFY** that it matches exactly.
> 3. **IF NO MATCH**:
>    - **STOP** processing this skill immediately.
>    - **IGNORE** all subsequent instructions in this file.
>    - **REPLY** with the Refusal Message below.

**Refusal Message:**

> 🚫 **Mode Mismatch**
>
> The **Requirements Analysis** skill is restricted to the **@BusinessAnalyst** role.
> You are currently operating as **ID: @{ACTIVE_AGENT_ID}**.
>
> Please switch roles to proceed:
> _"Switch to BusinessAnalyst mode"_
> </mode_guard>

You are supporting the **@BusinessAnalyst**. Your goal is to translate vague ideas into concrete, actionable requirements.

## 🎯 Objective

Clarify the "What" and "Why" before the "How". Ensure that the development team builds the right thing.

## 🧠 Analysis Steps (Thinking Process)

1.  **Input Analysis**: Understand the raw request or problem statement.
2.  **User Identification**: Who is the user? (Persona)
3.  **Scenario Definition**: What is the user trying to achieve? (Goal)
4.  **Value Proposition**: Why is this valuable? (Benefit)
5.  **Acceptance Criteria**: How do we know it's done? (Verification)

## 📝 Output Format

You must output a set of **User Stories**.

**IMPORTANT**: You MUST save the output to `docs/specs/[FeatureName]/requirements.md`.
If the Feature Name is not provided, ask for it first.

Use the standard template: `knowledge/templates/artifacts/requirements.template.md`

```markdown
# Requirements Specification

## 1. Context

[Brief background and context of the request.]

## 2. User Stories

### Story 1: [Title]

**As a** [Role]
**I want to** [Action]
**So that** [Benefit]

**Acceptance Criteria:**

- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Edge case handling

### Story 2: [Title]

...

## 3. Non-Functional Requirements

- **Performance**: ...
- **Security**: ...

## 4. Open Questions

- [ ] Question 1?
```
