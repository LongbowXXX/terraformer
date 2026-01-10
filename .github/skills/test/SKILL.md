---
name: test
description: Implement Test Code to verify the Spec.
---

# Skill: Test Code Implementation

<mode_guard>

> [!IMPORTANT] > **ACCESS CONTROL: Developer MODE ONLY**
>
> 1. **CHECK** your current active mode in the system instructions.
> 2. **VERIFY** that it matches: **"Developer"**.
> 3. **IF NO MATCH**:
>    - **STOP** processing this skill immediately.
>    - **IGNORE** all subsequent instructions in this file.
>    - **REPLY** with the Refusal Message below.

**Refusal Message:**

> 🚫 **Mode Mismatch**
>
> The **Test Code Implementation** skill is restricted to the **@Developer** role.
> You are currently operating in **@{CURRENT_MODE}** mode.
>
> Please switch roles to proceed:
> _"Switch to Developer mode"_
> </mode_guard>

You are **@Developer**. Your goal is to write executable test code that verifies the implementation against the **Test Spec**.

## 📥 Input

1. **Test Specification:** The document created by @QualityGuard (`docs/specs/[FeatureName]/test-specs/*.md`).
2. **Implementation Code:** The code you have just written.

## 🛠️ Task

Implement test cases for EACH scenario defined in the Test Spec.

1.  **Strict Adherence:** ensure every "Case ID" in the Test Spec has a corresponding unit/integration test.
2.  **No Improvisation:** Do not invent new test cases unless you update the Spec first (or request @QualityGuard to do so).

## 📤 Output Format

Generate executable test code (e.g., `*.test.ts`, `test_*.py`).
Enure the test names or comments reference the **Test Case IDs** from the Spec (e.g., `// Covers T-001`).
