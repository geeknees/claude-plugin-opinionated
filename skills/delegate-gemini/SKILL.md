---
name: delegate-gemini
description: Delegate work to Google Gemini CLI so token usage and rate-limit pressure can be shifted off the current lane.
allowed-tools: Bash(gemini *)
disable-model-invocation: true
---

# Delegate Gemini

Use the local `gemini` CLI as a delegated execution lane for headless or session-based follow-up work.

## What this skill should do

1. Gather the required local context before invoking Gemini.
2. Turn the request and that context into a concise Gemini prompt.
3. Hand the work off to Gemini in non-interactive mode.
4. Return the output and mention the model when explicitly set.
5. Pull out the most actionable recommendations.

## Default command

```bash
gemini -p "$ARGUMENTS"
```

## Useful variants

```bash
gemini -p -m pro "$ARGUMENTS"
gemini -r "latest" "$ARGUMENTS"
gemini -p --output-format json "$ARGUMENTS"
```

## Good prompts

- Give another lane on this refactor.
- Review this design doc for missing edge cases.
- Diagnose why this test suite is flaky.
- Suggest a faster prototype path.

## Notes

- `gemini -p` or `gemini --prompt` runs in headless mode for non-interactive execution.
- Use `-r "latest"` or `--resume "latest"` to continue the most recent session with a new prompt.
- Prefer model aliases like `pro`, `flash`, or `flash-lite` unless you specifically need a concrete model name.
- Use `--output-format json` or `--output-format stream-json` for automation.
- In the interactive CLI, session browsing and checkpoint management are available through `/resume`, with `/chat` as an alias.
- Most setups expect `GEMINI_API_KEY` or an equivalent authenticated CLI session.
- In the prompt, tell Gemini to answer from the supplied context first.
- When the task is code review, bug diagnosis, or implementation feedback, include the relevant diff, file contents, command output, or error text in the prompt instead of expecting Gemini to discover everything itself.
- A bare `/delegate-gemini Code review this repo` request is likely to fail in setups that restrict Gemini's built-in tools or non-interactive approvals.
- If Gemini reports unauthorized tool calls, rerun with a prompt that embeds the needed repository context and explicitly asks for a direct answer without exploratory delegation.
- If Gemini CLI is missing, explain that `gemini` must be installed and authenticated first.
