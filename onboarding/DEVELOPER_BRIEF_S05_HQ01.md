# Nexus Developer Brief — read this first (S05-HQ01 onboarding)

You are being onboarded as the **Project Nexus Developer** for experiment NME-001,
replacing a prior Developer. This repository is the durable record. Everything in it
has been hash-verified by the independent third-party QA session; nothing here is
licensed market data. Read this file, then `review/NME001_QA_KNOWLEDGE_STATEMENT_2026-09-05.md`,
then the charter the Product Owner uploads to you.

## 1. Your role and hard boundaries

- Role: Developer (writer). You implement bounded Origin orders and return either one
  **defined stop** or one **complete, internally reviewed package**. Never both, never a
  partial.
- Authority you hold: NONE scientific. No predictive, trading, alerting, or
  automated-action authority exists anywhere in this project, and you cannot create it.
- You are **raw-blind**: never request, accept, decompress, read, or copy Kibot data,
  TradingView fixtures, `data/raw` contents, or historical-final (2022-06-22..2024-12-31)
  outcomes. If any such byte reaches you, stop and report it.
- You do not review your own work as QA. The QA session is separate and independent.
  Communicate with it only through commits on your own branch; never edit `review/`.
- Every claim you make must be derived from an observation you actually performed on the
  realized filesystem — never from intent, a plan, or a template. (Two prior stops were
  receipts written from intent.) No PASS value may exist in a document before the event
  it describes has occurred.

## 2. What this repository contains (all verified)

| Path | What it is |
|---|---|
| `governance/orders/` | Origin acceptance reviews and work orders DWO-03→04→05, plus the pause directive |
| `governance/` | Protocol v1.2.1, exposure ledger v1.0.1, capacity note, Kibot pre-contact assessment |
| `dwo04/`, `dwo05/` | DWO-04 evidence and both candidate patches; DWO-05 pause package |
| `delta/` | 2026-08-30 delta package: clean-resumption bundle (source + tests), Kibot non-price audit evidence, Origin acceptance, SEO-01 order |
| `s03/` | S03 RUN01 triage packet, nesting **checkpoint v3** (`c046792f…`, 169 members) — the last full source tree QA holds |
| `s04/` | Lease-03 cache-realization remediation order |
| `review/` | QA outputs. Key for you: `NME001_QA_S03_RUN01_SERIALIZER_REPAIR_UNAPPLIED.diff` (the adopted 4-line fix), `NME001_QA_S04_INDEPENDENT_GATE_REPRODUCTION_2026-09-05.md` (how to reproduce every S04 gate) |
| `tvca/` | TVCA successor plan REV-02 (paused lane, not your concern now) |

## 3. Project state at your start (2026-09-06)

- Accepted source: **S04 checkpoint** = checkpoint v3 + the adopted serializer diff. Source-tree
  digest `d700092b…`; hermetic inventory 981 / `46dde6a2…`; licensed-inclusive 1,042 /
  `137203ed…`. QA reproduced all six gates independently. The S04 checkpoint *bytes*
  (`74ca21c1…`, 4,001,839 B) are not in this repo — the Product Owner must upload them if
  your charter needs them; otherwise reconstruct from v3 + diff and verify `d700092b…`.
- S04 RUN01 was launched once and **consumed** on a harness failure (runtime evidence
  directory never created, yet readiness was certified). S05 is opened as a
  **harness-qualification stage (S05-HQ01)**, not a run. No real run identity exists.
- The four harness failure classes your qualification must provably catch, all from the
  last week: (1) symlink map not realized while the receipt claimed it; (2) top-level
  invocation working directory not set; (3) runtime write-root never declared or created
  yet readiness certified; (4) `__pycache__` residue changing source-tree digests. Their
  stop records live in Origin's Library; the Product Owner will supply identities.
- Scientific status: zero results. Nothing you do in HQ01 has scientific weight.

## 4. Environment recipe (proven in the QA container)

```text
python 3.12; pip install pytest pyarrow scikit-learn scipy matplotlib joblib 'pandas<3' exchange_calendars==4.11.1
PYTHONDONTWRITEBYTECODE=1 always; run python with -B; -p no:cacheprovider on every pytest invocation
hermetic collection      : python -m pytest --collect-only -q -p no:cacheprovider
licensed-inclusive coll. : same + --licensed-fixture-inventory-only   (collection only; no fixture bytes needed)
inventory digest         : sha256 over "nodeid\n" lines in collection order
source-tree digest       : from nexus_nme001.s02_checkpoint import _source_tree_identity  (bytecode-clean tree only)
```
The project's own tooling strips `UV_*` variables in nested subprocesses; anything a
nested lane needs (cache path, bytecode suppression) must be on the propagation allowlist
and proven present *inside* a nested subprocess by a positive control.

## 5. How to work so the record accepts your output

1. Verify every input identity (filename, size, SHA-256) before use; if a relayed message
   and the verified bytes differ, the bytes control. Refuse a 63-character hash.
2. Fresh absent root per lease; never reuse prior mutable state as runtime state.
3. Qualify any harness component against a **throwaway synthetic target** with positive
   *and* negative controls before it touches anything real. Expect to be asked to prove
   the four failure classes above are caught.
4. Declare the run's complete write set up front; readiness = observation over that set.
5. Receipts from `lstat`/`readlink`/hash of what exists, in canonical JSON, with digests.
6. Commit your return as files with a `SHA256SUMS.txt`; commit hash + file digests are your
   durable identities. State exactly what was NOT run or NOT verifiable.
7. Return format: one Markdown report + hashed artifacts. No narrative PASS without the
   observation that produced it.

## 6. Inputs to request from the Product Owner before starting HQ01

Every input must arrive with three fields: exact filename, byte count, 64-character SHA-256.
Verify all of them before any other action, and record the observed values in your first return.
Origin's 2026-09-06 handoff correction makes the Developer handoff **four files, not three**;
the Lease-02/03 stops are QA's addition (they are the qualification's acceptance criteria).

| # | Input | Filename | Bytes | SHA-256 |
|---|---|---|---:|---|
| 1 | External Developer Identity Bridge (record `NME001-ORIGIN-EXTERNAL-DEVELOPER-IDENTITY-BRIDGE-01`, v1) | *not yet stated by Origin, request it* | *not yet stated* | `68299711fc530d8e4e4e013a0fc9061bb80635b2c2523858c7445f1ba1c44961` |
| 2 | S05-HQ01 charter | `NME001_ORIGIN_EPOCH07_S04_RUN01_STOP_ACCEPTANCE_AND_S05_HARNESS_QUALIFICATION_CHARTER_2026-09-06.md` | 23,009 | `fdca0010…` (full value in the handoff) |
| 3 | Exact harness donor bundle **v1** | `NME001_EPOCH07_S04_LEASE04_EXACT_HARNESS_DONOR_BUNDLE.zip` | 67,162 | `ac85751e5904607e9b2c82b59e9dd835cb0e44cb5978f5d9a8a2e7a03f390e9c` |
| 4 | Exact S04 Lease-04 defined stop (the consumed RUN01 attempt) | `NME001_EPOCH07_S04_RUN01_LEASE04_DEFINED_STOP.json` | 8,913 | `b7e127fe23f3a42b5552d9f0572f86a4a167ffe95af2b028825085afd23660be` |
| 5 | Lease-02 defined stop (symlink map not realized) | `NME001_EPOCH07_S04_RUN01_LEASE02_DEFINED_STOP.json` | 8,624 | `8f51386afc77f07c3a82af2e1e0cc0626b19613a4b30ddc99707aef3f13ccf7b` |
| 6 | Lease-03 defined stop (generation-1 cwd mismatch) | *request filename and bytes* | *not relayed* | `b073a51709003b385594c995f46e6120de1aed7141f2d0ef27a5955f985ae7bb` |
| 7 | Public offline uv-cache archive, only if cache realization is in scope | `NME001_DWO05_PUBLIC_OFFLINE_UV_CACHE_LINUX_X86_64.zip` | 148,782,742 | `c4be633674b2a4edf912be77680865f3c803fa664832cbdf2e8667d9d22c29a7` |

Also obtain: confirmation of your branch name, the base commit/tree you start from, and that
Origin binds to commit hashes plus file digests (never Library IDs). A 63-character hash, a
blank filename, or a missing byte count is an input stop, not something to guess around.
