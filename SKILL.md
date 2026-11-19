---
name: dev-skill
description: General rules on how things work and how the AI agent must behave across projects, including strict release, git, test coverage, manual acceptance, changelogs, Obsidian Kanban tasks, and execution constraints.
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

3. **User-Facing vs. Developer Changelogs & Release Notes:**
   - **User-Facing Projects (Apps with a UI):**
     - If the project is user-facing (e.g. web apps, mobile apps, desktop apps, browser extensions, Obsidian plugins with a UI):
       - The changelog / release notes must be easily understandable for non-super technical people.
       - **Do NOT** just list raw git commit messages or developer shorthand (e.g., "refactor hook dependencies", "bump tsx version").
       - **Rephrase and elaborate:** Deliver clear, detailed explanations of what actually changed from an end-user perspective, what problems were solved, and what new capabilities are available.
   - **Tooling / Non-UI Projects (CLI tools, libraries, backend services):**
     - If the project is strictly a developer tool, CLI utility, library, or backend infrastructure without an end-user UI:
       - Standard developer-oriented changelogs (e.g., Conventional Commits, technical bullet points) are appropriate.

## 2. Environment & Command Execution

- **Node.js & NPM:** ALWAYS execute `npm` and `node` inside WSL (e.g., `npm install`, `npm run dev`, `npm test`, `npm run build`).
- **Windows Host:** Never invoke `node` directly from Windows itself.

## 3. Comprehensive Test Coverage

Every piece of work must have proper and thorough test coverage across all layers:

- **Not Just Unit Tests:** Unit tests alone are never sufficient. Test suites must cover the real behavior of the feature or fix.
- **Integration Tests:** Verify component interactions, API requests/responses, state persistence, and full user journeys.
- **Screenshot & Visual Regression Tests:** Any work touching the user interface must include screenshot / visual tests to verify styling, layout, theme compatibility, and responsiveness across breakpoints.
- **All Tests Must Pass:** 100% of the test suite (unit, integration, and visual tests) must be green prior to considering work complete.

## 4. Mandatory Manual Acceptance by Independent Agent

Every finished piece of work must undergo and pass manual acceptance testing:

- **Independent Reviewer/Agent:** An independent verification agent (or fresh verification subagent) must inspect all changes.
- **Manual UI & Behavior Walkthrough:** The independent agent must manually check all altered UI elements, click through interactive flows, exercise empty/loading/error states, and inspect console logs/network behavior.
- **Zero Bug Guarantee:** The agent must rigorously validate that the changes work as intended in practice and introduce zero bugs or regressions before marking the task done.

## 5. Obsidian Kanban Board Tasks

When adding or managing tasks on an Obsidian Kanban board:

- **Short Tasks (One-liners):**
  - If a task is concise (a simple one-liner of around 10 words or fewer) without needing additional context or description, it can be added directly as a plain task item on the board.
- **Detailed Tasks (Long Titles, Descriptions, or Context):**
  - If a task has a long title, requires a description, context, acceptance criteria, or any additional notes/information:
    - **Always create a dedicated subpage (`.md` file)** in the exact same directory where the Kanban board file is located.
    - Place the detailed title, full description, checklist, and background info in that subpage.
    - **Link the subpage as the task item** on the Kanban board (e.g., `- [ ] [[Subpage Name]]`).

## 6. General Development Hygiene

- **Verification Before Completion:** Always run test suites and verification checks before declaring a task complete.
- **Clean Git State:** Inspect changes with `git status -s` and `git diff` before committing.
- **Safety First:** Never commit secrets, credentials, or `.env` files to version control.
