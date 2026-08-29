# DWO-04 deterministic reproduction contract

This contract applies only to `NME001-DWO-04-CANDIDATE` version `0.3.1`,
protocol `1.2.1`, and partition design `1.2.0`. All evidence is engineering
regression evidence with authority `NONE`. It does not open the historical
final, run real v1.2.1 development, ingest new data, or contact a provider.

## Frozen named-test identities

The final four collection bindings are computed only after every DWO-04 repair
and test lane has merged:

```bash
uv run --locked --extra dev python -m nexus_nme001.release_dwo04 \
  collection-bindings --project-root .
```

An independent reviewer freezes the returned hermetic and licensed counts and
SHA-256 digests in `release_dwo04.py`. Packaging and verification fail while
those bindings are absent and fail after any named test is deleted, renamed,
or added without an explicit re-freeze.

## Candidate-only hermetic lane

From the candidate root under Python 3.12 and the frozen lock:

```bash
uv run --locked --extra dev pytest -q \
  --junitxml=pytest_dwo04_hermetic.xml
```

Without `--licensed-fixtures`, pytest deselects the externally held licensed
cases instead of calling them passes or skips. The packager requires a complete
all-pass/no-skip JUnit set, reconciles it to live collection and the independent
frozen collection binding, canonicalizes away arbitrary test output, and then
reruns the exact command from the sealed ZIP.

## Separately held licensed regression

This lane remains the preserved v1.0.1 zero-vote regression. It may read only
the same three previously sealed TradingView files at their exact registered
destinations, after `licensed_fixtures.py` verifies both each CSV and its frozen
receipt by size and SHA-256. The files are not copied into the candidate.

```bash
uv run --locked --extra dev pytest -q --licensed-fixtures \
  --junitxml=pytest_dwo04_licensed.xml
```

The licensed run has no scientific, design, formal, predictive, or trading
vote. Missing, partial, misplaced, symlinked, size-mismatched,
receipt-mismatched, or byte-mismatched fixture sets fail before execution and
cannot produce this release. Packaging requires the complete licensed PASS
JUnit, verifies the fixtures, reruns the exact locked licensed command,
verifies the fixtures again immediately before freezing, and proves all
selected project bytes remained unchanged. The canonical licensed JUnit must
be a strict named-case superset of the hermetic evidence.

## Package, verify, and reproduce

```bash
uv run --locked --extra dev python -m nexus_nme001.release_dwo04 package \
  --project-root . \
  --hermetic-junit pytest_dwo04_hermetic.xml \
  --licensed-junit pytest_dwo04_licensed.xml \
  --output NME-001-DWO-04_UNREVIEWED_RESEARCH_CANDIDATE.zip

uv run --locked --extra dev python -m nexus_nme001.release_dwo04 verify \
  --package NME-001-DWO-04_UNREVIEWED_RESEARCH_CANDIDATE.zip

uv run --locked --extra dev python -m nexus_nme001.release_dwo04 reproduce \
  --package NME-001-DWO-04_UNREVIEWED_RESEARCH_CANDIDATE.zip
```

Packaging publishes exactly three sibling outputs:

- `NME-001-DWO-04_UNREVIEWED_RESEARCH_CANDIDATE.zip`
- `NME-001-DWO-04_CANDIDATE_MANIFEST.json`
- `NME-001-DWO-04_CANDIDATE_RECEIPT.json`

The external manifest binds the ZIP, embedded manifest, authority record, and
sealed reproduction result. The receipt binds the ZIP and external manifest.
Both are canonical JSON and deliberately avoid self-hash cycles.

Before freezing the ZIP, the release tool also performs two fresh locked,
offline builds on independent staged source trees with a fixed
`SOURCE_DATE_EPOCH`. It requires the wheel and source distribution inventories,
hashes, sizes, and bytes to be identical. Their exact identities and equality
result are recorded in the embedded manifest and independently recomputed by
the verifier.

The candidate patch is applied to the exact preserved DWO-03 ZIP baseline. A
post-apply snapshot must match every `README.md`, project/lock, `src/`, `tests/`,
`config/`, `governance/`, `docs/`, and `data/receipts/` path and byte in the
DWO-04 candidate. The patch itself and generated artifacts/manifests/JUnit/ZIP
outputs are excluded to avoid self-reference. The manifest binds the exact
baseline, patch, reconstructed file count, and complete snapshot digest.
The verifier also rebuilds the entire patch from an isolated Git commit of the
exact DWO-03 ZIP using fixed full-index, binary, no-rename options and requires
byte equality. Trailing payload, undeclared copy/rename headers, or any other
content not emitted by that canonical regeneration is rejected.

Release verification also pins literal byte counts and SHA-256 identities for
the active protocol and configuration, protocol diff, exposure ledger,
historical-final identity file, corrected capacity note, and both unchanged
`PREPARED_NOT_SENT` Kibot documents. Consistent edits to a document and its
dynamic in-project reference therefore cannot silently redefine the release.

## Historical preservation and data exclusions

The release carries byte-identical copies of the accepted DWO-03 candidate,
external manifest, receipt, embedded manifest, and both named-test evidence
files under `artifacts/historical_dwo03/` and
`artifacts/verification/`. The verifier pins their accepted hashes and sizes,
reconciles the three evidence files to the preserved ZIP, and verifies the
sidecar bindings. Protocol v1.2.0, frozen configuration v1.2.0, exposure ledger
v1.0.0, and the DWO-02-to-DWO-03 patch are separately pinned as historical
records.

The exact licensed attrition reconciliation is included at
`artifacts/verification/NME001_DWO04_LICENSED_ATTRITION_RECONCILIATION.json`.
Its canonical bytes are pinned and must report zero `MODEL_FULL` fits, nine
`TECHNICAL_NOT_ISSUED`, zero `OOD_ABSTAIN`, zero issued/scorable rows, a complete
issued/OOD-to-successful-FIT join, and all acquisition clearances false.

Raw market data, unsupported archive/container types, bulk market data, final
outputs, and new-confirmation data are prohibited. Source/test files are
limited to Python, configuration/receipts to JSON, governance to the exact
textual formats in use, and docs to Markdown or the one canonical patch. Only
the exact pinned historical DWO-03 ZIP may be nested. The three receipt paths,
sizes, and hashes are exact and no extra receipt is permitted. The packager
also rejects any member whose bytes equal a registered licensed fixture even
if it is renamed or given another extension. While the exact fixtures are
present, packaging additionally scans allowed textual content and member-name
bytes for complete raw rows of at least 24 bytes and exactly confirmed
contiguous 256-byte normalized-representation windows: raw bytes, every Base64 raw-byte
phase after ASCII-whitespace removal, and lowercase-normalized hex after all
non-hex characters are removed. Lexicographically sorted member concatenation
and structural-name separator removal close bounded split-member/name paths.
The manifest binds the exact methods, thresholds, fixture identities, complete
inventory digest, scanned-text subset and byte count, and the exact pinned
historical or machine-evidence artifacts whose content is verified separately.
The generated canonical hermetic and licensed JUnits are part of the content
scan, closing dynamic collected-name/parameter-ID channels. This is
fixture-backed package-time evidence with authority `NONE`; standalone
`verify` checks the bound record and inventory but cannot recreate substring
matching without the separately held licensed fixture bytes. Supplied JUnit
files cannot also enter through the ordinary project inventory. ZIP names,
normalized names, member types, metadata, sizes, compression ratios, ordering,
and canonical encoding are independently verified before any evidence is
trusted.
