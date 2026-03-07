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
- NEVER push directly to `main` — always use feature branches + PRs
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
1. **Task completion** → Update STATUS.md (move item to "Done")
2. **Learning discovered** → `mulch record` immediately
3. **Session end** → Append summary to `memory/YYYY-MM-DD.md`
4. **Blocker hit** → Update STATUS.md with details immediately
5. **Every 30 min of active work** → Quick STATUS.md update

## Agent Handoff Protocol

When finishing work and another agent (or human) will continue:
1. Update `memory/STATUS.md` with exact current state
2. Record any learnings with `mulch record`
3. Commit and push all changes
4. If mid-task: leave a clear note in STATUS.md about where you stopped

This ensures zero-context-loss handoffs between agents and collaborators.
