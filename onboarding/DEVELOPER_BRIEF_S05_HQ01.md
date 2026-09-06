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
  (`74ca21c1…`, 4,001,839 B) are not in this repo and are **not an HQ01 input**: the charter
  forbids importing, collecting, or running Nexus project code or tests during HQ01. Do not
  reconstruct or open the checkpoint unless a later real-run order names it.
- S04 RUN01 was launched once and **consumed** on a harness failure (runtime evidence
  directory never created, yet readiness was certified). S05 is opened as a
  **harness-qualification stage (S05-HQ01)**, not a run. No real run identity exists.
- The four harness failure classes your qualification must provably catch, all from the
  last week: (1) symlink map not realized while the receipt claimed it; (2) top-level
  invocation working directory not set; (3) runtime write-root never declared or created
  yet readiness certified; (4) `__pycache__` residue changing source-tree digests. The exact
  Lease-02/03/04 stop records are in this repo: `s05/` continuity packet (see §6).
- Scientific status: zero results. Nothing you do in HQ01 has scientific weight.

## 4. Environment recipe (QA's reproduction record — NOT for use during HQ01)

This recipe is how QA reproduced the S04 gates on the repo's checkpoint. Under the
S05-HQ01 charter §11 you must **not** collect or run Nexus tests, and §5 forbids network
dependency acquisition: HQ01 uses only the frozen public offline uv cache, its bundled
bootstrap, and locked offline `uv sync`. Read this section for the gotchas only.

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

## 6. Inputs (all delivered in one packet, archived in this repo)

Origin's sanitized continuity packet is the single handoff. QA verified its outer identity,
all nine internal digests, every charter-stated donor binding, and a zero-result leak scan.

- Packet: `s05/NME001_S05_HQ01_SANITIZED_CONTROL_CONTINUITY_PACKET_20260906.zip`, 103,630 B,
  `ced7d1a4a7d3bf4cd377c9fdcc826f7b885c4201f08775edde026c7e6915a1d5`. Verify it yourself, then
  verify `SHA256SUMS.txt` inside it, before reading anything else. Read `00_READ_FIRST.md`
  for precedence: the charter is the sole work authority; the bridge governs identities only.

| Member | Bytes | SHA-256 (prefix) | Role |
|---|---:|---|---|
| `…S05_HARNESS_QUALIFICATION_CHARTER_2026-09-06.md` | 23,009 | `fdca0010…` | controlling work authority |
| `NME001_ORIGIN_EXTERNAL_DEVELOPER_IDENTITY_BRIDGE_2026-09-06.md` | 7,411 | `68299711…` | identity/custody rules for your returns |
| `NME001_ORIGIN_S05_HQ01_CURRENT_STATE_RECONCILIATION_2026-09-06.md` | 6,560 | `27c45216…` | status only, no authority |
| `NME001_EPOCH07_S04_LEASE04_EXACT_HARNESS_DONOR_BUNDLE.zip` | 67,162 | `ac85751e…` | diagnostic donor, not qualified |
| `NME001_EPOCH07_S04_RUN01_LEASE02_DEFINED_STOP.json` | 8,624 | `8f51386a…` | regression spec: cache symlinks unrealized |
| `NME001_EPOCH07_S04_RUN01_LEASE03_DEFINED_STOP.json` | 4,856 | `b073a517…` | regression spec: generation-1 cwd |
| `NME001_EPOCH07_S04_RUN01_LEASE04_DEFINED_STOP.json` | 8,913 | `b7e127fe…` | regression spec: write-root unrealized |
| `…LEASE03_CWD_STOP_DISPOSITION_AND_LEASE04_RUN01_CONTINUATION_2026-09-06.md` | 17,326 | `be54cd54…` | retired Lease-04 order, context only |

**Separate, not in the packet, required before qualification can execute:** the public
offline uv-cache archive `NME001_DWO05_PUBLIC_OFFLINE_UV_CACHE_LINUX_X86_64.zip`,
148,782,742 B, `c4be633674b2a4edf912be77680865f3c803fa664832cbdf2e8667d9d22c29a7`. Its absence
is a preflight block, never permission to fetch dependencies from the network.

Also obtain from the Product Owner: your branch name and base commit/tree. Bind every
return by commit + tree + file digests exactly as the bridge specifies; never claim Library
IDs. A 63-character hash, a blank filename, or a missing byte count is an input stop.
