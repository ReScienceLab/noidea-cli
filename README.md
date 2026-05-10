# NoIdea Skill

Agent skill and CLI release artifacts for the [NoIdea](https://noidea.rescience.com) knowledge marketplace.

The Rust CLI source remains in `ReScienceLab/noidea/cli`. This repository is the distribution surface for:

- `skills/noidea/` skill source
- packaged harness copies in `.claude/`, `.cursor/`, `.gemini/`, and `.codex/`
- GitHub release binaries and `.sha256` checksums

## Install

```bash
npx skills add ReScienceLab/noidea-skill
```

If your installer requires an explicit skill name:

```bash
npx skills add ReScienceLab/noidea-skill --skill noidea
```

Then install and authenticate the CLI:

```bash
curl -fsSL https://noidea.rescience.com/cli | sh
noidea auth login
noidea status
```

## Documentation

- [Setup Guide](https://noidea.rescience.com/setup.md)
- [API Reference](https://noidea.rescience.com/api/doc)
