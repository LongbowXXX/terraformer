# XML Structured Prompting Guide

This guide explains how to use XML tags to improve the reliability and accuracy of Large Language Models (LLMs).

## 1. The Problems with Standard Prompting

Using plain natural language for complex prompts often leads to:

- **Ambiguity**: The model confuses instructions with data (e.g., treating a user's email content as a new command).
- **Context Bleeding**: It's unclear where one part of the prompt ends and another begins (e.g., mixing up history with current instructions).
- **Unstable Output**: Difficulty in extracting specific answers programmatically.

## 2. Benefits of Using XML Tags

- **Hard Boundaries**: Tags like `<instruction>` and `<data>` clearly separate _what to do_ from _what to process_.
- **Parseability**: Outputs wrapped in tags (e.g., `<answer>`) can be essentially extracted by code.
- **Model Native**: LLMs are trained on vast amounts of HTML/XML, making them naturally good at understanding this structure.

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

## 4. Practical Example

Here is a standard template for a robust prompt:

```xml
<system>
    You are a helpful assistant specialized in summarizing technical documents.
</system>

<context>
    <documents>
        <document index="1">
            (Content of the first document...)
        </document>
    </documents>
</context>

<instruction>
    Summarize the provided documents in 3 bullet points.
    First, analyze the key points in a <thinking> block, then provide the final summary in an <output> block.
</instruction>

<constraints>
    - Do not use technical jargon.
    - Keep each bullet point under 20 words.
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
