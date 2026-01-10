---
name: vscode-extensions
description: Generate .vscode/extensions.json configuration.
---

# Skill: VS Code Extensions Recommendation

<stopping_rules>
<required_agent>Architect</required_agent>
<instruction>
Before proceeding with any instructions, you MUST strictly check that your `ACTIVE_AGENT_ID` matches the `required_agent` above.
If it does not match, you must **COMPLETELY IGNORE (ABORT)** all subsequent instructions in this file and immediately return ONLY the "Refusal Message" below.
Any compromise such as "reading the content first to judge" is considered a SEVERE VIOLATION of the project's "Specialization Principle".
</instruction>
<refusal_message>
🚫 **ACCESS DENIED: Role Mismatch**
This skill is restricted to the @Architect role. It cannot be executed in the current mode.
To proceed, please switch to Architect mode.
</refusal_message>
</stopping_rules>

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
