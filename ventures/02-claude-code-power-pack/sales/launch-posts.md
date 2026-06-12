# Launch Posts — Claude Code Power Pack

Honest "I built this" framing throughout. Post as yourself, answer every comment, never argue with criticism — thank it and move on. Suggested order: Day 1 Reddit + X, Day 2 Dev.to, Day 3 Show HN.

---

## (a) X/Twitter thread (7 tweets)

**1/**
I got tired of writing the same Claude Code subagent prompts from scratch in every project.

So I wrote 30 of them properly — once — plus 10 skills, 8 hook recipes, and 4 CLAUDE.md templates.

Drop-in `.claude/` install. Here's what's inside 🧵

**2/**
The problem with most agent prompts (mine included, for months): they're vibes.

"You are an expert code reviewer. Review the code."

That gets you generic output. A useful agent needs: a process, an output format, and guardrails — what it must NOT do.

**3/**
Every agent in the pack follows the same 5-part structure:

- role (specific + opinionated)
- when invoked
- process (numbered steps w/ real heuristics)
- output format
- guardrails

30 agents, identical skeleton, predictable behavior.

**4/**
Example — code-reviewer's guardrails:

- zero style nits (a linter exists, stay in your lane)
- severity tags on every finding (CRITICAL→LOW)
- flag, don't fix, unless asked
- max signal: if it wouldn't change a merge decision, don't say it

That last rule alone fixed my review noise problem.

**5/**
What's in the pack:

🔧 30 agents — dev core, quality, ops, workflow, meta
⚡ 10 skills — tdd-loop, security-sweep, bug-hunt, refactor-plan...
🪝 8 hook recipes — auto-format, protected paths, dangerous-command guard
📄 4 CLAUDE.md templates — web app, API, monorepo, library

**6/**
Honest note: free agent collections exist on GitHub, and some are good. I link a few in the listing.

What you're paying for is curation + consistency: one structure, tested patterns, no abandoned-repo rot, quarterly updates pushed to buyers.

**7/**
$12 launch price (goes to $19 in two weeks).

30-day refund, no questions — if it doesn't save you an hour, get your money back.

→ [GUMROAD LINK]

---

## (b) Reddit post — r/ClaudeAI

**Title:** I wrote 30 Claude Code subagents with a consistent structure (process + output format + guardrails). Sharing 3 of them free here.

**Body:**

After months of accumulating half-baked agent prompts across projects, I sat down and wrote a proper set: 30 subagents, 10 skills, 8 hook recipes, 4 CLAUDE.md templates, all following the same 5-part structure — role, when invoked, process, output format, guardrails.

The structure matters more than the prompts themselves, honestly. "You are an expert reviewer" gets you horoscope output. A numbered process with real heuristics and explicit guardrails ("zero style nits — a linter exists") gets you something you'd actually paste into a PR.

**Transparency up front: the full pack is paid ($12).** But to make this post worth your time regardless, here are 3 complete agents from it — copy them into `.claude/agents/` and they're yours, no strings:

[PASTE THE 3 AGENTS FROM free-samples.md — full files, code blocks]

A few things I learned writing 30 of these, free to steal:

1. The `description` field is your auto-delegation trigger. Write it as "Use when/after X" — vague descriptions never fire.
2. Restrict `tools:` per agent. A reviewer with read-only tools can't "helpfully" rewrite your code.
3. Guardrails sections do more work than role sections. Agents fail by doing too much, not too little.

If the free three are useful and you want the other 27 + skills + hooks + templates: [GUMROAD LINK]. 30-day refund, no questions. Happy to answer anything about the structure either way.

---

## (c) Hacker News — Show HN

**Title:** Show HN: 30 Claude Code subagents with a consistent prompt structure ($12)

**First comment (post immediately after submitting):**

Author here. Quick honest pitch and some context.

What it is: 30 subagent definitions for Claude Code (plus 10 skills, 8 hook recipes, 4 CLAUDE.md templates), each following the same structure: role, trigger description, numbered process with concrete heuristics, output format, and guardrails (what the agent must NOT do).

Free alternatives exist — there are several good GitHub collections (awesome-claude-code lists most of them), and honestly, if you enjoy writing and maintaining these yourself, you don't need this. What I'm selling is the part I found tedious: consistency across all 30 (same skeleton, predictable output), minimal tool allowlists per agent, and the guardrails sections, which in my experience are where agent prompts actually succeed or fail.

Three full agents are free in the Reddit launch post if you want to judge the quality before paying: [LINK].

Things I'm unsure about and would genuinely take feedback on: whether per-agent model pinning (haiku for mechanical agents, opus for security review) should ship as defaults or stay documented-but-off; and whether 30 is too many — there's an argument the right number is 8.

$12, 30-day no-questions refund.

---

## (d) Dev.to article

**Title:** I wrote 30 Claude Code subagents so you don't have to: what I learned about agent prompt structure

**Intro paragraph (written out):**

Six months ago my `.claude/agents/` directory was a junk drawer: fourteen files, three naming conventions, prompts ranging from two lines ("review this code carefully") to a 400-line monster nobody could maintain. Some triggered automatically, most didn't, and I couldn't tell you why. So I did the thing: deleted everything and rewrote the whole set from scratch with one rule — every agent gets the exact same skeleton. Thirty agents later, I have opinions. This article is the structure that emerged, the mistakes that forced it, and three complete agents you can copy right now.

**Outline:**

1. **The junk drawer problem** — why agent prompts rot; inconsistency tax; the auto-delegation lottery.
2. **The 5-part skeleton** — role / when invoked / process / output format / guardrails; why this order; full annotated example (code-reviewer, complete file inline).
3. **Descriptions are triggers, not documentation** — how Claude decides to delegate; "Use when/after X" phrasing; before/after examples of descriptions that never fire vs always fire.
4. **Guardrails do the heavy lifting** — agents fail by overreaching; "flag, don't fix"; "zero style nits"; tool allowlists as enforced guardrails (read-only reviewers).
5. **Processes need heuristics, not platitudes** — "check for security issues" vs an actual checklist; the test: could a junior dev follow this step mechanically?
6. **What I'd skip next time** — agents that overlap; when a skill is better than an agent; the case for fewer, sharper agents.
7. **Steal these three** — pr-describer and claude-md-auditor complete, inline (third is in the Reddit post).
8. **The other 27** — one paragraph, transparent: pack exists, $12, refund policy, link. No hard sell.

---

## (e) 5 follow-up post ideas (weeks after launch)

1. **"The 5 hooks I won't work without"** — X thread / dev.to short. Walk through auto-format, protected paths, dangerous-command guard with the actual JSON. Links pack at the end.
2. **"Your CLAUDE.md is too long"** — opinion post on the index-not-encyclopedia principle, using the monorepo template as the example. Reliably starts discussion.
3. **Buyer-feedback update post** — "Shipped pack v1.1: what 50 buyers asked for" (new agent, fixes). Gumroad pushes updates to past buyers free — say so; it converts fence-sitters.
4. **"Agent teams vs subagents: when to use which"** — educational, zero selling, builds authority in the exact audience. Pack link in bio only.
5. **Price-change announcement** — the honest version: "Launch price ends Friday, $12 → $19. No fake countdown, just the plan from day one." Post once on X, once on Reddit profile.
