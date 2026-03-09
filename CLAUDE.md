# CLAUDE.md — Auto-loaded by Claude Code

## First Steps (every session)
1. Read `AGENTS.md` for full project instructions and rules
2. Read `memory/STATUS.md` for current project state
3. Run `npx mulch-cli prime` to load project expertise
4. Create `memory/YYYY-MM-DD.md` if it does not exist (with `# Session YYYY-MM-DD` header)

All automation source code and scripts go in `src/`.

## Rules
- Use conventional commits: `feat:`, `fix:`, `docs:`
- Never commit secrets

## Mid-Session Persistence (MANDATORY)

**After EVERY response where you created or modified files, you MUST:**
1. Run `/project:sync` before sending the response
2. If `/project:sync` is unavailable, at minimum: `git add -A && git commit -m "chore: mid-session sync"` + append 1-2 lines to `memory/YYYY-MM-DD.md`

This is non-negotiable. Do NOT batch syncs to "session end." Every file change triggers a sync.

## Mulch Recording Triggers (MANDATORY)

You MUST call `npx mulch-cli record <domain> --type <type> "<content>"` when ANY of these happen:
- A bug was found and fixed
- An architectural decision was made
- A new pattern or convention was discovered
- A significant failure happened

Do not defer these to session end. Record immediately when the event occurs.

## Memory Logging
- Update `memory/STATUS.md` after completing any milestone
- Log daily work in `memory/YYYY-MM-DD.md`
