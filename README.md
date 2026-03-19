# gab0-claude-toolkit

> A toolkit of AI-powered Claude Code slash commands — built for real-world use.

Claude Code supports custom slash commands (skills) that give Claude a focused persona, live tools, and a structured output format. This is a public collection of skills built and used daily.

---

## Quick Install

```bash
cp skills/forecast/SKILL.md ~/.claude/commands/forecast.md
```

Then in any Claude Code session:
```
/forecast "1 month" "OpenAI"
/forecast "Real Madrid"
/forecast "3 months" "K-pop"
```

---

## Skills

| Skill | Invocation | What it does |
|-------|-----------|--------------|
| [/forecast](./skills/forecast/README.md) | `/forecast "[time-horizon]" "[topic]"` | Oracle-style prediction for any topic — runs 10 adaptive live searches, builds a topic profile, finds the historical parallel, delivers falsifiable predictions with causal chains |

---

## What kind of topics?

Anything. The skill builds the right research strategy per topic instead of applying the same template to everything.

```
/forecast "1 month" "OpenAI"              # tech
/forecast "3 months" "Brazilian elections"  # politics
/forecast "1 season" "anime spring 2026"  # culture
/forecast "1 month" "Real Madrid"         # sports
/forecast "1 year" "coral reef bleaching" # science
/forecast "3 months" "K-pop"              # entertainment
/forecast "2 weeks" "crypto market"       # finance
/forecast "5 years" "nuclear energy"      # long-range
/forecast "1 month" "Joe Rogan"           # just curious
```

---

## How Skills Work

Each skill is a `.md` file in `~/.claude/commands/`. When you type `/skill-name` in Claude Code, the file loads as a system prompt and Claude executes it with access to the declared tools.

**Argument syntax** — positional, 0-based:
- `$0` — first argument
- `$1` — second argument
- `$ARGUMENTS` — all arguments as a single string

---

## Repo Structure

```
gab0-claude-toolkit/
├── .claude/
│   └── CLAUDE.md              # Claude's instructions for this repo
├── skills/
│   └── forecast/
│       ├── SKILL.md           # The skill prompt
│       ├── README.md          # Full documentation
│       └── examples/
│           └── sample-output.md
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
