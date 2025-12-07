# XML + Markdown Structured Prompting Guide

This guide explains how to combine **XML tags** and **Markdown** to create prompts that are both machine-parseable and human-readable.

## 1. The Power of XML + Markdown

While XML provides strict structural boundaries that LLMs excel at parsing, Markdown proivdes semantic meaning and readability. combining them gives you the best of both worlds.

### Why this combination works:

1.  **XML defines the "Container"**: It tells the model _where_ information looks like and _what_ it is (e.g., `<instruction>`, `<context>`). This prevents context bleeding.
2.  **Markdown defines the "Content"**: It tells the model _how_ to interpret the text inside (e.g., **bold** for emphasis, `-` for lists, `###` for hierarchy).

> **Concept**: Think of XML as the **envelope** and Markdown as the **formatted letter** inside.

## 2. Benefits

- **Clear Boundaries (XML)**: No confusion between instructions and data.
- **Rich Semantics (Markdown)**: Lists, headers, and code blocks allow for complex instructions without massive blocks of plain text.
- **Dual Readability**:
  - **For AI**: It parses the XML structure first, then processes the Markdown semantics.
  - **For Humans**: The prompt remains visually organized and easy to edit.

## 3. Common XML Tags Cheatsheet

| Category     | Tag                  | Purpose                                                                |
| :----------- | :------------------- | :--------------------------------------------------------------------- |
| **Meta**     | `<system>`           | Defines the absolute rules and behavior of the system.                 |
|              | `<role>`             | Sets the persona (e.g., "Expert Python Dev").                          |
| **Data**     | `<context>`          | Background information required for the task.                          |
|              | `<documents>`        | Reference materials or search results.                                 |
|              | `<example>`          | Few-shot examples to guide the model.                                  |
| **Control**  | `<instruction>`      | The core task command.                                                 |
|              | `<constraints>`      | Negative rules (what _not_ to do).                                     |
| **Thinking** | `<thinking>`         | A space for the model to "reason" before answering (Chain of Thought). |
| **Agentic**  | `<workflow>`         | Defines the specific loop or steps for an agent to follow.             |
|              | `<stopping_rules>`   | Absolute safety boundaries (e.g., "STOP if you start implementing").   |
|              | `<plan_research>`    | Instructions focused on context gathering and research phases.         |
|              | `<plan_style_guide>` | Specific formatting rules for the agent's output (e.g., plans).        |
| **Output**   | `<output>`           | The final answer container.                                            |

## 4. Practical Example: XML + Markdown

Here is a standard template showing how Markdown organizes the content _within_ the XML tags:

```xml
<system>
    You are a helpful assistant specialized in summarizing technical documents.
</system>

<context>
    <documents>
        <document index="1">
            ### Spec v1.0
            (Content of the first document...)
        </document>
    </documents>
</context>

<instruction>
    ### Your Task
    Summarize the provided documents in **3 bullet points**.

    ### Process
    1.  **Analyze**: Look for key themes in the `<thinking>` block.
    2.  **Draft**: Write the summary in the `<output>` block.
</instruction>

<constraints>
    - **No Jargon**: Use simple language.
    - **Length**: Keep each point under 20 words.
</constraints>
```

**Expected Output:**

```xml
<thinking>
    The document discusses X, Y, and Z. The key points are...
</thinking>

<output>
    - Point 1 summary.
    - Point 2 summary.
    - Point 3 summary.
</output>
```

## 5. Real-world References

For a live example of these tags in a production environment (specifically the Agentic tags), refer to the **VS Code Copilot Plan Agent**:

- [Plan.agent.md](https://github.com/microsoft/vscode-copilot-chat/blob/main/assets/agents/Plan.agent.md)
