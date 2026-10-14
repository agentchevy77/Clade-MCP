# Option Pricing Theory: No-Arbitrage, Black-Scholes-Merton, and Beyond
domain_id: 02-pricing-theory | last_updated: 2026-10-14 | status: reviewed
scope: How listed options are priced: no-arbitrage relations, replication, BSM/Black-76/Bachelier, American exercise and early-exercise practice, implied volatility (European and American-style), risk-neutral densities and static replication, volatility-surface structure, smile dynamics and arbitrage constraints, event variance and the vol clock, local/stochastic/jump/rough volatility models, model-free variance (VIX) and variance-swap conventions, model risk, numerical methods.
confidence_notes: Core theory (parity, bounds, CRR, BSM, Black-76, Bachelier, Dupire, Heston, SABR, Breeden-Litzenberger, Carr-Madan static replication, variance-swap replication, Lee bounds, SVI/SSVI conditions) is well established and verified against primary papers/Cboe docs; the Cboe VIX strike-selection rule was verified against the Mathematics Methodology v5.0 (2026-02-26) on 2026-10-14; empirical magnitudes (VIX averages, variance risk premium, box-spread spreads, typical Heston/SABR fits, skew-stickiness ratio) are recency-sensitive and tagged; the rough-vs-path-dependent volatility debate is actively contested (2018-2026). Revised 2026-10-14 against two independent critiques (v1 retained as 02-pricing-theory.v1.md).

## Core concepts
- **Option**: right (not obligation) to buy (call) or sell (put) an underlying at strike K by/at expiry T. **European**: exercise only at T. **American**: any time up to T. Listed US single-stock/ETF options (e.g., SPY) are American; SPX, VIX, and most cash-settled index options are European. CME quarterly ES options are American-style; weekly and end-of-month ES options are reported to be European-style [CME specs unreachable 2026-10-14; uncertain, see Mechanisms].
- **Forward price** F = S·e^{(r−q)T} (S spot, r continuously compounded risk-free rate, q continuous dividend/borrow yield). Options are naturally priced off F, not S. **Log-moneyness** k = ln(K/F). **Total implied variance** w(k,T) = σ_imp(k,T)²·T.
- **No-arbitrage (NA)**: no self-financing strategy with zero cost, non-negative payoff and positive probability of gain. Every pricing result here is an NA consequence; the stronger results (BSM) also need a model.
- **Replication / delta hedging**: an option's payoff can be reproduced by dynamically trading the underlying and a bond; NA then forces the option price to equal the cost of the replicating portfolio. The hedge ratio is **delta** Δ = ∂V/∂S.
- **Risk-neutral measure Q**: the probability measure under which discounted traded prices are martingales (Harrison-Kreps 1979; Harrison-Pliska 1981). Prices = e^{−rT}·E^Q[payoff]. Q is not a forecast; it is a pricing device that embeds risk premia. Under Q, E^Q[S_T] = F.
- **Put-call parity (PCP)**: C − P = S·e^{−qT} − K·e^{−rT} = e^{−rT}(F − K) for Europeans (Stoll 1969). Model-free. American version is a pair of inequalities (see Formulas).
- **Box spread**: long call spread + long put spread at the same strikes K1<K2 (buy C(K1), sell C(K2), buy P(K2), sell P(K1)); European payoff is exactly K2−K1 regardless of S_T; price = (K2−K1)e^{−rT}, so box prices reveal the **implied financing rate** the options market actually uses.
- **Binomial tree (Cox-Ross-Rubinstein 1979)**: discrete-time lattice; the one-step replication argument yields a risk-neutral probability p; converges to BSM as steps → ∞. Handles American exercise natively.
- **Black-Scholes-Merton (BSM)** (Black-Scholes 1973; Merton 1973): closed-form European price under geometric Brownian motion (GBM) with constant σ, r, q. **Black-76** (Black 1976): same formula written on the forward/futures price F; standard for options on futures (ES, commodity options) and for VIX options (whose forward is the VIX future). **Bachelier (normal) model** (Bachelier 1900): arithmetic Brownian motion dF = σ_N dW; prices are linear in a "normal vol" quoted in price units (bp for rates, $/bbl for oil); the live convention for swaptions/caps and, since April 2020, for CME WTI-linked options (see Formulas).
- **Implied volatility (IV)**: the σ that, plugged into BSM/Black-76, reproduces the market price. Exists and is unique because the BSM price is strictly increasing in σ (vega > 0) between the NA bounds. IV is a *quoting convention*: a bijective re-expression of price that is comparable across strikes, maturities, and underlyings. For American-style quotes (SPY, single names) the BSM inverse is ill-posed in the money; IV must be backed out with an American pricer ("de-Americanized"; see Formulas).
- **Volatility surface**: σ_imp as a function of (K or k, T). **Smile**: IV higher at both wings than ATM. **Skew**: asymmetric smile; for equity indices the put wing is steep and IV generally rises as K falls (the "smirk"); the call wing is usually flat-to-slightly-rising at short maturities and turns up in rally regimes with heavy upside-call demand (observed in 2020-21 and 2024-25 [regime dates from market reporting; uncertain]) - check the call wing separately rather than assuming monotonicity. Single names are typically more symmetric with event-driven shapes. **Term structure**: ATM IV vs T. **Smile dynamics (sticky strike / sticky delta / sticky local vol)**: competing descriptions of how the surface moves when S moves; the empirical compromise is Bergomi's skew-stickiness ratio (defined in Formulas).
- **Risk-neutral density (RND)**: q(K) = e^{rT}·∂²C/∂K² (Breeden-Litzenberger 1978). The scaled butterfly spread is a discrete estimate. A negatively skewed surface ⇒ RND with fatter left tail than lognormal. **Static replication** (Carr-Madan 1998): any twice-differentiable European payoff is a forward plus a strip of vanillas weighted by f''(K) - the mechanism behind the 1/K² log contract (VIX), the moment strips (Cboe SKEW) and custom hedges; hence every model calibrated to the vanilla surface prices every *path-independent* European payoff identically, and model choice only matters for path-dependent products.
- **Static arbitrage**: arbitrage detectable from a single snapshot of prices: (i) **butterfly/convexity** (calls convex in K, equivalently RND ≥ 0); (ii) **calendar** (total variance nondecreasing in T at fixed k; operationally, forward variance ≥ 0); (iii) **wing growth** bounded by Lee's moment formula (Lee 2004): asymptotic slope of w(k) in |k| is ≤ 2.
- **SVI / SSVI** (Gatheral 2004; Gatheral-Jacquier 2014): parametric slice and surface fits that can be constrained to be free of static arbitrage.
- **Local volatility (LV)** (Dupire 1994; Derman-Kani 1994): σ_loc(S,t) deterministic function chosen so a one-factor diffusion fits the whole surface exactly. **Stochastic volatility (SV)**: variance is its own random process (Hull-White 1987; Heston 1993; SABR, Hagan et al. 2002). **Jump-diffusion**: Merton 1976 (lognormal jumps), Kou 2002 (double-exponential). **Bates 1996**: Heston + Merton jumps. **Rough volatility**: log-vol driven by fractional Brownian motion with Hurst H ≈ 0.1 (Gatheral-Jaisson-Rosenbaum 2018; later cross-asset work puts equity indices nearer 0.2, see Empirical magnitudes). **Path-dependent volatility (PDV)**: vol as a deterministic function of past returns (Guyon-Lekeufack 2023).
- **Event variance and the vol clock**: total implied variance decomposes into a diffusive part running on a business-time clock (weekends/holidays nearly weightless) plus lumps of variance at scheduled events (earnings, FOMC, CPI). An inverted calendar-time IV term structure across an event is neither arbitrage nor "stress" (see Formulas).
- **Variance swap**: forward contract on realized variance; fair strike is model-free replicable by a strip of OTM options weighted 1/K² (Demeterfi-Derman-Kamal-Zou 1999; log-contract of Neuberger 1994). **VIX** is the Cboe implementation: 30-day model-free expected variance from SPX option mid-quotes, square-rooted and ×100.
- **Early-exercise premium (EEP)**: American minus European value. Drivers: dividends and hard-to-borrow fees (calls), interest on strike (puts), and for premium-upfront options on futures both sides.
- **Model risk**: losses from using a model whose assumptions fail (BSM: fat tails, vol clustering, leverage effect, jumps, discrete hedging, transaction costs, stochastic rates).

## Mechanisms
- **Why NA pricing works and who enforces it**: market makers and arbitrage desks (index-arb, delta-one, dealer vol desks) continuously check parity, boxes, vertical/butterfly/calendar bounds. Violations beyond transaction costs and financing are hit within milliseconds in SPX/SPY; what survives is a *band* of width set by bid-ask, borrow cost, and dividend uncertainty, not a point.
- **Replication argument (one step)**: with S going to S·u or S·d and dividends at continuous yield q reinvested, choose Δ shares and B bonds so that Δ·S·u·e^{qΔt} + B·e^{rΔt} = C_u and Δ·S·d·e^{qΔt} + B·e^{rΔt} = C_d. Then Δ = e^{−qΔt}(C_u − C_d)/(S(u−d)) and C = ΔS + B. Rearranging gives C = e^{−rΔt}[p·C_u + (1−p)·C_d] with p = (e^{(r−q)Δt} − d)/(u−d) (q = 0: p = (e^{rΔt} − d)/(u−d)). The real-world up-probability never enters: the hedge removes the directional bet, so only the *volatility* (spread between u and d) is priced. This is risk-neutral valuation.
- **Continuous-time hedged portfolio (BSM derivation sketch)**: Π = V − ΔS. With dS = μS dt + σS dW and Itô, dV = (V_t + ½σ²S²V_SS + μS V_S)dt + σS V_S dW. Choosing Δ = V_S cancels dW; Π is riskless, so dΠ = rΠ dt (plus dividend carry). Result: the BSM PDE V_t + ½σ²S²V_SS + (r−q)S V_S − rV = 0 with terminal payoff. μ drops out. Solving via heat-equation transform (or Feynman-Kac: V = e^{−rT}E^Q[payoff]) gives the closed form.
- **P&L of a delta-hedged option (the "fundamental theorem of derivatives trading")**: hedging an option bought at implied σ_i while the underlying realizes σ_r gives dP&L = ½·Γ·S²·(σ_r² − σ_i²)dt (El Karoui-Jeanblanc-Shreve 1998 robustness result). Consequences: (a) a long option earns if realized > implied, weighted by dollar gamma along the *path*; (b) the hedger's P&L depends on where S spends time (gamma is largest near K); (c) the option's "fair" vol is the vol that makes the expected hedging cost equal the premium - IV is the market's price of future gamma. **Discrete (trading-floor) form** per hedge interval, r = q = 0: P&L ≈ ½ΓS²(ΔS/S)² + Θ·Δt, and since Θ ≈ −½ΓS²σ_i²Δt for the hedged option, the breakeven move is |ΔS/S| = σ_i√Δt ≈ σ_i/16 per day: a long-gamma position needs the underlying to move more than the implied daily move to pay for theta. The continuous identity is the expectation of this; the realized term is noisy (Derman-Kamal 1999), so a "cheap" option needs realized > implied on average along the path, not on any given day.
- **Why the surface is not flat**: (1) returns have fat tails and jumps ⇒ OTM options are worth more than lognormal says (smile). (2) Leverage/feedback effect: vol rises when the index falls ⇒ negative spot-vol correlation ⇒ skew. (3) Post-October-1987 demand for crash protection and dealer short-gamma inventory constraints add a risk premium to OTM puts (Gârleanu-Pedersen-Poteshman 2009 demand-based pricing). (4) Vol is stochastic and mean-reverting ⇒ term structure (short-dated IV moves most) and curvature from vol-of-vol. (5) Single names: discrete dividends, borrow cost, and takeover/earnings jump risk create name-specific shapes.
- **Why IV is "a language"**: BSM is wrong as a *model* but useful as a *map*: quoting IV normalizes price for S, K, T, r, q; makes vega/gamma hedging comparable; supports surface interpolation; and any correct model must reproduce the market's IVs. Dealers hedge BSM Greeks against a *model* of surface moves (sticky strike/delta, SV, LV), not against BSM's own dynamics.
- **How the smile moves with spot (smile dynamics)**: Derman (1999) "Regimes of Volatility": *sticky strike* - σ_imp(K) unchanged when S moves (ATM vol slides along the fixed smile; delta = BSM delta); *sticky delta/moneyness* - σ_imp(k = ln K/F) unchanged (smile translates with spot); *sticky local vol* (implied tree) - fixed-strike vols move with spot and ATM vol moves twice as fast as the strike skew (Derman's rule of two). Bergomi's skew-stickiness ratio SSR (Formulas) classifies them: sticky delta 0, sticky strike 1, local vol → 2 at short maturity; measured short-dated SPX SSR ≈ 1.5 (Bergomi 2009, 2016) [from memory; verify], so neither pure heuristic gives the right delta; SSR reportedly rises toward 2 in sell-offs [uncertain].
- **Static replication of any European payoff (Carr-Madan 1998)**: a twice-differentiable f(S_T) equals a bond, a forward and a strip of puts below F and calls above F weighted by f''(K) (formula in Formulas). f = ln(S_T/F) gives f'' = −1/K² (the variance-swap strip); f = (ln S_T/F)^n gives the Bakshi-Kapadia-Madan (2003) moment strips behind Cboe SKEW; digitals and power payoffs get a surface-only price. Under continuous paths E^Q[ln(S_T/F)] = −½E^Q[∫σ²dt], which is why the log-contract strip price is the variance-swap strike.
- **How VIX is built and why it is a variance-swap strike**: the log contract's payoff ln(S_T/F) is statically replicated by the 1/K²-weighted strip of OTM puts and calls plus a forward; its Q-expectation equals −½·E^Q[∫σ²dt] under continuous paths, so a weighted strip price gives expected variance without a volatility model. Cboe computes this at two expirations and interpolates to 30 days. VIX futures are the market's forward price of that strip's square root; VIX options are priced and hedged against those futures, not against spot VIX, because spot VIX is not tradable and is strongly mean-reverting.
- **Why ES and VIX options use Black-76**: the hedging instrument is the future; the future's Q-drift is zero; discounting applies to the whole payoff. For ES (options on E-mini S&P futures, exercising into futures) the futures price already embeds r−q; CME quarterly ES options are American-style, while the weekly (Mon-Fri) and End-of-Month ES options are reported to be European-style [CME contract specs and Rulebook ch. 358A returned HTTP 503 on 2026-10-14; uncertain]. Both are premium-upfront (equity-style) options, so early exercise of ITM calls and puts can be optimal (intrinsic received early earns interest); for *futures-style margined* options (premium settled through variation margin, e.g. some ICE/Eurex/ASX contracts) early exercise is never optimal and the price is the *undiscounted* Black-76 value (Lieu 1990). For VIX options (European, cash-settled Wednesday morning to the VIX Special Opening Quotation; settlement ticker VRO [from training knowledge; Cboe specification page rendered empty fields on 2026-10-14, not re-verified]), the forward is the matching VIX future and PCP holds against that future: C − P = e^{−rT}(F_VIXfut − K). VIX option surfaces have *positive* skew (calls more expensive in IV terms) because VIX is bounded below, right-skewed and spikes.
- **Early exercise logic**: an American call on a non-dividend-paying stock is never exercised early (Merton 1973) *provided the stock can be shorted or lent at the risk-free rate*: selling it dominates (time value + interest on K). Caveat (Jensen-Pedersen 2016, "Early Option Exercise: Never Say Never", JFE 121(2)): when the borrow fee exceeds the interest on K (hard-to-borrow names; implied PCP financing rate < 0), deep-ITM calls trade at or below intrinsic and early exercise is optimal and routinely observed - expect assignment on short ITM calls in HTB names, and exercise rather than sell long ITM calls that are bid below parity. With discrete dividends, exercise can be optimal just before an ex-date when D exceeds the remaining time value, i.e. the matching put plus interest on K (Hull's necessary condition: D > K[1 − e^{−r(T−t_D)}]). American puts are exercised when the interest earned on K outweighs the time value, so deep-ITM puts with high r and long T carry EEP; rule of thumb: exercise when the put is bid at or below intrinsic (extrinsic < interest on K to expiry minus any dividend before expiry). Put EEP scales with r: ≈ 0 in zero-rate regimes (2009-15, 2020-21); at r ≈ 4-5% (2023-25) the worked CRR example's ~9% EEP is representative and short ITM puts carry real assignment risk. Dividends push put exercise after the ex-date; interest pushes it earlier.
- **Why models beyond BSM are needed and how practitioners pick**: path-independent European payoffs (digitals, power payoffs, any f(S_T)) are priced by the vanilla surface alone - every calibrated model agrees (static replication above), so use the arbitrage-free surface/RND directly. Model choice matters for *path-dependent* products. LV fits the surface exactly and is the standard first model for weakly path-dependent exotics (barriers, lookbacks, autocallables) because it reproduces vanillas, but it implies forward smiles that flatten (wrong for cliquets/forward-starts) and a spot-vol co-movement that is too rigid, so barrier prices are only partly right (hence LSV) and its hedges can move the wrong way (Hagan et al. 2002). SV gives realistic dynamics but cannot fit short-dated skew without jumps or roughness. Jump models fit short-dated smiles but have flat long-dated skew. Hybrids (Bates, LSV = local-stochastic vol) are the dealer norm for exotics; for vanilla quoting most desks use arbitrage-free parametric surfaces (SVI/SSVI) and reserve SV/LSV for risk.

## Formulas and quantitative rules
Variables: S spot; K strike; T years to expiry; r continuously compounded risk-free rate; q continuous dividend yield; σ volatility (annualized, decimal); F = S·e^{(r−q)T} forward; N(·) standard normal CDF, n(·) its PDF; D cash dividend; PV(D) its present value.

```
PUT-CALL PARITY AND BOUNDS (European; model-free)
C - P = S e^{-qT} - K e^{-rT} = e^{-rT}(F - K)
With discrete dividends: C - P = S - PV(D) - K e^{-rT}
Implied forward from a strike pair: F_imp = K + e^{rT}(C - P)   (use to back out implied dividend/borrow)
Two-unknown extraction (dealer practice): regress (C - P) on K across near-ATM strikes of one expiry:
  slope = -e^{-rT} (discount factor), intercept = S e^{-qT} = F e^{-rT}  =>  F and the market's own financing rate
  (consistent with the box rate) in one step. For American-style products use short-dated near-ATM strikes (EEP ~ 0)
  and treat the result as a band bounded by the American inequalities.
SPX convention: price off a discrete expected index-dividend stream ("dividend points" to each expiry), not a smooth q;
  cross-check the parity-implied dividends/financing against S&P 500 dividend futures / published forecasts.
Bounds: max(S e^{-qT} - K e^{-rT}, 0) <= C <= S e^{-qT};  max(K e^{-rT} - S e^{-qT}, 0) <= P <= K e^{-rT}
Vertical spread: 0 <= C(K1) - C(K2) <= (K2-K1) e^{-rT}, K1<K2;  slope -e^{-rT} <= dC/dK <= 0
Convexity: C(K) convex in K  <=>  butterfly >= 0

AMERICAN PARITY (inequalities; Merton 1973 / Hull)
No dividends:          S - K <= C_A - P_A <= S - K e^{-rT}
Discrete dividends:    S - PV(D) - K <= C_A - P_A <= S - K e^{-rT}
Also: P_A <= K (not K e^{-rT}); C_A = C_E on a non-dividend stock that can be shorted at the risk-free rate
  (fails in hard-to-borrow names: Jensen-Pedersen 2016).

BOX SPREAD AND IMPLIED FINANCING
Box(K1,K2) = C(K1) - C(K2) + P(K2) - P(K1);  European payoff = K2 - K1 at T
Price B = (K2 - K1) e^{-rT}  =>  implied r = -ln(B / (K2-K1)) / T
Example: SPX K1=5000, K2=6000, T=1y, B=950 => r = -ln(0.95) = 5.13%.  At r=4.5% fair B = 956.00.
Never sell an AMERICAN-style box (early assignment breaks the fixed payoff).
```

```
CRR BINOMIAL TREE (Cox-Ross-Rubinstein 1979)
dt = T/n;  u = e^{sigma sqrt(dt)};  d = 1/u;  p = (e^{(r-q)dt} - d)/(u - d);  disc = e^{-r dt}
V_node = disc [p V_up + (1-p) V_down];  American: V_node = max(V_node, intrinsic)
Worked: S=100,K=100,r=5%,q=0,sigma=20%,T=1 European call -> n=1: 12.16; n=10: 10.25; n=100: 10.431; n=1000: 10.4486; BSM: 10.4506
(convergence oscillates even/odd n; use large n, odd/even averaging, Richardson, or Leisen-Reimer 1996 for smooth convergence)
Same inputs, American put, n=500: 6.089 vs European put 5.570 => early-exercise premium ~0.52 (~9% of the put; a high-rate, r=5% example)
```

```
BLACK-SCHOLES-MERTON (continuous dividend yield q)
d1 = [ln(S/K) + (r - q + sigma^2/2) T] / (sigma sqrt(T));   d2 = d1 - sigma sqrt(T)
C = S e^{-qT} N(d1) - K e^{-rT} N(d2)
P = K e^{-rT} N(-d2) - S e^{-qT} N(-d1)
Interpretations: N(d2) = Q-probability S_T > K;  e^{-qT}N(d1) = call delta;  e^{-rT}N(d2) = -dC/dK (digital price).
Worked (S=100,K=100,r=5%,q=0,sigma=20%,T=1): d1=0.35, d2=0.15, N(d1)=0.6368, N(d2)=0.5596
  C = 10.4506,  P = 5.5735,  C-P = 4.8771 = 100 - 100 e^{-0.05}  (parity check)
  vega = S n(d1) sqrt(T) = 37.52 per unit sigma (0.375 per vol point)
With q=2%: C = 9.2270, P = 6.3301.   With r=q=0: C = P = 7.9656.
PDE: V_t + 1/2 sigma^2 S^2 V_SS + (r-q) S V_S - r V = 0
Assumptions: (1) GBM with constant sigma; (2) continuous frictionless trading, no costs/taxes; (3) constant r, borrow=lend;
(4) constant q (or none); (5) unrestricted short sales; (6) no arbitrage; (7) European; (8) no jumps.
```

```
BLACK-76 (options on futures / forwards; Black 1976)
d1 = [ln(F/K) + sigma^2 T/2] / (sigma sqrt(T));  d2 = d1 - sigma sqrt(T)
C = e^{-rT}[F N(d1) - K N(d2)];   P = e^{-rT}[K N(-d2) - F N(-d1)];   C - P = e^{-rT}(F - K)
Worked: F=100,K=100,r=5%,sigma=20%,T=1 -> C = P = 7.5771.   ES example: F=5500,K=5500,r=4%,sigma=15%,T=0.25 -> C = 162.9 index pts.
Futures-style (margined) options: drop the e^{-rT} (premium paid via variation margin; no early exercise) - Lieu 1990.
VIX options: set F = price of the VIX future expiring on the same Wednesday; T = time to the SOQ.
```

```
BACHELIER (NORMAL) MODEL:  dF = sigma_N dW   (Bachelier 1900; SABR beta = 0 is its stochastic-vol extension)
d = (F - K) / (sigma_N sqrt(T))
C = e^{-rT} [ (F - K) N(d) + sigma_N sqrt(T) n(d) ];   P = e^{-rT} [ (K - F) N(-d) + sigma_N sqrt(T) n(d) ]
ATM: C = P = e^{-rT} sigma_N sqrt(T / (2 pi)) ~ 0.399 e^{-rT} sigma_N sqrt(T)
Normal <-> lognormal vol (Hagan et al. 2002, leading order): sigma_N ~ sigma_LN (F - K)/ln(F/K) [1 - sigma_LN^2 T/24];  at K = F: sigma_N ~ sigma_LN F (1 - sigma_LN^2 T/24)
Use: rates (swaptions/caps quoted in bp normal vol; negative-rate era), and CME WTI-linked energy options since 2020-04-22
  after the -$37.63 May-2020 WTI settlement of 2020-04-20 (CME Clearing advisory "Switch to Bachelier Options Pricing Model",
  April 2020) [advisory number and exact effective date from memory; CME site unreachable 2026-10-14, uncertain].
Admits negative forwards/strikes; vega = e^{-rT} sqrt(T) n(d); delta = e^{-rT} N(d) (call).
```

```
DISCRETE DIVIDENDS
Escrowed model: price BSM on S~ = S - PV(dividends before T), same sigma. Simple, consistent with parity, but understates
  the volatility of the total asset and underprices options (esp. long-dated, many dividends); Haug-Haug-Lewis (2003) show this.
Forward/strike-split (Bos-Vandermark 2002): allocate each dividend between a spot adjustment and a strike adjustment by (t_D/T) weighting.
Spot ("liquidator") model (Haug-Haug-Lewis 2003): S jumps by D (floored at 0) at t_D; European price for one dividend is a
  one-dimensional numerical integral of BSM over the pre-dividend lognormal; extends to American via same integral or lattice.
Lattice approach (Vellekoop-Nieuwenhuis 2006): tree with interpolation at ex-dates; avoids the non-recombining explosion.
PCP consistency: C - P = S - PV(D) - K e^{-rT}.  Example: S=100, D=2 at t=0.5, r=5%, K=100, T=1 -> C-P = 2.926.
Index options (SPX): the market uses expected index dividend points per expiry (discrete stream from constituent ex-dates);
  a continuous q is adequate only for short-dated, far-from-ex-date-cluster expiries; single names: chunky dividends matter for T > ~6 months.
```

```
AMERICAN APPROXIMATIONS
MacMillan (1986) / Barone-Adesi-Whaley (1987) quadratic approximation (MacMillan: non-dividend stock; BAW generalize to cost of carry b = r - q):
  M = 2r/sigma^2,  Nb = 2b/sigma^2,  Kt = 1 - e^{-rT},  q2 = [-(Nb-1) + sqrt((Nb-1)^2 + 4M/Kt)]/2
  S* solves  S* - K = c(S*) + [1 - e^{-qT} N(d1(S*))] S*/q2
  C_A = c(S) + A2 (S/S*)^{q2} for S < S*, else S - K;  A2 = (S*/q2)[1 - e^{-qT} N(d1(S*))]
  (put analogous with q1 using the negative root). Fast; errors largest for long-dated, high-r.
Bjerksund-Stensland (1993): single flat exercise boundary -> closed form lower bound; (2002): two-period flat boundary, tighter;
  needs an accurate bivariate normal (Genz). Lower bound because the flat-boundary strategy is feasible but suboptimal.
Lattice: CRR/trinomial with max(continuation, intrinsic) at each node; standard reference method for listed equity options.
Longstaff-Schwartz LSM (2001): simulate paths; backward in time regress continuation value on basis functions of state
  (ITM paths only); exercise if intrinsic > fitted continuation. Needed for multi-factor/path-dependent American pricing.
```

```
IMPLIED VOLATILITY SOLVERS (European prices)
Target: find sigma with BSM(sigma) = C_mkt, C_mkt within NA bounds.
Newton-Raphson: sigma_{n+1} = sigma_n - [BSM(sigma_n) - C_mkt] / vega(sigma_n)
  Worked (C_mkt=10.4506, start 0.30): 0.30 -> 0.20036 -> 0.200000 -> converged (3 steps). Fails/oscillates for deep OTM (vega ~ 0).
Brent: bracketed (e.g., [1e-4, 5]) bisection + secant + inverse quadratic; robust, ~10-30 evaluations.
Jackel "Let's Be Rational" (Wilmott, Jan 2015): rational initial guess on the normalized Black price + 3rd-order Householder
  iterations; reported to reach machine precision in two iterations across the full strike/vol domain [two-iteration claim not re-checked
  against the paper]. Reference implementations: Jackel's C++ (jaeckel.org), py_vollib / lets_be_rational, MATLAB impvbybls 'jackel2016'.
  QuantLib's blackformula module (checked 2026-10-14, master) ships Newton plus Brenner-Subrahmanyam/Corrado-Miller, Chambers-Nawalkha,
  Radoicic-Stefanica and Li adaptive-SOR solvers, and Jackel's 2017 "Implied Normal Volatility" for Bachelier - not "Let's Be Rational".
Brenner-Subrahmanyam (1988) ATM seed: sigma ~ sqrt(2 pi / T) * C / S  (r=q=0): C=7.9656 gives 0.1997 vs true 0.20.

IV FOR AMERICAN-STYLE OPTIONS (SPY, single names, ES quarterlies) - "de-Americanization"
Invert an American pricer (CRR/trinomial with discrete dividends; BAW or Bjerksund-Stensland 2002 for speed), not BSM.
(1) Build the surface from OTM options only (puts below F, calls above), where EEP ~ 0 and BSM IV is usable.
(2) ITM quotes carry EEP and may sit at intrinsic (no BSM root, or a nonsense vol); do not use them for the smile -
    BSM-implied vols from ITM American puts (high r) and pre-ex-date ITM calls are biased high and create fake butterfly arbitrage.
(3) Back out the implied forward/dividends/borrow first (parity on near-ATM strikes or the ATM straddle), then solve.
(4) Vendors differ (OptionMetrics IvyDB: CRR binomial with projected discrete dividends [from documentation knowledge, not re-verified];
    Cboe/ORATS use their own), so IVs for the same quote can differ by ~0.5-1 vol point in ITM/short-dated/HTB cases [uncertain magnitude].
```

```
BREEDEN-LITZENBERGER RISK-NEUTRAL DENSITY
q(K) = e^{rT} d^2C/dK^2 ~ e^{rT} [C(K-dK) - 2C(K) + C(K+dK)] / dK^2
Worked (BSM S=100,r=5%,sigma=20%,T=1): dK=5 -> q(100)=0.01962; dK=1 -> 0.01972; exact lognormal 0.019724.
q(80)=0.0112, q(90)=0.0176, q(110)=0.0172, q(120)=0.0124 (lognormal right-skew in price space).
Checks: integral q = 1; E^Q[S_T] = F.  In practice: fit an arbitrage-free IV curve (SVI) first, then differentiate;
raw strike differences are dominated by bid-ask noise; wings must be extrapolated (Lee-consistent) to integrate to 1.
STATIC REPLICATION (Carr-Madan 1998): for twice-differentiable f,
  f(S_T) = f(F) + f'(F)(S_T - F) + int_0^F f''(K)(K - S_T)^+ dK + int_F^inf f''(K)(S_T - K)^+ dK
  Price = e^{-rT} f(F) + int_0^F f''(K) P(K) dK + int_F^inf f''(K) C(K) dK
  f = ln(S_T/F): f'' = -1/K^2 (log contract / variance swap);  f = (ln S_T/F)^n: Bakshi-Kapadia-Madan (2003) moment strips (Cboe SKEW);
  f = 1{S_T > K}: digital = -dC/dK (a vertical-spread limit) - no model needed for any path-independent European payoff.
```

```
STATIC ARBITRAGE CONSTRAINTS ON THE SURFACE (w = total implied variance, k = ln(K/F))
Calendar: w(k,T2) >= w(k,T1) for T2 > T1 at fixed k (Gatheral-Jacquier 2014, Lemma 2.1; requires proportional dividends).
Forward variance between T1 < T2 at fixed k: sigma_fwd^2 = (w2 - w1)/(T2 - T1) = (sigma2^2 T2 - sigma1^2 T1)/(T2 - T1);
  calendar arbitrage <=> sigma_fwd^2 < 0.  Example: 20% at 3m, 22% at 6m -> forward vol sqrt((0.0484*0.5 - 0.04*0.25)/0.25) = 23.8%.
  A calendar spread (long T2, short T1) is long forward variance at sigma_fwd; quote calendars in forward vol, not in the IV difference.
  Under continuous paths the implied forward variance is also the fair strike of a forward-starting variance swap.
Butterfly (Durrleman; G-J Lemma 2.2): a slice is free of butterfly arbitrage iff
  g(k) = (1 - k w'/(2w))^2 - (w'^2/4)(1/w + 1/4) + w''/2 >= 0  for all k   AND   lim_{k -> +inf} d_+(k) = -inf,  d_+ = -k/sqrt(w) + sqrt(w)/2;
  the second condition rules out probability mass escaping to infinity (right wing must grow slower than 2|k|).
Lee (2004) moment formula: for |k| large, w(k) <= 2|k|, i.e. asymptotic slope beta_R, beta_L in [0,2];
  beta_R = 2 - 4(sqrt(p~^2 + p~) - p~), p~ = sup{p : E^Q[S_T^{1+p}] < inf};  beta_L analogous with q~ = sup{q : E^Q[S_T^{-q}] < inf}.
  => IV grows at most like sqrt(2|k|/T) in the wings; never extrapolate IV linearly or flat without checking.
Moment explosions (Andersen-Piterbarg 2007): in Heston, SABR and most SV models E^Q[S_T^{1+p}] is infinite beyond a finite p* that
  depends on (T, rho, vol-of-vol), so Lee's slope bound binds and far-OTM wings (esp. calls with rho > 0, puts with rho < 0) are
  mis-priced by expansions such as Hagan's; check p* before using an SV model for wing extrapolation.
```

```
SVI (raw) slice: w(k) = a + b [rho (k - m) + sqrt((k - m)^2 + sigma^2)]
  a in R, b >= 0, |rho| < 1, m in R, sigma > 0, a + b sigma sqrt(1 - rho^2) >= 0;  Lee bound => b(1 + |rho|) <= 2.
  a: overall level; b: wing slope; rho: asymmetry (skew); m: horizontal shift; sigma: ATM curvature.
SSVI surface (Gatheral-Jacquier 2014): w(k, theta) = (theta/2) [1 + rho phi(theta) k + sqrt((phi(theta) k + rho)^2 + 1 - rho^2)],
  theta = ATM total variance at T.  Free of static arbitrage if: (1) d theta/dT >= 0; (2) 0 <= d(theta phi)/d theta <= (1/rho^2)(1 + sqrt(1 - rho^2)) phi;
  (3) theta phi(theta)(1 + |rho|) < 4; (4) theta phi(theta)^2 (1 + |rho|) <= 4.  Condition (3) is Lee's slope bound 2.
  Power-law phi(theta) = eta theta^{-gamma}, gamma in (0,1): passes the calendar conditions (Thm 4.1) but is butterfly-arbitrage-free only up to
  a maximum expiry (G-J Remark 4.4: condition (3) fails for large theta for any gamma; (4) fails for gamma < 1/2 at long T or gamma > 1/2 at short T);
  gamma = 1/2 makes the SVI-JW skew/wing parameters constant across expiries. For a surface guaranteed arbitrage-free at all T use
  phi = eta / (theta^gamma (1 + theta)^{1 - gamma}) with eta(1 + |rho|) <= 2 (G-J eq. 4.5); otherwise check (3)-(4) at your longest expiry.
  SSVI ATM skew (power law, gamma=1/2): d sigma_BS/dk |_{k=0} = rho eta / (2 sqrt(T))  -> skew decays like 1/sqrt(T).
```

```
SMILE DYNAMICS AND THE SKEW-STICKINESS RATIO (Derman 1999; Bergomi 2009, 2016)
SSR = (d sigma_ATM / d ln S) / (d sigma / dk |_ATM);  sticky delta: SSR = 0; sticky strike: SSR = 1; local vol: SSR -> 2 as T -> 0
Fixed-strike vol response:  d sigma(K) / d ln S ~ (SSR - 1) * d sigma/dk |_K
Smile-adjusted delta:  Delta ~ Delta_BSM + (vega / S) (SSR - 1) d sigma/dk |_K
  (sticky strike: Delta_BSM; sticky delta with negative skew: larger call delta; local vol: smaller call delta - Derman 1999, 2008 lecture 9)
Empirical: SPX short-dated SSR ~ 1.5 [Bergomi 2016 ch. 9, from memory; verify], so with d sigma/dk < 0 the hedge delta sits below BSM delta,
  halfway between sticky-strike and local-vol; the ratio is regime-dependent and must be re-estimated from fixed-strike vol regressions.
```

```
LOCAL VOLATILITY (Dupire 1994)
sigma_loc^2(K,T) = [dC/dT + (r - q) K dC/dK + q C] / (1/2 K^2 d^2C/dK^2)
In total-variance form (Gatheral 2006): sigma_loc^2 = (dw/dT) / g(k) with g as in the butterfly condition above
  => a surface is butterfly-arbitrage-free iff Dupire local variance is non-negative; calendar-free iff dw/dT >= 0.
Rule (Derman-Kani-Zou 1996; Gatheral 2006): implied vol ~ average of local vol along the path between F and K, so in a linear-skew
  approximation sigma_imp(K) ~ sigma_loc((F + K)/2), equivalently sigma_loc(x) ~ sigma_imp(2x - F): local vol varies with level about
  twice as fast as implied vol with strike (Derman's "rule of two"); short-dated implied skew ~ 1/2 x local-vol skew.
Limitation: LV forward smiles flatten with forward-start time; spot-vol dynamics are wrong (vol moves with S in a rigid way).
```

```
HESTON (1993)
dS = (r - q) S dt + sqrt(v) S dW1;  dv = kappa (theta - v) dt + xi sqrt(v) dW2;  corr(dW1, dW2) = rho
v0: initial variance (short-dated ATM level);  theta: long-run variance (long-dated ATM level);  kappa: mean-reversion speed
(term-structure convergence rate, half-life ln2/kappa);  xi: vol-of-vol (smile curvature, kurtosis);  rho: spot-vol correlation (skew sign/size).
Feller: 2 kappa theta > xi^2 keeps v > 0 (routinely violated by SPX calibrations).
Pricing via characteristic function (semi-closed form) + Fourier inversion (Carr-Madan, Lewis, COS); use the "little Heston trap"
formulation (Albrecher et al. 2007) to avoid complex-log discontinuities. Simulation: Andersen (2008) QE scheme.
Behavior: ATM skew decays ~1/T at long maturities; short-dated skew too flat vs SPX => add jumps (Bates) or roughness.
Calibration: minimize weighted squared IV (or vega-weighted price) errors over the surface; 5 parameters, often ill-posed (kappa-xi trade-off).
Order-of-magnitude SPX fits (sanity range for calibration output): v0 ~ 0.02-0.05, theta ~ 0.03-0.06, kappa ~ 1-3 (half-life 3-8 months),
  xi ~ 0.4-1.0, rho ~ -0.6 to -0.9  [ranges from experience; uncertain].  Gatheral (2006) SPX fit of 2005-09-15: v0 = 0.0174, theta = 0.0354,
  kappa = 1.3253, xi = 0.3877, rho = -0.7165 [quoted from memory; verify]  -> Feller ratio 2 kappa theta / xi^2 ~ 0.62 (violated).
  Andersen (2008) stress case: kappa = 0.5, theta = 0.04, xi = 1, rho = -0.9.
```

```
SABR (Hagan-Kumar-Lesniewski-Woodward 2002)
dF = alpha F^beta dW1;  d alpha = nu alpha dW2;  corr = rho.  beta in [0,1] (0 normal/Bachelier, 1 lognormal; backbone), rho skew, nu curvature, alpha level.
Hagan lognormal-IV expansion:
 sigma_B(K,F) ~ alpha / { (FK)^{(1-beta)/2} [1 + (1-beta)^2/24 ln^2(F/K) + (1-beta)^4/1920 ln^4(F/K)] } * (z/x(z)) *
   { 1 + [ (1-beta)^2 alpha^2 / (24 (FK)^{1-beta}) + rho beta nu alpha / (4 (FK)^{(1-beta)/2}) + (2 - 3 rho^2) nu^2 / 24 ] T }
 z = (nu/alpha) (FK)^{(1-beta)/2} ln(F/K);   x(z) = ln{ [sqrt(1 - 2 rho z + z^2) + z - rho] / (1 - rho) }
Issues: beta and rho are nearly collinear (fix beta; 0.5 was historical rates default); expansion degrades for long T or large nu*sqrt(T);
 implied density goes negative at low strikes (butterfly arbitrage) -> corrections (Obloj 2008), "Arbitrage-free SABR" PDE (Hagan et al. 2014),
 shifted/free-boundary SABR for negative rates (Antonov-Konikov-Spector 2015).
Equity sanity ranges (1-3 month SPX slices): beta = 1, rho ~ -0.5 to -0.8, nu ~ 0.5-1.5 [from experience; uncertain].
```

```
JUMP-DIFFUSION
Merton (1976): dS/S = (r - q - lambda kbar) dt + sigma dW + (e^J - 1) dN, J ~ N(mu_J, delta^2), kbar = e^{mu_J + delta^2/2} - 1
 Price = sum_{n>=0} e^{-lambda' T} (lambda' T)^n / n! * BSM(S, K, r_n, sigma_n, T),  lambda' = lambda (1 + kbar),
   sigma_n^2 = sigma^2 + n delta^2 / T,  r_n = r - lambda kbar + n ln(1 + kbar) / T
 Worked (S=K=100, r=5%, sigma=20%, T=1, lambda=0.1, mu_J=-10%, delta=15%): ATM call 10.70; implied vols of puts K=80/90/100/110:
   21.0% / 20.8% / 20.7% / 20.6% -> a negative skew from jumps alone; effect is largest at short T (jump risk does not scale with sqrt(T)).
Kou (2002): J double-exponential (up prob p, rates eta1, eta2); closed forms via Hh functions; heavier, asymmetric tails; tractable for barriers.
Bates (1996): Heston + Merton jumps; fits both short-dated smile (jumps) and long-dated skew (rho).
```

```
ROUGH VOLATILITY
RFSV (Gatheral-Jaisson-Rosenbaum 2018): log sigma_t = nu W^H_t (fractional Brownian motion), H ~ 0.1 estimated from realized vol.
rough Bergomi (Bayer-Friz-Gatheral 2016): v_u = xi_0(u) exp( eta sqrt(2H) int_0^u (u-s)^{H-1/2} dW_s - 1/2 eta^2 u^{2H} ), xi_0 = forward variance curve.
Implication: ATM skew ~ T^{H - 1/2} (H=0.1 -> T^{-0.4}; H=0.2 -> T^{-0.3}), matching the observed power-law skew term structure that Heston cannot produce.
rough Heston (El Euch-Rosenbaum 2019): characteristic function via fractional Riccati equation; calibration feasible.
```

```
EVENT VARIANCE AND THE VOL CLOCK
w(T) = sigma_d^2 tau(T) + sum_{events <= T} v_e,   tau = business-time clock (trading days, weekends/holidays ~ 0 weight; event days may be up-weighted),
  v_e = implied variance of each scheduled jump (earnings, FOMC, CPI).
From two expiries straddling one event:  v_e ~ w(T2) - w(T1) - sigma_d^2 (tau2 - tau1)   (sigma_d from the no-event expiry)
  Worked: ATM IV 18% at 5 trading days (no event), 30% at 10 trading days (includes earnings):
    w1 = 0.0324*5/252 = 0.000643;  w2 = 0.09*10/252 = 0.003571;  v_e = 0.003571 - 2*0.000643 = 0.002286  ->  implied 1-sd event move sqrt(v_e) = 4.8%
From the nearest straddle: implied sd ~ straddle/(0.8 S); expected absolute move ~ straddle/S (Patell-Wolfson 1979; Dubinsky-Johannes-Kaeck-Seeger 2019).
An inverted calendar-time IV term structure across an event is NOT calendar arbitrage: check w(T) nondecreasing, not IV.
Very short-dated options (T <= ~3 days): compute T in minutes to the settlement time - a.m.-settled SPX 8:30 CT (9:30 ET), p.m.-settled 15:00 CT
  (Cboe VIX Methodology convention) - and state which clock (calendar vs business time) you use; vendors differ, and the choice moves
  0-3 DTE IVs by several vol points. 0DTE was roughly half of SPX option volume in 2024 and 59% in full-year 2025 (Cboe release 2026-01-06), 61-66% in 2026.
```

```
MODEL-FREE VARIANCE AND VIX
Variance swap fair strike (Demeterfi-Derman-Kamal-Zou 1999), continuous paths, S* = any split point (use S* = F):
 K_var = (2/T) [ rT - (S0 e^{rT}/S* - 1) - ln(S*/S0) + e^{rT} int_0^{S*} P(K)/K^2 dK + e^{rT} int_{S*}^inf C(K)/K^2 dK ]
       = (2 e^{rT}/T) [ int_0^F P(K)/K^2 dK + int_F^inf C(K)/K^2 dK ]   when S* = F
Cboe VIX (discrete version; Cboe Volatility Index Mathematics Methodology v5.0, 2026-02-26, verified 2026-10-14):
 sigma^2 = (2/T) sum_i (dK_i / K_i^2) e^{RT} Q(K_i)  -  (1/T) (F/K0 - 1)^2
 F from the strike where |C - P| is smallest (lowest such strike on ties): F = K + e^{RT}(C - P);  K0 = first strike at/below F;  Q = bid-ask midpoint;
 dK_i = (K_{i+1} - K_{i-1})/2 for interior strikes; one-sided at the edges (lowest put: K_{i+1} - K_i; highest call: K_i - K_{i-1});
 OTM puts below K0, OTM calls above, both at K0 (averaged);
 strike selection: remove null quotes; EXCLUDE any option with a zero bid OR a zero ask; stop in each direction after two consecutive strikes
 with zero bid or zero ask (rule effective 2025-02-10; before that only zero-bid options were excluded); T in minutes/525,600;
 R = CMT Treasury yields cubic-splined.
 Near/next-term: SPX (incl. weeklys) with more than 23 and less than 37 days to expiry; interpolate the two variances to 30 days (43,200 min):
 VIX = 100 * sqrt{ [T1 s1^2 (NT2 - N30)/(NT2 - NT1) + T2 s2^2 (N30 - NT1)/(NT2 - NT1)] * N365/N30 }
Jensen: VIX future <= sqrt(forward variance strike); volatility swap strike <= variance swap strike (convexity adjustment).
Jumps: with jumps, E[RV] - K_log = (2/T) E[sum (e^J - 1 - J - J^2/2)] (Carr-Wu 2009): third-order in J, negative for down-jumps, so a crash
 makes realized variance EXCEED the log-contract value; small except in crashes.
Contract conventions: realized variance RV = (252/N) sum_{i=1}^N [ln(S_i/S_{i-1})]^2 x 100^2 (close-to-close, no mean subtraction, N trading days);
 variance-swap P&L = N_var (RV - K_var^2);  vega notional N_vega = 2 K_var N_var  (dollar P&L per vol point for small moves; N_var = N_vega/(2 K_var));
 VIX futures $1000 x index, VIX options $100 x index.
```

```
NUMERICAL METHODS (brief)
Finite differences: grid in x = ln S; explicit (stable only if dt small), implicit, Crank-Nicolson (2nd order; use Rannacher start-up
  to damp payoff-kink oscillations); American via PSOR or penalty; natural for 1-2 factors, barriers, Greeks by grid differencing.
Monte Carlo: V ~ e^{-rT} mean(payoff); error ~ 1/sqrt(N); variance reduction (antithetic, control variate with BSM, importance sampling),
  quasi-random (Sobol); needed for path-dependence and >2 factors; American via LSM.
Fourier: Carr-Madan (1999) damped call price c(k) = e^{-alpha k}/pi int_0^inf e^{-iuk} psi(u) du,
  psi(u) = e^{-rT} phi_T(u - (alpha+1)i) / (alpha^2 + alpha - u^2 + i(2alpha+1)u), FFT over a strike grid; alpha ~ 1-2.
  COS method (Fang-Oosterlee 2008) is faster/more accurate for the same characteristic functions. Any model with known phi (Heston, Bates, Kou, VG, CGMY, rough Heston).
```

## Empirical magnitudes
- BSM benchmark: S=100, K=100, r=5%, q=0, σ=20%, T=1 → call 10.4506, put 5.5735; American put (CRR n=500) ≈ 6.089 (computed 2026-10-14; stable reference).
- Rough-vol Hurst exponent: H ≈ 0.1 from realized-volatility estimates on equity indices (Gatheral-Jaisson-Rosenbaum 2018, Quant. Finance 18(6)); option-implied estimates from short-dated ATM SPX IV give H of order 0.3 (Livieri-Mouti-Pallavicini-Rosenbaum, arXiv:1702.02777, 2017/2018), attributed to the smoothing effect of time-to-maturity. Cross-asset realized-vol medians (Mouti, "Rough Volatility Across Assets", arXiv:2608.16749, submitted 2026-08-17, verified 2026-10-14): ~0.05 livestock, 0.07-0.10 rates/FX/agriculture/energy/metals, 0.13 single stocks, 0.20 equity indices; option-implied estimates for equity indices 0.21-0.28 (rates/FX: ATM-skew regression fails, R² ≈ 0), i.e. in this 2010-2025 dataset index roughness looks closer to H ≈ 0.2 than 0.1 [as of 2026, contested, see below]. A v1 citation "Eraker-Vilkov (2025), H ≈ 0.3" could not be found in arXiv or Crossref (their joint work is on 0DTE options) and has been dropped.
- Path dependence: up to ~90% of the variance of equity-index implied volatility and up to ~65% of future daily realized volatility is explained by weighted past returns (Guyon-Lekeufack 2023, Quant. Finance 23(9)) [R² figures consistent with the abstract; not re-verified 2026-10-14].
- Lee bound: wing slope of total variance ≤ 2; for SSVI this is θφ(θ)(1+|ρ|) ≤ 4 (Gatheral-Jacquier 2014, Remark 4.3).
- VIX construction constants: options with >23 and <37 days to expiry; 30-day target = 43,200 minutes; 365-day year = 525,600 minutes; 15-second quote snapshots; spot values computed 2:15-8:25 a.m. CT (GTH; 8:15 a.m. end in the 2019 document, 8:25 a.m. in current Cboe VIX specifications) and 8:30 a.m.-3:15 p.m. CT (RTH) per the 2019 VIX Methodology [GTH window may have changed with Cboe's 2021 GTH extension and 2025-announced 24x5 SPX/VIX sessions; uncertain]. Index-level filter (2019 VIX Methodology values): a spot value calculated within 2 minutes of the baseline that is ≥0.50 vol points *lower* than the baseline is suppressed (baseline republished); higher values, or drops ≤0.49, become the new baseline - upward moves are never filtered; the 2026 Mathematics Methodology states these as generic parameters ("threshold period (e.g., 5 minutes)", x vol points, subject to change). Cboe Volatility Index Mathematics Methodology, Version 5.0, Last Revised February 26, 2026 (Appendix 2; read 2026-10-14); its Appendix 1 logs (i) strike selection now excludes options with zero bid *or* zero ask (effective 2025-02-10; previously zero-bid only) and (ii) the Series-Level Filtering Algorithm (EMA-based outlier overlay on constituent quotes, formerly an appendix of the Cboe MSCI Volatility Indices Methodology) integrated as a formal section (effective 2025-08-25). Weighting formula unchanged.
- VIX settlement: final settlement value is a Special Opening Quotation (SOQ) using opening trade prices (or opening-quote midpoints) of the SPX options expiring 30 days after the VIX expiration, from a special opening auction (Cboe circular RG18-015; Cboe VIX options page). Expirations usually Wednesday; monthly and weekly expirations; settlement ticker VRO [from training knowledge; Cboe specifications page rendered with empty contract fields on 2026-10-14, not re-verified].
- Box-spread implied financing: Cboe (guest post, rates as of 2025-02-24) reported 3- and 5-year SPX box rates about 30-50 bp above matching Treasury yields and "often just 20 bp above benchmark rates" (5-year example 4.6%). A secondary summary of Cboe data reports 2025 box lending rates averaging ~26 bp over 3-month T-bills (range 6-44 bp in H1 2025) with a later widening to ~69 bp on dealer balance-sheet constraints [as of 2026-10, secondary source, not checked, uncertain]. Box rates track the SOFR/OIS curve more closely than T-bills.
- VIX level statistics (spot, 1990-01 to 2025-12): mean ≈ 19.4, median ≈ 17.6, modal region 12-15, 90th percentile ≈ 28.5 (Cboe history 1990-01 to 2026-10, see 04-volatility); record closes 9.14 (2017-11-03) and 82.69 (2020-03-16); VXO on OEX available from 1986 [values from memory; re-verify against Cboe history before quoting; as of 2025]. Use the median, not the mean, as the "normal" level: the distribution is right-skewed and regime-clustered, and roughly a third of days print below 15 [uncertain].
- Variance risk premium: SPX implied variance exceeds subsequently realized variance on average (Carr-Wu 2009, RFS 22(3), found strongly negative variance risk premia, i.e., variance-swap buyers pay a premium; the commonly cited mean log ratio of realized to swap variance for SPX is roughly −0.5 to −0.7 [not re-verified; uncertain]); in vol points the VIX-minus-realized gap averages a few points (commonly cited 3-5 pts) but is negative in crashes [uncertain magnitude; as of 2025].
- SPX ATM skew term structure decays approximately as a power law T^{−0.4} (Gatheral 2006; Gatheral-Jaisson-Rosenbaum 2018), far slower than Heston's 1/T at long T and steeper at short T; a Mouti-type H ≈ 0.2 implies T^{−0.3} instead.
- CRR convergence: error at n=100 ≈ 0.02 on a 10.45 call (0.2%); at n=1000 ≈ 0.002.
- Execution-side change relevant to VIX pricing relationships: SEC Release No. 34-106216 (File No. SR-CBOE-2026-004), "Notice of Filing of Amendment No. 1 and Order Granting Accelerated Approval of a Proposed Rule Change, as Modified by Amendment Nos. 1 and 2, To Adopt 'VIX Future-Option Orders'", published 2026-09-02 at 91 FR 56493-56504 (FR Doc. 2026-17908; verified via the Federal Register API 2026-10-14; the API exposes no signing date, so the v1 "notice dated 2026-08-28" is unverified). Earlier FR notices: 2026-01-16 (filing), 2026-02-24 and 2026-07-13 (longer period), 2026-04-14 (proceedings) [from the critique's API query; not independently re-fetched]. The order allows packaged execution of VIX options with VX futures.

## Practitioner heuristics
- **Price off the forward, not spot**: use F = S·e^{(r−q)T} or the implied forward from PCP at the ATM strike (or the (C−P)-on-K regression for both F and the discount factor); use the OIS/SOFR curve (or the box-implied rate for SPX) rather than T-bills; for single names back out implied borrow/dividends from parity and watch for hard-to-borrow names where puts trade rich (implied rate negative) and ITM calls get exercised early.
- **ATM approximations** (at the *forward* strike, Brenner-Subrahmanyam 1988): C_ATMF ≈ 0.4·F·e^{−rT}·σ·√T = P_ATMF; straddle ≈ 0.8·F·e^{−rT}·σ√T; relative error ≈ σ²T/24 (from C_ATMF = F e^{−rT}σ√T n(0)(1 − σ²T/24 + …)), so fine while σ√T ≲ 0.5 (20% vol out to ~6y, 60% vol only to ~8 months: 50% vol at 1y ≈ 1% error, 20% vol at 1y ≈ 0.17%). It is a forward-strike approximation: for high r−q or long T the spot-ATM option differs materially, and a steep smile shifts the straddle minimum off ATM. The "rule of 16" (daily σ ≈ annual σ/16, √252 ≈ 15.9) assumes 252 trading days and no event clustering; 1-σ expected move ≈ S·σ·√T.
- **Gamma-theta breakeven**: daily breakeven move ≈ σ_imp/16 (e.g. 20% IV ⇒ 1.25%/day); below it a long-gamma book bleeds theta, above it short gamma loses. Judge long/short gamma by realized-vs-implied *over the holding period*, not a single day.
- **Delta-hedged P&L = ½ΓS²(σ_r² − σ_i²) dt**: the option is "cheap" only if realized vol will exceed implied *where gamma is large*; vol realized far from the strike is nearly worthless to a long gamma position.
- **Skew rule of thumb (Derman's "rule of two")**: implied vol at strike K ≈ local vol at the midpoint (F+K)/2; equivalently σ_loc(K) ≈ σ_imp(2K−F); local vol varies with level about twice as fast as implied vol with strike, so short-dated implied skew ≈ ½ local-vol skew. Breaks for long-dated and jump-dominated short-dated smiles.
- **Term-structure regime**: in calm markets short IV < long IV (contango) and VIX futures in contango; inversion (backwardation) of the *diffusive* term structure signals stress. Exception: an inverted IV term structure across a scheduled event (single-name earnings week, FOMC/CPI for the index) is event variance, not stress - strip the event (v_e) before reading the regime. Mean-reversion speed of the surface is faster at the front.
- **Calendar spreads in forward vol**: quote and risk a calendar as forward variance σ_fwd² = (w2 − w1)/(T2 − T1); a "cheap" back-month on an IV-difference basis can be rich in forward vol when the front holds an event.
- **Surface sanity before any model**: check total variance nondecreasing in T at fixed k (forward variance ≥ 0); butterfly g(k) ≥ 0 plus the d₊ → −∞ wing condition; wing slopes ≤ 2; fit SVI per slice then enforce calendar condition between slices (G-J Lemma 3.3 / Theorem 4.1), or fit SSVI with power-law φ and verify the four corollary conditions at the longest expiry.
- **IV solver discipline**: use Jäckel's algorithm or a bracketed Brent for European quotes; Newton alone diverges when vega is tiny (deep OTM, short-dated); for American-style quotes invert an American pricer and build the smile from OTM options only; IV from mid-quotes can embed arbitrage - compute IV from bid and ask separately to get an IV band.
- **Model choice by product**: vanilla quoting → arbitrage-free parametric surface (SVI/SSVI/spline); any path-independent European payoff (digitals, power/variance payoffs) → the surface/RND itself, no dynamic model; barriers, lookbacks, autocallables (weakly path-dependent) → LV or LSV; cliquets/forward-starts/vol derivatives (forward-skew-dependent) → SV or rough vol; American listed options → CRR/trinomial (n ≥ 200-500) or Bjerksund-Stensland 2002 for speed; multi-asset American → LSM.
- **Heston use**: expect Feller violation; calibrate to the maturities you trade; do not trust the 1-week smile (add jumps); use QE simulation not Euler; reject fits outside the sanity ranges above without a reason.
- **SABR use**: fix β (0.5 or 1 in equities/commodities; normal/shifted in rates), calibrate α, ρ, ν per expiry; check the implied density for negativity below ~F·e^{−2σ√T}; do not extrapolate wings beyond the model's moment explosion.
- **VIX options**: never price off spot VIX; the underlying is the matching VX future; expect positive skew and IVs frequently far above the index's own vol; PCP with the future; the settlement is a Wednesday-morning SOQ that can differ materially from the prior close.
- **ES options vs SPX options**: both are quoted in Black-76/BSM terms; ES options exercise into futures, and the quarterly ES options are American-style (weekly/EOM reported European [uncertain]); the small EEP matters only deep ITM or when rates are high; ES and SPX implied forwards differ by the basis (dividends and financing), so compare the two surfaces in forward moneyness.
- **Assignment-risk calendar**: short ITM calls are at risk the day before each ex-dividend date (SPY: quarterly, third-Friday-of-March/June/September/December cluster) when D exceeds the matching put price plus interest on K, and at any time in hard-to-borrow names; short ITM puts are at risk whenever they trade near intrinsic at high r; check the OCC for strike adjustments after special dividends.
- **Dividends**: escrowed model is fine for short-dated index options with smooth yields; for single names with chunky dividends and T > 6 months, use the spot/lattice treatment; for SPX use the dividend-point stream.
- **Discrete hedging error** (Derman-Kamal 1999): standard deviation of hedging P&L for an option hedged n times ≈ √(π/4)·σ·vega/√n; for an ATM option σ·vega ≈ premium, so std ≈ 0.89·premium/√n - daily hedging of a 1-month option (n≈21) ≈ 19% of premium, hourly ≈ 7.5%. Hedge-frequency and transaction costs set a floor on how finely BSM can be realized. **Leland (1985)**: hedging a *short* option every Δt with proportional cost k is priced with σ_L² = σ²[1 + √(2/π)·k/(σ√Δt)]; use the "−" sign for a *long* option (lower vol, lower value). Valid only for payoffs whose gamma has one sign; mixed-gamma books need the Hoggard-Whalley-Wilmott (1994) nonlinear PDE.

## Common misconceptions and pitfalls
- "BSM assumes investors are risk-neutral." No: risk-neutral valuation is a consequence of replication; the real-world drift μ cancels. Risk aversion lives in Q through the pricing of variance and jump risk, which is why IV ≠ forecast of realized vol.
- "IV is the market's forecast of realized volatility." IV embeds a (usually positive) variance risk premium, skew effects, and supply-demand; on average implied > realized.
- "Delta is the probability of finishing ITM." N(d1) is the hedge ratio; N(d2) is the Q-probability of S_T > K; neither is a real-world probability.
- "Put-call parity holds for American options." Only as inequalities; the band width is the EEP difference. Early assignment on short legs breaks boxes, conversions and reversals in American-style products.
- "A call should never be exercised early on a non-dividend stock." True only when the stock can be shorted/lent at the risk-free rate. In hard-to-borrow names (borrow fee > interest on K) deep-ITM calls trade below parity and early exercise is optimal (Jensen-Pedersen 2016); otherwise sell rather than exercise, except immediately before an ex-dividend date when D exceeds the matching put plus interest on K (and for puts when interest on K beats time value).
- "The smile shows BSM is wrong, so BSM should be abandoned." The smile is quoted *in* BSM units; BSM is a transform, not a forecast. The errors come from using BSM Greeks with BSM's own dynamics (flat-vol moves).
- "You need a stochastic-vol model to price a digital or a power payoff." No: every model fitted to the vanilla surface gives the same price for any path-independent European payoff (Carr-Madan); the model only matters for barriers, forward-starts and other path-dependent claims.
- "Local vol fits perfectly, therefore it is the right model." Exact fit ≠ correct dynamics; LV forward smiles flatten and its deltas are often worse than sticky-delta (Hagan et al. 2002). Exotics priced with LV vs SV can differ by multiples of the bid-ask.
- "My delta is the BSM delta." Only under sticky strike. With SSR ≈ 1.5 on short-dated SPX, the hedge delta of a call sits below BSM delta (Formulas: smile-adjusted delta); using the wrong regime is a systematic, not random, hedging error.
- "An inverted IV term structure is calendar arbitrage / stress." Check total variance, not IV: w(T) can be nondecreasing while IV falls with T, and an earnings or macro date produces exactly this.
- "Variance swap ≈ volatility swap ≈ VIX." Volatility swap strike < variance swap strike (Jensen); VIX² is the variance-swap-like strip, VIX futures are < √(forward variance strike), and VIX options trade off the futures. Sizing: a vol swap "in vega" and a variance swap in variance notional differ by the factor 2K_var.
- "VIX is an average implied volatility." It is a strike-weighted strip (1/K² weights) that loads on OTM puts; skew raises VIX relative to ATM IV.
- "BSM IV is fine for SPY/single-name options." BSM inversion of an American price has no root (or a biased one) when the quote sits at intrinsic; ITM American puts at high r and pre-ex-date ITM calls produce fake smiles and spurious butterfly arbitrage. De-Americanize and use OTM quotes.
- Rates and time: mixing trading-day and calendar-day time, using T-bill instead of OIS/box rates, and ignoring the settlement-time convention (a.m. vs p.m.) produce IV errors of a vol point or more at the front end; the file's rule: T in minutes to the settlement time for T ≤ 3 days, business-time clock with explicit event weights beyond that, and state the convention.
- Breeden-Litzenberger on raw quotes: second differences of noisy mids give negative densities; smooth in IV space first, extrapolate wings consistently, and verify the density integrates to 1 with mean F.
- "Heston can fit any surface." Not short-dated skew; and parameter sets from different days are unstable (κ-ξ-ρ trade-offs) unless regularized.
- "Hagan SABR is arbitrage-free." The expansion yields negative densities at low strikes for long maturities; use arbitrage-free SABR or cap the usable strike range.
- Truncation in VIX: the stopping rule (two consecutive strikes with zero bid *or* zero ask since 2025-02-10) and the discrete strike grid make the index a biased (slightly low) estimate of the continuous strip in illiquid wings; the (F/K0 − 1)² term corrects for the ATM discretization only. The 2025 rule tightens truncation versus the 2019 zero-bid-only rule, so wing contributions can drop out earlier in illiquid sessions.
- Leland with the wrong sign: applying the "+" adjustment to a long-option book over-marks it; the sign follows the sign of the book's gamma.
- CRR with too few steps: even/odd oscillation of 0.5-2% around the true price for n < 50; use n ≥ 200 or Leisen-Reimer.

## Contested or uncertain claims
- **Rough vs path-dependent vs artefact**: Gatheral-Jaisson-Rosenbaum (2018) argue H ≈ 0.1 roughness is a universal feature; Cont-Das ("Rough Volatility: Fact or Artefact?", Sankhya B 86(1), 191-223, 2024, DOI 10.1007/s13571-024-00322-2, online 2024-02-21; arXiv:2203.13820 v3 2023-07-10; verified via Crossref 2026-10-14) show realized-volatility estimators display apparent H < 0.5 even when spot volatility is smooth; Livieri et al. (2017/2018) find H ≈ 0.3 from option-implied data; Mouti (2026) finds equity-index medians ≈ 0.20 realized and 0.21-0.28 option-implied after mean-reversion and noise corrections, i.e. less rough than the original H ≈ 0.1 for indices; Guyon-Lekeufack (2023) show a simple PDV model explains most of IV variation endogenously and argue PDV is the more parsimonious description, with "The implied volatility surface (also) is path-dependent" (arXiv 2312.15950 [not fetched]) extending this. Consensus as of 2026: the ATM-skew power-law term structure is a robust empirical fact; whether its source is fractional noise or deterministic path dependence, and whether the index exponent is nearer 0.1 or 0.2, is open. Reviewer disagreement resolved: one critique could not verify arXiv:2608.16749; it was fetched directly on 2026-10-14 and the figures above are from its abstract.
- **Source of the index skew**: jumps (Carr-Wu 2003 "What type of process underlies options?" argue short-dated smiles require jumps) vs leverage effect/stochastic vol vs demand pressure (Gârleanu-Pedersen-Poteshman 2009). Most desks treat it as all three; the weights matter for hedging short-dated puts.
- **Hedging: local vol vs sticky-delta vs SV deltas**: Hagan et al. (2002) claim LV deltas are wrong-signed in the smile correction; Dupire-school practitioners argue LV deltas are right when the surface is sticky-strike. Bergomi's SSR ≈ 1.5 for short-dated SPX [from memory] says the truth sits between; regime-dependent (SSR reportedly higher in sell-offs [uncertain]); LSV is the compromise.
- **Which rate is "risk-free" for option pricing**: T-bill CMT (what Cboe VIX uses), SOFR/OIS (what dealers fund at), or the box-implied rate (what the SPX market itself embeds, typically tens of bp above Treasuries). Differences are small for T < 3 months and material for LEAPS.
- **SABR β identification**: β and ρ are nearly observationally equivalent in a single slice; some fix β from the backbone (ATM vol vs F dynamics), others from fit. No consensus.
- **Variance risk premium interpretation**: compensation for crash/variance risk (rational pricing) vs dealer inventory and demand effects vs peso-problem sample bias; magnitudes shift with regime (post-2020 0DTE growth may have altered front-end premia) [uncertain, recency-sensitive].
- **Cboe VIX methodology changes**: the weighting formula is unchanged, but the strike-selection rule did change on 2025-02-10 (zero bid *or* zero ask exclusion and stopping rule; verified in Mathematics Methodology v5.0 Appendix 1), and the series-level quote filter was formalized 2025-08-25. The VIX-specific white paper at the 2019 URL remains the 2019-07-26 version, so whether the 2-minute/0.50-point index-level filter parameters are still in force is unverified [uncertain]. v1 of this file stated "no 2025-2026 change beyond filtering/governance"; corrected.
- **ES option exercise style**: quarterly ES options are American-style; one critique states weekly and EOM ES options are European-style. CME contract specifications and Rulebook Chapter 358A were unreachable (HTTP 503) on 2026-10-14, so the blanket v1 claim "ES options are American" has been narrowed and tagged [uncertain].
- **QuantLib and "Let's Be Rational"**: v1 listed QuantLib as an industry default implementation; the master blackformula.hpp (read 2026-10-14) contains no Let's-Be-Rational solver (it cites Jäckel only for the 2017 implied *normal* volatility routine). Corrected.
- **Bachelier switch at CME**: the April 2020 switch for WTI-linked options is well documented in market reporting; the advisory number (recalled as CME Clearing Advisory 20-171) and the 2020-04-22 effective date could not be re-fetched [uncertain].

## Relationships to other domains
- **03 (Greeks)**: every Greek here is a partial derivative of the formulas above (BSM/Black-76/Bachelier delta, gamma, vega, theta, rho; SV/LV model Greeks and the sticky-strike vs sticky-delta choice). The ½ΓS²(σ_r²−σ_i²) P&L identity, the gamma-theta breakeven and the SSR-adjusted delta are the bridges between pricing and hedging.
- **05 (dealer positioning and option flows) / 0DTE**: front-end variance risk premia, intraday gamma effects and the event-variance/vol-clock conventions for 0-3 DTE options link pricing to flow; the demand-based pricing mechanism (Gârleanu-Pedersen-Poteshman) is the theoretical hook.
- **Market structure / products domain (09)** (SPX vs SPY vs ES vs VIX contract specs, settlement conventions, a.m./p.m. settlement, exercise style, futures-style vs equity-style margining): pricing conventions (European vs American, Black-76 vs BSM, settlement time in T) depend on those specs; VIX settlement (SOQ/VRO) and VIX futures listing are defined there.
- **Volatility products / VIX domain (04)**: the variance-swap replication, the VIX formula, forward variance and the contract conventions here are the theoretical basis for VIX futures/options, variance swaps, and volatility ETPs; the futures-vs-spot distinction is the key link.
- **Volatility surface / skew trading domain**: SVI/SSVI, Lee bounds, Breeden-Litzenberger, Carr-Madan replication and the skew/smile-dynamics mechanisms here are the tools used for relative-value and dispersion trading.
- **Events / earnings and empirical return distribution domains (08, 10)**: fat tails, vol clustering and the leverage effect are the reasons the surface departs from BSM; scheduled-event variance is priced with the decomposition above; realized-vol estimation (and its roughness/path-dependence debate) feeds vol forecasting.
- **Key levels / support-resistance (general literature only)**: option-pricing theory enters via strike concentration (dealer gamma positioning near heavily traded strikes) and pin risk at expiry; this file deliberately contains no statistics on price reactions at any specific level type, per the governance constraint.
- **Risk management domain (13)**: model risk, discrete-hedging error, Leland costs and assignment risk quantified here set hedging-frequency and reserve policies.

## Sources
Academic/primary papers (verified titles and venues unless marked):
- Bachelier, L. (1900) "Théorie de la spéculation", Annales scientifiques de l'École Normale Supérieure 17.
- Black, F. & Scholes, M. (1973) "The Pricing of Options and Corporate Liabilities", Journal of Political Economy 81(3).
- Merton, R. C. (1973) "Theory of Rational Option Pricing", Bell Journal of Economics and Management Science 4(1).
- Merton, R. C. (1976) "Option Pricing When Underlying Stock Returns Are Discontinuous", Journal of Financial Economics 3.
- Black, F. (1976) "The Pricing of Commodity Contracts", Journal of Financial Economics 3.
- Cox, J., Ross, S. & Rubinstein, M. (1979) "Option Pricing: A Simplified Approach", Journal of Financial Economics 7.
- Stoll, H. (1969) "The Relationship Between Put and Call Option Prices", Journal of Finance 24.
- Harrison, J. M. & Kreps, D. (1979) "Martingales and Arbitrage in Multiperiod Securities Markets", Journal of Economic Theory 20; Harrison, J. M. & Pliska, S. (1981) "Martingales and Stochastic Integrals in the Theory of Continuous Trading", Stochastic Processes and their Applications 11.
- Breeden, D. & Litzenberger, R. (1978) "Prices of State-Contingent Claims Implicit in Option Prices", Journal of Business 51(4).
- Carr, P. & Madan, D. (1998) "Towards a Theory of Volatility Trading", in Jarrow, R. (ed.) Volatility: New Estimation Techniques for Pricing Derivatives, Risk Books.
- MacMillan, L. W. (1986) "Analytic Approximation for the American Put Option", Advances in Futures and Options Research 1, 119-139.
- Barone-Adesi, G. & Whaley, R. (1987) "Efficient Analytic Approximation of American Option Values", Journal of Finance 42(2), 301-320.
- Bjerksund, P. & Stensland, G. (1993) "Closed-Form Approximation of American Options", Scandinavian Journal of Management 9; (2002) "Closed Form Valuation of American Options", NHH Discussion Paper 2002/09, https://openaccess.nhh.no/nhh-xmlui/handle/11250/163705
- Longstaff, F. & Schwartz, E. (2001) "Valuing American Options by Simulation: A Simple Least-Squares Approach", Review of Financial Studies 14(1).
- Jensen, M. V. & Pedersen, L. H. (2016) "Early Option Exercise: Never Say Never", Journal of Financial Economics 121(2), 278-299, DOI 10.1016/j.jfineco.2016.05.008 (verified via Crossref 2026-10-14).
- Lieu, D. (1990) "Option Pricing with Futures-Style Margining", Journal of Futures Markets 10(4) [citation from memory].
- Haug, E. G., Haug, J. & Lewis, A. (2003) "Back to Basics: A New Approach to the Discrete Dividend Problem", Wilmott Magazine 2003(5), Sept 2003, pp. 37-47; reprinted in Haug (2007) Derivatives: Models on Models, Wiley [reprint chapter number not verified].
- Bos, M. & Vandermark, S. (2002) "Finessing Fixed Dividends", Risk (Sept 2002).
- Vellekoop, M. & Nieuwenhuis, J. (2006) "Efficient Pricing of Derivatives on Assets with Discrete Dividends", Applied Mathematical Finance 13(3).
- Jäckel, P. (2015) "Let's Be Rational", Wilmott Magazine (Jan 2015), DOI 10.1002/wilm.10395; Jäckel, P. (2006) "By Implication", Wilmott Magazine; Jäckel, P. (2017) "Implied Normal Volatility", Wilmott Magazine.
- Brenner, M. & Subrahmanyam, M. (1988) "A Simple Formula to Compute the Implied Standard Deviation", Financial Analysts Journal 44(5).
- Lee, R. W. (2004) "The Moment Formula for Implied Volatility at Extreme Strikes", Mathematical Finance 14(3), 469-480.
- Andersen, L. & Piterbarg, V. (2007) "Moment Explosions in Stochastic Volatility Models", Finance and Stochastics 11(1), 29-50.
- Gatheral, J. (2004) "A Parsimonious Arbitrage-Free Implied Volatility Parameterization with Application to the Valuation of Volatility Derivatives", Global Derivatives & Risk Management presentation (SVI origin).
- Gatheral, J. & Jacquier, A. (2014) "Arbitrage-Free SVI Volatility Surfaces", Quantitative Finance 14(1), 59-71; arXiv:1204.0646 (full text consulted for Lemmas 2.1-2.2, raw SVI, Theorems 4.1-4.2, Corollary 4.1, Remarks 4.3-4.5, eq. 4.5).
- Gatheral, J. (2006) The Volatility Surface: A Practitioner's Guide, Wiley.
- Dupire, B. (1994) "Pricing with a Smile", Risk 7(1); Derman, E. & Kani, I. (1994) "Riding on a Smile", Risk 7(2); Derman, E., Kani, I. & Zou, J. (1996) "The Local Volatility Surface: Unlocking the Information in Index Option Prices", Financial Analysts Journal 52(4).
- Derman, E. (1999) "Regimes of Volatility", Risk (April 1999); Derman, E. (2008) E4718 "The Smile" lecture 9 (sticky-strike/sticky-delta/implied-tree regimes, implied vol = average of local vols between S and K; PDF read 2026-10-14): https://emanuelderman.com/wp-content/uploads/2013/09/smile-lecture9.pdf
- Bergomi, L. (2009) "Smile Dynamics IV", Risk (Dec 2009); Bergomi, L. (2016) Stochastic Volatility Modeling, CRC (ch. 9, skew-stickiness ratio).
- Heston, S. (1993) "A Closed-Form Solution for Options with Stochastic Volatility with Applications to Bond and Currency Options", Review of Financial Studies 6(2).
- Hull, J. & White, A. (1987) "The Pricing of Options on Assets with Stochastic Volatilities", Journal of Finance 42(2).
- Albrecher, H., Mayer, P., Schoutens, W. & Tistaert, J. (2007) "The Little Heston Trap", Wilmott Magazine.
- Andersen, L. (2008) "Simple and Efficient Simulation of the Heston Stochastic Volatility Model", Journal of Computational Finance 11(3).
- Bakshi, G., Cao, C. & Chen, Z. (1997) "Empirical Performance of Alternative Option Pricing Models", Journal of Finance 52(5).
- Hagan, P., Kumar, D., Lesniewski, A. & Woodward, D. (2002) "Managing Smile Risk", Wilmott Magazine (Sept 2002); same authors (2014) "Arbitrage-Free SABR", Wilmott Magazine.
- Obłój, J. (2008) "Fine-Tune Your Smile: Correction to Hagan et al.", Wilmott Magazine.
- Antonov, A., Konikov, M. & Spector, M. (2015) "The Free Boundary SABR: Natural Extension to Negative Rates", Risk.
- Kou, S. G. (2002) "A Jump-Diffusion Model for Option Pricing", Management Science 48(8).
- Bates, D. (1996) "Jumps and Stochastic Volatility: Exchange Rate Processes Implicit in Deutsche Mark Options", Review of Financial Studies 9(1).
- Carr, P. & Wu, L. (2003) "What Type of Process Underlies Options? A Simple Robust Test", Journal of Finance 58(6); Carr, P. & Wu, L. (2009) "Variance Risk Premiums", Review of Financial Studies 22(3).
- Gârleanu, N., Pedersen, L. H. & Poteshman, A. (2009) "Demand-Based Option Pricing", Review of Financial Studies 22(10).
- Bakshi, G., Kapadia, N. & Madan, D. (2003) "Stock Return Characteristics, Skew Laws, and the Differential Pricing of Individual Equity Options", Review of Financial Studies 16(1).
- Patell, J. & Wolfson, M. (1979) "Anticipated Information Releases Reflected in Call Option Prices", Journal of Accounting and Economics 1(2); Dubinsky, A., Johannes, M., Kaeck, A. & Seeger, N. (2019) "Option Pricing of Earnings Announcement Risks", Review of Financial Studies 32(2).
- Gatheral, J., Jaisson, T. & Rosenbaum, M. (2018) "Volatility Is Rough", Quantitative Finance 18(6), 933-949; arXiv:1410.3394.
- Livieri, G., Mouti, S., Pallavicini, A. & Rosenbaum, M. (2017) "Rough Volatility: Evidence from Option Prices", arXiv:1702.02777 (abstract read 2026-10-14; journal version IISE Transactions 50(9), 2018 [from memory]).
- Mouti, S. (2026) "Rough Volatility Across Assets", arXiv:2608.16749 (submitted 2026-08-17; abstract read 2026-10-14).
- Bayer, C., Friz, P. & Gatheral, J. (2016) "Pricing under Rough Volatility", Quantitative Finance 16(6).
- El Euch, O. & Rosenbaum, M. (2019) "The Characteristic Function of Rough Heston Models", Mathematical Finance 29(1).
- Cont, R. & Das, P. (2024) "Rough Volatility: Fact or Artefact?", Sankhya B 86(1), 191-223, DOI 10.1007/s13571-024-00322-2 (online 2024-02-21; arXiv:2203.13820 v3 2023-07-10; Crossref checked 2026-10-14).
- Guyon, J. & Lekeufack, J. (2023) "Volatility Is (Mostly) Path-Dependent", Quantitative Finance 23(9), 1221-1258; SSRN 4174589. Follow-up: "The Implied Volatility Surface (Also) Is Path-Dependent", arXiv:2312.15950 (2023) [not fetched]; Andrès & Jourdain (2024) arXiv:2408.02477 (existence/uniqueness for the GL PDV model; v2 Oct 2025).
- Demeterfi, K., Derman, E., Kamal, M. & Zou, J. (1999) "More Than You Ever Wanted to Know About Volatility Swaps", Goldman Sachs Quantitative Strategies Research Notes (March 1999); journal version "A Guide to Volatility and Variance Swaps", Journal of Derivatives 6(4).
- Neuberger, A. (1994) "The Log Contract", Journal of Portfolio Management 20(2).
- Carr, P. & Madan, D. (1999) "Option Valuation Using the Fast Fourier Transform", Journal of Computational Finance 2(4).
- Fang, F. & Oosterlee, C. W. (2008) "A Novel Pricing Method for European Options Based on Fourier-Cosine Series Expansions", SIAM Journal on Scientific Computing 31(2).
- El Karoui, N., Jeanblanc-Picqué, M. & Shreve, S. (1998) "Robustness of the Black and Scholes Formula", Mathematical Finance 8(2).
- Derman, E. & Kamal, M. (1999) "When You Cannot Hedge Continuously: The Corrections of Black-Scholes", Risk 12(1).
- Leland, H. (1985) "Option Pricing and Replication with Transactions Costs", Journal of Finance 40(5); Hoggard, T., Whalley, A. E. & Wilmott, P. (1994) "Hedging Option Portfolios in the Presence of Transaction Costs", Advances in Futures and Options Research 7.
- Leisen, D. & Reimer, M. (1996) "Binomial Models for Option Valuation - Examining and Improving Convergence", Applied Mathematical Finance 3(4).
- Hull, J. C. Options, Futures, and Other Derivatives (11th ed., 2021), chs. on parity, trees (dividend-yield binomial), BSM, dividends, futures options (futures-style margining), early exercise; Haug, E. G. (2007) The Complete Guide to Option Pricing Formulas, 2nd ed.; Derman, E. & Miller, M. (2016) The Volatility Smile, Wiley; Bergomi, L. (2016) Stochastic Volatility Modeling, CRC.

Primary web sources (accessed 2026-10-14):
- Cboe, "Cboe Volatility Index (VIX) Methodology" (last revised 2019-07-26): https://cdn.cboe.com/resources/vix/VIX_Methodology.pdf
- Cboe, "Cboe Volatility Index Mathematics Methodology" (Version 5.0, Last Revised February 26, 2026; PDF fetched and text-extracted 2026-10-14; §2(ii)-(iv) forward/K0/strike selection/ΔK, §4-5 filtering, §6 series-level filtering, Appendix 1 changes, Appendix 2 document information): https://cdn.cboe.com/resources/indices/Cboe_Volatility_Index_Mathematics_Methodology.pdf
- Cboe, VIX Options product page: https://www.cboe.com/tradable-products/vix/vix-options/ ; specifications (rendered with empty exercise-style/settlement fields on 2026-10-14): https://www.cboe.com/tradable-products/vix/vix-options/specifications/
- Cboe Regulatory Circular RG18-015 (VIX settlement SOQ auction): https://cdn.cboe.com/resources/regulation/circulars/regulatory/RG18-015.pdf
- Cboe Insights (guest post, 2025-03-26, rates as of 2025-02-24), "Long-Dated Box Spreads: A Better Way to Buy a Home": https://www.cboe.com/insights/posts/long-dated-box-spreads-a-better-way-to-buy-a-home-updated/
- OIC/OCC, "Listed Options Box Spread Strategies for Borrowing or Lending Cash": https://www.optionseducation.org/getmedia/2ae6c8bd-9a8e-4d2f-8168-19b6ff9e3589/listed-options-box-spread-strategies-for-borrowing-or-lending-cash.pdf
- Federal Register, FR Doc. 2026-17908, SEC Release No. 34-106216, File No. SR-CBOE-2026-004, published 2026-09-02, 91 FR 56493-56504 (API record read 2026-10-14): https://www.federalregister.gov/api/v1/documents/2026-17908.json
- MathWorks documentation citing Jäckel (2015) and offering the 'jackel2016' IV method: https://www.mathworks.com/help/fininst/impvbybls.html
- QuantLib, ql/pricingengines/blackformula.hpp (master, read 2026-10-14; no Let's-Be-Rational routine): https://github.com/lballabio/QuantLib/blob/master/ql/pricingengines/blackformula.hpp
- arXiv abstract pages read 2026-10-14: https://arxiv.org/abs/2608.16749 (Mouti 2026), https://arxiv.org/abs/1702.02777 (Livieri et al.); Crossref records: https://api.crossref.org/works/10.1007/s13571-024-00322-2 (Cont-Das), Jensen-Pedersen 2016 (DOI above).
- CME Group E-mini S&P 500 options contract specifications and Rulebook ch. 358A, and CME Clearing advisory on the Bachelier switch: all returned HTTP 503 on 2026-10-14; related claims tagged [uncertain].
