# Options and Market Behavior — knowledge base index (checkpoint)

Status: **checkpoint commit, work in progress** (2026-10-14). Thirteen domain
files have been researched by parallel agents and adversarially fact-checked
by two independent critics each. Files marked `status: reviewed` in their
header have had the critiques applied; files marked `status: draft` have not
yet. A cross-file consistency audit, coverage audit, overview document and
glossary are planned but not yet done. Treat every number as "as of the date
stated next to it" and re-verify anything tagged `[uncertain]`.

Governance: this knowledge base contains no licensed market data, no raw
price series, and no SPY-specific prior-session high/low reaction
statistics (the NME-001 experiment's sealed hypothesis). See the root
`CLAUDE.md`.

| File | Domain |
|---|---|
| `01-options-fundamentals.md` | Contracts, exercise/assignment, settlement (AM/PM, SET/VRO), expiration cycles, SPX vs SPY vs ES, OCC mechanics, symbology |
| `02-pricing-theory.md` | Put-call parity, binomial, Black-Scholes-Merton, Black-76, American pricing, implied vol, Breeden-Litzenberger, SVI/SSVI, local/stochastic/rough vol, jumps, variance-swap replication, numerics |
| `03-greeks-and-hedging.md` | First- and higher-order Greeks with closed forms, delta-hedging P&L, gamma scalping, discrete-hedging error, sticky-strike/delta, portfolio Greeks |
| `04-volatility.md` | Realized-vol estimators, GARCH/HAR, implied vol, variance risk premium, skew, term structure, VIX methodology and products, VIX ETPs, VVIX, event vol, vol regimes |
| `05-dealer-positioning-and-option-flows.md` | Market-maker hedging, gamma exposure (GEX) and its limits, vanna/charm, pinning, expiration calendar effects, JPM collar and other systematic flows, 0DTE literature, gamma squeezes |
| `06-market-microstructure-and-intraday-behavior.md` | Order books, spreads, impact, auctions (open/close, MOC/LOC), LULD/MWCB, Reg NMS, PFOF, ETF arbitrage (SPY/ES), overnight vs intraday, intraday momentum, key-level mechanics, calendar conventions |
| `07-strategies-and-position-management.md` | Every standard strategy with payoff/Greek profile, management rules, assignment and pin risk, margin (Reg T, portfolio margin, SPAN), US tax treatment, Cboe benchmark indices |
| `08-empirical-literature-and-known-regularities.md` | Option-return puzzle, variance/skew premia, demand-based pricing, option-implied predictors, earnings, retail and 0DTE evidence, anomaly decay, multiple testing |
| `09-market-structure-regulation-and-plumbing.md` | Exchanges and market shares, OPRA, OCC, SEC/CFTC, FINRA rules, margin, trading hours, linkage, PFOF, prediction markets, international venues, volume records |
| `10-historical-episodes-and-regimes.md` | 1987 through 2026: crashes, vol spikes, squeezes and fund blowups, with mechanisms and lessons |
| `11-current-landscape-2025-2026.md` | Volumes, 0DTE share, new products and rules, 23x5 trading, prediction markets, macro and vol levels as of October 2026 |
| `12-data-tooling-and-research-methodology.md` | Data vendors and pitfalls, calendars and bar conventions, backtest design, multiple-testing control, probability-forecast scoring (Brier, calibration), software stack |
| `13-risk-management-and-behavioral.md` | Fat tails, stress matrices, sizing (Kelly, buying power), tail hedging economics, short-vol blowups, behavioural biases and retail P&L evidence |
