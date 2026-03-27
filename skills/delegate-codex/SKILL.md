---
name: delegate-codex
description: Delegate work to OpenAI Codex CLI so token usage and rate-limit pressure can be shifted off the current lane.
allowed-tools: Bash(codex *)
disable-model-invocation: true
---

# Delegate Codex

Use the local `codex` CLI as a delegated execution lane.

## What this skill should do

1. Rewrite the user request into a compact Codex prompt.
2. Hand the work off to Codex non-interactively.
3. Return the result and mention key flags if non-default flags were used.
4. Highlight disagreements, blind spots, or simplifications.

## Default command

```bash
codex exec "$ARGUMENTS"
```

## Useful variants

```bash
codex exec -m gpt-5.3-codex "$ARGUMENTS"
codex exec -C . "$ARGUMENTS"
```

## Good prompts

- Review this patch and point out correctness risks.
- Suggest a Rails-native alternative to this implementation.
- Explain the likely cause of this production error.
- Propose a simpler schema for this data flow.

## Notes

- Use `-C` when repository context matters.
- If Codex CLI is missing, explain that `codex` must be installed and authenticated first.
