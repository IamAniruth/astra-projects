# Module specifications and traceability

All modules are **Planned**. The scope below defines the first product only. Each module includes UI work, backend work, and observable acceptance evidence. Cross-cutting controls begin early rather than being deferred to a final security sprint.

The detailed [module/feature/sprint matrix](12-module-feature-sprint-matrix.md) is the canonical coverage index after Astra alignment, including M21-M22 and the optional PI-07. Read it alongside the [Astra evidence register](11-astra-llm-feature-mapping.md); platform completion is not product acceptance.

| ID | Module | Delivery sprints |
|---|---|---|
| [M01](#m01-developer-platform) | Developer platform | S01, S03, S16 |
| [M02](#m02-identity-and-sessions) | Identity and sessions | S02, S03 |
| [M03](#m03-workspaces-and-roles) | Workspaces and roles | S03, S15 |
| [M04](#m04-customers-and-contacts) | Customers and contacts | S04 |
| [M05](#m05-catalogue-and-imports) | Catalogue and imports | S04, S09, S21 |
| [M06](#m06-prices-units-and-stock) | Prices, units and stock | S05, S10 |
| [M07](#m07-enquiry-intake) | Enquiry intake | S06, S08, S09 |
| [M08](#m08-private-files-and-parsing) | Private files and parsing | S06, S12, S16 |
| [M09](#m09-jobs-and-usage-execution) | Jobs and usage execution | S07, S14, S16 |
| [M10](#m10-local-ai-extraction) | Local AI extraction | S08, S17 |
| [M11](#m11-catalogue-matching-and-review) | Catalogue matching and review | S09, S17, S21 |
| [M12](#m12-quotation-builder-and-calculations) | Quotation builder and calculations | S05, S10, S11 |
| [M13](#m13-approval-and-audit) | Approval and audit | S11, S16 |
| [M14](#m14-exports-and-optional-delivery) | Exports and optional delivery | S12, S15, S21 |
| [M15](#m15-subscriptions-and-entitlements) | Subscriptions and entitlements | S07, S14, S18 |
| [M16](#m16-public-website-and-onboarding) | Public website and onboarding | S13, S15 |
| [M17](#m17-international-and-market-settings) | International and market settings | S03, S05, S15, S21 |
| [M18](#m18-administration-and-customer-support) | Administration and customer support | S13, S16, S18 |
| [M19](#m19-security-quality-and-evaluation) | Security, quality and evaluation | S01, S02, S03, S04, S05, S06, S07, S08, S09, S10, S11, S12, S13, S14, S15, S16, S17, S18, S19, S20, S21 |
| [M20](#m20-deployment-and-release-operations) | Deployment and release operations | S01, S16, S17, S18, S20, S21 |
| [M21](#m21-governed-feedback-and-model-improvement) | Governed feedback and model improvement | S17, S19, S20, S21 |
| [M22](#m22-astra-platform-integration) | Astra platform integration | S01, S02, S03, S06, S07, S08, S09, S16, S17, S18, S19, S20, S21 |

## M01 Developer platform

- **Features:** Reproducible development, shared contracts, environments, and deployment.
- **React frontend:** Developer health page and consistent shell/error boundary.
- **Next.js/backend and worker:** Workspace setup; package build order; migrations; health/readiness; CI scripts and container builds.
- **Acceptance:** Fresh setup from lockfile and migrations succeeds; no secrets enter client bundles; production build artifacts run.
- **Sprint ownership:** S01, S03, S16.

## M02 Identity and sessions

- **Features:** Account signup, verification, login/logout, recovery, and session expiry.
- **React frontend:** Accessible auth screens with pending/error states; recovery link flow.
- **Next.js/backend and worker:** Reviewed auth library adapter, email integration, session validation, throttling and trusted origins.
- **Acceptance:** Expired/reused reset or verification links fail; unauthorized routes reject; logout invalidates session; recovery does not reveal account existence.
- **Sprint ownership:** S02, S03.

## M03 Workspaces and roles

- **Features:** Business onboarding, invitations, memberships, owner/admin/sales/approver/viewer permissions.
- **React frontend:** Workspace switcher, members screen, company identity and locale settings.
- **Next.js/backend and worker:** Tenant-scoped repositories and related-record constraints; role checks; audited membership changes.
- **Acceptance:** Two companies with overlapping IDs/SKUs remain isolated across API/jobs/files; revoked members lose access.
- **Sprint ownership:** S03, S15.

## M04 Customers and contacts

- **Features:** Create, search, edit and archive customers with international addresses.
- **React frontend:** Customer list/details and quote customer picker; validation and empty states.
- **Next.js/backend and worker:** Scoped CRUD, normalized search and duplicate warnings; archive policy for historical records.
- **Acceptance:** A salesperson can select a customer; archived customers retain historical quotes; another tenant cannot read contacts.
- **Sprint ownership:** S04.

## M05 Catalogue and imports

- **Features:** CSV mapping, preview, row errors, idempotent commit, product search, variants and aliases.
- **React frontend:** Import wizard, catalogue table, product editor, validation report.
- **Next.js/backend and worker:** CSV parsing limits; versioned import batches; SKU uniqueness per workspace; stale candidate invalidation.
- **Acceptance:** Invalid rows are reported without corrupting catalogue; repeated commit does not duplicate items; edits are auditable.
- **Sprint ownership:** S04, S09, S21.

## M06 Prices, units and stock

- **Features:** Effective price lists, currency, decimal quantities, unit conversion rules, informational stock.
- **React frontend:** Price editor, validity warnings, stock timestamp and override reason form.
- **Next.js/backend and worker:** Decimal validation, price precedence, effective intervals, tax category configuration, approval-safe price snapshots.
- **Acceptance:** Missing/expired or incompatible-currency prices block finalization; known unit conversions work; stock is not treated as reserved.
- **Sprint ownership:** S05, S10.

## M07 Enquiry intake

- **Features:** Pasted text or document submission, status, source provenance, editable reviewed lines.
- **React frontend:** Enquiry list/intake/detail, extraction review and version-conflict messages.
- **Next.js/backend and worker:** Scoped persistence, versions, job creation contract and source-to-line references.
- **Acceptance:** Malformed or empty enquiries fail clearly; staff can correct quantity/unit; review is tied to the current version.
- **Sprint ownership:** S06, S08, S09.

## M08 Private files and parsing

- **Features:** Upload/download, media validation, private storage, text extraction, optional OCR, lifecycle.
- **React frontend:** Upload progress, supported format/size guidance, source preview.
- **Next.js/backend and worker:** Storage adapter, random keys, checksums, safe parser limits, private authorization and deletion scheduling.
- **Acceptance:** Cross-company download denied; corrupt/oversized files fail safely; extracted text links to a page; private files are not public assets.
- **Sprint ownership:** S06, S12, S16.

## M09 Jobs and usage execution

- **Features:** Durable asynchronous jobs, retry/cancel, outbox, progress and atomic usage reservations.
- **React frontend:** Job progress, retry/cancel controls, failure explanation.
- **Next.js/backend and worker:** PostgreSQL product intent/outbox and usage ledger; Astra remote job IDs and reconciliation; optional Redis/BullMQ for product-owned tasks only, with explicit lease/idempotency ownership.
- **Acceptance:** Worker restart and duplicate queue delivery produce one durable result; cancellation and failures follow charging policy.
- **Sprint ownership:** S07, S14, S16.

## M10 Local AI extraction

- **Features:** Private authenticated Astra adapter, schema-constrained extraction, prompt versions, product evaluation and explicit manual fallback; no implicit external model provider.
- **React frontend:** Extracted fields with source evidence; invalid/unavailable model feedback.
- **Next.js/backend and worker:** Mock and real adapter; timeouts; schema validation; bounded repair; sensitive-log redaction.
- **Acceptance:** Held-out metrics reported; invented quantities/prices are not authoritative; unavailable model permits manual review.
- **Sprint ownership:** S08, S17.

## M11 Catalogue matching and review

- **Features:** Exact/alias then lexical candidate retrieval, top candidates, no-match and ambiguous handling.
- **React frontend:** Side-by-side requested and catalogue attributes; explicit choice and correction.
- **Next.js/backend and worker:** Tenant-scoped retrieval, valid-ID checks, match provenance and reviewed selection versioning.
- **Acceptance:** Foreign/inactive candidates rejected; similar variants remain distinguishable; no-match can remain unresolved and blocks completion.
- **Sprint ownership:** S09, S17, S21.

## M12 Quotation builder and calculations

- **Features:** Draft editing, server-calculated totals, rounding, discounts, validity, concurrency and revisions.
- **React frontend:** Line editor, recalculated totals, currency/unit errors, revision history.
- **Next.js/backend and worker:** Decimal domain service; customer/product/price snapshots; unique quote numbering; optimistic locks.
- **Acceptance:** Calculation fixtures match expected amounts; concurrent edits return conflict; no client-submitted total is trusted.
- **Sprint ownership:** S05, S10, S11.

## M13 Approval and audit

- **Features:** Submit, approve/reject, price override policy, audit trail and revision identity.
- **React frontend:** Approval inbox, diff/reason display and immutable approved view.
- **Next.js/backend and worker:** Role/state checks and approval snapshot in transaction; actor/time/action audit events.
- **Acceptance:** Sales-only user cannot approve; changed content needs new approval; approved version cannot be silently mutated.
- **Sprint ownership:** S11, S16.

## M14 Exports and optional delivery

- **Features:** Branded approved PDF, safe CSV, multilingual rendering, private downloads.
- **React frontend:** Preview/download/status; optional explicitly confirmed delivery is later scope.
- **Next.js/backend and worker:** Deterministic snapshot render job; escaped template inputs; embedded fonts; artifact checksum and authorization.
- **Acceptance:** Export matches approved totals/revision; repeated requests do not consume duplicate units; CSV formula injection and font cases tested.
- **Sprint ownership:** S12, S15, S21.

## M15 Subscriptions and entitlements

- **Features:** Plan offers, checkout, renewals, invoices, cancellation, grace policy, usage and reconciliation.
- **React frontend:** Pricing selection, billing summary, allowance and customer portal link.
- **Next.js/backend and worker:** One eligible provider adapter, signed-event processing, idempotent ledger, server enforcement and scheduled reconciliation.
- **Acceptance:** Duplicate/out-of-order events cannot double-grant access; cancellations honor end date; concurrent jobs cannot exceed allowance.
- **Sprint ownership:** S07, S14, S18.

## M16 Public website and onboarding

- **Features:** Home/product/demo/pricing/help/contact/policies, signup and guided first quote.
- **React frontend:** Responsive public routes, sample demo, onboarding checklist and honest claims.
- **Next.js/backend and worker:** Market-aware offers, contact flow, minimal analytics and rendered metadata strategy.
- **Acceptance:** Visitor understands product and offer; unsupported markets cannot purchase; demo uses fictional data; first-use journey completes.
- **Sprint ownership:** S13, S15.

## M17 International and market settings

- **Features:** Localized UI, region formats, billing/document currencies, time zones and supported-market matrix.
- **React frontend:** Language selector, flexible business/address fields, market availability messages.
- **Next.js/backend and worker:** Versioned market/template/rounding settings; separate billing and document context; reviewed effective rules.
- **Acceptance:** Different user language and billing country work; decimal/date/time-zone cases pass; enabled-language PDF is readable.
- **Sprint ownership:** S03, S05, S15, S21.

## M18 Administration and customer support

- **Features:** Operator health/job view, controlled support, usage insights and customer help.
- **React frontend:** Redacted operational dashboard, support requests and owner data-management screen.
- **Next.js/backend and worker:** Platform-specific authorization, audited support access, cost metrics, scoped export/deletion orchestration.
- **Acceptance:** Normal owner cannot enter platform admin; operators do not receive full documents by default; support cases are scoped.
- **Sprint ownership:** S13, S16, S18.

## M19 Security, quality and evaluation

- **Features:** Cross-cutting testing, safe parsing, privacy, accessibility, money validation and dependency review.
- **React frontend:** Accessible error/empty/loading states and safe source display.
- **Next.js/backend and worker:** CI checks, tenant/role tests, input validation, auditability, release severity policy and model evaluation.
- **Acceptance:** Relevant behavior tests pass each sprint; isolation, pricing, and approval failures block release; secrets not logged.
- **Sprint ownership:** S01, S02, S03, S04, S05, S06, S07, S08, S09, S10, S11, S12, S13, S14, S15, S16, S17, S18, S19, S20, S21.

## M20 Deployment and release operations

- **Features:** Staging/production separation, private inference, backups/restore, alerts, rollback, pilot and launch.
- **React frontend:** Useful outage/retry status and support availability.
- **Next.js/backend and worker:** Reproducible builds, migration jobs, monitored workers, restore/reconciliation drills, runbooks and release records.
- **Acceptance:** Restore and restart drills demonstrated; pilot targets evaluated; one market enabled only after readiness approval.
- **Sprint ownership:** S01, S16, S17, S18, S20, S21.

## M21 Governed feedback and model improvement

- **Features:** Consented correction capture, private knowledge updates, candidate lineage, evaluation and reversible model release.
- **React frontend:** Correction review, consent settings, private memory visibility, operator candidate comparison and rollback status.
- **Next.js/backend and Astra:** Preserve source/tenant/consent versions; connect applicable Astra candidate/evaluation/promotion mechanisms without treating registration as training; propagate deletion across source and derived stores.
- **Acceptance:** Opt-out data never enters training; tenant corrections remain isolated; only evaluated candidates can progress; failed candidates remain unreleased; deletion is evidenced.
- **Sprint ownership:** S17, S19, S20, S21.

## M22 Astra platform integration

- **Features:** Manifest-based contracts, server-managed credentials, runtime error mapping, remote jobs, budgets, capability qualification and operational evidence.
- **React frontend:** Accurate processing/uncertainty/unavailable states; customer never sees or supplies privileged Astra credentials.
- **Next.js/backend and Astra:** Keep Python model/runtime separate, use the private versioned gateway, establish tenant/principal binding and one execution owner, add authenticated wrappers only for necessary missing operations.
- **Acceptance:** Real qualified request path, denied cross-tenant calls, no legacy API bypass, cancellation/usage reconciliation and release-host evidence; unresolved upstream gaps block only affected capability and remain explicit.
- **Sprint ownership:** S01, S02, S03, S06, S07, S08, S09, S16, S17, S18, S19, S20, S21.

## Shared screen map

Public: home, product, demo, pricing, FAQ/help, contact, policies, signup/login/recovery. Customer: dashboard, onboarding, catalogue import/list/item, price lists, customers, enquiry intake/detail/review, quote editor/history/approval/export, jobs, settings/members, billing/usage, support, data export/deletion. Platform: redacted jobs/usage/service health and scoped support records.

Navigation visibility follows permissions, but backend authorization remains authoritative. Every screen includes loading, empty, error, validation, and narrow-screen behavior. Apply the [quality plan](07-quality-security-international.md) throughout and see [PI roadmap](../PI/README.md) for sequencing.

