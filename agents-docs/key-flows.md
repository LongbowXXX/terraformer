<!-- This document is generated/updated by the sync-doc workflow -->

# Key Feature Flows

## Entry Point: Installation

The user installs Terraformer by copying the `.github` directory into their project root.

## Flow 1: Context Generation (`/terraform-context`)

### Overview

Analyzes the legacy codebase to generate the "Constitution" (`AGENTS.md`).

### Processing Flow

1.  User invokes `/terraform-context` in Copilot Chat.
2.  Copilot executes `.github/prompts/terraform-context.prompt.md`.
3.  **Analysis**: Scans root files, `package.json`, `README.md`, etc.
4.  **Generation**: Produces a high-density summary of the project.
5.  **Output**: User saves the output as `AGENTS.md`.

## Flow 2: Team Generation (`/terraformer`)

### Overview

Generates the specialized Agents and Skills based on the project context.

### Processing Flow

1.  User invokes `/terraformer` in Copilot Chat.
2.  Copilot executes `.github/prompts/terraformer.prompt.md`.
3.  **Context Loading**: Reads `AGENTS.md` to understand the tech stack and rules.
4.  **Template Selection**: Reads templates from `.github/templates/`.
5.  **Customization**: Injects project-specific variables into templates.
6.  **Output**: Generates/Updates:
    - `.github/agents/*.agent.md`
    - `.github/prompts/*.prompt.md`

## Flow 3: Custom Skill Creation (`/create-custom-prompt`)

### Overview

Allows users to extend the system with their own workflows.

### Processing Flow

1.  User invokes `/create-custom-prompt`.
2.  Copilot asks for the Skill Name and Purpose.
3.  Copilot generates a new `.prompt.md` file in `.github/prompts/` based on the standard skill template.
4.  User can now invoke this skill via `/skill-name`.

## Flow 4: Documentation Sync (`/sync-doc`)

### Overview

Ensures `agents-docs/` remains up-to-date with the codebase.

### Processing Flow

1.  User invokes `/sync-doc`.
2.  Copilot analyzes the project structure and existing docs.
3.  Copilot generates or updates the standard documentation suite (`architecture.md`, `key-flows.md`, etc.).
4.  User reviews and saves the changes.
