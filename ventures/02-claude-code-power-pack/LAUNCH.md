# LAUNCH — Claude Code Power Pack (Gumroad)

> Your total time: **60–90 min once**, then ~15 min/week.
> Everything in `pack/` and `sales/` is ready — you package, upload, and post.

## Funnel

```
Reddit / X / HN / Dev.to posts (ready in sales/launch-posts.md)
        │ free samples as quality proof (sales/free-samples.md)
        ▼
Gumroad product page ($12 launch → $19 regular) ──→ instant zip delivery
```

Gumroad handles payment, VAT, delivery, refunds. Zero infrastructure.

## STEP 1 — Package the product (10 min)

```bash
cd ventures/02-claude-code-power-pack
zip -r claude-code-power-pack.zip pack/
```

Sanity-check the zip: it must contain `README.md`, `INSTALL.md`, `agents/` (30 files),
`skills/` (10 dirs), `hooks/`, `claude-md-templates/` (4 files).

## STEP 2 — Gumroad listing (30 min)

1. Create account at https://gumroad.com (email + payout method; Brazilians: Gumroad
   pays out via direct deposit/Payoneer — check current payout options for BR).
2. New product → type **Digital product** → upload the zip.
3. Copy title, subtitle, description, FAQ from `sales/gumroad-listing.md`.
4. Price: **$12** with "launch price" framing (raise to $19 after ~2 weeks — real
   change, announce it in posts). Enable "Pay what you want" floor $12 if you like.
5. Cover image: follow the cover spec at the bottom of `gumroad-listing.md`
   (make it in Canva in 10 min, or ask Claude via the Canva MCP).
6. Enable Gumroad **Discover** (their marketplace) — free extra distribution.

## STEP 3 — Launch posts (30 min, spread over 3 days)

All content is in `sales/launch-posts.md`. Suggested order:

| Day | Channel | Asset |
|-----|---------|-------|
| 1 | Reddit r/ClaudeAI | Reddit post (includes 3 free sample agents inline — this is the credibility play) |
| 1 | X/Twitter | Thread |
| 2 | Dev.to | Article ("I wrote 30 Claude Code subagents...") — real value, link at the end |
| 3 | Hacker News | Show HN (use the prepared first comment; HN hates salesmanship, the copy accounts for that) |

Rules: post as yourself, answer every comment honestly, never argue. If a post
flops, that's normal — the Dev.to article keeps pulling SEO traffic for months.

## STEP 4 — Maintenance loop (15 min/week)

- Answer Gumroad customer questions (paste them into Claude with this repo open).
- Once a month: post one item from the "follow-up post ideas" list.
- Once a quarter: open a Claude Code session in this repo and ask for a pack update
  pass (Claude Code ships new features; updating the pack = free "v2" announcement,
  and Gumroad pushes updates to past buyers — good will + reviews).

## Honest expectations

Dev impulse products at $12 typically do a burst at launch (anywhere from 3 to 100+
sales depending on post traction) then a long tail via Gumroad Discover and the
Dev.to article. Zero is possible. Marginal cost is zero; every sale is margin.

## Checklist

- [ ] zip built and verified
- [ ] Gumroad account + payout configured
- [ ] Product live at $12 with full listing copy
- [ ] Discover enabled
- [ ] Day 1: Reddit + X posts
- [ ] Day 2: Dev.to article
- [ ] Day 3: Show HN
- [ ] Weekly 15-min loop scheduled
