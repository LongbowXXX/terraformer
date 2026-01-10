---
description: Create a new skill (custom prompt) in .github/prompts/
---

1.  **Preparation**:

    - [ ] Read the official VS Code Custom Prompt documentation to ensure compliance with the latest specifications: `https://code.visualstudio.com/docs/copilot/customization/prompt-files`
    - [ ] Ask the user for the name and goal of the new skill if not already provided.

2.  **Create Skill File**:

    - [ ] Create a new file in `.github/prompts/` with the format `[skill-name].prompt.md`.
    - [ ] The content MUST be a valid VS Code Custom Prompt file with YAML frontmatter.
    - [ ] Use `.github/prompts/create-custom-prompt.prompt.md` as a reference for structure, but adapt the content to the specific goal of the new skill.
    - [ ] Ensure the "todo" technique is applied if the skill involves complex tasks (Task Initialization section).

3.  **Verification**:
    - [ ] Verify the file has the correct extension: `.prompt.md`.
    - [ ] Verify the file is in the correct directory: `.github/prompts/`.
    - [ ] Verify the YAML frontmatter is valid.
