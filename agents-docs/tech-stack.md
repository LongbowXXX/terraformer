<!-- This document is generated/updated by the sync-doc workflow -->

# Tech Stack and Dependencies

## Major Tech Stack

Terraformer is a "Meta-Application" that runs inside an IDE.

- **Runtime Environment**: Visual Studio Code
- **AI Engine**: GitHub Copilot Chat
- **Configuration Language**: Markdown (GFM) + YAML Frontmatter
- **Protocol**: ANTP v1.4 (AI-Native Transformation Protocol)

## Major Dependencies

| Component               | Requirement   | Usage                                    |
| ----------------------- | ------------- | ---------------------------------------- |
| **VS Code**             | Latest Stable | The host IDE.                            |
| **GitHub Copilot**      | Extension     | The AI engine that executes the prompts. |
| **GitHub Copilot Chat** | Extension     | The interface for invoking commands.     |

## Integration with External Services

- **GitHub API**: Used by Copilot to fetch context and code.
- **LLM (e.g., GPT-4)**: The underlying model used by Copilot.

## Development Tools

- **Git**: Version control.
- **Mermaid**: For diagramming within Markdown.
