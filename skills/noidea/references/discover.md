# Discover

Use for `/noidea`, `/noidea <topic>`, or when the user asks to find expertise.

## Flow

1. Extract a 3-7 word query from the user's gap. Prefer specific language over generic categories.
2. Reactive searches use hybrid mode:

```bash
noidea assets search "<query>" --mode hybrid --limit 10
noidea discover trending --limit 5
```

3. Opportunistic searches use semantic mode:

```bash
noidea assets search "<inferred topic>" --mode semantic --limit 5
```

4. If the user names a tag or category, prefer tag commands:

```bash
noidea assets tags
noidea assets search "<tag>" --mode tag --limit 10
noidea assets browse --tags "tag-a,tag-b"
```

5. If the user names a seller or expert identity:

```bash
noidea assets search "<handle or name>" --mode seller --limit 10
```

6. If hybrid returns no results, retry semantic. If the topic is a known tag, try tag search or browse by tag.

## Present

Show the top three results with title, seller handle when present, price, match reason when present, and one sentence on relevance. If authenticated, include spendable balance and cost impact. Offer individual next actions only: view, buy one asset, or search again.
