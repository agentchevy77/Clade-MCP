# NME-001 Origin DWO-05 Pause Ratification and Resumption Directive

Status: DRAFT — effective when Section 4 (review findings and dispositions)
is recorded from the completed ten-dimension adversarial review
Date: 2026-08-29
Authority: Project Nexus Origin independent review of the DWO-05 pause/preservation submission; Product Owner retains external-contact, account, purchase, data-ingestion, custody-movement, real-data, executor-provisioning, and final-opening authority
Research status: RESEARCH ONLY — NO FORMAL, PREDICTIVE, TRADING, ALERTING, OR AUTOMATED-ACTION AUTHORITY

## 1. Disposition

```yaml
reviewed_submission: NME001_DWO05_PAUSE_PRESERVATION_SITREP_FOR_ORIGIN_2026-08-29.md
submission_sha256: f8ba97bc80a89e67068e84ed55b20bf110c16cf41ff11945de13966027dd89fe
disposition: PAUSE_RATIFIED_PRESERVED_NOT_REJECTED
dwo05_order_status: REMAINS_OPEN_UNCHANGED
dwo05_release_identity_contract: UNCHANGED (candidate 0.3.2, protocol 1.2.2, partition 1.2.0)
foundation_status: DWO04_RETAINED_PENDING_DWO05
dwo06_created: false
architecture_reopened: false
matrix_or_guard_weakening_authorized: false
resumption_mode: ISOLATED_EXECUTOR_REQUIRED
atomic_relocation_procedure: NOT_AUTHORIZED_AT_THIS_TIME
authority_elevation: NONE
```

The DWO-05 pause is ratified. The release guard behaved exactly as designed:
three package attempts failed closed rather than freeze a candidate in an
environment that demonstrably rehydrates deleted licensed-fixture paths, and
no candidate, sidecar, or fixture-bearing distribution survived any attempt.
Pausing before the fourth attempt — instead of weakening the three-condition
matrix or running the untested whole-root relocation procedure — was the
correct fail-closed decision and is what this directive would have ordered.

## 2. Basis of this decision

This directive rests on the documentary record only. What this reviewer
independently verified, and the exact limits of that verification, are
recorded in `review/NME001_ORIGIN_INDEPENDENT_VERIFICATION_ANNEX_2026-08-29.md`:

1. All sixteen submitted files verify against every identity claimed for them
   anywhere in the record, including the exact DWO-05 order (21,766 bytes,
   `38de0b5f…`) reconstructed byte-perfect from the submitted paused-worktree
   patch.
2. The complete calendar layer — 412/415 sessions with the three half-days,
   the 630-session historical final, all four ledger range identities, the
   6,734-session protocol calendar, and the zero-overlap proof — reconstructs
   exactly from the public XNYS calendar under the record's own
   serialization convention.
3. The nine-session identity hash and the 9/84 Clopper–Pearson sensitivity
   recompute exactly.
4. Test executions, the DWO-04 candidate ZIP, the pause-checkpoint ZIP, and
   the licensed lane are internally consistent but not independently
   verifiable from the submission; nothing in this directive treats them as
   independently confirmed.

An adversarially verified ten-dimension code and consistency review of both
submitted patches was performed; its material results are in Section 4.

## 3. Ratification rationale

1. **The environmental diagnosis is the best-supported hypothesis.** The
   bounded residue inventory in attempt 3 captured exactly the three
   registered fixture files at their registered sizes and hashes —
   consistent with stale-path replay of previously present bytes, not with a
   build generating market data. The isolated copied-root ordinary build left
   `data/raw` absent, which exonerates the Hatch source-distribution path.
   The attempt-4 preflight reproduced the replay with no package command
   running at all, and an unrelated deleted freeze-stage tree returned in the
   same replay batch. No code path in the reviewed release/distribution
   modules creates, copies, or restores fixture bytes into `data/raw` during
   the no-raw proof.
2. **The guard's refusal is the system working.** A release contract that
   requires proof that ordinary builds are raw-free, in an environment where
   raw paths reappear asynchronously, must refuse to freeze. Every failure
   was recorded, restored, and left no partial candidate.
3. **The engineering work ordered by DWO-05 is present in the paused
   source.** The Hatch sdist exclusion, the three-condition matrix, the exact
   fit/prediction/scored/comparator relation contract, and the adversarial
   matrix ordered in DWO-05 §B–§E are implemented in the submitted worktree
   patch (Section 4 findings note the review's qualifications). Both stopped
   test lanes are claimed passing at 922/922 and 983/983; those executions
   are not independently verifiable here and will be re-proven on resumption.
4. **Authority discipline held.** No authority field changed anywhere in the
   pause package; the checkpoint carries no licensed content per its recorded
   scan results; the Kibot lane remains `PREPARED_NOT_SENT`; no provider
   contact occurred.

## 4. Review findings and dispositions

Pending: the ten-dimension adversarially verified review of both submitted
patches (fit/OOD precedence, configuration typing, capacity reconciliation,
distribution safety, adversarial-matrix coverage, protocol v1.2.2 scope,
environmental-diagnosis audit, licensed-data scan, cross-document
consistency) is executing. Its findings and their dispositions will be
recorded here before this directive takes effect.

## 5. Resumption directive

Resume DWO-05 release closure only when all of the following hold, in order:

1. **Executor.** The Product Owner provisions an ordinary, isolated
   filesystem/executor with no asynchronous path restoration, snapshotting,
   or workspace replay. The atomic whole-project relocation procedure
   (material-attempt row 19) is NOT authorized at this time: it would run
   inside the same pathological environment whose replay behavior is the
   blocker, and its restore/quarantine `finally` path is itself exposed to
   that behavior. If the Product Owner determines no isolated executor can be
   provisioned, return that determination to Origin with the environment's
   constraints before any relocation run; do not launch it on Developer
   authority.
2. **Materialization.** Materialize the pause checkpoint in the isolated
   executor and hash-verify every member against
   `NME-001-DWO-05_PAUSE_CHECKPOINT_SHA256SUMS_2026-08-29.txt` and the
   checkpoint manifest before any other action.
3. **Fixture custody.** Restore the same three licensed fixtures at their
   registered paths only after the Product Owner explicitly confirms
   fixture custody/movement authority for the new executor. Their use remains
   ephemeral, zero-vote, regression-and-exclusion-proof only. No new data, no
   other sessions, no provider contact.
4. **Stale-artifact hygiene.** Regenerate the canonical DWO-04→DWO-05 patch
   in the isolated executor; the submitted 505,877-byte `af1e0870…` patch is
   the binding paused identity and the stale 505,707-byte on-disk variant is
   superseded and must not be used. Regenerate the forward-written
   `DWO05_VERIFICATION_REPORT.md`, `NEXUS_DEV_RETURN_DWO05.md`, and
   `material_attempt_ledger_dwo05.md` from actual post-resumption results
   before any candidate freeze (Finding F-1).
5. **Full re-proof.** Rerun both complete JUnit lanes; run the unmodified
   three-condition/two-build actual-root matrix; run exactly one
   package/verify/sealed-reproduce sequence; obtain final independent
   non-author frozen-package QA.
6. **Ceiling.** Return at most
   `READY_FOR_INDEPENDENT_REVIEW_WITH_RESERVED_ACTIONS_HELD` under the
   unchanged DWO-05 acceptance conditions (DWO-05 order §6).

Concurred without modification:

- **No DWO-06** is created for this environmental release issue, and none for
  the P3 equality-boundary test debt. The P3 (missing equality-only
  regression at the exact 0.95 comparator-retention boundary, `>=` in code)
  is recorded as debt and must be listed in the DWO-05 handoff; it is
  scientifically inactive at the current zero denominator.
- **No weakening** of the distribution matrix, residue diagnostics,
  raw-state lock, or any fail-closed guard is authorized on resumption, even
  in an executor believed clean.

## 6. Reserved boundaries and authority state

Unchanged from the DWO-05 order. DWO-05 and this directive authorize no
provider contact; no account, trial, order, purchase, payment, contract, NDA,
credential, sample, download, API connection, or ingestion; no real
v1.2.1/v1.2.2 non-regression execution; no historical-final or
prospective-final opening; no modification of the 630-session historical-final
identities; no model, feature, baseline, outcome, market, or partition-design
change; and no formal, predictive, trading, alerting, or automated-action
authority. The Product Owner's separate bounded Kibot-inquiry authorization
remains valid, unexecuted, and unaffected.

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

## 7. Plain-language course statement

The workshop finished the repairs it was ordered to make, and every test on
the bench passes. But the room itself keeps putting deleted boxes back on the
shelf, and the packing rule says a crate may only be sealed after proving the
shelf stays empty. The packer refused to seal the crate three times — that
refusal is the safety system working, not failing. Keep the work preserved
exactly as checkpointed, move to a room that doesn't restock shelves on its
own, prove custody of the three licensed boxes again, rewrite the paperwork
from what actually happens in the new room, and seal one crate under the same
unweakened rules. Build no new machinery, open no sealed exam, contact no
vendor, and change no authority while doing it.
