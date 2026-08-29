# NME-001 v1.2.1 Capacity and Configuration Correction Note

Date: 2026-08-29  
Work order: NME-001-DWO-04  
Order SHA-256: `f5feb728d513c9bb827bb436000ac68d56f0fea395fd6593c778a21cafc54cba`  
Protocol: NEXUS-MARKET-EXPERIMENT-001 v1.2.1  
Research status: RESEARCH ONLY — NO FORMAL, PREDICTIVE, TRADING, ALERTING, OR AUTOMATED-ACTION AUTHORITY

## 1. Corrected capacity estimand

The only binary technical-event quantity retained for a Clopper–Pearson
sensitivity is `TECHNICAL_EVENT_SESSION_INCIDENCE`: whether an outer-test
session contains at least one technically evaluable REAL origin.

Origins are not labeled Bernoulli session trials. The opened legacy regression
contains these separate raw facts:

| Quantity | Reconstructed value |
|---|---:|
| Outer-test sessions | 84 |
| `PARTITION_ELIGIBLE_OPPORTUNITY` REAL rows | 168 |
| `EVENT_SEALED` REAL rows | 9 |
| `TECHNICALLY_EVALUABLE` REAL origin rows | 9 |
| Distinct technical-event sessions | 9 |

The nine ordered technical-event session identities are:

```text
2026-02-12
2026-02-17
2026-03-02
2026-03-10
2026-03-31
2026-04-07
2026-04-24
2026-04-27
2026-05-11
```

Their canonical ordered-session SHA-256 is
`c7f252ddbf88eeea8cd83818c30fbac0e0dac20e542d6bf19624098134167784`.
The serialization is the existing NME-001 compact JSON ordered-date array with
one terminal newline.

The raw technically evaluable label counts are:

| Class | Rows | Distinct sessions |
|---|---:|---:|
| `NO_CONTACT` | 1 | 1 |
| `DEFEND_OR_REJECT` | 1 | 1 |
| `BREAK_THROUGH_OR_ACCEPT` | 2 | 2 |
| `UNRESOLVED_OR_AMBIGUOUS` | 5 | 5 |

These technical labels are descriptive attrition facts. They are not
substitutes for fitted or scorable model support.

## 2. Conditional sensitivity only

The method identity is
`CLOPPER_PEARSON_TWO_SIDED_95_CONDITIONAL_IID_BINOMIAL_SENSITIVITY_ONLY`.
Conditional on treating the 84 observed outer-test sessions as iid Bernoulli
trials for this calculation only, the two-sided 95% Clopper–Pearson interval
for 9/84 technical-event sessions is approximately
`[0.05017738898650497, 0.19367005954466723]`.

This is not an unconditional exact coverage statement across serial,
nonstationary market time. It is not a 1998–2024 projection. It cannot clear
data acquisition, interpretation, model promotion, formal evidence, predictive
authority, or any trading action. The active configuration therefore leaves
the obsolete technical-origin and rare-technical-class rate input pairs null.

## 3. Acquisition-relevant output support

Acquisition-relevant quantities are output-reconciled scorable `MODEL_FULL`
row counts and scorable per-class row counts, with distinct-session counts
reported alongside:

| `MODEL_FULL` quantity | Rows | Distinct sessions |
|---|---:|---:|
| Successful REAL `FIT` | 0 | 0 |
| `TECHNICAL_NOT_ISSUED` | 9 | 9 |
| `OOD_ABSTAIN` | 0 | 0 |
| `ISSUED` | 0 | 0 |
| `SCORABLE` total | 0 | 0 |
| Scorable `NO_CONTACT` | 0 | 0 |
| Scorable `DEFEND_OR_REJECT` | 0 | 0 |
| Scorable `BREAK_THROUGH_OR_ACCEPT` | 0 | 0 |
| Scorable `UNRESOLVED_OR_AMBIGUOUS` | 0 | 0 |

The active scorable `MODEL_FULL` observation remains 0/84. Every acquisition
clearance flag is frozen false, even in a hypothetical engineering test whose
descriptive row counts exceed a threshold. The lane remains
`FAIL_CLOSED_EXPLORATORY_ACQUISITION_PROPOSAL`.

## 4. Output-backed verification

The DWO-04 pipeline writes
`machine/capacity_attrition_reconciliation.json` only for a successful run of
the separately authorized, exact legacy licensed-fixture regression. The
artifact is reconstructed from:

- `eligibility_ledger.csv`;
- `events.csv`;
- `predictions.csv`;
- `model_fits.json`; and
- `scored_events.csv`.

The frozen candidate copy is
`artifacts/verification/NME001_DWO04_LICENSED_ATTRITION_RECONCILIATION.json`,
3,567 bytes, SHA-256
`5223227e8e36c9038ac14002287d42146b1f879a2274d81773302d15f021465e`.
The licensed regression asserts its bytes equal both the pipeline-emitted file
and the canonical serialization of a fresh reconstruction.

It verifies the attrition chain rather than reloading the frozen counts. Every
`OOD_ABSTAIN` or `ISSUED` row must join to exactly one successful
same-cohort/fold/model `FIT` record. Pseudo-cohort scored rows remain valid
regression outputs but are excluded before REAL `MODEL_FULL` capacity
reconciliation. Any mismatch fails the licensed pipeline before it can label
the reconciliation `PASS`.

The active pipeline governance surface separately exposes
`capacity_clearance_control`. It names only output-reconciled scorable
`MODEL_FULL`/per-class rows as acquisition gate quantities. It does not project
technical-origin or rare-technical-class counts.

## 5. Configuration typing

The existing `ExperimentConfig` schema is unchanged. Exact runtime-type
validation is centralized for the already-declared JSON/runtime types.
`load_config`, `from_mapping`, direct dataclass construction, and
`validate_config` consistently raise `ContractError` for boolean-for-integer,
integer-for-float, and other wrong-type substitutions. Values are not coerced,
and no configuration validation service or new schema field was added.

## 6. Clearance and authority

```yaml
capacity_estimand: TECHNICAL_EVENT_SESSION_INCIDENCE
capacity_sensitivity_role: CONDITIONAL_IID_BINOMIAL_SENSITIVITY_ONLY
capacity_sensitivity_acquisition_vote: false
acquisition_gate_quantities: SCORABLE_MODEL_FULL_AND_SCORABLE_MODEL_FULL_PER_CLASS_ROWS
clears_development_total: false
clears_development_per_class: false
clears_final_total: false
clears_final_per_class: false
clears_all: false
capacity_status: FAIL_CLOSED_EXPLORATORY_ACQUISITION_PROPOSAL

formal_evidence_authority: NONE
predictive_authority: NONE
trading_authority: NONE
alerting_authority: NONE
automated_action_authority: NONE
real_v1_2_1_development: HOLD
stage_final: HOLD
historical_final_opened: NO
provider_contact_under_dwo04: NONE_AUTHORIZED
```
