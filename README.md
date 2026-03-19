# gab0-claude-toolkit

> A toolkit of AI-powered Claude Code slash commands — built for real-world use.

Claude Code supports custom slash commands (skills) that give Claude a focused persona, live tools, and a structured output format. This repo is a public collection of the skills I've built and use daily.

---

## Quick Install

**Install all skills at once:**
```bash
cp skills/*/SKILL.md ~/.claude/commands/
# Rename each file to match its skill name (e.g., forecast.md)
```

**Install a single skill:**
```bash
cp skills/forecast/SKILL.md ~/.claude/commands/forecast.md
```

Then invoke it in any Claude Code session:
```
/forecast "1 week" "AI industry"
```

---

## Skills

| Skill | Invocation | Description |
|-------|-----------|-------------|
| [forecast](./skills/forecast/SKILL.md) | `/forecast "[time-horizon]" "[topic]"` | Predicts the future of any topic using 10+ live web searches, signal analysis, and a structured Oracle report |

---

## How Skills Work

Each skill is a `.md` file stored in `~/.claude/commands/`. When you type `/skill-name` in Claude Code, the file is loaded as a system prompt. Claude then executes it with access to whatever tools the skill declares.

Skills in this repo use `$ARGUMENTS[0]`, `$ARGUMENTS[1]` etc. for user-provided inputs.

---

## Repo Structure

```
gab0-claude-toolkit/
├── .claude/
│   └── CLAUDE.md              # Claude's instructions for working in this repo
├── skills/
│   └── forecast/
│       ├── SKILL.md           # The skill prompt
│       └── examples/
│           └── sample-output.md
├── README.md
├── CONTRIBUTING.md
└── LICENSE
```

---

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) to add your own skill.

---

## Resources

- [Claude Code Docs](https://docs.anthropic.com/en/docs/claude-code)
- [Custom Slash Commands](https://docs.anthropic.com/en/docs/claude-code/slash-commands)

---

Built by [Gabe](https://github.com/GaboRM9) — designed for people who want Claude to do more than answer questions.
