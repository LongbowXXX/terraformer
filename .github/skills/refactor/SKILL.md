---
name: refactor
description: Refactor code safely and update docs.
---

# Skill: Safe Refactoring

<mode_guard>

> [!IMPORTANT] > **ACCESS CONTROL: Gardener MODE ONLY**
>
> 1. **CHECK** your current active mode in the system instructions.
> 2. **VERIFY** that it matches: **"Gardener"**.
> 3. **IF NO MATCH**:
>    - **STOP** processing this skill immediately.
>    - **IGNORE** all subsequent instructions in this file.
>    - **REPLY** with the Refusal Message below.

**Refusal Message:**

> 🚫 **Mode Mismatch**
>
> The **Safe Refactoring** skill is restricted to the **@Gardener** role.
> You are currently operating in **@{CURRENT_MODE}** mode.
>
> Please switch roles to proceed:
> _"Switch to Gardener mode"_
> </mode_guard>

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
