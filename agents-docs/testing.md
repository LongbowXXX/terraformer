<!-- This document is generated/updated by the sync-doc workflow -->

# Testing Strategy and Guide

## Test Configuration

Since Terraformer is a set of prompts and templates, "Testing" involves verifying that these prompts generate high-quality, correct outputs when executed by GitHub Copilot.

## Types of Tests

### Manual Verification (The "Test Project" Approach)

The primary method of testing is to apply Terraformer to a "Test Project" (a dummy legacy codebase).

1.  **Setup**: Create a dummy project (e.g., a simple To-Do app in Python or React).
2.  **Install**: Copy the `.github` folder from Terraformer to the dummy project.
3.  **Execute**: Run `/terraform-context` and `/terraformer`.
4.  **Verify**: Check if the generated `AGENTS.md`, agents, and skills are correct and relevant to the dummy project.

### Regression Testing

When modifying a prompt (e.g., `terraformer.prompt.md`):

- Run the modified prompt against a known codebase.
- Compare the output with previous outputs.
- Ensure no "hallucinations" or syntax errors in the generated files.

## Coverage Goals

- **Core Flows**: Ensure `/terraform-context` and `/terraformer` work 100% of the time.
- **Template Validity**: Ensure all templates in `.github/templates/` are valid Markdown and have correct placeholders.

## Testing Best Practices

- **Clean State**: Always test in a fresh VS Code window or a clean repo to avoid context pollution.
- **Model Variance**: Be aware that LLM outputs can vary. Run tests multiple times if results are inconsistent.
