# claude-plugin-opinionated

These plugins provide `/delegate-*` commands for getting second opinions from other AI assistants.

Included skills:

- `delegate-claude`
- `delegate-codex`
- `delegate-gemini`
- `delegate-copilot`

## Plugins

| Plugin | Type | Description |
|--------|------|-------------|
| delegate-claude | Plugin + Skill | Delegate a task to a local Claude CLI to spread token usage and rate-limit pressure. |
| delegate-codex | Plugin + Skill | Delegate a task to OpenAI Codex CLI to spread token usage and rate-limit pressure. |
| delegate-gemini | Plugin + Skill | Delegate a task to Google Gemini CLI to spread token usage and rate-limit pressure. |
| delegate-copilot | Plugin + Skill | Delegate a task to GitHub Copilot CLI to spread token usage and rate-limit pressure. |

## Repo layout

```text
.
├── .claude-plugin/
│   └── marketplace.json
└── skills/
    ├── delegate-claude/
    │   └── SKILL.md
    ├── delegate-codex/
    │   └── SKILL.md
    ├── delegate-gemini/
    │   └── SKILL.md
    └── delegate-copilot/
        └── SKILL.md
```

## Install in Claude Code

After pushing this repo to GitHub:

```bash
/plugin marketplace add geeknees/claude-plugin-opinionated
/plugin install delegate-claude@claude-plugin-opinionated
/plugin install delegate-codex@claude-plugin-opinionated
/plugin install delegate-gemini@claude-plugin-opinionated
/plugin install delegate-copilot@claude-plugin-opinionated
```

## Install as plain skills via skills.sh

```bash
npx skills add geeknees/claude-plugin-opinionated --skill delegate-claude
npx skills add geeknees/claude-plugin-opinionated --skill delegate-codex
npx skills add geeknees/claude-plugin-opinionated --skill delegate-gemini
npx skills add geeknees/claude-plugin-opinionated --skill delegate-copilot
```

## Usage

After installing a skill, use the matching `/delegate-*` command with a focused request. Keep the request concrete and include the relevant diff, code, error output, or design context.

| Skill | What it does | Default command |
|-------|---------------|-----------------|
| `delegate-claude` | Uses the local Claude CLI as a second execution lane. | `claude -p "$ARGUMENTS"` |
| `delegate-codex` | Uses OpenAI Codex CLI as a second execution lane. | `codex exec "$ARGUMENTS"` |
| `delegate-gemini` | Uses Google Gemini CLI as a second execution lane. | `gemini -p "$ARGUMENTS"` |
| `delegate-copilot` | Uses GitHub Copilot CLI as a second execution lane. | `copilot -p "$ARGUMENTS" --allow-all-tools` |

Example requests:

```text
/delegate-claude Review this diff for correctness, edge cases, and maintainability.
/delegate-codex Suggest a smaller implementation for this feature.
/delegate-gemini Diagnose why this test suite is flaky.
/delegate-copilot Compare this approach with a queue-based design.
```

Each skill expects the corresponding local CLI to be installed and authenticated first.

Provide Gemini with the relevant diff, file contents, or error output up front when you use `delegate-gemini` for code review or debugging. In many headless setups, Gemini cannot freely inspect the workspace, so a bare "review this repo" prompt is brittle.

## Notes

- Each skill is intentionally minimal and delegates to the corresponding local CLI.
- Adjust the binary names if your installed command is not `claude`, `codex`, `gemini`, or `copilot`.
- If you want fully automatic invocation, remove `disable-model-invocation: true` after testing.
