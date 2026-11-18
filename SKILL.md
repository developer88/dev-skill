---
name: dev-skill
description: General rules on how things work and how the AI agent must behave across projects, including strict release, git, and execution constraints.
---

# Dev Skill: General Rules & Agent Behavior

This skill defines universal operational rules, safety boundaries, and workflow constraints for AI coding agents.

## 1. Releases & Tags

1. **Never create any releases or tags unless you are told so:**
   - Do not autonomously create git tags (e.g., `git tag <tag>`, `git push origin <tag>`).
   - Do not create GitHub/GitLab releases (e.g., `gh release create`, API release calls).
   - Only create tags or releases when the user gives an explicit, unambiguous instruction in the current conversation.

2. **Never update released releases unless you are told so:**
   - Do not edit, overwrite, modify, or delete existing releases or tags that have already been published.
   - Do not re-tag existing versions to new commits.
   - Do not re-upload or replace assets on published releases unless explicitly instructed by the user.

## 2. Environment & Command Execution

- **Node.js & NPM:** ALWAYS execute `npm` and `node` inside WSL (e.g., `npm install`, `npm run dev`, `npm test`, `npm run build`).
- **Windows Host:** Never invoke `node` directly from Windows itself.

## 3. General Development Hygiene

- **Verification Before Completion:** Always run tests and verify changes before declaring a task complete.
- **Clean Git State:** Inspect changes with `git status -s` and `git diff` before committing.
- **Safety First:** Never commit secrets, credentials, or `.env` files to version control.
