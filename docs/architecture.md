# Architecture

The task board uses a simple separation of responsibilities:

```text
Meeting / approved team chat / private agent update
                    ↓
        Shared workbook update queue
                    ↓
     Scheduled reconciliation and validation
                    ↓
          Canonical JSON + HTML artifact
                    ↓
              Test and production site
```

## Components

### Sources

Use only explicitly approved meeting summaries and the designated team chat. Scope is a safety boundary: do not read every meeting or every chat just because a topic looks related.

### Shared workbook

The workbook is the human- and agent-friendly working surface. It contains the full task context, update submissions, and append-only history. It is not the live board and updates do not appear immediately in the HTML page.

### Canonical JSON

The JSON is the formal backup and machine-readable source for the board state. It preserves stable card IDs, task fields, history, provenance, and explicit removal tombstones.

### HTML board

The HTML is a read-only presentation. It should not make runtime API calls or contain secrets. It embeds a validated snapshot of board data and exposes search, filtering, grouping, history, and lightweight guidance for users.

### Automation

Scheduled processing reads approved sources, reconciles proposed updates against the workbook and JSON, validates the candidate, and publishes only a safe result. A failed or suspicious run leaves the last known-good board in place.

## Data ownership

The workbook and JSON are operational files in the team’s controlled working folder. The GitHub repository contains templates and the published presentation, not private source material. The HTML should be refreshed from the validated candidate rather than edited manually as a data store.
