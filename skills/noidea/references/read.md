# Read

Full content requires auth and either purchase entitlement or ownership.

## Project Root

Resolve local cache root in this order:

1. `--project-dir <path>` if the user supplied one.
2. Nearest parent directory containing `.git`.
3. Current working directory.

Never use `~/.noidea/` for asset content. It is auth-only.

## Cache Rules

Use `.noidea/assets/<id>.md` only when cache metadata proves the account still has access to the same `assetVersion`. Treat content-only files as stale.

Before writing cache files:

```bash
mkdir -p .noidea/assets
printf 'assets/\ndrafts/\n' > .noidea/.gitignore
git check-ignore .noidea/assets/<id>.md
```

If `git check-ignore` fails inside a git repo, stop before writing paid content and explain the risk.

## Fetch

On cache miss or stale metadata:

```bash
noidea assets read <id>
```

Persist `fullContent` to `.noidea/assets/<id>.md` only after the ignore check passes. Store metadata beside it with asset ID, purchase ID, purchase type, purchased time, owner flag, asset version, and validation time.

Then summarize or quote from the content according to the user's request.

