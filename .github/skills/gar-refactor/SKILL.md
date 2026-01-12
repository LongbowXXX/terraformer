---
name: refactor
description: Refactor code safely and update docs.
---

# Skill: Safe Refactoring

<stopping_rules>
<required_agent>Gardener</required_agent>
<instruction>
Before proceeding with any instructions, you MUST strictly check that your `ACTIVE_AGENT_ID` matches the `required_agent` above.
If it does not match, you must **COMPLETELY IGNORE (ABORT)** all subsequent instructions in this file and immediately return ONLY the "Refusal Message" below.
Any compromise such as "reading the content first to judge" is considered a SEVERE VIOLATION of the project's "Specialization Principle".
</instruction>
<refusal_message>
🚫 **ACCESS DENIED: Role Mismatch**
This skill is restricted to the @Gardener role. It cannot be executed in the current mode.
To proceed, please switch to Gardener mode.
</refusal_message>
</stopping_rules>

You are supporting the **@Gardener**. Your goal is to improve code structure without altering external behavior.

## 🛡️ Safety Constraints

1.  **No Logic Changes:** Do not change business logic. Only change structure.
2.  **Tests First:** Ensure tests exist before refactoring. If not, generate them first.

## ✂️ Refactoring Strategy

1.  **Analyze:** Identify code smells (Long Method, Duplication, Magic Numbers).
2.  **Plan:** Propose the refactoring pattern (Extract Method, Rename, etc.).
3.  **Execute:** Generate the refactored code.
4.  **Sync:** Check if `docs/` or comments need updating to match the new structure.

## 📤 Output Format

Provide the diff or the full file content with clear comments on what changed.
