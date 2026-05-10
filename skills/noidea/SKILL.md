---
name: noidea
description: >
  Knowledge marketplace skill for noidea.rescience.com. Invoke when the user
  is stuck, has a knowledge gap, needs research on a topic, wants to discover
  or purchase knowledge assets, wants to read purchased content, or wants to
  publish insights from this conversation as a marketplace asset. Trigger
  words: /noidea, no idea, discover assets, buy asset, publish insight, read
  asset, knowledge gap, can't find information, find expertise.
---

# NoIdea

Use the `noidea` CLI as the local marketplace control plane. The user normally
talks to you, and you run CLI commands only when useful.

## Route

- No argument or a topic: read `references/discover.md`.
- `buy <id>`: read `references/buy.md`.
- `read <id>`: read `references/read.md`.
- `publish` or `publish @<file>`: read `references/publish.md`.
- `seller`: read `references/seller.md`.
- `status`: run `noidea status`, `noidea wallet balance`, `noidea purchases list`, then count `.noidea/assets/*.md` in the project.
- Opportunistic discovery: read `references/proactive.md`.

## Principles

1. Infer the real knowledge gap before searching.
2. Convex is authoritative. `.noidea/assets/` is only a project cache and `.noidea/drafts/` is only a working copy.
3. Before writing paid content or drafts, create `.noidea/.gitignore` with `assets/` and `drafts/`, then verify the target is ignored when inside a git repo.
4. Show preview, link, price, wallet impact, and confirmation before purchase.
5. Use `--expected-price-cents` when buying. Never buy multiple assets automatically.
6. Publish flow is draft, human review, re-sync from local file, submit for review.
7. Use TOON output by default. Use `--json` only when strict parsing is required.
8. Do not use Nora runtime control-plane commands for this skill; use marketplace metadata and your judgment.
