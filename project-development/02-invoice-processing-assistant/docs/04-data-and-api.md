# Data model and proposed API contracts

These are product contracts to implement, not existing Astra routes.

| Entity | Information and invariants |
|---|---|
| Workspace / Client / Membership | Tenant, client grants, roles and revocation; scope every child lookup |
| Supplier | Client-owned identity and aliases; do not globally merge suppliers by name |
| Document / UploadAttempt | Immutable hash/storage key, type, pages, class, uploader, retention and repeated-upload provenance |
| ParseRun / ExtractionRun | Document hash, parser/OCR/model/prompt/schema versions, spans and outcome |
| FieldCandidate | Field path, raw text, normalized value, source page/region or text offsets, uncertainty and issues |
| InvoiceRevision / Line | Supplier, number, dates, currency, PO reference, description, quantities, units, prices, discounts, tax and totals |
| PurchaseOrder / Allocation | Versioned PO lines and cumulative invoice allocations, explicit units/currency |
| Exception / Resolution | Type, evidence, severity, actor, reason and revision; no silent dismissal |
| Approval / Export | Immutable approved revision, actor/time, mapping version, artifact hash and re-export history |
| Job / Audit / Usage | Product/remote IDs, idempotency key, correlation ID, transitions and settlement |

Dates become ISO values only when unambiguous. Amounts/quantities are decimal strings plus currency/unit. Identifiers remain strings, preserving leading zeros. Missing values are null, never zero by default. Bank details are sensitive extracted text; they cannot authorize payment or update supplier master data.

Example candidate within a record carrying document hash and parse-run ID:

```json
{"field":"invoice_number","raw":"INV-00042","normalized":"INV-00042","source":{"page":1,"text_start":80,"text_end":89},"status":"needs_review","issues":[]}
```

Confidence, if present, is uncalibrated until evaluated. Review uses source evidence and validation results.

| Proposed route | Behavior |
|---|---|
| POST /api/clients/{clientId}/documents | Bounded upload and provenance; idempotency required |
| POST /api/documents/{id}/extractions | Accepted job ID; does not imply completed extraction |
| GET /api/jobs/{id} | Scoped progress, typed failure and reconciliation state |
| POST /api/jobs/{id}/cancel | Persist request and show actual remote outcome |
| GET /api/invoices/{id} | Source, revision and exceptions |
| PATCH /api/invoices/{id}/revisions/{revision} | Optimistic version check; append revision/audit |
| POST /api/invoices/{id}/approve | Check role, revision and exception disposition atomically |
| POST /api/exports | Approved revision IDs, mapping version and idempotency |

Enforce scope on routes and artifact URLs. Define validation, unauthorized, conflict, unavailable and processing failures. Job states: queued/running/cancel_requested/succeeded/failed/cancelled/reconciling. Invoice states: needs_review/ready_for_approval/approved/superseded. Exports attach to approved snapshots. Edits invalidate approval through a new revision; they cannot mutate the old snapshot.
