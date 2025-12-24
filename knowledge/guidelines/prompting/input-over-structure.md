# Input Over Structure (3S + S.S.G.)

## Background & Purpose

In the past, AI models had strict input token limits, so "Short" and "Simple" summarization was recommended.
However, current models (Gemini 3 Pro/Flash, GPT-5.2, etc.) can process massive amounts of context.

The traditional guideline of "Pass only the necessary information concisely and force the user to explain logically" places an unnecessary burden on engineers and leads to missing information (a cause of hallucinations).

The new prompting principle **"Input Over Structure"** prioritizes **"Sufficient"** over "Necessary and Sufficient" (MECE).

## 3S Principle

Three principles for providing context:

1.  **Specific**

    - Write "Returns error code 500" instead of "It's acting weird".
    - Avoid ambiguous expressions; present specific phenomena and values.

2.  **Sufficient**

    - **[IMPORTANT]** Do not fear long text. Rather than editing out information to summarize, paste the entire log or code as is.
    - For AI, "Too much information (Noise)" is far better than "Not enough information".
    - Do not hesitate to include all potentially relevant files.

3.  **Source-based**
    - Do not try to explain the phenomenon in your own words; present the "Primary Source" (Source) such as error logs, actual code, and specifications as they are.
    - Do not mix in your own interpretations or biases.

## S.S.G. Framework

This is a "List of Materials to Pass to AI". You do not need to write beautiful sentences.

- **Situation**
  - Copy and paste the current error logs, error codes, etc. (No summarization needed).
  - Primary information on "What is happening".
- **Source**
  - Attach relevant files using `#file` or `@workspace`.
  - Logs, configuration files, specifications, etc.
- **Goal**
  - Concise statement of "What you want to do".
  - If **Situation** and **Source** are sufficient, simple commands like "Fix the error" or "Write a test" are enough.

## Expected Effects

- Even engineers who are not good at explaining can get high-precision answers simply by passing logs and files.
- Reduces AI guessing (hallucinations) and unnecessary confirmation steps (back-and-forth) caused by missing information.
