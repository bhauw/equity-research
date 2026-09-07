# Prompt Library — Verbatim Framework Prompts

Use these when running a phase manually or handing the framework to another session. Substitute
`[COMPANY NAME]`, `[TICKER]`, and the bracketed figures.

| Prompt | Purpose |
|---|---|
| 0 | Archetype classification |
| 1 | Industry & moat |
| 2 | Financial quality |
| 3 | Risk & variant perception |
| 4 | Synthesis + investment filter |
| 5 | All 8 investor lenses |
| D1–D4 | Narrative · cost of capital · relative valuation · integrity check |
| 6 | DCF & deterministic valuation |
| 7 | Monte Carlo |
| 8 | Final output package |
| 9 | Quarterly thesis update |

---

## PROMPT 0 — Archetype Classification (run first)

Before we begin the full analysis, classify [COMPANY NAME] into one of these archetypes:
1. Quality Compounder 2. Growth Accelerator 3. Deep Value / Cigar Butt
4. Turnaround / Special Situation 5. Cyclical / Commodity 6. Macro / Rate Sensitive

For each archetype, state: does this company fit (Yes / Partially / No); key evidence for or
against; final classification with confidence level (High / Medium / Low). Also flag if the
company is a hybrid.

This classification is used solely to select the appropriate valuation method in Phase 2.
All 8 investor lenses will be applied equally regardless of archetype.

---

## PROMPT 1 — Industry & Moat

Analyze [COMPANY NAME] ([TICKER]). Archetype classification: [OUTPUT FROM PROMPT 0].

Financial data: current price $[X] | market cap $[X]B | net debt $[X]B | TTM revenue $[X]B |
5Y revenue CAGR [X]% | TTM EBITDA margin [X]% | TTM EBIT margin [X]% | TTM FCF $[X]B |
ROIC (TTM) [X]% | ROE (TTM) [X]%

**A. Business & industry mapping** — business model, segment structure, revenue composition, cost
structure; TAM/SAM/SOM with historical growth and forward CAGR; industry structure (HHI, top 3–5
players, nature of competition); barriers to entry, switching costs, regulatory moats; capital
cycle (capacity additions, supply discipline, return-on-capital trends).

**B. Competitive advantage & moat** — primary moat source(s): cost advantage, switching costs,
network effects, brand, regulatory protection, asset uniqueness, IP, distribution; evidence of
durability (ROIC persistence, margin stability, share retention); competitive game theory
(competitor incentives, margin compression risk, disruption threats).

**C. Market position** — market share trend over 5–10 years (gaining, holding, losing); pricing
power evidence (inflation pass-through, premium ASPs, margin stability in downturns); customer
concentration and bargaining power.

Be explicit. Separate confirmed facts from reasoned inferences. No generic commentary.

---

## PROMPT 2 — Financial Deep-Dive

Continue the analysis of [COMPANY NAME].

**Return metrics** — ROIC, ROE, ROCE, FCF ROIC (TTM and 5-year averages); ROIC − WACC spread
(4.5% US non-financials, 8.5% Indonesian non-financials, 15% cost of equity for Indonesian banks);
incremental ROIC (ΔNOPAT / ΔInvested capital over 3 years); DuPont decomposition
(net margin × asset turnover × financial leverage → ROE).

**Margin analysis** — gross, EBIT, EBITDA, FCF margins over 5 years; FCF conversion (FCF/EBITDA),
flag if below 50%; margin stability through downturns vs peers; operating leverage profile
(incremental margin on revenue growth).

**Balance sheet** — net debt/EBITDA and interest coverage; stress test a 25–30% EBITDA decline —
does the company remain solvent?; debt maturity profile and refinancing risk; off-balance-sheet
obligations (leases, pensions, contingencies).

**Capital allocation** — reinvestment rate and implied sustainable growth (ROE × retention);
buyback discipline (executed above or below intrinsic value?); M&A track record (post-acquisition
ROIC vs WACC); SBC as % of FCF.

If Deep Value or Turnaround: also assess asset value, liquidation value, and tangible book value
per share relative to market price.

---

## PROMPT 3 — Risk & Variant Perception

Continue the analysis of [COMPANY NAME].

**E. Market-implied expectations (reverse DCF at current price)** — what revenue CAGR, margin,
ROIC and terminal growth does the current price imply? Are those above or below the historical
5-year actuals? Where is consensus optimistic vs pessimistic?

**F. Macro sensitivity** — rate sensitivity (earnings and valuation at ±100bps); inflation
exposure (input cost pass-through, labor cost sensitivity); FX exposure (revenue and cost base by
currency); credit cycle vulnerability (does the business need cheap credit to function?);
geopolitical risk (sanctions, trade restrictions, foreign ownership limits).

**G. Growth quality** — revenue decomposition into volume × price × mix; structural vs cyclical
split of current earnings; reflexive loops between stock price, capital access and fundamentals.

**H. Risk framework** — thesis-break analysis: under what 3 specific scenarios does the long case
fail?; the 3–5 monitoring variables that confirm or invalidate the thesis; disruption risk
(technological obsolescence, platform displacement, substitutes); ESG and regulatory trajectory.

---

## PROMPT 4 — Synthesis & Quality Classification

Produce the full Integrated Investment Synthesis for [COMPANY NAME]:
1. Market & competitive position — compact, evidence-based
2. Moat & pricing power — with specific ROIC/ROE figures and years validating durability
3. Financial superiority — TTM + 5Y averages, DuPont, FCF ROIC, balance sheet
4. Growth quality — structural vs cyclical split, reinvestment runway, capital efficiency
5. Risk summary — top 3 risks with severity (High/Medium/Low) and time horizon

**Overall quality classification** (choose one): Elite Compounder · High-Quality but Cyclical ·
Turnaround / Special Situation · Deep Value · Moderate Quality / Fair Business ·
Structurally Weak / Avoid

**Investment filter verdict:** state clearly "Worth deeper valuation work" OR "Not attractive —
capital better allocated elsewhere", with 3–5 decisive reasons.

**Capital allocation recommendation:** "High-priority candidate for detailed valuation and
monitoring" / "Monitor but wait for better price or clearer catalyst" / "Structurally
unattractive — do not allocate research time".

Be decisive. No hedging for the sake of balance. Evidence drives the conclusion.

---

## PROMPT 5 — All 8 Investor Perspectives

Using everything established in the prior analysis of [COMPANY NAME], produce an independent
assessment from each of the 8 investor perspectives. Each must reach its own verdict without
reference to the other lenses. All 8 carry equal weight. Disagreement between lenses is expected,
valuable, and should not be reconciled.

Full criteria and verdict wording per lens: see `lenses.md`. After all 8 verdicts, produce a
**lens summary table** showing which lenses are bullish, neutral or bearish, and explain what the
pattern of agreement or disagreement reveals about the investment's risk/reward profile.
Do not average them into a single view.

---

## PROMPT D1 — Narrative Before Numbers

Before we build the DCF model for [COMPANY NAME], answer these 6 story questions explicitly:
1. What business is this, and what is the realistic TAM ceiling ($ figure + time horizon)?
2. How does it make money? Will operating margins expand, hold, or mean-revert over 10 years —
   with specific reasoning, not just a direction?
3. How much reinvestment does growth require? Show reinvestment rate = revenue growth / ROIC.
   Capital-light or capital-heavy? Improving or worsening?
4. How risky is this business? Justify beta and cost of equity:
   Ke = Rf + β × ERP + country risk premium. Source the ERP from Damodaran for the primary
   operating country.
5. How many years of above-average growth are realistic? Stage 1 high growth (Y1–5),
   Stage 2 fade (Y6–10), Stage 3 terminal.
6. What does the mature Year-10+ company look like — terminal revenue growth, terminal ROIC,
   terminal reinvestment rate? Constraint: terminal growth ≤ nominal GDP of the primary market.

Only after answering all 6 should we proceed to the numbers.

---

## PROMPT D2 — Build the Cost of Capital

Build the cost of capital for [COMPANY NAME] from components — full method in `damodaran.md` §D2.
State the risk-free rate and its date; the industry unlevered beta and its source, re-levered at
the actual D/E and tax rate; Damodaran's implied ERP plus a revenue-weighted country risk premium;
cost of equity with every number shown; synthetic-rating cost of debt from interest coverage,
after tax; and WACC at explicit market-value weights.

Compare the computed WACC to the fixed assumption used in this framework. If they differ by more
than 1%, explain why and use the computed figure.

---

## PROMPT D3 — Relative Valuation & Multiple Decomposition

Step 1 — peer set: 4–6 comparables, each with EV/EBITDA, EV/EBIT, EV/FCF, P/E, revenue CAGR,
EBIT margin, ROIC, net debt/EBITDA.
Step 2 — where does [COMPANY NAME] trade on each multiple vs the peer median: premium, discount,
or in line?
Step 3 — fundamental decomposition: for each premium or discount, what fundamental (ROIC, growth,
margin, risk) justifies it? If none does, flag it as a valuation risk (premium) or opportunity
(discount).
Step 4 — implied fair value: apply peer median EV/EBITDA, EV/FCF and P/E to TTM figures for three
multiple-based valuations; compare to the DCF.
Step 5 — reconciliation: within 20% = internally consistent. Beyond 20% = identify the DCF
assumption driving the gap and judge whether the market's multiple pricing is more or less
reasonable.

---

## PROMPT D4 — Model Integrity Check

Before finalizing the DCF for [COMPANY NAME], verify the seven checks in `damodaran.md` §D7:
FCFF/FCFE consistency · reinvestment = growth/ROIC each year with implied ROIC shown ·
terminal consistency (reinvestment = g/terminal ROIC, terminal ROIC vs WACC justified, g ≤ nominal
GDP) · WACC construction (market-value weights, bottom-up beta, current implied ERP) · ΔWorking
capital included and realistic · justified margin trajectory · terminal value as % of EV
(if > 75%, extend the forecast or explain).

Report any integrity failures as ACTION REQUIRED items.

---

## PROMPT 6 — Valuation

Run the deterministic valuation for [COMPANY NAME]. Archetype: [FROM PROMPT 0].
WACC: [computed, or 4.5% US non-financial / 8.5% Indonesian non-financial / 15% Indonesian bank
cost of equity]. Terminal growth: long-term nominal GDP of primary region − 0.5%.

Step 1 — state all input assumptions explicitly before calculating. Justify each year's revenue
growth, margin forecast (expanding / stable / mean-reverting), and reinvestment = growth / ROIC.
Step 2 — 10-year DCF table: Year | Revenue | Growth | EBIT margin | EBIT | NOPAT | Reinvestment
rate | Reinvestment | FCFF | Discount factor | PV of FCFF.
Step 3 — terminal value = FCF(Y10) × (1+g) / (WACC − g). Show TV and its % of enterprise value.
Step 4 — equity value per share = (EV − net debt) / diluted shares.
Step 5 — sensitivity table: rows terminal growth (g−1% to g+2%), columns WACC (WACC−1% to
WACC+2%), cells intrinsic value per share.
Step 6 — reverse DCF: at the current price of $[X], what implied revenue CAGR, terminal margin,
ROIC and perpetual growth does the market require? Above or below 5-year historical actuals?

If Deep Value: also estimate liquidation value (assets at distress prices − all liabilities),
earnings power value (normalized EBIT / cost of capital, no growth), and replacement asset value.

All outputs in table format suitable for Excel.

---

## PROMPT 7 — Monte Carlo

Run the full Monte Carlo valuation simulation for [COMPANY NAME].

Five stochastic variables, N(μ,σ) with truncated bounds:
1. Revenue CAGR — μ=[X]%, σ from historical volatility, bounds [floor, ceiling]
2. Operating margin — μ=[X]%, σ=range/4, bounds [floor, ceiling]
3. Terminal growth — μ=[X]%, σ=0.5%, bounds [0.5%, GDP rate]
4. WACC — μ=[X]%, σ=0.5%, bounds [X, X]
5. ROIC — μ=[X]%, σ from historical std dev, bounds [X, X]

Hard constraint: WACC ≥ terminal growth + 1% enforced at every iteration.
Correlations: revenue CAGR ↔ reinvestment +0.6 · revenue CAGR ↔ operating margin −0.3 ·
WACC ↔ terminal multiple −0.5. Run 10,000 simulations (full DCF per iteration).

Outputs: statistics table (mean, median, 25th, 75th, 5th, 95th, std dev, skewness, kurtosis);
probability metrics — P(IV > current price), P(IRR ≥ 15%), P(IRR ≥ 10%), P(capital loss);
downside risk — expected shortfall (average of the bottom 5%), 5th percentile valuation, margin of
safety at current price; scenario breakdown — bear (25th pct), base (median), bull (75th pct);
histogram — bin midpoints and frequency % for 15 bins; CDF table at every 10th percentile from
5th to 95th; tornado chart — the 5 variables ranked by impact on valuation dispersion, showing IV
at the 10th and 90th percentile input for each.

---

## PROMPT 8 — Final Output Package

1. Base case: intrinsic value per share + margin of safety vs current price $[X]
2. Bear / base / bull table: explicit assumption changes, resulting intrinsic value, implied return
3. Expected IRR: the discount rate equating base-case intrinsic value to current price
4. Probability-weighted fair value: bear 25% / base 50% / bull 25%
5. Driver attribution: top 3 variables driving valuation uncertainty
6. Final classification: Deep Value · Fairly Valued Compounder · Premium Compounder ·
   Overvalued Quality · Narrative-Driven · Cyclical Trough Opportunity
7. Probabilistic conclusion, e.g. "68% probability undervalued, 22% fairly valued, 10% overvalued"

Format all outputs as clean labeled tables. Include units on all figures.

---

## PROMPT 9 — Quarterly Thesis Update

[COMPANY NAME] just reported [Q/FY YEAR] results.

Reported: revenue $[X] vs consensus $[X] vs my base case $[X] · EBIT margin [X]% vs prior [X]% vs
base case [X]% · FCF $[X]B vs base case $[X]B · key management commentary: [paste].

My original thesis assumptions: revenue CAGR [X]% → actual TTM [X]% · ROIC [X]% → actual TTM [X]% ·
margin [X]% → actual [X]% · moat strength [assessed as X] → any change?

1. Do these results strengthen, maintain, or weaken the investment case? Be direct.
2. Have any of the 3–5 key monitoring variables changed materially?
3. Has the archetype classification changed (e.g. compounder degrading to cyclical)?
4. Update the 8-lens summary: which perspectives have shifted?
5. Bayesian update: what probability adjustment do you recommend?
6. Revised base-case intrinsic value — has it moved materially?
7. Action: Add / Hold / Trim / Exit — with a decisive rationale.

Log every update in Tab 8 of the Excel model and in the vault note's update log.
