# **Development Context & Architecture Decision Record (ADR)**

**Note to Copilot:** This document serves as the **Single Source of Truth** for the "Terraformer" project. It defines not just the *what* and *how*, but the critical *why* behind our architectural choices. Always refer to this deep context when generating code, documentation, or strategic advice for this repository.

## **1\. Project Identity and Vision**

* **Name:** Terraformer  
* **Core Concept:** AI-Native Transformation Protocol (ANTP)  
* **Vision:** To democratize "AI-Native" development by making it accessible to legacy codebases. We view legacy code not as trash to be discarded, but as a "hostile planet" that needs terraforming to support AI life.  
* **Objective:** To develop a powerful meta-engine that acts as a bridge between human-centric development and AI-centric assistance. This engine analyzes legacy ("human-only") software projects—characterized by implicit context and tribal knowledge—and automatically generates the necessary configuration files, role definitions, and documentation structures to transform them into "AI-Native" environments where humans and AI agents can collaborate seamlessly.

## **2\. The Core Problem: The "Context Debt" Crisis**

Traditional software projects are often built on years of accumulated "tribal knowledge"—unwritten rules, architectural decisions made in hallway conversations, and business logic buried deep within spaghetti code. This creates a massive, invisible burden we call **Context Debt**.

When generic, generalist AI assistants (like a raw LLM session) are introduced to these environments, they fail inevitably. This failure manifests in two critical ways:

1. **The "Black Box" Effect:** The AI cannot see the "why" behind the code. It suggests modern solutions that break legacy constraints because those constraints were never documented explicitly.  
2. **Specification Drift (The Silent Killer):** Generalist AIs have a tendency to be "too helpful." When they encounter a gap between the documentation (Spec) and the actual code (Reality) during implementation, they often fix it "on the fly" without authorization.  
   * *Result:* The code works, but the documentation becomes obsolete. The design intent is lost. The project becomes unmaintainable.  
* **The Solution:** We do not simply "add AI tools" to a broken process. We **refactor the project context itself**. By making implicit context explicit and machine-readable, we pay off the Context Debt, creating an environment where AI can operate safely and effectively.

## **3\. The Protocol: ANTP v1.3 Detailed Layers**

We have defined the **AI-Native Transformation Protocol (ANTP)**, a comprehensive framework consisting of four strictly integrated layers. Each layer addresses a specific aspect of the human-AI collaboration gap.

| Layer | Component | Description & Strategic Value | Tech Stack |
| :---- | :---- | :---- | :---- |
| **L1** | **Constitution** | **The Rule of Law.** Defines the project's immutable laws, coding standards, and security policies. It acts as the "Global System Prompt" that applies to every interaction, ensuring consistency across all agents. | .github/copilot-instructions.md |
| **L2** | **Templates** | **Standardized Workflows.** A library of reusable prompt patterns for repetitive tasks (e.g., "Generate Unit Test", "Refactor Method"). These ensure that routine tasks are executed with high precision and uniform quality, regardless of the user. | .github/prompts/\*.prompt.md |
| **L3** | **Knowledge** | **Explicit Context / The Brain.** A standardized, machine-readable summary of the project (using the llms.txt standard). This converts scattered docs into a high-density information source that agents can query to understand the "Big Picture" without hallucinating. | llms.txt (Markdown) |
| **L4** | **Agents** | **The Workforce.** A team of specialized AI personas. Unlike a general chatbot, these agents have narrow scopes, specific tools, and strict authority boundaries. They prevent the "One AI fits all" problem. | .github/agents/\*.agent.md |

## **4\. Architecture: The Specialized Six (L4 Agents)**

To combat "Specification Drift" and ensure architectural integrity, we enforce the **Anti-Generalist Principle**. We do not allow "role-less" AI interactions. Instead, we define 6 specific roles, partitioning responsibilities to mimic a high-functioning human software team.

### **A. Management Layer (Authority Holders)**

These agents are the "Thinkers." They hold the power to decide *what* gets built and *how*.

1. **@Architect (The Gatekeeper):**  
   * **Responsibility:** High-level system design, architectural integrity, and impact analysis.  
   * **Authority:** **Sole authority** to approve specification changes and architectural decisions.  
   * **Output:** Mermaid diagrams, ADRs (Architecture Decision Records), and finalized specifications.  
2. **@BusinessAnalyst (The Translator):**  
   * **Responsibility:** Bridging the gap between vague human desires and concrete technical requirements.  
   * **Authority:** Defines *what* the system should do (User Stories, Acceptance Criteria).  
   * **Constraint:** Never writes implementation code. Focuses purely on logic and flow.  
3. **@QualityGuard (The Enforcer):**  
   * **Responsibility:** Code review, security auditing, and rule enforcement.  
   * **Authority:** Can veto any code that passes compilation but fails the "Constitution" (L1).  
   * **Behavior:** Acts as a strict, unyielding reviewer who cares more about long-term maintainability than short-term speed.  
4. **@Librarian (The Keeper of Truth):**  
   * **Responsibility:** Documentation & Context maintenance.  
   * **Trigger:** Activates whenever code changes to ensure docs/ and llms.txt are synchronized.  
   * **Goal:** To ensure that the "Map" (Docs) always matches the "Territory" (Code).  
5. **@Gardener (The Maintainer):**  
   * **Responsibility:** Proactive technical debt management, dependency updates, and dead code removal.  
   * **Behavior:** Works in the background or on specific maintenance sprints, ensuring the codebase doesn't rot over time.

### **B. Execution Layer (Restricted)**

This agent is the "Doer." They focus on speed and syntax.

6. **@Developer (The Implementer):**  
   * **Role:** Pure Implementation. Translates Specs into Syntax.  
   * **Strict Constraint (The Anti-Drift Lock):** **Zero authority to change specifications.**  
   * **The "Panic Button" Protocol:** If the Developer Agent encounters a logical contradiction, missing requirement, or API mismatch that prevents implementation *exactly as specified*, it **MUST NOT** improvise a solution.  
   * **Escalation:** It must STOP immediately and output a structured request to escalate the issue back to @Architect. This forces the human user to pause, rethink the design, and update the docs, effectively preventing drift.

## **5\. Implementation Strategy (Technical Decisions)**

### **Target Platform & Philosophy**

* **Primary Platform:** Visual Studio Code \+ GitHub Copilot.  
* **Philosophy:** "Zero Friction Adoption." We avoid requiring users to install complex Python scripts or build custom VS Code extensions. Instead, we leverage the native, file-based configuration capabilities of Copilot.  
* **Mechanism:** GitHub Copilot **Custom Agents** (.github/agents/) and **Prompt Files** (.github/prompts/).

### **Key Technology: handoffs & Prompt Files**

We selected this specific implementation path to create a GUI-driven, guided experience that feels like a full application, despite being just a set of Markdown files.

1. **The Engine (/terraformer):**  
   * **Implementation:** A dynamic **Prompt File** located at .github/prompts/terraformer.prompt.md.  
   * **Trigger:** User simply types /terraformer in Copilot Chat.  
   * **Dynamic Intelligence:**  
     1. **Fetch Latest Docs:** It first accesses https://code.visualstudio.com/docs/copilot/customization/custom-agents. This is critical because the YAML syntax for agents evolves rapidly. The engine effectively "updates itself" before running.  
     2. **Analyze Context:** It performs a deep scan of the user's workspace (file tree, README, tech stack).  
     3. **Generate Agents:** It outputs the 6 \*.agent.md files, tailored specifically to the project's language (e.g., generating Japanese prompts for a Japanese team) and framework constraints.  
2. **The Ecosystem (Agents & Handoffs):**  
   * **Implementation:** **Custom Agents** defined in .github/agents/\*.agent.md.  
   * **The UX Magic (Handoffs):** We utilize the handoffs property in the YAML frontmatter.  
     * When @Architect finishes a design, a button labeled **"Start Implementation (@Developer)"** appears.  
     * When @Developer hits a blocker, a button labeled **"🛑 Escalate to Architect"** appears.  
   * **Strategic Value:** This is not just UI candy. It **systemically enforces the ANTP workflow**. It reduces the cognitive load on the user (no need to remember who to call next) and physically prevents the AI from skipping the critical review/design phases.

## **6\. Repository Structure**

terraformer/  
├── docs/  
│   ├── PROJECT\_CHARTER.md       \# The "Constitution" of this project. Detailed definition of ANTP v1.3.  
│   └── DEVELOPMENT\_CONTEXT.md   \# This file. The ADR and single source of truth for AI context.  
├── prompts/  
│   └── terraformer.prompt.md    \# The Meta-Engine. The executable logic that bootstraps the protocol.  
└── README.md                    \# Entry point for human users.

## **7\. Future Roadmap**

* **Validation Phase:** Conduct user testing to verify the handoffs UI behavior in various VS Code environments (Insiders vs. Stable) to ensure robustness.  
* **L3 Automation:** Develop a specialized generator for L3 (llms.txt) to automate the @Librarian logic. This will likely involve a script or a more complex prompt chain to summarize code into high-level context.  
* **CI/CD Integration:** Explore ways to trigger @QualityGuard automatically within GitHub Actions, not just in the IDE chat.  
* **MCP Expansion:** Investigate integrating Model Context Protocol (MCP) servers to give agents direct access to external tools (e.g., Jira for @BusinessAnalyst, Database for @Architect).
