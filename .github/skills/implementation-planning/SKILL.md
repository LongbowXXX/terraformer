---
name: implementation-planning
description: Break down high-level requirements into concrete implementation plans.
---

# Implementation Planning Skill

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
