---
name: delegate-claude
description: Delegate work to a local Claude CLI so token usage and rate-limit pressure can be shifted off the current lane.
allowed-tools: Bash(claude *)
disable-model-invocation: true
---

# Delegate Claude

Use the local `claude` CLI as a delegated execution lane.

## What this skill should do

1. Restate the user's request into a compact Claude prompt.
2. Hand the work off to Claude in non-interactive mode.
3. Return the result with a short note about which model or flags were used.
4. Highlight disagreements, blind spots, or useful alternative paths.

## Default command

```bash
claude -p "$ARGUMENTS"
```

## Good prompts

- Review this diff for correctness, edge cases, and maintainability.
- Propose a smaller implementation for this feature.
- Find likely causes of this failing test.
- Give a second lane on this migration plan.

## Notes

- Prefer `--model` only when there is a clear reason.
- Keep prompts concrete and include code or context when available.
- If Claude CLI is missing, explain that `claude` must be installed and authenticated first.
