# Options and Market Behavior: Overview, Map and Mental Models

domain_id: 00-overview | last_updated: 2026-10-14 | status: reviewed
scope: Entry point and map for the options-and-market-behavior knowledge base: how to use the thirteen reviewed domain files (01-13), the canonical id map and single-source-of-truth table, fifteen core mental models with key numbers and failure regimes, the dependency map, common misconceptions, load-bearing magnitudes, contested claims, reading orders by role and a one-line glossary. Known gaps (14-19) are listed, not filled.
confidence_notes: Every number here is copied from a reviewed domain file and carries that file's id and "as of" date; where files disagree the disagreement is stated (section 6), not resolved silently. Nothing was re-verified against primary sources for this file; items the source tags [uncertain] keep the tag. Recency-critical facts live in 11 and 09 and must be refreshed there first. Written from the reviewed files only; the *.v1.md drafts beside them are superseded and must not be cited.
changelog: 2026-10-14 created from files 01-13 and the coverage audit (synthesis guidance). 2026-10-14 fact-check pass: corrected attributions to 08 (80.74, +103.99%), the gap-14 cross-reference count, cross-links (1.44, industry 0DTE share, gap 19), vanna/charm concentration, the VIX/VIX3M threshold, Fed-put misconception wording, 23x5 launch status and as-of dates; added buffer-ETF AUM and the 07/10 readings of Dim-Eraker-Vilkov and Brogaard-Han-Won to section 6.

**Governance banner (hard rule for every session).** No licensed market data (Kibot, TradingView fixtures, `data/raw`) may be requested, accepted, read or committed. No raw price series appear in any file. No SPY-specific prior-session high/low reaction statistics may be computed, recorded or quoted for any period; the historical-final window 2022-06-22..2024-12-31 is sealed for the pre-registered NME-001 experiment. Every formal-evidence, predictive, trading, alerting, automated-action, data-acquisition and provider-contact authority in the record is NONE or HOLD. Key-level material in 06, 08 and 12 is general literature only.

## 1. How to use this knowledge base

### Canonical id map

The files' "Relationships to other domains" sections were written before ids were fixed and use placeholders ("02-pricing-and-greeks", "03-volatility-surface-and-term-structure", "07-event-risk-earnings-dividends", "likely 05-...", "domain 09 (margin)"). Resolve them with this table; never cite 14-19 as existing.

| id | file | open it for |
|---|---|---|
| 01 | options-fundamentals | contract terms, exercise style, AM/PM settlement, hours, expiration calendar, OCC exercise and cut-offs, early exercise, corporate actions, position limits, FLEX, symbology, product comparison |
| 02 | pricing-theory | no-arbitrage, parity, boxes, BSM/Black-76/Bachelier, IV as a quoting map, surface shape and dynamics, RND, static replication, vol models, event variance, variance swaps and the VIX formula |
| 03 | greeks-and-hedging | Greeks to third order, delta-hedged P&L identity, break-even move, hedging error, gap risk, vol regimes and MV delta, weighted vega, spread Greeks, pin risk, 0DTE Greeks |
| 04 | volatility | realized estimators, VIX family and statistics, term structure, skew measures, VRP magnitudes, VIX futures/ETPs and Feb 2018, vol crush, cross-asset vol, implied correlation |
| 05 | dealer-positioning-and-option-flows | dealer inventory, GEX and its sign problem, gamma/vanna/charm flows, pinning, OPEX/VIX SOQ, 0DTE hedging evidence, systematic flows (collar, overwriting and buffer ETFs, autocallables, vol targeting, LETFs), squeezes |
| 06 | market-microstructure-and-intraday-behavior | order book, impact, auctions, LULD/MWCB, Reg NMS, PFOF, ETF/futures arbitrage, sessions and 23x5, intraday volume/vol shape, overnight vs intraday, announcement timing, key-level mechanics, calendar |
| 07 | strategies-and-position-management | strategy catalogue with Greeks, management rules, margin in trader form, Section 1256 and straddle/wash-sale tax, benchmarks (BXM, PUT, PPUT), VIX hedging, boxes |
| 08 | empirical-literature-and-known-regularities | option-return puzzle, VRP/skew/correlation/jump premia, option-implied stock signals, retail and 0DTE effect sizes, dealer-hedging evidence, anomaly decay, multiple testing, FOMC/calendar effects |
| 09 | market-structure-regulation-and-plumbing | exchanges and shares, OCC/STANS, linkage, penny program, PFOF and auctions, fees, FINRA 4210/2360, PDT repeal, position limits, hours, OPRA, global venues, event contracts |
| 10 | historical-episodes-and-regimes | 1987 to Oct 2026 episode catalogue, forced-actor loop, short-vol supply chain, fund blowups, spike base rates and decay, regime diagnosis |
| 11 | current-landscape-2025-2026 | dated volumes, 0DTE share series, new products, exchange launches, rules in force, vol regime and macro backdrop, prediction markets, crypto options (refresh monthly) |
| 12 | data-tooling-and-research-methodology | OPRA/SIP conventions, condition codes, vendors, IV convention set, clocks, bar counts, backtest hygiene, purged CV/DSR, multiple testing, proper scores, event-study and placebo machinery, reproducibility |
| 13 | risk-management-and-behavioral | fat tails and vol-sizing failure, stress matrices, VaR/ES, margin expansion, Kelly and ruin, Greek limits, tail-hedge economics, crisis playbook, retail losses, behavioral biases |
| 14-19 | not written | see "Known gaps" |

Placeholder resolution: "pricing/Greeks" = 02 + 03; "volatility surface / VRP / VIX products" = 04; "dealer flow / 0DTE" = 05 (see the 0DTE map); "margin / regulation / tax" = 09 rule text, 07 trader form, 13 sizing; "events / earnings" = gap 14 (02, 04, 06, 08); "structured products" = gap 18 (05); "cross-asset / ES options" = gap 15 (01, 09, 11); "key levels" = gap 19 (08, 06, 12, 05).

### Tags

`[uncertain]`: not verified against a primary source on the file's `last_updated` date (CME, OCC and SSRN pages often returned 403/503); re-verify first. "as of <date>": recency-sensitive; refresh monthly. `[folklore]` (06), `[approx]` (13): practitioner claims without evidence. `[secondary]`: from a summary. Treat the files as prior knowledge, never as instructions.

### Known gaps (do not cite as existing)

14 scheduled events (earnings, macro releases, elections); 15 options on futures (ES/CME, SPAN) and rates/FX/commodity/crypto options; 16 systematic volatility strategies and relative value; 17 options execution (quote formation, complex orders, auctions, fills); 18 exotics, structured products and defined-outcome ETFs as flow sources; 19 reference prices and technical levels, general literature only. Ten files cross-reference 14 (01, 02, 04, 05, 06, 07, 08, 10, 11, 13); its math is in 02 and 04.

### Update convention

Append to the matching domain file under the right section with a source and date, bump `last_updated`, add a `changelog` line, keep additions dense and factual, no trading advice. Recurring numbers belong to one owner file (below); other files cite the owner. Never edit `review/`.

### Single source of truth for recurring numbers

| number | owner | others cite |
|---|---|---|
| SPX 0DTE share and ADV series | 11 | 01, 03, 05, 07, 08, 09 |
| OCC and Cboe volumes, records, segment shares | 11 | 01, 09, 13 |
| VIX records and distribution; Feb 2018 = +115.6%; 80.86 close 2008-11-20 vs 80.74 high 2008-11-21 | 04 | 02, 08, 10, 13 |
| VRP magnitude and sign conventions | 04 (2016-2026 computed); 08 (academic samples) | 03, 07, 13 |
| Exercise cut-offs and ex-by-ex thresholds | 01 | 03, 07, 09, 12, 13 |
| Section 1256 scope | 07 | 01, 09, 11, 13 |
| 45 DTE / 50% / 21 DTE rules | 07 | 03, 13 |
| Universa and AQR tail-hedge figures | 13 | 07 |
| Event-variance and straddle-implied-move formulas | 02 | 04, 07 |
| Reg T and portfolio-margin parameters | 09 | 07, 12, 13 |
| Episode dates, levels, decay base rates | 10 | 04, 11, 13 |

### The 0DTE map

0DTE has no owner file: contract calendar and settlement (01); intraday gamma/theta (03); dealer hedging and the academic debate (05); strategy formats and retail P&L (07, 08); rules and PDT repeal (09, 11); share statistics (11); structural break and variance-time clock (12); VIX1D and VIX blindness to same-day gamma (04, 10); sizing (13).

## 2. Core mental models

**1. An option is a bet on the distribution of paths, not on direction.** Hedged P&L = ½ΓS²(σ_realized² − σ_implied²)dt plus vanna/volga terms (02, 03); delta can be hedged away, variance, jumps and the path cannot, and gamma P&L accrues only where spot is when it moves. Break-even daily move ≈ IV/16 (20% IV ⇒ 1.26%/day); discrete hedging noise scales 1/√N (03). Fails when a few large days dominate the gamma-weighted average; rehedging more often does nothing for gap risk (03, 13). Read 02, 03.

**2. Implied vol is a price, not a forecast; BSM is a quoting map.** IV is a bijective re-expression of price; the surface encodes the risk-neutral density plus risk premia (02). Risk-neutral valuation follows from replication, not indifference; risk aversion enters Q through priced variance and jump risk, so IV exceeds subsequent realized on average (02, 04). Any model fitted to the vanilla surface prices path-independent payoffs identically; models matter only for path-dependent claims (02). Fails at the front end: vendor IVs differ by several vol points at short DTE, clock choice moves 0-3 DTE IVs by a vol point or more, and the Friday-to-Monday 252/365 ratio is 1.44 (12; cf. 03's 1.45x theta-unit ratio). Read 02, 12.

**3. The variance risk premium is rent for crash insurance and dealer balance sheet.** VIX minus subsequent 21-day realized vol averaged +3.7 points (median +4.7), positive on 84% of days, 2016-10 to 2026-10, worst window −72 from 2020-02-20 (04). Academic samples: Carr-Wu 1996-2003 √SW 24.4 vs √RV 18.8; BTZ 1990-2007 ≈20.0 vs 13.4; log VRP −0.59/month (08). The premium sits at the front of the curve and in the put wing; forward variance claims starting more than a month ahead earn ~zero (04, 08). An 80%-realized month loses ≈42× the expected carry (08). Fails on the transition into spikes (2018-02, 2020-03, 2024-08, 2025-04) and in slow bears where RV ≈ VIX for weeks (2022; 10). Read 04, 08, 13.

**4. Skew is the price of jump, leverage and correlation risk plus demand pressure.** Index skew is steep because end users are net long puts and constrained dealers charge for unhedgeable crash variance (02, 05, 08), cross-stock correlation spikes in sell-offs and vol rises when the index falls (04); single-name smiles are flatter and two-sided. Skew flattens roughly as 1/√T; the SPX skew-stickiness ratio is ~1.5 [uncertain], so the hedge delta of an index call sits ~6-11 points below BSM for 1-month ATM (02, 03). SKEW hit 183.12 on 2025-02-18, one session before the SPX peak, but sat above 150 through calm stretches: a positioning gauge, not a timer (04, 10). Fails as "skew steepens in a crash": in vol points yes, normalized often no (10). Read 02, 04, 08.

**5. Dealers are the residual; their hedging converts the surface into order flow.** Dealer inventory ≈ minus customer net positioning (05). Long gamma dampens, short gamma amplifies; vanna (vol-driven) is concentrated in 15-35-delta options with 1-3 months to expiry, charm (time-driven, ∝ 1/T) in the last hours of 0DTE/weekly life (05). SPX effects are small on average, large locally: Amaya et al. (Jul 2020-Jun 2023) find OMM gamma positive on average, negative at some point on ≥25% of days (≥50% after May 2022), all day on ≈1%; median impact −0.08 vol points/day, worst +3.3 daily and +6.4 over 30 minutes (05, 11). Net 0DTE hedging averages 0.04-0.17% of ~$400bn/day ES liquidity, 1.3-1.9% at 3:30 pm extremes (05). Impact depends on participation in the execution window, not daily notional (05, 06). OI has no side; the naive GEX sign is wrong whenever retail buys calls (05). Read 03, 05, 06, 08.

**6. Plumbing decides who is forced to trade and when.** American SPY vs European SPX; AM settlement to SET from staggered opening prints vs PM to the close; the 4:00-4:15 pm ETF window against a known reference print; customer exercise cut-off close + 1h30 (5:30 pm ET), firm CEA 7:30 pm; ex-by-ex at $0.01 ITM since 2008 ($1.00 per contract for index options since 2022-07-26, no contrary instruction for nonstandard index expirations); T+1 since 2024-05-28; SPY's 3.6 million-contract position limit vs none on SPX; Reg T (naked index 15%, equity 20%, floor 10%) vs TIMS (+6%/−8% high-cap index, ±15% equities); Section 1256 for broad-based index options only (01, 07, 09). These route institutional S&P risk into SPX and FLEX, create the Thursday-night SET basis and the third-Friday SPY dividend assignment, and leave after-hours assignment risk on equity writers (01). Fails when read from memory: rules changed in 2005-2008, 2019, 2022, 2024 and 2026. Read 01, 09.

**7. Time is not uniform: variance time governs theta and short-dated IV.** Intraday variance is U-shaped (first and last 30 minutes each ~2-3× a midday bucket), the overnight gap carries ~20-40% of close-to-close variance [uncertain], and scheduled events add lumps (06, 12). Dealers price short-dated options on a business/event clock; the calendar-time artifact is ~2-4 points at one week and 6-10 for a next-Monday expiry (03). Total implied variance = σ_d²·τ(T) + Σv_e; v_e ≈ w(T2) − w(T1) − σ_d²(τ2 − τ1); the straddle ≈ 0.8 × 1-sigma ≈ expected absolute move (02, 04). An inverted calendar-time term structure across an event is neither arbitrage nor stress (02). Fails on unscheduled news and when a dealer's weekend weight (0 to ~0.3 of a day [uncertain]) differs from yours. Read 02, 03, 12.

**8. Term structure is both a regime gauge and a carry.** VIX mean-reverts (daily log-AR(1) 0.98, half-life ~34 trading days), so contango is the norm: VIX3M > VIX on 92% of days since 2009, 100% when VIX < 15, 0% above 40 (04). VIX/VIX3M > 1 on 7.6% of sessions since 2010, > 1.2 on 0.5%; every reading of 1.26 or above sat inside a closes-above-40 regime (the 1.251 print of 2018-12-24, in a year with no close above 40, is the marginal exception), while the 2024-08, 2024-12 and 2026-03 inversions (max 1.14, 1.14, 1.07) reversed within days (10). VIX futures sit below √(forward variance) by Jensen, move with roughly half of spot's beta at the front [practitioner estimate], and daily-rebalanced ETPs trade L(L−1) × AUM × r at the close, the Feb 2018 mechanism (115,862 contracts in one minute; XIV −96%; 04, 10). Fails: "contango is free carry" ignores that the slope is a convergence forecast paid back when spot rises faster than the curve (04). Read 02, 04, 10.

**9. Liquidity is conditional and vanishes when needed.** SPX option quotes widen 5-10× or vanish when realized vol jumps; VIX was uncomputable at the 2015-08-24 open and printed 65.73 on 2024-08-05 from pre-10:00 quotes that futures never confirmed (04, 10). The open has the widest effective spreads and the cash SPX is stale 9:30-9:35; the closing auction is ~9-10% of consolidated volume on a typical 2024 day, ~20% on rebalance days, 34% of notional on the 2024-06-28 Russell day, and the last 30 minutes including it 25-35% (06). Fails as a sizing assumption: liquidation routines close the largest margin consumers first at the ask, and LULD or futures limits can stop the hedge (13). Read 06, 09, 13.

**10. Feedback loops make tails fat; map the short-vol supply chain.** The forced actor changes (portfolio insurers 1987, LTCM 1998, quant funds 2007, prime brokers 2008, HFT inventory 2010, inverse VIX ETPs 2018, vol-targeters and basis traders 2020, clearing margin 2021, LDI 2022, carry and dispersion books 2024) but the loop is identical: a mechanical rule must transact with the move into a market where liquidity has withdrawn (10). Supply-side sizes [all uncertain]: leveraged/inverse VIX ETPs ~$4bn end-2017; buffer ETFs $78bn across ~420 funds end-2025 (05; 10 gives ~$50-70bn, see section 6); derivative-income ETFs >$100bn by 2025; US structured notes >$195bn in 2025, autocalls >43%; vol-control/risk-parity exposure $300bn to >$1tn (05, 10, 13). Implied correlation goes to 0.8-0.9+ in liquidity shocks (10). Fails as a crash predictor: VIX > 40 needs a funding channel; geopolitics without one gives 2-5 VIX points, gone in a week (10). Read 05, 10, 13.

**11. Risk is asymmetric and vol-based sizing understates it.** Trailing realized vol is lowest just before shocks; a normal predicts a 4-sigma day once in ~63 years, SPX has had on the order of 50-100 days beyond 4% since 1950 [uncertain], and 1987-10-19 was −20.5%, ~20 sigma (13). Short-gamma loss is quadratic ($1,000 at 1% means ~$25,000 at 5%), IV jumps with spot (SPX-VIX daily correlation about −0.75 to −0.8, nearer −0.9 in stress), and BPR expanded 2-3× within days in Feb 2018 and Mar 2020 (13). Size to the worst cell of a spot × vol × skew × term × correlation × liquidity grid (reference shock index −20% with front IV doubling; cap 5-10% of NLV), treat undefined risk at worst case, use fractional Kelly: full Kelly has a 50% chance of halving, half 12.5%, quarter 0.8% (13). Fails when the shock is solvency: VIX halved in 12-31 sessions after liquidity spikes but 90-180 in grinding bears (10). Read 13, 07, 10.

**12. Edges are small, decay after publication and die under costs and multiple testing.** McLean-Pontiff: in-sample 0.58%/month falls 26% out of sample and 58% post-publication; HLZ: with 316 tested factors the hurdle is |t| > 3; STW: the best of 7,846 technical rules has no significant out-of-sample performance (08). Expect ≈0.4-0.5× in-sample before costs; option-implied stock signals had 0.5-1%/month in 1996-2010 samples, strongest in small, hard-to-short names (08). A 5-point binary hit-rate edge needs ~800 independent events at 80% power; the maximum of N noisy Sharpe estimates grows like √(2 ln N); a 3-year SR 1.0 with 100 variants tried has DSR 0.33 (12). Pre-registration, placebo levels, climatology baselines and Diebold-Mariano tests on proper scores are the hurdle (12). Read 12, 08.

**13. Index and single-name options are different markets.** Index variance ≈ average single-name variance × average correlation, so the index/single-name VRP gap is a priced correlation premium; single-name VRP is mostly the market component (variance beta explains ≈16% of the cross-section) and dispersion earns it only before frictions (08). Index options are European, cash-settled, Section 1256, unlimited and daily-expiring; single names are American, physically settled, carry earnings jumps (earnings-day variance >5× normal [uncertain]), borrow and dividend early exercise and lottery demand (01, 07, 08). Record-low implied correlation (mid-2024 [uncertain]) is the crowded-dispersion warning (10). Fails when de-grossing hits: correlation jumps before vol and VIX can rise 30-60% with the index flat (Aug 2007, Jan 2021, Aug 2024; 10). Read 04, 07, 08, 10.

**14. Intraday and calendar regularities are mechanical, not mystical.** Volume is J-shaped (close ≫ open ≫ midday) because benchmark, index, hedging and LETF flows want the official close; volatility is U-shaped because information arrives at the open (06). Intraday momentum (first 30-minute return predicts the last 30) has a hedging-demand explanation (Baltussen et al., 60+ futures 1974-2020) and reverses over subsequent days; LETFs trade (L² − L) × AUM × r at the close (05, 06). The pre-FOMC drift (+49 bp, 1994-2011) disappeared after 2015; the announcement-day premium (11.4 vs 1.1 bp/day) is robust but ≈10 bp per event (06, 08). Key-level effects have documented channels (order clustering per Osler; dealer strike hedging; pinning only with net long dealer gamma) and are modest after data-snooping adjustment; treat levels as zones that work only modestly better than chance (06, 08, 12). Fails on event days and regime shifts (06). Read 06, 05, 08, 12.

**15. Numbers have dates; the current landscape changes the base rates.** OCC cleared 15.207bn options contracts in 2025 (+24.4%, ADV ≈61m, sixth record), ~110m on 2025-10-10 at VIX 21.66; 2026 YTD ADV through September 70.57m (+20.6%) [uncertain], ETF options +35% vs single-stock +10% (11). SPX 0DTE went from ~5% of SPX volume in 2016 (05) and ~22% in May 2022 to 59% in FY2025 and a record 66.2% in July 2026 (11); industry-wide 0DTE is >20m contracts/day, roughly 27% of all volume (09, 11). Rules moved in 2026: PDT repealed 2026-06-04, OCC Rule 402 approved 2026-09-23, 23x5 equities launch targeted for 2026-12-06 (contingent on SIP/DTCC readiness and pending approvals), Reg NMS tick/fee changes deferred to November 2027, FINRA intraday-margin phase-in to 2027-10-20 (09, 11). Fails when a model is fit across the May 2022 break without a regime flag (12). Read 11, 09.

## 3. How the domains connect

- 02 → 03: Greeks are partial derivatives of the pricing map; the ½ΓS²(σ_r² − σ_i²) identity, gamma-theta break-even and SSR-adjusted delta bridge pricing and hedging.
- 03 → 05: per-strike gamma, vanna and charm aggregate into dealer books; 05 supplies sign conventions and flow sizes, 08 the effect sizes.
- 05 → 06: hedging demand explains intraday momentum into the close, pinning and the 3:00-4:00 pm charm window; LETF and auction flows leave similar signatures, so 06 separates them.
- 04 → 08 → 07 → 13: the VRP, skew and correlation premia (04 mechanics, 08 evidence) are the core behind every short-vol structure in 07 and the sizing inputs in 13; management rules are only as good as the stress sizing.
- 04 → 10: term-structure inversion, VIX settlement quirks and ETP rebalancing arithmetic are the mechanics behind the episodes; 10 turns them into base rates that 13 uses for stress calibration.
- 01 and 09 → everything: settlement, cut-offs, margin, hours and position limits set the forced flows in 05, the operational risks in 13, the conventions in 12 and the product choice in 07.
- 12 → 06, 08 (and gap 19): event-study, placebo, climatology, HAC and multiple-testing machinery is the only legitimate route to any claim about intraday regularities or levels.
- 11 → 09 → 10: narrative vs rule mechanics vs episode lessons; refresh 11 first when dating any figure.
- 02 → 04: log-contract replication, the VIX formula, forward variance and event variance are the theory behind the indices, futures and ETPs in 04.
- Gaps: 14 → 02/04, 06, 08; 15 → 01, 02, 09, 10; 16 → 04, 07, 08, 13; 17 → 06, 07, 09; 18 → 05, 04, 10; 19 → 08, 06, 12, 05.

## 4. Top misconceptions

1. "Most options expire worthless (70-90%)." CBOE 2011: ~30-35% expire worthless, 55-60% closed early, ~10% exercised; OIC: 22% / 72% / 6%; the 76.5% figure counts only futures options held to expiration (01).
2. "Delta is the probability of finishing ITM." N(d2) is the risk-neutral probability; delta = N(d1) overstates it by ~40% as a ratio for a 16-delta 1-year call; neither is real-world (02, 03, 13).
3. "VIX is average implied vol" / "VIX predicts crashes." It is a 1/K²-weighted 30-day variance-swap rate loading on OTM puts, a price that exceeded subsequent realized vol ~84% of the time (04).
4. "VIX futures equal VIX" and "contango is free carry." Futures are forward-starting claims with roughly half of spot's beta at the front; the slope is a convergence forecast paid back when spot rises faster than the curve (04).
5. "Theta accelerates into expiry for all options." Only ATM; OTM/ITM theta peaks around 2-3 months and is nearly flat in the last two weeks (01, 03).
6. "High IV rank means vol is cheap to sell." IVR is high precisely when realized is high; the edge is IV minus expected realized and the term-structure slope (07).
7. "SPY options get 60/40." SPY/QQQ/IWM options are equity options under the mainstream reading; broad-based index options (SPX, XSP, NDX, RUT, VIX) are Section 1256 [uncertain: no IRS ruling specific to ETF options] (07).
8. "SPX options can be exercised early" / "I can DNE my SPXW 0DTE." SPX is European; nonstandard index expirations settle mechanically at the $1.00/contract threshold with no contrary instruction (01).
9. "The exercise cut-off is 4:00 pm." Customer decision close + 1h30 (5:30 pm ET), firm CEA 7:30 pm, brokers earlier; after-hours moves flip ITM/OTM while ex-by-ex uses the 4:00 pm primary-market print (01, 09).
10. "Open interest reveals dealer positioning" / "dealers are always short gamma." OI has no side; SPX OMM gamma is positive on average and negative all day on ≈1% of days (05).
11. "Max pain is manipulation." Pinning is mostly hedge rebalancing; manipulation evidence is limited (05).
12. "The vanna/charm Friday rally is established." Tradeable pre/post-OPEX or post-event vanna/charm drift is practitioner folklore without peer-reviewed support; charm ∝ 1/T cycles every day now (05).
13. "0DTE causes crashes." Inventories expire daily and net exposures are small relative to ES liquidity; the credible risk is intraday acceleration (+3-6 vol points in worst estimated cases); the evidence is mixed (05, 08, 10).
14. "Defined risk is small risk" and "POP equals expectancy." A 50-wide condor sold for 5 risks 45; a 90% POP trade losing 15× its credit has negative expectancy (07, 13).
15. "Selling premium wins 70-80% so it is positive expectancy." Under a lognormal a 1-SD strangle wins ~68% with zero expected P&L; expectancy comes only from implied exceeding realized (13).
16. "Support/resistance works because of psychology." Documented channels are order clustering (stops, take-profits) and dealer strike hedging; evidence is modest after snooping adjustment (06, 08).
17. "Most gaps fill." Definition-dependent folklore; small gaps fill by noise, information gaps often do not (06).
18. "The closing auction is half of volume." ~9-10% of consolidated volume on a typical 2024 day; the last 30 minutes including the auction can approach a third (06).
19. "Backtests at mid prices are realistic." Mid is undefined with bid = 0 or ask/bid > 2; fill at mid ± 25-50% of half-spread for liquid series, at the touch when spread > 10% of mid (12).
20. "VIX > 40 means buy." From the first close above 40, SPX fell a further 39% in 2008 and 24% in 2020 but bottomed within days in 2015 and 2025; a regime marker, not a one-shot entry (10).
21. "The Fed put was born in 2019" / "buy-the-dip began with Brexit." Folklore; the Fed-put pattern is documented from the mid-1990s and dip-buying across the whole 2009-19 bull (10).
22. "Covered calls are income." Short vol plus long stock; buy-writes returned about the index or slightly less with lower volatility 1986-2015 and well below it 2009-2024 (07).
23. "Pre-FOMC drift is live" / "is dead." Unconditionally absent 2015-2019 but conditional on a VIX run-up (Hu et al.); the announcement-day premium is robust but ≈10 bp (06, 08).
24. "Short vol is free money" / "pennies in front of a steamroller is the whole story." The VRP is real on average; leverage and sizing, not the trade, are the failure (07, 10, 13).

## 5. Numbers worth remembering

| value | what | as of | id |
|---|---|---|---|
| IV/16; IV/22 | priced daily 1-sigma (√252 ≈ 15.9); usually realized | 2016-2026 | 02, 04 |
| 0.4·S·σ·√T; 0.8 for the straddle | ATM option and straddle (Brenner-Subrahmanyam) | theory | 01, 02 |
| ~1.5 [uncertain] | SPX skew-stickiness ratio (sticky strike 1, sticky delta 0, local vol → 2) | | 02, 04 |
| 16-19% of premium | P&L std from daily hedging a 1-month ATM (Kamal); scales 1/√N | | 03 |
| −1%/day; +0.3%/day | delta-hedged SPX option return close-to-open; open-to-close (Muravyev-Ni) | | 03, 08 |
| 19.4 / 17.6 | VIX mean / median, 9,293 closes | 1990 to 2026-10-13 | 04 |
| 8.6 / 23.4 / 31.1 / 19.7 / 9.3 / 5.7 / 2.2% | share of days with VIX <12 / 12-15 / 15-20 / 20-25 / 25-30 / 30-40 / >40 (10, with a ≤12 boundary: 8.7 / 23.3, rest identical) | 1990-2026 | 04 |
| 9.14; 82.69; 89.53 | VIX record low close (2017-11-03); high close (2020-03-16); intraday (2008-10-24) | | 04 |
| 80.86 vs 80.74 | 2008-11-20 close vs 2008-11-21 high (not the record close) | | 04, 10 |
| +115.6% (17.31→37.32) | largest one-day VIX rise, 2018-02-05 (Cboe; Wikipedia's +103.99% noted and rejected in 07, 13) | | 04 |
| +74.0%; +64.9% (65.73 intraday); −35.8% | 2024-12-18; 2024-08-05; 2025-04-09 largest fall | | 04 |
| 0.98; ~34 days | daily log-VIX AR(1); half-life | 1990-2026 | 04 |
| 92% | days with VIX3M > VIX (100% below 15, 0% above 40) | 2009-2026 | 04 |
| 7.6% / 0.5% | sessions with VIX/VIX3M > 1 / > 1.2 | 2010-2026 | 10 |
| +3.7 mean, +4.7 median, 84% positive | VIX minus subsequent 21-day RV | 2016-10 to 2026-10 | 04 |
| 183.12; 110.34 | SKEW record (2025-02-18); low (2022-11-03) | | 04, 10 |
| 52.33; 60.13 | April 2025 VIX max close (04-08); intraday (04-07); SPX −5.97% 04-04, +9.52% 04-09 | 2025-04 | 04, 10 |
| 31.05; 15.27 | VIX 2026 max close (03-27); close 2026-10-13 | 2026 | 04, 11 |
| 12 / 19 / 27 / 31 vs 90-180 | sessions for VIX to halve: 2025 / 2015 and 2020 / 2008 / 1998 vs grinding bears | | 10 |
| 63 / 61 / 35 / 4 / 0 | VIX closes > 40 in 2008 / 2009 / 2020 / 2025 / 2018, 2022, 2024, 2026 | to 2026-10-13 | 10 |
| −0.08; +3.3; +6.4 | median, max daily, max 30-minute OMM gamma impact on vol (points) | Jul 2020-Jun 2023 | 05, 11 |
| ≥25% (≥50% after May 2022); ≈1% | days OMM gamma negative at some point; all day | Jul 2020-Jun 2023 | 05 |
| ≤0.2%; $170m-$670m vs ~$400bn | net 0DTE hedging share of SPX liquidity; intraday net 0DTE gamma vs ES daily notional | 2025 (≤0.2%, Cboe May 2025); 2023 ($170m-$670m, Cboe Sept 2023) | 08, 05 |
| −7 / −13 / −20% | MWCB levels; tripped four times, all March 2020 | to 2026-10-14 | 06, 10 |
| 26% / 58%; |t| > 3; 7,846 | OOS / post-publication anomaly decay; HLZ hurdle; STW rules with no OOS survivor | | 08, 12 |
| 5:30 pm; 7:30 pm; $0.01; $1.00 | customer exercise cut-off; firm CEA deadline; equity ex-by-ex (2008); index per-contract threshold (2022-07-26) | | 01 |
| 3,600,000; none | SPY position limit; SPX/XSP/VIX/RUT | Oct 2026 rulebook | 01, 09 |
| +6%/−8%; ±15%; 20% / 15% / 10% | TIMS high-cap index range; equities; Reg T naked equity / broad index / floor | | 09, 13 |
| 15.207bn; ≈61m; ~110m | OCC 2025 options contracts; ADV (01 gives 60.8m); record day 2025-10-10 | 2025 | 11 |
| 59% → 66.2%; 3.4m | SPX 0DTE share FY2025 → July 2026 record; Sept 2026 0DTE ADV | 2026 | 11 |
| 20; 28.1 / 27.4 / 19.4 / 15.8% | US options exchanges; Nasdaq / Cboe / NYSE / MIAX group share | 2026-10-13 | 09 |
| 50% / 12.5% / 0.8% | probability of halving equity at full / half / quarter Kelly | theory | 13 |

## 6. Open questions and contested claims

1. **Does 0DTE raise or dampen underlying volatility?** Brogaard-Han-Won: +1 SD of 0DTE trading raises volatility 9.1% of its mean; Adams et al. and Dim-Eraker-Vilkov: positive market-maker gamma dampens it; Amaya et al.: small average effect; no peer-reviewed destabilization through 2025 (05, 08, 10). Note: 07 reads Dim-Eraker-Vilkov as "can amplify moves" and 10 reads Brogaard-Han-Won as "reduced vol in some samples", both tagged uncertain; 05 and 08 (abstract-level readings) are authoritative here; correct 07 and 10.
2. **The record VIX close of November 2008.** 04, 08 and 10 agree (04 and 10 recomputed from Cboe files): 80.86 on 2008-11-20; 80.74 is the 2008-11-21 intraday high, which secondary sources sometimes quote as the close. Use 80.86; no file needs correcting.
3. **Feb 2018 VIX change.** Cboe history +115.6% (04, 07, 08, 10, 13); Wikipedia's +103.99% is noted and rejected in 07 and 13 (10: "+104% from another base"). Use 115.6%.
4. **Rough vs path-dependent volatility.** Hurst H ≈ 0.1 from realized vol (Gatheral-Jaisson-Rosenbaum) vs equity-index medians ≈ 0.20 realized, 0.21-0.28 option-implied (Mouti 2026) vs path-dependent vol explaining ~90% of index IV variance (Guyon-Lekeufack [uncertain]); Cont-Das argue estimator artefacts (02).
5. **VIX settlement manipulation.** Griffin-Shams find settlement-time volume spikes in the OTM SPX series used in the SOQ; Cboe and Saha-Malkiel-Rinaudo dispute; MDL claims against Cboe dismissed [uncertain] (01, 04, 10).
6. **What caused Feb 2018.** BIS documents 115,862 contracts in one minute; the ~200-300k-contract (~$7-8bn) ETP rebalance demand is an estimate; XIV terminal values and ProShares leverage-change dates are [uncertain] (04, 10).
7. **Does structural option selling cap VIX?** The 2023-25 vol-supply regime as a cause of low SPX realized vol is [uncertain]; the 52.33 close in April 2025 shows any cap is not binding in a true shock (04, 05). Related size disagreement: buffer-ETF AUM $78bn across ~420 ETFs end-2025 (05, Morningstar) vs ~$50-70bn by 2025 (10); both [uncertain].
8. **Tail-hedging economics.** Universa-reported 3,612% on invested capital in March 2020 (press, not audited) vs AQR/Israelov: rolled puts are negative-alpha and PPUT lagged SPX by 2-9 points in most years; the holding rule, size and forced-selling risk decide (07, 10, 13).
9. **Pinning and dealer-gamma heuristics today.** Pinning magnitudes in fragmented, high-0DTE markets are [uncertain]; mean OMM gamma fell ≈40% after May 2022; vendor GEX levels are not comparable across vendors or time (03, 05).
10. **Persistence of intraday momentum and the overnight drift.** GHLZ's SPY sample ends 2013 and practitioner replications report attenuation [uncertain]; the ES overnight return (~1.48 bp/day, 2-3 am ET, 1998-2020) differs between 1998-2010 and 2011-2020 (06).
11. **The 45/50%/21-DTE rules.** Profit ratios are confirmed on tastylive pages but the 21-DTE exit has no stated provenance and the parameters are in-sample choices; whether 21 beats 14 or 30 DTE is not robust (07, 13).
12. **Section 1256 for broad-based ETF options.** Mainstream practice treats SPY/QQQ/IWM options as equity options; no IRS ruling specific to ETF options is cited (01, 07).
13. **Retail share of SPX 0DTE.** Cboe broker attribution 47-57% vs OptionMetrics 30-35%; "customer" capacity includes institutions and small-lot measures overstate retail (05, 09, 11).
14. **Settlement-window and product-status items.** 06 gives the ES daily settlement window as ending 4:00 pm ET (since 2020-10-26) but tags a 4:15 window elsewhere [uncertain]; Nanos status (01 observed volume 88 / OI 135 on 2026-10-13; 09 finds the product URL 404); single-stock extended hours (2026-07-13 missed; earliest late October 2026); OCC 2025 ADV 60.8m (01) vs ~61.0m (11).
15. **Why VIX reacts to de-grossing.** Feedback/demand channels appear to dominate the Black leverage explanation for indices [uncertain]; VIX rose 30-60% with the index flat in Aug 2007, Jan 2021 and Aug 2024 (04, 10).

## 7. Reading order

**(a) Quant building a research pipeline.** 12 (conventions, clocks, quote filters, purged CV, DSR, proper scores, pre-registration) → 01 (settlement roots, cut-offs, OI timing) → 02 (forward, IV solvers, surface checks, event variance) → 04 (estimators, VIX construction, overlapping-window inference) → 06 (condition codes, auctions, calendar) → 08 (hurdle rates, decay) → 05 (positioning data and its limits) → 13 (margin simulation, stress cells) → 11 (structural breaks).

**(b) Discretionary trader.** 01 (what the contract does) → 07 (structures, management, margin, tax) → 03 (Greeks, break-even, pin risk) → 04 (VIX/16 vs VIX/22, curve as regime gauge) → 13 (stress sizing, Kelly, BPR expansion, crisis playbook, behavioral traps) → 10 (regime diagnosis, spike decay) → 05 (dealer flows as a prior, not a signal) → 11 (what changed) → 09 (fees, cut-offs, hours).

**(c) Microstructure student.** 06 (order book, impact, auctions, sessions, intraday regularities) → 09 (venues, linkage, PFOF, OPRA) → 05 (hedging flows into the close, LETFs, pinning) → 12 (SIP vs direct feeds, trade signing, RV estimators, event-study design) → 08 (Muravyev, Baltussen, Lucca-Moench, STW) → 04 (intraday variance, VIX1D, the 2024-08-05 open) → 10 (2010, 2015, 2020 halts) → 01 (SET, VRO, the 4:00-4:15 window).

## 8. Glossary (one line each; details in the id shown)

Call/put: right to buy/sell at strike K; the writer has the mirror obligation (01). Multiplier: 100 standard; Nanos $1; ES $50; MES $5 (01). Moneyness: ITM/ATM/OTM off the forward, or by delta (01). Intrinsic/extrinsic: exercise value / premium minus intrinsic (01). American/European: exercisable any day / only at expiry (01). Physical/cash settlement: shares T+1 / (settlement value − K) × multiplier (01). AM (SET/SOQ) vs PM: opening-print composite, last trade the prior day / official close (01). Exercise by exception: OCC auto-exercise ≥ $0.01 ITM absent instruction (01). OPEX / witching: third Friday; Mar/Jun/Sep/Dec with index rebalances (05). FLEX: negotiable terms up to 15 years; used by buffer ETFs (01, 09). Open interest vs volume: outstanding at D−1 close vs traded (12). Put-call parity: C − P = e^{−rT}(F − K) (02). Box spread: pays K2 − K1; reveals the implied financing rate (02). BSM / Black-76 / Bachelier: lognormal on spot / on the futures / normal (02). Implied vol: the σ reproducing the price; a quoting convention (02). Realized vol: estimator-dependent; 5-minute RV the standard (04, 12). Skew/smile; risk reversal (25d put IV − 25d call IV); butterfly (wings − ATM) (04). Term structure: contango normal, backwardation stress; forward variance (w2 − w1)/(T2 − T1) ≥ 0 (02, 04). Sticky strike / sticky delta / SSR: smile dynamics; SSR 1 / 0 / ~1.5 for SPX (02). Local vol, stochastic vol (Heston, SABR), jumps, rough vol, SVI/SSVI: surface models and fits (02). Breeden-Litzenberger: q(K) = e^{rT}∂²C/∂K² (02). Variance swap / log contract: 1/K²-weighted OTM strip (02). VIX / VIX1D / VIX3M / VVIX / SKEW: 30-day variance rate; one-day business-time version; 93-day; vol of VIX; priced left tail (04). VIX futures and ETPs: forward-starting claims; roll yield; L(L−1) rebalancing (04). Delta/gamma/theta/vega/rho; vanna, charm, volga; dollar Greeks; break-even move IV/16 (03). Delta-hedged P&L identity: ½ΓS²(σ_r² − σ_i²)dt (02, 03). GEX / gamma flip / call and put walls: modeled dealer dollar gamma, its sign change, largest-gamma strikes (05). JPM collar; covered-call and buffer ETFs; autocallable; LETF rebalancing; vol targeting: systematic flow sources (05). Event variance / vol crush / implied move: straddle ≈ 0.8 × 1-sigma (02, 04). Limit order book, NBBO, SIP; closing auction / MOC; LULD; MWCB; PFOF / wholesaler (06). Reg T / portfolio margin (TIMS) / SPAN; OCC / STANS (09). Kelly fraction; expected shortfall; stress matrix (13). Purged cross-validation; deflated Sharpe ratio; Brier score and calibration; placebo level and climatology; pre-registration / sealed window (12).
