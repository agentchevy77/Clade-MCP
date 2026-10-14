# Historical Volatility Episodes, Crashes, Squeezes and What Each Taught About Options Markets
domain_id: 10-historical-episodes-and-regimes | last_updated: 2026-10-14 | status: draft
scope: Equity/rates volatility episodes 1987 to Oct 2026 (dates; SPX/VIX/skew/term-structure/liquidity; forced actors; what broke; regulatory response; lesson), vol-fund blowups, the short-vol supply chain, and recurring regime patterns.
confidence_notes: Every VIX level, date and % change was checked against Cboe's published VIX daily history (data through 2026-10-13); SPX moves/drawdowns computed from FRED SP500 closes; pre-2024 narratives are well established; fund-loss sizes, ETP flow estimates, 0DTE shares, OCC volume records, MOVE levels and attributions of 2025-26 spikes are secondary-sourced or marked [uncertain]; everything from mid-2025 on is recency-sensitive.

## Core concepts
- **VIX**: Cboe's 30-day constant-maturity, model-free implied volatility of SPX from mid-quotes of OTM SPX puts/calls (two expiries bracketing 30 days; 23-37 DTE since SPX weeklies were added in 2014). Annualized %; VIX/sqrt(252) is the implied one-day sigma (VIX 20 => ~1.26%/day; VIX 80 => ~5%/day). Switched from S&P 100 (now VXO) to SPX in 2003; history back-filled to 1990.
- **Realized vol (RV)**: annualized stdev of actual returns. **Variance risk premium (VRP)** = implied minus subsequently realized variance; positive on average, deeply negative in crashes.
- **Skew**: OTM put IV above ATM/call IV at the same expiry. **Fixed-strike skew** = IV at a given strike; **normalized skew** = (25-delta put IV - ATM IV)/ATM IV. They can move oppositely in a crash. Cboe **SKEW index** (100 = lognormal) measures the priced left tail.
- **Term structure**: IV or VIX futures across maturities. **Contango** (far > near) is the calm norm; **inversion/backwardation** (VIX > VIX3M, or cash > front future) is the stress signature.
- **Vol-of-vol**: volatility of IV; **VVIX** = 30-day implied vol of VIX options.
- **Dealer gamma**: net option gamma of market makers. Long gamma (customers net sold options) => dealers buy dips/sell rips (dampening). Short gamma (customers net bought puts in a selloff or calls in a squeeze) => dealers sell as prices fall / buy as they rise (amplifying). **Gamma squeeze**: call buying forces dealers to buy stock, raising deltas and forcing more buying.
- **Portfolio insurance**: 1980s synthetic-put replication that sells futures as the market falls; economically identical to being short gamma without having bought the option.
- **Vol-targeting / risk parity / CTAs / vol-control annuities**: exposure inversely proportional to trailing RV; when RV jumps they sell regardless of view, with a lag.
- **VIX ETPs**: notes/funds on VIX futures indices (long VXX/UVXY; inverse XIV/SVXY). Leveraged/inverse products rebalance at the close to keep constant leverage, creating predictable end-of-day demand proportional to the day's move.
- **Variance swap**: pays notional x (realized variance - strike variance); convex in vol, so short positions lose at an accelerating rate (LTCM 1998, Mar 2020).
- **Autocallable**: retail note in which the investor is implicitly short a down-and-in put; dealer hedging of these books is a structural source of index vol supply (Asia, Europe, increasingly US).
- **Treasury basis trade**: long cash Treasuries vs short futures, repo-levered 50-100x [uncertain]; unwinds violently when margin/repo terms change (Mar 2020; feared Apr 2025).
- **LDI**: UK pension schemes hedging liabilities with leveraged gilt repo/swaps; rising yields => collateral calls => forced gilt sales (Sep 2022).
- **Carry trade**: fund risk assets in a low-rate currency (JPY); a rate/FX shock forces simultaneous unwinds across equities, FX and vol (Aug 2024).
- **Circuit breakers**: market-wide halts at SPX -7%/-13% (15 min, before 15:25 ET) and -20% (close), in force since Feb 2013; tripped four times in Mar 2020, never since (as of 2026-10-14). **LULD** (phased in 2013): single-security bands with 5-minute pauses; 1,278 halts on 2015-08-24.
- **0DTE**: same-day-expiry options; SPX gained Tuesday/Thursday expirations in 2022 [dates uncertain], giving a listed expiry every day.
- **MOVE**: ICE BofA index of 1-month implied vol of Treasury options; the rates analogue of VIX.
- **Correlation-to-1**: in crashes pairwise stock correlations spike, index vol approaches average single-stock vol, and dispersion trades (short index vol/long single-name vol) lose.
- **Fast crash vs slow bear**: fast crash = liquidity/deleveraging event (days-weeks; VIX > 50; RV > IV; deep inversion). Slow bear = rates/earnings repricing (months; VIX rarely > 40; IV > RV most days; skew flattens).

## Mechanisms
### Why vol events are self-reinforcing
- Every major episode shares one skeleton: an actor with a **mechanical rule** (delta hedge, leverage target, margin, rebalance, collateral call, redemption) must transact in the direction of the move, into a market where liquidity providers have already withdrawn. The actor changes (portfolio insurers 1987 -> LTCM counterparties 1998 -> quant funds 2007 -> prime brokers 2008 -> HFT inventory limits 2010 -> inverse VIX ETPs 2018 -> vol-targeters, basis traders and dealers 2020 -> clearing margin 2021 -> LDI funds 2022 -> carry traders 2024); the loop is identical: move -> forced flow -> bigger move -> wider spreads -> larger forced flow.
- **Liquidity is conditional**: market makers scale quoted depth to RV and inventory; when RV jumps, SPX option quotes widen 5-10x or vanish (stub quotes at $0.01 on 2010-05-06; no computable VIX at the open on 2015-08-24; VIX 65.73 on 2024-08-05 from wide opening quotes).
- **Dealer gamma amplification**: put buying leaves dealers short puts; they short futures and must sell more as spot falls. Documented in single names (Ni, Pearson, Poteshman, White 2021) and index intraday momentum (Baltussen et al. 2021); index-level dealer gamma is inferred, not observed, and its sign is contested.
- **Vol-target de-leveraging**: a 10%-target strategy at RV 10% is 1.0x; at RV 20% it must be 0.5x. Because RV is trailing, selling persists for days after the shock (2018, 2020). In 2022 these strategies were already light, one reason the bear produced no VIX spike.
- **Margin spirals** (Brunnermeier & Pedersen 2009): margins rise with vol, forcing deleveraging, raising vol. Visible in VIX-futures margin hikes (Feb 2018), NSCC's $26bn -> $33.5bn industry collateral call on 2021-01-28 (which triggered Robinhood's buying restrictions), and LDI collateral calls (Sep 2022).
- **Term inversion** arises because front-month vol prices the live shock while back months price mean reversion; it is a regime marker, not a bottom signal. Deeper/longer inversion = more systematic sellers losing carry at once.
- **Correlation-to-1**: in a liquidity shock everything is sold for cash; implied correlation goes to 0.8-0.9+ and relative-value books (LTCM, 2007 quants) that are implicitly short correlation lose together.

### The short-vol supply chain
- **Supply**: autocallables and other yield notes; covered-call and buffer ETFs; pension/insurer overwriting; hedge funds short variance, VIX futures or put spreads for carry; inverse VIX ETPs (most reflexive pre-2018); market makers who end up short when customers net buy.
- **Demand**: tail-hedge funds, pension overlays, vol-target hedges, retail call buyers, long-VIX ETPs, dealers hedging structured books.
- **Dealers warehouse the mismatch**: against autocallables dealers are long vega and sell index vol/variance in calm markets (suppressing IV); as spot falls through barriers the position's vega can flip and they must buy vol back, a known source of vol-of-vol in Nikkei/KOSPI/Euro Stoxx and increasingly SPX [flip mechanics uncertain].
- **Why it breaks**: carry sellers are paid the VRP for convex, path-dependent losses concentrated in the worst-liquidity days; many sellers are also forced de-leveragers (vol-target), so supply disappears exactly when demand spikes (Feb 2018, Mar 2020).

### Episode catalogue (dates | market facts | mechanism | what broke | response | lesson)
- **1987-10-19 Black Monday**: DJIA -22.6%, SPX -20.5%; futures fell more than cash as arbitrage broke; VXO (back-calculated) ~150 [uncertain]. ~$60-90bn [uncertain] of portfolio-insured assets sold futures after a -9% week; specialists/OEX market makers exhausted capital; Fed liquidity pledge 10-20. Response: Brady Commission (Jan 1988), NYSE circuit breakers (Oct 1988). Lesson: index put skew appeared and never left (Rubinstein 1994; Bates 2000); delta-replication is short gamma to the whole market.
- **1997-10-27/28**: DJIA -554 (-7.2%); NYSE breakers tripped for the first time, early close; VIX high 48.64 on 10-28, close 31.22 the same day. Breakers stop the clock, not the move.
- **1998 Russia/LTCM**: default 08-17; LTCM (equity ~$4.7bn, assets >$124bn, ~$1.25tn derivatives notional) lost $4.6bn incl. ~$1.3bn in equity vol (short long-dated index vol sold in the high teens, marked above 30 [levels uncertain]); 14 banks injected $3.625bn on 09-23 under NY Fed supervision; VIX close 45.74/high 49.53 on 10-08; Fed cut 09-29, 10-15 (inter-meeting), 11-17. Lesson: long-dated IV can rise to levels never realized and the mark kills before realized P&L arrives; "central bank of volatility" needs survival capital (Jorion 2000; Lowenstein 2000).
- **2000-02 dot-com bear**: SPX -49% (2000-03-24 to 2002-10-09), Nasdaq -78%; VIX closes peaked at 41.76/43.74 (2001-09-17/20, after a four-day 9/11 closure) and 45.08 (2002-08-05). Lesson: slow bears give VIX 25-45, not 80; dispersion and sector vol matter more than index vol; index puts bleed for two years.
- **2007 quant quake**: 02-27 VIX +64% (11.15 -> 18.31); 08-06/09 factor and stat-arb funds lost 20-30% (Khandani & Lo 2007/2011) while VIX only touched 37.50 intraday (08-16). A forced unwind of a crowded long-short book spread through shared positions, invisible in index vol. Lesson: crowding/deleveraging contagion precedes the headline crash; index IV is a poor early warning of hidden leverage.
- **2008 GFC**: Lehman 09-15 (VIX 31.70); SEC short-sale ban on ~800 financials 09-19 to 10-08 impaired option market-maker hedging; TARP vote fails 09-29, SPX -8.8%, VIX 46.72; October SPX +11.6% (10-13), -9.0% (10-15), +10.8% (10-28); VIX all-time intraday high 89.53 (10-24), closes 80.06 (10-27) and then-record 80.86 (11-20); 63 closes > 40 in 2008, 61 in 2009; SPX -56.8% (2007-10-09 to 2009-03-09). Dealer balance sheets (prime brokerage, repo, CDS) shrank as hedging demand exploded; implied correlation ~0.8-0.9 [uncertain]; single-name variance swaps on collapsing financials produced convex losses; the VW squeeze (10-28, Porsche's option-built stake) briefly made VW the largest company by market cap. Response: TARP, Fed facilities, Dodd-Frank, OTC clearing, Basel III. Lesson: VIX can stay > 40 for months; term structure inverts by tens of points; vol-point put skew shrinks while fixed-strike puts still pay; counterparty risk is a vol input.
- **2010-05-06 Flash Crash**: DJIA -998.5 intraday (~-9%) in 36 minutes from 14:32 ET; E-mini and SPX option liquidity vanished; trades >60% from reference busted (~20,000 [uncertain]); eight S&P 500 stocks printed $0.01; VIX high 40.71/close 32.80 (+31.7%), then 45.79 on 05-20 (euro crisis). SEC/CFTC (2010-09-30): a $4.1bn, 75,000-contract E-mini sell algorithm keyed to volume met HFT inventory recycling then withdrawal; Sarao's spoofing (charged 2015) is widely viewed as minor. Response: single-stock breakers (2010), LULD (2013), revised market-wide breakers (2013), erroneous-trade rules. Lesson: stop and market orders are free options to no one; option quotes vanish before futures; index "value" can be undefined for minutes.
- **2011-08 US downgrade**: S&P cut the US to AA+ after the close on 08-05; 08-08 SPX -6.66%, VIX +50.0% to 48.00; next three sessions ~+4.7%, -4.4%, +4.6% (Fed "mid-2013" guidance 08-09); 75 closes > 30 in 2011; SPX -19.4% (04-29 to 10-03 closes). Lesson: whipsaw regimes reward gamma scalping and punish both directional hedges; RV > IV for weeks.
- **2015-08-24**: E-mini limit-down 5% pre-open, paused 09:25-09:30; SPY opened -5.2%, hit -7.8% by 09:35; NYSE had opened only 38% of its S&P 500 names by 09:35; 1,278 LULD halts (1,058 in 327 ETPs, 220 in 144 non-ETPs); 20% of the 50 largest ETPs fell 10%+; IVV traded at a deep discount to SPY/E-mini/NAV until 09:43 (SEC 2015). VIX could not be computed at the open (Cboe's OPEN field equals the prior close), then printed 53.29 intraday and closed 40.74; DJIA ~-1,089 intraday [uncertain], -588 close. Response: LULD band changes, NYSE eliminated stop orders (2016), reopening collars. Lesson: ETF arbitrage needs an open, quotable underlying; opening VIX prints are unreliable (repeated 2024-08-05).
- **2016-06-24 Brexit**: polls implied Remain so VIX fell 18.5% on 06-23 (17.25) then rose 49.3% to 25.76 as SPX fell ~3.6% (and ~1.8% on 06-27 [uncertain]); sterling -8% to a 31-year low; new SPX highs within weeks. Lesson: binary-event vol crushes before the event; a surprise outcome without a funding channel recovers fast; "buy the dip" conditioning begins here.
- **2018-02-05 Volmageddon**: SPX -2.1% (02-02) then -4.1% (02-05); VIX 17.31 -> 37.32, +115.6%, largest one-day % rise in Cboe history (secondary sources quote +104% from another base); 02-06 intraday 50.30; SPX -10.2% peak-to-trough (01-26 to 02-08 closes). Front VIX futures rose ~90-100% [uncertain]; inverse and 2x VIX ETPs (XIV, SVXY, TVIX, UVXY; ~$3-4bn AUM [uncertain]) had to buy on the order of 200-300k VIX futures into the 16:15 settlement [uncertain] and were front-run. XIV's indicative value fell ~96% after hours; Credit Suisse announced an acceleration event 02-06 and the note was redeemed later that month [dates uncertain]; SVXY lost ~80-90% and ProShares cut it to -0.5x (UVXY to 1.5x) in late February [uncertain]. LJM Preservation & Growth (short SPX puts) lost ~80% over two days and liquidated; SEC/CFTC charged LJM and its managers in 2021 [month uncertain]. The SEC fined S&P DJI (2021) for a stale VIX-futures index feed at the 02-05 close [amount uncertain]. Lesson: published rebalance rules are a free option for everyone else; VIX futures, not VIX, drive ETP P&L; short-vol P&L is concave and path-dependent; size risk in VIX points (+20) not % (+116).
- **2018-Q4**: SPX -19.8% (09-20 to 12-24 closes) with VIX max close 36.07 (12-24; 10-10 +43.9%); 12-26 SPX +4.96%. Fed hikes plus QT ("autopilot" 12-19), thin holiday tape, Mnuchin's bank calls (12-23). Lesson: a near-bear with moderate vol when the decline is orderly; the 2019-01-04 Powell pivot created the modern Fed-put reflex.
- **2020-02/03 COVID**: SPX -33.9% (02-19 3386.15 to 03-23 2237.40), fastest 30% drop ever; daily -7.6% (03-09), -9.5% (03-12), +9.3% (03-13), -12.0% (03-16), +9.4% (03-24); breakers 03-09, 03-12, 03-16, 03-18; VIX record close 82.69 (03-16), intraday 85.47 (03-18); 35 closes > 40; RV > 80% annualized for weeks [uncertain]. Vol-target/risk-parity/CTA de-leveraging; dealers short gamma from put buying; basis-trade unwinds and dealer balance-sheet limits broke the Treasury market (10y 0.54% on 03-09 to 1.18% on 03-18 while stocks fell; Schrimpf-Shin-Sushko 2020; Duffie 2020; Vissing-Jorgensen 2021); Fed -50bp (03-03), -100bp plus $700bn QE (03-15), unlimited QE and corporate credit facilities (03-23). Blowups: Malachite Capital (short vol; closed mid-March with losses passed to counterparties [sizes uncertain]); Parplus Partners (ABN AMRO ~$200m client loss) [uncertain]; Ronin Capital (CME member default) [uncertain]; Allianz Structured Alpha (below). Lesson: VIX 80 = 5% daily sigma; term structure inverts 30+ points; normalized skew flattens while fixed-strike puts pay enormously; the only reliable hedge was owned before 02-19; VIX halved in 19 trading days after the peak but needed 231 to close < 20.
- **2020-21 retail boom**: OCC volume ~7.5bn (2020), ~9.9bn (2021), ~10.3bn (2022), ~11.1bn (2023), ~12.2bn (2024) contracts [approximate; 2025 higher, uncertain]. SoftBank "Nasdaq whale" (reported 2020-09-04): ~$4bn of megacap call premium, tens of billions delta notional [uncertain]; Nasdaq -5% on 09-03, VIX +26.5% to 33.60. GME: short interest ~140% of float (01-22); retail call buying forced dealer stock buying; high $483 on 2021-01-28; VIX +61.6% to 37.21 on 01-27 as funds de-grossed; NSCC collateral $26bn -> $33.5bn and Robinhood restricted buying 01-28; Melvin -53% in January, $2.75bn from Citadel/Point72, closed 2022-05-18. SEC Staff Report (Oct 2021): short covering was a small share of volume; did not find the gamma squeeze was the main driver [characterization uncertain]. Lesson: concentrated single-name option demand can dominate price; clearing margin, not regulators, stops squeezes; VIX reacts to de-grossing even when the index is flat.
- **2021-03-26 Archegos**: >$36bn gross via total-return swaps across ~6 prime brokers, each unaware of the others; losses CS ~$5.5bn, Nomura ~$2.85bn, MS $911m, UBS $774m, MUFG ~$300m; Goldman/MS/Deutsche sold blocks first; Hwang 18 years (Nov 2024); CS fined $387m (Jul 2023). Not options, but: swaps are synthetic stock with hidden leverage; first to liquidate loses least; margin must price concentration and liquidity, not just VaR.
- **2022 slow bear**: SPX -25.4% (01-03 4796.56 to 10-12 3577.03); Nasdaq -33%; Fed +425bp plus QT. VIX max close 36.45 (03-07), zero closes > 40, 49 closes > 30; RV ~25% [uncertain]; term structure flat-to-mildly inverted; put skew to multi-year lows (SKEW ~110-115 late 2022 [uncertain]) -> "skew collapse" debate. Why: positioning already light (vol-target/CTA underweight from January); orderly, rates-driven decline; hedgers burned by bleeding puts; bears sold stock rather than buying puts so dealers were not short gamma. Lesson: a slow bear transfers wealth from put buyers to put sellers while the index falls 25%; "VIX never above 40" is a positioning fact, not complacency.
- **2022-09/10 UK LDI**: mini-budget 09-23; sterling $1.0327 (09-26, record low); 30y gilt yields rose >100bp in four days; LDI collateral calls forced long-gilt sales (BIS: forced sales created ~7-10% price discounts); BoE announced temporary long-gilt purchases 09-28 (up to GBP 5bn/day over 13 auction days; GBP 19.3bn actually bought), TECRF 10-10, index-linked added 10-11, ended 10-14; Kwarteng sacked 10-14, Truss resigned 10-20; MOVE ~150-160 [uncertain]. Lesson: convex liabilities + leverage + collateral calls reproduce portfolio insurance in bonds; rates vol can be the epicentre while VIX sits ~30 (Pinter 2023).
- **2023-03 SVB**: $42bn run 03-09, seizure 03-10, Signature 03-12, BTFP 03-12; 2y CMT 4.60% (03-10) -> 4.03% (03-13), 5.05% (03-08) -> 3.81% (03-17), largest multi-day collapse since 1987 (FRED); MOVE ~200 on 03-15 [uncertain]; VIX only 26.52 close/30.81 high (03-13); Credit Suisse to UBS 03-19 with CHF 16bn AT1 zeroed; First Republic failed 05-01. Lesson: rates vol and equity vol decouple; front-end options carried the shock; index vol is cheap during a bank scare if the policy response is fast.
- **2023 0DTE growth**: 0DTE ~43% of SPX volume in 2023 and about half or more in 2024-25 [uncertain]; JPMorgan "Volmageddon 2.0" warning (Feb 2023) vs Cboe data showing balanced flow; VIX1D launched 2023-04-24 [uncertain]. Lesson: VIX (23-37 DTE) is blind to same-day gamma; intraday pins/accelerations are plausibly 0DTE-related but causality unproven.
- **2024-08-05 yen carry unwind**: BoJ to 0.25% (07-31); weak payrolls 08-02 (unemployment 4.3%, Sahm rule), VIX +25.8% to 23.39; 08-05 Nikkei -12.4% (worst since 1987), SPX -3.0%; VIX intraday 65.73 within minutes of the open (OPEN field = prior close, i.e. no computable 09:30 value) then closed 38.57 (+64.9%, third-largest % rise); -28.2% on 08-06; 23.79 by 08-08; SPX -8.5% (07-16 to 08-05 closes), new highs within weeks. Front VIX futures peaked in the 30s [uncertain]; VVIX among its highest ever [uncertain]. The VIX formula uses mid-quotes with no trade filter, so 5-10x-wide pre-10:00 quotes mechanically inflate it. BIS QR Sep 2024 ("Carry off, carry on"): "sharp but short-lived". Lesson: never size or trigger off cash VIX in the first 15-30 minutes; VIX ETPs/options settle on the SOQ; the cash-futures gap is itself a liquidity gauge.
- **2024-12-18 FOMC**: 25bp cut but dots showed only two 2025 cuts; SPX -2.95%; VIX 15.87 -> 27.62 (+74.0%, second-largest % rise); -23.8% on 12-20; SPX -3.7% drawdown (12-06 to 12-19). Lesson: from a low base % moves are huge while point moves are moderate (+11.75); one-sided positioning sets amplitude; event spikes revert in days.
- **2025-04 tariff shock**: announced after the close 04-02; SPX -4.84% (04-03), -5.97% (04-04), worst two days since Mar 2020; VIX 30.02 (+39.6%) then 45.31 (+50.9%); 04-07 VIX opened/printed 60.13, closed 46.98, SPX ~-21% intraday from the 02-19 high [uncertain]; 04-08 peak close 52.33; 04-09 90-day pause: SPX +9.52%, Nasdaq +12.16%, VIX -35.8% to 33.62 (largest one-day % fall ever); 04-10 SPX -3.46%, VIX 40.72; closing drawdown -18.9% (02-19 6144.15 to 04-08 4982.77). 10y rose 4.01% (04-04) -> 4.48% (04-11) and 30y +54bp in three days (most since 1982) while stocks fell, attributed to basis-trade/swap-spread unwinds and foreign selling [uncertain]; record daily and monthly options volume [figures uncertain]. VIX fell from peak close to < 25 in 12 trading days and < 20 in 23. Lesson: policy-driven crashes reverse on policy; inversion of 10+ points un-inverted in two weeks; the biggest vol crush follows the biggest headline, so long-vol must be monetized intraday.
- **2025-06 Israel/Iran 12-day war**: strikes 06-13 (VIX 20.82), US strikes on Fordow/Natanz/Isfahan 06-21, ceasefire 06-24; VIX max 22.17 (06-19); SPX record 6173.07 on 06-27. Geopolitics without a funding channel = 2-5 VIX points, gone in a week.
- **2025-08-01**: weak payrolls with large revisions and the BLS commissioner's dismissal; SPX -1.6%, VIX +21.9% to 20.38; faded. Fed cut 09-17 to 4.00-4.25%.
- **2025-10/11**: shutdown 10-01 to 11-12 (43 days, longest ever; BLS releases suspended, 10-29 FOMC met without October data). 10-10: SPX -2.71%, VIX +31.8% to 21.66 on renewed China tariff threats over rare-earth controls [attribution uncertain], with a record ~$19bn crypto liquidation. 10-16/17: regional-bank loan-fraud disclosures (Zions, Western Alliance) after the First Brands/Tricolor bankruptcies took VIX to a 25.31 close and 28.99 intraday before a sharp reversal as tariff rhetoric softened [uncertain]. SPX record 6890.89 (10-28); Nvidia $5tn and a Fed cut 10-29 [uncertain]. November: AI-valuation/capex and private-credit worries; SPX -5.1% (10-28 to 11-20); VIX 26.42 close/28.27 high on 11-20, the post-Nvidia-earnings reversal day [uncertain]; Fed cut 12-10 [uncertain]. Lesson: every 2025-H2 spike was VIX 20-28 and one to three days; April had taught that policy reverses.
- **2026-Q1 Iran war / oil shock**: Jan: Venezuela operation (01-03), criminal probe of Fed Chair Powell (01-11), 10% tariff threat on Europe over Greenland (01-17), SPX -2.06% on 01-20 [attribution uncertain], SPX record 6978.60 (01-27), shutdown 01-31 to 02-03 then DHS-only from 02-14 (ended 04-30, 76 days); Supreme Court struck down IEEPA tariffs 6-3 (02-20) and 15% global tariffs were announced (02-21). 02-28: US-Israeli strikes killed Khamenei; Hormuz shipping stalled from 03-01; Brent $72.48 (02-28) -> $112.57 (03-27) -> $118.35 peak (03-31); KOSPI breaker on 03-04 (-12% intraday). VIX intraday high 35.30 (03-09 open), closes 29.49 (03-06), 31.05 (03-27, the 2026 max), 30.61 (03-30); SPX -9.1% (01-27 to 03-30 close 6343.72), +2.91% on 03-31; 10y 4.46% (03-27); CPI 3.3% (Mar) and 4.2% (May). Two-week ceasefire 04-07 (SPX +2.51% 04-08), US blockade 04-13, Islamabad memorandum 06-17, blockade lifted 06-18, ceasefire collapsed 07-08, Brent > $100 again 07-23. Warsh confirmed Fed Chair 05-13. 06-05: SPX -2.64%, VIX +39.7% to 21.51 (cause unconfirmed; coincident with renewed US-Iran strikes 06-06 and hot inflation [uncertain]). Sep: 10y 5.01% (09-14, first > 5% since Oct 2023), Brent > $108, Fed hiked 25bp to 3.75-4.00% on 09-16 (first hike in three years), yet VIX's September max close was 17.84 and SPX made a record 7818.93 on 10-06; VIX 15.27 on 2026-10-13. Lesson: war + oil + inflation + hike produced a -9% drawdown and VIX ~30: the 2022 template, not 2020; anticipated shocks with unlevered positioning keep equity vol low while oil/rates vol carries the trade.

### Fund blowups tied to options/vol
- LTCM (1998): short long-dated index vol + convergence trades; survival capital beats expected value.
- Optionsellers.com (Nov 2018): naked short nat-gas calls; clients lost > 100% and owed their FCM [details uncertain].
- LJM Preservation & Growth (Feb 2018): short SPX puts marketed as "preservation"; ~80% loss in two days.
- XIV/SVXY (Feb 2018): ~$2bn+ of investor capital erased at one close [uncertain]; the -80% acceleration clause was in the prospectus.
- Malachite Capital (Mar 2020): short-vol/structured-product fund wound down; losses passed to prime brokers [uncertain].
- Allianz Structured Alpha (Mar 2020; SEC 2022-05-17): ~$11bn from 114 institutions; managers cut hedges and mismarked; losses > $5bn; AGI US pleaded guilty, > $1bn SEC penalties, > $5bn restitution; PMs Tournant, Taylor, Bond-Nelson charged. A "hedged" short-vol strategy is only as good as the hedges actually held that day.
- Infinity Q (Feb 2021; SEC 2022-02-17): CIO Velissaris altered inputs/code of a third-party pricing service to overvalue OTC derivatives by > $1bn; redemptions suspended 2021-02-22; later imprisoned [term uncertain]. Illiquid vol derivatives in a daily-NAV fund invite mismarking.
- Melvin Capital (Jan 2021): short GME; -53% in a month; closed May 2022.
- Archegos (Mar 2021): concentration and opacity via swaps; > $10bn bank losses.
- Tiger Global and long-duration growth funds (2022): -50%+ [uncertain] in a slow bear with no vol spike; beta and factor, not vol.

## Formulas and quantitative rules
```
VIX (Cboe, per expiry):
  sigma^2 = (2/T) * SUM_i [ dK_i / K_i^2 * exp(R*T) * Q(K_i) ] - (1/T) * (F/K0 - 1)^2
  K_i strike of i-th OTM option; dK_i strike spacing; Q(K_i) MID-QUOTE (bid+ask)/2; F forward via put-call parity;
  K0 first strike below F; R risk-free; T years. VIX = 100*sqrt(30-day interpolation across the two expiries).
  No trade is required: opening quotes 5-10x normal width => inflated VIX (2024-08-05).

Implied one-day move: sigma_1d = VIX/sqrt(252). VIX 15 -> 0.94%; 30 -> 1.89%; 50 -> 3.15%; 82.69 -> 5.21%.

Short variance swap P&L: P&L = -N_var*(sigma_R^2 - K^2); vega notional N_vega = 2*K*N_var.
  K = 20, N_vega = $1m => N_var = $25,000/pt^2. Realized 40 -> loss $30m (30x vega notional); realized 80 -> $150m.

Leveraged/inverse ETP close rebalance (notional): D = A*(L^2 - L)*r,  A = AUM, L = leverage, r = index day return.
  L = -1 and L = +2 both give D = 2*A*r (both BUY after an up day).
  Illustrative 2018-02-05: A ~ $4bn [uncertain], r ~ +0.95 => D ~ $7.6bn ~ 7.6e9/(1000*30) ~ 250,000 VIX futures.

Vol-target exposure: w_t = min(w_max, sigma_target/sigma_hat_t). Target 10%: RV 10% -> 1.0x; 20% -> 0.5x; 40% -> 0.25x.
  Dollar selling = AUM*(w_{t-1} - w_t), lagged because sigma_hat is trailing.

Dealer hedge flow: dHedge_shares = -Gamma_net_shares*dS; Gamma$ per 1% = Gamma_net_shares*S*0.01*S.
  Gamma_net < 0 => sell on down moves, buy on up moves (amplifies).

Synthetic put (portfolio insurance) hedge ratio: h = -N(-d1); as S falls N(-d1) rises => more selling.

Margin spiral: max position = Capital/m(sigma), m increasing in sigma; m proportional to sigma => sigma doubling halves position.

Term-structure stress ratio r = VIX/VIX3M (or VIX/front future): < 0.9 calm; 0.9-1.0 caution; > 1.0 inverted; > 1.2 crash regime.

Spike decay (Cboe closes; trading days from peak close to first close < 0.5*peak | < 25 | < 20):
  2025-04-08 (52.33): 12 | 12 | 23      2015-08-24 (40.74): 19 | 10 | 29      2020-03-16 (82.69): 19 | 57 | 231
  2008-11-20 (80.86): 27 | 163 | 273    1998-10-08 (45.74): 31 | 31 | 183     2011-08-08 (48.00): 94 | 58 | 113
  2002-08-05 (45.08): 176 | 77 | 192    2010-05-20 (45.79): 45 | 20 | 99
```

## Empirical magnitudes
- VIX record closes (Cboe): 82.69 (2020-03-16), 80.86 (2008-11-20), 80.06 (2008-10-27), 79.13 (2008-10-24), 76.45 (2020-03-18), 75.47 (2020-03-12). Intraday highs: 89.53 (2008-10-24), 85.47 (2020-03-18), 84.83 (2020-03-17), 83.56 (2020-03-16). Sources quoting 80.74 for Nov 2008 cite the 2008-11-21 high, not the record close.
- Largest one-day % rises in VIX close: +115.6% (2018-02-05), +74.0% (2024-12-18), +64.9% (2024-08-05), +64.2% (2007-02-27), +61.6% (2021-01-27), +54.0% (2021-11-26, Omicron), +50.9% (2025-04-04), +50.0% (2011-08-08), +49.3% (2016-06-24), +48.0% (2020-06-11), +46.5% (2020-02-24). Largest falls: -35.8% (2025-04-09), -29.6% (2010-05-10), -28.2% (2024-08-06), -27.0% (2011-08-09), -24.7% (2008-10-20), -23.8% (2024-12-20).
- Closes > 40 by year: 2008: 63; 2009: 61; 2010: 3; 2011: 11; 2015: 1; 2020: 35; 2025: 4; all other years since 2007 (incl. 2018, 2022, 2024, 2026 to 10-13): 0. Closes > 30: 2008: 79; 2009: 111; 2011: 75; 2020: 80; 2022: 49; 2025: 12; 2026 to 10-13: 2.
- Mean VIX close: 2017: 11.09 (min 9.14); 2008: 32.69; 2020: 29.25; 2022: 25.64; 2024: 15.55; 2025: 18.93; 2026 to 10-13: 18.10.
- Cboe VIX file OPEN field equals the prior close on 221 of 4,758 days since 2008, including the most stressed opens (2008-10-24/27, 2015-08-24, 2018-02-06, 2020-03-09/16, 2024-08-05): no computable 09:30 value. Do not use OPEN as a true open.
- SPX drawdowns (FRED closes, as of 2026-10-13): Jul-Aug 2024 -8.5%; Dec 2024 -3.7%; Feb-Apr 2025 -18.9%; Oct-Nov 2025 -5.1%; Jan-Mar 2026 -9.1%; Jun 2026 -4.5%. Record close 7818.93 (2026-10-06). Largest daily moves since 2025-06: -2.71% (2025-10-10), -2.64% (2026-06-05), -2.06% (2026-01-20); +2.91% (2026-03-31), +2.51% (2026-04-08).
- Historic SPX daily moves: -20.5% (1987-10-19), -12.0% (2020-03-16), -9.5% (2020-03-12), -8.8% (2008-09-29), -6.66% (2011-08-08), -5.97% (2025-04-04); +11.6% (2008-10-13), +10.8% (2008-10-28), +9.52% (2025-04-09), +9.4% (2020-03-24), +9.3% (2020-03-13).
- Bear markets: 2007-09 -56.8%; 2000-02 -49%; 2020 -33.9% in 23 trading days; 2022 -25.4% over 9 months; 1987 -33.5% from the Aug peak [uncertain]; 2018-Q4 -19.8%; 2011 -19.4%.
- Rates: 2y CMT 5.05% (2023-03-08) -> 3.81% (03-17); 10y 0.54% (2020-03-09) -> 1.18% (03-18); 10y 4.01% (2025-04-04) -> 4.48% (04-11); 10y 3.69% (2022-09-23) -> 3.97% (09-27) -> 3.72% (09-28) (FRED); 10y 5.01% on 2026-09-14 (secondary). MOVE ~200 (Mar 2023), ~150-160 (Oct 2022) [uncertain].
- Options volume (OCC, approx.): 7.5bn (2020), 9.9bn (2021), 10.3bn (2022), 11.1bn (2023), 12.2bn (2024); 2025 set annual, monthly (April) and daily records [uncertain]. 0DTE share of SPX volume ~43% (2023), ~50%+ (2024-25) [uncertain].
- Microstructure: 2015-08-24: 1,278 LULD halts; 4,078 post-halt trades ($34.6m) outside disseminated bands (SEC). 2010-05-06: $4.1bn/75,000-contract E-mini sell program (~1.3% of day volume per CME) (SEC/CFTC).
- Blowups: Archegos bank losses CS $5.5bn, Nomura $2.85bn, MS $0.91bn, UBS $0.77bn, MUFG ~$0.3bn; GME short interest ~140% of float (2021-01-22), NSCC collateral $26bn -> $33.5bn (2021-01-28); Allianz $11bn invested, > $5bn losses, > $1bn SEC penalty; Infinity Q > $1bn overvaluation; LTCM $4.6bn loss, $3.625bn recap.
- 2026 oil/inflation: Brent $72.48 (02-28) -> $118.35 (03-31) -> $71.57 (07-01) -> $100.69 (07-23) -> > $108 (09-14); CPI 3.3% (Mar), 4.2% (May); fed funds 3.75-4.00% after 09-16 hike [as of 2026-10-14].

## Practitioner heuristics
- **Size VIX risk in points and SPX %**, never VIX %: +20 points (Feb 2018), +22 over three days (Apr 2025); the +74% of Dec 2024 was +11.75 points.
- **Spike is the trade, decay is the carry**: closes > 40 halved within 12-31 trading days in liquidity shocks (2008, 2015, 2020, 2025) but 90-180 days in grinding bears (2002, 2011). Expect reversion to the mid-20s, then regime dependence. Breaks when the shock is solvency (Sep-Oct 2008), not liquidity.
- **Inversion is a regime switch, not a bottom**: with VIX/VIX3M > 1 stay long short-dated gamma and do not sell the front until the ratio has fallen for 3+ sessions. Exception: scheduled-event inversions un-invert on the event regardless of outcome.
- **Ignore cash VIX for the first 15-30 minutes** and whenever cash minus front future exceeds ~10 points; use the front future, VIX1D and SPX mid-quote widths (2015-08-24, 2024-08-05, 2025-04-07 open 60.13).
- **Evaluate hedges at the strike, not the delta**: when ATM IV triples, normalized skew flattens while every fixed-strike put gains.
- **Own the hedge before the catalyst**: after the first -5% day 1-month puts cost 3-5x. 3-6 month tails bought at VIX < 15 and rolled paid in 2018, 2020, 2024, 2025 and bled in 2017, 2021, 2023.
- **Monetize gamma into the headline**: the largest crushes (2025-04-09, 2024-08-06, 2010-05-10, 2008-10-20) followed policy or technical relief; exit windows are hours.
- **Diagnose the bear in week one**: funding stress (credit gapping, basis widening, carry breaking, overnight gaps) => 2008/2020/2025 template (VIX 50-80; buy the first crush, sell the second). Rates/earnings repricing with orderly moves => 2022/2026 template (VIX 25-36 ceiling; sell vol rallies; own put spreads, not puts).
- **Correlation jumps before vol in de-grossing** (Aug 2007, Jan 2021, Nov 2025): VIX can rise 30-60% with the index flat; watch implied correlation and factor returns.
- **Known mechanical flows get front-run**: inverse ETPs, month-end vol-target rebalances, index reconstitutions; the close-move exceeds what AUM alone implies.
- **Binary events are rarely binary**: Brexit, Dec-2024 FOMC and Apr-2025 realized 2-3x the implied move with one-sided positioning; sell event vol only when implied >= 1.5x the historical realized for that event type and skew is two-sided.
- **RV > IV is the crash regime; IV > RV is the bear regime**: track 10-day RV minus VIX daily; the VRP flips sign only in fast crashes.
- **Rates-vol regimes do not require equity-vol regimes** (SVB: MOVE ~200 vs VIX 26; LDI: gilt crisis vs VIX ~30; Sep 2026: 10y > 5% and a hike vs VIX < 18); hedge cross-asset separately.

## Common misconceptions and pitfalls
- "VIX is fear": it is the price of 30-day SPX variance, set by hedging demand and dealer inventory; it spikes on de-grossing without fear (2021-01-27) and stays flat in real crises (SVB).
- "VIX doubled so my options doubled": option price ~ IV x sqrt(T); 30-day VIX and a 0DTE's IV are different numbers; VIX ETPs track futures, which rose far less than cash on 2024-08-05.
- "XIV died because VIX spiked": it was accelerated because the front-two VIX futures roughly doubled; the futures are the product.
- "Skew always steepens in a crash": in vol points yes, normalized often no (Oct 2008, Mar 2020); specify the measure.
- "0DTE causes crashes": no crash since 2022 is attributable to 0DTE; intraday amplification is contested.
- "Circuit breakers prevent crashes": they pause the tape (1997, 2020); in 2015 LULD itself created ETF dislocations; the reopening is the risk.
- "One spoofer caused the flash crash": the SEC/CFTC attributed it to a large sell algorithm interacting with HFT inventory limits.
- "2022 was low vol": RV ~25% [uncertain] is high; VIX simply never exceeded RV by much because nobody needed puts.
- "VIX > 40 means buy": true in 2010, 2011, 2015, 2020, 2025; false in Sep-Oct 2008 (next month -17%); works only for those who can carry a second leg.
- "-10% in two days means a crash is under way": Apr 2025 reversed on day four; continuation depends on the funding channel, not the drop size.
- "Short vol is free money": the VRP is real on average (Dew-Becker et al. 2017; Cheng 2019) but pays for convex losses that arrive in one week (LTCM, LJM, Malachite, Structured Alpha).
- Pitfalls: back-testing on Cboe VIX history before 2003 (back-filled); using the Cboe OPEN field as a true open (221 of 4,758 days since 2008 equal the prior close); confusing the 2008-11-21 high (80.74) with the record close (80.86 on 11-20); quoting Feb 2018 as +104% instead of Cboe's +115.6%.

## Contested or uncertain claims
- **1987 cause**: Brady Commission blamed portfolio insurance; Roll (1988) showed the crash was global, including markets without it (amplifier, not cause).
- **Feb 2018 causality**: ETP rebalancing (~$7-8bn of futures demand) vs discretionary/systematic short-vol unwinds; BIS and most practitioners centre the ETPs, some argue they were too small to double the front futures alone.
- **Dealer gamma as an index driver**: sell-side/vendor net-gamma estimates attribute intraday reversals to dealers; academics find support in single names and intraday momentum but index-level figures rest on assumed customer direction and can disagree on sign.
- **0DTE and intraday vol**: JPMorgan (2023) warned of a cascade; Cboe data show balanced flow; Brogaard-Han-Won (2023) find reduced vol in some samples, others find higher intraday vol; Beckmeyer-Branger-Gayda (2023) find retail 0DTE buyers lose on average. No consensus on crash amplification.
- **Was 2024-08-05's 65.73 "real"**: Cboe says computed per methodology; most practitioners treat it as a quote artifact; any subsequent methodology revision is unverified [uncertain].
- **2022 skew collapse**: structural (growing systematic put-selling/overwriting supply, post-2020 hedge fatigue) vs cyclical (light positioning); skew re-steepened in 2024-25, supporting cyclical, while overwriting supply keeps growing.
- **GME gamma squeeze size**: practitioners/FT describe a gamma squeeze; SEC staff emphasized retail buying and sentiment and found short covering was a small share of volume.
- **April 2025 Treasury selloff**: basis-trade unwind vs foreign official selling vs swap-spread trades; the pause was reportedly influenced by the bond market [uncertain].
- **Fed put**: whether rapid reversals (2019, 2020, 2025) have structurally lowered the frequency of VIX > 40 regimes or merely delayed them.
- **Vol-target AUM**: estimates of vol-control/risk-parity/CTA equity exposure range from hundreds of billions to > $1tn, giving very different forced-selling estimates.
- **2026 attributions**: causes of 2026-06-05 and 2026-01-20, and the equity-market role of the Sep 2026 hike, are not yet established in reliable sources.

## Relationships to other domains
- Volatility surface/skew/term structure (likely 02-...): 1987 origin of index skew; 2022 skew flattening; fixed-vs-normalized skew in crashes.
- VIX and volatility products (likely 07-...): methodology weaknesses at the open (2015, 2024), cash-futures basis in spikes, ETP rebalancing math (2018), SOQ settlement vs cash.
- Dealer positioning/gamma/flows (likely 05-...): every amplifier above (portfolio insurance, dealer short gamma, vol-target, ETP rebalance) is hedging-flow feedback.
- Market microstructure/halts/liquidity (likely 09-...): 2010, 2015, 2020 breakers, stub quotes, busted trades, LULD.
- Event vol and macro catalysts (likely 11-...): FOMC 2024-12-18, Brexit, tariff announcements, payrolls (2024-08-02, 2025-08-01).
- 0DTE/short-dated options (likely 08-...): 2023 growth, VIX blindness to same-day gamma, VIX1D, contested amplification.
- Risk management/sizing (likely 12-...): convexity of short variance, margin spirals, survival capital (LTCM, LJM, Structured Alpha, Melvin), stress in VIX points.
- Rates/cross-asset vol (MOVE, swaptions): LDI 2022, SVB 2023, Treasury dysfunction 2020, Apr 2025 basis trade, Sep 2026 hike with low VIX.
- Support/resistance and key levels (likely 13-...): episodes show round-number index levels, prior highs and large-open-interest strikes attract hedging flow in stress; this file contains no statistics on SPY reactions at prior-session highs/lows (sealed experiment).

## Sources
Primary data and official reports
- Cboe, VIX daily history 1990-2026-10-13: https://cdn.cboe.com/api/global/us_indices/daily_prices/VIX_History.csv (all VIX levels, % changes, counts, decay and OPEN-field statistics computed from this file on 2026-10-14).
- Cboe, VIX methodology: https://cdn.cboe.com/api/global/us_indices/governance/Volatility_Index_Methodology_Cboe_Volatility_Index.pdf
- FRED: SP500 https://fred.stlouisfed.org/series/SP500 ; DGS2 https://fred.stlouisfed.org/series/DGS2 ; DGS10 https://fred.stlouisfed.org/series/DGS10 (computed 2026-10-14).
- SEC/CFTC (2010) "Findings Regarding the Market Events of May 6, 2010": https://www.sec.gov/news/studies/2010/marketevents-report.pdf
- SEC DERA (2015) "Equity Market Volatility on August 24, 2015": https://www.sec.gov/marketstructure/research/equity_market_volatility.pdf
- SEC Staff (2021) "Staff Report on Equity and Options Market Structure Conditions in Early 2021": https://www.sec.gov/files/staff-report-equity-options-market-struction-conditions-early-2021.pdf
- SEC press release 2022-84 (Allianz Structured Alpha): https://www.sec.gov/news/press-release/2022-84 ; SEC press release 2022-29 (Infinity Q): https://www.sec.gov/news/press-release/2022-29
- Presidential Task Force on Market Mechanisms (Brady Commission) (1988) report; Federal Reserve Financial Stability Report (May 2021), Archegos.
- BIS Quarterly Review Mar 2018 "Volatility is back": https://www.bis.org/publ/qtrpdf/r_qt1803.htm ; BIS Quarterly Review Sep 2024 "Carry off, carry on": https://www.bis.org/publ/qtrpdf/r_qt2409.htm
- Schrimpf, A., Shin, H.S., Sushko, V. (2020) "Leverage and margin spirals in fixed income markets during the Covid-19 crisis," BIS Bulletin No. 2.

Academic
- Rubinstein, M. (1994) "Implied Binomial Trees," Journal of Finance.
- Jackwerth, J., Rubinstein, M. (1996) "Recovering Probability Distributions from Option Prices," Journal of Finance.
- Bates, D. (2000) "Post-'87 Crash Fears in the S&P 500 Futures Option Market," Journal of Econometrics.
- Roll, R. (1988) "The International Crash of October 1987," Financial Analysts Journal.
- Jorion, P. (2000) "Risk Management Lessons from Long-Term Capital Management," European Financial Management.
- Lowenstein, R. (2000) "When Genius Failed" (book).
- Khandani, A., Lo, A. (2007) "What Happened to the Quants in August 2007?" Journal of Investment Management; (2011) "What happened to the quants in August 2007? Evidence from factors and transactions data," Journal of Financial Markets.
- Brunnermeier, M., Pedersen, L. (2009) "Market Liquidity and Funding Liquidity," Review of Financial Studies.
- Brunnermeier, M. (2009) "Deciphering the Liquidity and Credit Crunch 2007-2008," Journal of Economic Perspectives.
- Kirilenko, A., Kyle, A., Samadi, M., Tuzun, T. (2017) "The Flash Crash: High-Frequency Trading in an Electronic Market," Journal of Finance.
- Bollen, N., Whaley, R. (2004) "Does Net Buying Pressure Affect the Shape of Implied Volatility Functions?" Journal of Finance.
- Garleanu, N., Pedersen, L., Poteshman, A. (2009) "Demand-Based Option Pricing," Review of Financial Studies.
- Ni, S., Pearson, N., Poteshman, A., White, J. (2021) "Does Option Trading Have a Pervasive Impact on Underlying Stock Prices?" Review of Financial Studies.
- Baltussen, G., Da, Z., Lammers, S., Martens, M. (2021) "Hedging demand and market intraday momentum," Journal of Financial Economics.
- Barbon, A., Buraschi, A. (2021) "Gamma Fragility," working paper.
- Carr, P., Wu, L. (2006) "A Tale of Two Indices," Journal of Derivatives.
- Demeterfi, K., Derman, E., Kamal, M., Zou, J. (1999) "More Than You Ever Wanted to Know About Volatility Swaps," Goldman Sachs QS Research Notes.
- Whaley, R. (2009) "Understanding the VIX," Journal of Portfolio Management.
- Dew-Becker, I., Giglio, S., Le, A., Rodriguez, M. (2017) "The price of variance risk," Journal of Financial Economics.
- Cheng, I.-H. (2019) "The VIX Premium," Review of Financial Studies.
- Todorov, V. (2010) "Variance Risk-Premium Dynamics: The Role of Jumps," Review of Financial Studies.
- Duffie, D. (2020) "Still the World's Safe Haven? Redesigning the U.S. Treasury Market after the COVID-19 Crisis," Hutchins Center Working Paper.
- Vissing-Jorgensen, A. (2021) "The Treasury Market in Spring 2020 and the Response of the Federal Reserve," Journal of Monetary Economics.
- Pinter, G. (2023) "An anatomy of the 2022 gilt market crisis," Bank of England Staff Working Paper [number uncertain].
- Beckmeyer, H., Branger, N., Gayda, L. (2023) "Retail Traders Love 0DTE Options... But Should They?" SSRN.
- Brogaard, J., Han, J., Won, P. (2023) "How Does Zero-Day-to-Expiry Options Trading Affect the Volatility of Underlying Assets?" SSRN.
- Bandi, F., Fusari, N., Reno, R. (2023) "0DTE option pricing," SSRN [title uncertain].

Secondary (narrative; checked against primary where possible, all accessed 2026-10-14)
- Wikipedia: Black Monday (1987); Long-Term Capital Management; 2010 flash crash; August 2011 stock markets fall; 2015-2016 stock market selloff; 2020 stock market crash; GameStop short squeeze; Archegos Capital Management; 2022 stock market decline; September 2022 United Kingdom mini-budget; Liability-driven investment strategy; Collapse of Silicon Valley Bank; List of stock market crashes and bear markets; 2025 stock market crash; 2025 United States federal government shutdown; 2026 Iran war; Economic impact of the 2026 Iran war; 2025 in the United States; 2026 in the United States; VIX.
- Web search was unavailable while drafting; items marked [uncertain] (Feb 2018 ETP AUM/flows and dates, LJM/Malachite/Parplus/Ronin sizes, 0DTE shares, OCC records, MOVE/VVIX levels, Cboe expiry-launch dates, 2025-26 spike attributions) should be re-verified against Cboe, OCC, SEC/CFTC and BIS before reliance.
