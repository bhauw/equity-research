---
name: equity-research
description: Run Braxton's institutional 8-Lens + Damodaran equity research framework (v2) on a ticker — archetype classification, qualitative deep-dive, cost-of-capital build-up, 3-stage DCF, Monte Carlo, 8 equal-weight investor lenses, investment gates and position sizing — then write a structured note to the Obsidian vault's Investing/ folder. Use when the user says "run 8-lens", "analyze <ticker>", "equity research on X", "deep dive on <company>", wants a BUY/WATCH/AVOID verdict, or asks for a quarterly thesis update. Vault at ~/Library/Mobile Documents/iCloud~md~obsidian/Documents/claude.
---

# Equity Research — 8-Lens + Damodaran (v2)

Institutional-grade research on one company, run in a fixed sequence. Source of truth:
`~/Documents/Investing/Master Prompts/Investment_Research_Instructions_v2.docx`.

**Vault:** `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/claude`
**Ticker/company:** from the arguments. If empty, ask which one.

## Core philosophy — do not skip

All 8 investor lenses run on **every** company, **equally weighted**, regardless of archetype.
No lens is privileged. **Disagreement between lenses is the most useful output — surface it,
never average it away.** The archetype classification selects the *valuation method* only; it
never changes which lenses apply.

Conviction comes from disconfirmation, not confirmation. Damodaran's rule governs every number:
every number traces to a story, every story is expressed as a number. Output **ranges, not points** —
"$35–$65, central $50" is honest; "$47.23" is false precision.

## Before you start — load context

1. Read `Investing/Research Framework — 8-Lens Analysis.md` and `Investing/Investing Hub.md`
   (portfolio, current stances, vocabulary).
2. If the ticker is already a holding, read its existing note and the relevant
   `[[<exchange> Portfolio]]` note — this becomes an **update**, not a fresh start.
3. Existing models: `~/Documents/Investing/Investing/Excell/<TICKER>_Financial_Model.xlsx`
   and `Analysis/`. Read them rather than re-deriving numbers.
4. Load `references/prompt-library.md` for the verbatim prompt text of any phase you run.

## The sequence

### §0 — Data quality gate + archetype
Validate inputs first: price + date, diluted shares, market cap, EV, 5Y+TTM income statement,
5Y+TTM cash flow, latest+2Y balance sheet, and the derived metrics (ROIC, ROE, FCF conversion,
Net Debt/EBITDA, interest coverage, reinvestment rate). Full checklist in
`references/data-checklist.md`. Pull current figures via WebSearch if stale. Missing figures get
flagged explicitly — state the assumption made and why. Mark `DQ Gate: PASS/FAIL`.

Then classify into one of six archetypes (Quality Compounder, Growth Accelerator, Deep Value,
Turnaround/Special Situation, Cyclical/Commodity, Macro/Rate Sensitive) with Yes/Partially/No
evidence per archetype, a confidence level, and a hybrid flag. See
`references/archetypes-and-gates.md`.

### §1–§4 — Qualitative phase (run in sequence, context accumulates)
1. **Industry & moat** — business model, TAM/SAM/SOM, industry structure and HHI, barriers,
   capital cycle; moat source and durability evidence (ROIC persistence, margin stability,
   share retention); market position, pricing power, customer concentration.
2. **Financial quality** — ROIC/ROE/ROCE/FCF-ROIC (TTM + 5Y avg), ROIC−WACC spread, incremental
   ROIC, DuPont; margin trend and FCF conversion (flag < 50%); balance sheet incl. a 25–30%
   EBITDA-decline stress test, maturity profile, off-balance-sheet items; capital allocation
   (reinvestment rate, buyback discipline vs intrinsic value, M&A post-deal ROIC vs WACC,
   SBC as % of FCF). Deep Value/Turnaround: add asset, liquidation and tangible book value.
3. **Risk & variant perception** — reverse DCF at the current price; macro sensitivity (rates
   ±100bps, inflation pass-through, FX, credit cycle, geopolitics); growth quality
   (volume×price×mix, structural vs cyclical, reflexive loops); risk framework (3 thesis-break
   scenarios, 3–5 monitoring variables, disruption, ESG/regulatory).
4. **Synthesis** — quality classification (Elite Compounder / High-Quality but Cyclical /
   Turnaround / Deep Value / Moderate / Structurally Weak), an explicit **investment filter
   verdict** ("Worth deeper valuation work" vs "Not attractive"), and a capital-allocation
   recommendation. Be decisive; no hedging for balance.

**Gate: only proceed to valuation if the filter verdict is "Worth deeper valuation work."**

### §5 — The 8 lenses
Run all eight independently and equally: Buffett, Ackman, Dalio, Druckenmiller, Tepper,
Klarman, Marks, Icahn. Each reaches its own verdict without reference to the others; score each
1–10 (→ /80) and use the framework's exact three-way verdict wording per lens — see
`references/lenses.md`. Finish with a **lens summary table** (bullish/neutral/bearish) and an
explanation of what the *pattern of agreement and disagreement* reveals. Do not average.

### §6 — Damodaran valuation foundation (before any DCF)
Run in order — `references/damodaran.md` has the full method:
- **D1 Narrative before numbers** — the 6 story questions, each mapped to a model input.
- **D2 Cost of capital from components** — current 10Y government yield; bottom-up beta
  (industry unlevered beta re-levered at actual D/E); Damodaran implied ERP + revenue-weighted
  country risk premium; synthetic-rating cost of debt from interest coverage; market-value-weight
  WACC. Compare to the framework's benchmark rates (4.5% US non-financial, 8.5% Indonesian
  non-financial, 15% CoE Indonesian banks) — if they differ by >1%, explain and use the computed figure.
- **D3 Relative valuation** — 4–6 peers, multiple decomposition (any premium/discount must be
  justified by a fundamental), implied fair values, and reconciliation vs the DCF (>20% divergence
  must be explained).
- **D4 Model integrity check** — FCFF@WACC vs FCFE@CoE never mixed; reinvestment = growth/ROIC
  each year; terminal reinvestment = g/terminal ROIC; g ≤ nominal GDP; market-value WACC weights;
  ΔWC included; justified margin trajectory; TV ≤ 75% of EV. Report failures as **ACTION REQUIRED**.

### §7 — Deterministic valuation
Choose the primary method by archetype (table in `references/archetypes-and-gates.md`). Build the
**three-stage** DCF: high growth Y1–5, fade Y6–10, terminal Y11+. Output the year-by-year table
(Year | Revenue | Growth | EBIT margin | EBIT | NOPAT | Reinvestment rate | Reinvestment | FCFF |
Discount factor | PV), terminal value and its % of EV, equity value per share, a sensitivity grid
(terminal growth rows × WACC columns), and a reverse DCF at the current price.

### §8 — Monte Carlo
5 stochastic variables — revenue CAGR, operating margin, terminal growth, WACC, ROIC — each
N(μ,σ) with truncated bounds; correlations (CAGR↔reinvestment +0.6, CAGR↔margin −0.3,
WACC↔terminal multiple −0.5); hard constraint WACC ≥ g + 1% every iteration; 10,000 paths.
Report mean/median/quartiles/5th/95th/σ/skew/kurtosis, P(IV > price), P(IRR ≥ 15%), P(IRR ≥ 10%),
P(capital loss), expected shortfall of the bottom 5%, bear/base/bull, a 15-bin histogram table,
a decile CDF table, and a tornado ranking. If a full simulation isn't run in-session, give a
defensible reasoned estimate and **flag it as approximate**.

Size the margin of safety to uncertainty width, not a fixed buffer: <20% range = low uncertainty,
20–40% medium, 40–80% high, >80% very high (binary).

### §9 — Gates, sizing, final package
Six gates, applied equally to all archetypes: downside protection · balance-sheet resilience ·
competitive stability · return adequacy (IRR ≥ 10% base, ≥ 15% bull) · thesis legibility ·
lens coverage (≥ 5 of 8 bullish or neutral). Position sizing is lens-count driven — see
`references/archetypes-and-gates.md`.

Final package: base-case IV + MoS, bear/base/bull with explicit assumption deltas, expected IRR,
probability-weighted FV (25/50/25), driver attribution, final classification, probabilistic conclusion.

## Write the note

Save to `Investing/<TICKER> — <Company> Analysis.md`, opening with the Scorecard:

```markdown
---
tags: [investing, <ticker-lower>, <exchange>]
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
ticker: <TICKER>
exchange: <EXCHANGE>
company: <Company Inc.>
archetype: <archetype>
---
# <TICKER> — <Company>

> Version <n> · <context, e.g. post Q2 FY26 earnings> · <date>

## Scorecard
| Metric | Value |
|--------|-------|
| Price (<date>) | … |
| Archetype | … (confidence: H/M/L) |
| Quality classification | … |
| **Verdict** | **BUY / WATCH / AVOID — <size>** |
| Conviction | n/5 |
| WACC (computed / benchmark) | …% / …% |
| Base DCF FV (range) | $… – $… (central $…) |
| Bull FV / Bear FV | … / … |
| Prob-weighted FV | … |
| MC P50 | … |
| P(FV > Price) | …% |
| P(IRR ≥ 15%) | …% |
| Expected IRR (base) | …% |
| Upside (base) | …% |
| Stop loss | … |
| 8-Lens score | n/80 (m/8 bullish+) |
| Gates passed | n/6 |
| TV % of EV | …% |
| DQ Gate | PASS/FAIL |
| Triangulation | CONVERGED/DIVERGED |
| MoS | …% |
```

Then: Narrative (D1 answers) · Archetype rationale · Industry & Moat · Financial Quality ·
Risk & Variant Perception · Kill-the-trade · Cost of Capital build-up · DCF cases + sensitivity ·
Reverse DCF · Comps and reconciliation · Monte Carlo · **8-Lens table** (score + one-line verdict
per lens) + lens summary and the key disagreement · Gates & sizing · Monitoring variables and
thesis-break conditions.

## Quarterly update mode

If the user pastes new results, run the update prompt in `references/prompt-library.md`:
reported vs consensus vs your base case; whether the case strengthens/maintains/weakens; changes
in monitoring variables; archetype drift; shifted lenses; Bayesian probability update; revised
base-case IV; and a decisive Add/Hold/Trim/Exit. Append to a dated update log in the note.

## Finish

- Update the **Current Stances** table in `Investing/Investing Hub.md`.
- Add a `[[wikilink]]` from the relevant `[[<exchange> Portfolio]]` note.
- If an Excel model is wanted, build it to the 9-tab structure in `references/excel-model.md`
  (use the `xlsx-author` skill).
- Print in chat: the Scorecard, the headline verdict, and the single most important
  **disagreement between lenses**.

Braxton's voice: concise, practical, plain English. Be honest about uncertainty — mark every
number as sourced or estimated.
