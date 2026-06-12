# Gumroad Listing — Claude Code Power Pack

---

## Product Name

**Claude Code Power Pack**

### Title Variants (for A/B testing the listing headline)

1. **Claude Code Power Pack — 30 production-grade subagents, 10 skills, 8 hook recipes, 4 CLAUDE.md templates**
2. **Skip weeks of prompt engineering: a curated, consistent `.claude/` setup for Claude Code**
3. **30 Claude Code subagents that all follow the same tested structure (plus skills, hooks, and CLAUDE.md templates)**

### One-Line Subtitle

> A drop-in `.claude/` directory for developers who'd rather ship code than tune agent prompts.

---

## Full Description

### What this is

A curated pack of **30 production-grade Claude Code subagents**, **10 skills**, **8 hook recipes**, and **4 CLAUDE.md templates**. You unzip it into `.claude/` in any repo and Claude Code immediately has a competent code reviewer, bug hunter, test writer, security auditor, PR describer, and 25 more specialists — all written to the same structure, all tested against real codebases.

You could build all of this yourself. That's not a sales trick — it's literally true, and plenty of free agent collections exist on GitHub. What you're paying for is the part the free lists don't do:

- **One consistent structure.** Every agent in this pack follows the same skeleton: *role → when invoked → process → output format → guardrails*. When you read one, you can read all 30. When you want to customize one, you know exactly where to make the cut.
- **Curation, not accumulation.** Free lists grow by PR. This pack grows by deletion. 30 agents that each earn their slot beats 300 agents of wildly varying quality where half were written in an afternoon and never touched again.
- **Tested patterns.** Each agent has been run against real repos (TypeScript, Python, Go, mixed monorepos) and revised based on what it actually produced — not what the prompt looked like it would produce.
- **Guardrails on every agent.** Every single agent has an explicit "do not" section: scope limits, things it must flag instead of fix, output it must never invent. This is the difference between an agent you can trust on a work repo and one you babysit.
- **No abandoned-repo rot.** Updates included (see FAQ). When Claude Code changes its subagent format or adds capabilities, the pack gets updated.

### What's inside (exact contents)

- **30 subagents** (`.claude/agents/*.md`) — full list below
- **10 skills** (`.claude/skills/*/SKILL.md`) — multi-step workflows like a full TDD loop and a structured PR review
- **8 hook recipes** (`settings.json` snippets with comments) — copy-paste automations:
  1. Auto-format on every file edit (Prettier/Black/gofmt, detected per repo)
  2. Block edits to protected paths (lockfiles, migrations, `.env*`)
  3. Secret-pattern guard before any file write
  4. Run affected tests after edits to source files
  5. Lint gate before `git commit` runs
  6. Session-start context injector (branch, recent commits, open TODOs)
  7. Command audit log (every Bash call appended to a local log)
  8. Long-task desktop notification
- **4 CLAUDE.md templates** — TypeScript app, Python service, monorepo, open-source library. Each one is short on purpose, with comments explaining *why* each line is there and what to delete.
- **README** with install instructions, a "which agent do I use for X" cheat sheet, and customization notes.

### Who it's for

- You already use Claude Code daily and you've felt the gap between "Claude with a good agent setup" and "Claude out of the box."
- You've started writing your own subagents, got two or three decent ones, and stalled — because writing the other 27 is real work.
- You lead a team and want everyone running the same agent setup instead of five people's homegrown variants.

### Who it's NOT for

- You haven't used Claude Code yet. Start with the free tool first; this pack assumes you know what a subagent is.
- You enjoy prompt engineering and have time for it. Honestly, you'll have fun building your own — and the free GitHub lists are good raw material.
- You're looking for agents that magically write whole features unattended. These are focused specialists with deliberate scope limits, not autopilot.

### Install in 60 seconds

```bash
# 1. Unzip into your repo (or ~/.claude for global install)
unzip power-pack.zip -d .claude/

# 2. Verify Claude Code sees the agents
claude
> /agents        # all 30 listed

# 3. Use one
> Use the code-reviewer subagent on my latest changes
```

That's it. No build step, no dependencies, no MCP servers required. Plain markdown and JSON, readable and editable — you own every line.

### What makes it different from free GitHub lists

Straight answer, since you're going to compare:

| | Free GitHub collections | Power Pack |
|---|---|---|
| Price | $0 | $12 launch / $19 |
| Count | Often 100+ | 30, deliberately |
| Structure | Varies per contributor | Identical skeleton across all 30 |
| Guardrails | Sometimes | Every agent, always |
| Tested against real repos | Unknown | Yes, and revised from output |
| Maintained | Depends on the repo | Updates included |
| Output formats | Freeform | Specified per agent, so results are consistent and parseable |

If $12 isn't worth skipping the evaluation, testing, and rewriting work — genuinely, use the free lists. Three of the pack's agents are published free as samples so you can judge the quality bar before paying a cent.

### Pricing & refund policy

- **$12 launch price** / **$19 regular**. (No countdown timers. The launch price ends when launch ends; the listing will say which price is current.)
- **30-day refund, no questions asked.** If the pack doesn't save you more than $12 of your time, email me and you get your money back. You don't have to explain anything.

---

## The 30 Agents

### DEV CORE (10)

- **code-reviewer** — Reviews diffs for correctness, security, and maintainability; severity-ranked findings, no style nitpicks your linter already catches. *(free sample)*
- **bug-hunter** — Reproduces, isolates, and root-causes a reported bug before proposing the minimal fix.
- **test-writer** — Writes tests that match your existing test conventions; targets behavior, not implementation details.
- **refactor-surgeon** — Executes scoped refactors with a verification step after every move; never mixes refactoring with behavior changes.
- **perf-profiler** — Measures before guessing; produces a baseline, identifies the hot path, proposes ranked optimizations.
- **security-auditor** — OWASP-aligned sweep: injection, authz gaps, secret handling, dependency risk; findings with evidence, not vibes.
- **api-designer** — Designs REST/RPC endpoints with consistent naming, versioning, pagination, and error envelopes; outputs an OpenAPI sketch.
- **migration-writer** — Writes reversible database migrations with explicit up/down paths and a data-safety checklist.
- **docs-writer** — Writes docs from the code that exists, not the code it imagines; flags undocumented behavior instead of inventing it.
- **dependency-auditor** — Audits the dependency tree for known CVEs, unmaintained packages, license conflicts, and trivially-replaceable deps.

### QUALITY (5)

- **type-tightener** — Eliminates `any`/loose types incrementally, strictest-wins, without breaking the build mid-pass.
- **dead-code-finder** — Finds unreachable code, unused exports, and orphaned files; verifies with references before recommending deletion.
- **error-message-improver** — Rewrites error messages to say what happened, why, and what to do next; preserves error codes and log parsers.
- **a11y-auditor** — Audits UI code against WCAG 2.1 AA: semantics, focus order, contrast, ARIA misuse; cites the criterion per finding.
- **i18n-extractor** — Extracts hardcoded strings into your i18n system, preserving interpolation and pluralization correctly.

### OPS (5)

- **ci-fixer** — Reads the actual CI logs, reproduces the failure locally when possible, fixes the cause — not the symptom.
- **release-notes-writer** — Turns commit history into human release notes grouped by impact: breaking, features, fixes; no commit-hash dumps.
- **dockerizer** — Writes multi-stage Dockerfiles with sensible layer caching, non-root users, and a `.dockerignore` that actually ignores.
- **incident-analyzer** — Builds a timeline from logs and commits, identifies contributing factors, drafts a blameless postmortem.
- **env-auditor** — Audits environment variable usage: undocumented vars, missing validation, secrets in the wrong place, drift between `.env.example` and reality.

### WORKFLOW (5)

- **pr-describer** — Generates PR titles and descriptions from the actual diff: what changed, why, how to review it, what to watch. *(free sample)*
- **issue-triager** — Labels, prioritizes, and routes issues; asks for missing repro info with a specific checklist instead of "needs more info."
- **spec-writer** — Turns a fuzzy feature request into a spec with scope, non-goals, edge cases, and open questions.
- **commit-splitter** — Splits a tangled working tree into clean, logically separate commits with accurate messages.
- **conflict-resolver** — Resolves merge conflicts by understanding both branches' intent; flags semantic conflicts that merge cleanly but break.

### META (5)

- **prompt-improver** — Rewrites your prompts and agent definitions using the same structure this pack uses; shows the before/after diff.
- **claude-md-auditor** — Audits your CLAUDE.md for staleness, contradictions, bloat, and rules Claude can't actually follow. *(free sample)*
- **repo-onboarder** — Produces a guided tour of an unfamiliar codebase: entry points, data flow, conventions, danger zones.
- **sql-analyst** — Writes and reviews SQL with an explain-plan habit; flags full scans, N+1 patterns, and lock hazards.
- **data-cleaner** — Profiles messy datasets, proposes cleaning rules explicitly before applying them, and logs every transformation.

## The 10 Skills

- **tdd-loop** — Red/green/refactor cycle with enforced test-first ordering and a stop condition.
- **pr-review** — Full PR review pass: diff analysis, test coverage check, security glance, summary comment draft.
- **security-sweep** — Repo-wide security pass combining security-auditor, dependency-auditor, and env-auditor into one report.
- **perf-baseline** — Establishes performance baselines (build time, test time, bundle size, key endpoints) and stores them for comparison.
- **release-flow** — Version bump, changelog, release notes, and tag checklist in the right order.
- **bug-hunt** — Structured debugging session: reproduce → isolate → root-cause → minimal fix → regression test.
- **codebase-tour** — Onboarding walkthrough for a new repo: architecture map, conventions, where things live.
- **api-contract-check** — Diffs implemented endpoints against the OpenAPI spec and reports drift in both directions.
- **refactor-plan** — Produces a stepwise refactor plan with verification gates before any code is touched.
- **daily-wrap** — End-of-day summary: what changed, what's in flight, what tomorrow-you needs to know.

---

## FAQ

**Does it work with my stack?**
The agents are language-agnostic by design — they read your repo's conventions instead of assuming a stack. They've been tested against TypeScript, Python, Go, and mixed monorepos. A few agents are inherently stack-flavored (type-tightener is most useful in typed languages; a11y-auditor assumes web UI), and the listing of each agent says so.

**Do I get updates?**
Yes. Updates to the pack are free for existing buyers — Gumroad emails you when a new version ships. When Claude Code changes the subagent format or adds capabilities worth using, the pack gets revised. That's a core part of what you're paying for versus a frozen GitHub snapshot.

**What's the license? Can I use it commercially?**
Use it in any project — personal, commercial, client work, your day job. Modify everything. The only restriction: don't redistribute or resell the pack itself (or lightly-reworded versions of it). One purchase covers one developer; for a whole team, buy a copy per dev or email me for a team rate.

**How is this different from free GitHub repos of agents?**
Three things: consistency (every agent uses the same role/process/output/guardrails structure, so they compose and you can edit any of them confidently), testing (each agent was run against real repos and revised based on its actual output), and maintenance (updates included; free lists rot when maintainers move on). If those three things aren't worth $12 to you, the free lists are genuinely fine — and three full agents from this pack are published free so you can compare quality directly.

**Do I need all 30 agents?**
No, and you shouldn't install all 30 into every repo — more agents means more for Claude to consider when delegating. The README includes a "starter set" recommendation (8 agents that cover most daily work) and per-project suggestions. Delete what you don't use; they're just markdown files.

**Does it work with Claude Code on web/desktop, or just the CLI?**
Subagents, skills, and CLAUDE.md files live in `.claude/` in your repo, so they work anywhere Claude Code reads your repo — CLI, VS Code extension, and web sessions that check out your repo. The 8 hook recipes go in `settings.json` and apply wherever your settings are loaded.

**What's the refund policy?**
30 days, no questions asked, via Gumroad. If it doesn't save you more than it cost, you shouldn't pay for it.

**What Claude Code version do I need?**
Any version with subagent support (`/agents` command). The pack uses plain markdown with standard YAML frontmatter — no undocumented features, nothing version-pinned. If a future Claude Code release changes the format, the pack gets updated (see updates question).

---

## Cover Image

**Primary text:** `30 subagents. 10 skills. 8 hooks. One consistent structure.`
**Secondary text:** `A drop-in .claude/ pack for Claude Code`
**Visual direction:** Dark terminal aesthetic. A rendered file tree of `.claude/agents/` showing real agent filenames (code-reviewer.md, bug-hunter.md, test-writer.md…) with one file open beside it showing the YAML frontmatter and the five section headers. Monospace type, no stock-photo robots, no glowing brains.

## 5 Product Screenshots to Take

1. **The file tree.** `tree .claude/` output in a terminal showing all 30 agents, 10 skill folders, and the hooks/templates directories — proves the exact contents at a glance.
2. **One full agent, annotated.** The code-reviewer agent open in an editor with callout arrows labeling the five sections: role, when invoked, process, output format, guardrails. This is the "every agent looks like this" proof.
3. **An agent in action.** A real Claude Code session: user asks for a review, code-reviewer subagent produces the severity-ranked findings table on actual code. Crop to show the structured output format.
4. **Side-by-side consistency shot.** Three agents (one from DEV CORE, one from OPS, one from META) open in split panes, showing identical section structure across totally different domains.
5. **The 60-second install.** Terminal recording still: `unzip`, then `/agents` inside Claude Code listing all 30 — timestamped prompt lines showing the whole thing took under a minute.
