<!-- This document is generated/updated by the sync-doc workflow -->

# Tech Stack and Dependencies

## Primary Tech Stack

| Category                 | Technology         | Notes                                    |
| ------------------------ | ------------------ | ---------------------------------------- |
| **Platform**             | Visual Studio Code | GitHub Copilot extension required        |
| **Language**             | Markdown           | Prompts, templates, documentation        |
| **Configuration Format** | YAML               | Agent/skill frontmatter                  |
| **Diagram Notation**     | Mermaid            | Architecture diagrams, sequence diagrams |

## Project Characteristics

Terraformer is not a traditional "codebase" but a **collection of configuration files and templates**:

- **Executable Code**: None (no Python scripts, no TypeScript)
- **Runtime**: GitHub Copilot Chat (within VS Code)
- **Processing Engine**: LLM (Copilot's backend)

## Main Dependencies

### Required Dependencies (Runtime Dependencies)

| Dependency              | Type              | Purpose                            |
| ----------------------- | ----------------- | ---------------------------------- |
| **GitHub Copilot Chat** | VS Code Extension | Prompt execution, agent invocation |
| **VS Code**             | IDE               | Development environment            |

### Recommended Dependencies (Development Dependencies)

| Dependency                           | Type              | Purpose                                      |
| ------------------------------------ | ----------------- | -------------------------------------------- |
| **Markdown Preview Mermaid Support** | VS Code Extension | Mermaid diagram preview                      |
| **GitHub Pull Requests**             | VS Code Extension | PR management (for future CI/CD integration) |

### Recommended Extensions (from `.vscode/extensions.json`)

```json
{
  "recommendations": [
    "github.copilot-chat",
    "bierner.markdown-mermaid",
    "github.vscode-pull-request-github"
  ]
}
```

## External Service Integrations

### GitHub Copilot

- **Role**: Prompt execution, text generation, agent interaction
- **Integration Method**: Via VS Code extension
- **Authentication**: GitHub account (Copilot license required)

### VS Code Custom Agents API

- **Role**: Agent invocation in `@Agent` format
- **Reference Documentation**: https://code.visualstudio.com/docs/copilot/customization/custom-agents
- **Features Used**:
  - `.agent.md` file recognition
  - YAML frontmatter `handoffs:` property
  - `@Agent` mentions

### VS Code Prompt Files API

- **Role**: Skill invocation in `/command` format
- **Features Used**:
  - `.prompt.md` file recognition
  - `/command` triggers

## Development Tools

### Build Tools

**Not Applicable** - Terraformer does not require a build process.

All files are used as-is:

- Markdown files → Interpreted directly by Copilot Chat
- YAML frontmatter → Parsed directly by VS Code API

### Test Framework

**No Traditional Automated Tests** - Verification is done manually.

Verification Steps:

1. Create test project
2. Copy `.github/`
3. Execute `/terraformer`
4. Visually verify generated results

### Linters/Formatters

| Tool                  | Target           | Configuration    |
| --------------------- | ---------------- | ---------------- |
| VS Code Markdown Lint | Markdown files   | Default settings |
| VS Code YAML          | YAML frontmatter | Default settings |

### CI/CD

**Current Status**: None (Prototype Phase)

**Future Plans**:

- Auto-trigger `@QualityGuard` in GitHub Actions
- Automatic verification of generated results

## Version Management

### Project Version

- **ANTP Protocol**: v1.4
- **Status**: Prototype Phase

### Compatibility

| Component           | Minimum Version | Recommended Version |
| ------------------- | --------------- | ------------------- |
| VS Code             | 1.85+           | Latest stable       |
| GitHub Copilot Chat | 0.12+           | Latest              |

## Licensing

- **Project License**: MIT License
- **Dependency Licenses**: Not applicable (no external package dependencies)

## Tech Stack Selection Rationale

### Why Markdown Only?

| Option             | Rejection Reason                                   |
| ------------------ | -------------------------------------------------- |
| Python scripts     | Requires installation steps, dependency management |
| Node.js tools      | Same as above                                      |
| VS Code extension  | High development and distribution cost             |
| **Markdown files** | ✅ Achieves Zero Friction Adoption                 |

### Why YAML Frontmatter?

- GitHub Copilot Custom Agents adopts YAML as standard
- Readable by both humans and machines
- Compatible with existing Markdown ecosystem

### Why Mermaid?

- Embeddable in Markdown
- Renders directly in VS Code + Copilot
- No external tools required
