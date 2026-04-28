# E-Web AI Visibility Audit

A Claude Cowork plugin that runs E-Web Marketing's reusable AI Visibility Audit workflow end-to-end for any client domain.

## What this plugin does

Produces a client-ready AI Visibility Audit Report delivered as:

1. A branded Microsoft Word document (`.docx`) on the E-Web Marketing palette
2. A Gamma presentation deck on the **E-web Brand** custom theme

The workflow runs three interactive checkpoints with the analyst before fetching any data:

1. **Capture the client's website URL** — a single free-text question.
2. **Auto-suggest 5 SEMrush competitors** — filtered to remove marketplaces, directories, and non-commercial domains, with a one-sentence "why this competitor" rationale for each.
3. **Confirm or modify the competitor list** — the analyst can approve, remove, swap, or add domains (newly added domains are validated against SEMrush before the fetch begins).

After the three checkpoints, Claude pulls live data from SEMrush (AU database by default, with auto-switching for non-AU domains), runs an 8-section analysis, and delivers both files to the Cowork outputs folder.

## Install

### Option 1 — Drag-and-drop (simplest)

1. Download `eweb-ai-visibility-audit.plugin`.
2. Drag it into a Cowork session.
3. Click "Install" when Cowork previews the plugin.

### Option 2 — Shared marketplace (for the whole team)

1. Upload `eweb-ai-visibility-audit.plugin` to your internal Cowork marketplace or a shared Drive / Confluence / Notion location.
2. Add the marketplace source to the team's Cowork configuration.
3. Anyone on the team can install with one click.

## Prerequisites

Before running the workflow, the analyst's Cowork session must have these connectors active:

- **SEMrush** — for all organic-search data, top-page, keyword, and referring-domain pulls.
- **Gamma** — for presentation deck generation (must have access to the E-web Brand custom theme on the agency account).
- **Ahrefs Brand Radar** (optional) — if available, live AI mention data will be used; if not, platform scores are modelled from SEMrush signals and explicitly flagged in the report.

## Usage

### Command mode

Type the slash command in Cowork:

```
/ai-visibility-audit
```

Claude will immediately ask for the client's website URL, then suggest 5 competitors, then confirm before fetching data.

You can also pass the URL as an argument to skip the first question:

```
/ai-visibility-audit example.com.au
```

### Natural-language mode

Say any of the following and Claude will load the skill automatically:

- "Run an AI visibility audit for [client]"
- "I need an AI visibility report on [domain]"
- "Prepare AI SEO deliverables for [client]"
- "Audit a domain for AI search"
- "Generative search audit for [domain]"

## What you get

At the end of the workflow, Claude presents:

- A `computer://` link to the finished `.docx` (the Word document)
- A Gamma URL where the presentation deck is already generated
- A 4–6 bullet summary of the top real findings from the data
- A one-sentence note on any caveats (e.g. Brand Radar availability)

The wrap-up message is always under 150 words — the deliverables speak for themselves.

## Versioning

Current version: **0.1.0**

Future improvements (new sections, refined prompts, updated Gamma theme) ship to the whole team by updating this plugin's version and re-distributing the `.plugin` file.

## Contact

Maintained by E-Web Marketing's Senior SEO Strategy Team.
