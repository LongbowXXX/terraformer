---
description: Improve a GitHub Copilot prompt file (.prompt.md) using XML structured prompting techniques.
---

1. Ask the user for the path to the `.prompt.md` file they want to improve, if it's not already clear from the context.
2. Read the content of the target `.prompt.md` file.
3. Read the reference guide `knowledge/xml-structured-prompting.md` to understand the XML structured prompting capability.
4. Read the official documentation: `https://code.visualstudio.com/docs/copilot/customization/prompt-files` using the `read_url_content` tool to ensure compliance with the latest rules (e.g. YAML frontmatter, allowed variables).
5. Analyze the target prompt file against the guidelines in the knowledge base and the official documentation.
6. Rewrite the _body_ of the prompt file (keeping the frontmatter intact) to use the XML structure (`<system>`, `<context>`, `<instruction>`, etc.) as described in the knowledge base.
   - Ensure strict separation of instructions and context.
   - Use Markdown within the XML tags for readability.
   - Preserve any existing logic or requirements from the original prompt.
7. Verify that the YAML frontmatter is preserved and valid.
8. Present the updated content to the user or write it back to the file if the user approves.
