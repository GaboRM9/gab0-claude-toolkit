# gab0-claude-toolkit

> A toolkit of AI-powered Claude Code slash commands — built for real-world use.

Claude Code supports custom slash commands (skills) that give Claude a focused persona, live tools, and a structured output format. This repo is a public collection of skills built and used daily.

---

## Quick Install

**Install a single skill:**
```bash
cp skills/forecast/SKILL.md ~/.claude/commands/forecast.md
```

**Install all skills:**
```bash
for dir in skills/*/; do
  name=$(basename "$dir")
  cp "$dir/SKILL.md" ~/.claude/commands/"$name".md
done
```

Then invoke in any Claude Code session:
```
/forecast "1 week" "AI industry"
```

---

## Skills

| Skill | Invocation | Description |
|-------|-----------|-------------|
| [/forecast](./skills/forecast/README.md) | `/forecast "[time-horizon]" "[topic]"` | Live-research forecast for any topic — runs 13 adaptive searches, finds the historical parallel, and delivers a sharp Oracle report with causal predictions |

---

## How Skills Work

Each skill is a `.md` file in `~/.claude/commands/`. When you type `/skill-name` in Claude Code, the file is loaded as a system prompt and Claude executes it with access to the declared tools.

**Arguments** use positional syntax:
- `$0` — first argument
- `$1` — second argument
- `$ARGUMENTS` — all arguments as a single string

Example in a skill prompt:
```
**Topic:** $1
**Time Horizon:** $0
```

---

## Repo Structure

```
gab0-claude-toolkit/
├── .claude/
│   └── CLAUDE.md              # Claude's instructions for working in this repo
├── skills/
│   └── forecast/
│       ├── SKILL.md           # The skill prompt
│       ├── README.md          # Full skill documentation
│       └── examples/
│           └── sample-output.md   # Annotated example output
├── README.md
├── CONTRIBUTING.md
└── LICENSE
```

---

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) to add a skill.

---

## Resources

- [Claude Code Docs](https://docs.anthropic.com/en/docs/claude-code)
- [Custom Slash Commands](https://docs.anthropic.com/en/docs/claude-code/slash-commands)

---

Built by [Gabe](https://github.com/GaboRM9).
