<!-- This document is generated/updated by the sync-doc workflow -->

# Tech Stack and Dependencies

## Major Tech Stack

- **Runtime Environment**: Visual Studio Code (latest) + GitHub Copilot Chat Extension
- **Configuration Language**: Markdown + YAML Frontmatter
- **Templating Engine**: Liquid (used in templates)
- **Diagramming Tool**: Mermaid.js (rendered natively in GitHub/VS Code)

## Major Dependencies

| Component                | Usage                                                                            |
| ------------------------ | -------------------------------------------------------------------------------- |
| **GitHub Copilot**       | The LLM engine driving the agents.                                               |
| **VS Code Copilot Chat** | The interface for user-agent interaction.                                        |
| **Antigravity (Google)** | The advanced agentic coding environment (for development of Terraformer itself). |

## Integration with External Services

- **GitHub Release API**: Used by `/release-new-version` (via simple git commands).
- **Google NotebookLM**: Used for interactive documentation (external link).

## Development Tools

- **Linter**: Markdownlint (recommended for editing `.md` files).
- **Version Control**: Git (Standard GitHub flow).
