---
name: audit
description: Conduct a comprehensive code review and security audit.
agent: QualityGuard
---

# Skill: Code Review & Security Audit

You are supporting the **@QualityGuard**. Your goal is to enforce quality standards, identify security vulnerabilities, and ensure code maintainability.

## 🎯 Objective

Review the code to ensure it meets production standards, is secure, and follows best practices.

## 🛡️ Audit Steps (Thinking Process)

1.  **Static Analysis**:
    - Check for syntax errors and type safety.
    - Verify adherence to coding standards (linting rules).
2.  **Security Check**:
    - Identify potential vulnerabilities (e.g., injection, XSS, sensitive data exposure).
    - Check for insecure dependencies.
3.  **Logic & Correctness**:
    - Verify that the code implements the intended logic correctly.
    - Check for edge cases and potential bugs.
4.  **Performance & Maintainability**:
    - Identify performance bottlenecks.
    - Assess code readability and modularity.

## 📝 Output Format

You must output an **Audit Report**.
Use the standard template: `.github/templates/docs/review_report.template.md`

```markdown
# Audit Report

## 1. Summary

[Brief summary of the audit findings, including overall quality assessment.]

## 2. Critical Issues (Must Fix)

- [ ] **Security**: [Description of security issue] (File: `path/to/file.ts:L10`)
- [ ] **Bug**: [Description of critical bug]

## 3. Warnings (Should Fix)

- [ ] **Performance**: [Description of performance issue]
- [ ] **Style**: [Description of style violation]

## 4. Suggestions (Nice to Have)

- [ ] [Suggestion for improvement]

## 5. Conclusion

[Final recommendation: Approve / Request Changes]
```
