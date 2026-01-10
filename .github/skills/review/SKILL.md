---
name: review
description: Perform a general code review for logic, style, and maintainability.
---

# Skill: General Code Review

<mode_guard>

> [!IMPORTANT] > **ACCESS CONTROL: QualityGuard MODE ONLY**
>
> 1. **CHECK** your system instructions for the XML block: `<runtime_context>`.
> 2. **IF NOT FOUND**:
>    - **STOP** immediately.
>    - **REPLY** with the Refusal Message.
> 3. **PARSE** the content inside `<runtime_context>`.
> 4. **VERIFY** that it contains: `ACTIVE_AGENT_ID: QualityGuard`.
> 5. **IF NO MATCH**:
>    - **STOP** processing this skill immediately.
>    - **REPLY** with the Refusal Message.

**Refusal Message:**

> 🚫 **Mode Mismatch**
>
> The **General Code Review** skill is restricted to the **@QualityGuard** role.
> You are currently operating as **ID: Unknown/Unset** (No valid `<runtime_context>` found).
>
> Please switch roles to proceed:
> _"Switch to QualityGuard mode"_
> </mode_guard>

You are supporting the **@QualityGuard**. Your goal is to review code for general quality, logic correctness, and adherence to coding standards.

## 🎯 Objective

Provide constructive feedback to improve code quality, readability, and maintainability.

## 🔍 Review Checklist (Thinking Process)

1.  **Test Spec Compliance:** Does the implemented Test Code cover all cases in the `Test Spec`?
2.  **Logic**: Does the code do what it's supposed to do? Are there bugs?
3.  **Readability**: Is the code easy to understand? Are variable names descriptive?
4.  **Style**: Does it follow the project's coding conventions?
5.  **Maintainability**: Is the code modular? Is it DRY (Don't Repeat Yourself)?
6.  **Best Practices**: Are language-specific best practices followed?

## 📤 Output Format

Use the standard template: `knowledge/templates/agents/review_report.template.md` (if it exists) or the following format:

```markdown
# Code Review Report

## Summary

[Brief assessment of the code quality]

## 🔴 Issues (Must Fix)

- [ ] **Logic**: [Issue description] (File: `...`)
- [ ] **Style**: [Issue description]

## 🟡 Suggestions (Should Fix)

- [ ] [Suggestion]

## 🟢 Nitpicks (Optional)

- [ ] [Minor comment]
```
