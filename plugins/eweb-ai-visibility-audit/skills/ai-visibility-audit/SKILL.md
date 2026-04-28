---
name: ai-visibility-audit
description: Produces client-ready AI Visibility Audit Reports for E-Web Marketing. Use when the user asks to run an AI visibility audit, generate an AI SEO audit, analyse a domain's generative-search visibility across Google AI Overview / ChatGPT / Gemini / AI Mode, or prepare AI-search deliverables for a client. Trigger phrases include "AI visibility audit", "AI visibility report", "generative search audit", "AI SEO audit", "run the AI audit for [client]", "prepare AI visibility deliverables", "SEMrush + Gamma audit", "audit a domain for AI search".
---

# AI Visibility Audit — E-Web Marketing

Act as a Senior SEO Strategist at E-Web Marketing. Produce a client-ready AI Visibility Audit Report, delivered as:

1. A branded Microsoft Word document (`.docx`)
2. A Gamma presentation deck on the E-web Brand custom theme

Follow the three-step interactive checkpoint flow in order. Do NOT skip any checkpoint. Do NOT start data fetching until all three are complete.

---

## Step 1 — Collect Client Website URL

Use the AskUserQuestion tool to ask for the client's website URL.

- Question label: "Client website URL"
- Header: "Client domain"
- Free-text input (no multiple choice)

When the user replies:
- Normalise the URL to a root domain — strip `https://`, `www.`, trailing slashes, and any paths.
- Confirm the normalised domain back in one sentence, e.g. "Great — running the audit for `ayurvedicwellnesscentre.com.au`."
- Proceed immediately to Step 2 — do not ask again.

## Step 2 — Auto-Discover Top 5 Competitors from SEMrush

Call the SEMrush `domain_organic_organic` report:

- `database`: `au` (default; change only if the client is outside Australia)
- `domain`: the normalised client domain
- `display_limit`: 10
- `display_sort`: `cr_desc`

From the 10 returned rows, select the top 5 by:
- Highest competition level (cr)
- Meaningful common keywords (cl ≥ 5)
- Must be a genuine commercial competitor — **exclude** marketplaces (amazon, ebay), directories (yellowpages, yelp), review aggregators, Wikipedia, news sites, and any domain that is not a direct competitor in the client's service category.

Present the 5 competitors in a markdown table with these columns: `#`, `Competitor Domain`, `Common Keywords`, `SE Keywords`, `Competition Level`, `Why this competitor` (one-sentence rationale).

End the table with this exact prompt:

> **Are these the right competitors?**
> - Type "yes" to proceed with these 5.
> - Or reply with any changes — remove rows you don't want, add new domains (one per line), or swap specific rows.

## Step 3 — Confirm or Modify Competitors

Wait for the user's reply.

- If the user says "yes" or equivalent → proceed with the suggested 5.
- If the user requests modifications:
  - Apply every change exactly as asked.
  - For any newly added domain, validate with SEMrush `domain_rank` (database = au by default). If a domain returns "NOTHING FOUND", flag it and ask whether to proceed or swap.
  - Re-present the final list as a numbered list (not a full table) and say "Proceeding with these 5 — fetching live data now." Do NOT ask to confirm again.
- If the reply is ambiguous, ask one targeted follow-up question via AskUserQuestion. Never guess the user's intent.

---

## After All Three Checkpoints — Run the Audit

Once the five competitors are confirmed:

1. **Fetch data** — Read `references/data-fetch.md` for the exact SEMrush reports and parameters to pull for the client and each competitor. Run calls in parallel where independent.

2. **Analyse & build the report** — Read `references/report-structure.md` for the 8-section report template plus appendix. Every number in the final report must trace to a specific SEMrush row.

3. **Produce deliverables** — Read `references/deliverables.md` for the DOCX branding rules and the Gamma generation config (theme ID, numCards, textMode, etc.).

4. **Quality checks** — Verify every number against the raw SEMrush response, flag all modelled values, validate the DOCX with `python scripts/office/validate.py`, and confirm the Gamma generationId returns a valid URL before presenting.

5. **Present deliverables** — Keep the final wrap-up under 150 words. Provide:
   - A `computer://` link to the DOCX
   - The Gamma URL
   - 4–6 bullets summarising the top real findings from the data
   - A one-sentence note on caveats (e.g. Brand Radar availability)
   - A one-line instruction on the E-web Brand Gamma theme (the logo is already baked in — no manual upload needed)

Do NOT explain the full report inline. The deliverables are the explanation.

---

## Edge Cases

- **Non-AU client** — If the domain TLD is `.com`, `.co.uk`, `.co.nz`, `.sg`, `.in`, etc., change the SEMrush `database` parameter accordingly (`us`, `uk`, `nz`, `sg`, `in`). For an Australian-owned but globally-operating brand, ask once which database to use.
- **Fresh / low-authority domain** — If the client has fewer than 50 keywords, shift report emphasis from "where we're winning" to "foundation + runway" — more weight on Phase 1 hygiene, less on pillar content.
- **Dominant client** — If the client's Authority Score is higher than every suggested competitor, ask whether to track against aspirational peers or direct competitors — this fundamentally changes the competitor list.
- **Brand Radar available** — If the Ahrefs Brand Radar add-on returns live data instead of a "Missing addon" error, use live data and clearly label platform scores as "verified live" rather than "modelled".
- **Industry outside wellness/services** — Adapt content-pillar suggestions to the industry. For SaaS, suggest "Best [category] tools" comparison pages instead of treatment explainers. For e-commerce, suggest product-category pillars instead of service pillars.

---

## Operating Principles

- SEMrush is the source of truth. Every number in the deliverables must trace to a pulled row.
- If a SEMrush call returns zero rows or an error, note it and continue — don't block the report on a single missing data point.
- Flag modelled values explicitly in the appendix. Never represent modelled AI visibility scores as verified.
- The Gamma theme is always the E-web Brand custom theme (id `aymtetmhwuwh8r9`). If it's missing from `get_themes`, stop and tell the user — do not silently fall back to another theme.
- The wrap-up message stays under 150 words. The deliverables speak for themselves.
