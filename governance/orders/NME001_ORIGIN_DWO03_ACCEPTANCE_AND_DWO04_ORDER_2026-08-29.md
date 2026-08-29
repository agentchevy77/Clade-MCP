# NME-001 Origin DWO-03 Independent Acceptance Review and DWO-04 Narrow Correction Order

Date: 2026-08-29  
Authority: Project Nexus Origin independent acceptance review; Product Owner retains external-contact, purchase, data-ingestion, and final-opening authority  
Research status: RESEARCH ONLY — NO FORMAL, PREDICTIVE, TRADING, ALERTING, OR AUTOMATED-ACTION AUTHORITY

## 1. Disposition

```yaml
reviewed_work_order: NME-001-DWO-03
disposition: HOLD_NARROW_PATCH_AND_RETEST
foundation_status: RETAIN_DWO03_AS_ENGINEERING_FOUNDATION_PENDING_DWO04_CORRECTION
next_work_order: NME-001-DWO-04
architecture_reopened: false
real_data_ingestion: HOLD
stage_final: HOLD
kibot_inquiry_state: PREPARED_NOT_SENT
```

DWO-03 substantially satisfies the amended order. Package identity, archive safety, deterministic reproduction, calendar construction, final-date independence, trailing-memory implementation, adaptive-history isolation, and registered authority holds all pass independent review.

One source-level P1 remains: a failed estimator fit can be reported as `OOD_ABSTAIN` when the shared OOD envelope flags that row. This cannot issue or score a forecast, but it contradicts the frozen attrition order and can corrupt future OOD, coverage, and common-origin reporting.

Three bounded P2/M1 corrections and one post-freeze custody record must join the same surgical patch. No model, feature, market question, provider account, data acquisition, regime router, dashboard, alert, execution model, or governance service is authorized.

## 2. Submitted and independently verified identity

```yaml
candidate_zip:
  filename: NME-001-DWO-03_UNREVIEWED_RESEARCH_CANDIDATE.zip
  bytes: 744862
  sha256: 35e8c082baaa72e892b47e7b05d9bbb6d17fd35eb54a5285917838d9ace46f02
external_manifest_sha256: 8988d1c4a2f33bc9e080b662a3f5804d606ca5e59031002c2809d3bb2008db9e
receipt_sha256: a0b2334d07d3a0ddac62a2954a72f1bcffa8c40daa498b301dc1f0af95021c46
protocol_v1_2_sha256: 052bb08f12c4216186b07232d6dbac8da6bb1b30202a7b07a80be2443a625c95
frozen_config_sha256: b323f10f8c6f6d2738d2d32ba470c18f2527449118d294c1b4ec45168eff4a56
dwo02_to_dwo03_patch_sha256: b05ade55f55a8b1ed766c5075d2de2e69833b54333c55542f1000ff80fb28823
authorized_dwo03_order_sha256: 8c340da0f567d68bd812daca1950d427f0cf39ba09ea7fa287709de60d046b2d
```

Independent reproduction established:

- all submitted hashes and sizes match;
- 109 unique, safe, canonical, unencrypted archive members;
- all 108 non-self manifest entries match their recorded bytes and hashes;
- no raw CSV, Parquet, Feather, bulk dataset, final product, or new-confirmation data is packaged;
- two fresh builds produced byte-identical wheels and source distributions;
- the candidate-only lane passed 555/555, with 59 licensed cases correctly deselected;
- the separate licensed regression passed 614/614 using only the three previously sealed, independently hash-matched TradingView fixtures;
- independent and packaged JUnit records contain the same 555 and 614 unique named cases with zero failures, errors, or skips;
- the sealed reproduction command returned PASS with the exact 614-case full inventory; and
- independent reconstruction reproduced the candidate ZIP and sidecars byte-for-byte.

These are engineering and regression results only. No new provider data or 2022–2024 final bytes were opened.

## 3. Scientific and final-independence passes

The following DWO-03 corrections are accepted:

1. The primary learner uses the latest 1,260 training-authorized, partition-eligible session identities. Membership is frozen before event, label, validity, fit, OOD, or score status is known.
2. Every outer fit is frozen for its 21-session test block. The final helper selects one pre-boundary 1,260-session window, fits once, and never rolls or refits inside the 630-session final.
3. Preprocessing, climatology, penalty selection, learned baselines, and the shared `MODEL_FULL` OOD envelope use only the permitted trailing memory.
4. `EXPANDING_MEMORY_DIAGNOSTIC` and five-year/breakpoint diagnostics are report-only and excluded from tuning, model selection, gates, promotion, and authority.
5. Calibration is evaluation-only and never modifies probabilities or later fits.
6. The pinned calendar reconstructs 6,734 ordinary sessions from 1998-01-02 through 2024-12-31 with the required predecessor buffer.
7. The proposed historical final is exactly 630 ordinary sessions from 2022-06-22 through 2024-12-31, after the 2022-06-21 boundary embargo.
8. Its ordered-session SHA-256 is `423f3ad6a8b398b12700710cdb37584ded4beac091d985118a7ebebf159bf429`.
9. Its overlap with every recorded `SCIENTIFICALLY_OPENED` or `UNKNOWN` prior session is zero.
10. No Project Nexus record recovered by the independent continuity search evidences earlier NME-001 scientific use of those 2022–2024 dates. This remains a procedural historical holdout, not a claim of cryptographic physical isolation.
11. Public configuration, pipeline, and internal final entry paths reject v1.0.1, v1.1.0, and v1.2.0 final activation before source construction.

A historical pass could establish only historical reaction-probability evidence. It could not establish present-market relevance, tradability, fills, spread, slippage, queue position, or profit. Prospective relevance still requires a separately sealed epoch strictly after 2026-08-28.

## 4. Remaining findings

### P1-01 — fit failure is misreported as OOD

Protocol v1.2 and the capacity note register the order:

```text
TECHNICALLY_EVALUABLE -> FITTED_MODEL -> IN_SUPPORT_AFTER_OOD -> COMMON_ORIGIN -> SCORABLE
```

The development and final prediction loops instead branch on the shared OOD mask before checking whether that estimator fitted. They can therefore emit `OOD_ABSTAIN` with no same-cohort/fold/model `FIT` record.

The exact licensed regression reproduces the defect for REAL `MODEL_FULL`:

```yaml
technically_evaluable_events: 9
distinct_event_sessions: 9
fitted_model_full: 0
technical_not_issued: 8
ood_abstain_without_fit: 1
affected_session: 2026-04-07
selected_C: null
```

No probability is issued or scored, so this is not an authority bypass. It is a mandatory reporting and attrition-integrity correction before any real run.

### P2/M1-02 — the capacity uncertainty estimand is mislabeled

The candidate applies binomial Clopper–Pearson limits to `9/84` and calls the quantity a technically evaluable origin rate. The protocol can produce two REAL origins in one session, so origins are not Bernoulli session trials. In the observed sample the nine origins happen to occupy nine distinct sessions, permitting `9/84` to be described as the incidence of at least one technical origin per session. It does not justify an unconditional “exact 95%” claim across serial, nonstationary sessions or a 1998–2024 projection.

This cannot change the present decision: scorable `MODEL_FULL` support is `0/84`, so every acquisition-clearance result remains false. The method must nevertheless be labeled and bounded honestly before acquisition or real-data authorization.

### P2-03 — capacity verification does not reconstruct the registered attrition chain

The capacity tests reload frozen counts and recalculate their own hard-coded values. They do not join licensed regression outputs to fit, OOD, common-origin, and scoring records, and therefore did not catch P1-01.

### P2-04 — strict configuration typing is loader-only

The JSON loader rejects booleans substituted for integers, but direct `ExperimentConfig` construction and `validate_config` rely on Python equality, where `True == 1`. This cannot currently elevate authority or alter the registered final because active runtime paths use the strict loader and all authority fields require exact strings. It remains a public contract inconsistency and must be closed in the same patch.

## 5. Acceptance-review custody event

During the independent licensed-fixture review, one reviewer directly displayed the final row of the already-held TradingView source:

```yaml
effective_date: 2026-08-29
source_session: 2026-08-28
timestamp_utc: 2026-08-28T19:55:00Z
prior_classification: PROCEDURAL_HOLDOUT_UNOPENED
new_classification: SCIENTIFICALLY_OPENED
other_2026_holdout_sessions_value_exposed_by_this_review: 0
```

This is a post-DWO-03-freeze exposure event, not an original candidate defect. It does not overlap the proposed 2022–2024 historical final and does not affect the separately future epoch strictly after 2026-08-28. Preserve exposure ledger v1.0.0 unchanged and record this event append-only in the canonical `NME001_PRIOR_EXPOSURE_LEDGER_v1_0_1.json` before the next candidate is frozen.

The event also demonstrates the disclosed procedural limitation: registered entry points can fail closed, but ordinary filesystem access cannot prevent or automatically journal an operator reading raw bytes. Do not reopen the Relay/evidence-vault architecture to address that at this stage. Maintain the exposure ledger and classify any future out-of-band inspection conservatively.

## 6. NME-001-DWO-04 — bounded correction order

The Developer may use its Codex executor, repair implementation and tests on the fly, and return one consolidated candidate without escalating routine coding choices. Escalate only a change to the market question, model/features, final identities, provider contact, account/cost action, data acquisition, real-data execution, or final opening.

### A. Preserve

1. Preserve DWO-03 candidate `35e8c082…46f02`, protocol v1.2.0, configuration, sidecars, evidence, and ledger v1.0.0 unchanged as historical artifacts.
2. Preserve the accepted calendar, 630 final identities, trailing-memory design, diagnostic isolation, authority holds, archive protections, and reproduction contract.
3. Make no feature, outcome, baseline, model, symbol, timeframe, regime, indicator, alert, execution, or trading change.

### B. Correct fit/OOD precedence

1. Continue computing one shared training-only OOD envelope and mask.
2. Inside each development and final model loop, first determine whether that exact cohort/fold/model has a successful fit.
3. If no fit exists, emit `TECHNICAL_NOT_ISSUED` with the registered fit failure. Do not emit `OOD_ABSTAIN`.
4. Only a fitted model may emit `OOD_ABSTAIN` or `ISSUED`.
5. Add a reconciliation invariant: every `OOD_ABSTAIN` or `ISSUED` row must join to one successful same-cohort/fold/model `FIT` record.
6. Preserve the shared OOD mask across candidate and baselines; do not allow a model to gain coverage by ignoring `MODEL_FULL` support.

### C. Correct capacity meaning

1. Freeze the nine distinct observed technical-event session identities or their ordered hash and define the binary estimand as `TECHNICAL_EVENT_SESSION_INCIDENCE`: at least one technically evaluable REAL origin in an outer-test session.
2. Do not call origins Bernoulli trials. Report the raw nine-origin/nine-session facts separately.
3. If Clopper–Pearson is retained, label it a conditional iid-binomial sensitivity, not unconditional exact coverage across time. It may not clear acquisition, interpretation, promotion, or authority.
4. Make scorable-`MODEL_FULL` row counts and per-class row counts the acquisition-relevant gate quantities, with distinct-session counts reported alongside. They remain zero in the opened sample.
5. Keep every acquisition-clearance flag false and the lane `FAIL_CLOSED_EXPLORATORY_ACQUISITION_PROPOSAL`.

### D. Complete verification and type enforcement

1. Add a hermetic regression where the OOD envelope exists, the test row is OOD, and one model fit fails; assert that model is `TECHNICAL_NOT_ISSUED` in development and final.
2. Reconstruct from the licensed regression: 168 `PARTITION_ELIGIBLE_OPPORTUNITY` rows; 9 `EVENT_SEALED`; 9 `TECHNICALLY_EVALUABLE` on 9 distinct sessions; class counts `1/1/2/5`; 0 `MODEL_FULL` `FIT`; 9 `MODEL_FULL` `TECHNICAL_NOT_ISSUED`; 0 `OOD_ABSTAIN`; 0 `ISSUED`; 0 `SCORABLE`; all clearance flags false.
3. Test the successful-fit OOD path so the precedence repair cannot disable valid `OOD_ABSTAIN` behavior.
4. Centralize strict runtime-type validation for the existing `ExperimentConfig` fields and their already-declared JSON/runtime types so file loading, `from_mapping`, direct construction, and `validate_config` reject boolean-for-integer and other wrong types consistently with `ContractError`. Do not coerce values, add schema fields, or introduce a validation service.
5. Update traceability to point to output-reconciled tests rather than frozen-count recitation alone.

### E. Update exposure custody without changing the final

1. Preserve ledger v1.0.0 byte-for-byte.
2. Create the canonical `NME001_PRIOR_EXPOSURE_LEDGER_v1_0_1.json`, append-only from v1.0.0, that reclassifies only 2026-08-28 as `SCIENTIFICALLY_OPENED` effective this acceptance review and records this decision's hash.
3. Recompute affected range counts and identities exactly; do not relabel any other session without evidence.
4. Reprove zero overlap between the unchanged 630-session 2022–2024 final and all `SCIENTIFICALLY_OPENED` or `UNKNOWN` sessions.
5. Bind the v1.2.1 configuration to the exact v1.0.1 ledger filename and SHA-256.

### F. Keep external and data actions reserved

1. DWO-04 itself authorizes no external contact. Preserve the Kibot inquiry exactly as `PREPARED_NOT_SENT` in the engineering candidate.
2. Do not contact Massive.
3. Do not create an account, trial, order, payment, credential, contract, NDA, download, API connection, or data ingestion.
4. The Product Owner's prior approval of the bounded Kibot inquiry remains valid as a separate lane; DWO-04 neither revokes nor executes it. Sending still requires the Product Owner's sender name, reply address, company-field choice, and explicit action-time confirmation. At send time, record the confirmation actor/time, exact message hash, submission time/identifier if supplied, and every vendor response. This is a contact record, not a new orchestration system.

### G. Return and retest

The release identity contract is:

```yaml
work_order: NME-001-DWO-04
candidate_id: NME001-DWO-04-CANDIDATE
candidate_version: 0.3.1
protocol_version: 1.2.1
partition_design_version: 1.2.0
```

Return one v1.2.1 / candidate 0.3.1 patch containing:

- exact candidate ZIP `NME-001-DWO-04_UNREVIEWED_RESEARCH_CANDIDATE.zip`;
- exact external manifest `NME-001-DWO-04_CANDIDATE_MANIFEST.json`;
- exact external receipt `NME-001-DWO-04_CANDIDATE_RECEIPT.json`;
- v1.2.0-to-v1.2.1 and candidate diffs;
- hash-bound v1.2.1 protocol and configuration, while preserving the v1.2.0 protocol and configuration byte-for-byte under versioned historical names;
- candidate manifest and receipt binding to this finalized DWO-04 order's filename and SHA-256;
- full hermetic and licensed named-test evidence;
- exact attrition-reconciliation evidence;
- corrected capacity/configuration note;
- canonical `NME001_PRIOR_EXPOSURE_LEDGER_v1_0_1.json`;
- deterministic build/package reproduction evidence; and
- a concise Developer handoff stating every unrun real/final/provider lane.

Run the complete hermetic and licensed suites plus focused independent non-author review. Add an explicit v1.2.1 authority regression: configuration, public pipeline, and internal final entry paths must reject v1.2.1 final activation before source construction, and every real-v1.2.1 development path must remain held. The licensed suite may use only the same three hash-verified fixtures through the preserved v1.0.1 regression lane, with zero scientific, design, or evidence vote. Do not run real v1.2.1 development, open the historical final, execute provider contact under this work order, or ingest new data.

## 7. Authority and stop state

```yaml
development_engineering_foundation: DWO03_RETAINED
formal_evidence_authority: NONE
predictive_authority: NONE
trading_authority: NONE
alerting_authority: NONE
automated_action_authority: NONE
real_v1_2_0_development: NOT_RUN
real_v1_2_1_development: HOLD
stage_final: HOLD
historical_final_opened: NO
new_confirmation_data_authority: HOLD
kibot_inquiry: PREPARED_NOT_SENT
external_provider_contact_during_dwo04: NONE_AUTHORIZED
massive_contact_any_form: NOT_AUTHORIZED
account_trial_purchase_credentials_download_ingestion: HOLD
```

## 8. Plain-language course statement

The laboratory, calendar, sealed exam dates, and adaptive-memory design are sound. One dashboard light is wired in the wrong order: when the engine has no fitted model but also sees an out-of-distribution row, it labels the row “outside the map” instead of first saying “no engine was built.” Nothing moves and no forecast escapes, but the maintenance record is wrong. Correct that wire, make the capacity statistic say exactly what it measures, close the small type/test gaps, record the one 2026 session exposed during this review, and retest the same machine. Do not redesign the laboratory.
