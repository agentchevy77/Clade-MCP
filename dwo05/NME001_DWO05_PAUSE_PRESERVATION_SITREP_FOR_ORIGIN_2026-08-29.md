# NME-001 DWO-05 — Pause/Preservation SITREP for Origin

Date: 2026-08-29  
Prepared for: Project Nexus Origin  
Current disposition: `PAUSED_PRESERVED_FOR_REGROUPING`  
Scientific result: `INSUFFICIENT_EVIDENCE`  
Evidence/predictive/trading authority: `NONE`

## 1. Executive situation

DWO-05 development has been paused before a fourth package attempt.

The engineering source is in substantially better condition than the DWO-04
parent and retains the three ordered DWO-05 repairs plus extensive fail-closed
edge hardening. Both complete stopped test lanes pass. No scientific model,
feature, target, symbol, timeframe, holdout, prediction, alert, execution, or
trading behavior was changed.

The remaining blocker is not a demonstrated code or Hatch build-policy defect.
The strongest supported diagnosis is a managed-workspace filesystem behavior:
paths deliberately removed during the actual-root `NO_RAW_DIRECTORY` proof are
asynchronously recreated from stale workspace state. The release guard
correctly treats that recreation as a failure and refuses to freeze a
candidate.

No DWO-05 release-candidate ZIP, candidate-sidecar manifest, or release receipt
exists. The preservation checkpoint described below is not a candidate. DWO-04
remains the retained engineering foundation pending DWO-05.

## 2. Governing identities

| Item | Bytes | SHA-256 |
|---|---:|---|
| Exact DWO-05 order | 21,766 | `38de0b5f369c15c524657ca5052b73d9ce7d9525d7e3c8cfc31d4ea7e503699c` |
| Preserved DWO-04 parent ZIP | 1,800,260 | `a08a2c9df9df6d34267e4c0bb0afdd0acfc78c1d98b29de48964f9698b0619c6` |
| DWO-05 output-reconciliation artifact | 10,524 | `6938e5265e13d3d3079698d5aabb701cdebd8a132d41dd3361556ccde2a91223` |
| Final stopped hermetic JUnit | 135,230 | `80feb11774be58fd74e2c60b487009dcc100f52a1a243bcf05fd21f63a5f328b` |
| Final stopped licensed JUnit | 144,229 | `cbc075f49e29caddbbcd212078ca565a6858fd7cb8c5cda0d3c20992506d1efe` |
| Current DWO-04→paused-worktree patch | 505,877 | `af1e0870651444197fdbe03e03438dbc88eb8728a40401a1451acc5af2fe1d9f` |

Named-test inventory bindings:

- hermetic: 922 tests, SHA-256
  `7baf3ae855cc94a15ca26c484e7b2fb324024b9a6d5fe68262e8f3c9a5e2dc2c`;
- licensed: 983 tests, SHA-256
  `15138cc5ffc83929e566b1024270cd62e6ec8d70d57c1500cf28763cbd3ea12e`.

## 3. Development results retained

Final stopped executions:

- hermetic: **922/922 PASS**, 61 licensed-only cases correctly deselected,
  zero failures, errors, or skips disguised as PASS;
- licensed: **983/983 PASS**, zero failures, errors, or skips;
- focused release/distribution regression after matrix-first ordering:
  **133 PASS**, one licensed-only case deselected;
- exact DWO-04 historical release regression: **53/53 PASS**.

The paused source retains:

1. explicit ordinary sdist exclusion of the complete `data/raw/**` tree;
2. wheel/sdist exclusion of `__pycache__`, `.pyc`, and `.pyo` artifacts;
3. filename, exact-payload, full-row, bounded raw/Base64/hex fragment,
   cross-member, metadata, trailing-byte, renamed-container, and nested-archive
   scanning;
4. strict fit/prediction/scored/common-origin reconciliation, including exact
   types, identities, fold relations, probability vectors, and mandatory
   baselines;
5. strict JSON Boolean/integer separation in release verification;
6. archived `pyproject.toml` policy parsing and exact binding of all build lanes
   to the candidate policy bytes;
7. a nonblocking cross-process raw-state lock;
8. bounded canonical residue inventory on any unexpected raw-state recreation;
9. exact inclusion and parent-byte binding of the six transitive DWO-03
   regression dependencies; and
10. package-local, root-bound, single-use matrix-first ordering so the complete
    three-condition actual-root build proof runs before the long fresh licensed
    regression.

## 4. Package-attempt chronology

### Attempt 1 — sealed reproduction exposed missing transitive history

The first controlled development package attempt completed the locked distribution
matrix, deterministic freeze, and initial candidate verification. Sealed
reproduction then returned:

`884 passed, 61 deselected, 30 errors`

All 30 errors were setup failures in `tests/test_release_dwo03.py`. DWO-05 had
included that historical test module but omitted its six required historical
DWO-03 artifacts/JUnits. The defect was repaired by adding and exact-parent
binding those six dependencies. Raw restoration passed; no partial candidate or
sidecar survived.

### Attempt 2 — unexpected raw-tree recreation

After the transitive repair and full retest, the second package attempt passed
the fresh licensed rerun but failed closed in `NO_RAW_DIRECTORY` because a
nonempty raw tree reappeared. This occurred before residue diagnostics existed,
so its exact contents were not claimed. Exact-three restoration passed and no
candidate or sidecar remained.

An isolated copied-root ordinary build subsequently left `data/raw` absent,
which argues against Hatch or the source-distribution exclusion as the cause.
Deleted raw-recovery and freeze-stage paths also reappeared together in a stale
filesystem replay batch.

### Attempt 3 — root-owned run captured the replay exactly

The third package attempt ran from the root executor and again failed closed in
the actual-root no-raw condition. The new bounded residue inventory captured
exactly the three registered fixture files:

| Fixture | Bytes | SHA-256 |
|---|---:|---|
| Untouched | 1,453,678 | `ee9391284564b85e8875aa95be51eb74898d38455e87e9e5335c07ad79214985` |
| Split check | 1,518,236 | `10231f1451f79a09b8242528d78adf239bf6c55c2ff014735d9754a9f1ad519d` |
| Corporate-action check | 2,066,778 | `11215bd7ce1fec4d8fb2b92c3437e3085de67a909a41a9324ddf726a1f86a5c8` |

This is strong evidence consistent with stale exact-fixture path replay. The
isolated copied-root result weighs against an ordinary build generating market
CSVs. The canonical root and a separately held recovery copy both reverified
exact afterward. No output survived.

### Attempt 4 — not launched

A fourth attempt was designed to isolate the root from workspace replay. Its
initial persistent-delete preflight itself demonstrated the same behavior:
deleted fixture and old staging paths returned at the next executor boundary.
No fourth package command ran.

Matrix-first ordering was then added and fully retested. A more elaborate
workaround—atomic relocation of the complete project root, creation of a fresh
path-correct offline virtual environment, package execution, quarantine of any
replayed original tree, and exact restoration—was technically reviewed but not
executed. Development was paused before taking that larger operational step.

## 5. Current workspace/custody caveats

- The current source whitelist contains 138
  source/governance/configuration entries.
- The on-disk release patch is stale by one final ledger-only edit: 505,707
  bytes, SHA-256
  `1e274c16e055ebdc879dcd7dc067b4178a09b9e4b7a02623200b7e06fe9bc0bd`.
- The preservation package therefore carries a separately generated current
  paused-worktree patch: 505,877 bytes, SHA-256
  `af1e0870651444197fdbe03e03438dbc88eb8728a40401a1451acc5af2fe1d9f`.
- Stale freeze-stage directories and exact duplicate recovery copies can recur
  in this managed scratch environment. They are not deliverables and should be
  reconciled only after materialization into an isolated filesystem.
- The three licensed CSVs are not present in the preservation ZIP and were not
  saved as deliverables.

## 6. Preservation package

| Artifact | Bytes | SHA-256 | Library ID |
|---|---:|---|---|
| `NME-001-DWO-05_PAUSE_CHECKPOINT_2026-08-29.zip` | 1,358,185 | `dd02872e2c5911b1020b35db81743bae360e0a423f7293a43e4663c6a0e7d1f6` | `libfile_1fc4cab98f508191b4cf9980c81991a1` |
| `NME-001-DWO-05_PAUSE_CHECKPOINT_MANIFEST_2026-08-29.json` | 1,215 | `b2f43b6c616282bf65fdd19f237899288a90f6b0ac7e60098353239a35f4f30e` | `libfile_503ba1d4336881919f4ff316f936032c` |
| `NME-001-DWO-05_PAUSE_AND_REGROUP_NOTE_2026-08-29.md` | 5,840 | `a3caaf9fbc0fc678a2eca241dcfbbd0fc94a142490702d7417321749bd07b15f` | `libfile_90e869d1fdf48191940f7a388f51f928` |
| `NME-001-DWO-04_TO_PAUSED_DWO-05.patch` | 505,877 | `af1e0870651444197fdbe03e03438dbc88eb8728a40401a1451acc5af2fe1d9f` | `libfile_fcbad7df9fc481918959b2eedc53e0c5` |
| `NME-001-DWO-05_PAUSE_CHECKPOINT_SHA256SUMS_2026-08-29.txt` | 458 | `ec1823db32104b299e562aad123b229bbe299463658395d07118a23e5ee6674f` | `libfile_40dc1b1507408191a649e05391f72889` |

Checkpoint verification:

- 145 unique deterministic ZIP members;
- ZIP integrity PASS;
- zero `data/raw` members;
- zero licensed CSV filename hits;
- zero exact-payload hits;
- zero complete-row hits;
- zero bounded-fragment hits;
- candidate/predictive/trading authority all `NONE`.

## 7. Recommended Origin decision

Recommended disposition:

`PAUSE_PRESERVE_AND_REGROUP — RESUME_RELEASE_ONLY_IN_ISOLATED_EXECUTOR`

Preferred restart path:

1. materialize and hash-verify the preservation checkpoint in an ordinary,
   isolated filesystem with no asynchronous path restoration;
2. only after Origin confirms both the isolated executor and licensed-fixture
   custody/movement authority, restore the same three fixtures separately at
   their registered paths under their existing zero-vote
   regression/exclusion authority;
3. regenerate the canonical DWO-04→DWO-05 patch;
4. rerun both complete JUnits;
5. run the same three-condition/two-build actual-root matrix;
6. run one package/verify/sealed-reproduce sequence;
7. obtain final independent non-author frozen-package QA; and
8. return at most
   `READY_FOR_INDEPENDENT_REVIEW_WITH_RESERVED_ACTIONS_HELD`.

Recommendation: do not create a DWO-06 merely for this environmental release
issue. If an isolated executor is unavailable, Origin should explicitly decide
whether the atomic whole-project relocation procedure is acceptable before
work resumes.

## 8. Exact authority state

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
kibot_inquiry_authority: AUTHORIZED_SEPARATELY
kibot_inquiry_execution: NOT_SENT
dwo05_provider_contact_scope: NONE
massive_contact_any_form: NOT_AUTHORIZED
account_trial_purchase_credentials_download_ingestion: HOLD
```

## 9. Minimal handoff text

Send Origin:

> DWO-05 is paused and preserved, not rejected. The engineering source passes
> 922/922 hermetic and 983/983 licensed tests, but no DWO-05 candidate was
> frozen because the managed workspace asynchronously replayed the exact three
> licensed fixture paths during the actual-root no-raw proof. The guard failed
> closed correctly. Process
> `NME001_DWO05_PAUSE_PRESERVATION_SITREP_FOR_ORIGIN_2026-08-29.md` together
> with the pause-checkpoint manifest. Prefer resuming release closure in an
> isolated executor; do not weaken the matrix, elevate authority, or create a
> DWO-06 solely for this environmental issue.
