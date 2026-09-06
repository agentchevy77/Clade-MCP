# NME-001 Third-Party QA — S05-HQ01 Continuity Packet Verification and Post-Compaction Reconciliation (2026-09-06)

Packet: `NME001_S05_HQ01_SANITIZED_CONTROL_CONTINUITY_PACKET_20260906.zip`, 103,630 bytes,
SHA-256 `ced7d1a4a7d3bf4cd377c9fdcc826f7b885c4201f08775edde026c7e6915a1d5` (archived at `s05/`).
Method: deterministic recomputation in the QA container. This return is advisory; it grants no authority.

## 1. Packet integrity — PASS

| Check | Result |
|---|---|
| Outer size and SHA-256 vs Origin's relay | match |
| `SHA256SUMS.txt` (9 members) | 9/9 OK |
| Charter 23,009 B `fdca0010…` | match, first time held as bytes |
| Identity bridge 7,411 B `68299711…` | match (v1, as previously reviewed) |
| Donor bundle v1 67,162 B `ac85751e…3f390e9c`, 15 members | match |
| Donor internal bindings stated in charter §5 (capsule `78396a85…`, component manifest `226458f2…`, harness diff `5fcb15df…`, supervisor `50998a20…`) | 4/4 match |
| Component manifest `harness_components` (10) vs bundle members | 10/10 size+SHA-256 match |
| Lease-02 stop 8,624 B `8f51386a…`; Lease-03 stop 4,856 B `b073a517…`; Lease-04 stop 8,913 B `b7e127fe…` | all match the identities relayed at stop time |
| Leak scan (OHLCV row patterns, registered fixture/vintage digests, credential patterns) | zero hits |

## 2. Independent confirmation of the S04 exact-cause finding

From the donor bytes, not from any summary: `s04_sequence.sh` redirects stdout to
`$run_dir/evidence/s04_hermetic_collection.txt` (line 79) and writes three further evidence
targets (lines 82, 88, 90); no donor member creates `$run_dir/evidence`. The only `mkdir`
calls in the harness create the protected `C` and `RAW` roots (`s04_placement_controller.py`
221–223). Charter §2's classification `INCOMPLETE_REALIZED_WRITE_SET` is confirmed.

## 3. Reconciliation of QA's compacted understanding against Origin's current-state record

No conflict found. Specifically consistent: S04 checkpoint identity (`74ca21c1…`, tree
`d700092b…`, 981/1,042 inventories) equals QA's independent S04 gate reproduction; S04 RUN01
launched once and consumed; S05-HQ01 authorized, lease unclaimed, no run reserved; Origin's
rejection of QA's earlier cwd hypothesis for Lease-04 stands as recorded. Two items QA holds
only as reported, never as bytes: the S02 lease-by-lease ledger (three consumed) and the S01
predecessor disposition. QA accepts the documented total of five consumed attempts as
Origin's record, not as independently verified.

## 4. Findings

- **QA-S05-01 (NONBLOCKING_IMPROVEMENT, recurrent).** The relay message to QA again carried a
  blank `Filename:` line — the third occurrence. The packet's own records are complete; the
  defect is in Origin's relay template. Recommend the Product Owner refuse to forward any
  relay with an empty identity field.
- **QA-S05-02 (open logistics, potential preflight block).** The 148,782,742-byte uv-cache
  archive has no defined delivery route into the outside Developer's session. It exceeds
  GitHub's per-file limit, Origin cannot push to GitHub, and charter §5 forbids network
  dependency acquisition. Resolve before the lease is claimed: either a Product Owner upload
  into the Developer session, or a hash-bound release asset / LFS object per the bridge's
  LFS rule. Test the route with the exact bytes, then bind the observed identity.
- **QA-S05-03 (NONBLOCKING_IMPROVEMENT, QA-side, fixed).** QA's Developer brief §3–§4 told the
  Developer how to collect Nexus tests and reconstruct the checkpoint; charter §11 forbids
  both during HQ01. Corrected in this commit; the recipe is now marked as QA's reproduction
  record only.

## 5. Charter observations for Origin (no modification requested)

The charter is internally consistent with the stop records and the donor. Its qualification
matrix (§7) covers the three S04 failure classes directly (QN-01 write-root, QN-02 cwd,
QN-04 cache symlink) and adds the commit-boundary cases QA had recommended. The fourth
class QA tracked, `__pycache__` digest drift, is outside HQ01 by construction (no Nexus
source is opened) and should reappear as a real-run precondition in the later S05 RUN01 order.

## 6. Disposition

```yaml
packet_integrity: PASS
licensed_data_exclusion: PASS
donor_bindings: PASS_15_MEMBERS_10_COMPONENTS
s04_exact_cause: INDEPENDENTLY_CONFIRMED_FROM_DONOR_BYTES
qa_compacted_state_vs_origin_record: RECONCILED_NO_CONFLICT
open_item: UV_CACHE_DELIVERY_ROUTE_TO_DEVELOPER_SESSION
qa_evidence_authority: NONE
```
