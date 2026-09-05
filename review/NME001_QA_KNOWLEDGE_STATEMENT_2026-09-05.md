# Third-Party QA — Knowledge State Statement for Nexus Onboarding

Date: 2026-09-05
Role held: independent third-party QA (documentary + recomputation lane), outside the Nexus role set
Authority: NONE (no evidence, predictive, trading, alerting, automated-action, or final-opening authority; never held custody of licensed bytes)
Purpose: tell the current Nexus roles exactly what this reviewer knows, has verified, holds, and does not know, so orientation can fill the gaps rather than re-explain the known.

## 1. Knowledge horizon

Continuous knowledge from the DWO-03 acceptance (2026-08-29) through the TVCA
successor plan REV-02 (2026-09-02). **Nothing after 2026-09-02 is known.**
Specifically unknown: Origin V2 (character-limited), Developer V3, and the
Research, Steward, and TradingView Lab roles — their charters, authorities,
handoff formats, and where they sit in the order/acceptance chain.

## 2. Roles as understood at the 2026-09-02 horizon

| Role | Understood function |
|---|---|
| Product Owner (human) | Holds all external-contact, account, purchase, custody-movement, real-data, executor, and final-opening authority; ratifies orders (recorded "Ok lets proceed" for the Kibot acquisition) |
| Origin | Independent acceptance review; issues hash-bound work orders (DWO-03→04→05, SEO-01, TVCA REV-01/02); accepts/holds Developer returns |
| Developer | Implements orders in an isolated executor with internal non-author review; raw-blind under TVCA-S01 |
| Licensed Custodian / Lab operator / custody-confined QA | Named in REV-02 as separately recorded custody roles (not yet observed in action) |
| Third-party QA (this reviewer) | Delta reviews on request; returns PASS/HOLD/REJECT with exact artifact references |

## 3. Project state as last known (2026-09-02)

- Experiment NME-001: SPY 5-minute RTH level-reaction research; protocol v1.2.2; partition design 1.2.0; historical final 2022-06-22..2024-12-31 (630 sessions, `423f3ad6…`) unopened.
- DWO-04 accepted (release parent retained). DWO-05: paused after three fail-closed packaging attempts (workspace path replay); clean-resumption layer (`8cb8151a…`) accepted by Origin, infrastructure frozen; no DWO-05 candidate exists; licensed lane and release matrix NOT_RUN_NOT_AUTHORIZED.
- Kibot SPY 1-minute vintage `62a2383a…` purchased ($82.46, PO-authorized), post-delivery audit ACCEPT_WITH_BOUNDED_EXCLUSIONS; limitation FEED_VENUE_CONDITION_ODDLOT_POLICY_UNDISCLOSED.
- SEO-01 (first real licensed stage=development execution) authorized and in progress at last sight; no frozen result received by QA.
- Legacy TradingView corporate-action fixture (2,066,778 B, `11215bd7…`) unrecoverable; successor plan TVCA-S01 REV-02 reviewed by QA: PASS on all nine questions, two P3 advisories (acausal binding clause; proportionality of a sole-attempt live capture for zero-vote evidence).
- Every authority field last seen: NONE/HOLD as recorded in the delta package and REV-02 §11.

## 4. What this reviewer has independently verified (not taken on faith)

- All 16 original submitted files and every later artifact hash-match every identity claimed for them anywhere in the record, including documents reconstructed from patch hunks (DWO-05 order `38de0b5f…`, protocol v1.2.2 `3e2ba3ef…`).
- Full XNYS calendar layer rebuilt from `exchange_calendars` 4.11.1: 412/415 sessions and half-days, all four ledger range identities, 6,734-session protocol calendar, 630-session final identity, zero overlap with opened sessions, 7,146 ordinary + 62 half-day sessions 1998–2026, 559,992 expected five-minute windows.
- Statistics: Clopper–Pearson 9/84 bounds; nine-session identity hash `c7f252dd…`.
- Both DWO-05 fixture-free JUnits: 922 unique cases, 0 failures/errors/skips, identical named sets across Developer and Origin runs; historical 983-case licensed JUnit identity `cbc075f4…`.
- Every Kibot audit aggregate recomputed from the raw ledgers (2,772,235 rows; 559,719 observed windows; 18,608 partial; 273 empty over 56 sessions; 11 extreme sessions; final incompletes 2023-12-29 / 2024-06-03 / 2024-12-31; all artifact hashes).
- Code review (22+18 agents, adversarially verified): DWO-05 §B–§E repairs present (28/28 items), DWO-04 fit-before-OOD acceptance re-confirmed, protocol v1.2.1→v1.2.2 byte-faithful with no scientific change, environmental-replay diagnosis survived refutation, zero licensed content in any patch or package.
- TVCA REV-02: Pine carrier reconstructs to 892 B / `577eaaee…`; six ex-dates valid sessions; receipt amounts and listing identity match.

## 5. Standing QA findings still open at the horizon

1. SEO-01 stage=development lacked an explicit Product Owner ratification record (DELTA-X01) — a one-line PO ratification was requested.
2. Volatility-correlated exclusion set (crisis cluster, flash crash, 2018-02-06, 75 successor days) is an unacknowledged calm-regime selection-bias risk; exclusion-impact/sensitivity reporting requested in the SEO-01 return.
3. "Independent" Origin reproduction ran on the same host as the Developer run — should be labeled role-separated.
4. Records edited in place after approval (PO authorization record); fixture read under implicit authority during the Kibot audit; recurring filename drift (`5MIN` vs `5M`) and authority-key naming variance (`NONE` vs `NONE_AUTHORIZED`); no known-variance list.
5. Structural: governance output has grown far faster than scientific output (zero scorable rows at horizon); the licensing ambiguity for hosted-AI processing of vendor data was owner-accepted rather than vendor-cleared.

## 6. What this reviewer holds (see 01_HELD_ARTIFACT_INVENTORY_SHA256.txt)

The complete governance record as received (orders, protocol v1.2.1, ledger v1.0.1, capacity note, Kibot assessment), DWO-04 evidence and both candidate patches, the DWO-05 pause package, the 2026-08-30 delta package (incl. the clean-resumption bundle and Kibot non-price evidence), TVCA REV-02, and all QA outputs — on private branch `claude/context-request-thkmhv` of `agentchevy77/Clade-MCP`. **No licensed market rows, fixtures, raw vintage, credentials, or PII are held.**

## 7. Orientation requested from Nexus

1. Current role charter and authority map (Origin V2, Developer V3, Research, Steward, TradingView Lab, Custodian) and which role is QA's counterparty for submissions and returns.
2. Every Origin order, acceptance, and Developer return issued after 2026-09-02, with hashes — especially: SEO-01 frozen return/candidate (if any), PO ratification of SEO-01, disposition of REV-02 (ratified? REV-03?), and the current state of the TVCA-S01 transition table.
3. Current authority-state block and any known-variance register.
4. Preferred QA return format and character limits now in force (Origin V2 is character-limited — QA can produce compact returns on request).
5. Confirmation that the 2026-08-30 delta package and REV-02 remain the last QA-reviewed artifacts, or the list of what QA has missed.

Standing offer: this lane can recompute hashes, calendars, ledger aggregates, JUnit inventories, and patch-vs-order compliance on any submitted package; it cannot execute licensed lanes and will not accept licensed bytes.
