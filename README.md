# GK Claude Skills

A collection of reusable [Claude Code](https://claude.ai/code) skills built by Gourav Kumar.

## What are Claude Skills?

Skills are reusable slash commands for Claude Code. When installed, they appear as `/skill-name` commands in your Claude Code session. Each skill bundles a prompt, context, and instructions that Claude follows when invoked.

## Skills

| Skill | Description |
|-------|-------------|
| [nodejs-install](skills/nodejs-install/) | Check for Node.js/npm and install Node.js 24 on macOS (nvm) or Windows (Chocolatey), with validation and troubleshooting |

## How to Use a Skill

1. Copy the skill's `.md` file into your Claude Code skills directory:
   - **Global** (available in all projects): `~/.claude/skills/`
   - **Project-local**: `.claude/skills/` in your project root

2. Restart Claude Code or run `/refresh` to load the new skill.

3. Invoke it with `/skill-name` in any Claude Code session.

## Skill Structure

Each skill lives in `skills/<skill-name>/` and contains:

```
skills/
└── my-skill/
    ├── skill.md        # Main skill definition (frontmatter + prompt)
    └── README.md       # Usage guide and examples
```

### Skill Frontmatter

```yaml
---
name: my-skill
description: One-line description shown in /help
---

Your skill prompt goes here...
```

## Contributing

Feel free to open a PR or issue if you have suggestions or want to share a skill.

## License

MIT
