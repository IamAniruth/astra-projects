# WS module, feature and source coverage

All work is Planned. M01-M18 are delivery modules, each with two WS features, six tasks and six acceptance IDs. This is traceability, not proof of implementation.

## Module and feature map

| Module | Responsibility | Features | Sprint | Status |
|---|---|---|---|---|
| M01 | Offer, buyer and market discovery | WS-S01-F01/F02 | [S01](../PI/PI-01-foundation/S01-scope-provider-gates/sprint-plan.md) | Planned |
| M02 | Architecture and shared-service ownership | WS-S02-F01/F02 | [S02](../PI/PI-01-foundation/S02-architecture-contracts/sprint-plan.md) | Planned |
| M03 | Identity, workspaces and privileged access | WS-S03-F01/F02 | [S03](../PI/PI-01-foundation/S03-identity-admin-access/sprint-plan.md) | Planned |
| M04 | Public product and trust pages | WS-S04-F01/F02 | [S04](../PI/PI-02-website-offers/S04-public-website/sprint-plan.md) | Planned |
| M05 | Demonstration and paid-pilot enquiry | WS-S05-F01/F02 | [S05](../PI/PI-02-website-offers/S05-demo-pilot-funnel/sprint-plan.md) | Planned |
| M06 | Plans, pricing and market offer versions | WS-S06-F01/F02 | [S06](../PI/PI-02-website-offers/S06-plans-market-offers/sprint-plan.md) | Planned |
| M07 | Eligible checkout and verified payment intake | WS-S07-F01/F02 | [S07](../PI/PI-03-billing-usage/S07-secure-checkout/sprint-plan.md) | Planned |
| M08 | Renewal, cancellation and access reconciliation | WS-S08-F01/F02 | [S08](../PI/PI-03-billing-usage/S08-subscription-lifecycle/sprint-plan.md) | Planned |
| M09 | Allowance reservation and product entitlements | WS-S09-F01/F02 | [S09](../PI/PI-03-billing-usage/S09-usage-entitlements/sprint-plan.md) | Planned |
| M10 | Customer workspace and assisted setup | WS-S10-F01/F02 | [S10](../PI/PI-04-customer-product/S10-assisted-onboarding/sprint-plan.md) | Planned |
| M11 | Entitled AI workflow and reviewed result integration | WS-S11-F01/F02 | [S11](../PI/PI-04-customer-product/S11-product-workflow-adapter/sprint-plan.md) | Planned |
| M12 | Customer billing, history and support lifecycle | WS-S12-F01/F02 | [S12](../PI/PI-04-customer-product/S12-customer-self-service/sprint-plan.md) | Planned |
| M13 | Admin overview, customers and support | WS-S13-F01/F02 | [S13](../PI/PI-05-admin-operations/S13-admin-customers-onboarding/sprint-plan.md) | Planned |
| M14 | Admin billing, offers and market controls | WS-S14-F01/F02 | [S14](../PI/PI-05-admin-operations/S14-admin-billing-markets/sprint-plan.md) | Planned |
| M15 | Admin processing recovery and service monitoring | WS-S15-F01/F02 | [S15](../PI/PI-05-admin-operations/S15-admin-jobs-health/sprint-plan.md) | Planned |
| M16 | Supported-market and localization qualification | WS-S16-F01/F02 | [S16](../PI/PI-06-qualification-launch/S16-international-qualification/sprint-plan.md) | Planned |
| M17 | Security, retention and target-host recovery | WS-S17-F01/F02 | [S17](../PI/PI-06-qualification-launch/S17-security-recovery/sprint-plan.md) | Planned |
| M18 | Paid pilot, release evidence and handover | WS-S18-F01/F02 | [S18](../PI/PI-06-qualification-launch/S18-pilot-launch-handover/sprint-plan.md) | Planned |

## Website summary coverage

Source: [Sales and subscription summary](../AI-Product-Website-Sales-and-Subscription-Summary.md).

| Source sections | Requirement | Owning sprints |
|---|---|---|
| 1-2 | One offer/product/buyer, commercial model and supported-market limits | S01, S06 |
| 3 | Public pages, customer area and owner administration | S03-S05, S10-S15 |
| 4 | Account, verified payment, onboarding and useful first task | S03, S07-S12, S18 |
| 5 | Plans, customer-facing usage, failures/retries and limits | S06, S09, S14 |
| 6 | Checkout, webhook verification, cancellation, grace and reconciliation | S07-S09, S12, S14 |
| 7 | Private model, product/backend boundaries and real hosting readiness | S02, S11, S15, S17 |
| 8 | Core product workflow and owner tools | S10-S15; product-domain implementation is an external dependency |
| 9 | Pilot funnel, measured sales, launch and staged expansion | S01, S05, S18; later expansion deferred |
| 10 | Conversion, first-value, recurring vs setup revenue and delivery costs | S05, S09, S13, S18 |
| 11-12 | Readiness and complete initial paid product | S16-S18 with all earlier applicable gates |
| 13 | Market-by-market checkout/language/currency/support/data-path qualification | S01, S06-S08, S10, S14, S16-S18 |

## Admin specification coverage

Source: [Admin panel specification](../AI-Product-Admin-Panel-Specification.md).

| Source sections | Requirement | Owning sprints |
|---|---|---|
| 1-3 | Private admin layout, roles, MFA and controlled content access | S02-S03, S13 |
| 4 | Safe dashboard and revenue/cost/health definitions | S09, S13, S15 |
| 5-6 | Customer detail, distinct states and assisted onboarding | S10, S13 |
| 7 | Draft/active/archived versioned offers and migration rules | S06, S14 |
| 8 | Billing/event visibility, cancellation, reconciliation and access exceptions | S07-S09, S14 |
| 9 | Atomic usage ledger, corrections and measured/estimated costs | S09, S14 |
| 10 | Attempts, retry eligibility, cancellation and uncertain remote outcomes | S11, S15 |
| 11 | Timestamped health, incidents and internal support | S12-S13, S15, S17 |
| 12 | Market controls, distinct locales/currencies and verified data requests | S10, S12, S14, S16-S17 |
| 13 | Audit, current permissions, confirmation, concurrency and safe exports | S03 plus all mutations; integrated S17 |
| 14 | Records and authoritative service boundaries | S02 and consuming sprints |
| 15 | Foundation, pilot/subscription operations and staged expansion | PI-01 through PI-06; optional expansion deferred |
| 16 | Complete admin acceptance checks | S03, S07-S18; integrated S18 checklist |
| 17 | Pre-coding decisions | S01-S02 plus owning sprint decisions |

Trace individual source acceptance checks into execution evidence using [templates](../templates/README.md). Later integrations, multi-provider migration, automatic overages, bulk operations, full visual content editing and advanced marketing are not quietly included in the initial release.

## Product reuse policy

The reference quotation plan is a format and integration example. EQ S13-S18 and PI-08 or corresponding product services may overlap this commercial plan. S02 records one implementation owner and evidence link per shared capability; acceptance can reuse appropriate evidence, but customer/operator integration must still be checked. WS S11 does not claim to implement or qualify the product's AI workflow itself.
