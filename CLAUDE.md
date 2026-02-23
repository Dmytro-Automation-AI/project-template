# CLAUDE.md — Auto-loaded by Claude Code

## First Steps (every session)
1. Read `AGENTS.md` for full project instructions and rules
2. Read `memory/STATUS.md` for current project state
3. Run `npx mulch-cli prime` to load project expertise

## Quick Reference
- **Project:** [Project Name]
- **Tech:** [Tech Stack]
- **Repo:** [GitHub URL]
- **Test account:** see `docs/test-accounts.md`

## MCP Server Configuration
MCP servers for Claude Code are configured in `~/.claude.json` (top-level `mcpServers` key).
- **User-level (global):** `~/.claude.json` → `mcpServers` object
- **Project-scoped (shared):** `.mcp.json` in the project root
- **NOT** `~/.claude/.mcp.json` or `~/.claude/settings.json` — those are ignored for MCP
- Use `claude mcp add <name> ...` CLI or edit `~/.claude.json` directly

## Rules
- Update `memory/STATUS.md` after completing any milestone
- Record learnings with `npx mulch-cli record <domain> --type <type>` before ending session
- Use conventional commits: `feat:`, `fix:`, `docs:`
- Never commit secrets (project test accounts in `docs/` are fine)
- Log daily work in `memory/YYYY-MM-DD.md`
