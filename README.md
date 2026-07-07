# Development QA Checklist

A standalone, interactive checklist for Brandgility template developers — covering every step from picking up a ticket through final QA hand-off.

**Repository:** https://github.com/ThomasBrace/dev-qa-checklist

## Usage

Open `[Development-Checklist-standalone.html](https://thomasbrace.github.io/dev-qa-checklist/Development-Checklist-standalone.html)` directly in any modern browser. No build step or server required.

### Features

- **Three-section checklist** — Before Development, Before Sending to QA, and Miscellaneous
- **Progress tracking** — live percentage and item count updated as you check items off
- **Persistent state** — completed items and the template name are saved to `localStorage`, so progress is preserved across page refreshes
- **Download PDF** — generates a letter-format PDF via [html2pdf.js](https://github.com/eKoopmans/html2pdf.js), with the template name and today's date in the filename (e.g. `MKC-716 Shuttle Card - 2026-06-25.pdf`)
- **Reset** — clears all checked items and restarts from scratch

### PDF download

The Download PDF button requires an internet connection to load `html2pdf.js` from the cdnjs CDN. If offline, use the browser's **File → Print → Save as PDF** option instead.

The generated PDF:
- Avoids splitting checklist rows and section headers across page breaks
- Includes a "Generated: [date]" timestamp in the footer
- Uses letter format (8.5 × 11 in)

## Development

The entire app lives in a single file: `Development-Checklist-standalone.html`. It uses the Brandgility DC (Document Component) format — the template HTML and component logic are embedded as encoded script blocks inside the file, which the bundled runtime unpacks and renders at load time.

To update checklist items, edit the `getData()` method inside the `<script type="text/x-dc">` block within the template string.

## Checklist sections

| # | Section | Coverage |
|---|---------|----------|
| 01 | Before Development | Ticket review, file setup, font downloads, tagging |
| 02 | Before Sending to QA | Use case, template settings, UI fields, asset pickers, hotel picker, text/image rules |
| 03 | Miscellaneous | Dev/QA comments |
