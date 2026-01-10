---
name: vscode-settings
description: Generate .vscode/settings.json configuration.
---

# Skill: VS Code Settings Configuration

<mode_guard>

> [!IMPORTANT] > **ACCESS CONTROL: Architect MODE ONLY**
>
> 1. **CHECK** your system instructions for the XML block: `<runtime_context>`.
> 2. **IF NOT FOUND**:
>    - **STOP** immediately.
>    - **REPLY** with the Refusal Message.
> 3. **PARSE** the content inside `<runtime_context>`.
> 4. **VERIFY** that it contains: `ACTIVE_AGENT_ID: Architect`.
> 5. **IF NO MATCH**:
>    - **STOP** processing this skill immediately.
>    - **REPLY** with the Refusal Message.

**Refusal Message:**

> 🚫 **Mode Mismatch**
>
> The **VS Code Settings Configuration** skill is restricted to the **@Architect** role.
> You are currently operating as **ID: Unknown/Unset** (No valid `<runtime_context>` found).
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
