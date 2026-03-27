# claude-plugin-opinionated

A minimal Claude Code marketplace repo for delegating work to other local AI CLIs. It is to hand work off to another lane so token usage and rate-limit pressure can be spread across tools.

Included skills:

- `delegate-claude`
- `delegate-codex`
- `delegate-gemini`
- `delegate-copilot`

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
## Notes

- Each skill is intentionally minimal and delegates to the corresponding local CLI.
- Adjust the binary names if your installed command is not `claude`, `codex`, `gemini`, or `copilot`.
- If you want fully automatic invocation, remove `disable-model-invocation: true` after testing.
