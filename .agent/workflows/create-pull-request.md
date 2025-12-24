---
description: Create a pull request following project guidelines, ensuring actual code changes are verified.
---

1. **Analyze Context & Guidelines**

   - Read `knowledge/guidelines/pr-creation-guidelines.md` to understand the current standards.
   - Read `knowledge/workflows/templates/pull_request.md` to load the required template structure.

2. **Check Git Status & Identify Base Branch**

   - Run `git status` to verify you are on the correct branch and if there are uncommitted changes.
   - Identify the target base branch (typically `main` or `master`). You can check available branches with `git branch -a`.

3. **Verify Actual Code Changes (CRITICAL)**

   - **Do not rely on git log/commit messages.** They may be incomplete or misleading.
   - Run `git diff <base_branch>...HEAD --stat` to see the list of changed files.
   - For _every_ significant file changed, run `git diff <base_branch>...HEAD -- <filename>` to read the actual code differences.
   - Understand _exactly_ what was modified, added, or deleted.

4. **Draft PR Content**

   - Construct the PR Title and Description based on your analysis of the **actual code**.
   - **Title**: Clear and concise (see guidelines).
   - **Description**: Must follow the template structure:
     - **Context (Why)**: Link the issue (if known) and explain the motivation.
     - **Changes (What)**: High-level summary of changes (don't line-by-line narrate, but be accurate based on your diff reading).
     - **Verification**: Explain how to verify the changes.
     - **Risks**: Note any risks.
     - **Self-Check**: Ensure all checklist items are met.

5. **Create Pull Request**
   - **Preferred Method:** If the `remote-github` MCP server is available, use the `create_pull_request` tool.
     - Ensure all fields (owner, repo, title, body, head, base) are correctly populated.
   - **Alternative:** Use the `gh` CLI tool or manual creation.
     - Command: `gh pr create --title "<Title>" --body "<Description>"`
   - If automation fails, propose the Title and Body to the user so they can create it manually.
