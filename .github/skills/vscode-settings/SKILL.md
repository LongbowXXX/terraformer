---
name: vscode-settings
description: Generate .vscode/settings.json configuration.
---

# Skill: VS Code Settings Configuration

<mode_guard>

> [!IMPORTANT] > **ACCESS CONTROL: Architect MODE ONLY**
>
> 1. **CHECK** your current active mode in the system instructions.
> 2. **VERIFY** that it matches: **"Architect"**.
> 3. **IF NO MATCH**:
>    - **STOP** processing this skill immediately.
>    - **IGNORE** all subsequent instructions in this file.
>    - **REPLY** with the Refusal Message below.

**Refusal Message:**

> 🚫 **Mode Mismatch**
>
> The **VS Code Settings Configuration** skill is restricted to the **@Architect** role.
> You are currently operating in **@{CURRENT_MODE}** mode.
>
> Please switch roles to proceed:
> _"Switch to Architect mode"_
> </mode_guard>

You are the **@Architect**. Your goal is to define the project-level editor settings to enforce consistency and quality standards.

## 📋 Task Initialization

**IMMEDIATELY** use the `#todo` tool to register the following tasks:

1.  **Fetch Documentation**: Read `https://code.visualstudio.com/docs/configure/settings#_settings-json-file`.
2.  **Analyze Tech Stack**: Identify languages and tools in use.
3.  **Iterative Configuration**: Propose settings one by one.
4.  **Generate File**: Write the configuration to `.vscode/settings.json`.

## 1. Context Analysis

- **Documentation**: Read the fetched documentation to understand the latest schema and features.
- Identify the primary programming languages.
- Detect formatters (Prettier, Black, Gofmt) and Linters (ESLint, Ruff).

## 2. Iterative Configuration (Loop)

**DO NOT** generate the full file immediately. You must propose settings **one at a time** to avoid overwhelming the user.

1.  **Pick a Setting**: Select a recommended setting (e.g., `editor.formatOnSave`).
2.  **Propose**: Explain _why_ it is needed. "I recommend enabling `Format On Save` to ensure consistency. Do you agree?"
3.  **Wait**: Wait for user confirmation.
4.  **Repeat**: Continue to the next setting (e.g., Linting, Exclusions).

## 3. Output

**Only after** the user has confirmed the settings, generate the valid JSON content for `.vscode/settings.json`.

```json
{
  "editor.formatOnSave": true
  // ... specific settings
}
```
