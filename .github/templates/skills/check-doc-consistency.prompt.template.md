---
name: check-doc-consistency
description: Check consistency of project documentation and propose fixes.
agent: Librarian
---

# Skill: Check Documentation Consistency

You are supporting the **@Librarian**. Your goal is to verify the consistency of all documentation starting from the project's `README.md`, and propose or implement necessary corrections.

## 🎯 Objective

Ensure that:

1.  **Structure is Complete**: `README.md` acts as a proper entry point and all links work.
2.  **Content is Consistent**: Documentation matches the actual codebase (files, classes, configs).
3.  **DRY Principle is Followed**: Information is not duplicated unnecessarily.
4.  **Project Rules are Met**: Documentation follows `agents-docs/` structure and other project conventions.

## 🛠️ Execution Steps

### Step 1: Read Documentation

1.  **Read Entry Point**:

    - Use `view_file` to read `README.md`.
    - Identify key sections and links to other documents.

2.  **Read Agent Documentation**:
    - Use `list_dir` to list files in `agents-docs/`.
    - Use `view_file` to read key documents like `agents-docs/directory-structure.md`, `agents-docs/tech-stack.md`, and `agents-docs/key-flows.md`.

### Step 2: Verify Links and References

1.  **Extract Links**:

    - Identify all file paths and relative links in the read documents.

2.  **Verify Existence**:
    - Use `find_by_name` or `list_dir` to verify that linked files and directories actually exist.
    - Check for broken images or dead links.

### Step 3: Verify Content Consistency

1.  **Directory Structure**:

    - Compare `agents-docs/directory-structure.md` with the actual output of `list_dir` on the project root and key subdirectories.
    - Note any missing or obsolete directories in the documentation.

2.  **Tech Stack & Config**:

    - Compare `agents-docs/tech-stack.md` with `pyproject.toml`, `package.json`, or other configuration files.
    - Ensure versions and dependencies match.

3.  **Code References**:
    - If documents mention specific classes or functions, use `grep_search` or `find_by_name` to confirm they still exist and are named correctly.

### Step 4: Report and Fix

1.  **Generate Report**:

    - Create a summary of findings categorized by:
      - ✅ **Pass**: Items that are consistent.
      - ⚠️ **Warning**: Minor inconsistencies or potential issues.
      - ❌ **Error**: Broken links, missing files, or major contradictions.

2.  **Propose/Implement Fixes**:
    - **Auto-Fix**: For simple issues like typos or broken relative paths, use `replace_file_content` to fix them immediately.
    - **Proposal**: For structural changes or missing content, describe the recommended changes in the report.

## 📤 Output Format

Present your findings in the following format:

```markdown
# Documentation Consistency Report

## Summary

[Brief summary of the overall state of documentation]

## Findings

### ✅ Consistent Items

- README.md links are valid.
- ...

### ❌ Issues Found

- **Broken Link**: `README.md` refers to `docs/setup.md` which does not exist.
- **Outdated Content**: `directory-structure.md` misses the new `services/payment` directory.

## Actions Taken

- Fixed typo in `README.md`.

## Recommendations

- Update `directory-structure.md` to include `services/payment`.
```
