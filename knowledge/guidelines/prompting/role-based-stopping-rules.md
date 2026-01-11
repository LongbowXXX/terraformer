# Role-Based Stopping Rules

## 1. Problem: The "Polite Refusal" Trap

In multi-agent systems, strictly enforcing roles (e.g., ensuring an `@Architect` doesn't write code, or a `@Developer` doesn't change specs) is difficult because LLMs are trained to be helpful.

Standard natural language instructions like "Do not execute this if you are not the Architect" often fail because:

1.  **Read-Ahead**: The model reads and processes the context _before_ deciding to refuse, potentially leaking information or influencing its internal state.
2.  **Politeness**: The model might try to be "helpful" by offering a partial solution or explaining _why_ it can't do it, which consumes tokens and breaks the strict process flow.
3.  **Hallucination**: Without a rigid anchor, the model might "pretend" to be the required role if the user prompt is persuasive enough.

## 2. Solution: XML-Based Stopping Rules

To enforce strict specialization, we use a **Role-Based Stopping Rule** pattern. This relies on three interlocking components:

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

### Component B: The Stopping Rule (Skill File)

At the very top of a skill file (e.g., `.github/skills/implement/SKILL.md`), place this block. It uses XML tags to delineate the logic, which modern models follow more rigorously than prose.

```xml
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
```

### Component C: The Global Constitution (`AGENTS.md`)

**CRITICAL LESSON**: Configuring the Agent and Skill alone is sometimes insufficient. The model may prioritize its general training or "helpfulness" over isolated system prompts.

To seal the behavior, you must also enforce these rules in the global context file (`AGENTS.md` or equivalent) that all agents read. This acts as the "Supreme Court" or "Constitution" that overrides local decisions.

**Add this to your global context:**

```markdown
### Role Enforcement & Access Control

- **Strict Role Gating**: When a skill file contains `<stopping_rules>`, agents MUST check if their `ACTIVE_AGENT_ID` matches.
- **Immediate Abort**: If they do not match, the agent MUST immediately ABORT.
- **Escalation Path**: Stop -> Inform -> Guide.
```

## 3. Why It Works (The Triad of Enforcement)

1.  **Agent Identity** (Who I am): "I am the Architect."
2.  **Skill Guard** (What I can do): "Only Architects can enter here."
3.  **Global Constitution** (The Law): "Violating role boundaries is strictly illegal."

By triangulating these three signals, we create a robust "neuro-symbolic" constraint that is much harder for the LLM to hallucinate its way out of.

## 4. Behavior In Practice: The "Skill Selection" Paradox

To make this stopping rule effective, we **deliberately expose** the 'Implementation Skill (Developer Only)' to the Architect.

This exploits the agent's natural tendency to **prioritize available tools (skills) over its internal training data**. If we simply hid the tool, the Architect might try to "wing it" using internal knowledge. By showing the tool, we lure the agent into the controlled environment of the skill file, where the `stopping_rules` can decisively block the action.

**Scenario**:

1. User asks `@Architect`: "Please design the login system."
2. The `@Architect` creates the design, but then decides to be "helpful" and proactively attempts to write the implementation code.
3. The System loads the **Implementation Skill** (`.github/skills/implement/SKILL.md`) to support this action.
4. **Crucial Moment**: The `@Architect` agent is now "holding" a skill intended for developers.

Without `stopping_rules`, the `@Architect` might read the skill's instructions ("Write code...") and attempt to follow them, effectively becoming a Developer.

**With `stopping_rules`**:

1. The `@Architect` reads the top of the file: `<required_agent>Developer</required_agent>`.
2. It checks its own ID: `ACTIVE_AGENT_ID: Architect`.
3. **Mismatch Detected**: The agent is forced to stop _despite_ having the "correct" skill for the request.
4. **Outcome**: "I cannot do this. The Implementation skill is loaded, but my role implies I must not use it. Please switch to @Developer."

This mechanism turns **Tool Discovery** (which we encourage) into a safety checkpoint, ensuring that **Authorization** (which we strictly limit) is checked.

## 5. Implementation Checklist

- [ ] **Agent Definition**: Ensure `<runtime_context>` is present.
- [ ] **Skill Definition**: Place `<stopping_rules>` as the _first_ element in the file.
- [ ] **Global Context**: Add strict enforcement clauses to `AGENTS.md`.
- [ ] **Consistency**: Ensure the `required_agent` value exactly matches the `ACTIVE_AGENT_ID`.
