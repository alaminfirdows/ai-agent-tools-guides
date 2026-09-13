# AI Agent Tools Guides

A collection of ready-to-use Claude Code configs: subagents, slash commands, skills, workflow checklists, and settings/hooks. Mostly geared toward Laravel projects. Copy what you need into your project's `.claude/` folder (or `~/.claude/` for global use).

## What's Inside

### `agents/` — Subagents
Specialized agents Claude can delegate to. Drop into `.claude/agents/`.
- `coder-junior`, `coder-assistant`, `coder-senior` — implementation agents by task complexity
- `code-reviewer`, `security-reviewer` — review agents, use proactively before commits
- `debugger` — root-causes failing tests/errors before fixing
- `test-writer` — writes/fixes Pest tests

### `commands/` — Slash Commands
Drop into `.claude/commands/`.
- `/explore-modules` — explore multiple codebase modules in parallel
- `/fix-issue <issue-number>` — investigate and fix a GitHub issue
- `/issue-read <issue-number-or-link>` — display a GitHub issue with context
- `/pr-summary` — summarize a pull request's changes

### `skills/` — Skills
Auto-invoked based on file paths or description match. Drop into `.claude/skills/`.
- `team-billing` — enforces multi-tenancy/billing rules when touching Controllers/Models/Actions
- `team-billing/security-review` — security-focused diff review (manual invocation only)

### `workflows/` — Checklists
Step-by-step markdown playbooks for common jobs: `bug-fix`, `database-migration`, `new-feature`, `laravel-review`, `security-audit`. Use as reference or feed to the `Workflow` tool.

### `calude/`
- `hooks/git-guard.sh` — blocks `git push`/`commit`/force-push commands, forcing PR-based workflow
- `settings/` — example `settings.json` / `settings.local.json`
- `spec-driven-development/` — `/spec`, `/task`, `/review`, `/commit` commands for a spec-first workflow, plus a worked example

## How to Use

1. Copy the folder(s) you want into your project's `.claude/` directory, e.g.:
   ```bash
   cp -r agents commands skills /path/to/your-project/.claude/
   ```
2. For global use across all projects, copy into `~/.claude/` instead.
3. Restart Claude Code (or start a new session) so it picks up the new agents/commands/skills.
4. Slash commands run with `/command-name`; agents are invoked automatically or via `Use the <agent> subagent`; skills auto-trigger on matching files/descriptions.
