<!-- This document is generated/updated by the sync-doc workflow -->

# Testing Strategy and Guide

## Test Configuration

Since Terraformer is a configuration engine for AI agents, "testing" primarily involves verifying that the prompts and agent definitions produce the desired behavior in GitHub Copilot.

## Types of Tests

### Prompt Logic Tests (Unit Tests)

- **Goal**: Verify that a specific Skill (e.g., `/plan`) follows its instructions.
- **Method**:
  1.  Open a test file.
  2.  Invoke the skill.
  3.  Verify the output format and content against the prompt's requirements.

### Agent Interaction Tests (Integration Tests)

- **Goal**: Verify that Agents respect their roles and boundaries.
- **Method**:
  1.  Ask `@Developer` to change a requirement.
  2.  **Expected Result**: Refusal and escalation to `@Architect`.
  3.  Ask `@Architect` to plan a feature.
  4.  **Expected Result**: A detailed plan in the correct format.

## Test Execution Method

Currently, testing is manual.

1.  **Setup**: Install the `.github` folder into a clean "Test Project".
2.  **Execution**: Run through the Key Flows defined in `key-flows.md`.
3.  **Validation**: Check if the AI's responses match the "Expected Behavior" defined in the Skill/Agent files.

## Testing Best Practices

- **Clear Context**: Always ensure `AGENTS.md` is up-to-date before testing.
- **Isolation**: Test one skill at a time to isolate issues.
- **Edge Cases**: Test with ambiguous requests to see if the Agent asks for clarification.

## Common Testing Issues

- **Hallucination**: The AI invents facts not in the context.
  - _Solution_: Add explicit constraints to the Prompt or `AGENTS.md`.
- **Ignoring Instructions**: The AI skips a step in the SOP.
  - _Solution_: Use stronger language (e.g., "You MUST...") or break the prompt into smaller steps.
