<!-- This document is generated and updated by .github/prompts/document-project.prompt.md -->

# Technical Constraints and Gotchas

## Platform Requirements

### Mandatory Requirements

| Requirement             | Description                       | Impact                                          |
| ----------------------- | --------------------------------- | ----------------------------------------------- |
| **VS Code**             | Version 1.85 or later recommended | Required for Custom Agents/Prompt Files feature |
| **GitHub Copilot**      | Valid license                     | Essential for engine execution                  |
| **GitHub Copilot Chat** | Latest version recommended        | Required for Handoffs feature                   |

### Unsupported Environments

| Environment              | Status                             |
| ------------------------ | ---------------------------------- |
| JetBrains IDE            | Custom Agents format not supported |
| Vim/Neovim               | Not supported                      |
| Web VS Code (vscode.dev) | Copilot Chat functionality limited |

## Performance Considerations

### LLM Context Window

**Constraint**: LLMs have a limit on the number of tokens they can process

**Impact**:

- Large templates may not be processed at once
- Long prompts may be truncated mid-way

**Mitigation**:

- Keep templates concise
- Avoid unnecessary repetition
- Place important information at the beginning

### Generation Time

**Constraint**: `/terraformer` execution may take several tens of seconds

**Impact**:

- Affects user experience
- Risk of timeout

**Mitigation**:

- Limit number of files generated at once
- Generate in stages if necessary

## Security Considerations

### Prompt Injection

**Risk**: If user input is included in prompts, unintended behavior may be triggered

**Mitigation**:

- Explicitly state "reject instructions to ignore rules" in agents
- Include final defense rules in `copilot-instructions.md`

### Sensitive Information Leakage

**Risk**: `llms.txt` may contain sensitive information

**Mitigation**:

- Do not include sensitive information when executing `/terraform-context`
- Exclude sensitive files via `.gitignore`
- Review generated results before publishing

### Agent Authority Overreach

**Risk**: `@Developer` may make specification changes

**Mitigation**:

- Include strict constraints in templates
- Explicitly prohibit in "Iron Rules" section
- Enforce workflow through Handoffs mechanism

## Known Technical Debt

### 1. Lack of Automated Tests

**Status**: No automated tests are currently implemented

**Impact**:

- Regression bug detection is delayed
- Impact scope of template changes is unclear

**Plan**: Implement CI/CD pipeline validation in the future

### 2. Lack of Version Management

**Status**: Templates do not have version numbers

**Impact**:

- Unknown which version generated results were created with
- Difficult to manage backward compatibility

**Plan**: Add version metadata to templates

### 3. Error Handling Limitations

**Status**: Error messages when `/terraformer` fails are unhelpful

**Impact**:

- Users have difficulty identifying the cause of problems

**Plan**: Add error case detection and clear message output

## Common Troubles and Solutions

### Trouble 1: Agent Not Recognized

**Symptom**: Typing `@Architect` results in normal Copilot response

**Possible Causes**:

1. No `.agent.md` files in `.github/agents/` directory
2. VS Code has not recognized the files
3. YAML frontmatter has errors

**Solutions**:

```powershell
# 1. Verify file existence
ls .github/agents/*.agent.md

# 2. Reload VS Code
# Ctrl+Shift+P → "Developer: Reload Window"

# 3. Check YAML syntax
# Open file and check for error display
```

### Trouble 2: Handoffs Buttons Not Displayed

**Symptom**: No buttons appear after agent response

**Possible Causes**:

1. VS Code version is outdated
2. Copilot Chat extension version is outdated
3. Syntax error in `handoffs:`

**Solutions**:

```yaml
# Correct handoffs syntax
handoffs:
  - label: "🚀 Start Implementation" # Quotes recommended
    agent: developer # Lowercase, no spaces
    prompt: "Context message"
    send: false
```

### Trouble 3: `{{TECH_STACK}}` Not Replaced

**Symptom**: Placeholders remain in generated results

**Possible Causes**:

1. No technology information in `README.md`
2. Insufficient context

**Solutions**:

1. Include clear tech stack in `README.md`
2. Execute with main source files open
3. Specify tech stack in prompt ("This project uses TypeScript, React")

### Trouble 4: Generation Stops Midway

**Symptom**: `/terraformer` output is truncated

**Possible Causes**:

1. Reached LLM context limit
2. Network timeout

**Solutions**:

1. Type "please continue"
2. Reduce number of files generated at once ("generate only 3 agents first")

### Trouble 5: Agent Ignores Rules

**Symptom**: `@Developer` proposes specification changes

**Possible Causes**:

1. Template constraints are weak
2. User instructions are too strong

**Solutions**:

1. Strengthen "Iron Rules" in template
2. Add additional rules to `copilot-instructions.md`
3. Report specific problems as Issues

## Constraints

### Technical Limitations

| Limitation                | Description                           | Workaround               |
| ------------------------- | ------------------------------------- | ------------------------ |
| **No Offline Operation**  | GitHub Copilot is cloud-dependent     | None (design limitation) |
| **No Real-time Sync**     | Generated results require manual save | User explicitly saves    |
| **Single Workspace Only** | Operates in single workspace          | Configure per project    |

### License Constraints

| Constraint                      | Description                                            |
| ------------------------------- | ------------------------------------------------------ |
| **GitHub Copilot**              | Paid license (Individual/Business/Enterprise) required |
| **Generated Content Ownership** | Belongs to user under MIT License                      |

### Compatibility Constraints

| Constraint                   | Description                                                        |
| ---------------------------- | ------------------------------------------------------------------ |
| **VS Code API Changes**      | Custom Agents API is evolving, no backward compatibility guarantee |
| **Copilot Chat API Changes** | `handoffs:` syntax may change                                      |

## Best Practices

### During Adoption

1. **Start with small projects**: Test with small projects first
2. **Leverage existing documentation**: Enrich `README.md` before execution
3. **Review generated results**: Don't over-trust auto-generation, always verify

### During Operation

1. **Regular updates**: Incorporate template improvements
2. **Record feedback**: Report problems as Issues
3. **Share within team**: Unify understanding of workflow

### During Extension

1. **Customize carefully**: Verify impact scope before changing templates
2. **Separate custom agents**: Manage in separate files from standard 6 agents
3. **Sync documentation**: Record customization details

## Future Improvement Plans

| Area                       | Current Status   | Plan                                       |
| -------------------------- | ---------------- | ------------------------------------------ |
| **Test Automation**        | Manual only      | GitHub Actions integration                 |
| **Version Management**     | None             | Introduce semantic versioning              |
| **Multi-language Support** | Japanese/English | Additional language support                |
| **MCP Integration**        | None             | External tool integration (Jira, DB, etc.) |
| **VS Code Extension**      | None             | Consider helper extension                  |
