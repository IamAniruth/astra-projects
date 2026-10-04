# AI Product Admin Panel — Specification

Prepared: 4 October 2026  
Status: Proposed requirements for implementation; no admin panel has been built or deployed.  
Companion: [Website Sales and Subscription Summary](AI-Product-Website-Sales-and-Subscription-Summary.md)

## 1. Purpose and scope

Create a private administration panel for the owner and authorized staff operating the AI subscription business described in the companion summary. It should support customer onboarding, subscription oversight, usage management, failed-job recovery, support, and service monitoring.

Start with one AI product, one validated market, a paid pilot, and one standard subscription offer. The quotation assistant is the illustrative product: customers import a catalogue, submit enquiries, review suggested matches, and export quotations using their approved prices. The same administration foundation can later support other products.

This panel is separate from the public sales website and the customer workspace. A customer workspace administrator manages their own company; they do not receive platform administration privileges.

Framework, database, hosting, payment provider, prices, quotas, retention periods, and support commitments remain implementation decisions. This specification proposes behavior without selecting those services or inventing commercial terms.

## 2. Layout and navigation

An illustrative route is `app.yourbrand.com/admin`. The address is only a routing choice; server-side authorization protects every page, API action, file request, and export.

Use a desktop-first layout with a collapsible sidebar, readable tables, a global customer/workspace search, and a header showing the signed-in administrator, environment, and display time zone. Support smaller screens for checking incidents and customer status.

Suggested navigation:

1. Overview
2. Customers and workspaces
3. Onboarding
4. Plans and offers
5. Billing and subscriptions
6. Usage and costs
7. AI jobs
8. Service health
9. Support
10. Markets and settings
11. Administrators and audit log

Lists need search, filters, pagination, empty states, loading states, and understandable errors. Detail pages should link related records so an operator can move from a customer to their subscription, usage, jobs, and support history.

## 3. Roles and access

These are proposed permission boundaries. An initial owner may perform several roles, but backend permissions should remain explicit.

| Role | Allowed responsibilities | Restrictions |
|---|---|---|
| Owner | Manage staff access, configuration, offers, and operational actions | Sensitive actions still require confirmation and an audit record |
| Operations | Onboard customers, inspect job metadata, manage incidents, retry eligible jobs | Cannot grant administrator access or issue refunds |
| Billing | Inspect invoices and subscriptions; initiate authorized billing actions | No customer document access or infrastructure secrets |
| Support | View customer status, onboarding progress, and support cases | Cannot change prices, quotas, billing, or staff permissions |
| Read-only reviewer | Read explicitly permitted reports and audit events | No mutations or unrestricted document access |

Require individual administrator accounts and multi-factor authentication. Enforce permissions in the backend, deny access by default, and revoke sessions when an administrator is disabled. Require recent authentication for staff-role changes and other sensitive actions.

Keep customer content hidden by default. When investigation requires document or result access, require a specific workspace, an authorized purpose, and a recorded access event. Prefer metadata and redacted diagnostics. Customer impersonation is outside the first version.

## 4. Overview dashboard

Show actionable information for a selected period, with its time zone, last refresh time, and links to underlying records.

| Area | Display | Follow-up action |
|---|---|---|
| Customers | Active workspaces, pilots, and onboarding awaiting action | Open the filtered customer or onboarding list |
| Billing | Collected payments and refunds by currency; failed renewals | Inspect billing records or follow up on payment failure |
| Subscriptions | Active subscriptions and cancellations scheduled | Review subscription details |
| Usage | Workspaces approaching or reaching allowances | Review usage and available upgrade options |
| Processing | Queued, running, successful, and failed jobs | Inspect delayed or failed work |
| Health | Backend, queue, model, storage, and billing-sync status | Open an incident or component status |
| Support | Open cases, unassigned cases, and overdue follow-ups | Assign or update a case |

Separate setup fees and pilot payments from recurring revenue. Label estimated processing costs and their calculation method. Do not add different currencies into a single revenue total without an explicit conversion method, rate source, and rate date. Unknown or stale health data must not appear healthy.

## 5. Customers and workspaces

### Customer list

Show workspace name and ID, primary contact, business country, product, offer, onboarding stage, access state, subscription state, usage, and creation date. Filter by these fields where useful.

### Workspace detail

Provide tabs for:

- **Overview:** Business profile, contacts, supported market, language, locale, time zone, and assigned operator.
- **Members:** Workspace users, customer roles, invitation state, and seat usage.
- **Onboarding:** Checklist, assigned owner, blockers, and first successful workflow.
- **Billing:** Provider references, invoices, payment events, subscription dates, and scheduled changes.
- **Usage:** Allowance period, consumed and reserved units, adjustments, and remaining allowance.
- **Jobs:** Processing history, status, duration, error category, and retry eligibility.
- **Support and activity:** Cases, operator notes, and relevant audit events.

Authorized actions include assigning an onboarding owner, resending an invitation with rate limits, correcting profile fields, and suspending or restoring workspace processing with a reason. A suspension does not cancel the subscription automatically. Show its billing implications before confirmation.

Keep business lifecycle, billing state, and processing access separate. For example, an active subscription may belong to a workspace suspended for an operational incident. Display the reason access is blocked instead of one ambiguous status badge.

## 6. Assisted onboarding

Use a configurable checklist suited to the selected product:

1. Record pilot scope, success criteria, agreed offer, and contact.
2. Confirm payment through a verified billing record.
3. Create or verify the workspace and customer membership.
4. Record required product settings and customer-approved data setup.
5. Import a catalogue or other agreed source data.
6. Run a sample task and have the customer review the result.
7. Record completion, outstanding issues, and the pilot review date.

For the quotation assistant, track catalogue version, import validation errors, document currency, and quotation-export setup. Do not silently change customer prices or mark generated quotations as approved by the customer.

Each checklist item records its state, owner, completion time, and notes. Completing onboarding must not bypass billing or entitlement checks.

## 7. Plans and market offers

Separate the internal plan from its sellable offers. A plan defines features and limits; an offer adds billing cadence, currency, price, setup fee, market eligibility, and provider mapping.

Required fields include product, plan code, offer version, customer-facing name, supported market, billing currency, billing interval, usage unit, allowance, seat limit, storage/file limits, and provider price reference where applicable.

Use draft, active, and archived states. Validate required configuration before activation. Archive offers to prevent new purchases while retaining historical references.

Existing subscriptions retain their agreed offer version unless an explicit migration is scheduled. Preview affected customers, effective dates, price changes, and allowance effects before applying a migration. Initial implementation may handle migrations manually through a controlled process.

Keep overage charging disabled initially. An allowance increase must be an explicit plan change, purchased top-up if supported, or a recorded adjustment with a reason and expiry.

## 8. Billing and subscription operations

The panel displays billing state synchronized by the backend. It must never treat a checkout redirect or an operator-edited payment flag as proof of payment.

Show provider, external references, charge currency, amounts, billing period, renewal date, cancellation schedule, invoice links, payment failures, refunds, and disputes. Store references and safe metadata rather than raw payment credentials.

| Action | Required behavior |
|---|---|
| Refresh billing state | Query the configured provider and record the reconciliation outcome |
| Cancel at period end | Show the effective date; submit the request; retain access until the confirmed end date under the policy |
| Change plan | Preview effective date, allowance changes, and provider-calculated charges before confirmation |
| Initiate refund | Require billing permission, amount, currency, reason, and confirmation; track provider outcome |
| Grant temporary access | Create a separate, time-limited entitlement exception with a reason; preserve actual billing status |
| Review payment failure | Show customer notification history and the applicable grace-period deadline |

For the first version, refunds and complex plan changes may open the provider's authorized dashboard rather than implement custom transaction controls. Reconcile resulting changes back into the application and retain local operator context.

Provide a webhook/event view containing event ID, type, received time, processing status, safe error details, and retry history. Backend handling must verify signatures, deduplicate events, reconcile out-of-order events, and periodically detect missed updates. Reprocessing an event must not duplicate payments, entitlements, or allowances.

Refunds, cancellations, access suspension, and deletion are separate actions. Explain their effects explicitly instead of assuming one performs the others.

## 9. Usage and processing costs

Show customer-facing usage in the unit sold: quotation jobs, documents, questions, or audio minutes. Display internal token and compute measures separately when available.

Use a usage ledger with workspace, job/reference, unit, quantity, event type, billing-period reference, timestamp, and adjustment reason. Preserve original entries and record corrections as additional entries.

Reserve allowance atomically when accepting work, then finalize or release it according to the defined success/failure policy. Check current entitlements again when queued work starts. Concurrent submissions and retries must not cause quota overruns or duplicate consumption.

Show consumed, reserved, adjusted, and remaining units clearly. Usage periods follow confirmed entitlement boundaries; a page view or duplicate renewal event must not reset an allowance. Define how plan changes and top-ups affect those boundaries before enabling them.

Cost reports should distinguish measured costs from estimates and identify the costing assumptions. Include model compute, storage, optional processing services, and recorded support effort where available; do not imply token counts alone represent profitability.

## 10. AI jobs and failure recovery

The job list shows job ID, workspace, product/workflow, creation time, state, queue wait, processing duration, model/version, safe error category, and retry count. Support filtering by workspace, time, and failure category.

Suggested states are queued, running, succeeded, failed, cancellation requested, and cancelled. A cancellation request remains pending until the worker acknowledges it or a defined recovery procedure resolves it.

Job details show attempt history, usage effects, and safe diagnostics. Input files and result content require separate authorized access.

Allow a retry only after checking workspace access, input availability, current job state, retry policy, and remaining allowance. Link each attempt to the original logical job, prevent concurrent duplicate retries, and prevent duplicate customer exports or usage charges. Explain whether a retry will consume allowance before confirmation.

Support cancellation of queued work and cooperative cancellation of running work where implemented. Do not promise that already-running inference stops immediately. Keep bulk retry and arbitrary model commands outside the initial panel.

## 11. Service health and support

Monitor backend availability, queue depth and oldest waiting job, worker heartbeat, model endpoint reachability, failure rates, storage capacity, billing reconciliation lag, backup status, and the latest restore-test result. Show thresholds and observed timestamps; a backup completing does not demonstrate that restoration works.

An operational incident can record affected components, start time, owner, customer impact, updates, and resolution. Provide a controlled pause for new processing during incidents while keeping status and account information accessible where possible.

Support cases link to a workspace and optionally a job or invoice. Track category, priority, assigned administrator, status, next follow-up, and internal notes. Clearly separate internal notes from customer-visible replies. Messaging integrations and automatic outbound campaigns are outside the first version.

## 12. Markets, settings, and data handling

Maintain explicit supported-market configuration: seller entity, customer countries, languages, billing currencies, provider mappings, approved offers, support arrangements, and verified hosting/processing regions.

New markets begin disabled. Require recorded readiness checks for checkout and renewal, product quality, support, applicable policy review, and the full processing/storage path before activation. This panel records operational readiness; it does not establish legal or tax compliance.

Keep interface language, business country, billing currency, document currency, and hosting region independent. Disabling new sales in a market must not silently terminate existing subscriptions. Any changes affecting existing customers need a separate transition plan.

Store timestamps consistently and display explicit time zones for billing deadlines and reports. Use currency-aware amounts and formatting. Infrastructure credentials belong in a secrets-management mechanism; the panel should show configuration status and masked references.

Track export and deletion requests with requester verification, scope, owner, state, and completion evidence. Delete across the defined data stores according to the approved retention policy, with documented backup expiry and any retained billing records. Deleting a workspace must not leave an unintended active subscription. Keep deletion as a reviewed operational workflow in the first version.

## 13. Audit and action safeguards

Audit privileged changes and sensitive reads with actor, role, workspace where applicable, action, target, timestamp, reason, request ID, outcome, and safe before/after values. Redact secrets and customer content. Ordinary administrators must not be able to edit or remove audit entries.

For billing changes, access exceptions, suspensions, offer activation, and staff-role changes, show a confirmation describing the exact target and effect. Require a reason for overrides. Record pending and failed operations as well as completed changes.

Use server-side validation, protection against cross-site request forgery where applicable, secure session handling, and rate limits. Validate tenant scope on every data operation. Background exports must enforce the same permissions as interactive views and use private, expiring downloads.

Protect against repeated submissions and stale edits. Use operation identifiers for retriable mutations and detect concurrent record changes so two administrators cannot silently overwrite each other's decisions.

## 14. Suggested records and service boundaries

| Record | Purpose |
|---|---|
| Administrator / role / permission | Platform staff identity and permitted actions |
| Customer / workspace / membership | Business identity, isolated data boundary, and customer users |
| Onboarding task | Setup ownership, progress, and evidence |
| Plan / offer version / market | Features, commercial terms, and availability |
| Subscription / billing event / invoice reference | Provider-linked billing history and current state |
| Entitlement / access exception | Effective features, limits, and approved temporary access |
| Usage ledger / reservation | Accounted usage and work awaiting completion |
| Job / attempt | Logical processing request and execution history |
| Support case / incident | Customer assistance and service interruptions |
| Audit event / export or deletion request | Accountability and data operations |

The admin frontend calls an authenticated backend. That backend owns authorization, billing-provider communication, entitlements, usage accounting, job control, and audit writes. Workers access the private model service through controlled infrastructure. Do not place provider secrets or direct model administration endpoints in browser code.

## 15. Implementation sequence

| Phase | Deliverables | Completion evidence |
|---|---|---|
| Foundation | Administrator sign-in, MFA, permissions, workspace lookup, audit recording | Unauthorized and wrong-role requests are rejected by the backend |
| Pilot operations | Workspace details, onboarding, billing visibility, usage, job history, controlled retry, health view | An operator can onboard a paid pilot and resolve a failed job |
| Subscription operations | Reconciliation, cancellation, access exceptions, usage adjustments, support tracking | Renewal and failure scenarios preserve correct access and usage |
| Expansion | Versioned offers, market activation, richer cost reporting, additional staff roles | A second validated market can be configured without breaking existing customers |

For launch, prioritize the foundation and pilot operations, plus the subscription controls required by the actual offer. Advanced analytics, multi-provider migrations, bulk actions, visual website editing, and automated marketing can wait.

## 16. Acceptance checks

Before using the panel for paying customers, verify:

1. Customers cannot open admin APIs, and staff permissions apply even when requests bypass the UI.
2. Workspace filters, direct record IDs, files, jobs, and exports cannot leak another company's data.
3. Disabled administrators lose access, and privileged changes produce attributable audit records.
4. Checkout confirmation, duplicate webhooks, out-of-order events, and reconciliation produce the correct billing and entitlement state.
5. Cancellation preserves access until the confirmed end date; payment failure follows the configured grace policy.
6. Temporary access expires as configured without falsifying payment status.
7. Concurrent jobs, allowance resets, failed attempts, and operator retries do not duplicate usage or exceed enforced limits.
8. Retrying an unsafe, already-running, or completed job is rejected or handled according to an explicit recovery policy.
9. Refund and suspension actions show their independent billing and access effects.
10. New offer versions leave existing subscriptions unchanged until an explicit migration occurs.
11. Currency totals remain separate, billing deadlines identify their time zones, and unsupported markets cannot purchase.
12. Model downtime, stale monitoring, delayed billing synchronization, and failed backups are visible to operators.
13. Sensitive customer-content access is restricted and logged; logs and errors do not expose secrets.
14. Export and deletion workflows verify the requester, respect approved retention rules, and reconcile outstanding subscriptions.
15. The complete pilot journey works: verified payment, onboarding, first reviewed result, usage accounting, and support follow-up.

## 17. Decisions needed before coding

Confirm the first product and buyer group, existing application stack, authentication approach, initial staff roles, seller and launch market, supported currency and language, payment provider, offer terms, usage-counting rules, grace period, retry policy, hosting/model setup, monitoring thresholds, retention rules, and support process.

Use these decisions to turn this specification into screen designs, backend contracts, and implementation tasks. Treat the companion summary as the business scope and this document as the proposed operating interface.
