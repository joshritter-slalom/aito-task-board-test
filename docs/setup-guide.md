# Setup guide

Use this guide to create a team-specific instance without modifying the Standup instance.

## 1. Define the instance

Record the team name, approved meeting names, approved chat, meeting cadence, working-folder location, test repository, production repository, and production site URL. Keep source scope explicit and narrow.

## 2. Create the working folder

Copy the files from `templates/` into a controlled shared folder:

- the update workbook
- the agent instructions
- the canonical JSON file

Replace placeholders with team-specific values. Do not add credentials or private meeting content to the repository.

## 3. Seed the board

Review several weeks of approved meeting material. Identify open work, reconcile duplicate references, preserve historical evidence, and present the proposed task inventory for human review before publishing the first board.

## 4. Create repositories

Create separate test and production repositories. Use the existing board HTML as the structural starting point, but remove the source team’s data, history, links, automations, and configuration. For a static site with multiple pages, keep each page as a separate file under `public/` and document its URL.

## 5. Configure refreshes

Create the daily and pre-meeting jobs only after the workbook, JSON, source scope, and test board have been validated. Use the schedule guidance in `scheduled-refresh-workflow.md` and adjust times to the team’s cadence.

## 6. Validate access

Confirm that intended users can access the site through Slalom SSO and that the production repository’s hosting app grants the right audience.
