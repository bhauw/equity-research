# Excel Model Structure — 9 Tabs

Build in order; each tab feeds the next. Use the `xlsx-author` skill to produce the file.

| Tab | Content |
|---|---|
| 0_Dashboard | Archetype, quality classification, all 8 lens verdicts, IRR, margin of safety, final recommendation |
| 1_Raw_Data | 5-year + TTM income statement, cash flow, balance sheet — raw figures |
| 2_Derived_Metrics | ROIC, ROE, FCF conversion, DuPont table, ROIC−WACC spread, all ratios |
| 3_DCF_Model | 10-year projection, WACC inputs, terminal value, equity value per share |
| 4_Sensitivity | Terminal-growth rows × WACC columns → intrinsic value per share |
| 5_Scenarios | Bear / Base / Bull with explicit assumption changes and resulting valuations |
| 6_Monte_Carlo | CDF table, histogram bin data, tornado data, probability metrics |
| 7_Comps | Peer comparison: EV/EBITDA, EV/FCF, P/E, ROIC, gross margin, EBIT margin |
| 8_Monitoring | Key variables, thesis-break conditions, dated quarterly update log |

## Tab 3 — DCF column structure

| Column | Formula |
|---|---|
| Year | 1 … 10 |
| Revenue ($M) | Prior × (1 + growth) |
| Revenue growth | Explicit and justified each year |
| EBIT margin | From the margin trajectory (stable / expanding / mean-reverting) |
| EBIT ($M) | Revenue × EBIT margin |
| NOPAT ($M) | EBIT × (1 − effective tax rate) |
| Reinvestment rate | Growth ÷ ROIC |
| Reinvestment ($M) | NOPAT × reinvestment rate |
| FCFF ($M) | NOPAT − reinvestment |
| Discount factor | 1 ÷ (1 + WACC)^Year |
| PV of FCFF | FCFF × discount factor |
| Terminal value (Y10) | FCFF₁₁ ÷ (WACC − g) |
| PV of terminal value | TV × Year-10 discount factor |
| Enterprise value | Σ PV(FCFF) + PV(TV) |
| Equity value / share | (EV − net debt) ÷ diluted shares |

## Tab 6 — Monte Carlo charting

- CDF: percentile → intrinsic value in columns A/B → line chart. Add a vertical reference line at
  the current price via a secondary series (X = price, Y = 0 to 1).
- Histogram: bin midpoints in A, frequency % in B. If generating yourself:
  `NORM.DIST(x, mean, sd, FALSE) × bin_width × n_simulations`.
- Tornado: horizontal bar chart sorted by absolute valuation impact; positive and negative bars in
  different colors.

Ask for paste-ready tables: "histogram bin midpoints and frequency % for 15 equal-width bins
between $[5th pct] and $[95th pct] assuming N(μ, σ)".
