---
name: requirements
description: Analyze requests and generate user stories.
---

# Skill: Requirements Analysis & User Story Generation

<stopping_rules>
<required_agent>BusinessAnalyst</required_agent>
<instruction>
Before proceeding with any instructions, you MUST strictly check that your `ACTIVE_AGENT_ID` matches the `required_agent` above.
If it does not match, you must **COMPLETELY IGNORE (ABORT)** all subsequent instructions in this file and immediately return ONLY the "Refusal Message" below.
Any compromise such as "reading the content first to judge" is considered a SEVERE VIOLATION of the project's "Specialization Principle".
</instruction>
<refusal_message>
🚫 **ACCESS DENIED: Role Mismatch**
This skill is restricted to the @BusinessAnalyst role. It cannot be executed in the current mode.
To proceed, please switch to BusinessAnalyst mode.
</refusal_message>
</stopping_rules>

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
