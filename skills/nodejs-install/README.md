# nodejs-install

Guides you through installing Node.js 24 on macOS or Windows, with pre-install validation so it never tries to install something that's already there.

## What it does

1. **Checks first** — runs `node -v`, `npm -v`, `npx -v` and reports what's already installed
2. **Installs if needed** — macOS via nvm, Windows via Chocolatey
3. **Validates** — confirms all four checks pass after installation
4. **Troubleshoots** — per-platform tables for common failure modes

## Usage

```
/nodejs-install
```

## Installation

Copy `SKILL.md` to your Claude Code skills directory:

```bash
# Global (all projects)
mkdir -p ~/.claude/skills/nodejs-install
cp SKILL.md ~/.claude/skills/nodejs-install/SKILL.md
```

Then restart Claude Code or run `/refresh`.

## Expected versions

| Tool | Version |
|------|---------|
| Node.js | v24.15.0 |
| npm | 11.12.1 |
| npx | bundled with npm |
