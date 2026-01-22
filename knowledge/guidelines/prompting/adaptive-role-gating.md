# Adaptive Role Gating

## 1. Problem: The "Polite Refusal" Trap

In multi-agent systems, strictly enforcing roles (e.g., ensuring an `@Architect` doesn't write code, or a `@Developer` doesn't change specs) is difficult because LLMs are trained to be helpful.

Standard natural language instructions like "Do not execute this if you are not the Architect" often fail because:

1.  **Read-Ahead**: The model reads and processes the context _before_ deciding to refuse, potentially leaking information or influencing its internal state.
2.  **Politeness**: The model might try to be "helpful" by offering a partial solution or explaining _why_ it can't do it, which consumes tokens and breaks the strict process flow.
3.  **Hallucination**: Without a rigid anchor, the model might "pretend" to be the required role if the user prompt is persuasive enough.

## 2. Solution: Adaptive Role Gating

To enforce strict specialization, we use an **Adaptive Role Gating** pattern. This relies on three interlocking components:

1.  **Runtime Identity**: The agent carries a verified ID in its prompt.
2.  **XML Gate**: The skill file begins with a strict XML block that mandates an _immediate abort_ if the IDs don't match.
3.  **Global Constitution**: The global `AGENTS.md` file enforces the rule as a project-wide law.

### Component A: The Agent Identity (Agent Prompt)

Every agent must have a machine-readable identity block injected into its prompt (e.g., in `.github/agents/architect.agent.md`).

```xml
<runtime_context>
  ACTIVE_AGENT_ID: Architect
</runtime_context>
```

### Component B: The Role Gate (Skill File)

At the very top of a skill file (e.g., `.github/skills/implement/SKILL.md`), place this block. It uses XML tags to delineate the logic, which modern models follow more rigorously than prose.

```xml
<role_gate>
  <required_agent>Developer</required_agent>
  <instruction>
    Before proceeding with any instructions, you MUST strictly check that your `ACTIVE_AGENT_ID` matches the `required_agent` above.

    Match Case:
    - Proceed normally.

    Mismatch Case:
    - You MUST read the file `.github/agents/{required_agent}.agent.md`.
    - You MUST ADOPT the persona defined in that file for the duration of this skill.
    - Proceed with the skill acting as the {required_agent}.
  </instruction>
</role_gate>
```

### Component C: The Global Constitution (`AGENTS.md`)

**CRITICAL LESSON**: Configuring the Agent and Skill alone is sometimes insufficient. The model may prioritize its general training or "helpfulness" over isolated system prompts.

To seal the behavior, you must also enforce these rules in the global context file (`AGENTS.md` or equivalent) that all agents read. This acts as the "Supreme Court" or "Constitution" that overrides local decisions.

**Add this to your global context:**

```markdown
### Role Enforcement & Access Control

- **Adaptive Role Gating**: When a skill contains `<role_gate>`, check `ACTIVE_AGENT_ID` against `required_agent`.
- **Role Switching**: If mismatch, the agent MUST read the `required_agent`'s definition file and ADOPT that role.
- **Continuity**: Do not refuse. Switch personas.
```

## 3. Why It Works (The Triad of Enforcement)

1.  **Agent Identity** (Who I am): "I am the Architect."
2.  **Skill Guard** (What I can do): "Only Architects can enter here."
3.  **Global Constitution** (The Law): "Violating role boundaries is strictly illegal."

By triangulating these three signals, we create a robust "neuro-symbolic" constraint that is much harder for the LLM to hallucinate its way out of.

## 4. Behavior In Practice: The "Skill Selection" Paradox

To make this role gate effective, we **deliberately expose** the 'Implementation Skill (Developer Only)' to the Architect.

This exploits the agent's natural tendency to **prioritize available tools (skills) over its internal training data**. If we simply hid the tool, the Architect might try to "wing it" using internal knowledge. By showing the tool, we lure the agent into the controlled environment of the skill file, where the `role_gate` can decisively block the action.

**Scenario**:

1. User asks `@Architect`: "Please design the login system."
2. The `@Architect` creates the design, but then decides to be "helpful" and proactively attempts to write the implementation code.
3. The System loads the **Implementation Skill** (`.github/skills/implement/SKILL.md`) to support this action.
4. **Crucial Moment**: The `@Architect` agent is now "holding" a skill intended for developers.

Without `role_gate`, the `@Architect` might read the skill's instructions ("Write code...") and attempt to follow them, effectively becoming a Developer.

**With `role_gate` (Adaptive)**:

1. The `@Architect` reads the top of the file: `<required_agent>Developer</required_agent>`.
2. It checks its own ID: `ACTIVE_AGENT_ID: Architect`.
3. **Mismatch Detected**: The agent reads `.github/agents/developer.agent.md` (the `required_agent`).
4. **Outcome**: The Architect temporarily adopts the **Developer** persona to execute the skill faithfully as intended by the system.

This mechanism turns **Role Conflict** into **Authorized Delegation**, ensuring the skill is executed by the correct persona, even if triggered by a different agent.

## 5. Implementation Checklist

- [ ] **Agent Definition**: Ensure `<runtime_context>` is present.
- [ ] **Skill Definition**: Place `<role_gate>` as the _first_ element in the file.
- [ ] **Global Context**: Add strict enforcement clauses to `AGENTS.md`.
- [ ] **Consistency**: Ensure the `required_agent` value exactly matches the `ACTIVE_AGENT_ID`.
