# Project Nexus — EPOCH07-S04 Cache-Realization Remediation and RUN01 Continuation

**Identity:** `NME001-ORIGIN-EPOCH07-S04-CACHE-REALIZATION-REMEDIATION-AND-RUN01-CONTINUATION-01`  
**Issued:** `2026-09-06T01:15:21Z`  
**Disposition:** `LEASE02_PREFLIGHT_DURABILITY_STOP_ACCEPTED / RUN01_NOT_LAUNCHED / RUN_ATTEMPT_NOT_CONSUMED / LEASE02_CLOSED_PERMANENTLY / ACCEPTED_S04_CHECKPOINT_REMAINS_CONTROLLING / RUN01_RESERVATION_RETAINED / LEASE03_AUTHORIZED_FOR_ONE_FRESH_PUBLIC-CACHE-REALIZATION-CONTRACT-RESTORATION-AND-THE-SAME-RUN01 / NO_S04_RUN02`  
**Scientific effect:** `ZERO_AUTHORIZED_SCIENTIFIC_SEMANTIC_EFFECT`  
**Authority basis:** Origin's standing bounded Nexus autonomy under the Product Owner's anti-ceremony direction. No new Product Owner approval is required.

## 1. Stop disposition

Origin accepts the exact Lease-02 stop as a truthful, safe, prelaunch engineering stop:

- record: `NME001_EPOCH07_S04_RUN01_LEASE02_DEFINED_STOP.json`;
- Library: `libfile_3675c784ebc88191a8c1fd16fa7ff33f`;
- version: `0`;
- size: `8,624` bytes;
- SHA-256: `8f51386afc77f07c3a82af2e1e0cc0626b19613a4b30ddc99707aef3f13ccf7b`;
- status: `S04_RUN01_DEFINED_STOP`; and
- failure boundary: `PRELAUNCH_DURABILITY / REALIZED_PUBLIC_CACHE_FILESYSTEM_INVENTORY`.

The exact counters control: run launch count `0`; outer launcher, supervisor child, project import, `uv sync`, collection, tests, scientific execution, protected staging, protected custody, readiness, and `.venv` all did not start or did not exist. Protected inputs were not materialized. Historical-final bytes and outcomes remained closed.

Therefore:

1. Lease 02 is consumed and closed permanently.
2. S04 RUN01 was not launched, attempted, consumed, or converted into evidence.
3. The same RUN01 identity remains a lawful unconsumed reservation.
4. This order authorizes a fresh prelaunch continuation and, only if every gate passes, the first and only S04 RUN01 launch. It is not a retry, rerun, relaunch, RUN02, S05, or Epoch 08.
5. Lease-02 records remain diagnostic/preflight records with engineering and scientific evidence authority `NONE`.

## 2. Accepted checkpoint remains unchanged

The accepted prospective S04 checkpoint remains the sole project-source input:

- Library: `libfile_ac30da9757808191abde59ff75dceff6`;
- version: `0`;
- size: `4,001,839` bytes;
- SHA-256: `74ca21c1dab80fb3fb1a8fd87211127495c7e60c0fde13448e7bcb42affb0104`;
- manifest SHA-256: `1f59b080407ee65cd622c6175fd5f3a26861251361b3a2ed3c463b70cf56f5cc`;
- source-tree SHA-256: `d700092b3c414e8ccfb3dfb7bc076ed7a8ea1359be38b2ebba728b0e3d5893fa`;
- accounting: `171` manifest-bound members plus one self-excluded manifest; and
- dependency projection: `13+1 / 14 EXACT`, SHA-256 `878bc4fac6824920d427f1c9b5f862949604896365ba752f143c2aedd87822f5`.

The accepted collect-only inventories remain exactly:

- hermetic: `981`, ordered SHA-256 `46dde6a20b29221f6961bd8ff02254950080d58ffb3f517a98c8c25cab6e626e`; and
- licensed-inclusive: `1,042`, ordered SHA-256 `137203ed6b1267349e37898f1deed5a2844429eebea1be3cb8b4eb4e74428464`.

No project source, test, configuration, lockfile, checkpoint, dependency, inventory, protocol, model, label, metric, exclusion, partition, final identity, or scientific meaning may change under this order. Do not create a successor checkpoint of any identity or replace/refreeze the accepted S04 checkpoint.

## 3. Cache-forensics finding

The immutable public cache archive is healthy and regular-file-portable within the already-frozen Linux x86_64 / CPython 3.12 execution binding:

- Library: `libfile_7e5b770cc5708191a05b044ebdecf534`;
- size: `148,782,742` bytes;
- SHA-256: `c4be633674b2a4edf912be77680865f3c803fa664832cbdf2e8667d9d22c29a7`;
- ZIP entries: `8,933`, all regular and non-symlink;
- payload: `8,928` manifest-bound regular files;
- control members: the payload manifest, package manifest, wheel-source identities, symlink map, and bootstrap; and
- archive symlink entries: `0` by design.

The exact identities of the relevant bundled controls are:

| Control | SHA-256 |
| --- | --- |
| `CACHE_PAYLOAD_MANIFEST.json` | `f153c44e1d1f07685c1855026c54b764f19c6d1ec008f65e66af03abf55e0def` |
| `PACKAGE_MEMBER_MANIFEST.json` | `4fb00aa2d367d8ff4ef18658ef794e85831468bead201e0fe0b44de0a994fa68` |
| `PUBLIC_WHEEL_SOURCE_IDENTITIES.json` | `a01d4e2e5d7ce5fb267a8c2db812875353aa78170cfc7ff8ad303c7cf6b26466` |
| `UV_CACHE_SYMLINK_MAP.json` | `ef888c8981ba1375c7df590f9f2e01d879376da18b4e2f0b2647cb8d81b50368` |
| `bootstrap_uv_cache.py` | `1509a85876f73e0c404306a52ec1d153715271fa08a9fec445134abc6ad64740` |

The archive's exact bootstrap is the frozen mechanism that copies the regular payload into an absent `XDG_CACHE_HOME/uv` and reconstructs the `31` safe relative directory symlinks from the map.

Lease 02 realized all `8,928/8,928` regular files with zero missing or unexpected regular paths, but realized `0/31` symlinks. All `31` mapped link paths were absent. The bundled bootstrap's canonical `NME001_DWO05_UV_CACHE_REALIZATION_RECEIPT.json` was absent. The Lease-02 custom receipt nevertheless stated `payload_symlinks: 31`; that attestation is invalid and must never be reused as proof.

The direct process deviation is that Lease 02 did not complete the frozen bootstrap contract and produced a custom PASS receipt from intended construction values rather than from an observed non-following walk of the realized filesystem. This is the launcher-level form of a forward-written PASS record. The later durability probe was the first independent topology check and correctly caught it before launch.

Origin independently ran the exact bundled bootstrap over the exact archive in a disposable, nonproject, unprotected root on the same runtime filesystem. It produced `8,928` regular files and `31` exact contained relative symlinks. This establishes that the archive, map, bootstrap, and filesystem capability are sufficient; it is a diagnostic, not S04 run evidence. Lease 03 must reproduce the result independently.

Adopt this bounded cause classification:

`CACHE_REALIZATION_ATTESTATION_INVALID / CUSTOM_REALIZATION_DID_NOT_COMPLETE_FROZEN_BOOTSTRAP_CONTRACT / REGULAR_PAYLOAD_INTACT / REQUIRED_LINK-MAP_RECONSTRUCTION_OMITTED`

Filesystem chronology and unchanged link-parent metadata support omission during realization and rule out later positive-control cleanup in the preserved Lease-02 root. The exact lower-level mechanism—skipped bootstrap invocation versus an incomplete custom construction—is not needed for the safe from-zero remedy. Do not redefine link-versus-copy as equivalent and do not weaken the frozen `8,928 + 31` contract.

## 4. Successor lease and clean roots

Remain within:

```text
work_order: NME-001-SEO-01
execution: NME-001-SEO-01-RECOVERY-EPOCH-07
segment: EPOCH07-S04
run: NME001-SEO01-EPOCH07-S04-RUN01
run_state: RESERVED_NOT_LAUNCHED / LAUNCH_COUNT_0 / ATTEMPT_NOT_CONSUMED
closed_lease: NME001-E07-S04-WRITER-LEASE-02 / CLOSED_PERMANENTLY
successor_lease: NME001-E07-S04-WRITER-LEASE-03
lease_scope: PRELAUNCH-PUBLIC-CACHE-REALIZATION-CONTRACT-RESTORATION-AND-SAME-RUN01-ONLY
```

Exactly one oriented high-capability Developer may claim Lease 03 after reading this order, confirming Lease 02 is closed, and confirming no other Nexus Developer writer, test, scientific process, or authorized run is active.

Choose one new absent absolute parent `B`, disjoint from all prior roots. Recreate the S04 root map from the controlling S04 RUN01 order under that parent. Every Lease-02 mutable project root, cache realization, receipt, harness, checker, probe, launcher, and runtime artifact is diagnostic-only and must not be resumed, copied as runtime state, or treated as transferable PASS evidence.

The accepted S04 checkpoint and the immutable authorities named in this and the controlling S04 order must be freshly materialized and reverified. If the new absent root, single-writer state, or any authority identity cannot be established exactly, stop.

## 5. Exact cache realization remedy

Before any project import, `uv sync`, test, protected-input action, or scientific action:

1. Materialize and rehash the exact public cache archive under the same frozen Linux x86_64 / CPython 3.12 runtime and normalized-environment binding required by the controlling S04 order. Verify ZIP CRC, safe regular-only member types, exact `8,933` archive paths, package manifest, payload manifest, wheel-source identities, symlink map, bootstrap identity, path safety, case/Unicode collision absence, and zero packaged symlink or special entries.
2. Extract it into a fresh package root without changing its bytes. Reject traversal, absolute paths, duplicate names, special entries, and any manifest discrepancy.
3. Require the selected fresh `P/uv` destination to be absent.
4. Invoke the exact bundled `bootstrap_uv_cache.py` once, unmodified, with its exact extracted package root and `--xdg-cache-home P`. Do not substitute direct `copytree`, a hand-written realizer, copied directories, hard links, junctions, a dependency refresh, network resolution, or a hand-created canonical receipt.
5. Preserve and freshly read back the bootstrap-created `P/NME001_DWO05_UV_CACHE_REALIZATION_RECEIPT.json`.
6. Independently rewalk `P/uv` using non-following filesystem inspection (`lstat` and literal `readlink`). Require:
   - `8,928/8,928` regular files at the exact payload-manifest paths, sizes, and SHA-256 values;
   - total regular payload size `481,715,990` bytes;
   - `31/31` symlinks at the exact map paths with the exact literal relative targets;
   - every link's parent and every ancestor from that parent through `P/uv` is a real non-symlink directory;
   - every resolved link target contained within `P/uv` and resolving to a real non-symlink directory;
   - zero missing, unexpected, broken, absolute, escaping, or special entries; and
   - `uv cache dir` resolving exactly to `P/uv` under the final normalized environment.
7. Before its first use, freeze and hash the independent cache-verifier source bytes. Canonically serialize two independently observed, path-sorted JSON arrays. Regular-ledger `path` values must use the exact payload-manifest namespace, with exactly one guarded `uv-cache/` prefix added to each `P/uv`-relative observed path; entries use exact keys `path`, `sha256`, and `size_bytes`. Symlink-ledger paths remain exact `P/uv`-relative link-map paths; entries use exact keys `path` and `target`, where `target` is the literal `readlink` value. Sort records by the UTF-8 byte order of `path`; encode with `ensure_ascii=true`, lexicographically sorted object keys, separators `(',', ':')`, UTF-8, and exactly one terminal LF. Hash each observed ledger separately; compare every record and the complete path sets with the expected payload manifest and link map. Create a sanitized Lease-03 wrapper receipt that clearly separates expected manifest counts from observed filesystem counts. Its PASS must derive from these observed ledgers—not by copying the expected `31` from the map. Bind both observed-ledger digests, the archive and all five control hashes, canonical bootstrap receipt hash, verifier-source SHA-256, root, environment, and observation time.
8. Preserve/read back the wrapper receipt and independent verification result before any external-harness freeze. Keep the realized cache unchanged until the final launcher-bound durability probe, except for the expressly authorized read-only hashes, `lstat`/`readlink` inspection, inheritance probes, and `uv cache dir` resolution.

Any cache mismatch, bootstrap error, missing canonical receipt, receipt/observation disagreement, link-type substitution, target escape, or need to alter the immutable archive, manifests, map, bootstrap, dependency versions, or platform contract requires a defined stop. No second cache realization is authorized under Lease 03.

## 6. Fresh external-harness and prelaunch chain

All unchanged requirements of `NME001_ORIGIN_EPOCH07_S04_CHECKPOINT_ACCEPTANCE_AND_RUN01_ORDER_2026-09-05.md`—Library `libfile_2ea24c3afb7c819186578964de4d8c66`, backing `file_00000000ec3881f592a7d0cf92066502`, v0, `24,545` bytes, SHA-256 `a47fb126fa41d20fcd5b4e4b6327b603cfed7e4495c9580f1b386ac115a0a47e`—remain controlling, including the normalized environment, `SOURCE_DATE_EPOCH` absence, `PYTHONDONTWRITEBYTECODE=1` propagation, bytecode-clean checkpoint verification, protected-data absence, exact readiness object, custody/placement gates, lane order, observability, return, QA boundary, stops, and authority restrictions.

### Precedence and substitution

This order supersedes the controlling S04 RUN01 order only for the failed public-cache realization/receipt method, the fresh Lease-03 root and record bindings, and the expressly renewed Lease-03 prelaunch counters. Every inherited reference to Lease 02, its parent/root paths, cache receipt, candidate/review/checker/probe records, launch authority, or stop/update duties is read as the corresponding fresh Lease-03 identity and record. Lease 02 remains closed and no Lease-02 PASS transfers. The fixed segment remains `EPOCH07-S04`, the fixed run remains `NME001-SEO01-EPOCH07-S04-RUN01`, and all inherited lane, protected-input, scientific, return, QA, hold, and authority semantics remain byte-for-meaning unchanged.

Reconstruct the external harness from the durable sanitized baseline and diffs named in that order, never from Lease-02 mutable runtime state. The allowed Lease-03 changes are limited to:

- binding the fixed S04 segment and RUN01 identity to the fresh Lease-03 root, schema, filename, log, output, and record identities;
- wiring the exact canonical bootstrap receipt and the independently observed Lease-03 cache-verification receipt;
- requiring the exact `8,928` regular plus `31` symlink contract before launch;
- binding this Origin order and the exact accepted S04 checkpoint/inventories; and
- fixed-target hash updates mechanically caused by only those allowed changes.

Preserve the prior `verify_cache()` semantics, including the `uv-cache/` prefix guard, non-following inventory, literal symlink-target checks, contained resolution, and exact regular-file hashes. Do not accept zero symlinks or link-type alternatives.

Before checker invocation, freeze the fresh candidate, manifest, baseline-to-Lease03 unified diff, planned placement matrix, environment/cache probe, cache receipts, independent filesystem verification, launcher candidate, durability candidate, checker candidate, and expected-result contract. Obtain one fresh role-separated nonauthor static review over the exact frozen bytes. The reviewer must independently verify that the change is confined to the authorized external realization and mechanical bindings and that no project/checkpoint/scientific semantics changed.

To avoid needless approval cycling, Lease 03 may create an initial prechecker candidate plus at most one repair/refreeze only if the first complete static review identifies a defect confined to the explicit mechanical allowlist above. Each candidate requires a complete fresh review. A second-candidate failure, scope expansion, or ambiguity requires a defined stop.

After a complete static PASS, invoke one disposable positive-control checker and then one authoritative checker, both under the exact normalized environment with `python -B`. Require the expected positive-control failure and residue disposal, followed by exact authoritative PASS. No third checker invocation and no post-checker repair are authorized.

Publish and freshly read back the authoritative checker result, final launcher record, supervisor durable probe, and one launcher-bound durability probe. The final probe must independently re-prove the exact cache filesystem inventory immediately before launch, including fresh canonical observed-regular and observed-symlink ledger digests compared to the expected manifest and map. Before transitioning to `RUN_LAUNCH_READY`, durably preserve and read back a compact Lease-03 prelaunch capsule—or an exact set of individually durable records sufficient to reconstruct it—containing the external harness, component manifest, unified diff, independent cache-verifier source, both observed cache ledgers and digests, canonical and wrapper cache receipts, environment/cache inheritance probe, planned protected-placement matrix, expected-result contract, static review, checker results, launcher, durability probes, and exact hashes. Do not include the public cache payload, protected data, project runtime residue, or mutable root.

Lease-02 reviews, checker counters, and PASS records do not transfer to Lease 03 and do not count as Lease-03 invocations.

## 7. Conditional first RUN01 launch

Only after every fresh Lease-03 prelaunch gate above passes may the lease transition to `RUN_LAUNCH_READY` and invoke the still-unconsumed `NME001-SEO01-EPOCH07-S04-RUN01` exactly once.

Execute Sections 5 through 8 of the controlling S04 RUN01 order unchanged. That includes:

- exact environment and cache binding;
- unchanged offline `uv sync --locked --extra dev --offline`;
- exact `981` hermetic collection and complete pass before protected materialization;
- exact nine-placement protected-input custody and readiness gate;
- exact `1,042` licensed-inclusive collection and complete pass;
- restoration and rehash of protected placements;
- unchanged `stage=development` scientific lane over the authorized development prefix only;
- historical-final hold;
- checkpoint and runtime-residue reconciliation;
- deterministic double-build, complete licensed-byte leakage scan and external receipt;
- role-separated final-return review; and
- either one complete sealed candidate for external QA or one defined stop.

The outer launcher handoff is the single point at which launch count becomes `1` and the S04 RUN01 attempt is consumed. No launched run may be retried. This order grants no S04 RUN02.

## 8. Stop and return rules

At any prelaunch or launched failure, preserve/read back one exact stop record, update Developer role memory in place, close Lease 03, and stop for Origin. Do not start a successor action.

Stop immediately for any identity, manifest, inventory, checkpoint, cache, receipt, environment, harness, checker, durability, custody, placement, lane, test, scientific, leakage, historical-final, observability, or authority mismatch; for any unauthorized network/provider/data action; or for any requested change outside this exact order.

If a complete sealed and internally reviewed S04 RUN01 candidate is produced, classify it only as:

`CANDIDATE_READY_FOR_EXTERNAL_QA / ZERO_SCIENTIFIC_VOTE`

Third-party QA is not a pre-run approval gate for this narrow engineering remedy. It remains mandatory before scientific vote, historical-final consideration, or any authority change.

Authority remains:

```yaml
development_execution: AUTHORIZED_ONCE_UNDER_THE_STILL_UNCONSUMED_S04_RUN01_AFTER_ALL_LEASE03_PREFLIGHT_GATES
development_evidence_authority: NONE_UNTIL_COMPLETE_RETURN_THIRD_PARTY_QA_AND_ORIGIN_REVIEW
historical_final: HOLD
operational_release: HOLD
formal_predictive_authority: NONE
trading_authority: NONE
broker_authority: NONE
alerting_authority: NONE
automated_action_authority: NONE
```

Proceed autonomously after exact order readback, quiescence confirmation, and Lease-03 claim. Return only at a defined stop or with the complete sealed and internally reviewed S04 RUN01 candidate.
