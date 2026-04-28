# Data Fetch Specification

This document specifies the exact SEMrush reports and parameters to pull after the three interactive checkpoints are complete.

Run calls in parallel where independent (e.g. client reports alongside competitor reports).

## Client Domain — Full Pull

### 1. Domain overview

- Report: `domain_rank`
- Params:
  - `database`: `au` (or the country code confirmed with the user)
  - `domain`: client's normalised domain
- Returns: Authority Score, organic keywords, organic traffic, organic cost, rank.

### 2. Organic keywords (top 25 by traffic)

- Report: `domain_organic`
- Params:
  - `database`: same as above
  - `domain`: client domain
  - `display_limit`: 25
  - `display_sort`: `tr_desc`
  - `export_columns`: `Ph,Po,Pp,Nq,Cp,Ur,Tr,Co,Tg`
- Columns returned: Keyword, Position, Previous Position, Search Volume, CPC, URL, Traffic %, Competition, Trends.

### 3. Top pages by traffic (top 15)

- Report: `domain_organic_unique`
- Params:
  - `database`: same
  - `domain`: client domain
  - `display_limit`: 15
  - `display_sort`: `tr_desc`

### 4. Backlink overview

- Report: `backlinks_overview`
- Params:
  - `target`: client domain
  - `target_type`: `root_domain`
- Returns: total backlinks, referring domains, authority score, trust score.

### 5. Top referring domains (top 15 by authority)

- Report: `backlinks_refdomains`
- Params:
  - `target`: client domain
  - `target_type`: `root_domain`
  - `display_limit`: 15
  - `display_sort`: `domain_ascore_desc`

## Each Competitor — Compact Pull

For each of the five confirmed competitors, pull:

### 1. Domain overview

- `domain_rank` — same structure as client call.

### 2. Top organic keywords (top 10)

- `domain_organic` with `display_limit: 10`, `display_sort: tr_desc`, `export_columns: Ph,Po,Nq,Tr,Ur,In` (In includes intent flags).

### 3. Top pages (top 5)

- `domain_organic_unique` with `display_limit: 5`, `display_sort: tr_desc`.

### 4. Backlink profile

- `backlinks_overview` with `target_type: root_domain`.

## Source-Opportunity Pull (for Section 5 of the Report)

After the client + competitor pulls, identify the strongest competitor by Authority Score and pull:

- `backlinks_refdomains` for that competitor with `display_limit: 20`, `display_sort: domain_ascore_desc`.

Cross-reference against the client's referring-domain list. Surface 6–8 high-authority domains that cite the competitor but NOT the client — these become the "Source Opportunities" section.

## Error Handling

- If `domain_rank` returns "NOTHING FOUND" for the client, stop and tell the user — the client is not in the SEMrush index for the selected database.
- If a competitor returns "NOTHING FOUND", note it in the report as a negative finding (weak competitor) and continue.
- If any single data pull errors or times out, note it in the report's methodology appendix and continue with a partial dataset.

## Optional: AI Visibility Signals

If the connected account has Ahrefs Brand Radar (or a SEMrush AI Toolkit equivalent), also pull:

- Brand Radar mentions overview (per platform: Google AI Overview, Google AI Mode, ChatGPT, Gemini)
- Brand Radar cited domains and cited pages
- Brand Radar AI responses (top prompts with source counts)

Label these as "verified live" in the report. If the addon returns a "Missing addon" error, fall back to modelled platform scores anchored to verified SEMrush signals (see `deliverables.md` for the modelling formula) and label them "modelled" in the appendix.
