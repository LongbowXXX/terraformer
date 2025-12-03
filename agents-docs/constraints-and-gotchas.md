<!-- This document is generated/updated by the sync-doc workflow -->

# Technical Constraints and Gotchas

## Performance Requirements

- **Latency**: Prompt execution depends on the Copilot API latency. Complex prompts like `/terraformer` may take 30-60 seconds to complete.
- **Context Window**: Be mindful of the LLM's context window. Very large `AGENTS.md` files might be truncated.

## Security Considerations

- **Prompt Injection**: Since prompts are text, they could theoretically be manipulated. However, they run locally in the user's IDE, mitigating remote risks.
- **Secrets**: Agents should NOT be given access to real secrets (API keys, passwords) in the prompts or `AGENTS.md`.

## Known Technical Debt

- **Template Duplication**: Some instructions might be repeated across multiple agent templates.
- **Manual Sync**: Keeping `agents-docs/` in sync with the actual prompts requires manual effort (or running `/sync-doc`).

## Common Troubles and Solutions

- **"I don't know how to do that"**: If Copilot refuses a command, ensure the `.github/prompts` folder is correctly placed and VS Code has indexed it.
- **Partial Generation**: If output stops mid-way, type "continue" to ask Copilot to finish.

## Constraints

- **No Runtime**: Terraformer cannot "execute" code itself; it only generates it.
- **Human-in-the-Loop**: All AI-generated code MUST be reviewed by a human (`@QualityGuard` role).
