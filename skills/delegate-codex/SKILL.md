---
name: delegate-codex
description: Delegate work to OpenAI Codex CLI so token usage and rate-limit pressure can be shifted off the current lane.
allowed-tools: Bash(codex *)
disable-model-invocation: true
---

# Delegate Codex

Use the local `codex` CLI as a delegated execution lane for scripted or CI-style runs.

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
codex exec -m gpt-5-codex "$ARGUMENTS"
codex exec -C . "$ARGUMENTS"
codex exec --json "$ARGUMENTS"
codex exec resume --last "$ARGUMENTS"
codex exec --full-auto "$ARGUMENTS"
```

## Good prompts

- Review this patch and point out correctness risks.
- Suggest a Rails-native alternative to this implementation.
- Explain the likely cause of this production error.
- Propose a simpler schema for this data flow.

## Notes

- `codex exec` is the non-interactive command for delegated runs; `codex e` is the short form.
- Use `-C` or `--cd` when repository context matters.
- Use `--json` for newline-delimited JSON events in automation.
- Use `resume --last` to continue the most recent exec session in the current working directory.
- `--full-auto` applies the low-friction preset: `workspace-write` sandbox and `on-request` approvals.
- For stricter non-interactive automation, prefer `--ask-for-approval never` instead of the deprecated `on-failure` mode.
- If Codex CLI is missing, explain that `codex` must be installed and authenticated first.
