# NME-001 Third-Party QA — S05-HQ01 F01 Frozen Qualification Return: Charter §10 Bounded Review (2026-09-06)

**Candidate:** `NME001_EPOCH07_S05_HQ01_FROZEN_QUALIFICATION_RETURN_2026-09-06.zip`, 9,486,845 bytes,
SHA-256 `4c6efd4e2564500efc542e26610d67a9059db4ce236e4dea08f66a34ce86a3bf`
(record `NME001-E07-S05-HQ01-FROZEN-QUALIFICATION-RETURN-01`; handoff `NME001-ORIGIN-S05-HQ01-F01-QA-HANDOFF-01`).
Both are archived unaltered under `s05/` in this repository.

**Method.** Deterministic recomputation in the QA container (outer identity, all 219 manifest bindings, embedded controls,
freeze equality, supervisor diff application, leak scan), then eight independent review lenses with two adversarial
refuters per material finding (76 agents, all read-only), then QA synthesis. The candidate was **not executed** here: the
Codex runtime paths and the 148,782,742-byte cache are absent, so every execution claim is checked against the returned
artifacts and code, not reproduced. Nothing in this review grants execution, evidence, or scientific authority.

## Classification

```yaml
result: NONBLOCKING_IMPROVEMENT
material_blockers: 0
qualification_of_f01_against_fixed_matrix: SUPPORTED_BY_RETURNED_RECORDS
recommended_next: ORIGIN_CHOOSES_PATH_A_OR_B_IN_SECTION_6
```

No MATERIAL_BLOCKER was found by any lens or survived verification. The frozen F01 harness passed the fixed eight-case
matrix with identical production bytes, the S04 failure class is caught at the named boundary, and the attempt-commit
boundary is coherent. The improvements below are real gaps in the production harness that the qualification driver
covers during HQ01 but that nothing would cover during a real run. They do not invalidate the qualification.

## 1. Deterministic verification — all PASS

| Check | Result |
|---|---|
| Outer size and SHA-256 vs handoff | match |
| `PACKAGE_MANIFEST.json`: 219 members, only itself excluded; 220 files on disk | 219/219 size+hash match, 0 unbound except the manifest |
| `controls/CHARTER.md` 23,009 B `fdca0010…`; `controls/S04_TERMINAL_STOP.json` 8,913 B `b7e127fe…`; `controls/STARTUP_ORDER.md` 17,510 B `3335ad00…` | all match known identities |
| `EXACT_DONOR_SUPERVISOR.py` vs donor `s02_supervisor.py` | byte-identical (`50998a20…`) |
| `SUPERVISOR_GENERALIZATION.diff` applied to donor | yields `production/supervisor.py` byte-exactly (`e218664f…`) |
| `freezes/F01/PRODUCTION_HARNESS.zip` vs `production/` | 5 members, byte-identical; `FROZEN_MANIFEST.json` per-file hashes match |
| F00 → F01 production change | `harness.py` only, +5 lines (272a273–277); supervisor, cache, inherit, schema, fixture unchanged |
| `production_sha256` `bf3c9811…` / `fixture_sha256` `723d254c…` | reproduce as sha256 of the canonical per-file identity map |
| Inputs map (20 hash-bound files) | identical across all eight descriptors except the per-case durable probe |
| Leak scan (OHLCV rows, registered fixture/vintage digests, key/token patterns) over all members and nested zips | zero hits; only `exchange_calendars` appears, as public-cache path names |
| Nexus source or checkpoint content in the return | none; `74ca21c1…` appears nowhere outside `controls/` |

## 2. Answers to the four charter §10 questions

**Q1 — Exact S04 stop and accepted checkpoint state preserved? YES.** The controls are the exact bytes. The checkpoint
was neither materialized nor referenced by any executed artifact; every commit and durable probe carries the fixture hash
in its `checkpoint_sha256` field (a field-name overload the RUN order must not inherit: there it must carry the real
checkpoint identity). Attempt accounting reconciles from disk: 4 `QUALIFICATION_CASE_COMMIT.json`, 0 `RUN_ATTEMPT_COMMIT`,
5 heartbeat STARTED lines (2+2+1), 6 supervisor invocations including QN-06's failed `Popen`, 9 outer invocations
(8 + QN-06 replay), 9 instantiations (8 F01 + 1 retired F00). Five predecessor attempts remain documented, not audited.

**Q2 — Same production bytes passed the fixed matrix without Nexus or protected contact? YES, as supported by the records.**
Independent reconciliation from artifacts alone gave zero mismatches across eleven checks for all eight cases: terminal
boundary equals the ledger and the charter row (QP-01/02 SUCCESS; QN-01 `WRITE_SET_READINESS_GATE` on a non-directory
`E`, the S04 class; QN-02 `INHERITED_CWD_GATE`; QN-03 `INHERITED_ENVIRONMENT_GATE`; QN-04 `EXACT_PUBLIC_CACHE_GATE` raised
by `production/cache.py` on the missing `wheels-v6/pypi/contourpy/…` link, not by the wrapper; QN-05
`SUPERVISED_CHILD_EXIT_GATE` exit 23 with no later stage; QN-06 `POSTCOMMIT_CHILD_SPAWN_GATE` then replay exit 73 with
`new_spawn_attempts` 0); commits 1/1/0/0/0/0/1/1; spawns 2/2/0/0/0/0/1/0; both JUnits exactly one `test_synthetic`
with no failure/error/skip; commit `descriptor_sha256` equals the shipped descriptor; expected artifact sets exact with
zero forbidden or unexpected members; success and stop records mutually exclusive. Every perturbation is imposed from
outside production (`qualification/driver.py:185-207, 300-301, 318-321`) and production contains no case-keyed branch.

**Q3 — Readiness derives from and observes the complete descriptor write set at the correct stages? YES for what
production owns, with a gap in completeness.** Construction, `lstat`, containment/separation, the
create/write/fsync/rename/parent-fsync/read/delete probe with residue check, reserved-target absence, parent probes for
`P`/`V` before their stages, managed-tree observation with undeclared-descendant rejection, and rejection of disagreeing
targets all map to `production/harness.py` (219–248, 250–278, 280–324, 71–91) and all iterate the descriptor's single
`write_set`; `write_set_sha256` in every readiness receipt recomputes exactly. The gap: a declared file that is missing
after its owning stage is not rejected by production (only observed if present, 273–277); non-managed roots
`E L O D TMP MPL` are never swept for undeclared writes; readiness entries carry no absolute target path; and the
whole-set final reconciliation exists only in `qualification/driver.py` (322–341, 361–372). In HQ01 the driver closed
every one of these. In a real run there is no driver.

**Q4 — Attempt-commit boundary coherent and non-gameable? Coherent; non-gameable within the returned evidence; four
residual vectors for a real run.** The commit is written strictly after every deterministic check and strictly before
the first spawn attempt, by exclusive create with file and parent fsync and exact readback, binding the descriptor hash,
readiness and precommit receipt identities, command, and environment; a pre-existing commit rejects re-entry before any
repair or spawn; a partially written commit counts as consumed (the fail-closed direction); QN-06 proves one commit, one
failed OS spawn, zero successful spawns, and replay rejection. Residual: the commit copies `production_sha256` and
`checkpoint_sha256` from the descriptor rather than recomputing them from realized bytes (closed for HQ01 by the inputs
map, which QA recomputed); the control tree `T` is not swept for undeclared members, and `python -B` does not prevent
loading a pre-existing `__pycache__` file; interpreter and uv are bound by path and version string only; `emit()`/`commit()`
write before checking the target's declared postcondition, which matters only for a mis-declared RUN descriptor.

## 3. The disclosed limitation — partly resolved by QA

The developer declared the interpreter-cache key `uv/interpreter-v4/e128016a93bda1d6/7f8106be2b9d4caa.msgpack` UNKNOWN in
derivation and prefix invariance. Using the return's own SeaHash routine (`qualification/uv_path_contract.py:27-32`,
which reproduces all five observed `uv-*.lock` basenames), the shard directory reproduces exactly as
`SeaHash(b"x86_64\xff" + b"Linux\xff" + b"6.18.35\xff") = e128016a93bda1d6`, i.e. machine, system, and **kernel release**
(`RUNTIME_PROVENANCE.json`: `Linux-6.18.35-x86_64-with-glibc2.39`; a neighbouring release string yields a different
name). The msgpack filename `7f8106be2b9d4caa` did not reproduce from any candidate encoding of the bound interpreter path
and remains underived. Consequences: prefix invariance of the shard is now explained, not merely observed; the key is
host-kernel dependent; and `production/harness.py:191-195` gates python path/version, implementation, system, machine,
and libc but not `platform.release()`. If a real run lands on a different kernel, the post-sync cache observation
(line 429) rejects the undeclared member before the commit (line 438), so the outcome is an **unconsumed pre-commit
engineering stop**, not a consumed attempt. Not blocking; the RUN order must bind the kernel release.

## 4. Findings — all NONBLOCKING_IMPROVEMENT (each survived at least one adversarial refuter; the appendix has both verdicts)

| # | Finding | Members | Real-run consequence | Fix |
|---|---|---|---|---|
| HQ-01 | Declared file missing after its owning stage is not rejected by production; only files that exist are observed | `production/harness.py:273-277`; `driver.py:123-129` | a mis-derived or unproduced output passes production silently | reject any `EXISTS_IF_STAGE_REACHED` entry absent after its stage |
| HQ-02 | No production sweep for undeclared writes in `E L O D TMP MPL` (nor `T`, `B`, `R`); only `Q`, `P`, `V` are checked | `harness.py:214, 231, 286-306`; `driver.py:322-341` | undeclared outputs certified by omission, the S04 family of defect | final whole-write-set reconciliation before `SUCCESS`: every entry observed PASS or ABSENT, any extra file rejected |
| HQ-03 | Readiness receipt entries carry no absolute target path; charter §6 item 5 is met only through `write_set_sha256` and the descriptor hash | `harness.py:232-248`; `readiness.json` | receipts not self-describing for an auditor | add `path` to every receipt entry |
| HQ-04 | Commit provenance by declaration: tree digests copied from the descriptor; launcher does not bind its own executing identity; interpreter/uv bound by path+version | `harness.py:335-336, 191-195, 393-396` | a real-run commit could carry declared, not observed, harness identity | recompute the production tree digest from realized `T/production`, record `identity(sys.argv[0])` and interpreter/uv binary hashes in the commit |
| HQ-05 | Interpreter-cache shard key depends on kernel release, which is not gated | `uv_path_contract.py:27-32`; `harness.py:191-195` | avoidable pre-commit stop on a different host kernel | bind `platform.release()` in the descriptor runtime block; derive the shard key prospectively |
| HQ-06 | Supervisor now relays child output through pipes read in 64 KiB blocking chunks; the donor wrote the log directly, so stdout and `supervisor.log` stay empty until exit or 64 KiB | `production/supervisor.py:221-222, 258-265`; donor 146-147 | no live child output during a long hermetic run; heartbeat is unaffected | line-wise or unbuffered relay |
| HQ-07 | `reader.join()` after the EXITED heartbeat has no timeout; a grandchild inheriting the pipe blocks the supervisor indefinitely | `supervisor.py:295-315` | hang after child exit if the Nexus suite leaves a nested process | close pipes / join with timeout after EXITED |
| HQ-08 | Concurrent launch or a second re-entry leaves a non-truthful or missing stop record (loser's STOP suppresses the winner's; `replay_rejection` emit sits outside the `try`, so a second re-entry exits 1 with a traceback rather than 73) | `harness.py:328-329, 383-387, 475` | spawning stays fail-closed; the record can mislead | entry-level lock; emit replay rejection inside the handler |
| HQ-09 | `emit()`/`commit()` write the target before checking its declared postcondition | `harness.py:118-129, 341-343` | a mis-declared RUN descriptor could materialize `RUN_ATTEMPT_COMMIT` before the gate fires | check `after` before `write_exclusive` |
| HQ-10 | E-absent precondition for the positive cases is constructed, not observed; `initial_evidence_state` in `invocation.json` is copied from expectation | `driver.py:276-279, 308`; `harness.py:225-234` | pre-state of precommit roots unrecorded | record created-vs-pre-existing in the readiness receipt |
| HQ-11 | `SANITIZATION.json` enumerates no members, hashes, or patterns; its count (226) is reconcilable only by inference | `SANITIZATION.json` | scan coverage not auditable | enumerate scanned members and the pattern set |

## 5. Observations (no action requested)

- Supervision topology changed from one 300 s supervisor process over the whole donor sequence to in-process per-stage
  supervision of the collection and test children with a hard-coded 30 s interval. The long prelaunch (481 MB cache
  bootstrap, offline sync) runs without heartbeat. Consistent with the charter; a real-run operator should know.
- QP-02's "different absolute prefix" varies every component and the depth below the exclusive lease parent; a stronger
  variation would have breached charter §11. Accepted as the strongest permitted variation.
- QN-05 fails at the collection stage, not the JUnit stage; the charter's disjunctive wording ("child/test command that
  returns nonzero") permits this and the test-stage path uses the same gate code.
- `LEASE_CLAIM.json` is self-descriptive (no claim-file identity or readback digest), and every outer invocation ran as
  PID 7 in a fresh PID namespace, so process-level quiescence is structurally near-vacuous in this sandbox. Writer
  exclusivity for a real run must rest on the durable exclusive-create claim, not on process observation.
- The four qualification helpers are copied into `T/qualification` and hash-bound in every case, including positives;
  the frozen production bundle contains only the five production members. Not a violation.
- The read-only archive is staged at `/workspace/scratch/cbd6528b11d8/inputs/`, outside the lease parent; the driver
  re-hashes it before every case, so QN-05's PASS shows it intact after QN-04's perturbation.
- The handoff relay to QA carried a populated `Filename:` line. Origin's text-artifact fix worked.

## 6. Recommendation

The charter leaves one repair-and-refreeze cycle (1 of 2 used). Two acceptable paths:

- **Path A — proceed with F01 as qualified.** Issue the S05 RUN01 order against the frozen F01 bytes and move HQ-01 to
  HQ-05 into that order's acceptance requirements: the reviewer recomputes the production tree digest from the returned
  `T/production` bytes; the reviewer performs the whole-write-set reconciliation over the returned receipts that
  production does not perform; the descriptor binds the kernel release and the prospectively derived shard key; the
  commit's `checkpoint_sha256` carries the real checkpoint identity. Accept HQ-06 to HQ-09 as residual risk.
- **Path B — spend the remaining cycle.** One bounded production change set (HQ-01, HQ-02, HQ-03, HQ-04, HQ-05, HQ-06,
  HQ-07, HQ-09), then re-run the identical eight cases with no new cases. All of these fall inside charter §8's
  permitted work ("derive readiness from the complete realized write set", the supervisor's logging semantics, the
  prospective commit semantics, closing the disclosed unknown). If that cycle fails, the charter's defined stop applies.

QA's preference is Path B, because HQ-01 and HQ-02 are the same family as the S04 defect (a state certified without full
observation), and the next real run consumes an attempt. Path A is defensible if Origin prefers to keep the qualified
bytes frozen and shift those checks to review. Origin adjudicates.

## 7. Not verifiable from the returned bytes

Actual execution and timing; contents of `T` at run time beyond the 20 declared inputs; the bytes of `bootstrap_uv_cache.py`
and the cache archive; interpreter and uv binary hashes; the external durability of `durable_probe_readback.json`; the
lease claim, quiescence observation, and Library custody identities (including the outer zip binding, which the return
correctly does not claim); F00's driver and descriptor bytes; the msgpack cache-key derivation.

## 8. Role disclosure and disposition

QA's earlier continuity and harness-failure advice informed the charter. No QA code is present in the return and no
QA repository content was used by the developer (checked). This review shaped no harness bytes.

```yaml
candidate_sha256: 4c6efd4e2564500efc542e26610d67a9059db4ce236e4dea08f66a34ce86a3bf
classification: NONBLOCKING_IMPROVEMENT
material_blockers: 0
nonblocking_improvements: 11
q1_s04_and_checkpoint_preserved: YES
q2_same_bytes_passed_fixed_matrix_no_protected_contact: YES_PER_RECORDS
q3_readiness_from_complete_write_set: YES_WITH_COMPLETENESS_GAP_HQ01_HQ02_HQ03
q4_commit_boundary_coherent_nongameable: COHERENT_RESIDUAL_HQ04_HQ08_HQ09
disclosed_limitation: PARTLY_RESOLVED_SHARD_KEY_IS_KERNEL_RELEASE_DEPENDENT
real_run_authority_granted: NONE
qa_evidence_authority: NONE
```
