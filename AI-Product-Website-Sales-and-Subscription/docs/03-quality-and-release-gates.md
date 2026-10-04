# WS quality, acceptance and release gates

Status: Proposed verification requirements; no checks have been executed against an application.

## Definition of done

A sprint needs concrete artifacts/implementation, actual version identities, meaningful relevant tests, failures and limits, and a named reviewer decision. Discovery uses real permitted buyer/source/eligibility evidence; implemented workflows use domain/integration/browser evidence. Mocks support UI development but do not qualify payments, AI output or production hosting.

## Integrated checks

1. Customer identity, workspace boundaries and operator roles hold for direct API requests, counts, files, histories, exports and background jobs. Revocations apply to sessions, caches and in-flight delivery.
2. Privileged accounts use MFA; sensitive support reads need scoped approved access and audit. Logs and client bundles exclude secrets/customer payloads.
3. Pricing/checkout use server-selected eligible offers; redirects alone cannot grant access. Invalid webhook signatures fail. Repeated/out-of-order/missed events reconcile correctly.
4. Renewal, failure/grace, cancellation, plan changes, refunds/disputes and access exceptions produce distinct documented billing/access outcomes and correct effective dates.
5. Atomic usage reservation, retry/failure treatment and period transitions withstand concurrent work without duplicate settlement. Current entitlements are checked again at execution.
6. Unknown remote outcomes reconcile before retry; attempts, cancellation and recovery preserve product review/results and usage.
7. Public content, demo and market availability match actual scope. No invented testimonials, savings, unlimited capacity or worldwide-coverage claims.
8. Language/country/billing currency/document currency are independent; currency precision, Unicode/RTL where applicable, time-zone/DST and renewal boundaries are tested.
9. Every enabled market has eligible provider/seller arrangements, reviewed applicable policies, localized purchase/cancellation/support journeys and actual full data-path/quality evidence.
10. Data exports/deletion verify scope/requester, cover original and derived stores and document backup/billing/audit exceptions. Restore reapplies current deletions/grants and reconciles jobs/subscriptions/usage.
11. Health timestamps expose unknown/stale/model-down/billing-lag states. Actual capacity and restore drills meet agreed targets; completing a backup is not a restore test.
12. One permitted paid customer can purchase, onboard, finish the selected product's useful reviewed task, inspect usage/invoices, obtain support and cancel under the offered terms.

## Stage gates

| Gate | Required evidence |
|---|---|
| Lead-only public site | Reviewed supported scope/content/policies, accessible working contacts, no unintended checkout |
| Checkout staging | Actual eligible-provider configuration, sandbox lifecycle/security checks and server entitlements |
| Paid pilot | Applicable S01-S17 checks, actual qualified product, agreed scope/cost/availability/support and verified billing |
| General subscriptions | Observed pilot, sustainable measured capacity/cost, recovery/market/privacy evidence and release handover |
| Additional market/product | Separate qualification; website geographic reach does not authorize sales |

All admin specification acceptance items must be mapped to evidence before operator release. Cross-tenant leakage, incorrect money/entitlements, duplicate processing/settlement, unsupported product quality or unresolved recovery failures remain blockers.

## Evidence and operations

Record app commit, auth/provider configuration, schema, offer/market/policy versions, product/model/prompt/data/host identities, dates, sample counts and reviewer. Do not place secrets or unapproved customer material in evidence. Privacy-conscious metrics need definitions and denominators; show measured costs separately from estimates.

Execution later may require actual deployment, provider account steps or transactional communications under the authorized implementation scope. This planning task creates no accounts, makes no purchase, sends no message and deploys nothing.
