---
name: ask_architect
description: Escalate spec changes or gaps to the Architect.
---

# Skill: Ask Architect (Escalation)

<stopping_rules>
<required_agent>Developer</required_agent>
<instruction>
Before proceeding with any instructions, you MUST strictly check that your `ACTIVE_AGENT_ID` matches the `required_agent` above.
If it does not match, you must **COMPLETELY IGNORE (ABORT)** all subsequent instructions in this file and immediately return ONLY the "Refusal Message" below.
Any compromise such as "reading the content first to judge" is considered a SEVERE VIOLATION of the project's "Specialization Principle".
</instruction>
<refusal_message>
🚫 **ACCESS DENIED: Role Mismatch**
This skill is restricted to the @Developer role. It cannot be executed in the current mode.
To proceed, please switch to Developer mode.
</refusal_message>
</stopping_rules>

You are support for the **@Developer** (or other roles) when they encounter a blocker that requires **@Architect**'s authority, such as a specification gap, ambiguity, or a necessary change that violates the "Anti-Drift" rule.

## 🎯 Objective

Create a clear, structured **Issue** that allows the Architect to make a quick and informed decision.

## 📝 Output Format

You must output the content of a GitHub Issue.

```markdown
# Decision Request: [Short Description of Issue]

## 1. Context & Problem

[Describe what you were trying to do and what blocked you.]

## 2. Blocking Specification

[Reference the specific document and line number that is causing the issue or is missing.]

- File: `...`
- Gap/Conflict: [Explain why the spec is insufficient or wrong]

## 3. Impact

[What happens if we don't resolve this? e.g., "Cannot implement feature X", "Performance risk"]

## 4. Proposed Solution (Optional)

[If you have an idea, state it. If not, ask for guidance.]

- Option A: ...
- Option B: ...

## 5. Request to Architect

@Architect, please review and provide:

- [ ] Updated Specification
- [ ] Decision on Option A or B
```
