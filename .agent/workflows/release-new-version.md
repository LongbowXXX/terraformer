---
description: Release a new version of the project
---

1. Determine the next version

   - Run `git describe --tags --abbrev=0` to get the last tag (e.g., `v0.0.5`).
   - If the user provided a version, use it.
   - If not, parse the last tag and increment the patch version (e.g., `v0.0.5` -> `v0.0.6`).

2. Check changes since the last version

   - Run `git describe --tags --abbrev=0` to get the last tag.
   - Run `git log <last-tag>..HEAD --pretty=format:"%s"` to see the commit messages since the last tag.
   - Run `git diff <last-tag>..HEAD --stat` to see which files have changed.
   - Run `git diff <last-tag>..HEAD` to view the actual code changes and ensure the commit messages match the reality (commit messages can be misleading).

3. Update CHANGELOG.md

   - Add a new header for the new version with the current date: `## [<version>] - <YYYY-MM-DD>`.
   - Categorize the changes (Added, Changed, Deprecated, Removed, Fixed, Security) based on the git log.
   - Update the previous version's header to include the link if using link references (optional).

4. Commit the changes

   - Run `git add CHANGELOG.md`
   - Run `git commit -m "chore: release v<version>"`

5. Tag the release

   - Run `git tag v<version>`

6. Push changes and tags
   - Run `git push origin HEAD --tags`
