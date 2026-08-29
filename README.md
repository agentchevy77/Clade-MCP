# NME-001 Governance Record — DWO-04 / DWO-05

This branch holds the Project Nexus NME-001 research-governance record as
received on 2026-08-29, together with the Origin-side independent review
performed on it.

NME-001 is a research-only market-microstructure experiment operated under a
fail-closed authority model: every formal-evidence, predictive, trading,
alerting, automated-action, data-acquisition, and provider-contact authority
in this record is `NONE` or `HOLD`. Nothing in this repository grants,
implies, or elevates any such authority, and no market data — licensed or
otherwise — is present in any file here.

## Current state

- **DWO-04** (narrow correction candidate v0.3.1, protocol v1.2.1): accepted
  by Origin with three findings (one P1 build-custody defect, two P2
  reconciler gaps) that became the DWO-05 order.
- **DWO-05** (build-safety and evidence-reconciliation closeout, target
  v0.3.2 / protocol v1.2.2): implementation complete and passing both test
  lanes, but **paused before candidate freeze** — a managed-workspace
  filesystem asynchronously recreated deleted licensed-fixture paths during
  the required actual-root no-raw build proof, and the release guard
  correctly failed closed. No DWO-05 candidate exists.
- **Origin decision** on the pause:
  `governance/orders/NME001_ORIGIN_DWO05_PAUSE_RATIFICATION_AND_RESUMPTION_DIRECTIVE_2026-08-29.md`.

## Layout

| Path | Contents |
|---|---|
| `governance/orders/` | The chain of Origin acceptance reviews and work orders (DWO-03→04, DWO-04→05, and the DWO-05 pause decision) |
| `governance/` | Active protocol v1.2.1, exposure ledger v1.0.1, capacity/configuration note, Kibot pre-contact assessment |
| `dwo04/` | DWO-04 candidate evidence: verification report, reproduction contract, material-attempt ledger, external manifest/receipt, and the DWO-03→DWO-04 candidate patch |
| `dwo05/` | DWO-05 pause package: SITREP for Origin, pause-checkpoint SHA256SUMS, and the DWO-04→paused-DWO-05 worktree patch |
| `review/` | Origin's independent verification annex: every hash, calendar, session-identity, and statistical claim in the record that could be recomputed, with results |

## Verification status

All sixteen received files verify against every identity claimed for them
inside the record. The calendar layer (session counts and all
ordered-session identity hashes, including the 630-session historical final)
was independently reconstructed from the public XNYS calendar and matches
exactly. See `review/NME001_ORIGIN_INDEPENDENT_VERIFICATION_ANNEX_2026-08-29.md`
for the full results and the explicit list of claims that are *not*
verifiable from this record (candidate ZIP bytes, JUnit executions, licensed
fixtures, checkpoint ZIP).
