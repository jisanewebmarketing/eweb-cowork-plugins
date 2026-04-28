# Report Structure

The report has 8 sections plus an appendix. Title format: `<Client Brand Name> | AI Visibility Report`.

Every section below maps to both the DOCX and the Gamma deck. Preserve section numbering and order exactly.

## Executive Summary

- Opening paragraph (3–5 sentences) — high-level framing of the client's AI-search position and the single most important strategic message.
- Headline Metrics scorecard (table with 5 columns): AI Visibility Score, Monthly AI Audience, Total Mentions, Cited Pages, Share of Voice — with MoM deltas.
- "Three Things to Tell Leadership" — 3 bullets, each a single sentence with a crisp point and a number.

## 1. AI Visibility Performance

- Platform-level scores table: Google AI Overview, ChatGPT, AI Mode, Gemini. Columns: Platform, Score /100, Trend (6mo), MoM Δ, What's driving it.
- Audience & mentions trend analysis — 4 bullets.

### Modelled AI Visibility Index (only when live data unavailable)

When Brand Radar is not available, compute platform scores using:

```
AI Visibility Score (0-100) =
    0.35 × (count of AI-triggering SERP features on top 25 keywords / max possible)
  + 0.25 × (Position-1 count on commercial intent keywords / max possible)
  + 0.20 × (Authority Score / 100)
  + 0.20 × (Referring Domains / benchmark)
```

Per-platform modifiers:
- Google AI Overview: weight AIO-triggering keywords 2×.
- AI Mode: weight long-tail + question-style keywords 1.5×.
- ChatGPT: weight review/commercial keywords + referring-domain count 1.5×.
- Gemini: weight structured-data presence 2× (low by default — flags as a gap).

Flag every modelled value in the methodology appendix.

## 2. Competitive Landscape

- Head-to-head table: Brand, AI Vis, AI Audience, MoM, Mentions, Authority Score, Org KW, Org Traffic, Backlinks, Ref Domains.
- AI Visibility Scorecard (3-column table): Dimension, We lead on, We trail on. Dimensions: Local/service queries, Commercial Position-1, Treatment/content depth, Product content, Review signals, Authority signal.
- Key Competitive Observations — 5 bullets.

## 3. Topic Performance

- "Where We Are Winning" table — topics where client ranks top-5. Columns: Topic, Volume, Intent, Position, Status.
- "Topic Opportunities" table — topics where competitors rank top-10 but client doesn't rank top-20. Columns: Topic, Volume, Intent, Currently Won By, Gap.
- Intent values: Informational, Navigational, Commercial, Transactional.
- 3 bullets of strategic observations tying the opportunities to specific content plays.

## 4. Prompt Performance

- Top 7–10 AI prompts the client likely appears on. Columns: Prompt, AI Platform, Sources Cited, Driver.
- Pattern summary — 4 bullets (what type of queries dominate each platform, what's missing).

When Brand Radar is unavailable, derive prompts from the client's Position-1 rankings on informational and commercial queries, cross-referenced with SERP features that trigger AI assistants.

## 5. Citation & Source Analysis

- "Top Domains Citing Us" table (top 10). Columns: Domain, Type, Authority Score, Why it matters.
- "Source Opportunities" table (6–8 rows) — high-authority domains citing the strongest competitor but NOT the client. Columns: Domain, AS, Traffic, Citing Competitor, Outreach Angle.
- Priority Outreach Targets — 5–6 bullets with specific 60-day actions.

## 6. Which Pages Are Working

- Top-cited URLs table (top 10). Columns: URL, Traffic/mo, #KWs, Top Keyword (with Position + Volume), Ref. Domains.
- Flag rows where the SERP includes AI Overview (from SERP features in `domain_organic`).
- Content Observations — 5 bullets explaining WHY each page works.

## 7. Key Observations

Three bulleted lists, each with 4–7 bullets:

- **Strengths** — what the data shows we're winning at.
- **Weaknesses & Risks** — structural gaps and concentration risks.
- **Opportunities** — specific growth levers tied to data.

Every bullet must tie back to a specific data signal (a number, a URL, a keyword position).

## 8. Next Steps — 90-Day Action Plan

Three phases, each a table with columns: Initiative, Owner, Target (day), Impact.

- **Phase 1 — Foundational Hygiene (Days 1–30)** — schema rollout, Google Business Profile, canonical fixes, internal linking, review acquisition flow.
- **Phase 2 — Pillar Content Build (Days 31–60)** — head-term pillar, treatment/category explainers, herbs/products library, local-modifier pages.
- **Phase 3 — Authority & Measurement (Days 61–90)** — digital PR, whitepaper, monthly rescan, credential syndication.

End with a "90-Day Target Outcomes" callout (6 bullets — projected movement on each headline metric).

## Appendix — Methodology & Data Notes

- **Data Sources** — list each SEMrush report used, the date pulled, the database code.
- **Verified Live vs. Modelled** — explicit table showing which figures are SEMrush-pulled and which are modelled via the AI Visibility Index formula.
- **Glossary** — AI Visibility Score, Share of Voice, Cited Pages, AI Overview, Authority Score, Domain Rating.

## Consistency Rules

- Every competitor appears in every applicable section — do not drop competitors mid-report.
- Every number appearing in the report must be traceable to a specific SEMrush row. Do not round aggressively (keep at least 2 sig figs for percentages).
- The client row in every competitive table is visually distinguished (bold, highlighted fill).
- Winning topic tables use a soft green fill; opportunity/gap tables use a soft red fill.
