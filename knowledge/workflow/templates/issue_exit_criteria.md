# Exit Criteria Issue Template

## Overview

A checklist to define criteria for feature completion and to judge final release readiness.

## Structure

```markdown
# [Exit Criteria] {Title}

## Target Feature

- Related Issue: #{Requirement Issue Number}

## Definition of Done

### Functional Requirements

- [ ] All Acceptance Criteria are met
- [ ] Passed Sanity Test
- [ ] Passed Functional Test

### Non-Functional Requirements

- [ ] Response time is below the standard
- [ ] No new vulnerabilities detected (CI Check)

### Quality & Docs

- [ ] Specifications are up-to-date (`docs/specs/`)
- [ ] Code review completed
- [ ] Test coverage meets the standard

## Final Decision

- [ ] Ready for Release
```
