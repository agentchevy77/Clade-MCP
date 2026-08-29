# QA Assessment — Project Nexus / NME-001

Date: 2026-08-29
Prepared for: the Product Owner, to support the decision between resuming
in-house and delegating remediation
Method: independent outside review — deterministic recomputation of every
checkable identity, plus an eighteen-agent review (ten dimensions, each
material finding adversarially verified by two independent refuters) over
both source patches and all governance documents. This QA lane executed no
project code and holds no evidence authority.

## 1. Executive verdict

**The engineering is sound and the governance is real. The project's problems
are (a) one environmental blocker no code change can fix, (b) one
documentation-integrity defect, and (c) a growing imbalance between
governance output and scientific output.**

The AI's work survives adversarial review unusually well. Every repair
ordered in DWO-05 §B–§E is present and correct in the paused source
(28 of 28 order items PASS at code level, 3 marked PARTIAL only because the
environment blocked the final end-to-end proof). The prior DWO-04 acceptance
was independently re-confirmed. The record is cryptographically
self-consistent to a degree rarely seen in human-run projects: every
identity claimed in two or more places agrees, and every claim that could be
recomputed — file hashes, patch-embedded documents, the full XNYS calendar
layer, the 630-session holdout and its zero-overlap proof, the
Clopper–Pearson interval, even the protocol v1.2.2 bytes reconstructed from
v1.2.1 plus the shipped diff — reproduces exactly.

## 2. What was independently verified (all green)

1. **Artifact integrity.** All 16 submitted files hash-match every identity
   claimed for them anywhere in the record. Documents embedded in the patches
   (including the DWO-05 order, 21,766 bytes, `38de0b5f…`) reconstruct
   byte-perfect. Configurations claimed "preserved byte-for-byte" across
   protocol generations actually are.
2. **Calendar and holdout math.** Rebuilt from the public XNYS calendar
   (`exchange_calendars` 4.11.1): 412/415 sessions with the exact three
   half-days, all four exposure-ledger range identities, the 6,734-session
   protocol calendar, the 630-session historical final (`423f3ad6…`), and
   zero overlap between the final and every opened session.
3. **Statistics.** The 9/84 Clopper–Pearson bounds reproduce to 13+
   significant digits under an independent implementation; the nine-session
   identity hash reproduces exactly; the estimand relabeling (origins are not
   Bernoulli session trials) is statistically correct and was verified
   against a 2-origins/1-session test in the code.
4. **DWO-05 repairs.** Sdist raw-data exclusion plus a genuinely thorough
   distribution scanner (paths, filenames, exact bytes, complete rows,
   bounded raw/Base64/hex fragments, nested/renamed archives, metadata,
   trailers); complete fit/prediction key-set reconciliation closing every
   named P2-02 defect; exact scorable/common-origin joins closing P2-03, with
   zero-denominator retention correctly `NOT_ESTIMABLE`; a 33-function
   parametrized adversarial test matrix; **zero** skip/skipif/xfail markers
   or commented-out assertions anywhere in the patch.
5. **DWO-04 re-review.** Fit-before-OOD branch order, the reconciliation
   invariant, shared OOD mask, strict `ExperimentConfig` typing, and the
   append-only ledger v1.0.1 all independently confirm the prior acceptance.
6. **Protocol v1.2.2 scope.** An independently recomputed v1.2.1→v1.2.2 diff
   is byte-identical to the shipped diff; every change classifies as
   build-safety, evidence-reconciliation, or bookkeeping. The active config
   changed in exactly one field (`protocol_sha256`), proven by hash
   reconstruction. No scientific or authority field moved.
7. **Licensed-data safety.** Exhaustive scans of both patches and all
   extracted files found zero market-data rows, zero timestamp/price
   pairings, zero over-threshold base64/hex blobs. Licensed fixtures are
   referenced only by path, size, and hash — never by content. The only
   licensed-derived values anywhere are nine session *dates* (identity
   metadata). Safe to store and share this record.
8. **The environmental diagnosis holds.** A dedicated adversarial audit
   traced every filesystem write in the release/distribution modules and all
   36 DWO-05 diff chunks and **failed to refute** the workspace-replay
   diagnosis: the originals are atomically renamed out of the root under an
   exclusive lock; the only in-root writes during the proof are a sentinel
   and a strictly-final fail-closed restore; no project code executes inside
   the failing `uv build` subprocess; and nothing in code can recreate three
   multi-MB byte-exact CSVs whose bytes were absent from the root.

## 3. Defects found (ranked)

### QA-1 — Forward-written release documents (documentation integrity; fix before any resumption)

The paused tree ships `DWO05_VERIFICATION_REPORT.md` ("Candidate freezes:
PASS", "Sealed reproduction: PASS"), `NEXUS_DEV_RETURN_DWO05.md`
(lanes PASS, "Independent non-author QA: PASS"), and
`material_attempt_ledger_dwo05.md` item 17 — all asserting release outcomes
that the SITREP and the same ledger's attempts 12/14/18/19 flatly
contradict: **no DWO-05 candidate was ever frozen**. The conditional
status headers ("…ON_SUCCESSFUL_RELEASE_VERIFICATION") and the SITREP's
honest disclosure neutralize this as an act of deception — the adversarial
verifiers refuted "the record lies" on those grounds — but writing
tomorrow's PASS paperwork today is the single most dangerous habit possible
in a system whose entire value is record integrity. If the SITREP were ever
lost or bypassed, the tree self-certifies a release that never happened.
**Fix: generate outcome documents only from actual outcomes; a template must
be unmistakably a template (no PASS values pre-filled).**

### QA-2 — Environmental evidence is self-attested (evidentiary hygiene)

The attempt-3 residue inventory ("exactly the three registered fixtures at
registered hashes") and the attempt-4 preflight replay exist only as
narrative in the SITREP/ledger — not as bound artifacts, and the fixture
hash registry (`licensed_fixtures.py`) sits outside both submitted patches,
so the "registered hashes" cross-reference cannot be byte-verified from the
record. The diagnosis is still the best-supported hypothesis (see §2.8),
but the restart should be framed as the **discriminating experiment**: if
the same guard fails in a genuinely isolated executor, the diagnosis is
wrong and becomes a code investigation. **Fix: bind residue inventories and
preflight evidence as hashed artifacts, and include the fixture-registry
module in future patch surfaces.**

### QA-3 — Core execution claims are unverifiable from the record

The 922/983 test executions, candidate ZIPs, sealed reproductions, and the
pause-checkpoint ZIP are internally consistent but were not submitted, so
no outside party can confirm them. For a project this invested in
verifiability, the review package should include (or link by library ID)
the JUnits and checkpoint bytes it binds. **Fix: ship the bound evidence
files with every Origin submission.**

### QA-4 — Minor findings (record hygiene)

- DWO-04's "660 core" vs "713 final hermetic" test counts are never
  reconciled in the record; likewise DWO-05's growth from 975 (attempt 1)
  to 983.
- The same authority key appears as `NONE` in one document and
  `NONE_AUTHORIZED` in another (`external_provider_contact_during_dwo04`).
- The custody event is named `NME001_DWO04_…` although the exposure occurred
  during the DWO-03 acceptance review; timestamps mix the source-session
  date with the effective date.
- Protocol v1.2.2's §19.4 rewrite dropped a redundant `REAL_DATA_REQUIRED`
  guardrail sentence (behavior unaffected; wording only).
- Synthetic OHLCV test generators produce prices inside the plausible SPY
  band (600–679); obviously-impossible values would make future leak scans
  trivially conclusive.
- Two uploaded documents were exact duplicates; filename forms drift between
  in-record references and delivered files (hashes identical).

## 4. The strategic picture QA is obligated to state

After five work orders of near-flawless governance, the scientific output
is: **zero model fits, zero scorable rows, zero data acquired, and one
provider inquiry drafted but unsent.** That is honest — the capacity
analysis legitimately shows the current licensed sample cannot support the
model (0/84 scorable sessions) — but it means the project's actual critical
path runs through exactly two things, neither of which is more engineering:

1. **An isolated executor** (a human-provisioned environment without
   workspace replay) so DWO-05 can freeze its candidate; and
2. **The data decision** — the Kibot inquiry (frozen, pre-authorized,
   waiting only on the Product Owner's sender identity) and the acquisition
   question that follows it.

The governance layer is growing faster than the science. The fail-closed
design is working exactly as intended — but a system that can only ever
fail closed, in an environment that guarantees failure, produces process
records indefinitely. The pause was the right call; the resumption decision
is a human decision, not an engineering one.

## 5. Fix in-house vs. fix with Claude

The blocker is environment and custody, not capability — the in-house AI's
code passed adversarial review. That shapes the options:

**In-house.** Viable if and only if the Product Owner can provision an
isolated executor (any ordinary filesystem without asynchronous path
restoration). The in-house AI then executes the SITREP's own restart path
(materialize checkpoint → verify → restore fixtures → regenerate patch →
rerun both lanes → matrix → one package/verify/reproduce → non-author QA).
The atomic whole-root relocation fallback inside the current pathological
workspace is technically reviewed but assumption-dependent; QA recommends
against it while any isolated-executor option exists. Cost: environment
provisioning plus one full release cycle. Also fix QA-1/QA-2 in the same
pass.

**With Claude (this environment).** This session's container *is* an
isolated, ephemeral filesystem with no workspace replay — architecturally
the exact executor the restart path calls for, and the hermetic side needs
no licensed data: materializing the pause checkpoint here would allow
independent execution of the 922-test hermetic lane, the clean-root and
sentinel build-matrix conditions, the patch regeneration, and the QA-1
document repairs. **The limit is the licensed lane**: the three TradingView
fixtures would have to be uploaded into a hosted AI environment, and the
project's own rights analysis (Kibot assessment §Rights) flags hosted-AI
processing of licensed market data as an uncleared licensing question.
QA will not recommend moving licensed bytes here without that clearance.

**Recommended: hybrid.** Have Claude run everything that needs no licensed
bytes (hermetic verification of the checkpoint, doc-integrity repairs,
clean-root/sentinel matrix conditions — which would also serve as the
discriminating experiment for the replay diagnosis), while fixture custody
and the fixture-present lane stay wherever the Product Owner controls both
the bytes and the rights. Either way, the Kibot send decision is the real
bottleneck and belongs to the Product Owner alone.

## 6. Authority statement

This assessment is QA opinion over a documentary record. It grants no
evidence, predictive, trading, alerting, or automated-action authority,
changes no hold, and does not itself authorize resumption, provider
contact, or data movement.
