---
description: Improve a GitHub Copilot prompt file (.prompt.md) using XML structured prompting techniques.
---

1. Ask the user for the path to the `.prompt.md` file they want to improve, if it's not already clear from the context.
2. Read the content of the target `.prompt.md` file.
3. Read the reference guide `knowledge/xml-structured-prompting.md` to understand the XML structured prompting capability.
4. Read the official documentation: `https://code.visualstudio.com/docs/copilot/customization/prompt-files` using the `read_url_content` tool to ensure compliance with the latest rules (e.g. YAML frontmatter, allowed variables).
5. Analyze the target prompt file against the guidelines in the knowledge base and the official documentation. Determine if the current structure needs refactoring effectively to support XML tagging.
6. **[CRITICAL]** If the structure needs refactoring:
   - Perform _only_ the structural refactoring first.
   - **DO NOT** apply any XML tags in this step.
   - **DO NOT** combine structure changes with tagging.
   - **Preserve** all existing structure and text (e.g., do not remove `# Chapter` or other headers).
   - Present the refactored structure to the user and **wait for confirmation** before proceeding.
7. Once the structure is confirmed (or if no refactoring was needed):
   - Rewrite the _body_ of the prompt file (keeping the frontmatter intact) to use the XML structure (`<system>`, `<context>`, `<instruction>`, etc.) as described in the knowledge base.
   - **Preserve** existing logical structure and text content (e.g., keep `# Chapter` headers inside or outside tags as appropriate, but do not delete them).
   - Ensure strict separation of instructions and context.
   - Use Markdown within the XML tags for readability.
   - Preserve any existing logic or requirements from the original prompt.
8. Verify that the YAML frontmatter is preserved and valid.
9. Present the updated content to the user or write it back to the file if the user approves.
