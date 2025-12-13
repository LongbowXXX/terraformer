---
description: Create a new skill (custom prompt) in .github/template-skills/
---

1.  **Preparation**:

    - [ ] Read the official VS Code Custom Prompt documentation to ensure compliance with the latest specifications: `https://code.visualstudio.com/docs/copilot/customization/prompt-files`
    - [ ] Ask the user for the name and goal of the new skill if not already provided.

2.  **Create Skill File**:

    - [ ] Create a new file in `.github/template-skills/` with the format `[skill-name].prompt.template.md`.
    - [ ] The content MUST be a valid VS Code Custom Prompt file with YAML frontmatter.
    - [ ] Use `.github/template-skills/create-custom-prompt.prompt.template.md` as a reference for structure, but adapt the content to the specific goal of the new skill.
    - [ ] Ensure the "todos" technique is applied if the skill involves complex tasks (Task Initialization section).

3.  **Verification**:
    - [ ] Verify the file has the correct extension: `.prompt.template.md`.
    - [ ] Verify the file is in the correct directory: `.github/template-skills/`.
    - [ ] Verify the YAML frontmatter is valid.
