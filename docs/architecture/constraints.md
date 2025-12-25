<!-- This document is generated/updated by the sync-doc workflow -->

# Technical Constraints and Gotchas

## Performance Requirements

- **Token Usage**: Agents must be concise. `AGENTS.md` and skills are injected into the context window, so they must be kept as compact as possible to leave room for the actual codebase.
- **Latency**: Agent responses (especially with GPT-5 class models) can take time. Users should be patient.

## Security Considerations

- **Secrets**: Do NOT put secrets (API keys, passwords) in `AGENTS.md` or any prompt file. These are sent to the LLM.
- **Code Execution**: The `@Developer` agent writes code, but it is the _user's_ responsibility to review and execute it. Agents should not be given autonomous access to dangerous terminals.

## Known Technical Debt

- **Context "Compression"**: As a project grows, `AGENTS.md` might become too large. We need to implement a mechanism to split or summarize context (e.g., retrieval-augmented generation or RAG) in future ANTP versions.
- **Model Dependency**: Some complex prompts (like `/plan`) are optimized for GPT-5 and might perform poorly on weaker models.

## Common Troubles and Solutions

- **"I don't know about file X"**: The agent might not have the file in its context. Open the file in the editor or reference it explicitly (`#file:path/to/file`) in the chat.
- **Hallucinations**: If an agent invents a library function, check the `tech-stack.md` and ensure the library version is compatible.

## Constraints

- **Anti-Generalist Principle**: `@Developer` will REFUSE to make changes that contradict the `implementation_plan.md`. This is a feature, not a bug. If you need to change the spec, ask `@Architect`.
