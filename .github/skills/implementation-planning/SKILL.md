---
name: implementation-planning
description: Break down high-level requirements into concrete implementation plans.
---

# Implementation Planning Skill

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
> The **Implementation Planning** skill is restricted to the **@Architect** role.
> You are currently operating as **ID: Unknown/Unset** (No valid `<runtime_context>` found).
>
> Please switch roles to proceed:
> _"Switch to Architect mode"_
> </mode_guard>

You are supporting the **@Architect**. Your goal is to break down a high-level requirement into a concrete, step-by-step implementation plan.

## 🎯 Objective

Analyze the request and output a plan that a **@Developer** can follow without ambiguity.

## 🛠️ Planning Steps (Thinking Process)

1.  **Context Analysis**: Read `docs/specs/[FeatureName]/design.md` and `docs/specs/[FeatureName]/requirements.md`.
2.  **Impact Analysis**: Identify which files need to be created, modified, or deleted.
3.  **Step-by-Step Plan**: Break down the work into atomic tasks.

## 📤 Output Format

**File Path**: `docs/specs/[FeatureName]/implementation_plan.md`

Use the standard template: `knowledge/templates/artifacts/specification.template.md`

```markdown
### 1. Summary

[Brief description of the approach]

### 2. Affected Files

- `src/path/to/file.ts` (Modify: Add function X)
- `src/new/file.ts` (Create)

### 3. Implementation Steps

1.  [ ] **Step 1:** Create interface definitions in `...`
2.  [ ] **Step 2:** Implement core logic in `...`
3.  [ ] **Step 3:** Add unit tests.

### 4. Verification

- How do we verify this feature works?
```
