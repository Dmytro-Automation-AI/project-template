# Project Name

## Overview
- **Client:** [Client Name]
- **Contact:** [Email / Phone]
- **Company:** [Company Name]
- **Project Type:** [Client / Internal / Demo / Delivery / Research]
- **Created:** [Date]
- **Assigned to:** [Team member]

## Goal
[One paragraph on what this project is for and what success looks like.]

## Current Scope
- [Primary scope item]
- [Secondary scope item]
- [Out-of-scope note if useful]

## Key Links
- **Discord channel:** [#channel-name]
- **Repo:** [GitHub URL]
- **Meeting recording:** [Fathom / Loom link]
- **Client docs:** [Google Drive / other link]
- **Live app:** [URL if deployed]

## Architecture / Approach
[Describe the current technical or operational approach once decided.]

## Working Map
- `docs/index.md` — map of important docs, notes, and references
- `memory/STATUS.md` — live project snapshot
- `meetings/` — transcripts and summaries
- `docs/` — durable project docs
- `src/` — implementation artifacts and source files
- `.mulch/` — structured agent knowledge

## Setup After Cloning
```bash
npm install  # auto-configures git hooks via prepare script
```

This enables the pre-commit hook that enforces `memory/STATUS.md` updates.

## For AI Agents
**Start here:** Read `AGENTS.md`, then `memory/STATUS.md`, then `docs/index.md` if the project has grown beyond a simple setup.
