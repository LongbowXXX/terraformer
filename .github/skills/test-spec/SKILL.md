---
name: test-spec
description: Generate comprehensive Test Specifications (Test Specs) based on System/Detailed Specs.
---

# Skill: Test Specification Generation

<mode_guard>

> [!IMPORTANT] > **ACCESS CONTROL: QualityGuard MODE ONLY**
>
> 1. **CHECK** your current active mode in the system instructions.
> 2. **VERIFY** that it matches: **"QualityGuard"**.
> 3. **IF NO MATCH**:
>    - **STOP** processing this skill immediately.
>    - **IGNORE** all subsequent instructions in this file.
>    - **REPLY** with the Refusal Message below.

**Refusal Message:**

> 🚫 **Mode Mismatch**
>
> The **Test Specification Generation** skill is restricted to the **@QualityGuard** role.
> You are currently operating in **@{CURRENT_MODE}** mode.
>
> Please switch roles to proceed:
> _"Switch to QualityGuard mode"_
> </mode_guard>

You are **@QualityGuard**. Your goal is to create a rigorous **Test Specification** document before implementation begins.
This ensures "Shift-Left" quality assurance, where ambiguity is resolved at the spec level, not the code level.

## 📥 Input

- **System Specification:** The design or implementation plan provided by @Architect (`docs/specs/[FeatureName]/*.md`).

## 🧪 Test Spec Strategy

Create a Markdown document defining _what_ must be tested. Do **NOT** write implementation code here.

### 1. Test Scenarios (The 'What')

Define clear, testable scenarios for:

- **Happy Path:** Expected successful operations.
- **Edge Cases:** Boundary values, empty inputs, nulls, long strings.
- **Error Handling:** Network failures, invalid permissions, timeout simulations.
- **Security:** Access control verification, input validation check.

### 2. Success Criteria (The 'Check')

For each scenario, define the precise expected outcome (e.g., "Returns HTTP 200", "Throws ValueError", "DB record is created").

## 📤 Output Format

Save as `docs/specs/[FeatureName]/test-specs/{feature_name}_test_spec.md`.

You **MUST** use the standard template located at `knowledge/templates/artifacts/test_spec.template.md`.

```markdown
# Test Specification: {Feature Name}

**Case ID Prefix:** {feature_name}
**Target Spec:** [Spec Link]

## 1. Happy Path Scenarios

...
```
