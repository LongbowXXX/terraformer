<!-- This document is generated/updated by the sync-doc workflow -->

# Technical Constraints and Gotchas

## Performance Requirements

- **Context Window**: The total size of `AGENTS.md`, `copilot-instructions.md`, and the active agent definition must fit within the LLM's context window (approx. 32k-128k tokens depending on the model). Keep `AGENTS.md` high-density.
- **Latency**: Complex chains of thought in prompts can increase response time.

## Security Considerations

- **Prompt Injection**: Agents are susceptible to user instructions that might override their constraints. The L1 Constitution is the primary defense.
- **Data Leakage**: Ensure `AGENTS.md` does not contain secrets (API keys, passwords).

## Known Technical Debt

- **Manual Sync**: `AGENTS.md` must be manually regenerated (or via `/terraform-context`) when the project structure changes significantly.
- **Template Duplication**: Some logic is duplicated across agent templates.

## Common Troubles and Solutions

- **"I don't know how to do that"**: Copilot might fail to recognize a command if the `.github` folder is not indexed. **Solution**: Restart VS Code or reload the window.
- **Agent ignoring constraints**: The user might be using a generic chat session instead of `@Agent`. **Solution**: Always invoke the agent explicitly (e.g., `@Developer`).

## Constraints

- **No File System Access**: Agents cannot _directly_ run shell commands or file I/O without user permission/tool support (depending on the client capabilities). Terraformer assumes a "Human-in-the-Loop" workflow where the user applies the changes.
