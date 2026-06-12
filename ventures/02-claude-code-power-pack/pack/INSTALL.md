# Install Guide

Three ways to install, depending on scope. All of them are just copying files — there is no installer, registry, or network access involved.

## Option A — Single project (recommended first)

Installs for one repository. Lowest blast radius; lets you evaluate the pack before going global.

```bash
cd /path/to/your-project
mkdir -p .claude
cp -r /path/to/pack/agents .claude/
cp -r /path/to/pack/skills .claude/
```

Result:

```
your-project/
└── .claude/
    ├── agents/code-reviewer.md ... (30 files)
    └── skills/tdd-loop/SKILL.md ... (10 dirs)
```

## Option B — Global (all your projects)

Installs for every project on your machine. Project-level files with the same name take precedence over global ones, so you can still override per-project.

```bash
mkdir -p ~/.claude
cp -r /path/to/pack/agents ~/.claude/
cp -r /path/to/pack/skills ~/.claude/
```

## Option C — Team (checked into the repo)

Same as Option A, then commit `.claude/` so every teammate (and Claude Code on the web/CI) gets the same setup:

```bash
git add .claude/agents .claude/skills
git commit -m "Add Claude Code agent and skill pack"
```

Tip for teams: review the pack in the PR like any other code — these files steer an AI that edits your codebase, and they deserve the same scrutiny.

## Verify the install

1. Open Claude Code in the project.
2. Run `/agents` — all 30 agents should be listed with their descriptions.
3. Ask: *"use the repo-onboarder subagent to give me a tour"* — a good first run that touches nothing.
4. Skills check: ask *"what skills do you have available?"* or invoke one directly: *"run the daily-wrap skill"*.

## Picking and choosing

You don't need all 30. A sensible minimal set if you want to start light:

```bash
cd /path/to/pack/agents
cp code-reviewer.md bug-hunter.md test-writer.md pr-describer.md \
   claude-md-auditor.md /path/to/your-project/.claude/agents/
```

Frontend folks: add `a11y-auditor`. Backend: `api-designer`, `migration-writer`, `sql-analyst`. On-call: `incident-analyzer`, `ci-fixer`.

## Troubleshooting

**Agent doesn't appear in `/agents`**
- The file must be directly in `.claude/agents/` (not a subdirectory) and end in `.md`.
- Frontmatter must start at line 1 with `---` and close with `---`. No blank line above the first `---`.
- YAML errors (a stray `:` inside an unquoted description is the usual culprit) silently break a file. Quote the description if it contains special characters.

**Agent appears but never auto-triggers**
- Auto-delegation matches on the `description`. If you've edited it into something vague, Claude can't match it. Trigger explicitly ("use the X subagent") or restore a trigger-oriented description ("Use when/after ...").

**Name collisions**
- If a project already has an agent with the same name, the project-level file wins over global. Rename one of them (`name:` in frontmatter AND the filename, keep them identical).

**Skill not loading**
- Each skill must live at `.claude/skills/<name>/SKILL.md` — the per-skill directory is required, and the file must be named exactly `SKILL.md`.

**Hooks (if you adopted any) misbehaving**
- Hooks live in `.claude/settings.json`, are JSON (comments not allowed), and shell commands run with your shell's environment. Test the command standalone in a terminal first. See `hooks/README.md`.

**Still stuck?**
- Run `claude doctor` for environment-level diagnostics, and check the official docs for your CLI version's agent/skill spec — the format is stable but new optional fields appear over time.
