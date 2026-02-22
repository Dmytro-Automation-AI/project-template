# AGENTS.md — Project Instructions

> Any AI agent working on this project: read this file first, then `memory/STATUS.md`.

## Project Overview
- **Client:** [Client Name]
- **Goal:** [One-line project goal]
- **Status:** [Current phase]
- **Repo:** [GitHub URL]

## Tech Stack
- TBD (to be decided during implementation planning)

## Working Rules

### Critical
- NEVER commit secrets, API keys, or credentials
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
├── README.md          # Project overview for humans
├── .mulch/            # Structured expertise (Mulch CLI)
│   └── expertise/     # JSONL files per domain
├── memory/            # Project memory (markdown)
│   ├── STATUS.md      # Current state — READ THIS FIRST
│   └── YYYY-MM-DD.md  # Daily work logs
├── meetings/          # Call transcripts and summaries
├── docs/              # Requirements, specs, references
└── src/               # Source code and scripts
```

## Mulch Expertise System

We use [Mulch CLI](https://github.com/jayminwest/mulch) for structured project expertise alongside markdown memory.

### Quick Commands
```bash
npx mulch-cli prime              # Load all expertise (run at session start)
npx mulch-cli prime <domain>     # Load one domain only
npx mulch-cli query --all        # Browse all expertise
npx mulch-cli search "keyword"   # Search across domains
npx mulch-cli record <domain> --type <type> "content"  # Record new expertise
npx mulch-cli status             # Check expertise freshness
```

### Record Types
| Type | Required Fields | Use Case |
|------|----------------|----------|
| convention | content | "Always use UTC timestamps" |
| pattern | name, description | Named patterns with file references |
| failure | description, resolution | What went wrong and how to fix it |
| reference | name, description | Key files, endpoints, links |
| guide | name, description | Step-by-step procedures |

### When to Use What
| Need | Tool |
|------|------|
| Current project state | `memory/STATUS.md` |
| Daily work log | `memory/YYYY-MM-DD.md` |
| Meeting notes | `meetings/` |
| Technical convention/pattern | `mulch record --type convention` |
| Failure + resolution | `mulch record --type failure` |
| Architecture decision | `mulch record --type decision` |
| Key resource/link | `mulch record --type reference` |

## Memory Rules (Auto-Save System)

Agents MUST save progress at these checkpoints:

### Auto-Save Triggers
1. **Task completion** — Update `memory/STATUS.md` (move item from "In Progress" to "Done")
3. **Session end** — Append summary to `memory/YYYY-MM-DD.md`
4. **Blocker hit** — Update STATUS.md with blocker details immediately
5. **Every 30 minutes of active work** — Quick STATUS.md update
6. **Learning discovered** — `mulch record` to capture expertise

### STATUS.md Format
Always maintain this structure in `memory/STATUS.md`:
```markdown
## Current State
- Phase: [Discovery/Design/MVP/Testing/Launch]
- Last updated: [date + who/what agent]
- Blocked by: [nothing / description]

## Done
- [x] Completed items with dates

## In Progress
- [ ] Current work items (with % if applicable)

## Next Up
- [ ] Planned items in priority order

## Key Context
```

### Decision Record Format
```markdown
# NNN: Short Title
**Date:** YYYY-MM-DD
**Status:** Accepted/Proposed/Superseded

## Context
What prompted this decision?

## Decision
What was decided?

## Alternatives Considered
- Option A: [pros/cons]
- Option B: [pros/cons]

## Consequences
What follows from this decision?
```

## Agent Handoff Protocol

When finishing work and another agent (or human) will continue:
1. Update `memory/STATUS.md` with exact current state
2. Record any learnings with `mulch record`
3. Commit and push all changes
4. If mid-task: leave a clear note in STATUS.md about where you stopped and what's next
