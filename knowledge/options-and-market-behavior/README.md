# Options and Market Behavior — knowledge base index

domain_id: README | last_updated: 2026-10-14 | status: reviewed
scope: entry point and map for the options-and-market-behavior knowledge base used as long-term memory by AI sessions in this repository
confidence_notes: every domain file is source-cited and was adversarially fact-checked; numbers are only as current as the "as of" date beside them, and anything tagged `[uncertain]` must be re-verified before use

## How to use this knowledge base

1. Read `00-overview-and-mental-models.md` first. It holds the canonical id map,
   the core mental models, the cross-domain dependency map, the "single source
   of truth" table that says which file owns each recurring number, the top
   misconceptions, and reading orders for different kinds of task.
2. Open only the domain files the task needs (each is 8,000 to 12,000 words;
   the whole base is about 150,000 words and must not be loaded at once).
3. Use `glossary.md` to resolve a term or ticker to its definition and owner file.
4. Tag conventions inside the files: `[uncertain]` marks a claim that could not be
   verified against a primary source; `as of <date>` marks a recency-sensitive
   number; "Contested or uncertain claims" sections record where sources or
   reviewers disagreed and how it was resolved.

## Governance

This repository is the NME-001 research-governance record. The knowledge base
contains **no licensed market data, no raw price series, and no SPY-specific
prior-session high/low reaction statistics** (the experiment's sealed hypothesis;
historical-final window 2022-06-22 through 2024-12-31). Key-level and
support/resistance material cites general published literature only. Every
file states this exclusion explicitly, and both the consistency audit and the
per-file extracts checked it. See the root `CLAUDE.md` for the full rule set.

## Files

| File | Domain | Audit rating |
|---|---|---|
| `00-overview-and-mental-models.md` | Entry point: canonical id map, 15 core mental models, dependency map, single-source-of-truth table, 0DTE map, 24 misconceptions, 31 numbers worth remembering, open questions, reading orders | — |
| `glossary.md` | 297 terms and tickers in 11 groups with precise definitions, key numbers and owner-file pointers | — |
| `01-options-fundamentals.md` | Contracts, moneyness, exercise styles, AM vs PM settlement (SET, VRO), expiration calendar, SPX vs SPXW vs XSP vs SPY vs ES, OCC exercise/assignment chain, early exercise, corporate actions, strike and tick rules, OSI symbology, position limits, FLEX | strong |
| `02-pricing-theory.md` | Put-call parity, bounds, box spreads, binomial, Black-Scholes-Merton and Black-76 with worked numbers, discrete dividends, American pricing, implied-vol solvers, Breeden-Litzenberger, static-arbitrage constraints, SVI/SSVI, Dupire, Heston, SABR, jumps, rough vol, variance-swap replication and the exact VIX formula, numerics | strong |
| `03-greeks-and-hedging.md` | Closed-form first- and second-order Greeks, behavior across moneyness and time, delta-hedging P&L decomposition, gamma scalping, discrete-hedging error, sticky-strike vs sticky-delta, portfolio Greeks, spread Greeks | strong |
| `04-volatility.md` | Realized-vol estimators, GARCH/HAR, expected move, variance risk premium and its term and strike structure, skew and skew-stickiness, VIX family methodology (VIX, VIX1D, VIX9D, VIX3M, VVIX, SKEW), VIX futures and ETPs, vol regimes with base rates recomputed from Cboe data, event vol | strong |
| `05-dealer-positioning-and-option-flows.md` | Market-maker hedging, gamma exposure and its sign-assumption limits, vanna and charm flows, pinning evidence, expiration-calendar effects, JPM collar and other systematic flows, leveraged-ETF rebalancing, 0DTE hedging literature, gamma squeezes, what is established vs folklore | strong |
| `06-market-microstructure-and-intraday-behavior.md` | Order books, spread components, impact, opening and closing auctions (MOC/LOC timelines), LULD and circuit breakers, Reg NMS status, PFOF, ETF arbitrage and SPY/ES lead-lag, 23x5 trading status, intraday regularities, overnight vs intraday returns, key-level mechanics (general literature), calendar conventions | strong |
| `07-strategies-and-position-management.md` | Every standard structure with payoff and Greek profile, when each fits, management and rolling rules, assignment and pin risk, Reg T and portfolio margin, SPAN, US tax treatment, Cboe benchmark indices | adequate |
| `08-empirical-literature-and-known-regularities.md` | Option-return puzzle, variance and skew premia, demand-based pricing, option-implied return predictors with magnitudes and sample periods, earnings, retail and 0DTE evidence, dealer-hedging effect sizes, anomaly decay and multiple testing | strong |
| `09-market-structure-regulation-and-plumbing.md` | The 20 US options exchanges and market models, OPRA, OCC and STANS, SEC vs CFTC, FINRA rules and the 2026 pattern-day-trader replacement, margin, hours by product, linkage, PFOF, prediction markets, international venues, volume records | strong |
| `10-historical-episodes-and-regimes.md` | 1987 through 2026 episodes with a uniform template (what moved, who was forced, what broke, lesson), fund blowups, VIX spike-decay and inversion base rates, regime diagnosis | strong |
| `11-current-landscape-2025-2026.md` | Volumes and 0DTE share series, new products and expirations, rule changes, 23x5, prediction markets, crypto options, macro and vol levels as of October 2026; refresh monthly | adequate |
| `12-data-tooling-and-research-methodology.md` | Data vendors and their pitfalls, calendar and bar conventions, IV-convention locks, backtest design, purged cross-validation, multiple-testing control, probability-forecast scoring (Brier, calibration, Clopper-Pearson), software stack | strong |
| `13-risk-management-and-behavioral.md` | Fat tails, stress matrices, sizing (Kelly, buying power), drawdown math, tail-hedge economics, short-vol blowups, operational risk, behavioral biases and retail P&L evidence, kill-switch rules | strong |

## How it was built (provenance)

Built 2026-10-14 by orchestrated agents with web access to primary sources
(Cboe, OCC, SEC, CFTC, FINRA, Federal Register, CME, FRED, peer-reviewed papers).
Pipeline per domain: one researcher wrote the file against a detailed brief;
two independent critics (factual accuracy; practitioner completeness) each
raised 10 to 27 substantiated issues; one reviser applied them, rejecting only
with primary-source evidence and recording rejections in the file. Then a
compact fact extract of every file fed a cross-file consistency audit (27
inconsistencies found and corrected with 46 edits, several verified by
recomputation from Cboe's published VIX history) and a coverage audit, whose
synthesis guidance produced the overview and glossary, each fact-checked
against the domain files and revised. Draft-stage versions and audit records
are not kept in the repository.

## Maintenance convention

- When a session learns something durable (a verified number, a corrected
  claim, a new product or rule), append it to the owner file under the right
  section with a source and date, bump `last_updated`, and add a line to that
  file's changelog note in its header block.
- Recurring numbers have one owner file (table in the overview); other files
  cite the owner rather than restating the number.
- `11-current-landscape-2025-2026.md` is time-sensitive by design and should
  be refreshed monthly from OCC and Cboe releases.

## Known gaps (identified by the coverage audit, not yet written)

Six domain ids are reserved for files that several existing files point to but
nobody owns. A future session with budget should research them with the same
research, critique, revise pipeline:

| Reserved id | Scope |
|---|---|
| `14-scheduled-events-earnings-and-macro-calendar` | Earnings, macro releases, elections; how options price scheduled events; single-name earnings behavior |
| `15-options-on-futures-and-cross-asset-options` | ES/CME option mechanics and SPAN margin; rates, FX, commodity and crypto option conventions |
| `16-systematic-volatility-strategies-and-relative-value` | Professional vol books: dispersion, skew and forward-vol trades, VIX basis, cross-asset vol carry, overlay mandates |
| `17-options-execution-and-order-handling` | Quote formation, order types, complex orders, price-improvement auctions, how to actually get filled |
| `18-exotics-structured-products-and-embedded-option-flows` | Autocallables, buffer ETFs, variable-annuity hedging, QIS indices as structural vol suppliers; exotic pricing basics |
| `19-technical-levels-and-reference-price-literature` | Order clustering, round numbers, prior-session extremes: the general evidence base only, governance-safe (no SPY statistics) |

In-place expansions the audit recommended (one line each): ES/MES fine points
and Section 1256 reasoning (01); a practical surface-fitting pipeline (02);
Greeks of VIX and futures-style products and multi-expiry P&L explain (03);
single-name surfaces and implied-correlation construction (04); a worked
dealer-positioning estimate from open-close data (05); options microstructure
and deeper key-level literature (06); execution and rolling mechanics with
benchmark construction (07); post-2015 replication table and machine-learning
option-return literature (08); CME options on futures and international venue
detail (09); cross-asset and crypto episodes (10); Europe/UK/Asia section and
AUM verification (11); machine learning and backtest-engine design (12);
liquidity-risk quantification by regime and model-risk governance (13).
