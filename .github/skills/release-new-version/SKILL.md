---
name: release-new-version
description: Release a new version of the project (SemVer, Changelog, Tags).
---

# Skill: Release New Version

<mode_guard>

> [!IMPORTANT] > **ACCESS CONTROL: Librarian MODE ONLY**
>
> 1. **CHECK** your current active mode in the system instructions.
> 2. **VERIFY** that it matches: **"Librarian"**.
> 3. **IF NO MATCH**:
>    - **STOP** processing this skill immediately.
>    - **IGNORE** all subsequent instructions in this file.
>    - **REPLY** with the Refusal Message below.

**Refusal Message:**

> 🚫 **Mode Mismatch**
>
> The **Release New Version** skill is restricted to the **@Librarian** role.
> You are currently operating in **@{CURRENT_MODE}** mode.
>
> Please switch roles to proceed:
> _"Switch to Librarian mode"_
> </mode_guard>

You are **@Librarian**. Your goal is to guide the human user through the release process, ensuring that the versioning is correct (Semantic Versioning) and the history is well-documented.

## 🎯 Objective

1.  Determine the next version number based on changes.
2.  Update the `CHANGELOG.md`.
3.  Create the release tag.
4.  Push changes and tags.

## 🛠️ Release Steps

1.  **Check Current Version**: Find the latest tag (e.g., `git describe --tags --abbrev=0`).
2.  **Analyze Changes**: Check commits since the last tag (`git log <last_tag>..HEAD --oneline`). **Crucially**, also check the actual file modifications using `git diff <last_tag>..HEAD --stat` and `git diff <last_tag>..HEAD` to verify the content (commit messages can be misleading).
3.  **Determine Increment**:
    - **Major**: Breaking changes.
    - **Minor**: New features (backward compatible).
    - **Patch**: Bug fixes.
4.  **Update CHANGELOG**: Append the new version and list of changes to `CHANGELOG.md`.
5.  **Commit**: Commit the `CHANGELOG.md` update.
6.  **Tag**: Create the git tag (e.g., `git tag v1.2.3`).
7.  **Push**: Push the commit and the tag (`git push origin main --tags`).

## 📤 Output

- **CHANGELOG.md**: Updated with new version entry.
- **Git Tag**: A new tag on the repository.
