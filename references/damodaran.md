# The Damodaran Framework — Valuation Rigor

Damodaran is not an investor "style" like the 8 lenses. Where the lenses answer *should I
invest?*, this answers *how do I build the model correctly?* Core principle: every number traces
to a story, every story is expressed as a number. Models that can't be narrated are just
spreadsheets; narratives without numbers are fairy tales.

Free data (updated annually): `pages.stern.nyu.edu/~adamodar` — industry betas, implied ERPs,
country risk premiums, default-spread tables, Excel templates. Source WACC inputs from there
rather than guessing.

## D1 — Narrative before numbers

Answer these six in plain language **before opening Excel**. Each maps to a model input.

| Story question | Model input it drives |
|---|---|
| What business is this, and how big can it get? | Revenue TAM ceiling, terminal-year revenue |
| How does it make money — margins grow, hold, or compress? | Operating margin trajectory Y1–10 |
| How much must it reinvest to grow? | Reinvestment rate = growth / ROIC |
| How risky is this business vs alternatives? | Beta, cost of equity, WACC |
| When does growth slow to a mature rate? | Length of high-growth phase; fade period |
| What does the mature version look like? | Terminal growth, terminal ROIC |

Constraint: terminal growth ≤ nominal GDP growth of the primary market.

## D2 — Cost of capital, built from components

The single most common valuation error is a casually chosen WACC.

1. **Risk-free rate** — current 10-year government bond yield in the company's reporting
   currency (USD → 10Y UST; IDR → 10Y Indo govvie, or value in USD and adjust for the inflation
   differential). Today's yield. Not short rates, not historical averages. State the date.
2. **Beta — bottom-up, not regression.** Take the industry average unlevered beta from
   Damodaran's tables, then re-lever: `Levered β = Unlevered β × (1 + (1 − tax) × D/E)`. Show the
   D/E and tax rate used.
3. **Equity risk premium** — Damodaran's current *implied* ERP, not a historical average.
   Weight by revenue geography. Add country risk premium for emerging-market exposure:
   `CRP = country default spread × (σ equity / σ country bond)`.
   `Cost of equity = Rf + β × (mature ERP + weighted CRP)`.
4. **Cost of debt — synthetic rating.** Estimate the rating from interest coverage
   (EBIT / interest), take the matching default spread from Damodaran's table, then
   `after-tax Kd = (Rf + spread) × (1 − marginal tax)`.
5. **WACC** — `(E/V) × Ke + (D/V) × after-tax Kd`, at **market value weights** (E = market cap,
   D = market value of debt), never book.

Compare the computed WACC to the framework benchmarks (4.5% US non-financial, 8.5% Indonesian
non-financial, 15% cost of equity for Indonesian banks). Differ by more than 1% → explain why and
**use the computed figure**.

## D3 — Three-stage DCF structure

Collapsing everything into one growth rate plus a terminal value is the most common modeling
error — it forces an abrupt jump from high growth to stability in a single year.

| Phase | Years |
|---|---|
| Stage 1: high growth | 1–5 |
| Stage 2: transition / fade | 6–10 |
| Stage 3: terminal / stable | 11+ |

Critical checks:
- Terminal reinvestment rate must be internally consistent: `reinvestment = g / terminal ROIC`.
  Never set g and ROIC independently.
- Terminal ROIC should converge *toward* — not necessarily equal — WACC. A durable moat justifies
  a perpetual spread, but it should narrow.
- If terminal value > 75% of EV, the explicit forecast is doing too little work: extend it or
  question the growth story.
- Compare Year-10 FCF growth to terminal growth. Far apart = a cliff; extend the fade period.

## D4 — Relative valuation as the sanity check

Not a primary method — a check on the DCF. If the DCF says $100 and every comp says $50, explain
the gap or revisit the assumptions.

| Multiple | Best used for |
|---|---|
| EV/EBITDA | Capital-intensive businesses, cross-border comps |
| EV/EBIT | Where D&A ≈ maintenance capex |
| EV/FCF | FCF-generative businesses |
| P/E | Mature, stable earnings |
| EV/Revenue | Early-stage, negative-margin growth |
| P/Book | Banks, financials, asset-heavy firms |

**Multiple decomposition rule:** every multiple is a function of fundamentals — growth, margins,
ROIC, risk. A premium to peers must be matched by a fundamental that justifies it (higher ROIC,
faster growth, lower risk). No fundamental difference = multiple-expansion risk.

Process: 4–6 peers with EV/EBITDA, EV/EBIT, EV/FCF, P/E, revenue CAGR, EBIT margin, ROIC,
Net Debt/EBITDA → premium/discount vs peer median → decompose each gap → apply peer medians to
TTM figures for three multiple-based fair values → reconcile with the DCF. Within 20% = internally
consistent; beyond 20% = identify the driving assumption and judge which pricing is more reasonable.

## D5 — Probabilistic margin of safety

Graham's margin of safety is a fixed buffer. Damodaran's is a function of distribution width:
high uncertainty demands a bigger discount; a predictable compounder can be bought closer to IV.

| Uncertainty | DCF range as % of base case |
|---|---|
| Low (mature, predictable) | < 20% |
| Medium (established, some uncertainty) | 20–40% |
| High (growing, early stage) | 40–80% |
| Very high (turnaround, binary) | > 80% |

Output ranges, not points. "$35–$65, central $50" is honest; "$47.23" creates overconfidence.

## D6 — Common mistakes to avoid

1. **Mixing FCFF and FCFE.** FCFF (pre-debt) → discount at WACC. FCFE (post-debt, post-interest)
   → discount at cost of equity. Never cross-discount. The most common Excel error.
2. **Growth without reinvestment.** 15% revenue growth with a declining capex line is
   internally inconsistent. Show `reinvestment = growth / ROIC`.
3. **Terminal growth above nominal GDP.** Nothing outgrows its economy forever.
4. **Book-value weights in WACC.** Use market cap and market value of debt.
5. **Ignoring working capital.** `FCFF = NOPAT − net capex − ΔWC`. Omitting ΔWC overstates FCF,
   worst for fast growers.
6. **Circular WACC.** Market-value weights depend on value, which depends on WACC. Use Excel
   iteration or a target capital structure.
7. **Constant margins.** A flat margin from Y1 to Y10 is lazy and almost always wrong. Model a
   justified trajectory.

## D7 — Model integrity check (run before finalizing)

Verify and report failures as **ACTION REQUIRED**:
1. FCFF vs FCFE consistency — state the method and confirm the discount rate matches.
2. Reinvestment rate = growth / ROIC each year; show implied ROIC per year; flag economically
   impossible years.
3. Terminal: reinvestment = g / terminal ROIC; terminal ROIC vs WACC justified by the moat work;
   g ≤ nominal GDP.
4. WACC: market-value weights, bottom-up beta, current implied ERP.
5. ΔWC included every year and tracking realistically with revenue growth.
6. Margin trajectory justified year by year against the story.
7. Terminal value as % of EV; if > 75%, extend the forecast or explain.
