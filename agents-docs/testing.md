<!-- This document is generated/updated by the sync-doc workflow -->

# Testing Strategy and Guide

## Test Configuration

Since Terraformer is a configuration engine, "testing" primarily involves verifying that the generated prompts and agents behave as expected when invoked in a target environment.

## Types of Tests

### Prompt Verification (Unit Tests)

- **Goal**: Ensure individual skills (e.g., `/plan`) produce consistent, high-quality outputs.
- **Method**: Run the prompt against a known set of inputs (e.g., "Plan a login feature") and evaluate the response against a rubric.

### Agent Interaction (Integration Tests)

- **Goal**: Verify that agents correctly hand off tasks and respect constraints.
- **Method**: Simulate a full workflow (e.g., User -> Architect -> Developer) and check if the `@Developer` refuses to change specs.

### End-to-End (E2E) Tests

- **Goal**: Verify the entire "Terraforming" process.
- **Method**:
  1.  Create a blank "legacy" project.
  2.  Run `/terraformer`.
  3.  Verify that `.github/` is populated correctly.
  4.  Verify that `AGENTS.md` is generated.

## Test Execution Method

Currently, testing is primarily **manual**.

1.  Open a test workspace.
2.  Copy the `.github` folder from the source.
3.  Open Copilot Chat.
4.  Execute the command/skill.
5.  Review the output.

## Coverage Goals

- **Critical Skills**: `/plan`, `/implement`, `/refactor` must be verified for every major release.
- **Safety Constraints**: The "Anti-Generalist" constraints must be tested to ensure they are active.

## Testing Best Practices

- **Use Clean Context**: Always test in a fresh session or window to avoid context contamination.
- **Record Outputs**: Save the chat logs of successful tests as "Golden Records" for regression testing.
