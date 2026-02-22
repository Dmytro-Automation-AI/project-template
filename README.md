# Project Name

## Overview
- **Client:** [Client Name]
- **Contact:** [Email / Phone]
- **Company:** [Company Name]
- **Pipeline Stage:** [Discovery / In Progress / Demo / Delivered]
- **Created:** [Date]
- **Assigned to:** [Team member]

## Project Status
- [ ] Discovery call completed
- [ ] Requirements documented
- [ ] Materials received from client
- [ ] Work started
- [ ] MVP complete
- [ ] Demo delivered
- [ ] Client review & approval
- [ ] Deployed / Handed off

## Key Links
- **Meeting recording:** [Fathom / Loom link]
- **Client docs:** [Google Drive / other link]
- **Live app:** [URL if deployed]

## Architecture
[Describe the technical approach once decided]

## Setup After Cloning
```bash
git config core.hooksPath .githooks
```
This enables the pre-commit hook that enforces `memory/STATUS.md` updates.

## For AI Agents
**Start here:** Read `AGENTS.md` then `memory/STATUS.md` before doing any work.

## Documents
- `meetings/` — call transcripts and summaries
- `memory/STATUS.md` — current project state (always up to date)
- `docs/` — specs, references, test accounts
- `.mulch/expertise/` — structured project knowledge (query with `npx mulch-cli query --all`)
