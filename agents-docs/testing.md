<!-- This document is generated/updated by the sync-doc workflow -->

# Testing Strategy and Guide

## Test Configuration

Since Terraformer is a "Prompt Engineering" project, "tests" are primarily manual verifications of the generated output (LLM responses).

## Types of Testing

### Verification (Human-in-the-Loop)

- **Scope**: All agent outputs.
- **Method**: User explicitly follows the flow: `@Architect` -> User Approval -> `@Developer`.
- **Criteria**: Does the generated code match the generated plan?

### Prototype Mode Testing

- **Target**: Rapid prototyping sessions.
- **Method**: User adds "(Prototype Mode)" to the request.
- **Expectation**: Lower strictness, faster output. Code may contain `TODO` or simplifications.

### Regression Testing (for Prompts)

- **Target**: Core skills like `/plan` and `/refactor`.
- **Method**: Re-running standard prompts against a known "Golden" codebase (e.g., the `terraformer` repo itself) and checking if the output structure remains consistent.

## Test Data Management

- **Golden Project**: The `terraformer` repository itself serves as the primary test case.
- **Test Projects**: Create varying "legacy" projects (e.g., a messy Python script, a monolithic Java app) to test the `/terraform-context` generation capabilities.

## Testing Best Practices

- **Atomic Prompts**: Test skills with simple, atomic requests first.
- **Context Overload Checks**: Verify that agents don't crash or get confused when `AGENTS.md` is large.
