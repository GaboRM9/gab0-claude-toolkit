# gab0-claude-toolkit — Claude Project Instructions

## What This Repo Is

A public portfolio of Claude Code slash commands (skills) built for real-world use. Each skill is a self-contained prompt that Claude executes when invoked via `/skill-name` in Claude Code.

## Skills in This Repo

| Skill | Invocation | Description |
|-------|-----------|-------------|
| forecast | `/forecast "1 week" "Mexico"` | Live-research Oracle forecast for any topic — domain-adaptive, causal predictions, historical parallel |

## Naming Conventions

- All skill folders use **lowercase-hyphenated** names (e.g., `skills/forecast/`, `skills/market-scan/`)
- `SKILL.md` is always uppercase
- `README.md` lives at the skill level for documentation
- Example files go in `examples/` subfolder

## Skill Structure Requirements

Every skill must have:

```
skills/<skill-name>/
├── SKILL.md              # The prompt file (with frontmatter)
├── README.md             # Skill documentation
└── examples/
    └── sample-output.md  # Annotated example output
```

### Required SKILL.md Frontmatter

```yaml
---
name: skill-name
description: One-line description of what the skill does
argument-hint: [arg1] [arg2]
allowed-tools: WebSearch, WebFetch   # list only what the skill actually needs
model: opus                           # opus for research-heavy, sonnet for general
---
```

### Argument Syntax

Claude Code uses **positional 0-based** argument variables:
- `$0` — first argument
- `$1` — second argument
- `$ARGUMENTS` — all arguments as a single string

Do NOT use `$1`/`$2` (1-based, wrong) or `$ARGUMENTS[0]`/`$ARGUMENTS[1]` (array syntax, not supported).

## How to Test a Skill Locally

1. Copy the skill's `SKILL.md` to `~/.claude/commands/<skill-name>.md`
2. Open Claude Code in any project
3. Invoke with `/skill-name arg1 arg2`
4. Verify the output matches the expected structure in `examples/sample-output.md`
5. Remove from `~/.claude/commands/` when done testing

## Adding a New Skill

See `CONTRIBUTING.md` for the full process.
