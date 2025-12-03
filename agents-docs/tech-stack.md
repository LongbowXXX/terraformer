<!-- This document is generated/updated by the sync-doc workflow -->

# Tech Stack and Dependencies

## Major Tech Stack

- **Runtime**: GitHub Copilot (VS Code Extension)
- **Configuration Language**: Markdown + YAML Frontmatter
- **Diagramming**: Mermaid.js

## Major Dependencies

Since Terraformer is a configuration engine, it does not have runtime library dependencies (like npm or pip packages). Its "dependencies" are the environment it runs in.

| Component          | Requirement   | Usage              |
| :----------------- | :------------ | :----------------- |
| **VS Code**        | Latest Stable | The IDE platform   |
| **GitHub Copilot** | Subscription  | The AI engine      |
| **Copilot Chat**   | Extension     | The chat interface |

## Integration with External Services

- **GitHub API**: Used implicitly by Copilot to fetch context and codebase information.

## Development Tools

- **Version Control**: Git
- **Editor**: VS Code
