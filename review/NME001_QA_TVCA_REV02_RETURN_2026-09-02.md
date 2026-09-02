# NME-001 Independent QA Return — TVCA Legacy Closure and Successor Plan REV-02

Date: 2026-09-02
Reviewed: `NME001-TVCA-LEGACY-CLOSURE-AND-SUCCESSOR-PLAN-REV02`, 48,089 bytes,
SHA-256 `a06e02cc132717240b03b41b6bc3b09fc52851e5ab67184322d5c8f5af4e8fce`
(`libfile_4cc997e280288191b723ed71ff360fce`). Documentary review only. This
return establishes eligibility at the REV-02 gate only and creates no
operational, evidence, predictive, trading, alerting, or final-opening authority.

## Identity verification (independently recomputed)

| Claim in REV-02 | Result |
|---|---|
| Document SHA-256 `a06e02cc…` | PASS |
| Bundle member `data/receipts/corporate_action_check_receipt.json` = `499cf40b…` | PASS (against the held `8cb8151a…` bundle) |
| Bundle member `data/receipts/source_receipt.json` = `c8744332…` | PASS |
| Bundle member `src/nexus_nme001/pipeline.py` = `cea08d93…` | PASS |
| Pine carrier UTF-8/LF, 892 bytes, `577eaaee…` | PASS — reconstructs exactly from the quoted block (trailing LF required) |
| Six ex-dates are XNYS sessions; 2026-06-18 explained by 2026-06-19 closure | PASS |
| §4.2 expected 2025 amounts, listing identity, `BATS:SPY` label, legacy fixture identity 2,066,778 B / `11215bd7…` | PASS — all present verbatim in the accepted historical receipt |
| Two-plane DWO-05 identities (`cbc075f4…` 983 JUnit, `6a6b7163…` 922 JUnit, `15138cc5…` inventory, `a3caaf9f…` note, `a6ed0f1e…` layer manifest, `f168863f…` delta) | PASS — all previously verified in this QA record |
| REV-01, QA Submission 01, Reviews A–D, partial custody receipt (`874fc001…`, `ff89bdb1…`, `41de33a5…`, `f737dca0…`, `2cb68b49…`, `45f988d3…`, `85c7dc03…`) | UNVERIFIABLE — not held by this QA lane; treated as cited provenance only |

Fixture-search closure: this lane confirmed no 2,066,778-byte file exists in
its own environment (2026-09-01); the Product Owner's exhaustive-search closure
is accepted as recorded. `LEGACY_CORPORATE_ACTION_FIXTURE_UNRECOVERABLE` is a
proper tombstone; the identity/receipt provenance survives.

## §9 verdicts

| # | Question | Verdict | Note |
|---|---|---|---|
| 1 | Two-plane binding without re-adjudication; no `RECOVERY`/`RERUN`/`983` aliases | **PASS** | Both planes bound by exact verified hashes; successor identity clean |
| 2 | Decidable Custodian-only 2026 filtering; no successor 2026 acquisition or downstream transfer | **PASS** | Selected-field rule + validator "no 2026 output" predicate is decidable; honest that buffering is not provable |
| 3 | QA-accepted pre-observation commitment before first value-capable action; typed closed slots | **PASS** | §5.3 is complete; `UNPOPULATED_AT_PRECOMMIT` is correctly not a wildcard |
| 4 | Six-session rule unchanged; TVCA-S01 one-way stop, zero scientific vote | **PASS** | Rule dates and amounts match the accepted receipt exactly; mismatch → HOLD, never silent correction |
| 5 | Separately controlled output validation + Custodian scan before every crossing | **PASS** | Validator reads raw independently of projector; cell-equality, lattice, no-2026, sanitized-surface predicates present |
| 6 | Staged lifecycle acyclic; no post-observation edits, runtime identity selection, or pre-acceptance crossing | **PASS** with P3 | See F-1: one binding clause is worded acausally |
| 7 | 61-row crosswalk: four exclusive classes, legacy-only override, frozen slots, bounded claims | **PASS** | 61 = 983 − 922 reconciles with the held inventories |
| 8 | 922-baseline reconciliation; `UNCHANGED_INHERITED` rule; separation from TVCA-S01 | **PASS** | Balance equation is exact and reproducible from baseline + diff |
| 9 | Sole attempt, scanner timing, lane gates, non-self-executing transitions, final boundary, stop conditions jointly fail-closed | **PASS** | No path found from any failure to progression |

## Findings

- **F-1 (P3, wording):** §6.4 requires the immutable final composite manifest
  to bind "this plan and every later applicable Origin order." An immutable
  object cannot bind orders issued after it (the execution and release orders
  in §8 follow the composite). Reword to "every prior applicable Origin order";
  later orders bind the manifest, not the reverse. No lifecycle change needed.
- **F-2 (P3, proportionality — advisory, not a HOLD):** REV-02 is fail-closed
  and internally sound, but it spends six hash-specific orders, a sole-attempt
  live capture, three projections, two validators, and a ten-stage manifest
  chain to obtain evidence the plan itself classifies as zero-vote
  corroboration — and same-vendor agreement, which §4.2 says "must not be
  reported as independently validated amount truth." The accepted receipt
  already names SSGA's distribution page as the governing source. QA
  recommends Origin consider whether a REV-03 that clears the TVCA-S01 hold
  by `INDEPENDENT_ISSUER_COMPARISON` of the six ex-dates and amounts alone —
  with no TradingView value-capable interaction — is scientifically
  equivalent under the plan's own zero-vote definition. If Origin judges
  vendor-vintage consistency worth the cost, REV-02 stands as written.
- **F-3 (INFO):** Pine v6 syntax in the frozen carrier reviewed statically:
  `request.dividends`/`request.splits` signatures and `dynamic_requests` are
  valid v6 usage. Since no data-free compiler mode exists on TradingView, the
  plan's own rule makes any compile error consume the sole attempt; the static
  review lowers but does not eliminate that risk.

## Disposition

`REV02_PASS_ELIGIBLE_FOR_PRODUCT_OWNER_RATIFICATION` — with F-1 as a
wording correction that may be applied in the ratified text without a new
review cycle, and F-2 recorded for Origin's decision.

```yaml
rev02_identity_verification: PASS
q1..q9: PASS (q6 PASS with P3 wording note)
operational_authority_granted: NONE
scientific_authority_granted: NONE
```
