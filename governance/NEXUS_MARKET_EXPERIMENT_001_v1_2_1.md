# NEXUS MARKET EXPERIMENT 001

Document ID: `NME-001`  
Version: `1.2.1`  
Date: `2026-08-29`  
Status: `FROZEN_FOR_BUILD`  
Risk lane: `RESEARCH_LITE`  
Executive owner: Executive / Research Architect  
Implementation owner: Developer Lead  
Claim state: `RESEARCH_HYPOTHESIS`  
Delivery state: `EXPLORATORY`  

Permanent marking:

> `EXPLORATORY ONLY — NO TRADING AUTHORITY`

Version `1.2.1` is a bounded corrective patch to v1.2.0. It preserves the
research question, event, feature, outcome, estimator, comparator,
pseudo-control, partition design, fixed trailing 1,260-session memory,
historical-final identities, and realized evidence thresholds. Under
`NME-001-DWO-04`, it enforces fit-before-OOD attrition, labels the capacity
estimand and uncertainty sensitivity honestly, completes output-reconciled
verification and runtime-type enforcement, and appends one acceptance-review
custody event. Exact v1.0.1, v1.1.0, and v1.2.0 bytes remain preserved
separately. No provider contact, data ingestion, real v1.2.1 development, or
final access is authorized by this protocol freeze.

## 1. Research question

When SPY first enters a preregistered pre-contact approach band around the immediately prior full RTH session's high or low, do data available at that completed 5-minute bar improve the 30-minute joint probability estimate of:

1. `NO_CONTACT`;
2. `DEFEND_OR_REJECT`;
3. `BREAK_THROUGH_OR_ACCEPT`; or
4. `UNRESOLVED_OR_AMBIGUOUS`

relative to trailing-memory climatology, simple distance/volatility geometry, generic recent price path, and matched nonprivileged pseudo-levels?

The central falsification question is:

> Does the prior-session high/low identity add calibrated probability information beyond ordinary distance, volatility, clock, and recent price path?

## 2. Decision this experiment may change

The result may justify one of three decisions:

- continue the prior-session-extreme hypothesis into an independently opened historical confirmation and later prospective shadow epoch;
- narrow the hypothesis because only generic approach/path behavior is detectable; or
- stop investing in this level family because it does not beat simple controls.

A falsified or inconclusive result is a valid success for this experiment.

## 3. Scope

| Field | Frozen value |
|---|---|
| Instrument | SPDR S&P 500 ETF Trust |
| TradingView standard ID | `AMEX:SPY` |
| Bar interval | Exactly 5 minutes |
| Candle type | Ordinary time-based candles |
| Session | US equity RTH only, 09:30–16:00 `America/New_York` |
| Ordinary-session slots | 78, bar-open stamps 09:30 through 15:55 |
| Level family | `PRIOR_RTH_EXTREME` |
| Levels | Immediately prior complete RTH session high and low |
| Forecast origin | Close of the first eligible pre-contact approach bar |
| Outcome window | The next six completed 5-minute RTH bars; clock never restarts at contact |
| Proposed historical-design cutoff | No later than 2024-12-31 16:00 ET |
| Primary training memory | Latest 1,260 training-authorized sessions before each fit |
| Expanding all-history learner | `EXPANDING_MEMORY_DIAGNOSTIC`; report-only; zero evidence vote |
| Prospective relevance | Requires a separately sealed epoch strictly after 2026-08-28 |
| Primary data lane | One unspliced authorized provider/feed profile; none acquired or authorized by v1.2 |
| Primary score | Four-class Brier score and skill versus frozen comparators |
| Model | L2-regularized multinomial logistic regression |

## 4. Explicit non-goals

This experiment does not:

- produce BUY/SELL labels, entries, exits, option structures, P&L, or execution claims;
- test QQQ, sectors, individual stocks, overnight/extended hours, futures, or options;
- test moving averages, VWAP, round numbers, adaptive terrain, confluence, repeated attacks, or other level families as forecast objects;
- use Level 2, NBBO, trades, order flow, news, macro, sectors, breadth, or Sonar;
- use `attack`, `reinforced`, `fatigue`, inherited votes, qualitative scores, or legacy weights;
- modify Pine, TradingView alerts, broker connections, or frozen governance artifacts;
- select definitions or features after inspecting the final holdout; or
- grant formal-evidence, predictive, trading, alerting, production, or automated-action authority.

## 5. Data identity and custody

### 5.1 Historical prototype and future acquisition boundary

The retained v1.0.1 engineering run used one untouched TradingView chart-data
CSV exported from a disposable `AMEX:SPY` 5-minute RTH chart. Those 2025–2026
sessions remain scientifically opened and may not enter a historical final.
They are historical development material only and DWO-03 grants no authority
to reprocess them.

Only after separate real-development and data-use authorization may those
opened 2025–2026 sessions be used again, and then only as an explicitly
labeled modern development diagnostic with zero historical-confirmation,
prospective-confirmation, promotion, or authority vote.

Any future long-history source must be separately authorized before account
creation, purchase, download, or ingestion. Publicly advertised coverage is a
design hypothesis, not verified source coverage. One provider/feed identity
must cover the experiment without splicing, and written rights must permit the
approved private processing, retention, and review workflow.

Record in a sidecar receipt:

```text
source_receipt_id
provider
feed_profile
tradingview_standard_symbol
instrument_name
venue_or_listing
interval
candle_type
timezone
chart_session_display
metrology_session_basis
dividend_adjustment_state
split_adjustment_basis
currency
exported_at_utc
source_cutoff
raw_filename
raw_size_bytes
raw_sha256
row_count
first_bar_open_utc
last_bar_open_utc
```

The chart-visible source is expected to record `NYSE Arca by Cboe One`; the Developer SHALL observe and record the actual value rather than assume it.

### 5.2 Adjustment basis

- Primary geometry uses split-adjusted-only prices.
- Dividend adjustment is off.
- Raw TradingView volume is retained.
- Sessions spanning a split, distribution, symbol mapping change, or other corporate-action discontinuity are excluded from the primary cohort with a reason code unless exact comparability is established before scoring.
- No adjusted and unadjusted series may be mixed.

The visible TradingView `ADJ off` state establishes only that dividend adjustment is off. The receipt must separately state the split basis actually used.

For this TradingView prototype, `split_adjustment_basis` may be populated as `TRADINGVIEW_SPLIT_ADJUSTED` only when the receipt preserves all of the following:

1. the exact standard symbol and provider/feed shown on the exported chart;
2. the official TradingView source and retrieval date stating that historical chart prices are recalculated for stock splits;
3. the exported date range; and
4. a check of split events inside that range, with every event either consistently reflected in the series or excluded as `CORPORATE_ACTION_BOUNDARY`.

The governing source is <https://www.tradingview.com/support/solutions/43000765406-what-are-stock-splits/>. If those items cannot be established, record `split_adjustment_basis=UNKNOWN`; every affected real-data opportunity is `INVALID_ADJUSTMENT_BASIS`. The Developer may still complete fixture and engineering lanes but may not infer the basis from price continuity alone.

### 5.3 Provider boundary

- No provider, feed, adjustment, or data-vintage splicing.
- Missing OHLCV bars are never forward-filled or interpolated.
- Vendor corrections create a new dataset identity and hash.
- A future API source may be added only as a separate adapter and research cohort after explicit authorization.
- A future overlap audit must precede any claim that TradingView and another provider are interchangeable.

### 5.4 Normalized bar schema

```text
symbol
timestamp_utc
bar_open_et
bar_close_et
session_date
scheduled_slot
open
high
low
close
volume
provider
feed_profile
adjustment_basis
source_receipt_id
```

Timestamps are bar-open timestamps. Every bar represents `[bar_open, bar_close)` and becomes available only at `bar_close`.

## 6. Session and prior-level contract

1. The calendar is pinned to `XNYS` in `America/New_York`; UTC offsets are never hand-coded. The implementation must construct the pinned calendar with explicit requested start/end bounds plus enough preceding-session buffer to resolve the first candidate session's lawful predecessor.
2. Ordinary RTH sessions have exactly 78 scheduled 5-minute slots.
3. Scheduled half-days are excluded from v1 as both current sessions and prior-reference sessions.
4. The reference session is the immediately prior lawful RTH session. There is no reach-back to an older complete session.
5. `PRIOR_HIGH`, `PRIOR_LOW`, and prior close require all 78 prior-session slots. Otherwise both levels are invalid with `PRIOR_SESSION_INCOMPLETE`.
6. Opening, internal, duplicate, out-of-order, and terminal missing slots remain distinct reason codes.
7. Current-session bars must be continuous through the origin and throughout the six-bar outcome window. Missing bars outside the required causal window do not retroactively invalidate it.
8. Forming bars and bars beyond the dataset cutoff are excluded.
9. Halts or malformed bars inside a required window make the affected opportunity invalid; they are not an ambiguous market outcome.
10. Calendar construction fails loudly when the pinned implementation cannot serve the explicit range, predecessor coverage is incomplete, or the emitted schedule identity differs from its frozen receipt. Synthetic `date + timedelta` sequences do not satisfy calendar integration evidence.

## 7. Static level identity

Each level is immutable for the current session and identified by:

```text
instrument = AMEX:SPY
level_family = PRIOR_RTH_EXTREME
level_side = PRIOR_HIGH | PRIOR_LOW
current_session_date
reference_session_date
level_value
price_basis
provider
feed_profile
normalized_dataset_sha256
```

`PRIOR_HIGH` is approached from below. `PRIOR_LOW` is approached from above. They are two orientations of one family, not two independent votes.

Define orientation:

\[
q=+1 \text{ for PRIOR_HIGH}, \qquad q=-1 \text{ for PRIOR_LOW}.
\]

For any price \(p\), level \(L\), and frozen event scale \(A\):

\[
z(p)=q\frac{p-L}{A}.
\]

`z < 0` is the safe/approach side; `z > 0` is beyond the level.

## 8. Causal normalization scale

The ATLAS-derived directionless reference scale is retained without inheriting any legacy score or authority:

\[
A_t=\max(ATR14_{5m,RTH,t-1},\;0.06\times ATR14_{Daily,RTH,prior},\;8\times tick).
\]

For SPY, `tick = 0.01` unless the source receipt proves otherwise.

- True range is `max(high-low, abs(high-prior_close), abs(low-prior_close))`.
- Both ATRs use Wilder's recursive moving average.
- For each ATR, the first value is the arithmetic mean of the first 14 valid true-range observations; later values follow `ATR_t = (13*ATR_t-1 + TR_t)/14`.
- The 5-minute sequence carries across lawful ordinary RTH sessions, excludes extended-hours and shortened-session bars, and uses the previous valid ordinary RTH close as `prior_close` for the first bar of a session. It ends at the bar immediately preceding the candidate origin bar.
- The daily sequence uses one complete ordinary RTH OHLC observation per session, uses the previous valid ordinary RTH close in true range, and ends at the immediately prior session.
- Both components must have completed their 14-observation initialization before an origin. Warmup bars may be processed but cannot produce a scored event.
- At every completed bar, the event detector uses the causally available `A_t`.
- When an event is sealed, `A = A_t0` is frozen for the entire six-bar outcome.
- Undefined ATR, invalid warmup, or zero/nonfinite scale produces `INVALID_SCALE`.

The scale is a normalization device, not a direction forecast and not an evidence vote.

## 9. Approach-origin event contract

### 9.1 Frozen bands

Using oriented distance `z`:

- far/safe region: `z < -0.50`;
- approach band: `-0.50 <= z < -0.10`;
- contact zone: `-0.10 <= z <= +0.10`;
- safe-side resolution threshold: `z <= -0.50`;
- through-side resolution threshold: `z >= +0.50`.

These are preregistered falsification thresholds, not established market truths. They may not be changed in this candidate because another value scores better.

### 9.2 Opening eligibility

Define `A_preopen` from the 5-minute ATR ending at the prior ordinary session's final bar and the daily ATR ending at that prior session. At the 09:30 open, the level must be on the far safe side under `A_preopen`. If the session opens in the approach band, in the contact zone, or beyond the level, that level/session is `ABSTAIN_OPENING_POSITION` and no later recross may substitute.

### 9.3 State machine

For each eligible level, scan bars forward chronologically. For a completed bar define:

\[
z_{near}=\max(z(low),z(high)), \qquad z_{far}=\min(z(low),z(high)).
\]

This definition works for both orientations: `z_near` is the traded extreme closest to or furthest through the level. The first bar with `z_near >= -0.50` is the decisive first-departure bar. A later, more attractive bar may never replace it.

Apply this precedence at the close of each bar:

| Priority | Exact condition | Terminal result |
|---:|---|---|
| 0 | The decisive bar closes later than 15:30 ET | `ABSTAIN_INSUFFICIENT_HORIZON` |
| 1 | The other real level already has an open six-bar window and this level reaches its decisive first-departure bar | `ABSTAIN_OVERLAPPING_EVENT` for this level |
| 2 | Both still-eligible real levels have their decisive first-departure bar on this same bar | `ABSTAIN_SIMULTANEOUS_LEVELS` for both |
| 3 | For one level, `z_far > +0.10`, so the entire traded range is beyond the contact zone | `ABSTAIN_GAP_BYPASS` |
| 4 | `z_near >= -0.10` and `z_far <= +0.10`, so the bar range intersects the contact zone | `ABSTAIN_DIRECT_CONTACT` |
| 5 | `-0.50 <= z_near < -0.10` and `-0.50 <= z(close) < -0.10` | `EVENT_SEALED` |
| 6 | The decisive bar satisfies none of priorities 2–5 | `ABSTAIN_UNSEALED_FIRST_APPROACH` |

The horizon gate is applied first. Priority 1 applies only when a previously sealed event window is already open. Otherwise Priority 2 is arbitrated before either level is sealed, even if the two level-specific conditions would otherwise differ. `ABSTAIN_GAP_BYPASS` is a pre-origin disposition only.

Once an opportunity leaves `ELIGIBLE`, no later bar may replace it. Maximum one event is admitted per `(session_date, level_side)`.

Only one Experiment 001 event may have an open six-bar window at a time. At each bar close, finalize any event whose `W6` is that bar before evaluating a new first departure; a new origin at the `W6` close does not overlap. If the other level reaches its decisive first-departure bar at a `W1..W5` close of an active event, it is `ABSTAIN_OVERLAPPING_EVENT`.

Continue scanning after the latest eligible origin only to distinguish a late first departure from no departure. A first departure after the 15:30-close limit is `ABSTAIN_INSUFFICIENT_HORIZON`; a level that remains in the far region for the entire session is `NO_EVENT_NO_APPROACH`. A later recross is not a separate state; the opportunity was already terminal at its first departure or at session close.

### 9.4 Origin time and horizon

- The forecast origin is the close of the qualifying approach bar.
- Features may use data available at or before that close.
- The outcome window is exactly the next six completed 5-minute RTH bars.
- The clock never restarts when contact occurs.
- The latest eligible origin is a bar closing at 15:30 ET.
- An otherwise valid later origin is `ABSTAIN_INSUFFICIENT_HORIZON`.

This is an approach forecast. A contact-triggered nowcast is a different experiment and may not be pooled with it.

## 10. Outcome contract

Let the six outcome bars be `W = 1..6` and use the event's frozen `L`, `q`, and `A`.

### 10.1 Contact

A bar contacts the level when its traded high-low interval intersects:

\[
[L-0.10A,\;L+0.10A].
\]

The first intersecting bar is the contact bar. A complete gap across the interval is not contact. After an event has been sealed, a gap is outcome telemetry—not an abstention—and cannot remove the issued forecast from scoring.

### 10.2 Four mutually exclusive labels

After a valid contact, use completed-bar closes from the contact bar through `W6`, inclusive, for directional resolution. Closes before the first contact cannot confirm either direction:

- safe-side confirmation: any outcome close with `z(close) <= -0.50`;
- through-side confirmation: any outcome close with `z(close) >= +0.50`.

| Outcome | Exact rule |
|---|---|
| `NO_CONTACT` | No outcome bar contacts the zone, including a path that gaps across the zone without later intersecting it. |
| `DEFEND_OR_REJECT` | Contact occurs; safe-side confirmation occurs; through-side confirmation never occurs. |
| `BREAK_THROUGH_OR_ACCEPT` | Contact occurs; through-side confirmation occurs; safe-side confirmation never occurs. |
| `UNRESOLVED_OR_AMBIGUOUS` | Contact occurs and neither confirmation occurs, or both confirmations occur in any order. |

Apply this outcome precedence:

1. If no bar in `W1..W6` intersects the contact zone, label `NO_CONTACT`. If any such bar is wholly beyond the zone (`z_far > +0.10`), also record subtype `OUTCOME_GAP_BYPASS`.
2. Otherwise locate the first contact bar and inspect only that bar through `W6`.
3. If any inspected bar's range spans both resolution thresholds (`z_far <= -0.50` and `z_near >= +0.50`), label `UNRESOLVED_OR_AMBIGUOUS` with subtype `AMBIGUOUS_INTRABAR_BOTH`, regardless of its close.
4. Otherwise apply the completed-close rules in the table. Safe and through confirmations both occurring in the inspected bars, in either order, produce `UNRESOLVED_OR_AMBIGUOUS`.

Thus every valid six-bar path after an issued forecast receives exactly one of the four labels. No OHLC candle is used to invent intrabar ordering.

The word `ACCEPT` is an operational close-through proxy in v1, not proof of durable market acceptance.

### 10.3 Joint and conditional probabilities

The primary forecast is the joint four-class vector:

\[
\mathbf{p}=(p_{NC},p_{DR},p_{BT},p_{UR}), \qquad \sum p_k=1.
\]

Conditional reaction probabilities may be derived only beside the contact probability:

\[
P(DR\mid contact)=\frac{p_{DR}}{1-p_{NC}},\quad
P(BT\mid contact)=\frac{p_{BT}}{1-p_{NC}},\quad
P(UR\mid contact)=\frac{p_{UR}}{1-p_{NC}}.
\]

If `1 - p_NC <= 1e-12`, all three conditional reaction probabilities are emitted as unavailable; they are never coerced to zero or infinity.

`NO_CONTACT` is an outcome, not an abstention. The joint vector receives the primary score.

## 11. Invalid and abstention states

Every opportunity is emitted to an eligibility ledger even when it is not scored.

The ledger separates `origin_disposition`, `forecast_status`, and `outcome_evaluation_status`. Before prediction, a row terminates as one invalid/abstention/no-event disposition or as `EVENT_SEALED`. After `EVENT_SEALED`, that origin disposition is immutable; prediction processing then sets `forecast_status=ISSUED`, `OOD_ABSTAIN`, or `TECHNICAL_NOT_ISSUED`. A later missing bar, halt, malformed outcome, dataset end, or other technical failure is recorded in `outcome_evaluation_status` and coverage accounting; it may not erase the sealed origin or retroactively abstain an issued forecast.

### Invalid data

- `INVALID_SYMBOL_OR_FEED`
- `INVALID_TIMEZONE_OR_SESSION`
- `INVALID_ADJUSTMENT_BASIS`
- `PRIOR_SESSION_INCOMPLETE`
- `CURRENT_REQUIRED_BAR_MISSING`
- `DUPLICATE_OR_NONMONOTONIC_BAR`
- `MALFORMED_OHLCV`
- `INVALID_SCALE`
- `INVALID_FEATURE_HISTORY`
- `CORPORATE_ACTION_BOUNDARY`
- `HALT_OR_UNSCORABLE_WINDOW`
- `DATASET_END`

### Valid-data abstentions outside the primary cohort

- `ABSTAIN_OPENING_POSITION`
- `ABSTAIN_UNSEALED_FIRST_APPROACH`
- `ABSTAIN_DIRECT_CONTACT`
- `ABSTAIN_GAP_BYPASS`
- `ABSTAIN_SIMULTANEOUS_LEVELS`
- `ABSTAIN_OVERLAPPING_EVENT`
- `ABSTAIN_INSUFFICIENT_HORIZON`
- `NO_EVENT_NO_APPROACH`

These rows remain in counts. They are never silently deleted or relabeled.

## 12. Origin-known feature set

All features carry `available_at <= origin_available_at`. Missing required features produce invalid data; the primary model does not impute them.

Let `t` be the completed origin bar. All normalized features use the event's frozen `A`.

Unless a feature explicitly says otherwise, `t-n` means the sequence of preceding completed bars from lawful ordinary RTH sessions only. The sequence may cross a lawful overnight/session boundary, excludes extended hours and shortened-session bars, and is an observation lag rather than elapsed clock time. This is why the former `return_30m_A` is named `return_6_rth_steps_A`. All required lags must exist before a forecast is issued; otherwise the opportunity is `INVALID_FEATURE_HISTORY`.

| Feature | Definition |
|---|---|
| `level_side` | `PRIOR_HIGH` or `PRIOR_LOW` |
| `origin_time_fraction` | RTH minutes from 09:30 to origin close divided by 390 |
| `level_close_distance_A` | `q * (close_t - L) / A` |
| `return_5m_A` | `q * (close_t - close_t-1) / A` |
| `return_15m_A` | `q * (close_t - close_t-3) / A` |
| `return_6_rth_steps_A` | `q * (close_t - close_t-6) / A`; six ordinary-RTH bar observations, not necessarily 30 elapsed minutes across a session boundary |
| `approach_persistence_6` | Fraction of changes ending `t-5..t` for which `q*(close_j-close_j-1) > 0`; zero changes do not count as toward |
| `range_expansion_3_20` | Median true range of `t-2..t` divided by median true range of `t-22..t-3` |
| `volatility_scale_pct` | `A / L` |
| `relative_volume_tod_20` | Cumulative current RTH volume through origin divided by median cumulative volume through the same slot over the prior 20 complete RTH sessions |
| `gap_A` | `q * (current_session_open - prior_session_close) / A` |
| `session_path_A` | `q * (close_t - current_session_open) / A` |
| `session_vwap_distance_A` | `q * (close_t - causal_session_VWAP_t) / A` |
| `prior_close_to_level_A` | `q * (L - prior_session_close) / A` |
| `prior_range_A` | `(prior_high - prior_low) / A` |

Session VWAP uses cumulative RTH `typical_price=(high+low+close)/3` multiplied by volume through the origin only. Relative volume uses the immediately preceding 20 ordinary 78-slot sessions only, at the same scheduled slot; all 20 must have valid volume through that slot. Final current-session volume is forbidden.

EMA9, EMA20, EMA50, SMA200, ATR descendants, and other plotted indicators are not candidate features in v1. The ATR scale is normalization, not a forecast vote.

Every feature belongs to the single non-additive `PRICE_BEHAVIOR_TELEMETRY` family.

## 13. Models and comparators

### 13.1 Primary candidate

- L2-regularized multinomial logistic regression with an intercept.
- Solver `lbfgs`, `max_iter=10000`, convergence tolerance `1e-10`, and no class weights.
- Numeric standardization and fixed-category one-hot encoding are fitted inside each training fold only.
- Frozen penalty grid: `C = [0.01, 0.1, 1.0, 10.0]`.
- Fixed seed `20260828` wherever a library operation requires one.
- No post-hoc isotonic or Platt calibration in v1.
- No trees, boosting, neural networks, discretionary interactions, or feature search.

The same estimator, preprocessing, tuning grid, session weights, and convergence rules apply to every learned baseline. They differ only by their frozen feature subsets.

For each outer fit:

1. Freeze the ordered partition-eligible calendar identities before event generation. Select the latest 1,260 training-authorized identities strictly before the fold's permanent embargo, excluding every earlier permanent outer embargo and reaching farther back only to replace those excluded identities. Membership may not depend on an event, label, class, validity, fit, OOD, or scoring result. Fewer than 1,260 identities fails closed.
2. Construct `inner-eligible` from that frozen trailing-memory window. Raw bars from excluded sessions may still supply causal prior levels and rolling features, but excluded outcomes never enter preprocessing, tuning, fitting, OOD support, or climatology.
3. Take the latest 759 sessions from `inner-eligible` and divide them, in order, into exactly three cycles of one temporary inner embargo followed by 252 validation sessions.
4. For each inner fold, train only on earlier identities inside the same trailing-memory window, excluding that fold's immediately preceding temporary embargo, and validate on the following 252-session block. With 1,260 primary-memory sessions, the first fold has exactly 501 earlier training sessions.
5. All four outcome classes must be present in each training fit. A missing class or nonconvergence makes that inner fold unscorable for that estimator.
6. A `C` is eligible only if it produces valid scores on the same three inner folds. Select among eligible values by the lowest pooled session-weighted four-class Brier loss across all three blocks. Exact ties choose the smallest `C`. If no `C` remains, emit `INSUFFICIENT_TRAINING_CLASS_OR_FIT`.
7. Refit the estimator with the selected `C` on the same 1,260-session memory, including temporary inner-embargo sessions but excluding permanent outer embargos, and freeze it for the entire 21-session outer-test block. Every train-derived preprocessing transform, climatology, OOD envelope, penalty choice, and comparator is fitted only on this memory. If all four classes are not present or the refit fails, emit `INSUFFICIENT_TRAINING_CLASS_OR_FIT` for that estimator and outer fold.

Prediction attrition is evaluated independently for each exact
cohort/fold/model after the shared training-only OOD mask is constructed. A
missing or failed fit terminates first as `TECHNICAL_NOT_ISSUED` with the
registered fit failure. Only a model with one successful same-cohort/fold/model
`FIT` record may proceed to the shared OOD decision and emit `OOD_ABSTAIN` or
`ISSUED`. Every `OOD_ABSTAIN` and `ISSUED` row must reconcile to exactly one
such successful `FIT` record. The shared `MODEL_FULL` support mask still
applies identically to the candidate and baselines; no model gains coverage by
ignoring that support decision.

Inner-fold boundaries are a pure function of the frozen chronological session
identities, the permanent-embargo identities, and the constants above.  They
are constructed before any validation or final label is read.  Every penalty
value, learned baseline, `MODEL_FULL`, REAL fit, and PSEUDO fit receives the
same three validation-session identities for a given permitted training
region.  Labels may only make a predeclared fold unscorable; they may never
move, enlarge, shrink, or replace it.

For final mode, select the latest 1,260 training-authorized identities once,
strictly before the final-boundary embargo and excluding all permanent
development embargos. Run the same inner selection and refit on only that
memory, then freeze every model and comparator across all 630 final sessions.
No sequential final-block refit is permitted in v1.2.

The all-permitted-history learner is retained only as
`EXPANDING_MEMORY_DIAGNOSTIC`. It must use the same chronological folds but is
report-only and excluded from hyperparameter or memory selection,
strongest-baseline selection, specificity, interpretation gates, capacity
clearance, final direction checks, promotion, and every authority decision. It
may not replace or ensemble with the primary learner.

### 13.2 Mandatory common-origin baselines

| ID | Inputs and purpose |
|---|---|
| `B_CLIM` | Session-weighted four-class frequencies from the frozen 1,260-session primary memory with Dirichlet `alpha=1`; tests improvement over local base rates. Its vector is frozen for the entire outer-test block and updates only at the next outer fold. |
| `B_DISTANCE_VOL` | `level_close_distance_A`, `volatility_scale_pct`, and `origin_time_fraction`; tests simple first-passage geometry. |
| `B_PRICE_PATH` | Oriented returns, persistence, gap, session path, range expansion, relative volume, VWAP distance, volatility, and clock, but no explicit `level_side`, `L`, level-distance, `prior_close_to_level_A`, or `prior_range_A`; tests generic momentum/reversal. Orientation is required only to express every outcome in common safe/through coordinates. |
| `B_GENERIC_COMBINED` | `level_side`, level distance, volatility, clock, and every `B_PRICE_PATH` input, but not `prior_close_to_level_A` or `prior_range_A`; tests combined generic geometry and path. |
| `MODEL_FULL` | All frozen features; tests whether the two registered prior-session-geometry fields improve the generic combined forecast. |

Every comparator uses the same eligible real-level origins, folds, sample weights, outcome definitions, and fold-level support mask. Beating `B_GENERIC_COMBINED` is required before interpreting the registered prior-session geometry fields as incremental. Coordinate specificity itself is tested separately by the pseudo-level control.

### 13.3 Pseudo-level specificity control

For each prior full session, construct two deterministic nonprivileged coordinates:

```text
PSEUDO_UPPER = prior_low + 0.75 * (prior_high - prior_low)
PSEUDO_LOWER = prior_low + 0.25 * (prior_high - prior_low)
```

Apply the identical orientation, event, horizon, feature, label, model, and split machinery. Real and pseudo models are fitted separately but use identical preprocessing, weighting, folds, penalty selection, and outcome rules.

A pseudo opportunity is excluded before event scanning when, using the session's causally available pre-open scale, its contact zone overlaps either registered real-level contact zone or the other pseudo contact zone:

\[
|P-L_{prohibited}| \le 0.20A_{preopen}.
\]

No contact, outcome, or later bar may affect this exclusion.

The specificity analysis uses only out-of-sample rows from the same evaluation stage for which both `MODEL_FULL` and `B_GENERIC_COMBINED` produced valid probabilities. Before accessing outcomes or losses, fit one deterministic real-versus-pseudo propensity model with:

```text
target: REAL=1, PSEUDO=0
balance variables: origin_time_fraction, level_close_distance_A,
                   volatility_scale_pct, return_15m_A,
                   level_orientation, outer_evaluation_block
numeric preprocessing: pooled weighted mean/standard-deviation scaling
categorical preprocessing: fixed one-hot encoding
estimator: L2 logistic regression, C=1.0, solver=lbfgs
max_iter: 10000
tolerance: 1e-12
seed: 20260828
```

Here `level_orientation=q`, encoded as the fixed binary values `-1` and `+1`. The propensity fit uses base weight `u_i = 1/n_(cohort,session)` so each cohort-session initially has total weight one. Let `e_i=P(REAL_i=1|X_i)`. Apply overlap weights:

\[
w_i=u_i(1-e_i) \text{ for real rows}, \qquad
w_i=u_ie_i \text{ for pseudo rows}.
\]

Normalize weights separately within each cohort to sum to one. For every numeric variable and fixed one-hot indicator, define weighted `SMD=(mean_REAL-mean_PSEUDO)/sqrt((var_REAL+var_PSEUDO)/2)` using those normalized weights and population weighted variances `sum(w*(x-mean)^2)`. Binary indicators use the same formula, equivalently variance `mean*(1-mean)`. A zero pooled variance passes only when the two weighted means are identical; otherwise its absolute SMD is infinite and balance fails. Before a specificity claim, every absolute SMD must be `<=0.10`; effective sample size `(sum w)^2/sum(w^2)` must be at least 100 events and 30 distinct sessions in each cohort; and both cohorts must retain at least 95% common-origin model/baseline coverage. Otherwise emit `SPECIFICITY_INDETERMINATE`.

For each cohort `c`, calculate `BSS_c = 1 - BS_FULL,c / BS_GENERIC,c`. The registered contrast is `S = BSS_REAL - BSS_PSEUDO`. Estimate its 95% percentile interval with 5,000 moving-block bootstrap resamples over the union of chronological session dates, blocks of exactly five consecutive sessions, and seed `20260828`. Every resampled session carries all real and pseudo rows together; predictions and propensity weights stay fixed, while cohort weights are renormalized inside each resample.

Prior-extreme specificity passes only when `BSS_REAL >= 0.01`, `S >= 0.01`, and the lower 95% bound for `S` is above zero. Otherwise the permitted interpretation is generic path/geometry predictability. Pseudo-level performance is a specificity control, not another evidence vote.

## 14. Chronological evaluation

### 14.1 Partitions, primary memory, and capacity screen

Define a `partition-eligible session` before event generation: an ordinary
78-slot session on the pinned calendar whose date lies inside the frozen source
coverage and cutoff. Eligibility is independent of source validity, event,
label, class, fit, OOD, or score. Every identity is frozen and processed in
chronological order; no future outcome may enter an earlier fit.

For a real-level opportunity to be valid, the chronologically immediately
preceding exchange session must itself be an ordinary 78-slot reference
session with all required bars. A half-day or incomplete predecessor cannot be
skipped. Explicit calendar construction includes a predecessor buffer, and a
missing first predecessor fails loudly rather than shortening the cohort.

1. Build and freeze the chronological partition-eligible sequence `S1..SN`
   before event generation; no random row split.
2. Before any proposed final is frozen, compare every candidate identity with
   the immutable prior-exposure ledger. A final identity intersecting
   `SCIENTIFICALLY_OPENED` or `UNKNOWN` fails closed.
3. For the immediate historical design, the 630 final identities must end no
   later than 2024-12-31. The proposed ordinary-session block is
   2022-06-22..2024-12-31, subject to exact pinned-calendar verification and a
   single provider's verified coverage. It is historical confirmation only.
4. Reserve the immediately preceding ordinary session as the final-boundary
   embargo. Its outcomes never enter fitting, tuning, or evaluation.
5. Use the first 1,260 development identities as the initial primary-memory
   history. Starting at the next identity, consume exact cycles of one
   permanent embargo followed by 21 outer-test sessions. At least 168 complete
   cycles and 5,587 total eligible sessions remain the arithmetic design
   targets. Every complete cycle is consumed; a remainder shorter than 22
   sessions stays visible and unscored.
6. Before each outer fit, select the latest 1,260 training-authorized identities
   strictly before its embargo, omit all earlier permanent embargos, and reach
   back only to replace omitted embargo identities. Freeze that fit for the
   following 21 sessions.
7. For final mode, select the latest 1,260 authorized identities once before
   the final-boundary embargo, omit every permanent development embargo, refit
   once, and freeze through all 630 final sessions. Final mode remains
   unauthorized.
8. All event horizons terminate inside one complete session. Record
   `purge=NOT_APPLICABLE`; keep all dispositions and REAL/PSEUDO
   opportunities from one session in one partition.
9. Embargo bars may supply a later session's causally available prior level and
   rolling inputs, but embargo outcomes never enter preprocessing, fitting,
   tuning, OOD support, climatology, or evaluation.

The partition arithmetic is unchanged:

```text
1,260 + 168 * (1 + 21) + 1 + 630 = 5,587 sessions
3,528 development test sessions = 7,056 maximum REAL level-session opportunities
```

The proposed, unverified 1998-01-02..2024-12-31 provider-range hypothesis has
6,734 pinned ordinary sessions: 6,103 pre-final development sessions, 220 full
outer cycles, three trailing unscored sessions, 4,620 outer-test sessions, and
9,240 maximum REAL level-session opportunities. Its requested canonical
schedule SHA-256 is
`089933a52b6d17e09fd61b422383ca38d61ff34aaec9eeea97886d30428f9245`;
the 6,734 ordered ordinary-identity SHA-256 is
`d2ef712ab8d19228f1b424901def2765c9d341d39a2b8a813a7f0ff6c73fe963`.
The backing calendar begins 1997-12-02 for a 31-day predecessor buffer; the
first requested session's predecessor is 1997-12-31. These are calendar design
facts only, not proof that a provider supplies complete or licensed bytes.

That arithmetic is not an interpretation-capacity claim. The v1.0.1 opened
sample registered 9 technically evaluable REAL origin rows on 9 distinct
technical-event sessions among 84 outer-test sessions, 0 fitted
`MODEL_FULL` rows, 0 `MODEL_FULL` OOD abstentions, 0 issued or scorable
`MODEL_FULL` REAL rows, and technical-label counts `1/1/2/5`. It did not
register nine scorable model rows. The ordered technical-event session
identities are 2026-02-12, 2026-02-17, 2026-03-02, 2026-03-10, 2026-03-31,
2026-04-07, 2026-04-24, 2026-04-27, and 2026-05-11; their ordered-session
SHA-256 is
`c7f252ddbf88eeea8cd83818c30fbac0e0dac20e542d6bf19624098134167784`.

Capacity reporting must preserve this attrition chain separately:

`PARTITION_ELIGIBLE_OPPORTUNITY -> EVENT_SEALED -> TECHNICALLY_EVALUABLE -> FITTED_MODEL -> IN_SUPPORT_AFTER_OOD -> COMMON_ORIGIN -> SCORABLE_MODEL_FULL -> PER_CLASS`.

The binary planning estimand is
`TECHNICAL_EVENT_SESSION_INCIDENCE`: whether an outer-test session contains at
least one technically evaluable REAL origin. Origins are not Bernoulli session
trials; the nine origin rows and nine distinct technical-event sessions are
reported separately. If a two-sided 95% Clopper-Pearson lower limit (lower
tail 0.025) is shown for 9/84, it is labeled only as a conditional
iid-binomial sensitivity for this binary session-incidence estimand. It is not
unconditional exact temporal coverage, may not be projected as evidence over
1998--2024, and has zero acquisition, interpretation, promotion, or authority
vote.

The acquisition-relevant quantities are realized scorable `MODEL_FULL` row
counts and their per-class row counts, with distinct-session counts alongside.
They are `0/84` total, zero distinct scorable sessions, and `0/0/0/0` by
class in the opened sample. Their lower limit is zero. Thus this lane does not
clear 200 scorable development rows, 30 per class, 50 final rows, or five per
final class. Technical-label counts `1/1/2/5` are descriptive non-gating raw
facts. Unobserved fitted, OOD, common-origin, and scoring support may not be
assumed away. Every acquisition-clearance flag remains false.

The lane is therefore a `FAIL_CLOSED_EXPLORATORY_ACQUISITION_PROPOSAL`, not
interpretation-capable. This screen informs whether acquisition risk is
acceptable; it never replaces realized gates. Fewer than the partition target,
any failed uncertainty screen, or insufficient realized support emits
`INSUFFICIENT_HISTORY_FOR_EVALUATION` or `INSUFFICIENT_EVIDENCE`; thresholds
and boundaries may not be weakened after labels are observed.
### 14.2 Procedural holdout custody

The immutable prior-exposure ledger classifies every earlier session range as
`CUSTODY_OR_IDENTITY_ONLY`, `PROCEDURAL_HOLDOUT_UNOPENED`,
`SCIENTIFICALLY_OPENED`, or `UNKNOWN`. Scientific opening includes any event,
feature, label, model, prediction, metric, plot, intentional outcome
inspection, or use in rate/design selection. A proposed final must be disjoint
from both `SCIENTIFICALLY_OPENED` and `UNKNOWN` above the runtime layer.

The active v1.2.1 exposure file is
`NME001_PRIOR_EXPOSURE_LEDGER_v1_0_1.json` (SHA-256
`4e190926e0dec2d4304b5962904439e4642c0dfc9ac19afd12d776b5fa8cba86`).
It is append-only from the byte-preserved historical
`NME001_PRIOR_EXPOSURE_LEDGER_v1_0_0.json` (SHA-256
`9d68286c2db7b1d2ba60e0fab059c9a1e357340223a5255cc80a16d6e24d1719`).
The DWO-03 acceptance review directly displayed only the 2026-08-28 source
row, so v1.0.1 reclassifies that one ordinary session from
`PROCEDURAL_HOLDOUT_UNOPENED` to `SCIENTIFICALLY_OPENED`, effective
2026-08-29, under DWO-04 order SHA-256
`f5feb728d513c9bb827bb436000ac68d56f0fea395fd6593c778a21cafc54cba`.
The previously unopened 2026-06-01..2026-08-27 remainder contains exactly 62
ordinary sessions with ordered-session SHA-256
`ffe0e90d6a357c619cbceab622abe99729961001da4166404caf3df3023bd7ce`;
the reclassified singleton identity SHA-256 is
`f466ad8c5e70977605fd2969937c301e196733d23a6c29b593199de75a7c1c11`.
No other session is relabeled. The ledger still exhaustively classifies all
415 scheduled XNYS sessions: 412 ordinary sessions in registered exposure
ranges plus three scheduled half-days, each conservatively
`SCIENTIFICALLY_OPENED` because its bytes participated in prior
session-validation and no-reachback logic.
The proposed 630-session historical identity file is
`NME001_HISTORICAL_FINAL_IDENTITIES_2022-06-22_TO_2024-12-31.json` (file
SHA-256 `db4737f03b94c1779ccd186b675d0a41fb33af3e165a949c36e476bef224c003`,
ordered-session SHA-256
`423f3ad6a8b398b12700710cdb37584ded4beac091d985118a7ebebf159bf429`).
The unchanged 630-session historical final has zero overlap with every
`SCIENTIFICALLY_OPENED` or `UNKNOWN` identity in v1.0.1. Any byte, parent,
custody-event, range, or identity mismatch fails before scientific opening.

If one provider cannot support the historical design ending by 2024-12-31,
freeze a prospective holdout instead: calendar and ordinary-session rule,
start strictly after 2026-08-28, target 630, exclusions, and mechanical stop
rule must be immutable before observation. Identities append as sessions occur
without substitution. Historical 2025–2026 outcomes cannot be relabeled as
unseen merely because another vendor supplies the bytes.

Engineering SHALL:

- implement both development and final modes;
- run only `stage=development`;
- permit ingestion, normalization, row-count/hash checks, and pre-event calendar/session identity assignment for the full sealed file;
- generate no final-block events, features, labels, predictions, metrics, plots, or intentional outcome inspection;
- return the frozen historical identities or prospective start/stop rule and whole-dataset hash without final scores; and
- state `final_holdout_opened: NO`.

`NO` means procedurally unscored under the prohibitions above; it does not claim that final-period raw bytes were physically inaccessible. `YES` means any prohibited final-block product or inspection occurred, must be disclosed as contamination, and fails final acceptance for this version.

Independent V&V opens `stage=final` only after verifying the frozen definitions, leakage controls, candidate code, baseline parity, and development report.

No model or semantic change is permitted after the final block is opened. Any change creates a new experiment version and a new untouched confirmation requirement. A historical final ending by 2024-12-31 can support historical confirmation only; present-market relevance requires the separate post-2026-08-28 prospective epoch.

### 14.3 Dependence and weighting

- Session date is the statistical cluster.
- In each fitting or scoring cohort, row weight is `w_i = 1 / n_rows_in_session`, so every represented session has total weight one. Use these weights for learned-model fitting, climatology counts, Brier loss, log loss, calibration, and paired differences.
- Confidence intervals use a noncircular moving-block bootstrap over chronological session-level paired losses: form all overlapping blocks of exactly five consecutive sessions, sample blocks with replacement until at least `N` sessions are drawn, concatenate and truncate to `N`, and compute percentile 2.5%/97.5% limits over exactly 2,000 resamples with seed `20260828`.
- Model-minus-baseline losses are bootstrapped as paired differences on common origins.

### 14.4 Predeclared era-stability diagnostics

Using only already-generated out-of-sample development predictions, report
non-overlapping five-calendar-year blocks aligned from the provider's first
full calendar year, followed by one separately labeled partial block. Never
fit a block-local model, climatology, or baseline. For each block report paired
`MODEL_FULL` loss differences against every frozen common-origin baseline,
class counts, OOD and abstention rates, common-origin retention, and registered
uncertainty.

A block is numerically estimable only with at least 50 common origins, 30
distinct sessions, five observations in every class, and 95% common-origin
retention for each reported baseline. Every unsupported block remains visible
with counts and `NOT_ESTIMABLE`; it may not be pooled, deleted, or replaced.

One exogenous market-structure breakpoint diagnostic uses 2001-04-09 only as
the all-U.S.-market decimalization completion date unless a documented
SPY-specific conversion session is frozen before data opening. Each side must
meet the same numerical support thresholds after the 1,260-session burn-in and
have comparable provider metadata; otherwise report `NOT_ESTIMABLE`. Era and
breakpoint outputs are stability diagnostics only. They do not select an era,
memory length, regime classifier, model, or authority outcome.

## 15. Scores and reports

Primary multiclass Brier loss:

\[
BS=\frac{1}{2\sum_i w_i}\sum_i w_i\sum_{k=1}^{4}(p_{ik}-y_{ik})^2.
\]

For comparator `b`:

\[
BSS_b=1-\frac{BS_{MODEL\_FULL}}{BS_b}.
\]

Required secondary diagnostics:

- weighted multiclass log loss with the numerical floor defined below;
- classwise one-vs-rest Brier loss;
- reliability plots;
- classwise calibration intercept and slope;
- probability entropy/sharpness;
- class counts and base rates by level side, clock bucket, and volatility bucket;
- top-class accuracy and macro-F1 as descriptive diagnostics only;
- eligible, issued, invalid, abstained, OOD, and scored counts by reason;
- technical coverage and scored coverage; and
- paired session-block confidence intervals.

At least 95% common-origin retention is required between the primary candidate and every common-origin baseline. Otherwise comparison integrity fails.

Every probability vector must be finite, contain no value outside `[0,1]`, and sum to one within `1e-12`; otherwise the row is invalid and is not silently repaired. For log loss and calibration only, freeze `epsilon=1e-15`, calculate `p_tilde=clip(p,epsilon,1-epsilon)`, and renormalize `p_star=p_tilde/sum(p_tilde)`. Weighted log loss is `-sum_i(w_i*log(p_star_i,y_i))/sum_i(w_i)`.

For each class, fit the unpenalized weighted logistic recalibration model

\[
logit(P(y_i=k))=a_k+b_k logit(p^*_{ik})
\]

by direct weighted maximum likelihood, initialized at `(a=0,b=1)`, with no class weights or regularization. Report `a_k` as intercept and `b_k` as slope. If either binary outcome is absent, the optimizer lacks a finite unique solution, or separation prevents finite estimation, report `CALIBRATION_NOT_ESTIMABLE`; do not substitute a penalized value.

Calibration intercepts and slopes are evaluation-only diagnostics computed
from already-generated out-of-sample predictions and matured outcomes. They
may never alter an emitted probability, preprocessing transform, climatology,
OOD envelope, penalty choice, comparator, or subsequent fit. No observation,
label, diagnostic, or outcome may influence a prediction made before that
observation's registered outcome has matured.

## 16. OOD and coverage

`NO_CONTACT` is never an abstention.

V1 permits only integrity and support abstentions, not confidence-based selective prediction.

Fit a training-only robust support envelope for each numeric feature:

- center = training median;
- scale = training median absolute deviation;
- OOD when absolute robust z-score exceeds 8;
- unseen categorical value = OOD;
- zero-MAD features require equality with the training value.

Construct one fold-level OOD mask from the complete frozen `MODEL_FULL` feature set and apply that identical mask to `MODEL_FULL` and every common-origin baseline. Baselines may not gain coverage by ignoring a feature used by the candidate.

OOD is determined at origin from training-only support, but fit status has
strict precedence inside each cohort/fold/model prediction path. When that
exact model has no successful `FIT` record, the row is
`TECHNICAL_NOT_ISSUED` with the registered fit failure even if the shared OOD
mask is true. Only a fitted model may emit `OOD_ABSTAIN` or `ISSUED`, and every
such row must reconcile to exactly one successful same-cohort/fold/model
`FIT` record. For a successfully fitted model, an OOD row may receive
diagnostic probabilities internally for testing, but its `forecast_status` is
`OOD_ABSTAIN` and no forecast is issued or scored. An in-support row with valid
probabilities has `forecast_status=ISSUED`. The separate
`origin_disposition=EVENT_SEALED` remains unchanged in every case.

Report separately:

1. event yield = `EVENT_SEALED / valid level-session opportunities`, where the denominator is every non-invalid real level/session ledger row, including opening positions, direct contacts, unsealed approaches, and no-approach rows;
2. technical coverage = `technically evaluable EVENT_SEALED origins / EVENT_SEALED`;
3. scored support coverage = `in-support issued predictions / technically evaluable EVENT_SEALED origins`;
4. ordinary scores on valid in-support issued rows; and
5. coverage-adjusted incremental loss improvement for each comparator.

For item 5, assign each `EVENT_SEALED` origin its common-origin paired improvement `loss_comparator - loss_model` when it is technically evaluable, in support, and issued; assign exactly zero when a post-origin technical failure or OOD state prevents scoring. Average with session-total-one weights over all `EVENT_SEALED` origins. Opportunities with no forecast origin—opening abstentions, direct contacts, unsealed approaches, and `NO_EVENT_NO_APPROACH`—belong in event-yield reporting but are not assigned fictitious outcome losses. This prevents post-origin selective coverage from hiding difficult cases without conflating non-events with abstentions.

## 17. Interpretation gates

### 17.1 Minimum support before historical interpretation

- at least 200 scorable real-level development episodes;
- at least 30 realized examples of each class for class-specific calibration interpretation;
- at least 95% common-origin retention.

Otherwise: `INSUFFICIENT_EVIDENCE`.

The independently opened final block has a separate direction-only minimum of
at least 50 scorable REAL episodes, at least five realized examples of each of
the four classes, and the same 95% common-origin retention requirement. The
v1.2.1 capacity screen does not project that the proposed lane will clear
either final threshold: its observed scorable-`MODEL_FULL` total and every
scorable per-class row count are zero, with zero distinct scorable sessions.
Technical-label counts `1/1/2/5` and the conditional iid-binomial
technical-event-session-incidence sensitivity are descriptive and have zero
gate or clearance vote.
The five-per-class final minimum supports only the registered
same-direction confirmation check; it does not authorize class-specific
calibration interpretation below the unchanged 30-per-class threshold.  If
the final block misses either minimum, or any ordinary coverage or integrity
gate, the result is `INSUFFICIENT_EVIDENCE`.  The block is not enlarged,
reopened, or repeatedly sampled after its labels are seen.

### 17.2 Smallest worthwhile effect

For eligibility as historical candidate evidence, development and independently opened final results must show:

- `BSS_b >= 0.01` for every applicable common-origin baseline `b`;
- lower 95% paired confidence bound above zero versus the strongest baseline, defined as the applicable common-origin comparator with the lowest weighted Brier loss;
- classwise calibration intercept magnitude no greater than 0.05 and slope between 0.80 and 1.20 where class support is sufficient;
- at least 95% technical coverage and at least 95% scored support coverage;
- the frozen pseudo-level specificity test in Section 13.3 passes; and
- the same improvement direction in the independently opened procedural final block without retuning.

Failure to beat `B_GENERIC_COMBINED` means no incremental registered-level-geometry evidence. Failure of the Section 13.3 contrast means no evidence specific to prior-session extremes.

Passing all historical gates creates only:

> `CANDIDATE HISTORICAL PREDICTIVE EVIDENCE FOR THIS EXACT OBJECT`

It does not grant formal predictive or trading authority. A later sealed prospective shadow epoch, independent V&V pass, external gate review, Executive decision, and Product Owner authorization remain required.

Any independently opened final ending on or before 2024-12-31 is historical
confirmation only. It cannot establish relevance to 2026 conditions. That
requires an immutable, no-retuning shadow epoch strictly after 2026-08-28.

Five-minute OHLCV can address only the registered reaction-probability
question. Fill probability, spread, slippage, queue position, and net profit
require a later execution-specific protocol; no result here supports a
tradability claim.

## 18. Kill, narrow, and stopping rules

- Stop or narrow if `MODEL_FULL` does not beat climatology and `B_GENERIC_COMBINED` on development data.
- Attribute any pseudo-level-equivalent result to generic path/geometry, not prior-extreme identity.
- Do not rescue a failed result by changing thresholds, deleting regimes, adding symbols, trying unregistered indicators, or opening the final block repeatedly.
- If support is insufficient, acquire more history under a new authorized data lane; do not weaken the outcome or evidence threshold.
- Routine internal repairs and regression tests are unlimited within the frozen semantics. Return to the Executive only for a semantic deviation, failed interpretation gate, cost/security decision, or material scope reconsideration.

## 19. Historical foundations and current DWO-04 correction authority

Exact v1.0.1 / `NME-001-DWO-01` and v1.1.0 / `NME-001-DWO-02` artifacts
remain historical engineering foundations. Their vertical-slice objective,
TradingView export instructions, raw-file custody, normalized data, event
tables, development evaluation, and prior required return are audit history
only. They are not active v1.2 instructions and are not relabeled as v1.2
evidence.

The DWO-03 candidate, protocol v1.2.0, active configuration at that freeze,
sidecars, evidence, and ledger v1.0.0 remain byte-preserved historical
engineering foundations. `NME-001-DWO-04`, whose authoritative order SHA-256
is `f5feb728d513c9bb827bb436000ac68d56f0fea395fd6593c778a21cafc54cba`,
governs this bounded correction. The earlier DWO-03 amended order remains
historical authority only; its superseded same-filename SHA beginning
`cc2a4517` has no authority.

### 19.1 Current objective

Return one deterministic, pre-data v1.2.1 / candidate 0.3.1 patch that:

- enforces successful same-cohort/fold/model fit before either OOD abstention
  or issuance in development and final;
- reconciles every OOD abstention and issued row to one successful fit record;
- names the session-incidence estimand, raw origin facts, and conditional
  iid-binomial sensitivity without projecting unconditional temporal coverage;
- reconstructs the licensed attrition outputs rather than reciting frozen
  counts;
- enforces declared runtime types consistently across all public configuration
  construction and validation paths; and
- appends the one 2026-08-28 custody event while preserving the unchanged
  630-session historical final and every accepted DWO-03 control.

No provider contact, provider data, real v1.2.0 or v1.2.1 development region,
or final block is opened by this objective.

### 19.2 Authorized work

1. Patch only the offline fit/OOD precedence, attrition reconciliation,
   capacity meaning and verification, strict configuration typing, append-only
   exposure custody, identity bindings, package machinery, and deterministic
   tests authorized by DWO-04.
2. Exercise only synthetic fixtures, pinned-calendar schedules, frozen date
   identities, prior-exposure metadata, and the already-held licensed regression
   fixtures under their existing v1.0.1 regression authority and zero vote.
3. Preserve v0.1.0, v0.2.0, v0.3.0, v1.0.1, v1.1.0, v1.2.0, old orders,
   configurations, receipts, sidecars, raw-data hashes, evidence, and prior
   reports without relabeling.
4. DWO-04 authorizes no external contact. Preserve the Kibot inquiry exactly
   as `PREPARED_NOT_SENT`; prior separate approval neither revokes nor executes
   it. Do not contact Massive.
5. Do not create any provider account, trial, order, payment, credential,
   contract, NDA, sample, download, API connection, or ingestion.
6. Do not add or alter a feature, outcome, baseline, model, symbol, timeframe,
   regime/router, indicator, alert, automation, execution model, forecast
   action, or trading behavior.

### 19.3 Mandatory DWO-04 verification

At minimum, test:

1. a shared OOD envelope with an OOD row and one failed model fit yields
   `TECHNICAL_NOT_ISSUED`, never `OOD_ABSTAIN`, in development and final;
2. a successful-fit OOD row still yields `OOD_ABSTAIN`, and every
   `OOD_ABSTAIN` or `ISSUED` row reconciles to one successful exact
   cohort/fold/model `FIT` record;
3. the licensed regression outputs reconstruct 168 partition-eligible
   opportunities, 9 sealed and technically evaluable REAL origins on 9
   distinct sessions, class counts `1/1/2/5`, 0 `MODEL_FULL` fits, 9
   `MODEL_FULL` technical non-issuances, 0 OOD abstentions, 0 issuances, 0
   scorable rows, and all clearance flags false;
4. the technical-event session identities/hash, raw origin facts, scorable row
   and per-class counts, distinct sessions, and conditional sensitivity label
   are exact and non-authoritative;
5. loader, `from_mapping`, direct construction, and `validate_config` reject
   boolean-for-integer and every other wrong declared runtime type with
   `ContractError`, without coercion;
6. ledger v1.0.0 remains byte-exact and usable historically; ledger v1.0.1
   proves a one-session append-only reclassification, exact range counts and
   hashes, and zero prohibited overlap with the unchanged 630-session final;
7. configuration, public pipeline, and internal final entry points reject
   v1.0.1, v1.1.0, v1.2.0, and v1.2.1 final activation before source
   construction, and every real-v1.2.1 development path remains held;
8. all accepted calendar, memory, diagnostics, malformed-OHLCV, final-journal,
   exact-scope, reliability, archive-safety, and deterministic regressions
   remain passing;
9. candidate-only test collection passes without external bytes; licensed
   fixture verification fails before collection on any identity mismatch; the
   lanes have separate named JUnit identities; and
10. deterministic package construction, manifest reconciliation, prohibited
    bulk/final members, static verification, and exact hermetic reproduction
    all pass.

All accepted DWO-02 malformed-OHLCV, final-journal, exact-scope, reliability,
determinism, and package-reconstruction tests remain regression requirements.

### 19.4 Current acceptance and return

Engineering acceptance requires all authorized candidate-only and licensed
regression tests to pass, zero protocol/config/hash drift, byte-exact
preservation of frozen foundations, no prohibited provider/final access, and
deterministic compact packaging. A missing licensed fixture is a disclosed
`NOT_RUN`, not a candidate-only failure and never a PASS. A vendor response is
not expected because DWO-04 performs no contact.

Return:

- the patched v0.3.1 source candidate and frozen dependency lock;
- complete named candidate-only test evidence and the separately labeled
  licensed-fixture result;
- the v1.2.0-to-v1.2.1 protocol diff, candidate diff, and active configuration
  identity while preserving versioned v1.2.0 bytes;
- the canonical v1.0.1 prior-exposure ledger, preserved v1.0.0 ledger, and
  unchanged historical-final identities;
- the corrected capacity/configuration note and exact attrition reconciliation;
- pinned-calendar and trailing-memory evidence;
- stability and diagnostic-only evidence;
- the exact Kibot inquiry preserved as `PREPARED_NOT_SENT` and the unchanged
  precontact assessment;
- deterministic package, manifest, verification, and reproduction identities;
  and
- all remaining limitations and unrun lanes, with final, formal, predictive,
  and trading authority unchanged.

Return `COMPLETE_WITH_LIMITS` when the authorized implementation and tests are
complete but real provider data, vendor rights, or statistical evidence remain
unavailable. Return `DECISION_REQUIRED` only for a reserved semantic, contact,
account, cost, credential, data, or final-access decision. Do not return
`REAL_DATA_REQUIRED` as permission to export, acquire, or ingest anything.

### 19.5 Developer autonomy and escalation

The standing rule in `NEXUS_BRIEF.md` applies:

> If the intended scientific meaning remains unchanged, fix it, add a regression test, and continue.

Routine implementation defects and regression repairs are authorized.
Escalate a semantic change affecting cohort membership, predictions, losses,
matching, interpretation, any prohibited external action, or final access.
## 20. Modification restrictions

Engineering may not modify this file after its v1.2.1 hash is frozen. Semantic changes require a later `NME-001` version or a superseding Executive decision before implementation. A correction that preserves semantics receives a patch version and new hash.

## 21. Sources and inherited boundaries

- Nexus mission and role authority: `NEXUS_MULTI_AI_OPERATING_CHARTER_v0.1.0_2026-08-25.md`.
- Calendar/symbol orientation: `NEXUS_METROLOGY_CALENDAR_AND_SYMBOL_CONTRACT_v0.1.md`; its candidate status and qualifications remain intact.
- Neutral geometry orientation: ATLAS records are reused only for static identity, causal availability, orientation, normalization, and event lifecycle. No legacy score, acceptance, or predictive authority is inherited.
- Measurement catalog: `SENSOR_ENCYCLOPEDIA` remains a candidate-formula reference, not proof of incremental value.
- No-double-vote rule: all v1 features remain inside `PRICE_BEHAVIOR_TELEMETRY`.
- Historical TradingView-foundation chart-export reference (not active v1.2 acquisition authority): <https://www.tradingview.com/support/solutions/43000537255-how-to-export-chart-data/>
- Historical TradingView-foundation intraday-limit reference (not active v1.2 acquisition authority): <https://www.tradingview.com/support/solutions/43000480679-historical-intraday-data-bars-and-limits-explained/>
- Scikit-learn Brier score: <https://scikit-learn.org/stable/modules/generated/sklearn.metrics.brier_score_loss.html>
- Scikit-learn probability calibration: <https://scikit-learn.org/stable/modules/calibration.html>
- Scikit-learn time-series evaluation warning: <https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.TimeSeriesSplit.html>
- Exchange calendar implementation reference: <https://github.com/gerrymanoim/exchange_calendars>
- SEC decimalization completion record; 2001-04-09 is the all-U.S.-market completion date, not a SPY-specific conversion date: <https://www.sec.gov/rules-regulations/2001/07/request-comment-effects-decimal-trading-subpennies>

## 22. Authority

```yaml
research_lane: RESEARCH_LITE
claim_state: RESEARCH_HYPOTHESIS
delivery_state: EXPLORATORY
developer_may_open_development_region: SYNTHETIC_ONLY_PENDING_SEPARATE_REAL_DATA_AUTHORITY
developer_may_open_final_holdout: NO
real_v1_2_0_development: NOT_RUN
real_v1_2_1_development: HOLD
new_confirmation_data_authority: HOLD
massive_contact_any_form: NOT_AUTHORIZED
kibot_written_inquiry: PREPARED_NOT_SENT_SEPARATE_PRIOR_APPROVAL_NOT_EXECUTED_BY_DWO04
external_provider_contact_during_dwo04: NONE_AUTHORIZED
account_trial_purchase_credentials_download_ingestion: HOLD
formal_evidence_authority: NONE
predictive_authority: NONE
trading_authority: NONE
alerting_authority: NONE
automated_action_authority: NONE
```
