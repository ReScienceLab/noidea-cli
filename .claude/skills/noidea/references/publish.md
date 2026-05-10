# Publish

Publishing is seller-only and must be resumable. Never publish without explicit human confirmation after local review.

## Seller Gate

```bash
noidea status
```

If `isSeller` is false, send the user to `<web_url>/become-seller` and stop until they confirm completion.

## Draft File

Drafts live in `.noidea/drafts/<slug>.md` with YAML frontmatter:

```markdown
---
noidea_draft_id: ""
title: "Title"
summary: "Short summary."
tags: ["tag"]
price_cents: 1800
api_url: "https://calculating-weasel-388.convex.site"
synced_at: ""
sync_status: "pending_review"
---

Body content.
```

Frontmatter is local state only. The CLI strips it before upload when using `--body @file` or `--body-stdin`.

Before writing drafts, create `.noidea/.gitignore` with `assets/` and `drafts/`, then verify the draft path is ignored inside git.

## New Draft Flow

1. Assess whether the conversation contains a reusable, non-obvious practitioner insight worth paying for. If not, say so and stop.
2. Fetch tags:

```bash
noidea assets tags
```

3. Write `.noidea/drafts/<slug>.md`. Slug is title lowercased with spaces replaced by hyphens; append `-2`, `-3`, etc. on collision.
4. Save draft:

```bash
noidea assets draft save --body @.noidea/drafts/<slug>.md --title "..." --summary "..." --tags "tag-a,tag-b" --price <cents>
```

5. Update frontmatter with `noidea_draft_id`, `synced_at`, and `sync_status: pending_review`.
6. Tell the user to edit the file in their IDE and say "publish" when ready. Stop.

## Resume Flow

Scan `.noidea/drafts/*.md` for `noidea_draft_id`.

- `pending_review`: ask whether to resume that draft. On "publish", re-sync first.
- `synced`: on explicit confirmation, re-sync again before publishing.
- `published`: keep for reference; do not publish again.

## Re-sync And Publish

Always re-sync from the edited file immediately before publishing:

```bash
noidea assets draft save --id <draft_id> --body @.noidea/drafts/<slug>.md --title "..." --summary "..." --tags "tag-a,tag-b" --price <cents>
noidea assets draft publish <draft_id>
```

After publish, update frontmatter `sync_status: published` and show the asset URL.

