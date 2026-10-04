# WS decisions and dependency register

Prepared: 4 October 2026. All entries are open until named owners record evidence and a decision.

| Decision | Owner role / gate | Required evidence |
|---|---|---|
| First product, buyer and workflow | Product, S01 | Buyer access, permitted examples, useful-task/pilot criteria |
| Seller, first market and provider | Commercial, S01/S07 | Current official eligibility/recurring/settlement/refund documentation and actual onboarding approval |
| Offer, setup fee, currency and allowances | Commercial/product, S01/S06 | Value/cost evidence and explicit terms; no invented prices |
| Shared-service ownership | Architecture/product, S02 | Actual product code/contracts and one owner for identity/billing/usage/jobs |
| Frontend/backend/auth/store stack | Engineering, S02/S03 | Compatibility, deployment topology, threat/data-flow review |
| Staff roles and support access | Security/operations, S03 | Permission matrix, MFA/revocation, approver and expiry policy |
| Usage counting/retries/period resets | Product/engineering, S09 | Concrete success/failure/concurrency/plan-change examples |
| Grace/cancellation/refund/dispute policy | Commercial/support, S08 | Documented access/charge effects reviewed for actual seller/market |
| Product workflow and quality | Product/domain, S11 | Real end-to-end review/result, model/component commercial suitability and independent quality evidence |
| Privacy/retention/deletion | Data owner, S12/S17 | Full data inventory, request authority, backup/audit/billing exceptions |
| Market/language/data location | Market/operations, S16 | End-to-end provider/product/support/localization and actual processing-path records |
| Host capacity/recovery/support | Operations, S17 | Real selected workload, restore drill, thresholds, support owners/hours |
| Pilot and release | Product/operations, S18 | Measured buyer outcomes, costs, failure checks and rollback handover |

## Shared-product overlap

For each existing EQ or other product capability, record: product sprint/commit, service authority, WS consuming sprint, contract/version, reused evidence and additional integration checks. A planning document is not evidence that a service exists.

The product may not yet have application code. That blocks real S11 integration and paid launch, not completion of these planning documents. Do not narrow the useful-product promise silently to a marketing site or mock dashboard.

## Model size planning estimate (2026-10-04)

Planning estimate, not a selection or measurement. Source: [Model size and training time guide](../../../astra-llm/codebase/command-documentation/14-MODEL_SIZE_AND_TRAINING_TIME_GUIDE.md), section 10.

The website, offers, billing, usage and admin modules need no LLM; they are an ordinary web application. Model size depends on the product sold through the site:

| Product | Minimum workable | Comfortable for paying customers |
|---|---|---|
| Website, billing, admin | 0 | 0 |
| Enquiry-to-quotation (first product) | about 100-350 M, extraction-only training | 1-3 B |
| Invoice processing | about 350 M-1 B | 1-3 B |
| Manual / troubleshooting | about 1 B | 3-8 B |
| Company knowledge assistant | about 1-3 B | 7-8 B |
| Support reply assistant | about 3 B | 7-8 B or more |

The model, hardware and hosting decisions remain open; launching one narrow product first keeps the required model small. S11/S17 still need the real selected workload and quality evidence.

## Deferred choices

Additional payment providers/migration automation, annual/bundled offers beyond validated need, automatic overages, multi-product catalogue, bulk retry, visual website editor, automated campaigns, private-installation automation and regional multi-deployment are separate later scopes.

Review current primary provider/platform documentation during implementation before selecting versions or making eligibility claims. The source specifications' named providers are examples, not endorsements or guarantees.
