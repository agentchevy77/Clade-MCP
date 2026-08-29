# NME-001 Independent Verification Annex — DWO-04/DWO-05 Record Review

Date: 2026-08-29
Reviewer role: Project Nexus Origin — independent acceptance review (documentary lane)
Scope: everything verifiable from the submitted record alone. No candidate ZIP
bytes, JUnit files, licensed fixtures, or executable environment were
submitted, so no test execution, sealed reproduction, or archive-member
verification was performed in this lane. Every result below is either a
deterministic recomputation performed by this reviewer or is explicitly marked
unverifiable.

Research status: RESEARCH ONLY — NO FORMAL, PREDICTIVE, TRADING, ALERTING, OR
AUTOMATED-ACTION AUTHORITY. Nothing in this annex creates evidence authority.

## 1. Submitted artifact identity verification

Every submitted artifact whose identity is claimed anywhere in the record was
rehashed by this reviewer (full digests in §7). All sixteen submitted files verify; the two
apparent duplicates are byte-identical copies.

| Submitted artifact | Bytes | SHA-256 (computed) | Claimed where | Match |
|---|---:|---|---|---|
| DWO-04 order (`NME001_ORIGIN_DWO03_ACCEPTANCE_AND_DWO04_ORDER_2026-08-29.md`) | 16,955 | `f5feb728…` | ledger v1.0.1, manifest, receipt, capacity note, DWO-04 verification report, material ledger | PASS |
| Protocol v1.2.1 | 64,173 | `df1b7f3e…` | DWO-04 verification report; v1.2.2 closeout note | PASS |
| Exposure ledger v1.0.1 | 7,035 | `4e190926…` | DWO-04 verification report | PASS |
| Capacity/configuration note v1.2.1 | 5,915 | `383cc720…` | DWO-04 verification report | PASS |
| DWO-04 candidate external manifest | 2,088 | `cf000cda…` | DWO-04 receipt; DWO-05 order §2 | PASS |
| DWO-04 candidate external receipt | 2,100 | `54b9a121…` | DWO-05 order §2 | PASS |
| DWO-03→DWO-04 candidate patch | 577,192 | `60f9a84b…` | DWO-05 order §2 | PASS |
| DWO-04→paused-DWO-05 patch | 505,877 | `af1e0870…` | DWO-05 SITREP §2/§5/§6; checkpoint SHA256SUMS | PASS |
| DWO-05 pause-checkpoint SHA256SUMS | 458 | `ec1823db…` | DWO-05 SITREP §6 | PASS |
| DWO-05 pause SITREP (both copies) | 11,394 | `f8ba97bc…` | (self; two byte-identical copies submitted) | PASS |
| DWO-04 verification report (both copies) | 7,186 | `d8beaa12…` | reconstructed from DWO-03→DWO-04 patch (see §2) | PASS |
| DWO-04 reproduction contract | 7,830 | `af79e975…` | reconstructed from DWO-03→DWO-04 patch | PASS |
| DWO-04 material-attempt ledger | 4,252 | `b508254a…` | reconstructed from DWO-03→DWO-04 patch | PASS |
| Kibot pre-contact assessment | 11,027 | `30c3318e…` | no external claim in the submitted record | N/A (recorded) |

## 2. Patch-embedded document reconstruction

Both submitted patches embed governance documents as new files. This reviewer
reconstructed every new file from the raw unified-diff hunks and rehashed the
result. Every reconstruction that has an independently claimed identity
matches exactly:

From the DWO-03→DWO-04 patch:

| Reconstructed file | Bytes | Claimed identity | Match |
|---|---:|---|---|
| `config/frozen_config_v1_2_0.json` | 4,572 | `b323f10f…` (preserved config v1.2.0) | PASS |
| `governance/NEXUS_MARKET_EXPERIMENT_001_v1_2_0_TO_v1_2_1.diff` | 25,519 | `96862517…` | PASS |
| `governance/NEXUS_MARKET_EXPERIMENT_001_v1_2_1.md` | 64,173 | `df1b7f3e…` | PASS |
| `governance/NME001_PRIOR_EXPOSURE_LEDGER_v1_0_1.json` | 7,035 | `4e190926…` | PASS |
| capacity note, DWO-04 order, verification report, reproduction contract, material ledger | — | as in §1 | PASS |

From the DWO-04→paused-DWO-05 patch:

| Reconstructed file | Bytes | Claimed identity | Match |
|---|---:|---|---|
| `governance/orders/NME001_ORIGIN_DWO04_ACCEPTANCE_AND_DWO05_ORDER_2026-08-29.md` | 21,766 | `38de0b5f…` (exact DWO-05 order, SITREP §2) | PASS |
| `config/frozen_config_v1_2_1.json` | 4,618 | `a0a0b8a6…` (active config v1.2.1, preserved byte-for-byte) | PASS |
| `governance/NEXUS_MARKET_EXPERIMENT_001_v1_2_2.md` | 69,081 | `3e2ba3ef…` (paused-worktree protocol v1.2.2, closeout note) | PASS |
| `governance/NME001_V1_2_2_INFRASTRUCTURE_CLOSEOUT_NOTE_2026-08-29.md` | 3,482 | `4e108c1e…` (paused DWO-05 verification report) | PASS |
| `governance/NEXUS_MARKET_EXPERIMENT_001_v1_2_1_TO_v1_2_2.diff` | 27,421 | `8cfae55a…` (paused DWO-05 verification report) | PASS |

The byte-identity of `config/frozen_config_v1_2_1.json` in the DWO-05 tree
with the claimed active v1.2.1 configuration, and of
`config/frozen_config_v1_2_0.json` in the DWO-04 tree with the accepted
DWO-03 configuration, independently confirms the claimed byte-for-byte
preservation across protocol generations.

## 3. Calendar and session-identity reconstruction

This reviewer independently reconstructed the calendar layer with
`exchange_calendars` 4.11.1 (the exact package/version pinned in ledger
v1.0.1), calendar `XNYS`, classifying 390-minute sessions as ordinary. The
canonical serialization (compact JSON ordered ISO-date array plus one terminal
newline) reproduces every claimed identity hash:

| Claim | Claimed value | Reconstructed | Match |
|---|---|---|---|
| Schedule 2025-01-02→2026-08-28, total sessions | 415 | 415 | PASS |
| — ordinary sessions | 412 | 412 | PASS |
| — ordinary-session identity | `eb22307f…` | `eb22307f…` | PASS |
| — scheduled half-days | 2025-07-03, 2025-11-28, 2025-12-24 (210 min) | same three, 210 min | PASS |
| Historical final 2022-06-22→2024-12-31, ordinary sessions | 630 | 630 | PASS |
| — ordered-session identity | `423f3ad6…` | `423f3ad6…` | PASS |
| Ledger range `NME001_PRIOR_TV_DEVELOPMENT_001` (2025-01-02→2026-05-28) | 348 / `aebefc29…` | 348 / match | PASS |
| Ledger range final-boundary (2026-05-29) | 1 / `9520d412…` | 1 / match | PASS |
| Ledger range procedural holdout (2026-06-01→2026-08-27) | 62 / `ffe0e90d…` | 62 / match | PASS |
| Ledger range opened 2026-08-28 | 1 / `f466ad8c…` | 1 / match | PASS |
| Ordinary sessions 1998-01-02→2024-12-31 (protocol calendar) | 6,734 | 6,734 | PASS |
| Nine technical-event sessions are valid XNYS sessions | — | all nine valid | PASS |
| Overlap of 630-session final with every `SCIENTIFICALLY_OPENED`/half-day/boundary-opened session | 0 | 0 | PASS |

Ledger arithmetic also reconciles: 348 + 1 + 62 + 1 = 412 ordinary sessions,
plus 3 scheduled half-days = 415 scheduled sessions.

## 4. Statistical and identity recomputation

| Claim | Claimed value | Recomputed | Match |
|---|---|---|---|
| Nine-session identity hash (compact JSON array + newline over the nine listed dates) | `c7f252dd…` | `c7f252dd…` | PASS (exact) |
| Clopper–Pearson two-sided 95% for 9/84, lower | `0.05017738898650497` | `0.05017738898650…` | PASS (agrees to ~13 significant digits; residual difference is this reviewer's numerical tolerance) |
| Clopper–Pearson two-sided 95% for 9/84, upper | `0.19367005954466723` | `0.19367005954466…` | PASS (same tolerance) |

The estimand relabeling itself (`TECHNICAL_EVENT_SESSION_INCIDENCE`,
conditional iid-binomial sensitivity only, zero gate vote) is consistent with
the DWO-04 order §C and correctly avoids the Bernoulli-origins mislabeling
identified in DWO-03 finding P2/M1-02.

## 5. Not verifiable from the submitted record

The following claims are internally consistent but cannot be independently
verified from the submitted bytes, and this annex asserts nothing about them:

1. The DWO-04 candidate ZIP (`a08a2c9d…`, 1,800,260 bytes), its embedded
   manifest (`da5ce6d9…`, 206,649 bytes), archive-member inventory, and
   sealed reproduction results — the ZIP was not submitted.
2. All test executions: DWO-03 555/614; DWO-04 660/713/773; DWO-05 922/983,
   133 focused, 53 historical; JUnit digests — no JUnit files were submitted.
3. The three licensed TradingView fixtures (sizes/hashes as registered) and
   every licensed-lane result — correctly not submitted; licensed bytes must
   never enter this record.
4. The DWO-05 pause-checkpoint ZIP (`dd02872e…`), its manifest and regroup
   note — only their hashes (verified against the submitted SHA256SUMS file)
   and library IDs were submitted.
5. The DWO-05 output-relation reconciliation artifact (`6938e526…`, 10,524
   bytes) and both final stopped JUnits (`80feb117…`, `cbc075f4…`).
6. The stale on-disk release patch (505,707 bytes, `1e274c16…`) disclosed in
   SITREP §5 — not submitted; the delivered current patch (505,877 bytes,
   `af1e0870…`) verifies.
7. The managed-workspace replay behavior itself — an environmental claim about
   a filesystem this reviewer has no access to. The record's own evidence for
   it is assessed in the decision document, not certified here.

## 6. Review-workflow findings

See the companion decision document
(`governance/orders/NME001_ORIGIN_DWO05_PAUSE_RATIFICATION_AND_RESUMPTION_ORDER_2026-08-29.md`)
for the code-review findings from the ten-dimension review of both patches
(fit/OOD precedence, configuration typing, capacity reconciliation,
distribution safety, adversarial-matrix coverage, protocol v1.2.2 scope,
environmental-diagnosis audit, licensed-data scan, and cross-document
consistency), each adversarially verified before being relied upon.

## 7. Full computed digests of the submitted files

```text
f5feb728d513c9bb827bb436000ac68d56f0fea395fd6593c778a21cafc54cba  NME001_ORIGIN_DWO03_ACCEPTANCE_AND_DWO04_ORDER_2026-08-29.md
38de0b5f369c15c524657ca5052b73d9ce7d9525d7e3c8cfc31d4ea7e503699c  NME001_ORIGIN_DWO04_ACCEPTANCE_AND_DWO05_ORDER_2026-08-29.md (reconstructed)
df1b7f3eec85f8d0e0f6c8f9c2237713a3bf6207987e65195e42ac881e1060cb  NEXUS_MARKET_EXPERIMENT_001_v1_2_1.md
4e190926e0dec2d4304b5962904439e4642c0dfc9ac19afd12d776b5fa8cba86  NME001_PRIOR_EXPOSURE_LEDGER_v1_0_1.json
383cc72067bab86bafeb4fbe9665459cd20364ab48c93f91ae9fceafde9e4e3c  NME001_V1_2_1_CAPACITY_AND_CONFIGURATION_NOTE_2026-08-29.md
30c3318e289fe5630289c153a949f1370e196c89e4fefe6936bbd38c816d2a11  KIBOT_PRECONTACT_ASSESSMENT_2026-08-29.md
d8beaa12036ff073053abad6147550dc2e0ddbdd354b193f0a43d4974372dca2  DWO04_VERIFICATION_REPORT.md
af79e97518eb612e9394945870f8efc3ab66db19903c92a40536db3b6515b821  DWO04_REPRODUCTION.md
b508254ad6b63e47e6a58a8ed09880898009abf856d04da2b668e475168961d0  material_attempt_ledger_dwo04.md
cf000cdadfbfd14b787483907259558fe0299e041eb3ce97185bb2efad3cc2a6  NME-001-DWO-04_CANDIDATE_MANIFEST.json
54b9a12150c85f6ec3c3a4a3dfc33e7e6b7a4ef280f38a440be8ab41ba1579ea  NME-001-DWO-04_CANDIDATE_RECEIPT.json
60f9a84b7f541087934a7c62da507499f4ea68ab59a0c799cadf9551f55d6e70  NME-001-DWO-03_TO_DWO-04.patch
f8ba97bc80a89e67068e84ed55b20bf110c16cf41ff11945de13966027dd89fe  NME001_DWO05_PAUSE_PRESERVATION_SITREP_FOR_ORIGIN_2026-08-29.md
af1e0870651444197fdbe03e03438dbc88eb8728a40401a1451acc5af2fe1d9f  NME-001-DWO-04_TO_PAUSED_DWO-05.patch
ec1823db32104b299e562aad123b229bbe299463658395d07118a23e5ee6674f  NME-001-DWO-05_PAUSE_CHECKPOINT_SHA256SUMS_2026-08-29.txt
```

## 8. Authority statement

```yaml
verification_lane: DOCUMENTARY_AND_RECOMPUTATION_ONLY
evidence_authority: NONE
formal_evidence_authority: NONE
predictive_authority: NONE
trading_authority: NONE
alerting_authority: NONE
automated_action_authority: NONE
```
