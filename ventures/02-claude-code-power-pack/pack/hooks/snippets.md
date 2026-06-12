# 8 Hook Recipes (copy-paste)

Each recipe is standalone JSON for `.claude/settings.json`. Merge the ones you adopt (see README). All recipes: macOS/Linux, require `jq` unless noted.

---

## 1. Auto-format on edit

Runs your formatter on every file Claude edits or writes — no more "please also run prettier". Auto-detects the right formatter by extension.

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "f=$(jq -r '.tool_input.file_path // empty'); case \"$f\" in *.ts|*.tsx|*.js|*.jsx|*.json|*.css|*.md) npx prettier --write \"$f\" >/dev/null 2>&1 ;; *.py) black -q \"$f\" 2>/dev/null ;; *.go) gofmt -w \"$f\" 2>/dev/null ;; *.rs) rustfmt \"$f\" 2>/dev/null ;; esac; exit 0"
          }
        ]
      }
    ]
  }
}
```

Note the `exit 0`: formatting failure should never fail the edit.

---

## 2. Protect sensitive paths (blocking)

Blocks Claude from editing files that should never be touched casually: env files, lockfiles, applied migrations, prod configs. Exit code 2 blocks the tool and tells Claude why.

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "f=$(jq -r '.tool_input.file_path // empty'); case \"$f\" in *.env|*.env.*|*package-lock.json|*pnpm-lock.yaml|*/migrations/*|*prod*.config.*) echo \"BLOCKED: $f is protected by hook policy. Ask the user to change it manually.\" >&2; exit 2 ;; esac; exit 0"
          }
        ]
      }
    ]
  }
}
```

Adjust the `case` patterns to your repo. Start in warn mode by changing `exit 2` to `exit 0` for a day.

---

## 3. Command logger

Appends every Bash command Claude runs to a local audit log. Cheap insurance and great for retracing sessions.

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "jq -r '\"[\" + (now | strftime(\"%Y-%m-%d %H:%M:%S\")) + \"] \" + (.tool_input.command // \"\")' >> ~/.claude/bash-audit.log; exit 0"
          }
        ]
      }
    ]
  }
}
```

---

## 4. Test-on-save for source edits

Runs the test suite (quietly, fast subset recommended) after Claude edits source files, and feeds failures straight back into context.

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "f=$(jq -r '.tool_input.file_path // empty'); case \"$f\" in */src/*) npm test --silent -- --bail 2>&1 | tail -20 ;; esac; exit 0"
          }
        ]
      }
    ]
  }
}
```

Swap `npm test` for your runner (`pytest -x -q`, `go test ./...`, `cargo test -q`). Keep it under a few seconds or scope it to the changed package — a slow hook taxes every single edit.

---

## 5. Session-start context loader

Injects git status and recent history into Claude's context at the start of every session — Claude begins already oriented instead of spending its first tool calls on `git status`.

```json
{
  "hooks": {
    "SessionStart": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "echo '== branch =='; git branch --show-current 2>/dev/null; echo '== status =='; git status --short 2>/dev/null | head -20; echo '== last 5 commits =='; git log --oneline -5 2>/dev/null"
          }
        ]
      }
    ]
  }
}
```

(No `jq` needed.) Stdout from `SessionStart` hooks is added to context automatically.

---

## 6. Stop-hook TODO reminder

When Claude finishes a turn, scans files changed in the working tree for fresh `TODO`/`FIXME` markers and surfaces them — catches the "I'll note this as a TODO" that would otherwise ship.

```json
{
  "hooks": {
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "git diff --name-only HEAD 2>/dev/null | xargs -r grep -n 'TODO\\|FIXME' 2>/dev/null | head -10"
          }
        ]
      }
    ]
  }
}
```

---

## 7. Dangerous-command guard (blocking)

Blocks the categories of shell command you never want run without a human: recursive force deletes, force pushes, hard resets, curl-pipe-to-shell.

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "c=$(jq -r '.tool_input.command // empty'); echo \"$c\" | grep -qE 'rm -rf /|rm -rf ~|git push.*--force|git reset --hard|curl[^|]*\\|\\s*(ba)?sh|chmod -R 777' && { echo \"BLOCKED by dangerous-command guard: $c\" >&2; exit 2; }; exit 0"
          }
        ]
      }
    ]
  }
}
```

This is a tripwire, not a sandbox — it catches the common footguns, not a determined adversary. Tune the regex to your fears.

---

## 8. Long-task completion notification

Desktop notification when Claude finishes a turn — for the "kick off a big refactor, go make coffee" workflow.

**macOS:**

```json
{
  "hooks": {
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "osascript -e 'display notification \"Claude finished\" with title \"Claude Code\" sound name \"Glass\"'"
          }
        ]
      }
    ]
  }
}
```

**Linux (libnotify):**

```json
{
  "hooks": {
    "Stop": [
      {
        "hooks": [
          { "type": "command", "command": "notify-send 'Claude Code' 'Claude finished'" }
        ]
      }
    ]
  }
}
```
