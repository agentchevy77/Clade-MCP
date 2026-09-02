# NME-001 — Origin Legacy TVCA Closure and Prospective Successor Plan REV-02

Document ID: `NME001-TVCA-LEGACY-CLOSURE-AND-SUCCESSOR-PLAN-REV02`  
Date: `2026-09-02`  
Governing experiment: `NME-001`  
Governing work order: `NME-001-SEO-01`  
Origin status: `REV01_INDEPENDENT_QA_HOLD / REV02_DRAFT_FOR_PRODUCT_OWNER_AND_INDEPENDENT_QA`  
Decision sought now: `APPROVE_REV02_FOR_INDEPENDENT_QA_REVIEW_ONLY`  
Operational authority created by this draft: `NONE`  
Formal, predictive, trading, alerting, and automated-action authority: `NONE`

## 1. Origin disposition and revision provenance

The Product Owner's exhaustive search is closed. The missing historical TradingView corporate-action fixture remains:

```yaml
legacy_fixture: BATS_SPY_5m_RTH_20250102_20260828_CORPORATE_ACTION_CHECK_DEV_ONLY.csv
expected_size_bytes: 2066778
expected_sha256: 11215bd7ce1fec4d8fb2b92c3437e3085de67a909a41a9324ddf726a1f86a5c8
recovery_disposition: LEGACY_CORPORATE_ACTION_FIXTURE_UNRECOVERABLE_AFTER_EXHAUSTIVE_SEARCH
payload_status: REFERENCED_ONLY_PAYLOAD_NOT_FOUND
byte_replacement: NONE
further_archaeology: NOT_REQUIRED
```

This is a closed recovery outcome, not evidence that the historical file never existed. Its registered identity, receipt, manifests, and historical records remain provenance. If the exact bytes later surface incidentally, they must be quarantined and independently adjudicated; they do not automatically enter an active lineage.

REV-01 remains frozen on independent-QA `HOLD`. It is not amended in place and did not pass review:

| Record | Durable identity | SHA-256 | Disposition |
| --- | --- | --- | --- |
| REV-01 plan | `libfile_2ae78bc639c88191a2957459babb26c0`, version 1 | `874fc00113ccd0c9da0c14d56753f320806a881deccaaf4bf5d71041ab6d7b6f` | `INDEPENDENT_QA_HOLD` |
| Formal QA Submission 01 | `libfile_f8906e6296648191a0876926a8b8c8ff` | `ff89bdb12889750dc2a0d77f566700ab966135db630d076843a701a8f19fb2a0` | `REVIEW_ONLY` |
| QA Review A — Science | `libfile_6a0b2e68f99881919a5f98f0747d1d27` | `41de33a5fbcb2172177d657a5f6410088c21f8bb460b4bd0ac1a6f6f968ec124` | `HOLD` |
| QA Review B — Custody | `libfile_ba0fc02c4b9c8191ae5d38caa5644e12` | `f737dca00c57102b0143383b5fc3ce8f188cd20d206406ccda5de7cf95949122` | `PASS` |
| QA Review C — Adversarial | `libfile_21e1921890d8819190181e6f2fa100f1` | `2cb68b492ed8d53257531ae1dcdb5f7560ee31c6bba4efe507573dd640063093` | `HOLD` |
| QA Adjudication D | `libfile_32f35c6e072881919b4eb9cfb88350b3` | `45f988d335f918bfeefa932d23b7bfdaf8ff976d1bdca809ad637d64df0655c2` | `HOLD / REVISION_PERMITTED` |

REV-02 is the separately identified prospective correction allowed by Adjudication D. It incorporates only the eight normalized corrections `D-NMC-01` through `D-NMC-08`. It does not authorize source work, collection, qualification, licensed access, compilation, acquisition, projection, execution, scanning, release, Kibot access, or historical-final access.

## 2. Exact historical status and successor separation

### 2.1 Two-plane DWO-05 status

The historical record contains two simultaneously true planes. They must not be collapsed into a single `PASS` or `NOT_RUN` token.

Controlling durable foundation:

```yaml
clean_resumption_bundle:
  library_file_id: libfile_e716d00202688191a1ac59c2343e4edf
  size_bytes: 4005350
  sha256: 8cb8151a9ef619db96d5f9ed4d8c6ba01f635b309a0224634432b523d952ffbd
origin_clean_resumption_acceptance:
  library_file_id: libfile_8100a8ab25d88191b1085e05e293ff53
  size_bytes: 14632
  sha256: 08d82c10faa92befdca4e391fd4e04d1399b6d2d78c989516016ad3d63c32f5d
```

Historical paused Developer checkpoint:

```yaml
checkpoint_status: PAUSED_PRESERVED_FOR_REGROUPING
status_member:
  path: checkpoint/NME-001-DWO-05_PAUSE_AND_REGROUP_NOTE_2026-08-29.md
  size_bytes: 5840
  sha256: a3caaf9fbc0fc678a2eca241dcfbbd0fc94a142490702d7417321749bd07b15f
historical_developer_licensed_record:
  path: pytest_dwo05_licensed.xml
  size_bytes: 144229
  sha256: cbc075f49e29caddbbcd212078ca565a6858fd7cb8c5cda0d3c20992506d1efe
  recorded_result: PASS_983_OF_983_ZERO_FAILURES_ERRORS_SKIPS
  ordered_inventory_sha256: 15138cc5ffc83929e566b1024270cd62e6ec8d70d57c1500cf28763cbd3ea12e
  independent_origin_licensed_reproduction: NOT_RUN
  formal_evidence_authority: NONE
dwo05_candidate_created: false
```

Later Origin-accepted clean-resumption state:

```yaml
clean_layer_status: ACCEPTED_FIXTURE_FREE_RESTART_FOUNDATION
origin_fixture_free_reproduction:
  recorded_result: PASS_922_OF_922_ZERO_FAILURES_ERRORS_SKIPS
  junit_size_bytes: 135229
  junit_sha256: 6a6b71639543fddc902f541fbb3514cf13b4a0130813d5d5db5c226cf1612978
licensed_inventory_collection_only:
  count: 983
  ordered_inventory_sha256: 15138cc5ffc83929e566b1024270cd62e6ec8d70d57c1500cf28763cbd3ea12e
  licensed_cases_executed_by_clean_resumption: 0
licensed_lane: NOT_RUN_NOT_AUTHORIZED
release_matrix: NOT_RUN_NOT_AUTHORIZED
dwo05_release_candidate: NOT_CREATED
dwo04_release_candidate_parent: RETAINED_PENDING_DWO05_CANDIDATE
formal_evidence_authority: NONE
```

Accordingly: a preserved paused-Developer-checkpoint JUnit records 983/983 licensed cases passing, with authority `NONE`. The later accepted clean-resumption operation did not repeat those licensed cases; it independently reproduced the 922-case fixture-free lane, bound the 983 inventory by collection only, left the licensed lane and release matrix `NOT_RUN_NOT_AUTHORIZED`, and created no DWO-05 release candidate. DWO-04 remains the retained release-candidate parent. Neither plane erases or upgrades the other.

The preserved checkpoint member manifest is historical, not the composition manifest for the assembled clean layer. Current clean-layer composition is governed by `NME001_DWO05_CLEAN_RESUMPTION_LAYER_MANIFEST.json`, 71,825 bytes, SHA-256 `a6ed0f1e55bfbc9892eaef3940b44a1765137312f49c3bee8ff50d5905c04b30`, inside the exact QA-delta package `libfile_d316dd90c110819182e72682daad07ff`, SHA-256 `f168863f2530c2047c5d7cffc99876c86ed13e0296e3173bc5d6385c1efbe5a3`. REV-02 makes no blanket claim that every checkpoint path is byte-identical inside the clean layer.

### 2.2 Surviving fixture custody

| Fixture | Stable identity | Bytes | SHA-256 |
| --- | --- | ---: | --- |
| Untouched | `libfile_09b7172563fc819196ffcaf1329776f8` | 1,453,678 | `ee9391284564b85e8875aa95be51eb74898d38455e87e9e5335c07ad79214985` |
| Split check | `libfile_7960fcb71af88191809af6f37cee8bde` | 1,518,236 | `10231f1451f79a09b8242528d78adf239bf6c55c2ff014735d9754a9f1ad519d` |

Their partial custody receipt remains `libfile_5989b22a466481919f850f16d9a9ab55`, SHA-256 `85c7dc033c1491f3f85b94772d641fc20748509fba3c8fc306ab1d100ee00e99`.

### 2.3 New lineage and naming

Origin proposes one prospective successor contract:

`NME001-TVCA-SUCCESSOR-01` (`TVCA-S01`)

It must never be described as recovery, recreation, reconstruction, replacement, completion, or execution of the missing-byte lineage. It cannot prove byte or semantic equivalence to the lost 2026-08-28 vintage or rewrite either historical DWO-05 plane.

The only canonical future successor execution identity is:

`NME-001-SEO-01-TVCA-S01-EXECUTION-01`

No successor order, receipt, report, archive, JUnit, manifest, scan record, or aggregate evidence may use `RECOVERY`, `RERUN`, or `983` as a successor alias. Literal historical identities may be quoted only as historical provenance.

## 3. Scientific boundary and one-way provenance stop

The corporate-action rule can affect scientific eligibility; TVCA is therefore not purely engineering evidence. The frozen scientific rule remains bound to:

- bundle `NME-001-DWO-05_CLEAN_RESUMPTION_INPUT_BUNDLE.zip`, SHA-256 `8cb8151a9ef619db96d5f9ed4d8c6ba01f635b309a0224634432b523d952ffbd`;
- member `data/receipts/corporate_action_check_receipt.json`, SHA-256 `499cf40b047de88cf07b76b549b1a9d38529e9612fac0354cfab5ff4459d0964`;
- member `data/receipts/source_receipt.json`, SHA-256 `c8744332a3c07a770fd0ba4b1bf7927f0539bee4aebd39fa2fc4c2b2c6106551`; and
- enforcing source member `src/nexus_nme001/pipeline.py`, SHA-256 `cea08d93523448dcd687a1269bff50106813c9b6feca283523d834189db3e8d6`.

The rule is: each listed ex-date is a corporate-action boundary session; if it is inside the development-session inventory, every affected opportunity on that session receives `CORPORATE_ACTION_BOUNDARY` and is excluded from valid fitting, labeling, prediction, and scoring. It does not automatically exclude the next session and permits no reach-back or successor-day invention. The dates are:

- `2025-03-21`
- `2025-06-20`
- `2025-09-19`
- `2025-12-19`
- `2026-03-20`
- `2026-06-18`

No already-materialized Kibot eligibility ledger is asserted here. At the source-only checkpoint, the canonical six-date/rule object, accepted development-session inventory, and deterministic ordered eligibility/no-reachback result must be bound so unchanged behavior is reproducible. The successor cannot generate, add, remove, move, or reinterpret any exclusion.

`TVCA-S01` is a custody/provenance corroboration with zero evidentiary weight in scientific inference. It cannot alter scientific inputs, eligibility, transformations, features, labels, fitted values, predictions, probabilities, metrics, baseline comparisons, advancement criteria, confidence, or interpretation. Failure, uncertainty, incomplete evidence, custody defect, or mismatch creates or preserves an operational `HOLD`. A `PASS` can only remove the TVCA-S01-specific operational hold after the applicable later Origin order exists; it cannot validate, improve, promote, or increase confidence in a scientific result and cannot create authority.

```yaml
tvca_s01_scope: OPENED_2025_DEVELOPMENT_ONLY
tvca_s01_scientific_vote: ZERO
tvca_s01_failure_effect: ONE_WAY_OPERATIONAL_HOLD
tvca_s01_pass_effect: REMOVES_ONLY_TVCA_S01_SPECIFIC_HOLD_PENDING_SEPARATE_ORDER
tvca_s01_pass_scientific_effect: NONE
legacy_2026_boundary_verification: NOT_REPLACED_NOT_RUN
stage_final_tvca_dependency: UNRESOLVED
parent_successor_output_equivalence: NOT_ESTIMABLE
```

The scientific-development lane continues to use the accepted Kibot vintage as its sole market-row source. All TradingView raw files, projections, and market-bearing capture records must be absent from that lane.

## 4. Pre-acquisition truth and honest 2026 semantics

Everything in this section remains ineligible for action until its exact future Origin order exists.

### 4.1 Authorized 2025 lattice

After an accepted source-only checkpoint and a separate licensed-preflight order, a licensed Custodian process becomes eligible to derive the exact 2025 lattice from the durable untouched fixture. The process may parse pre-existing 2026 `time` cells inside raw custody solely to exclude non-2025 rows. It may not select, emit, log, durably copy, or transfer any 2026 OHLCV or other prohibited value.

The canonical lattice artifact must bind:

- exact ordered UTC timestamps whose `America/New_York` session date is in calendar year 2025;
- first and last timestamp;
- row count;
- serialization rule and SHA-256; and
- disclosure token `PREEXISTING_2026_TIME_FILTERING_OCCURRED_INSIDE_RAW_CUSTODY` when applicable.

No 2026 row or value may enter a projection or reach Developer, ordinary QA, or the scientific executor. This is a selected-field and custody-crossing rule; it does not make the impossible claim that file I/O or a raw-custody parser never physically buffers an unselected byte.

### 4.2 Pre-observation reference matrix

Before a value-capable TradingView interaction, QA must freeze these 2025 expectations from the accepted historical receipt and reconcile event/date/instrument/listing facts to identified issuer evidence:

| Ex-date | Expected field | Historical TradingView gross amount |
| --- | --- | ---: |
| `2025-03-21` | `DIVIDEND_GROSS` | `1.69552803` |
| `2025-06-20` | `DIVIDEND_GROSS` | `1.76111698` |
| `2025-09-19` | `DIVIDEND_GROSS` | `1.83111405` |
| `2025-12-19` | `DIVIDEND_GROSS` | `1.99336803` |

Expected additional results:

```yaml
dividend_net_nonempty_rows: 0
split_numerator_nonempty_rows: 0
split_denominator_nonempty_rows: 0
listing:
  ticker: SPY
  exchange: NYSE_ARCA
  cusip: 78462F103
  isin: US78462F1030
  listing_date: 1993-01-22
```

The new export cannot create its own expected truth. Each compared field must be prospectively labeled exactly one of:

- `INDEPENDENT_ISSUER_COMPARISON`;
- `LEGACY_TRADINGVIEW_VINTAGE_CONSISTENCY_ONLY`; or
- `NOT_COMPARABLE`.

Amounts are parsed as base-10 decimal text; binary floating point is prohibited. Successor-versus-historical-TradingView amounts require exact decimal equality after representational leading/trailing-zero normalization only. Issuer amount comparison uses only a predeclared, directly comparable basis and published precision. If the issuer basis is not directly comparable, amount status is `NOT_COMPARABLE`; issuer corroboration is limited to ex-date, event existence, instrument, and listing. Same-vendor agreement must not be reported as independently validated amount truth.

## 5. Frozen acquisition contract and pre-observation commitment

### 5.1 Source identity

```yaml
lineage: NME001-TVCA-SUCCESSOR-01
standard_symbol: AMEX:SPY
instrument: SPY
listing: NYSE_ARCA
interval: 5m
candle_type: ordinary
chart_session: RTH
metrology_session: RTH_0930_1600
timezone: America/New_York
dividend_adjustment: OFF
permitted_session_window: EXACT_OPENED_2025_DEVELOPMENT_LATTICE_ONLY
value_capable_attempts_authorized_by_this_draft: 0
future_plan_maximum_attempt_budget: 1
future_attempt_id: NME001-TVCA-S01-LIVE-ATTEMPT-01
developer_as_acquirer: PROHIBITED
```

The historical observed export label `BATS:SPY` and feed `NYSE Arca by Cboe One` are expectations, not assumed facts. The actual label, feed, chart configuration, and applied source identity must populate predeclared closed slots. Ambiguity or drift is `HOLD`.

### 5.2 Frozen Pine carrier

The carrier remains UTF-8/LF, 892 bytes, SHA-256 `577eaaee77880e043558f86fa1baef3e8465c131225b851dc0363d2671209645`:

```pine
//@version=6
indicator("NME001 TVCA SUCCESSOR 01", overlay = false, dynamic_requests = false)
float dividendGross = request.dividends("AMEX:SPY", dividends.gross, gaps = barmerge.gaps_on, lookahead = barmerge.lookahead_off, ignore_invalid_symbol = false)
float dividendNet = request.dividends("AMEX:SPY", dividends.net, gaps = barmerge.gaps_on, lookahead = barmerge.lookahead_off, ignore_invalid_symbol = false)
float splitNumerator = request.splits("AMEX:SPY", splits.numerator, gaps = barmerge.gaps_on, lookahead = barmerge.lookahead_off, ignore_invalid_symbol = false)
float splitDenominator = request.splits("AMEX:SPY", splits.denominator, gaps = barmerge.gaps_on, lookahead = barmerge.lookahead_off, ignore_invalid_symbol = false)
plot(dividendGross, "dividend_gross")
plot(dividendNet, "dividend_net")
plot(splitNumerator, "split_numerator")
plot(splitDenominator, "split_denominator")
```

The carrier may not change inside REV-02. A compile failure or required edit stops as `TVCA_S01_PINE_CARRIER_CHANGE_REQUIRED / HOLD` and would require a new prospective revision, hash, commitment, and approvals.

A syntax-only compile is outside the sole live attempt only if a demonstrably data-free compiler mode and receipt are prospectively bound. Otherwise compilation is value-capable and occurs inside the attempt.

### 5.3 Canonical pre-observation commitment

Before the first operation capable of evaluating the carrier against chart data or materializing a market-derived value, the licensed manifest owner must preserve `NME001_TVCA_S01_PRE_OBSERVATION_COMMITMENT_01.json` under a canonical UTF-8 JSON profile. Its identity, bytes, SHA-256, UTC timestamp, owner, and durable version must receive an independent-QA documentary acceptance receipt. QA acceptance establishes eligibility only; a later hash-specific Origin acquisition order is still required.

The commitment must bind by value or exact referenced digest:

1. accepted REV-02 and source-only checkpoint identities;
2. exact 2025 lattice bytes/count/first/last/hash;
3. issuer/listing evidence and field-level comparison status;
4. decimal and canonicalization rules;
5. Pine bytes/hash and compile classification;
6. projector, validator, scanner, profiles, synthetic corpora, expected results, and invocations;
7. expected symbol/feed/chart/export/timeframe/session/timezone/adjustment/window configuration;
8. actor assignments;
9. the one attempt identity and closed ordered nonbranching action script; and
10. typed closed slots for later compile, observed configuration, attempt outcome, raw capture, projections, validation, capture receipt, post-capture identity manifest, scan manifest, custody-confined QA instantiation-acceptance receipt, scan receipts, final composite manifest, promotion packet, and external terminal packet-scan receipt identities.

Each slot must declare type, cardinality, population source, responsible actor, canonicalization, and whether terminal `null` is allowed. Before observation its value is `UNPOPULATED_AT_PRECOMMIT`; it is not a wildcard. No field may be added, removed, retyped, reinterpreted, or populated from an uncommitted source after observation.

### 5.4 Sole live attempt and capture chain

If later authorized, the attempt begins with the first action capable of evaluating the carrier against chart data or materializing or revealing a market-derived value. It includes value-capable compile, preview, add-to-chart, evaluation, refresh, export initiation, cancellation, partial/zero-byte output, platform error, and mechanical failure. These are steps within one attempt only when they follow the exact precommitted order; none permits branching or repetition.

Every terminal outcome consumes the sole attempt:

```yaml
success: TVCA_S01_LIVE_ATTEMPT_COMPLETED_CAPTURED
cancelled: TVCA_S01_LIVE_ATTEMPT_CONSUMED_CANCELLED / HOLD
partial_or_zero_byte: TVCA_S01_LIVE_ATTEMPT_CONSUMED_PARTIAL / HOLD
platform_or_compile_error: TVCA_S01_LIVE_ATTEMPT_CONSUMED_PLATFORM_ERROR / HOLD
mechanical_failure: TVCA_S01_LIVE_ATTEMPT_CONSUMED_MECHANICAL_FAILURE / HOLD
configuration_or_identity_mismatch: TVCA_S01_LIVE_ATTEMPT_CONSUMED_IDENTITY_MISMATCH / HOLD
```

A second value-capable action after failure is unauthorized. Any future second attempt requires a new prospective plan/attempt identity, pre-observation commitment, Product Owner ratification, independent QA acceptance, and hash-specific Origin order. No observation from the consumed attempt may alter the carrier, oracle, window, lattice, schema, canonicalization, precision, acceptance criteria, scanner, or validator.

The capture receipt must reference the commitment hash and bind the actually applied Pine/compile receipt, observed configuration, ordered actions/timestamps, operator/custody environment, terminal outcome, and immediate identity/size/hash of every retained raw/partial/error artifact. The staged immutable chain is:

`QA-accepted pre-observation commitment -> capture receipt -> raw/projection identities -> post-capture identity manifest -> deterministic scan manifest -> custody-confined QA instantiation acceptance -> output-validation and scan receipts -> final composite manifest -> composite-manifest scan -> exact promotion packet -> external terminal packet-scan receipt -> controlled promotion crossing`.

Later artifacts cannot revise earlier objects.

## 6. Raw custody, projections, validation, and leakage controls

### 6.1 Actors and three projections

Developer is a raw-blind implementer. Licensed custody roles are separately recorded for manifest ownership, capture, projection, actual-output validation, and raw-side scanning. When the same custody principal performs projection and validation, the evidence must be labeled `CUSTODIAN_SELF_VERIFICATION + INDEPENDENT_QA_DOCUMENTARY_REVIEW`; it may be called independent raw verification only if later evidence proves a separately controlled licensed verifier.

The Custodian retains all raw sources. No raw TradingView CSV is mounted for Developer. One frozen deterministic projector emits only:

| Projection | Ordered columns |
| --- | --- |
| `NME001_TVCA_S01_UNTOUCHED_2025_TIME_PROJECTION.csv` | `time` |
| `NME001_TVCA_S01_SPLIT_2025_METADATA_PROJECTION.csv` | `time`, `split_numerator`, `split_denominator` |
| `NME001_TVCA_S01_CORPORATE_2025_METADATA_PROJECTION.csv` | `time`, `dividend_gross`, `dividend_net`, `split_numerator`, `split_denominator` |

For pre-existing full-range inputs, the projector may parse `time` inside raw custody solely to exclude non-2025 rows and may read only same-named permitted metadata cells for authorized 2025 rows. The new successor export must itself be bounded to the exact committed 2025 window; if not, stop `TVCA_S01_AUTHORIZED_WINDOW_EXPORT_UNAVAILABLE / HOLD`.

Developer may receive only projections and fixed-schema sanitized records after every applicable validation and pre-release scan passes. No raw price/volume field or 2026 TradingView row/value may cross raw custody.

### 6.2 Actual-output release validator

Before any actual projection or associated releasable record leaves raw custody, a separately hash-bound validator that does not invoke the projector or trust its self-report must read the raw source and output independently and issue a projection-bound receipt.

For every projection it must verify:

- exact identity, size, hash, row count, and profile;
- exact ordered header and canonical serialization;
- unique timestamps in exact ordered equality with the authorized 2025 lattice;
- no 2026 output;
- exact equality of every emitted cell to the canonical same-named permitted raw cell at the same timestamp; and
- an exhaustively enumerated release surface containing no raw excerpt, rejected row, prohibited column, non-profile or extra source-cell value outside the exact validated projection field/location, stack trace, debug dump, or unvalidated transformation output.

Receipts contain only fixed status/reason tokens and identity/count/hash metadata; they do not reproduce mismatched values. Release requires both:

```yaml
actual_output_validation: PASS
applicable_raw_custody_release_scan: PASS
```

Positive/negative synthetic qualification must cover wrong schema/order, extra columns, lattice defects, 2026 output, wrong same-named source values, prohibited-value substitution into an allowed column, formatting drift, diagnostic sentinel leakage, and interrupted comparison. A second projector or formal whole-program noninterference proof is not required.

### 6.3 Scanner instantiation and qualification

Before acquisition, freeze scanner source/dependencies/hash, invocation, deterministic result serialization, every transform and parameter, fragment thresholds/boundaries, collision rules, recursive archive coverage and bounds, intentional-identity-string rules, closed identity slots, and known-positive/known-negative/boundary/corruption qualification corpora with expected results. Pre-acquisition QA may accept only this scanner schema, rules, qualifications, and typed population contract; it cannot accept unknowable post-capture identities or receipts.

After capture, the manifest owner must create immutable `NME001_TVCA_S01_POSTCAPTURE_IDENTITY_MANIFEST_01.json` inside raw custody. It binds the actual capture receipt, raw/partial/error artifacts, projections, observed configuration, and tool identities, but contains no scan receipt and does not claim scan acceptance. Under the precommitted deterministic population rule, the owner must then populate `NME001_TVCA_S01_LEAKAGE_SCAN_MANIFEST_01.json` solely from the accepted pre-observation commitment and this post-capture identity manifest. Runtime identity selection is prohibited. Before any non-raw-custody release, a separately identified documentary QA reviewer operating read-only inside the authorized custody boundary must accept or reject that exact instantiated manifest and issue a fixed-schema, custody-retained receipt. This custody-confined review exposes no artifact outside custody and grants no lane or operational authority.

The actual-output validator must run against each projection and each applicable projection-associated fixed-schema release record for which its frozen profile defines decidable predicates. Separately, all applicable scanners must run against every proposed outbound artifact, including the post-capture identity manifest and the custody-confined QA receipt. Only after the instantiated scan manifest is QA-accepted and those validation/scan results are immutable may the final composite manifest be assembled and scanned under the frozen contracts. Only after that scan passes may the exact sanitized promotion packet be assembled and scanned, followed by creation of its external terminal packet-scan receipt. No byte may cross raw custody before these conditions are met. A hash-specific promotion-review order may then release only that exact validation-and-scan-passed packet plus receipt for documentary promotion QA. No lane execution, further handoff, or other release may occur unless that promotion review returns `PASS` and a later exact order independently authorizes the next transition.

Qualification must cover every transform, fragment thresholds, intentional strings, authorized metadata versus prohibited fragments, renamed/nested archive members, collision handling, and corrupted/encrypted/unsupported/unreadable/truncated/over-bound/incomplete inputs. Any uncertainty or incomplete scan is `HOLD`.

Every byte-bearing post-acquisition artifact proposed to cross raw custody—including projections, sanitized logs/errors, capture/custody/validation/transformation records, manifests, promotion packets, QA handoffs, JUnits, ledgers, binaries, packages, archive members, and the final return—must pass its applicable scan before release. Internal transients need not be individually scanned if they never leave custody; if proposed for release, they enter scope.

Developer separately scans every Developer-controlled release against projection bytes and identities available to Developer and may not claim raw-byte comparison. Custodian separately scans the immutable final return against raw bytes/identities available inside custody and externally binds the return and both scan receipts. For the unavailable historical fixture, only registered filename/size/hash/encoded-identity/known-metadata scans are possible; fragment-level raw-byte scanning remains `NOT_RUN_BYTES_UNAVAILABLE`.

### 6.4 Staged manifests and terminal receipt

After all pre-composite validation and scans pass, the immutable final composite manifest must reference the pre-observation commitment and post-capture identity manifest and bind:

- all three Custodian-held raw identities;
- all three projection identities;
- projector, validator, scanner, profiles, invocations, qualification, transformation, and scan records;
- lattice and reference-matrix identities;
- attempt, capture, and observed configuration;
- output-validation and custody-scan receipts;
- this plan and every later applicable Origin order; and
- each custody transfer and independently substantiated—or honestly relabeled—repeat verification.

The final composite manifest itself must then pass the applicable frozen scan. The Custodian must assemble and scan the exact sanitized promotion packet, then create an external fixed-schema terminal packet-scan receipt binding the final composite-manifest identity/hash, its scan receipt, the promotion-packet identity/hash, the packet-scan result, and the frozen scanner/manifest identities. To avoid self-reference, that terminal receipt does not scan or hash itself and is not a member of the packet whose hash it binds; its own durable identity and hash must be externally bound before the promotion-review crossing.

No source edit is permitted to insert observed hashes; the pre-frozen external schemas and typed slots own later population. The lifecycle is acyclic and mandatory:

1. accepted pre-observation commitment with typed closed slots;
2. immutable post-capture identity manifest;
3. deterministic scan-manifest population from only items 1 and 2;
4. custody-confined documentary QA acceptance of the exact instantiated scan manifest, with no custody crossing;
5. projection-scoped actual-output validation and applicable scans of every proposed outbound artifact, including items 2 and 4;
6. immutable final composite manifest binding items 1–5;
7. scan of the final composite manifest;
8. exact sanitized promotion-packet assembly and scan;
9. external terminal packet-scan receipt; and
10. hash-specific promotion-review order permitting only that packet and receipt to cross for documentary QA.

## 7. Source-only implementation, test provenance, and coverage

### 7.1 Permitted future source scope

Only after independent QA passes REV-02, Product Owner later ratifies the passed plan for bounded progression, and a hash-specific Origin source order exists may Developer begin from:

```yaml
library_file_id: libfile_e716d00202688191a1ac59c2343e4edf
sha256: 8cb8151a9ef619db96d5f9ed4d8c6ba01f635b309a0224634432b523d952ffbd
```

With every licensed payload absent, Developer may implement only:

- the permanent legacy-fixture tombstone and exact two-plane historical registry;
- the separately versioned TVCA-S01 contract and external manifest schemas;
- the deterministic three-profile projector;
- the separately identified actual-output validator;
- the deterministic leakage scanner and qualification corpora;
- no-fallback lane selectors;
- the canonical 61-row licensed-behavior crosswalk;
- the 922-baseline-node reconciliation;
- synthetic, hermetic, successor-licensed, custody/tamper, and leakage controls; and
- documentation necessary to reconcile these changes.

New bytes must never occupy, alias, symlink to, or auto-resolve through the legacy filename or registry slot.

### 7.2 Source-only checkpoint

Before licensed timestamp access, public-oracle acquisition, Pine compilation, TradingView interaction, or market-row acquisition, preserve:

- complete source and unified diff from the accepted baseline;
- full manifest and SHA-256 list;
- dependency/environment identity;
- exact lane selectors, collection serialization, ordered inventories, counts, and digests;
- projector/validator/scanner sources and hashes, profiles, corpora, expected results, and invocations;
- the closed-slot manifest and scanner population schemas;
- the 61-row crosswalk and 922-baseline reconciliation;
- the canonical six-date rule and method for deriving the future ordered eligibility/no-reachback result;
- proof that scientific models, inputs, features, transformations, labels, cohorts, metrics, advancement criteria, final controls, and exclusion semantics are unchanged; and
- a scope reconciliation showing every change is necessary for TVCA-S01.

Developer collects once, freezes the exact successor inventories before any execution, saves the checkpoint durably, and stops. QA acceptance of the checkpoint grants no operational authority.

### 7.3 Coverage taxonomy

Each of the 61 historical licensed behaviors receives exactly one pre-execution disposition:

1. `REEXECUTED_WITH_2025_LICENSED_EVIDENCE`;
2. `HERMETIC_REEXECUTED`;
3. `SYNTHETIC_SURROGATE_ONLY`; or
4. `LEGACY_ONLY_NOT_REEXECUTABLE_WITH_AUTHORIZED_WINDOW`.

Licensed reexecution requires every field and temporal dependency for the permitted successor claim to exist in the authorized projections. Hermetic reexecution supports only its stated nonlicensed claim. A synthetic surrogate supports only the analogous guard it actually exercises. Legacy-only is mandatory for any unavailable exact-byte, raw-file schema/format, OHLCV, full-range, or unauthorized-2026 dependency. Projection evidence, synthetic cases, external scans, matching node names, or later PASS cannot upgrade a row.

The canonical machine-readable crosswalk must contain exactly 61 unique rows and bind at least:

| Required field | Rule |
| --- | --- |
| Parent identity and claim | Exact ordinal `1..61`, node ID, stable claim ID/text |
| Dependencies | Required fields, exact-byte dependency, schema/format dependency, temporal range, fixture/profile identities |
| Successor mapping | Node/lane or `NONE`; source-semantics class |
| Frozen classification | Exactly one four-class disposition, rationale, claim delta |
| Claim boundary | Exact permitted successor claim and prohibited claims |
| Provenance | Baseline and complete diff/manifest bindings |
| Result slots | Typed `UNPOPULATED`/`NOT_RUN` slots populated only later |

Later results cannot change disposition, erase a claim delta, enlarge a permitted claim, or turn surrogate/legacy-only evidence into reexecution. Aggregate reporting shows four separate counts summing to 61, with zero unclassified/duplicate rows; it must not report “61 verified,” “full licensed coverage,” parent equivalence, or a blended PASS.

### 7.4 Historical 922 baseline reconciliation

The 922-node hermetic inventory is a historical baseline, not a promised successor count. Every baseline node must be reconciled exactly once as `UNCHANGED_INHERITED`, `CHANGED_SUCCESSOR_CASE`, or `NOT_COLLECTED_IN_SUCCESSOR`; every new case is `NEW_SUCCESSOR_CASE`.

`UNCHANGED_INHERITED` requires unchanged body, resolved parameters/IDs, markers, fixtures, assertions, expected values/exceptions, expected behavior, and relevant fixture-contract dependencies against the hash-bound baseline. The accepted baseline plus complete diff/manifest must make the decision reproducible. A same-name changed node is excluded from the unchanged count and disclosed as changed. A separate per-case cryptographic fingerprint is not required.

The frozen reconciliation reports `baseline_nodes`, `unchanged_inherited`, `changed_same_name_or_semantics`, `not_collected_in_successor`, `new_successor`, and `successor_total` and must balance exactly.

### 7.5 Prospective lane identities

- `NME001_SEO01_TVCA_S01_HERMETIC`
- `NME001_SEO01_TVCA_S01_2025_LICENSED_CORROBORATION`
- `NME001_SEO01_SCIENTIFIC_DEVELOPMENT_KIBOT_ONLY`

No successor count or digest is prescribed. The result must not be called or blended with the historical 922/983 plane even if a count or digest coincides.

## 8. Non-self-executing authority and prospective sequence

This plan is non-self-executing. Product Owner approval to submit for review authorizes review only. QA `PASS`, checkpoint acceptance, precommit acceptance, promotion-packet acceptance, or any technical PASS establishes eligibility at its named documentary gate only; none is operational authority. Each transition requires a later hash-specific Origin order naming actors, inputs/actions, prerequisite artifacts, and stop boundary. An unlisted action is prohibited. One future order may cover adjacent rows only if it expressly binds each row. No row authorizes historical-final access.

| Transition | Required future order | Actor | Prerequisite accepted artifacts | Maximum action and stop |
| --- | --- | --- | --- | --- |
| Source implementation, collection, qualification | `NME001-TVCA-S01-SOURCE-ORDER-[HASH]` | Raw-blind Developer | Product-Owner-ratified, independent-QA-`PASS` REV-02; accepted DWO-05 frozen foundation; exact hash-specific source order | Implement only accepted scope; collect/freeze inventories; run only named hermetic/synthetic tool qualifications; stop at immutable checkpoint. No licensed, TradingView, Kibot, or final access. |
| Licensed preflight and precommit | `NME001-TVCA-S01-LICENSED-PREFLIGHT-ORDER-[HASH]` | Named licensed Custodian | Accepted source checkpoint and tool-qualification evidence; exact hash-specific licensed-preflight order | Derive lattice/reference evidence and freeze precommit only; no value-capable TradingView action, capture, release, execution, or final access. Stop at QA-reviewed preflight. |
| One live capture and custody-bound transformation | `NME001-TVCA-S01-ACQUISITION-ORDER-[HASH]` | Named Lab operator, Custodian, and custody-confined documentary QA | Accepted pre-observation commitment and QA receipt; accepted licensed-preflight return; frozen attempt, Pine, tool, profile, validator, and scanner identities; exact hash-specific acquisition order | Perform sole committed attempt; retain raw/partial/error artifacts; create projections and manifests; obtain custody-confined QA acceptance of scanner instantiation; validate and scan sanitized promotion artifacts. No retry or custody crossing. Stop at sealed validation-and-scan-passed custody-bound packet and external terminal receipt. |
| Sanitized promotion handoff and review | `NME001-TVCA-S01-PROMOTION-REVIEW-ORDER-[HASH]` | Custodian and documentary promotion QA | Custody-confined QA-accepted instantiated scan manifest and receipt; exact validation-and-scan-passed sanitized promotion packet; externally bound terminal packet-scan receipt; exact hash-specific promotion-review order | Release only that exact packet and receipt across custody for documentary promotion QA; QA reviews receipts/evidence without claiming raw reproduction. Stop at `PASS`/`HOLD`/`REJECT` promotion return. |
| Successor licensed and separate Kibot scientific execution | `NME-001-SEO-01-TVCA-S01-EXECUTION-01-[HASH]` | Licensed-test executor and separately identified Kibot-only scientific executor | Accepted promotion-QA return with `PASS`; accepted source checkpoint and precommit; populated post-capture, scan, and final composite manifests; frozen inventories and lane-specific mounts; exact hash-specific execution order | Run exact frozen lanes in order with lane-specific mounts. TVCA failure holds; PASS has no scientific vote. Stop after immutable returns. No final access. This order cannot be issued and execution cannot proceed before promotion-packet acceptance. |
| Final scans and bounded technical release | `NME001-TVCA-S01-RELEASE-ORDER-[HASH]` | Custodian, Developer scan operator, documentary QA | Immutable execution returns; qualified frozen scanners; populated scan manifests; all prior validation, custody, scan, and promotion receipts; exact hash-specific release order | Scan every releasable artifact under frozen contracts; release only exact allowlisted evidence. Stop at Origin review. No authority elevation. |

If later ordered, execution proceeds from one clean checkpoint rematerialization:

0. Verify checkpoint, environment, precommit/post-capture/scan/final-composite manifests, accepted promotion return, lane-specific mount allowlists, and every permitted artifact identity before collection or execution; prove prohibited artifacts absent.
1. Run the exact frozen successor hermetic inventory with all licensed payloads absent. Report the 922-baseline reconciliation separately.
2. Run 2025 licensed corroboration with only the three accepted metadata projections mounted; no raw TradingView file or Kibot payload may be present. Report each crosswalk row only under its frozen class and claim.
3. Only after the one-way provenance hold is cleared, run scientific development with every TradingView raw/projection artifact absent and only the accepted Kibot development input mounted.
4. Freeze immutable returns and complete Developer-side and Custodian-side scans before any bounded release.

Any runtime inventory, source, crosswalk, reconciliation, mount, custody, scan, or authority drift terminates the specific authorization.

## 9. Independent QA questions for REV-02

Independent QA must return `PASS`, `HOLD`, or `REJECT` on each question:

1. Does REV-02 bind the literal historical DWO-05 execution/evidence states without re-adjudication, and are all successor identities free of `RECOVERY`, `RERUN`, and `983` aliases?
2. Does it define a decidable actor/field/action boundary permitting Custodian-only filtering of pre-existing 2026 timestamps while prohibiting new successor 2026 acquisition and all 2026/raw-OHLCV downstream transfer?
3. Does it require a canonical QA-accepted pre-observation commitment to freeze Pine, lattice, reference/decimal bases, configuration, tools, roles, and the sole attempt before the first value-capable interaction, with only typed closed slots populated later?
4. Does it preserve the six-session exclusion/no-reachback rule unchanged and define TVCA-S01 as a one-way provenance stop whose failure may hold progression but whose PASS has zero scientific evidentiary promotion?
5. Does it require separately controlled actual-output validation and Custodian scanning before every raw-custody crossing, including exact profile/lattice/source-cell equality, no 2026 output, and no unsanitized content?
6. Does the staged precommit, post-capture identity manifest, deterministic scan manifest, custody-confined QA instantiation acceptance, projection-scoped validation, outbound scans, final composite manifest, composite scan, and external terminal packet-scan receipt lifecycle bind later identities without circularity, post-observation source edits, runtime identity selection, or pre-acceptance custody crossing?
7. Does the 61-row crosswalk use four mutually exclusive evidence classes, dependency-based legacy-only override, frozen result slots, and bounded claims without implying full-range or historical-parent equivalence?
8. Does the 922-baseline reconciliation enforce the `UNCHANGED_INHERITED` rule, exclude changed same-name nodes, and keep every historical identity/inventory/digest separate from TVCA-S01?
9. Are the sole-attempt/no-retry rule, scanner qualification and pre-release timing, lane gates, non-self-executing transitions, final-holdout boundary, and all stop conditions jointly fail-closed?

Plan review does not require unavailable bytes, parent-successor output equivalence, a second projector, whole-program noninterference proof, proof that raw-custody infrastructure never buffers a pre-existing 2026 byte, scans of internal objects never released, or per-case hashes when baseline plus complete diff makes classification reproducible.

## 10. Consolidated stop conditions

Stop without runtime repair, retry, reclassification, tolerance change, substitution, aliasing, claim enlargement, or execution if any of the following occurs:

- the accepted REV-02, source checkpoint, pre-observation commitment, or later Origin order identity differs;
- a required future action lacks its exact hash-specific Origin order;
- a commitment field/slot is open, unknown, mutated, uncommitted, or populated from the wrong source;
- the chronology from accepted commitment to first value-capable action is not proven;
- the applied Pine, chart/export configuration, symbol, feed, interval, session, timezone, adjustment state, or window is ambiguous or mismatched;
- the first value-capable attempt fails, cancels, partially completes, produces zero bytes, errors, or deviates from the nonbranching script;
- a second live attempt, any value-capable action outside the one precommitted ordered sequence, or any export initiation beyond the single precommitted export step is attempted;
- the exact 2025 successor window cannot be enforced or the new capture contains a 2026 row/value;
- a 2026 TradingView row/value or raw OHLCV reaches a projection, Developer, ordinary QA, or the scientific executor;
- actual-output validation is absent, incomplete, errored, schema/lattice/serialization mismatched, or finds a same-cell mismatch;
- a releasable artifact contains an unsanitized diagnostic, raw excerpt, extra field, or unvalidated transformation surface;
- scanner contract/qualification/instantiation is absent, incomplete, drifted, or unaccepted;
- any applicable scan is positive, incomplete, errored, or omitted before custody crossing;
- the composite manifest, capture chain, raw/projection identity, custody receipt, or mount allowlist differs;
- the 61-row crosswalk is incomplete, duplicated, unbalanced, reclassified, or assigns a forbidden evidence class;
- a raw/schema/OHLCV/full-range/unauthorized-2026 dependency is not legacy-only;
- a result changes a disposition/claim or a report blends the four evidence classes;
- the 922 reconciliation is incomplete/unbalanced, changes after checkpoint, or counts a changed same-name node as unchanged;
- runtime collection differs from the frozen successor inventory or lane selector;
- any successor artifact uses `RECOVERY`, `RERUN`, or `983` as an alias or collides with a historical identity;
- the six-date rule, development eligibility/no-reachback result, scientific input, model, feature, transformation, label, cohort, metric, advancement criterion, final control, or interpretation changes;
- a TVCA-S01 PASS is used to validate or promote a scientific result;
- the historical final opens, may have been exposed, or its record state becomes uncertain; or
- authority beyond the exact named transition would be required.

## 11. Current authority state

```yaml
legacy_fixture_search: CLOSED_UNRECOVERABLE
historical_dwo05_checkpoint_licensed_record: PASS_983_OF_983_AUTHORITY_NONE
origin_clean_resumption_licensed_lane: NOT_RUN_NOT_AUTHORIZED
dwo05_release_candidate: NOT_CREATED
historical_recovery_epoch04_disposition: CLOSED_AT_FIXTURE_CUSTODY_PREFLIGHT_NO_TEST_COLLECTION_OR_EXECUTION
successor_plan_rev01: INDEPENDENT_QA_HOLD
successor_plan_rev02: DRAFT_PENDING_PRODUCT_OWNER_APPROVAL_FOR_INDEPENDENT_QA_REVIEW
successor_execution_identity: NME-001-SEO-01-TVCA-S01-EXECUTION-01
successor_execution_order: NOT_ISSUED
developer_tvca_s01_source_work: HOLD
source_or_test_collection: HOLD
synthetic_qualification_execution: HOLD
licensed_fixture_or_timestamp_access: NOT_AUTHORIZED
public_oracle_acquisition: NOT_AUTHORIZED
pine_compile_or_live_evaluation: NOT_AUTHORIZED
successor_acquisition: NOT_AUTHORIZED
projection_or_rematerialization: NOT_AUTHORIZED
licensed_successor_execution: HOLD
kibot_access: HOLD
scientific_execution: HOLD
scan_or_release_operation: HOLD
historical_final_opening_record: NONE_RECORDED
absence_of_final_open_record_interpretation: NOT_PROOF_OF_NONACCESS
stage_final: HOLD
operational_release: HOLD
formal_evidence_authority: NONE
predictive_authority: NONE
trading_authority: NONE
alerting_authority: NONE
automated_action_authority: NONE
```

## 12. Product Owner decision boundary

Approval of REV-02 will authorize only independent QA review of its exact bytes and SHA-256. It will not authorize source work, collection, qualification, licensed timestamp or oracle access, Pine compilation, TradingView acquisition, projection, scans or custody release, test execution, Kibot access, scientific execution, historical-final access, or operational release.

If independent QA returns `PASS`, the plan becomes eligible for a separate Product Owner ratification and later hash-specific Origin orders. QA acceptance itself never begins work.

## 13. Controlling evidence

- REV-01 plan — `libfile_2ae78bc639c88191a2957459babb26c0`, version 1, SHA-256 `874fc00113ccd0c9da0c14d56753f320806a881deccaaf4bf5d71041ab6d7b6f`
- Formal QA Submission 01 — `libfile_f8906e6296648191a0876926a8b8c8ff`, SHA-256 `ff89bdb12889750dc2a0d77f566700ab966135db630d076843a701a8f19fb2a0`
- QA Adjudication D — `libfile_32f35c6e072881919b4eb9cfb88350b3`, SHA-256 `45f988d335f918bfeefa932d23b7bfdaf8ff976d1bdca809ad637d64df0655c2`
- QA-delta package containing the clean-layer manifest — `libfile_d316dd90c110819182e72682daad07ff`, SHA-256 `f168863f2530c2047c5d7cffc99876c86ed13e0296e3173bc5d6385c1efbe5a3`
- DWO-05 clean-resumption bundle — `libfile_e716d00202688191a1ac59c2343e4edf`, SHA-256 `8cb8151a9ef619db96d5f9ed4d8c6ba01f635b309a0224634432b523d952ffbd`
- Origin clean-resumption acceptance — `libfile_8100a8ab25d88191b1085e05e293ff53`, SHA-256 `08d82c10faa92befdca4e391fd4e04d1399b6d2d78c989516016ad3d63c32f5d`
- Partial TradingView custody receipt — `libfile_5989b22a466481919f850f16d9a9ab55`, SHA-256 `85c7dc033c1491f3f85b94772d641fc20748509fba3c8fc306ab1d100ee00e99`
- TradingView Pine Script v6 reference — <https://www.tradingview.com/pine-script-reference/v6/>
