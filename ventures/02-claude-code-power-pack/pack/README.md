# Claude Code Power Pack

**30 production-grade subagents · 10 skills · 8 hook recipes · 4 CLAUDE.md templates**

A drop-in `.claude/` toolkit for developers who use Claude Code daily and would rather skip the weeks of prompt-engineering it takes to build a good agent setup from scratch.

## What's inside

```
pack/
├── agents/                30 subagents (.md with YAML frontmatter)
│   ├── DEV CORE          code-reviewer, bug-hunter, test-writer, refactor-surgeon,
│   │                     perf-profiler, security-auditor, api-designer,
│   │                     migration-writer, docs-writer, dependency-auditor
│   ├── QUALITY           type-tightener, dead-code-finder, error-message-improver,
│   │                     a11y-auditor, i18n-extractor
│   ├── OPS               ci-fixer, release-notes-writer, dockerizer,
│   │                     incident-analyzer, env-auditor
│   ├── WORKFLOW          pr-describer, issue-triager, spec-writer,
│   │                     commit-splitter, conflict-resolver
│   └── META              prompt-improver, claude-md-auditor, repo-onboarder,
│                         sql-analyst, data-cleaner
├── skills/                10 skills (each a dir with SKILL.md)
│                         tdd-loop, pr-review, security-sweep, perf-baseline,
│                         release-flow, bug-hunt, codebase-tour,
│                         api-contract-check, refactor-plan, daily-wrap
├── hooks/                 8 copy-paste hook recipes (settings.json snippets)
├── claude-md-templates/   4 opinionated CLAUDE.md starters
│                         web-app, api-service, monorepo, library
├── README.md             this file
└── INSTALL.md            detailed install + troubleshooting
```

Every agent follows the same five-part structure — role, when invoked, process, output format, guardrails — so behavior is predictable across the whole pack.

## Requirements

- Claude Code CLI (any recent version; subagents and skills are core features)
- That's it. No dependencies, no build step, no telemetry. It's all plain Markdown and JSON.

## 60-second install

From the unzipped pack directory, into the project you're working on:

```bash
mkdir -p /path/to/your-project/.claude
cp -r agents skills /path/to/your-project/.claude/
```

Verify: open Claude Code in that project and run `/agents` — you should see all 30 listed.

Hooks and CLAUDE.md templates are not auto-installed by design — they change behavior and deserve a deliberate look. See `hooks/README.md` and `claude-md-templates/` and copy what you want.

For global install (`~/.claude/`), team install (checked into the repo), and troubleshooting, see [INSTALL.md](INSTALL.md).

## How subagents trigger

Two ways:

1. **Automatic delegation** — Claude reads each agent's `description` and delegates when the task matches. E.g. after you ask for a change and then say "review what you just wrote", the `code-reviewer` description matches and gets picked up.
2. **Explicit invocation** — just name it: *"use the code-reviewer subagent on src/auth/"*, *"have the migration-writer plan this schema change"*. Explicit always works; use it when you want a specific agent for sure.

## How skills trigger

Skills load when their `description` matches what you ask for: *"run the tdd-loop on this feature"*, *"do a security-sweep of the repo"*, *"give me a codebase-tour"*. You can also reference them explicitly the same way.

## Customizing

These files are a starting point, not a sealed product — edit freely:

- **Narrow an agent's tools**: tighten the `tools:` line in its frontmatter.
- **Pin a model**: add `model: haiku` to cheap/mechanical agents (e.g. `release-notes-writer`), `model: opus` to deep reasoning ones (e.g. `security-auditor`).
- **Add project context**: append project-specific conventions to any agent's body — e.g. your error-envelope shape inside `api-designer`.

## License

Personal and commercial use in unlimited projects, for you and your team. You may modify everything. You may **not** resell or redistribute the pack itself (or trivially modified copies) as a product.

## Support & updates

Updates are pushed through the store you bought this from — past buyers get them free. Found a problem or want an agent added? Reply through the store page; pack updates ship quarterly.
