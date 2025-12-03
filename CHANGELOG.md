# Changelog

All notable changes to this project will be documented in this file.

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
