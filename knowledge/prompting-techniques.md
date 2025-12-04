# Copilot Custom Prompting Techniques

This document summarizes effective techniques for creating custom prompts for GitHub Copilot in VS Code.

## Task Management with `#todos`

### Problem

When a custom prompt requires performing multiple complex operations (e.g., analyzing context, generating multiple files, validating links), Copilot may occasionally skip steps or lose track of progress, leading to incomplete results.

### Solution

Enforce structured execution by explicitly registering tasks using the `#todos` tool at the beginning of the prompt and requiring a final verification step.

### Implementation Steps

1.  **Task Initialization**:
    At the very beginning of the prompt (after the role definition), instruct Copilot to immediately use the `#todos` tool to register all high-level tasks.

2.  **Final Verification**:
    Add a "Final Check" section at the end of the prompt that requires Copilot to confirm all registered todos are completed.

### Example Template

```markdown
# Role: [Role Name]

...

## 📋 Task Initialization

**IMMEDIATELY** use the `#todos` tool to register the following tasks to track your progress:

1.  **Step 1**: [Description of step 1]
2.  **Step 2**: [Description of step 2]
3.  **Validation**: Perform checks.
4.  **Final Check**: Review the "Final Check" section.

... [Rest of the prompt] ...

## ✅ Final Check

**Before finishing, confirm:**

- [ ] All todos are marked as completed.
- [ ] All requirements are met.
```

### Benefits

- **Visibility**: Users can see the planned tasks in the "Todos" view.
- **Completeness**: Reduces the risk of missing steps in complex workflows.
- **Self-Correction**: Encourages the model to review its own work against the checklist.

## Knowledge Retrieval for Latest Specifications

### Problem

Copilot's training data has a cutoff, so it may not know about the latest features, file structures, or tools available in VS Code Copilot (e.g., new prompt file formats, new chat tools).

### Solution

Explicitly instruct Copilot to fetch the latest documentation from official URLs at the beginning of the prompt before performing any generation tasks.

### Implementation Steps

1.  **Identify Critical URLs**:
    Determine which documentation pages contain the specifications relevant to your prompt (e.g., prompt files, custom agents, tools).

2.  **Add Prerequisite Section**:
    Add a section (e.g., "PREREQUISITE: Knowledge Retrieval") that forces Copilot to read these URLs.

### Example Template

```markdown
## 🚨 PREREQUISITE: Knowledge Retrieval

**Before generating or updating, you MUST:**

1.  **Fetch Latest Docs**:
    - `https://code.visualstudio.com/docs/copilot/customization/prompt-files` (for prompt file structure).
    - `https://code.visualstudio.com/docs/copilot/reference/copilot-vscode-features#_chat-tools` (for available tools).
    - `https://code.visualstudio.com/docs/copilot/customization/custom-agents` (for custom agent structure).
```

### Benefits

- **Accuracy**: Ensures generated files comply with the latest schemas and standards.
- **Capability**: Enables the use of the newest tools and features that the model might not inherently know.
