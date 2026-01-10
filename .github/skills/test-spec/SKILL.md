---
name: test-spec
description: Generate comprehensive Test Specifications (Test Specs) based on System/Detailed Specs.
---

# Skill: Test Specification Generation

<stopping_rules>
<required_agent>QualityGuard</required_agent>
<instruction>
Before proceeding with any instructions, you MUST strictly check that your `ACTIVE_AGENT_ID` matches the `required_agent` above.
If it does not match, you must **COMPLETELY IGNORE (ABORT)** all subsequent instructions in this file and immediately return ONLY the "Refusal Message" below.
Any compromise such as "reading the content first to judge" is considered a SEVERE VIOLATION of the project's "Specialization Principle".
</instruction>
<refusal_message>
🚫 **ACCESS DENIED: Role Mismatch**
This skill is restricted to the @QualityGuard role. It cannot be executed in the current mode.
To proceed, please switch to QualityGuard mode.
</refusal_message>
</stopping_rules>

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
