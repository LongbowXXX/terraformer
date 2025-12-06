# Changelog

All notable changes to this project will be documented in this file.

## [0.0.8] - 2025-12-06

### Added

- **Knowledge**: Added AI Literacy section and human AI-readiness documentation.
- **Prompts**: Added prompt for generating `AGENTS.md` context file.
- **Documentation**: Added `knowledge/` directory description to `README.md`.
- **Agents**: Introduced core AI agent roles and skill prompt templates.
- **Workflows**: Added workflow for creating new custom prompt skills.

## [0.0.7] - 2025-12-05

### Added

- **Prompts**: Added `terraformer` agent prompt for ANTP v1.4.
- **Agents**: Added agent templates for Architect, Business Analyst, and Quality Guard roles.

## [0.0.6] - 2025-12-05

### Added

- **Agents**: Added QualityGuard agent template and comprehensive software review perspectives knowledge.
- **Workflows**: Added `release-new-version` workflow.
- **Context**: Added `terraform-context` prompt for generating project context.

### Documentation

- **Guidelines**: Added guidelines for PR creation and software review perspectives in `AGENTS.md`.
- **Copilot**: Added custom prompting techniques for GitHub Copilot.

## [0.0.5] - 2025-12-04

### Added

- **Knowledge**: Added `knowledge/prompting-techniques.md`.
- **Skills**: Added new skill templates for documentation consistency, custom prompt creation, documentation synchronization, and auditing.

### Changed

- **Prompts**: Updated `terraformer` and `terraform-context` prompts.

## [0.0.4] - 2025-12-03

### Added

- **Documentation**: Added humorous comment to `README.md`.
- **Workflows**: Added markdown link check to `doc-sync` workflow.

### Changed

- **Prompts**: Updated `doc-sync` prompt principles to emphasize DRY and file links.
- **Documentation**: Regenerated agent documentation with new principles.

## [0.0.3] - 2025-12-03

### Added

- **Skills**: Added `create-custom-prompt` meta-skill for easier extension.
- **Documentation**: Added Copilot Chat installation instructions to `README.md`.

### Changed

- **Prompts**: Updated `terraform-context` to link new documentation files.
- **Prompts**: Refined `terraformer` prompt to list only representative agents/skills.
- **Agents**: Corrected `@Developer` agent name capitalization.
- **Documentation**: Removed obsolete `{{TECH_STACK}}` references.

## [0.0.2] - 2025-12-02

### Added

- **Agents**: Added `@Debugger` agent.
- **Skills**: Added `/implementation` and `/check-doc-consistency` skills.
- **Documentation**: Added `glossary.md` generation to `/doc-sync`.

### Changed

- **Prompts**: Updated `terraformer.prompt.md` to support updating existing agents/skills and fixed flow order.
- **Documentation**: Removed specific agent/skill counts to reduce maintenance burden.
- **Documentation**: Updated `AGENTS.md` with reference URLs.

## [0.0.1] - 2025-12-01

### Added

- **Documentation**: Comprehensive documentation for Terraformer's key functional flows, use cases, and project charter.
- **Prompts**: `terraformer.prompt.md` for generating agents and skills.
- **Architecture**: ANTP v1.4 Roles & Skills architecture.
- **Mascot**: Added `mascot.png`.

### Changed

- **Diagrams**: Refactored Mermaid diagram syntax for consistency.
