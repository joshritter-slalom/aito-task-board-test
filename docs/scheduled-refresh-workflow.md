# Scheduled refresh workflow

The exact schedule is team-specific, but the sequence should remain consistent.

## Daily overnight refresh

After the source-note summarization job has completed and after the team’s update cutoff:

1. Read only approved meeting summaries, the designated team chat, workbook updates, and canonical JSON.
2. Assign blank update IDs from workbook row numbers using a stable format such as `NEW-R####`.
3. Match updates to existing Card IDs where possible.
4. Reconcile new tasks, field changes, status changes, priority changes, history, and explicit removals.
5. Flag conflicts, missing ownership, malformed data, duplicate IDs, and suspicious count changes.
6. Validate the candidate JSON, workbook, and HTML payload.
7. If validation passes, update the operational files and board artifact. If it fails, preserve the last known-good state and save a failure report.

## Pre-meeting refresh

Run a final pass on the meeting day after the cutoff and early enough to allow review before the meeting. For a 2:30 p.m. Eastern meeting, a late-morning cutoff and refresh is a reasonable starting point, subject to the team’s availability.

## Concurrency

Multiple desktop agents may work in the shared folder. Each agent should make narrow row-level edits, avoid the same open row when possible, and never replace the workbook wholesale. The central job should re-read the latest workbook before processing and leave unresolved conflicts as `Needs review`.

OneDrive normally manages file synchronization, but a refresh should verify that the latest file version is available before reading it. Do not publish a partial or stale candidate.
