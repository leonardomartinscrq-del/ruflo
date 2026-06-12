---
name: daily-wrap
description: End-of-session wrap-up - capture what changed (files/commits), decisions made and why, open questions, and the next three concrete steps, written to a dated notes file so the next session can resume cold. Use at the end of a work session or when asked to summarize and save progress.
---

Close the session with a written state dump good enough that a brand-new session — with zero conversation memory — can resume the work in minutes. The wrap records facts from git (not recollection), the reasoning behind decisions (the part git cannot tell you), and next steps concrete enough to execute verbatim.

## Steps

1. Gather what changed from the source of truth: run `git status --porcelain` (uncommitted work), `git diff --stat` (unstaged scope), and `git log --oneline -15` plus the current branch and SHA (`git rev-parse --abbrev-ref HEAD; git rev-parse --short HEAD`). If a previous wrap file recorded a session-end SHA, log only commits since it: `git log <prev-sha>..HEAD --oneline`.
2. Read the most recent file in `notes/` matching `wrap-*.md` (if any) and carry forward its still-open questions and undone next steps — items resolved this session get marked done, not silently dropped.
3. Reconstruct decisions made this session from the conversation: for each, record WHAT was decided, WHY (the constraint or evidence that drove it), and what alternative was rejected. This is the highest-value section — code shows the what; only the wrap preserves the why.
4. List open questions and known issues: anything uncertain, blocked, failing, or deliberately deferred — including failing tests left red and TODOs introduced.
5. Write the next 3 concrete steps. Each must be executable by a cold session without asking anything: include file paths, function names, and exact commands. "Continue the refactor" fails this test; "Extract validation from `src/api/users.ts:142-180` into `src/validation/user.ts`, then run `npm test -- users`" passes.
6. Write the file to `notes/wrap-YYYY-MM-DD.md` using today's date (`mkdir -p notes` first; if today's file already exists, append a `## Session 2 (HH:MM)` section instead of overwriting). Structure:
   - `## State` — branch, SHA, dirty/clean, commits this session
   - `## Changed` — files/commits with one-line whys
   - `## Decisions` — what / why / rejected alternative
   - `## Open questions`
   - `## Next steps` — the 3 concrete items, numbered
7. If `notes/` is not in version control and the repo has a `.gitignore` policy against it, leave it as-is; do not commit anything — this skill only writes the file.
8. Echo a compact version of the wrap (State + Next steps) back to the user so the session ends with shared understanding.

## Output

- `notes/wrap-YYYY-MM-DD.md` with the five sections above.
- An inline summary to the user: current branch/SHA, one-line per decision, and the 3 next steps.

## Rules

- Facts about changes come from git commands run now, never from memory of the conversation.
- Always record branch + SHA so the next session can `git diff` from the exact resume point.
- Each next step must name files/commands explicitly — the cold-start test is binding.
- Never include secrets, tokens, or credential values in the wrap file.
- Append on same-day reruns; never destroy an earlier wrap.
- No git commits, no pushes — writing the notes file is this skill's only side effect.
