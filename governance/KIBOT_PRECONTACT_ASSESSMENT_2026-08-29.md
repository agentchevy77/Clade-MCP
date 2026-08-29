# Kibot Pre-Contact Rights and Coverage Assessment

Date: 2026-08-29  
Official-source review cutoff: 2026-08-29T05:31:38Z  
Status: `PRECONTACT_ONLY_INQUIRY_NOT_SENT`  
Authority: `ZERO_COST_NON_BINDING_WRITTEN_INQUIRY_ONLY`

```yaml
work_order: NME-001-DWO-03
authoritative_order: NME001_ORIGIN_DWO02_ACCEPTANCE_AND_DWO03_ORDER_2026-08-29.md
authoritative_order_sha256: 8c340da0f567d68bd812daca1950d427f0cf39ba09ea7fa287709de60d046b2d
kibot_owner_authorization_sha256: f8e8f02dc9f13c2ff5b009ac51070e02fc32eca58143ba4f35a70590519d98f1
inquiry_sent: false
vendor_response_received: false
recipient_preflight: PASS_PUBLIC_KIBOT_LICENSING_FORM
guessed_email_used: false
attachments_planned: false
account_created: false
trial_activated: false
purchase_or_payment: false
credentials_used_or_requested: false
sample_or_data_downloaded: false
provider_data_ingested: false
rights_status: NOT_CLEARED_PENDING_WRITTEN_VENDOR_RESPONSE
coverage_status: PLAUSIBLE_BUT_UNVERIFIED
acquisition_authority: NONE
```

## Decision

Kibot is a plausible provider for a historical SPY minute-data lane, but the
public pages do not clear the project's data-rights, provenance, adjustment,
volume-definition, completeness, or correction-history requirements. No data
purchase or ingestion decision can be made from the public material alone.

The exact send-ready inquiry is frozen in
`KIBOT_DWO03_SEND_READY_INQUIRY_2026-08-29.md`. It requests only written
clarification. It does not request or authorize an account, trial, order,
payment, contract, NDA, sample, download, API connection, or ingestion.

## Current official contact route

The official public route is Kibot's unauthenticated contact form:

- URL: <https://www.kibot.com/contact.html>
- Visible required fields: name, email, subject, and message.
- Visible optional field: company.
- Selected recipient/topic: `KIBOT_SUPPORT_LICENSING` / `Licensing`.
- Visible message limit: 6,000 characters.
- Account or payment gate on the public inquiry page: `NOT_OBSERVED`.
- Form submission attempted: `NO`.

The form still requires an authorized sender name and reply address at send
time. Those values were not invented or entered during this review. If the
form presents an account, trial, payment, credential, contract, NDA, sample,
download, or API requirement during submission or follow-up, the inquiry lane
must stop and return that requirement to the Product Owner.

## Public-source findings and unresolved points

| Topic | What Kibot's current public material indicates | Why written clarification remains required |
| --- | --- | --- |
| SPY coverage | A current Top 50 ETFs 1-minute product page and Kibot's official ETF intraday inventory list SPY with a start date of 1998-01-02; the inventory says it was updated 2026-08-28. | This is not an exact SPY session/bar inventory, completeness attestation, end-date/vintage identity, or list of known gaps and corrections. |
| Available resolutions | The same page says its 1-minute package also gives access to 5-, 15-, and 30-minute resolutions. | It does not establish whether direct 5-minute files are a deterministic aggregation of the exact 1-minute files, nor which source and inclusion rules apply through time. |
| Purchase form | The product page labels the package a one-time purchase with no subscription. Other pages describe optional recurring update subscriptions. | The project needs written confirmation of the smallest SPY-only non-renewing scope, exact price and inclusions, and that no recurring service is required or automatically attached. |
| License | The license says private use, non-transferability, archival copying, and use on two personally accessed computers. | It does not expressly permit hosted AI/Codex processing, a private cloud workspace, or access by Project Nexus Developer and independent QA roles acting for one Product Owner. |
| Retention ambiguity | The FAQ says downloaded files may be kept indefinitely and describes copying data files to multiple machines, while the license states a two-computer private-use limit. | Kibot must identify the controlling interpretation for exact source bytes, backups, receipts/hashes, private workspaces, and role-based review after access or update service ends. |
| File schema | The format reference specifies `Date,Time,Open,High,Low,Close,Volume`, Eastern Time by default, and bar-open timestamps. | The project needs an explicit `America/New_York`/DST identity, RTH boundary behavior, and exact direct-5-minute aggregation rules for SPY. |
| OHLCV construction | The format reference describes first/max/min/last price and summed volume aggregation. | It does not completely identify which trades and reporting conditions enter SPY minute OHLCV across the whole 1998-present archive. |
| Completeness | The quality page describes calendar/bar-count checks and repair methods, while explicitly noting that no historical provider can guarantee universal completeness. | The project requires the known SPY-specific missing-session/bar inventory, outage/halt treatment, quantified completeness where available, and the present correction cutoff. |
| Odd lots and trade conditions | The bid/ask and FAQ pages state that standard tick data omits odd-lot prints and exposes conditions only in an experimental millisecond variant. | That does not answer whether standard SPY minute-bar prices and volume include odd lots, or whether inclusion changed with SIP/CTA/reporting conventions during the archive. |
| Adjustment variants | Current product and update pages refer variously to unadjusted, split-adjusted, and split-and-dividend-adjusted data; the adjustment article describes adjusted versus unadjusted data and retroactive price/volume changes. | The project needs separate unadjusted and split-only/dividend-off files, exact price/volume factors and rounding, and complete SPY split/distribution metadata without mixing variants. |
| Corrections and vintage | The license permits corrections without notice, and update documentation says historical corrections and backfills may be applied. | Reproducibility requires an exact delivered vintage, immutable local retention, and a correction/revision record sufficient to explain changes between vintages. |
| Source identity | Public product pages label SPY as NYSE and other pages describe consolidated US exchange/ECN data. | Nexus's prior symbol identity was `AMEX:SPY`; a new provider must document its SPY listing/tape/feed identity and historical venue or mapping changes rather than assume equivalence. |

## Rights assessment

The standard public license is not sufficient evidence for the intended
workflow. The word `Data` in the license includes related or derived
information, and the license prohibits transfer while limiting use to private
licensee activity. Until Kibot answers in writing, the following remain
uncleared:

1. Uploading or exposing raw source bytes to a hosted AI processing service in
   a private workspace.
2. Raw-byte access by a Developer role and an independent QA role acting only
   for the same Product Owner.
3. Whether those roles may inspect derived features, labels, models, metrics,
   reports, receipts, and hashes.
4. Indefinite private retention of original source bytes and derived research
   artifacts after download/update access ends.
5. Use of private backup, execution, and QA machines or environments beyond
   the public license's two-computer wording.

Accordingly, `rights_status` remains
`NOT_CLEARED_PENDING_WRITTEN_VENDOR_RESPONSE`.

## Coverage and metrology assessment

Public material makes the required time span plausible: SPY is listed from
1998-01-02, which precedes the DWO-03 historical-design floor and leaves room
for the calendar predecessor and capacity margins. That is only a catalog
claim. Before any acquisition decision, a vendor response must identify:

- the exact first and latest SPY observations in the offered vintage;
- all ordinary RTH sessions and known missing or partial sessions;
- exact expected and actual RTH bar counts, or a machine-readable equivalent;
- the exchange/tape/feed identity and any dated identity changes;
- timestamp zone, DST rules, open-time convention, and 5-minute boundaries;
- the complete trade and volume inclusion rules, including odd lots, auctions,
  TRF/off-exchange reports, late prints, cancels, and corrections;
- all dated changes to sources, filters, bar construction, or reporting
  definitions;
- exact unadjusted, split-only, and split-and-dividend-adjusted deliverables;
  and
- complete corporate-action and correction/revision metadata.

Until those details are supplied and independently assessed,
`coverage_status` remains `PLAUSIBLE_BUT_UNVERIFIED`.

## Send/no-send readiness

```yaml
message_body_frozen: true
message_body_within_visible_6000_character_limit: PASS
message_body_characters: 5377
message_limit_characters: 6000
authorized_sender_name_available: false
authorized_reply_address_available: false
public_contact_form_available: true
account_gate_observed: false
protected_action_taken: false
send_readiness: READY_AFTER_SENDER_IDENTITY
```

The sender identity fields are the only operational inputs intentionally left
unfilled. They do not change the scientific or licensing questions. The
message must be sent unchanged apart from those contact-form identity fields.

## Official sources reviewed

All sources below are official Kibot pages accessed on 2026-08-29. Public web
copy is treated as preliminary information, not as a negotiated license
clarification or scientific data receipt.

1. Contact form: <https://www.kibot.com/contact.html>
2. License agreement: <https://www.kibot.com/license.html>
3. Buy-data catalog: <https://www.kibot.com/buy.html>
4. Top 50 ETFs 1-minute product and SPY start date:
   <https://www.kibot.com/historical-data/top-50-etfs-1-minute-intraday-data.html>
5. Official ETF intraday inventory:
   <https://www.kibot.com/Files/2/All_ETFs_Intraday.txt>
6. Data format reference:
   <https://www.kibot.com/file-format/data-format-reference.html>
7. Time-zone reference:
   <https://www.kibot.com/file-format/timezone-conversion.html>
8. Adjusted versus unadjusted data:
   <https://www.kibot.com/file-format/adjusted-vs-unadjusted-data.html>
9. Data completeness and quality assurance:
   <https://www.kibot.com/quality/data-completeness.html>
10. Bid/ask, trade conditions, and odd-lot discussion:
   <https://www.kibot.com/quality/bid-ask-and-nbbo-quotes.html>
11. FAQ: <https://www.kibot.com/faq.html>
12. Data updates and delivery:
    <https://www.kibot.com/delivery/data-updates.html>
13. Adjustments request and retroactive history changes:
    <https://www.kibot.com/api/adjustments-request.html>

## Authority boundary

```yaml
formal_evidence_authority: NONE
predictive_authority: NONE
trading_authority: NONE
alerting_authority: NONE
automated_action_authority: NONE
provider_contact_authority: KIBOT_ZERO_COST_NON_BINDING_INQUIRY_ONLY
provider_data_authority: NONE
purchase_authority: NONE
```
