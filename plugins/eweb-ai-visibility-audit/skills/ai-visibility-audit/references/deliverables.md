# Deliverables Specification

Two deliverables per audit: a branded Microsoft Word document and a Gamma presentation deck.

---

## Deliverable 1 — Branded Word Document (`.docx`)

Use the `docx` skill. Build with `docx-js` following these rules.

### E-Web Marketing palette

| Token | Hex | Use |
|---|---|---|
| Primary Navy | `0F2A4F` | H1, H2, cover title, meta-table labels, table header fill |
| Accent Red | `C8102E` | Cover subhead, H1 bottom border, callout top border |
| Slate | `475569` | H3, subtle body |
| Light | `F1F5F9` | Callout background |
| Winning green | `E6F4EA` | "Where We Are Winning" table fill |
| Gap red | `FCE8E6` | "Topic Opportunities" table fill |
| Alt row | `F8FAFC` | Zebra striping in long tables |
| Border grey | `CBD5E1` | All table borders |
| Muted | `64748B` | Footer text |
| Text | `1E293B` | Body |

### Layout rules

- US Letter (12240 × 15840 DXA), 1-inch margins.
- **Cover page** — "E-WEB MARKETING" small red header, "Client Insights Report" subhead with a red rule below, large client name in navy, "AI Visibility Report" in red, subtitle in slate italic, meta table with 6 rows (Client / Market / Reporting Period / Primary Competitors / Prepared By / Data Sources), confidential line at the bottom.
- **Running header** — red rule line + "E-WEB MARKETING  |  <Client> — AI Visibility Report" on left, date on right.
- **Running footer** — "Confidential — E-Web Marketing" on left, "Page X of Y" on right.
- **H1** always gets a red (Accent Red) bottom border.
- **Tables** always use `WidthType.DXA` (never PERCENTAGE), dual widths (`columnWidths` array + cell `width`), `ShadingType.CLEAR` (never SOLID), 100pt/140pt cell margins, header row with navy fill + white text.
- **"Where We Are Winning"** tables fill entire table with winning green. **"Topic Opportunities"** tables fill with gap red.
- **Key takeaway callouts** use a red top border (size 16) + light blue background + 200/240pt internal margins.
- The client row in every competitive table is bold and uses a soft orange accent fill (`#FFF4E5`).

### Validation

Before delivery, run `python scripts/office/validate.py <path>` from the docx skill. Fix any errors or warnings.

### Save location

`<ClientSlug>_AI_Visibility_Report_<Month>_<Year>.docx` in the outputs folder.

---

## Deliverable 2 — Gamma Presentation Deck

Use the Gamma `generate` tool with these EXACT settings.

### Theme — CRITICAL

- `themeId`: `aymtetmhwuwh8r9`
- This is the **E-web Brand custom theme** — E-Web's official Gamma theme with navy + red palette, brand typography, and logo already wired at the theme level.
- **Do NOT substitute any other theme** (Dialogue, Consultant, Commons, etc.) under any circumstances.
- Before calling `generate`, call `get_themes` with `name: "E-web Brand"` to verify the theme exists and the ID matches. If it does not return, STOP and tell the user the theme is missing — do not silently fall back.

### Generation parameters

```
format: "presentation"
themeId: "aymtetmhwuwh8r9"
textMode: "generate"
numCards: 20
cardOptions.dimensions: "16x9"
textOptions.amount: "brief"
textOptions.tone: "confident, consultative, readable, warm"
textOptions.audience: "non-technical senior marketing client"
textOptions.language: "en-gb"
imageOptions.source: "aiGenerated"
imageOptions.stylePreset: "photorealistic"
imageOptions.style: "<tailor to client's industry — e.g. 'calm editorial photography of <industry>, warm neutral tones, soft natural light, aligned with a navy-and-red corporate palette'>"
```

### `additionalInstructions` value to pass verbatim

> Use the E-web Brand custom theme exactly as configured — respect every brand token (colours, typography, logo placement). Prioritise readability: one topic per slide, generous whitespace, no cramming multiple tables onto a single card. Audience is non-technical senior client leadership — bullets are single sentences, max 3–5 per slide. Preserve every number verbatim. The deck must feel like an E-Web Marketing deliverable at first glance.

### 20-slide structure

1. Title — client name + "AI Visibility Report" + E-Web prepared-by credit + date
2. Executive Summary
3. Headline Metrics (table)
4. Three Things to Tell Leadership
5. AI Visibility by Platform (table)
6. Audience & Mentions Trend
7. Competitive Landscape Head-to-Head (table)
8. Key Competitive Observations
9. Where We Are Winning (table)
10. Topic Opportunities (table)
11. Top AI Prompts (table)
12. Prompt Patterns
13. Top Domains Citing Us (table)
14. Source Opportunities
15. Top Performing Pages (table)
16. Strengths & Risks
17. Opportunities
18. 90-Day Plan — Phase 1
19. 90-Day Plan — Phase 2 & 3
20. Target Outcomes + Thank You

### Note to include in wrap-up message

The E-Web Marketing logo and brand styling are baked into the E-web Brand theme — no manual logo upload needed. If the deck still feels visually off (dense tables, small type), the fix is content density not theme — tell the user to request a rerun with more `numCards` spread or to move bullet-heavy slides to appendix.

---

## Why-This-Theme Rationale (for internal reference)

E-Web Marketing's branded client deliverables always ship on the E-web Brand custom theme. Substituting standard themes breaks brand consistency, loses the logo, and shifts the palette off-brand. The theme is the single source of truth for agency visual identity across every client deck.

If the theme ever needs visual improvements (density, type size, colour tweaks), the fix is made once in Gamma's theme editor and every subsequent deck inherits it automatically. Never solve a visual problem by switching themes in this workflow.
