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

3. **General Development Discipline:**
   - **Verification before completion**: Test suites and typechecks must be verified prior to completing tasks.
   - **Git cleanliness**: Always check `git status -s` and `git diff` before committing.
   - **Credential safety**: Strict prohibition against committing `.env` files or raw API secrets.

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
Clone or copy `SKILL.md` into your global config directory:
```bash
# Windows
mkdir "%USERPROFILE%\.gemini\config\skills\dev-skill"
copy SKILL.md "%USERPROFILE%\.gemini\config\skills\dev-skill\"

# Linux / macOS / WSL
mkdir -p ~/.gemini/config/skills/dev-skill
cp SKILL.md ~/.gemini/config/skills/dev-skill/
```

### Claude Code
```bash
mkdir -p ~/.claude/skills/dev-skill
cp SKILL.md ~/.claude/skills/dev-skill/
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
