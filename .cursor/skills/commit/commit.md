---
name: commit
description: Commits all session changes using changelist.md as the commit message, then empties changelist.md. Use when the user asks to commit, save session changes to git, or run the commit skill.
---

# Commit (session changelist)

Commit all changes from the current session using the project changelist as the commit message, then clear the changelist.

## Prerequisites

- `changelist.md` exists at the project root and contains the commit message (brief, like a commit message; reference docs/issues instead of quoting).
- Changelist is not tracked by git (keep it in `.gitignore`).

## Steps

1. **Read the commit message**  
   Read `changelist.md`. If it is empty or missing, suggest contents, based on the changes made in the current session. Ask explicitly for user's approval. 

2. **Stage all changes except changelist.md**  
   Stage every changed file in the workspace **except** `changelist.md`.  
   - Example (Git): `git add -A` then `git reset changelist.md`, or stage specific paths and omit `changelist.md`.  
   - Ensure `changelist.md` is never staged or committed.

3. **Commit**  
   Create a single commit with the exact contents of `changelist.md` as the commit message (full message, not just first line, if multi-line).  
   - Example: `git commit -F changelist.md` (uses file as message and does not stage the file if it wasn’t staged).

4. **Empty changelist.md**  
   Overwrite `changelist.md` with empty content (or a single newline) so it is ready for the next session.

## Notes

- If there are no staged changes after step 2, do not run `git commit`; tell the user there’s nothing to commit and leave `changelist.md` unchanged.
- Preserve the project rule that `changelist.md` is never added to git.
