# WS architecture, contracts and product ownership

Status: Proposed planning baseline; S02 makes final technology and ownership decisions.

## Components

Public website -> authenticated accounts/customer application -> commercial backend -> selected product adapter -> private product/model services.

Owner administration uses the same authoritative backend for customer/billing/usage metadata with separate platform permissions. The customer-product pipeline owns business records, review/approval and product results. Website hosting alone does not host the model.

React + TypeScript and Next.js Route Handlers are a reference-compatible option, not a required deployment decision. Database/private object storage, authentication library, worker/runtime and provider remain unselected. Inspect the actual selected-product code before creating a new service. No dependency versions or provider eligibility are asserted here.

## Authoritative ownership

| Capability | Required owner/contract |
|---|---|
| Identity and membership | One authenticated source of workspace/user/grants, revocation and staff permissions |
| Plan and offer | Internal plan and immutable offer versions; provider mappings are references |
| Billing | One event/reconciliation authority; signatures, event deduplication and provider-state checks |
| Entitlements | One effective access policy separate from raw provider statuses and temporary exceptions |
| Usage | One reservation/settlement ledger keyed to the logical product operation and period |
| Jobs | One owner per effect; product/remote IDs and reconciliation before replay |
| Product state/results | Selected product's domain service, including review, approvals, source access and export policies |
| Audit/data lifecycle | Attributable restricted records, deletion propagation and justified retention |
| Administration | Authorized calls to the above services, never direct unreviewed state edits |

If the product already provides identity, billing or usage, reuse or deliberately consolidate under S02; do not run parallel authorities. Document migration/transition if existing customers are involved before changing ownership.

## Required records

Customer/workspace/membership; administrator/role/permission; product reference; plan/offer version; seller/market configuration; provider customer/subscription/invoice/event references; entitlement/access exception; usage reservation/event; job/attempt/remote reference; onboarding task; support case; incident; audit; data request and release evidence.

Store charge currency and product-document currency separately. Use exact monetary representation with currency precision, UTC event instants and named display time zones. Preserve original ledger/audit events; append corrections. Never store raw card credentials.

## Proposed interfaces

Paths are illustrative product contracts, not implemented APIs.

| Interface | Behavior |
|---|---|
| GET /api/offers | Only eligible active offers; exact terms/version/currency |
| POST /api/pilot-requests | Validated idempotent lead record and internal ownership |
| GET /api/workspace | Current authenticated account/plan/access view |
| POST /api/billing/checkout | Server-selected offer/provider price; scoped customer association |
| POST /api/webhooks/{provider} | Signature verification, unique event receipt and asynchronous processing |
| GET /api/billing | Scoped invoice/period/status view with freshness |
| POST /api/billing/cancel | Authorized request; confirmed effective state and separate pending outcome |
| GET /api/usage | Period, unit, consumed/reserved/released/remaining |
| POST /api/product/jobs | Entitlement admission and single logical operation into existing product owner |
| GET /api/jobs/{id} | Scoped state/attempt/reference; safe diagnostics |
| POST /api/admin/jobs/{id}/reconcile | Query execution owner before retrying unknown outcomes |
| POST /api/admin/jobs/{id}/retry | Current grants/input/access/budget checks and idempotent eligible recovery |
| GET /api/admin/workspaces | Permission-filtered operational metadata |
| POST /api/admin/access-exceptions | Authorized reason/expiry without falsifying payments |
| POST /api/data-requests | Verified request, scoped background processing and honest status |

Use typed unauthorized/forbidden/not-found/conflict/invalid/limit/unavailable/reconciling states without leaking tenant metadata. Expensive effects accept operation identifiers; mutable records carry expected versions. Repeated submissions cannot duplicate charges, entitlements, jobs or exports.

## Product adapter and lifecycle

Agree product ID, authenticated workspace/principal mapping, qualified workflow/version, usage unit, operation ID, input reference, remote job ID, progress, result reference, review-required state, final disposition and settled usage. Customer content stays behind the product's permissions and private storage.

Reserve usage atomically before accepting work. Recheck entitlements and current grants at execution; settle or release under published policy once. Persist accepted remote IDs and reconcile a lost response before replay. Cancellation can remain requested; do not equate a UI click with stopped inference.

A customer reaching a product dashboard is not successful delivery. S11 needs the full input -> processing -> human review as required -> saved/exported useful result, using actual product evidence. Admin recovery cannot bypass product approvals or expose inaccessible history.

## State separation

Keep payment, subscription, effective access, operational suspension, onboarding and deletion state separate. A refund does not automatically cancel a subscription; suspension does not stop billing; deleting records does not prove subscription closure. Show pending, effective dates and verified outcomes clearly.

Website copy and live offers must derive from the same reviewed scope. New markets default disabled; historical subscriptions retain their agreed terms unless an explicit migration is accepted.
