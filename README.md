# Claude Config Backup

This repository contains Claude MCP settings and custom skills.

## Files

- `claude_desktop_config.json` — MCP server configuration (API keys redacted)
- `settings.json` — Claude Code settings
- `CLAUDE.md` — Global Claude instructions
- `skills/` — Custom skills

## Restore

1. Copy `claude_desktop_config.json` to `~/Library/Application Support/Claude/`
   and fill in your actual API keys
2. Copy `skills/` to `~/.claude/skills/`
3. Copy `CLAUDE.md` to `~/.claude/CLAUDE.md`
4. Copy `settings.json` to `~/.claude/settings.json`

> ⚠️ API keys have been redacted. Add your own keys before using.
