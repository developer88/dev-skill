# dev-skill

Universal development rules and behavioral constraints for AI coding agents (Antigravity, Claude Code, Cursor, Gemini CLI, GitHub Copilot, Codex, and more).

## Overview

`dev-skill` establishes essential ground rules and safeguards that coding assistants must follow when working across your repositories.

### Key Rules Enforced

1. **Releases & Tags Guardrail:**
   - **Never create releases or tags autonomously**: The agent will never run `git tag` or publish GitHub/GitLab releases without an explicit, direct instruction from the user.
   - **Never update already published releases**: The agent will not modify, overwrite, re-tag, delete, or re-upload assets for existing published releases unless explicitly directed.

2. **Execution Environment Hygiene:**
   - **Node.js & NPM inside WSL**: On Windows workstations with WSL, `npm` and `node` tasks must always run inside WSL (`wsl -- npm ...`), avoiding native Windows node path conflicts.

3. **Comprehensive Test Coverage:**
   - **Full test pyramid**: Every piece of work must have thorough test coverage—not just unit tests, but also integration tests and screenshot / visual regression tests for UI changes.
   - **Zero failure policy**: All tests across all suites must pass with 100% success before finishing.

4. **Mandatory Manual Acceptance by Independent Agent:**
   - **Independent verification**: Every finished task must pass manual acceptance testing performed by an independent agent (or dedicated review subagent).
   - **Thorough UI inspection**: The agent manually checks all UI elements, clicks through interactive components, inspects visual state, and validates that the solution is functional, stable, and completely bug-free.

5. **General Development Discipline:**
   - **Clean Git State**: Inspect changes with `git status -s` and `git diff` before committing.
   - **Credential Safety**: Strict prohibition against committing `.env` files or raw API secrets.

---

## Installation

### Recommended: Install via `skills.sh` CLI

Install globally for all supported coding agents with one command:

```bash
npx skills add developer88/dev-skill -g
```

To install only for the current project:

```bash
npx skills add developer88/dev-skill
```

To install directly using the GitHub URL:

```bash
npx skills add https://github.com/developer88/dev-skill.git -g
```

### Supported Agents

`skills add` automatically discovers and links to:
- **Google Antigravity / Gemini CLI** (`~/.gemini/config/skills/dev-skill`)
- **Claude Code** (`~/.claude/skills/dev-skill`)
- **GitHub Copilot CLI**
- **Cursor**
- **Pi / OpenCode / Codex** (`~/.agents/skills/dev-skill`)

---

## Manual Installation

If you prefer installing manually without `npx`:

### Google Antigravity & Gemini CLI
Clone or symlink `SKILL.md` into your global config directory:
```bash
# Windows (Junction)
New-Item -ItemType Junction -Path "$HOME\.gemini\config\skills\dev-skill" -Target "<path_to_repo>"

# Linux / macOS / WSL (Symlink)
ln -s "<path_to_repo>" ~/.gemini/config/skills/dev-skill
```

### Claude Code
```bash
ln -s "<path_to_repo>" ~/.claude/skills/dev-skill
```

---

## Updating

Update all installed global skills to the latest version:

```bash
npx skills update -g
```

Or update this skill specifically:

```bash
npx skills update dev-skill -g
```

---

## License

[MIT](LICENSE)
