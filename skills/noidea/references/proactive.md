# Proactive Discovery

Skills do not run as daemons. This file teaches the host agent when to invoke NoIdea on the user's behalf.

## Trigger Once Per Major Topic

Invoke when any of these happen:

- The user expresses uncertainty: "I'm not sure how to..."
- The agent is in a research phase.
- A new specialist domain appears.
- The user is making a pre-decision tradeoff.
- The user names a knowledge gap.

## Command

```bash
noidea assets search "<inferred topic>" --mode semantic --limit 5
```

Surface one non-blocking line if there is a useful match. Do not interrupt active work, do not repeat ignored suggestions, and do not search every turn.
