# gab0-claude-toolkit — Claude Project Instructions

## What This Repo Is

A public portfolio of Claude Code slash commands (skills) built for real-world use. Each skill is a self-contained prompt that Claude executes when invoked via `/skill-name` in Claude Code.

## Skills in This Repo

| Skill | Invocation | Description |
|-------|-----------|-------------|
| forecast | `/forecast "1 week" "AI industry"` | Predicts the future of any topic using live web research |

## Naming Conventions

- All skill folders use **lowercase-hyphenated** names (e.g., `skills/forecast/`, `skills/market-scan/`)
- SKILL.md is always uppercase
- Example files go in `examples/` subfolder

## Skill Structure Requirements

Every skill must have:

```
skills/<skill-name>/
├── SKILL.md              # The prompt file (with frontmatter)
└── examples/
    └── sample-output.md  # Example invocation + output description
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

## How to Test a Skill Locally

1. Copy the skill's `SKILL.md` to `~/.claude/commands/<skill-name>.md`
2. Open Claude Code in any project
3. Invoke with `/skill-name arg1 arg2`
4. Verify the output matches the expected structure in `examples/sample-output.md`
5. Delete the file from `~/.claude/commands/` when done testing

## Adding a New Skill

See `CONTRIBUTING.md` for the full process.
