# NME-001 Origin DWO-04 Independent Acceptance Review and DWO-05 Narrow Correction Order

Date: 2026-08-29  
Authority: Project Nexus Origin independent acceptance review; Product Owner retains external-contact, account, purchase, data-ingestion, real-data, and final-opening authority  
Research status: RESEARCH ONLY — NO FORMAL, PREDICTIVE, TRADING, ALERTING, OR AUTOMATED-ACTION AUTHORITY

## 1. Disposition

```yaml
reviewed_work_order: NME-001-DWO-04
disposition: HOLD_NARROW_PATCH_AND_RETEST
foundation_status: RETAIN_DWO04_AS_ENGINEERING_FOUNDATION_PENDING_DWO05_CORRECTION
next_work_order: NME-001-DWO-05
architecture_reopened: false
market_question_changed: false
model_or_feature_change_authorized: false
real_data_ingestion: HOLD
real_v1_2_1_development: HOLD
real_v1_2_2_development: HOLD
stage_final: HOLD
historical_final_opened: NO
kibot_inquiry_state: PREPARED_NOT_SENT
```

DWO-04 closes the ordered fit-before-OOD defect, strict configuration typing,
capacity-estimand labeling, and exposure-ledger correction. Its submitted ZIP
is clean, deterministic, and correctly reports zero licensed `MODEL_FULL`
fits, OOD abstentions, issuances, and scorable rows.

It cannot receive final engineering acceptance because one ordinary documented
build path can package all three separately held licensed CSVs into a source
distribution. That is one P1 custody/build-path defect. The independent audit
also found two related P2 gaps in the generic output-backed capacity
reconciler. These gaps do not change the current zero-score result and cannot
grant authority, but they can certify incomplete or contradictory positive
support evidence in a future run.

Authorize one consolidated DWO-05 correction. It is a build-safety and
evidence-reconciliation closeout, not a new research phase. The Developer may
repair routine implementation details and negative tests autonomously and
return one candidate; no interim approval is required unless a frozen boundary
listed in Section 7 would change.

## 2. Submitted and independently verified identity

```yaml
candidate_zip:
  filename: NME-001-DWO-04_UNREVIEWED_RESEARCH_CANDIDATE.zip
  bytes: 1800260
  sha256: a08a2c9df9df6d34267e4c0bb0afdd0acfc78c1d98b29de48964f9698b0619c6
external_manifest:
  bytes: 2088
  sha256: cf000cdadfbfd14b787483907259558fe0299e041eb3ce97185bb2efad3cc2a6
external_receipt:
  bytes: 2100
  sha256: 54b9a12150c85f6ec3c3a4a3dfc33e7e6b7a4ef280f38a440be8ab41ba1579ea
dwo03_to_dwo04_patch:
  bytes: 577192
  sha256: 60f9a84b7f541087934a7c62da507499f4ea68ab59a0c799cadf9551f55d6e70
embedded_manifest:
  bytes: 206649
  sha256: da5ce6d9b71eafe25857a9fa21ae8dfcd16016e7572eda4af2d8bbda113f8b84
authorized_dwo04_order_sha256: f5feb728d513c9bb827bb436000ac68d56f0fea395fd6593c778a21cafc54cba
```

Independent package and execution results:

- 133 unique, canonical, regular, unencrypted ZIP members;
- no path traversal, aliases, case-fold collisions, ZIP comment, or trailing payload;
- every one of the 132 non-self manifest entries independently matched its recorded size and SHA-256;
- receipt, external manifest, embedded manifest, candidate, protocol, configuration, and DWO-04 order bindings reconcile exactly;
- the exact DWO-03 baseline plus the submitted patch reconstructed all 122 governed DWO-04 files byte-for-byte;
- sealed reproduction returned PASS with the exact 713-case hermetic and 773-case full inventories;
- independent hermetic execution passed 713/713, with the 60 licensed cases correctly deselected;
- an isolated, fixture-backed licensed execution passed 773/773 using only the same three hash-verified TradingView fixtures;
- both independent named-test sets exactly match the submitted JUnit sets, with zero failures, errors, or skips; and
- the clean staged wheel and source-distribution reproduction recorded in the package is byte-deterministic.

One reviewer-side licensed attempt produced 772 passes and one environment
failure because two concurrent review processes resynchronized the same
temporary virtual environment while a nested subprocess launched. The failed
assertion was `ModuleNotFoundError` for the already-installed local package,
not a candidate test failure. The complete lane was rerun in a dedicated
offline environment and passed 773/773. Both attempts are disclosed; only the
isolated rerun is probative.

No provider contact, external transmission, new data, real v1.2.1 execution,
or historical-final opening occurred.

## 3. DWO-04 corrections accepted

The following results are accepted and must remain unchanged:

1. Development and final now test the exact cohort/fold/model fit before OOD.
2. A missing or failed fit yields `TECHNICAL_NOT_ISSUED`, never `OOD_ABSTAIN`.
3. Every actual `OOD_ABSTAIN` or `ISSUED` row in the licensed run has exactly one successful same-cohort/fold/model `FIT` record.
4. The licensed REAL `MODEL_FULL` result is exactly 9 technically evaluable origins on 9 sessions, 0 `FIT`, 9 `TECHNICAL_NOT_ISSUED`, 0 OOD, 0 issued, and 0 scorable.
5. The technical classes remain `1/1/2/5`, and all acquisition-clearance flags remain false.
6. `TECHNICAL_EVENT_SESSION_INCIDENCE` is correctly a binary session estimand. Its Clopper–Pearson interval is explicitly a conditional iid-binomial sensitivity with zero acquisition, interpretation, promotion, gate, or authority vote.
7. Every declared `ExperimentConfig` runtime type fails closed across JSON loading, `from_mapping`, direct construction, and `validate_config`; an independent 840-case wrong-type matrix found zero acceptances.
8. Protocol v1.2.0, configuration v1.2.0, exposure ledger v1.0.0, and the DWO-03 candidate remain byte-exact historical records.
9. Ledger v1.0.1 reclassifies only 2026-08-28 as `SCIENTIFICALLY_OPENED`; its counts, ranges, hashes, parent binding, and order binding reconstruct exactly.
10. The 630-session historical final remains unchanged, unopened, and disjoint from every opened or unknown ledger identity.
11. Public configuration, development, pipeline, and internal final paths reject real v1.2.1 or final activation before source construction.
12. No model, feature, outcome, baseline, symbol, timeframe, regime router, alert, action, or trading behavior changed.

## 4. Remaining findings

### P1-01 — ordinary source-distribution build includes licensed raw data

The sealed DWO-04 candidate ZIP is clean. The release tool obtains its clean
build evidence by creating prefiltered staging trees in which `data/raw` is
already absent. The project-level Hatch configuration, however, restricts only
the wheel target and does not exclude `data/raw` from the source-distribution
target.

After the three exact registered fixtures were placed at their required
licensed-regression paths, the ordinary documented command equivalent to:

```text
uv build --offline --wheel --sdist .
```

produced a safe wheel but a 3,168,359-byte `.tar.gz` containing all three CSVs,
whose uncompressed raw payload totals 5,038,692 bytes. Two independent builds
were byte-identical, demonstrating a deterministic leak path rather than random
contamination.

No such distribution was sent, saved as a Nexus deliverable, or included in
the submitted candidate. The temporary review builds were isolated as
sensitive and are not authorized for use or sharing. No session value was
intentionally inspected, so this mechanical custody event does not reclassify
another market session scientifically.

This is P1 because an ordinary build can create a shareable artifact containing
the full licensed payload, while the recorded build proof exercises only a
sanitized staging condition.

### P2-02 — failed-fit and prediction evidence is not completely reconciled

The generic capacity reconciler validates identities only for successful
`FIT` records and for `OOD_ABSTAIN`/`ISSUED` predictions. It can return
`prediction_fit_reconciliation: PASS` for:

- an empty fit-attempt ledger;
- an empty or malformed failed-fit row;
- duplicate failed-fit rows;
- a successful and failed row sharing one identity;
- failed rows with a wrong fold; and
- additional `TECHNICAL_NOT_ISSUED` predictions with missing or unknown cohort/fold/model identity.

The actual pipeline output is clean: 40 fit-attempt rows have 40 unique keys,
and its stricter generation-time reconciliation rejects duplicate fit
identities. The defect is therefore in the standalone evidence verifier, not in
the frozen licensed result or fit-before-OOD execution.

### P2-03 — `SCORABLE_MODEL_FULL` and common-origin evidence are under-bound

The registered attrition narrative includes `COMMON_ORIGIN`, but the capacity
reconciler counts candidate issued/scored identifiers without validating:

- the scored row's exact cohort/fold/session/class join;
- the candidate probability vector;
- mandatory baseline prediction validity; or
- comparator-specific common-origin counts and retention.

An adversarial positive-support fixture with no baseline predictions and no
probability fields was counted as scorable. A forged or absent scored-row fold
was also accepted. This cannot change DWO-04's exact zero-issued result and
every clearance remains forcibly false, but the reconciler is not yet adequate
to certify positive future support.

## 5. NME-001-DWO-05 — consolidated narrow correction order

### A. Preserve the accepted foundation

1. Preserve DWO-04 candidate `a08a2c9d…b0619c6`, all sidecars, protocol v1.2.1, configuration, exposure ledger v1.0.1, and test evidence unchanged as historical artifacts.
2. Preserve the accepted fit-before-OOD execution, shared OOD mask, calendar, trailing-memory design, adaptive-history isolation, capacity session estimand, custody classifications, historical-final identities, and authority holds.
3. Add no feature, outcome, baseline, estimator, symbol, timeframe, regime, indicator, alert, execution, forecast action, or trading behavior.

### B. Make every ordinary distribution build raw-data safe

1. Add an explicit Hatch source-distribution exclusion covering the complete root-relative `data/raw/**` tree. The minimum acceptable configuration is:

   ```toml
   [tool.hatch.build.targets.sdist]
   exclude = ["/data/raw/**"]
   ```

2. Retain the exact wheel package allowlist. Do not rely on a prefiltered staging tree as the only safety mechanism.
3. From the actual project root, prove ordinary wheel and source-distribution builds exclude every `data/raw` path and byte under three conditions: no raw directory, a hermetic sentinel CSV, and all three exact licensed fixtures at their registered paths.
4. In the fixture-backed lane, scan both distributions for filenames, exact fixture bytes, complete raw rows, and the already-registered bounded raw/Base64/hex fragments. Any hit fails packaging.
5. Make release verification exercise the fixture-present root build before freezing, then verify the final candidate archive remains raw-free. The sanitized staged build may remain as an additional reproducibility check, not the sole proof.
6. Record clean-root and fixture-present build inventories, sizes, hashes, and exclusion results separately. Do not publish or retain a fixture-bearing distribution as a deliverable.
7. Reuse only the same three already-held, hash-verified TradingView fixtures under the preserved v1.0.1 licensed-regression authority. Their use is ephemeral and limited to regression and package-exclusion proof, with zero scientific, design, formal-evidence, predictive, or trading vote. Do not retain a fixture-bearing wheel, source distribution, ZIP, or other derived deliverable.

### C. Reconcile every fit attempt and prediction row

1. Validate every fit row before branching on status. Require exact types and registered identities for cohort, outer fold, model, and status.
2. Permit only the generated statuses `FIT`, `INSUFFICIENT_TRAINING_CLASS_OR_FIT`, and `NO_TEST_ORIGINS` in the development reconciliation lane.
3. Derive the expected fit-attempt key set from the registered outer folds, cohorts `REAL`/`PSEUDO`, and frozen `MODEL_ORDER`; require exactly one fit-attempt row for every expected key and no other key.
4. Reject missing, duplicate, conflicting, malformed, boolean, fractional, coercible, noncanonical, unknown-cohort, unknown-model, and wrong-fold fit rows regardless of success/failure status.
5. Validate every prediction row's complete opportunity/cohort/fold/model/status identity before status branching, including `TECHNICAL_NOT_ISSUED`.
6. Derive the complete registered expected prediction-key set from the exact prediction-stage opportunity/event identities crossed with frozen `MODEL_ORDER` inside each cohort/fold. Require exactly one prediction row for every expected key, no omission, and no extra key.
7. Require every prediction key to join to exactly one fit-attempt record. Retain the stricter rule that `OOD_ABSTAIN` or `ISSUED` requires that record's status to be `FIT`.
8. Reconcile prediction opportunity/session/cohort/fold identity to the exact eligibility and event outputs for every model, not only REAL `MODEL_FULL`.

### D. Make positive scorable and common-origin evidence exact

1. Define candidate `MODEL_FULL` scorable support as an exact evaluated `ISSUED` prediction with a valid finite four-class probability vector, registered class label, and complete opportunity/session/cohort/fold identity.
2. Reconcile every scored row to the exact candidate prediction, eligibility, and event on opportunity ID, session, cohort, fold, and class. Reject missing, duplicate, conflicting, unknown, or coercible identities.
3. Compute and report comparator-specific common-origin counts and retention for every mandatory baseline from valid issued prediction rows. For each baseline, freeze the denominator as the complete valid scorable REAL `MODEL_FULL` candidate-origin set and the numerator as its exact intersection with that baseline's valid scorable issued-origin set. If the denominator is zero, report retention as `NOT_ESTIMABLE`, never as a favorable value. Do not imply that candidate-only scorable support is itself common-origin evidence.
4. Treat absent, malformed, duplicate, or identity-mismatched comparator evidence as a structural reconciliation failure. Treat one present, exact `TECHNICAL_NOT_ISSUED` comparator row as legitimate attrition: it contributes zero common support and failed retention but does not make the output relation structurally invalid. Apply the analogous registered meaning to a valid support abstention.
5. Represent the attrition structure honestly: candidate scorable support and comparator-specific common-origin support may branch after valid issuance rather than being mislabeled as one unproved linear stage.
6. Keep the acquisition-relevant candidate total/per-class row counts and distinct-session counts visible alongside every comparator's common-origin counts. Do not weaken any existing threshold or retention requirement.
7. Preserve DWO-04's exact licensed facts: zero REAL `MODEL_FULL` issued/scorable rows, zero candidate scorable sessions, zero per-class support, and all acquisition-clearance flags false.
8. Generic or synthetic reconciliation remains authority `NONE`; exact licensed provenance may attach only after the complete fixture identity and output relation are independently verified.

### E. Add one comprehensive adversarial relation matrix

At minimum, add negative tests for:

- empty, missing, malformed, duplicate, conflicting, wrong-fold, wrong-cohort, wrong-model, and unknown-status fit rows;
- missing, duplicate, malformed, unknown-identity, boolean/fractional-fold, and unsupported-status prediction rows, including `TECHNICAL_NOT_ISSUED`;
- `OOD_ABSTAIN` or `ISSUED` without one exact successful fit;
- scored rows with missing/forged cohort, fold, session, class, or opportunity identity;
- issued predictions with missing, nonfinite, out-of-range, wrong-length, or non-unit-sum probabilities;
- candidate-positive support with each mandatory baseline absent, malformed, duplicate, invalid, or identity-mismatched, each of which must fail structurally;
- candidate-positive support with one present, exact `TECHNICAL_NOT_ISSUED` or valid OOD baseline row, which must reconcile successfully but contribute zero common support and fail retention when the candidate denominator is positive;
- duplicate or contradictory comparator rows;
- sentinel and exact licensed raw paths/fragments in ordinary wheel/sdist builds; and
- mutation of any clearance flag, authority field, ledger binding, historical-final identity, or v1.2.1/v1.2.2 real/final hold.

Include positive controls for a complete successful-fit OOD row, a complete
candidate-scored row, and valid comparator-specific common-origin joins. Tests
must reconstruct outputs, not merely restate frozen counts.

### F. Release identity and return

The DWO-05 release identity contract is:

```yaml
work_order: NME-001-DWO-05
candidate_id: NME001-DWO-05-CANDIDATE
candidate_version: 0.3.2
protocol_version: 1.2.2
partition_design_version: 1.2.0
```

Return exactly one consolidated candidate with:

- `NME-001-DWO-05_UNREVIEWED_RESEARCH_CANDIDATE.zip`;
- `NME-001-DWO-05_CANDIDATE_MANIFEST.json`;
- `NME-001-DWO-05_CANDIDATE_RECEIPT.json`;
- DWO-04-to-DWO-05 candidate patch and v1.2.1-to-v1.2.2 protocol diff;
- hash-bound protocol v1.2.2 and active configuration;
- preserved versioned protocol/configuration v1.2.1 and all older accepted foundations;
- byte-identical exposure ledger v1.0.1 and historical-final identity file;
- exact output-reconciliation artifact including candidate-scored and comparator common-origin evidence;
- complete hermetic and licensed named JUnits;
- clean-root, sentinel-present, and fixture-present wheel/sdist exclusion evidence;
- deterministic package, patch-reconstruction, and sealed-reproduction evidence; and
- a concise handoff identifying every unrun real, final, provider, acquisition, and authority lane.

Bind the candidate, external manifest, receipt, protocol, configuration,
reconciliation evidence, and this finalized order's filename/SHA-256. Run the
complete hermetic and licensed suites and a focused independent non-author
review. The Developer may correct any routine edge case within Sections B–E
before returning; do not stop for intermediate approval unless a frozen scope
boundary would change.

## 6. Acceptance conditions for DWO-05

DWO-05 is eligible for independent acceptance only when:

1. all submitted identities and archive members verify;
2. the ordinary fixture-present source-distribution build is proven raw-free;
3. every fit, prediction, scored, and comparator row participates in the exact registered relations or fails closed;
4. candidate-scored and comparator common-origin quantities are separately and correctly named;
5. the current licensed zero-score reconstruction remains exact;
6. all hermetic, licensed, build, patch, and sealed-reproduction tests pass with no failure, error, or skip disguised as PASS; and
7. all real-data, final, provider, predictive, and trading holds remain unchanged.

Do not create a DWO-06 merely for cosmetic wording, additional packaging
ceremony, or a non-authoritative P3 with no credible effect on data custody,
scientific interpretation, reproducibility, or a future positive-support
decision. Record such debt in the handoff and proceed to the substantive data
decision after DWO-05 acceptance.

## 7. Reserved boundaries and authority state

DWO-05 does not authorize:

- provider contact under this work order;
- an account, trial, order, purchase, payment, contract, NDA, credential, sample, download, API connection, or ingestion;
- new or non-regression real v1.2.1/v1.2.2 data execution;
- historical-final or prospective-final opening;
- modification of the 630-session historical-final identities;
- model, feature, baseline, outcome, market, or partition-design expansion; or
- formal, predictive, trading, alerting, or automated-action authority.

The Product Owner's separate bounded Kibot-inquiry authorization remains valid
and is neither revoked nor executed by DWO-05. It still requires the missing
sender name, reply address, company-field choice, and explicit action-time
confirmation before the exact unchanged message may be submitted. At send
time, record the confirmation actor/time, exact message hash, submission
identifier/time if supplied, and every vendor response.

```yaml
development_engineering_foundation: DWO04_RETAINED_PENDING_DWO05
development_evidence_authority: NONE
formal_evidence_authority: NONE
predictive_authority: NONE
trading_authority: NONE
alerting_authority: NONE
automated_action_authority: NONE
real_v1_1_development: HOLD_PENDING_CORRECTED_PROTOCOL_AND_SEPARATE_DATA_INGESTION_AUTHORITY
real_v1_2_0_development: NOT_RUN
real_v1_2_1_development: HOLD
real_v1_2_2_development: HOLD
stage_final: HOLD
historical_final_opened: NO
v0_1_0_final_authority: HOLD
new_confirmation_data_authority: HOLD
kibot_inquiry: PREPARED_NOT_SENT
external_provider_contact_during_dwo05: NONE_AUTHORIZED
massive_contact_any_form: NOT_AUTHORIZED
account_trial_purchase_credentials_download_ingestion: HOLD
```

## 8. Plain-language course statement

The repaired engine now labels a failed fit correctly, the calendar and sealed
exam remain intact, and the current licensed result is still honestly zero.
Two inspection gauges, however, can certify incomplete paperwork, and the
ordinary shipping-box command can accidentally place the raw licensed cargo
inside the box. DWO-05 locks the raw-data storeroom out of every ordinary
distribution and makes the inspection gauge trace every fit, forecast, score,
and comparator relationship end-to-end. Then this infrastructure closeout
ends and Nexus returns to the substantive data decision.
