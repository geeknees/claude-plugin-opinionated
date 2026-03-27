---
name: delegate-gemini
description: Delegate work to Google Gemini CLI so token usage and rate-limit pressure can be shifted off the current lane.
allowed-tools: Bash(gemini *)
disable-model-invocation: true
---

# Delegate Gemini

Use the local `gemini` CLI as a delegated execution lane.

## What this skill should do

1. Turn the request into a concise Gemini prompt.
2. Hand the work off to Gemini in non-interactive mode.
3. Return the output and mention the model when explicitly set.
4. Pull out the most actionable recommendations.

## Default command

```bash
gemini -p "$ARGUMENTS"
```

## Useful variants

```bash
gemini -p -m gemini-2.5-pro "$ARGUMENTS"
gemini --resume latest -p "$ARGUMENTS"
```

## Good prompts

- Give another lane on this refactor.
- Review this design doc for missing edge cases.
- Diagnose why this test suite is flaky.
- Suggest a faster prototype path.

## Notes

- Most setups expect `GEMINI_API_KEY` or an equivalent authenticated CLI session.
- If Gemini CLI is missing, explain that `gemini` must be installed and authenticated first.
