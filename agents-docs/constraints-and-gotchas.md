<!-- This document is generated/updated by the sync-doc workflow -->

# Technical Constraints and Gotchas

## Performance Requirements

- **Latency**: Copilot responses depend on the LLM's load. Complex prompts (like `/plan`) may take longer to generate.
- **Context Window**: There is a limit to how much context Copilot can read. Keep `AGENTS.md` and `agents-docs/` concise and high-density.

## Security Considerations

- **No Secrets**: Never put API keys, passwords, or sensitive data in `AGENTS.md` or Prompts. These are sent to the LLM.
- **Code Safety**: AI-generated code must always be reviewed. `@QualityGuard` is a safeguard, not a guarantee.

## Known Technical Debt

- **Prompt Fragility**: LLMs are non-deterministic. A prompt that works today might behave slightly differently tomorrow.
- **Context Drift**: If `AGENTS.md` is not updated, the AI will make decisions based on outdated info.

## Common Troubles and Solutions

- **"I don't know about X"**: The AI claims ignorance.
  - _Solution_: Check if "X" is documented in `AGENTS.md` or `agents-docs/`. If not, add it.
- **Agent breaks character**: `@Developer` starts designing architecture.
  - _Solution_: Remind the agent of its role or re-run `/terraform-context` to refresh `AGENTS.md`.

## Constraints

- **Text-Only**: Copilot Chat is primarily text-based. It cannot "see" images or run binary executables.
- **No File System Access**: Agents cannot _directly_ create files without user confirmation (they propose changes).
