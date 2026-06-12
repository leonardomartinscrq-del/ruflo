---
name: security-sweep
description: Repo-wide security scan - secrets patterns, injection surfaces (SQL/shell/path/template), missing authz on routes, dependency audit, and unsafe deserialization, producing a prioritized findings report. Use when asked for a security audit, before a release, or after inheriting an unfamiliar codebase.
---

Sweep the entire repository for the vulnerability classes that actually get codebases breached: leaked credentials, injection, missing authorization, vulnerable dependencies, and unsafe deserialization. Every grep hit is verified by reading its surrounding code before it becomes a finding — a report full of false positives is worthless.

## Steps

1. Scope the target: detect languages and frameworks (manifests, lockfiles, route files) and list configuration surfaces (`.env*`, `*.yml`, `*.json`, `*.toml`, CI files, Dockerfiles). Note what is test/fixture/example territory so hits there can be down-ranked.
2. Secrets scan — grep the tree for high-signal patterns:
   - Generic: `(api[_-]?key|secret|token|password|passwd|credential)\s*[:=]\s*['"][^'"]{8,}`
   - AWS: `AKIA[0-9A-Z]{16}` ; GitHub: `ghp_[A-Za-z0-9]{36}` and `github_pat_` ; Slack: `xox[baprs]-` ; Stripe: `sk_live_` ; JWTs: `eyJ[A-Za-z0-9_-]{10,}\.`
   - Key material: `-----BEGIN (RSA |EC |OPENSSH )?PRIVATE KEY`
   - Connection strings: `(postgres|mysql|mongodb(\+srv)?|redis|amqp)://[^/\s:]+:[^@\s]+@`
   Then check hygiene: is `.env` listed in `.gitignore`? Do `git log --oneline --all -- '*.env*' '*credentials*' '*secret*'` hits suggest secrets were ever committed (history hint — flag for rotation even if since deleted)?
3. Injection surfaces — grep and then READ each hit to confirm user input can reach it:
   - SQL: string-built queries (`f"SELECT`, `"SELECT " +`, template literals or `%` formatting into `execute`/`query`) versus parameterized calls.
   - Shell: `child_process.exec(`, `os.system(`, `subprocess.*shell=True`, backticks/`system(` — flag any with interpolated variables.
   - Path: user input flowing into `open()`, `fs.readFile`, `path.join`/`os.path.join` without normalization plus prefix check (`..` traversal).
   - Template/code: `render_template_string`, `eval(`, `new Function(`, `exec(`, `vm.runInContext` with non-literal arguments.
4. Authorization on routes: enumerate route registrations (Express `(app|router)\.(get|post|put|patch|delete)`, FastAPI/Flask decorators, Spring `@*Mapping`, Rails `routes.rb`). For every state-mutating route (POST/PUT/PATCH/DELETE), verify an auth middleware/decorator/guard is applied at the route or its mount point. Also flag object-level authz gaps: handlers fetching records by client-supplied ID without an ownership/tenant check (IDOR).
5. Dependency audit: run the native auditor (`npm audit --omit=dev`, `pip-audit`, `cargo audit`, `govulncheck ./...` — whichever applies). Record critical/high advisories with the vulnerable package, installed version, and fixed version.
6. Unsafe deserialization: `pickle.loads`, `yaml.load(` without `SafeLoader`/`safe_load`, `Marshal.load`, Java `ObjectInputStream.readObject`, and deep-merge of parsed JSON into objects (prototype pollution: merges touching `__proto__`/`constructor`).
7. Verify and triage: open each candidate, confirm untrusted data can actually reach the sink, then classify — Critical (exploitable now: live secret, unauth mutating route, injection from request data), High (exploitable with conditions), Medium (defense-in-depth gap), Low (hardening/hygiene). Discard or footnote hits confined to tests, fixtures, and docs examples.

## Output

A prioritized findings report containing:
- Summary line: counts per severity.
- Findings table: severity | class (secret/injection/authz/dependency/deserialization) | file:line | evidence (masked) | concrete remediation.
- Rotation list: any credential that ever touched the repo or its history.
- Dependency advisories with upgrade targets.
- Explicit "scanned but clean" list of the classes checked, so coverage is auditable.

## Rules

- NEVER print full secret values — mask to last 4 characters in all output.
- Every reported finding must be confirmed by reading the code around the hit; raw grep matches are candidates, not findings.
- A secret found anywhere in git history is compromised: remediation is rotate, not just delete.
- Do not modify code, rotate keys, or upgrade dependencies during the sweep unless explicitly asked — report first.
- If a class cannot be checked (e.g. no auditor available offline), say so explicitly rather than implying it passed.
