# Independent QA Reproduction of EPOCH07-S04 Checkpoint Gates

Date: 2026-09-05 · Authority: NONE (corroboration only; grants no execution, evidence, or promotion authority)

Method: QA applied its own adopted diff (`45ec8717…`, 3,348 B) to an isolated copy of checkpoint v3
(`c046792f…`) and recomputed every gate the S04 Developer reported, using the project's own tooling
(`s02_checkpoint._source_tree_identity`, the exact inventory commands from `S02_TEST_INVENTORIES.json`).
Bytecode residue was removed before source-tree hashing (`__pycache__` under collected paths alters the digest —
worth noting for any future reviewer environment).

| Gate | Reported by S04 Developer | QA reproduction | Match |
|---|---|---|---|
| v3 source tree (unpatched) | `8f53575b…` | `8f53575b…` | PASS |
| S04 projected source tree (patched) | `d700092b…` | `d700092b…` | PASS |
| v3 hermetic inventory | 980 / `8c9d737f…` | 980 / `8c9d737f…` | PASS |
| v3 licensed-inclusive inventory | 1,041 / `d6adcdfc…` | 1,041 / `d6adcdfc…` | PASS |
| S04 hermetic inventory | 981 / `46dde6a2…` | 981 / `46dde6a2…` | PASS |
| S04 licensed-inclusive inventory | 1,042 / `137203ed…` | 1,042 / `137203ed…` | PASS |
| Licensed-only difference | 61 | 61 | PASS |

Post-patch file identities for the reviewer's byte-level comparison (checkpoint v3 paths):

```text
6c96e64add567354f3a3f841056bb4297554c1f0abe4904f99f7e0c705c1d55d  src/nexus_nme001/s02_execution.py
96043989bf5a7600248d4022d592d117c126760f9de02610e379d057376acd47  tests/test_s02_execution.py
```

Not reproduced by QA (not held): the published S04 checkpoint bytes (`74ca21c1…`, 4,001,839 B, manifest
`1f59b080…`, 171+1 paths). QA notes the path count grew by two beyond the two patched files; the role-separated
reviewer should confirm those additions are exactly the re-frozen inventory/overlay records and that the
remaining 167 members are byte-identical to v3, as the Developer claims. Nothing here authorizes a run identity,
licensed input, or scientific execution.
