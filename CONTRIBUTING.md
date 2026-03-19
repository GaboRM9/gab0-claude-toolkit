# Contributing a New Skill

## Folder Structure

Each skill lives in its own folder under `skills/`:

```
skills/<skill-name>/
├── SKILL.md              # The prompt file
└── examples/
    └── sample-output.md  # What the skill produces
```

Use **lowercase-hyphenated** names (e.g., `market-scan`, `code-review`, `pitch-coach`).

---

## SKILL.md Template

```markdown
---
name: skill-name
description: One-line description of what the skill does
argument-hint: [arg1] [arg2]
allowed-tools: WebSearch, WebFetch
model: opus
---

[Your skill prompt here. Use $ARGUMENTS[0], $ARGUMENTS[1], etc. for user inputs.]
```

### Frontmatter Fields

| Field | Required | Notes |
|-------|----------|-------|
| `name` | Yes | Lowercase-hyphenated, matches folder name |
| `description` | Yes | Shown in `/help` — be specific |
| `argument-hint` | Yes | Shown as usage hint in Claude Code |
| `allowed-tools` | Yes | Only list tools the skill actually uses |
| `model` | Yes | `opus` for research-heavy, `sonnet` for general tasks |

---

## sample-output.md Template

```markdown
# <Skill Name> Skill — Sample Output

## Example Invocation
\`\`\`
/skill-name "arg1" "arg2"
\`\`\`

## What This Produces
[Description of each section in the output]

## Notes
[Any quirks, caveats, or tips for best results]
```

---

## Testing Locally

1. Copy your skill to `~/.claude/commands/<skill-name>.md`
2. Open Claude Code in any project
3. Invoke with `/skill-name arg1 arg2`
4. Verify output matches the structure in `examples/sample-output.md`
5. Iterate on the prompt until satisfied
6. Remove from `~/.claude/commands/` when done

---

## Adding to README

Add a row to the Skills table in `README.md`:

```markdown
| [skill-name](./skills/skill-name/SKILL.md) | `/skill-name "[arg1]" "[arg2]"` | Brief description |
```
