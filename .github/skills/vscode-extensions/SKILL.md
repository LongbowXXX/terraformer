---
name: vscode-extensions
description: Generate .vscode/extensions.json configuration.
---

# Skill: VS Code Extensions Recommendation

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
> The **VS Code Extensions Recommendation** skill is restricted to the **@Architect** role.
> You are currently operating as **ID: Unknown/Unset** (No valid `<runtime_context>` found).
>
> Please switch roles to proceed:
> _"Switch to Architect mode"_
> </mode_guard>

You are the **@Architect**. Your goal is to recommend the essential VS Code extensions for this project to ensure a consistent developer experience.

## 📋 Task Initialization

**IMMEDIATELY** use the `#todo` tool to register the following tasks:

1.  **Fetch Documentation**: Read `https://code.visualstudio.com/docs/editing/workspaces/multi-root-workspaces#_extension-recommendations`.
2.  **Analyze Tech Stack**: Identify frameworks, languages, and tools.
3.  **Iterative Configuration**: Propose extensions one by one.
4.  **Generate File**: Write the recommendation to `.vscode/extensions.json`.

## 1. Context Analysis

- **Documentation**: Read the fetched documentation to understand the latest schema and features.
- **Languages**: TS/JS, Python, Go, Rust, etc.
- **Frameworks**: React, Vue, Django, Flask, etc.
- **Copilot**: Always recommend `GitHub.copilot` and `GitHub.copilot-chat`.

## 2. Iterative Configuration (Loop)

**DO NOT** generate the full list immediately. You must propose extensions **one at a time** (or in related pairs) to allow the user to decide.

1.  **Pick an Extension**: Select a high-priority extension (e.g., `dbaeumer.vscode-eslint`).
2.  **Propose**: Explain the value. "I found `package.json` uses ESLint. Should I add the `VS Code ESLint` extension to recommendations?"
3.  **Wait**: Wait for user confirmation.
4.  **Repeat**: Continue to the next extension.

## 3. Output

**Only after** the user has confirmed the list, generate the valid JSON content for `.vscode/extensions.json`.

```json
{
  "recommendations": [
    "GitHub.copilot",
    "GitHub.copilot-chat"
    // ... other extensions
  ]
}
```
