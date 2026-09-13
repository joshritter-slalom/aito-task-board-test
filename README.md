# GenAI Standup Team Task Board

This repository contains a reusable example of a lightweight, agent-assisted task board. It is designed for teams that need to turn meeting conversations and private updates into a shared, accountable view of open work.

The repository contains the presentation layer and sanitized framework materials. Live meeting notes, task history, workbook data, canonical JSON, credentials, and local machine paths stay outside GitHub.

## Start here

- `standup-living-board.html` — self-contained, read-only board artifact.
- `docs/architecture.md` — how the components fit together.
- `docs/setup-guide.md` — how to create a new team-specific instance.
- `docs/operating-model.md` — how people and agents provide updates.
- `docs/scheduled-refresh-workflow.md` — recommended automation sequence.
- `docs/test-to-production.md` — safe branch, validation, and promotion process.
- `templates/` — sanitized starter instructions, JSON, and workbook.
- `examples/` — small synthetic sample data only.

## Hosting

The board can be hosted as a static HTML asset in a Slalom static web repository. The current production site is `https://aito-task-board.static.slalom.com`, and the board is published at `/standup-living-board.html`. A new team should use its own test and production repositories and its own provisioned `*.static.slalom.com` site when separate access or ownership is required.

The hosting template supports multiple HTML pages in one site. Put each page in `public/`, give it a stable filename, and add it to the landing-page asset list. Pages share the site’s SSO and deployment pipeline but should keep their data and refresh workflows separate.

## Important boundary

This repository is a framework and presentation example, not a complete operational deployment. Each team must configure its own meeting sources, approved chat, shared working folder, workbook, canonical JSON, automations, access controls, and production repository.
