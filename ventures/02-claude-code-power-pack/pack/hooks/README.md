# Hook Recipes

Hooks are shell commands that Claude Code runs automatically at lifecycle events — before/after tool calls, at session start, when Claude finishes a turn. They are the difference between *asking* Claude to always run the formatter and *guaranteeing* it happens.

Unlike agents and skills, hooks are **not** drop-in: they execute shell commands on your machine, so each recipe in [`snippets.md`](snippets.md) is meant to be read, understood, and then pasted into your settings.

## Where hooks live

| File | Scope |
|---|---|
| `.claude/settings.json` | project (shared if committed) |
| `.claude/settings.local.json` | project, just you (gitignored) |
| `~/.claude/settings.json` | all your projects |

## Anatomy of a hook

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          { "type": "command", "command": "your-shell-command-here" }
        ]
      }
    ]
  }
}
```

- **Event** (`PostToolUse` above): when it fires. The recipes use:
  - `PreToolUse` — before a tool runs; exit code 2 **blocks** the tool call (stderr is fed back to Claude)
  - `PostToolUse` — after a tool succeeds
  - `SessionStart` — when a session begins; stdout is added to Claude's context
  - `UserPromptSubmit` — when you submit a prompt; stdout is added to context
  - `Stop` — when Claude finishes responding
- **matcher**: regex matched against the tool name (`Edit|Write`, `Bash`, empty = all tools). Only applies to `PreToolUse`/`PostToolUse`.
- **command**: runs with your shell. Hook input arrives as JSON on **stdin** (tool name, arguments, file paths, etc.) — the recipes use `jq` to read it.

## Merging recipes

`settings.json` is a single JSON document — if you adopt several recipes, merge their entries into **one** `"hooks"` object, appending to each event's array. Recipe 1 + Recipe 3 for example:

```json
{
  "hooks": {
    "PostToolUse": [ { "...recipe 1 entry..." : "" } ],
    "PreToolUse":  [ { "...recipe 3 entry..." : "" } ]
  }
}
```

(Snippets show each recipe standalone for clarity.)

## Requirements & portability

- Recipes are written for **macOS/Linux** (bash + `jq`). On Windows, use WSL or rewrite the one-liners in PowerShell.
- `jq` is required by most recipes: `brew install jq` / `apt install jq`.
- Test any command **standalone in a terminal first**, with a sample JSON piped to stdin, before wiring it into settings. A hook that errors on every tool call is a miserable debugging session.

## Safety notes

- Hooks run with your user's permissions, automatically, every time the event fires. Keep them fast (<2s) and side-effect-light.
- Blocking hooks (`PreToolUse` + exit 2) are powerful: start them in "warn" mode (exit 0, just echo) for a day before flipping to enforcement.
- Never put secrets in hook commands — settings files get committed more often than people intend.
