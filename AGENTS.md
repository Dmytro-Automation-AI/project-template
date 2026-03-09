# AGENTS.md — [Project Name]

> Any AI agent working on this project: read this file first, then `memory/STATUS.md`.

## Project Overview
- **Client:** [Client Name]
- **Goal:** [What we're building]
- **Status:** [Current phase]
- **Repo:** github.com/Dmytro-Automation-AI/[repo-name]
- **Discord channel:** [#channel-name]

## Tech Stack
- [List technologies used]

## Working Rules

### Critical
- NEVER commit secrets, API keys, or credentials (project test accounts in `docs/` are fine)
- Push directly to `main` — no feature branches or PRs needed
- ALWAYS update `memory/STATUS.md` after completing a milestone
- ALWAYS run `npx mulch-cli prime` at session start to load project expertise
- ALWAYS run `npx mulch-cli record` before finishing work to capture learnings

### Always
- Read `memory/STATUS.md` before starting any work
- Write clear commit messages (conventional commits: `feat:`, `fix:`, `docs:`)
- Log daily work in `memory/YYYY-MM-DD.md`

### Ask First
- Changing the tech stack or architecture
- Deploying to production
- Modifying any existing client data

## Project Structure
```
├── AGENTS.md          # You are here — agent instructions
├── CLAUDE.md          # Claude Code entry point (points here)
├── README.md          # Project overview for humans
├── .mulch/            # Structured expertise (Mulch CLI)
│   └── expertise/     # JSONL files per domain
├── memory/            # Narrative memory (markdown)
│   ├── STATUS.md      # Current state — READ THIS FIRST
│   └── YYYY-MM-DD.md  # Daily work logs
├── meetings/          # Call transcripts and summaries
├── docs/              # Specs, references, test accounts
└── src/               # ALL automation source code and scripts
```

## `src/` — Source Code Rules (CRITICAL)

**ALL automation scripts, workflows, and code files MUST live in `src/`.**

- Every file written, generated, or used for this project's automation goes in `src/`
- Subdirectories within `src/` should group by technology or purpose
  - Examples: `apps-script/`, `python-scripts/`, `n8n-workflows/`, `zapier/`, `make-scenarios/`
- This is the single source of truth for everything that runs or was used to build the automation
- If you create a new script, helper, or tool — commit it to `src/` immediately
- Never leave working code only in external tools (Google Drive, Apps Script editor, n8n, etc.) — always sync to `src/`

## Knowledge System

We use a **hybrid approach**: Mulch CLI for structured/searchable knowledge, markdown for narrative/state.

### Mulch (structured knowledge)
```bash
npx mulch-cli prime              # Load all expertise (run at session start)
npx mulch-cli prime <domain>     # Load one domain only
npx mulch-cli query --all        # Browse all expertise
npx mulch-cli search "keyword"   # Search across domains
npx mulch-cli record <domain> --type <type> "content"  # Record new expertise
npx mulch-cli status             # Check expertise freshness
```

**Record types:** convention, pattern, failure, decision, reference, guide

### When to Use What
| What you have | Where it goes |
|---|---|
| Current project state (done/doing/next) | `memory/STATUS.md` |
| Daily work log | `memory/YYYY-MM-DD.md` |
| Meeting transcript or summary | `meetings/` |
| Large specs, docs, test accounts | `docs/` |
| Automation scripts, workflows, code | `src/` |
| Technical convention or pattern | `mulch record --type convention` or `pattern` |
| Something broke + how to fix it | `mulch record --type failure` |
| Architecture/tech decision + rationale | `mulch record --type decision` |
| Key link, endpoint, or contact | `mulch record --type reference` |
| Step-by-step procedure | `mulch record --type guide` |

### Auto-Save Triggers
1. **After every response where files were changed** → MUST run `/project:sync`
2. **Task completion** → Update STATUS.md (move item to "Done")
3. **Learning discovered** → `mulch record` immediately
4. **Blocker hit** → Update STATUS.md with details immediately
5. **Bug fixed, decision made, pattern found, or significant failure** → MUST run `npx mulch-cli record` immediately

## End-of-Session Sync (CRITICAL)

**Always run `/project:sync` before ending any work session.**

This slash command (`.claude/commands/sync.md`) does everything in one shot:
1. Syncs external artifacts (n8n workflows, configs) to `src/`
2. Updates `memory/STATUS.md`
3. Appends to `memory/YYYY-MM-DD.md` (safe to run multiple times/day — appends, never overwrites)
4. Records Mulch entries for new decisions/bugs/patterns
5. Commits and pushes to GitHub

## Agent Handoff Protocol

When finishing work and another agent (or human) will continue:
1. Run `/project:sync`
2. If mid-task: leave a clear note in STATUS.md about exactly where you stopped

This ensures zero-context-loss handoffs between agents and collaborators.
