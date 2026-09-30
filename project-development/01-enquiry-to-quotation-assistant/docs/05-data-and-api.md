# Data model and API contracts

## Database entities

All business-owned records carry a workspace identifier. A client-supplied workspace ID is never proof of membership. Use composite foreign keys or equivalent constraints where needed so related records cannot cross companies accidentally.

| Entity group | Main fields and rules |
|---|---|
| User, session, account, verification | Auth-library-owned schema; do not invent password/session handling |
| Workspace, membership, invitation | Business name, seller/buyer country settings, locale, time zone, role; unique workspace/user membership; expiring single-use invitation |
| MarketProfile | Market code, supported locales/currencies, availability, version, reviewed templates, effective dates |
| Customer | Workspace, name, contacts, flexible billing/delivery address, external reference; soft archive |
| CatalogueImport, Product, ProductAlias | Workspace, normalized SKU, source row, category, description, attributes, base unit, active state; unique SKU within workspace; versioned imports |
| PriceList, PriceEntry | Workspace, product, customer segment, currency, decimal unit price, effective interval, tax category; no ambiguous active overlaps |
| InventorySnapshot | Product, quantity, unit, source, captured time; informational only |
| FileAsset | Workspace, random storage key, detected media type, size, checksum, scan/parser state, retention policy; never a public path |
| Enquiry, EnquiryLine | Customer, raw source, requested quantity/unit/specifications, locale, provenance, review status, version |
| ModelRun, MatchCandidate | Model/prompt/schema version, timing, source references, candidate product IDs, retrieval score, review outcome; keep score distinct from calibrated confidence |
| Job, JobAttempt, Outbox | Durable ID, workspace, kind, status, lease, idempotency key, retry count, error code, checkpoint |
| Quote, QuoteRevision, QuoteLine | Stable quote number, immutable revision snapshots, product/price snapshots, decimal quantities/rates, currency, validity, totals, state |
| Approval, ExportArtifact | Revision ID, actor, decision, timestamp, file ID, checksum, render version |
| Plan, Subscription, Entitlement | Internal plan, provider IDs, billing currency, effective allowance, status, period boundaries, scheduled change |
| UsageReservation, UsageEvent | Workspace, period, operation ID, reserved/consumed/released units; unique operation ledger entry |
| WebhookEvent | Provider/event ID uniqueness, verified receipt, processing status, reconciliation reference |
| AuditEvent, SupportCase | Actor, action, scoped target, redacted changes, correlation ID, time; controlled support access |

Maintain UTC event instants and named time zones for local schedules. Store money as appropriate database numeric values or validated minor-unit amounts; never use binary floating-point arithmetic for authoritative amounts. Persist document currency and billing currency separately.

Add indexes for workspace plus common filters, job status/lease, effective price intervals, quote/customer/time, and provider event ID. Enforce constraints in the database, not only UI forms. Add optimistic concurrency versions to mutable drafts and import operations.

## State transitions

- Enquiry: draft -> submitted -> processing -> needs_review -> reviewed. Failed processing records an actionable error and permits an authorized retry.
- Job: pending -> queued -> running -> succeeded/failed/cancelled. Cancellation is cooperative; partial writes cannot publish a completed result.
- Quote revision: draft -> submitted -> approved/rejected. Editing submitted or approved content creates a new draft revision or explicitly withdraws submission under policy; approval never silently transfers.
- Quote document delivery: exported and optionally sent are separate events tied to an approved revision. Expired or superseded exports remain historical and are labelled appropriately.
- Subscription: use an internal provider-independent access policy; do not assume all providers expose identical status values.

## API conventions

Base: `/api/v1`. Authentication endpoints mount at `/api/auth`; billing webhooks use `/api/webhooks/{provider}`.

Return JSON, typed validation errors, a correlation ID, and no stack traces. Use cursor pagination on large lists. Return 401 for unauthenticated requests, 403 for known forbidden actions, 404 for inaccessible object IDs where appropriate, 409 for stale versions/state conflicts, 422 for invalid domain input, and 429 for rate/usage limits. Explicitly prevent caching of private responses.

Successful async work returns 202 with `jobId` and a status URL. Expensive creation actions accept an idempotency key. API examples describe a contract to implement, not existing endpoints.

| Module | Endpoints | Important contract |
|---|---|---|
| Health | GET /health/live; GET /health/ready | No secrets; readiness checks only required serving dependencies |
| Workspace | POST /workspaces; GET/PATCH /workspaces/:id; GET/POST /workspaces/:id/members | Server membership and role checks |
| Customers | GET/POST /customers; GET/PATCH /customers/:id | Workspace scoped; prevent archived customer misuse |
| Catalogue | POST /catalogue/imports; GET /catalogue/imports/:id; POST /catalogue/imports/:id/commit; GET /products | Preview validation before import commit; idempotent commit |
| Prices | GET/POST /price-lists; POST /price-lists/:id/entries | Effective-date, currency, and unit checks |
| Files | POST /files; GET /files/:id/download; DELETE /files/:id | Private upload/download; deletion respects retention and referenced artifacts |
| Enquiries | POST/GET /enquiries; GET/PATCH /enquiries/:id; POST /enquiries/:id/process | Version checking; usage reservation before processing |
| Jobs | GET /jobs/:id; POST /jobs/:id/retry; POST /jobs/:id/cancel | Workspace checks for every operation; retry only recoverable states |
| Matching | GET /enquiries/:id/matches; PATCH /enquiries/:id/lines/:lineId | Only same-workspace products; explicit user selection |
| Quotes | POST /quotes; GET/PATCH /quotes/:id; POST /quotes/:id/revisions | Deterministic calculation and revision concurrency |
| Approval | POST /quotes/:id/submit; POST /quotes/:id/revisions/:revision/approve; POST .../reject | Validate role and exact content/revision; audit atomically |
| Export | POST /quotes/:id/revisions/:revision/exports; GET /exports/:id | Revision locked, asynchronous generation, authorized download |
| Billing | GET /billing; GET /usage; POST /billing/checkout; POST /billing/portal | Provider eligibility and server-selected plan prices |
| Settings | GET/PATCH /settings; GET /markets | Market availability checked on backend |
| Admin | GET /admin/jobs; GET /admin/usage; POST /support/cases | Separate platform role; redact customer payloads by default |
| Data lifecycle | POST /workspace-export; POST /workspace-deletion | Owner authorization, confirmation, queued processing and documented retention |

### Processing request example

```json
{
  "enquiryId": "example-enquiry-id",
  "expectedVersion": 3
}
```

The session identifies the actor. A verified workspace context scopes the enquiry lookup. Respond with a durable job ID; do not accept prices or approval state from an AI response.

### Quote line example

```json
{
  "productId": "example-product-id",
  "quantity": "20",
  "unit": "piece",
  "priceEntryId": "example-price-entry-id",
  "expectedVersion": 4
}
```

The server resolves the actual price, verifies units and currency, recalculates totals, and snapshots the inputs. Overrides require separate permission, a reason, and audit evidence.

## Migrations and data lifecycle

Generate migrations, review SQL and data backfills, apply in staging, then deploy through a controlled migration job. Use expand/contract changes when old and new application versions overlap. Test restore and migration forward recovery before launch.

Deletion covers source files, derived text/indexes, model logs, exports, and relevant business records according to the selected policy. Keep only records with an explicitly justified retention basis; document backup expiry and billing-record exceptions. No deletion promise is inferred from merely removing a UI row.

