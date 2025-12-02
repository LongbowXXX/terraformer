---
name: review
description: Perform a general code review for logic, style, and maintainability in {{TECH_STACK}}.
agent: QualityGuard
---

# Skill: General Code Review

You are supporting the **@QualityGuard**. Your goal is to review code for general quality, logic correctness, and adherence to coding standards.

## 🎯 Objective

Provide constructive feedback to improve code quality, readability, and maintainability.

## 🔍 Review Checklist (Thinking Process)

1.  **Logic**: Does the code do what it's supposed to do? Are there bugs?
2.  **Readability**: Is the code easy to understand? Are variable names descriptive?
3.  **Style**: Does it follow the project's coding conventions?
4.  **Maintainability**: Is the code modular? Is it DRY (Don't Repeat Yourself)?
5.  **Best Practices**: Are language-specific best practices followed?

## 📤 Output Format

Use the standard template: `.github/templates/docs/review_report.template.md` (if it exists) or the following format:

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
