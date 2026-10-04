# Enquiry-to-Quotation Assistant: admin panel specification

Prepared: 4 October 2026  
Project: EQ | Status: Planned; documentation only, no admin panel implemented  
Reference structure: [Support Reply Assistant admin specification](../../05-support-reply-assistant/docs/09-admin-panel-specification.md) and [reference PI](../../05-support-reply-assistant/PI/PI-08-admin-panel/README.md)  
Delivery: [PI-08 administration](../PI/PI-08-admin-panel/README.md)

## 1. Need and boundaries

A focused admin area is needed to manage workspace access, catalogue imports, authoritative prices, quote policies, subscriptions, processing failures and support. Extend existing module M18 rather than introduce a duplicate business administration system.

Use the project's React/TypeScript/Vite frontend and Next.js business APIs with private Astra integration. Admin screens belong inside the authenticated product; a separate deployment is not required. The public website and salesperson's quotation workspace remain distinct experiences.

Workspace administration manages one distributor's organization and business data. Platform administration manages service customers, entitlements and operations. Being a platform operator does not automatically authorize customer document access or quote approval.

This adapts the reference project's planning format to quotation workflows. It does not add reply drafting, support-knowledge publication or ticket management as product features. No automatic sending, autonomous product substitutions, inventory reservation, purchase ordering or collection of payments for quoted goods is included.

## 2. Navigation and screens

Illustrative frontend routes are /settings for workspace management and /admin for platform operations. Protect every API and artifact on the server independently of navigation.

| Screen | Scope | Main actions and information |
|---|---|---|
| Overview | Separate workspace/platform views | Onboarding blockers, pending imports, missing prices, jobs, usage and incidents |
| Workspace and members | Workspace; platform-safe metadata | Invitations, roles, company settings, onboarding and access state |
| Customers and catalogue | Workspace | Archive customers/products, validate imports, inspect conflicts and versions |
| Prices and units | Authorized workspace staff | Effective price lists, customer overrides, units, currency and configured tax/discount rules |
| Quote governance | Workspace approvers/authorized administrators | Policy, submission queue, revision history, approval and export provenance |
| Jobs and files | Workspace; restricted platform view | Parsing/OCR/extraction/matching/export status, errors and controlled recovery |
| Plan and usage | Workspace billing role | Subscription state, invoice references, allowance, seats if offered, usage ledger |
| Customers and subscriptions | Platform billing/operations | Service onboarding, billing reconciliation, access exceptions and support |
| Markets and templates | Authorized configuration owners | Qualified availability, language, currencies and document templates |
| Health, audit and data requests | Scope-limited administration | Monitoring, support access, retention, export/deletion and restore evidence |

Use search, filters, cursor pagination, accessible forms and keyboard navigation. Show selected workspace, environment, display time zone and data freshness. Provide honest loading, empty, failed, stale and unavailable states. Lists, counts and downloads must obey the same permissions as record details.

## 3. Roles and permissions

Reuse the roles from [product scope](01-product-scope.md); implement explicit permissions for sensitive actions.

| Role | Administration scope |
|---|---|
| Workspace owner | Own workspace settings, membership, billing and quote approval under policy |
| Workspace administrator | Authorized operational settings and imports; billing or price overrides only if explicitly granted |
| Salesperson | Permitted customer/enquiry/draft work and submission; no automatic approval or platform access |
| Approver | Approve/reject exact quote revisions within assigned policy |
| Viewer | Read/download explicitly permitted records; no mutations |
| Platform operator | Redacted health, workspace and job metadata; controlled support and recovery |
| Platform billing permission | Service billing and entitlement administration without customer document access |
| Platform access-management permission | Operator membership and permissions; no implicit authority to approve customer quotations |

Require individual accounts, MFA for privileged administration, secure sessions and timely revocation. Enforce workspace scope on related records and files, including lookup IDs, aggregate counts, queued work and old download URLs. A workspace owner cannot grant platform permissions.

Customer-content support access records purpose, target workspace, approved scope, approving authority and expiry. Audit grants and content reads. Ordinary operators see safe metadata only; unrestricted impersonation is excluded.

## 4. Workspace onboarding and settings

Track permitted sample/customer data, onboarding owner, company identity, members, catalogue import, valid prices, supported input qualification, first reviewed enquiry and first approved export. Completion of a checklist never bypasses payment or authorization checks.

Keep interface language, company country, document currency, subscription currency, time zone and hosting region separate. Support one currency per quote. Display dates and monetary amounts using the chosen locale while retaining authoritative instants/decimal values.

Keep onboarding state, processing suspension and subscription state separate. Suspension blocks new processing under the incident policy; it does not silently cancel renewal. Membership changes use version checks, and seat-limited plans enforce concurrent invitations according to a documented counting policy.

## 5. Catalogue, customers and price control

Catalogue import follows preview, validation and idempotent commit. Show duplicate SKUs, unknown units, missing fields, invalid amounts, conflicts and row-level provenance. SKU uniqueness is workspace-local. Do not silently overwrite conflicting approved data.

Archiving customers/products prevents prohibited new use without erasing historical quote snapshots. Price entries identify product, segment/customer override, currency, unit, effective interval and authority. Reject ambiguous active overlaps, incompatible units/currencies and invalid dates.

Authoritative prices and totals come from business records and deterministic decimal calculations, never from generated model text. Require an explicit permission and recorded reason for price/discount/tax overrides. Use reviewed conversion and rounding rules rather than guessed unit conversion or currency exchange.

Changing a price list does not rewrite existing approved quotations. Draft refresh/repricing must show differences and create the appropriate unapproved revision. Approved quotes retain their immutable product, price and rule snapshots; expired or superseded artifacts stay historical and clearly labelled. Confirm policy for withdrawn products or changed commercial rules before allowing a fresh approval/export.

Inventory is a timestamped informational snapshot. Administration must not represent it as live availability, reservation or a confirmed delivery promise.

## 6. Quote policies, approval and artifacts

Quote governance shows enquiry/source lineage, selected products, authoritative price snapshots, quantity/unit corrections, calculation-rule version, validity, approval decision and artifact hash.

Approvals bind to exact content/revision under workspace policy. Concurrent stale edits fail with a conflict. Editing submitted or approved content creates a new draft or explicitly withdraws submission under policy; approval cannot transfer automatically. Platform support permissions cannot substitute for a customer approver.

Export uses the approved immutable revision, recomputes or verifies the stored deterministic totals as required, and produces private PDF/safe CSV artifacts with renderer/version provenance. Recheck current authorization and applicable expiry/supersession policy at export/download. Never regenerate a historical quote using today's prices.

Exported, downloaded and optionally sent are separate events. Initial admin scope stops at approved exports. Any later email delivery requires separate qualification, explicit confirmation and reliable delivery-state handling; no sending connector is enabled here.

## 7. Jobs and recovery

Track import, parsing/OCR, extraction, retrieval/matching and export jobs using logical IDs, environment, workspace, input version, attempts, remote Astra ID, safe errors, budget and usage settlement.

Preserve S07 execution ownership: Astra owns accepted inference execution; product services own their business records and product tasks. When a response is lost after remote acceptance, show unknown/reconciling status and query the persisted remote ID before resubmission.

Retry only recoverable work after checking current grants, input availability/version, entitlement, budget and active attempts. Use idempotency and concurrency controls to prevent duplicate effects or charges. Explain usage treatment before confirmation. Cancellation stays requested until the owning service acknowledges or reconciles it.

Treat parser/OCR failure as unsupported or actionable error, not successful extraction. Manual fallback stays labelled. Admin recovery cannot approve matches, invent missing quantities or overwrite reviewed quote revisions.

## 8. Billing, usage and markets

Show provider references, plan/version, billing period, charge currency, renewal/cancellation date, payment failure, invoice references and effective access policy. Server-verified provider state determines access; checkout redirects are insufficient.

Verify webhook authenticity, deduplicate events, reconcile out-of-order/missed events and enforce entitlements when work is accepted and starts. Track reserved, consumed, released and adjusted usage through an append-only ledger. Define charging for failures, retries, exports and revisions in S14 before selling allowances.

Temporary access requires authority, reason and expiry without falsifying payment history. Use the provider's authorized dashboard for initially deferred complex refunds/plan changes and reconcile outcomes. These are software-service payments, not payments from the distributor's buyer for goods.

Version offers and provider mappings. Existing subscriptions retain their agreed terms unless explicitly migrated. Keep currencies separate in revenue reports; label cost estimates and exclude invented profitability claims.

New markets stay disabled until S15 evidence covers eligible checkout/renewal, localized documents, product quality, support, reviewed policies and actual processing locations. Disabling new sales does not silently terminate existing customers. Optional market expansion remains S21.

## 9. Support, audit and data lifecycle

Support cases link the affected workspace and optionally job/quote/invoice, with owner, priority, status and follow-up. Keep internal notes distinct from customer-visible communication. No outbound messaging integration is added.

Audit actor, permission scope, target, operation/request ID, time, reason, outcome and safe before/after values for role changes, imports, price overrides, approvals, recovery, access grants and entitlement changes. Ordinary administrators cannot edit audit history. Redact credentials and customer content.

Verified export/deletion requests cover business records, original files, extracted text, indexes, model records, artifacts and optional feedback, with documented backup expiry and justified audit/billing retention. Removing a UI row is not deletion completion.

Restores and rollbacks reapply current membership revocations, deletions and applicable business-data restrictions before reopening access. Preserve immutable approval/artifact lineage. Reconcile any active subscription separately when closing a workspace.

## 10. Health and quality evidence

Display API/worker/Astra availability, oldest queue age, leases, safe failure rates, storage, billing-sync lag, backups and last restore drill, including observation timestamps. Unknown or stale observations must not appear healthy.

Show evaluation checkpoint/prompt/schema/data/host versions, thresholds, denominators, reviewer and remaining failures. S17 supplies actual quotation-quality/capacity results; until then show pending evidence. A rendered admin dashboard is not evidence of model quality or production readiness.

Store secrets only in backend infrastructure. Protect actions with server validation, request-forgery controls where applicable, rate limits, idempotency and optimistic concurrency. Show precise target/effect confirmations for privileged or destructive changes.

## 11. Proposed backend additions

All routes follow the existing /api/v1 conventions in [data/API contracts](05-data-and-api.md). They are proposals, not implemented endpoints.

| Route relative to /api/v1 | Contract |
|---|---|
| GET /admin/workspaces | Platform-safe workspace list with explicit role checks |
| GET /workspaces/:id/admin/overview | Authorized workspace aggregates |
| POST /admin/support-access | Approved, scoped, expiring grant with audited content access |
| GET /admin/audit | Permission-filtered redacted events |
| POST /jobs/:id/reconcile | Ask the existing job owner to resolve an uncertain outcome |
| POST /admin/workspaces/:id/entitlement-adjustments | Reasoned, expiring access/usage adjustment |
| GET /admin/health | Restricted operational observations and freshness |
| GET /admin/readiness | Pending/failed/accepted evidence, actual versions and reviewers |

Reuse existing membership, catalogue, price, approval, export, job retry/cancel, billing, settings and data-lifecycle routes. Extend current records with support-access grants, adjustment/incident records and readiness evidence where required. Do not create parallel quote, usage or job authorities.

## 12. Delivery and acceptance

| Sprint | Scope | Existing service owners |
|---|---|---|
| [S22](../PI/PI-08-admin-panel/S22-admin-access-workspaces/sprint-plan.md) | Access, workspaces, onboarding and support grants | S02/S03/S13; S14 if seats offered |
| [S23](../PI/PI-08-admin-panel/S23-admin-catalogue-quote-governance/sprint-plan.md) | Catalogue/prices, policy, approval and artifact governance | S04-S06/S09-S12 |
| [S24](../PI/PI-08-admin-panel/S24-admin-commercial-operations/sprint-plan.md) | Jobs, billing, markets, health, audit, retention and readiness | S07/S14-S16; consumes S17/S18 evidence |

PI-08 extends M18 and related modules, with existing service ownership preserved. It does not depend on optional PI-07. Schedule required controls before the S17 paid pilot and include final acceptance in S18. Quality evidence may remain pending during development, avoiding a circular release dependency.

- [ ] Workspace users cannot invoke platform actions or read another tenant through IDs, search, aggregates, downloads or jobs.
- [ ] Revoked users and expired support grants lose access, including cached/in-flight results; privileged actions are audited.
- [ ] Import retries are idempotent; conflicting SKUs, price overlaps, units and currencies require explicit resolution.
- [ ] Model output cannot set authoritative prices/totals or approve substitutions.
- [ ] Price updates leave approved snapshots intact; repricing/editing creates unapproved content.
- [ ] Approval/export binds to the exact revision, preserves totals and denies stale/conflicting requests.
- [ ] Remote uncertainty is reconciled before retry; repeated actions do not duplicate execution, artifacts or usage.
- [ ] Concurrent allowances and repeated billing events preserve correct access and ledger balances.
- [ ] Market availability matches recorded qualification; billing/document currency remain independent.
- [ ] Deletion/restore drills enforce current access and retention while preserving required history.
- [ ] Health and evaluation views expose unknown/pending/failed states accurately.
- [ ] A permitted pilot completes onboarding, import, reviewed matching, deterministic pricing, approval and private export.

## 13. Open decisions

Confirm named role owners, approval/override policy, seat and usage counting, price-change/withdrawal policy, export expiry behavior, eligible provider, grace period, retention, support-access approver, operational thresholds and initial market/language.

Record outcomes in [decisions and risks](09-decisions-and-risks.md). No framework installation, application code, billing connection, runtime benchmark or deployment is performed by this planning document.
