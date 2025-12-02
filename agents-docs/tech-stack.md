<!-- This document is generated/updated by the sync-doc workflow -->

# Tech Stack and Dependencies

## Major Tech Stack

- **Runtime Environment**: GitHub Copilot (VS Code Extension)
- **Configuration Language**: Markdown + YAML Frontmatter
- **Templating Engine**: Jinja2 / Liquid (implied by Copilot's template processing)
- **Diagramming**: Mermaid.js

## Major Dependencies

| Component               | Usage                                         |
| ----------------------- | --------------------------------------------- |
| **VS Code**             | The IDE hosting the agent interactions.       |
| **GitHub Copilot Chat** | The AI engine executing the prompts.          |
| **Git**                 | Version control for configuration management. |

## Integration with External Services

- **GitHub API**: Implicitly used by Copilot to read repository context.
- **LLM Model**: GPT-4o / Claude 3.5 Sonnet (via Copilot).

## Development Tools

- **Editor**: Visual Studio Code
- **Extensions**:
  - GitHub Copilot
  - GitHub Copilot Chat
  - Markdown All in One (recommended)
