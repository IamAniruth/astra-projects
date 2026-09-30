# EQ PI-05: Website, subscriptions and supported markets

**Status:** Planned  
**Scope:** Core first-product delivery  
**Sprints:** S13, S14, S15  
**Planning duration:** three two-week sprints, subject to actual staffing and sizing

## Business objective

A buyer can understand the product, onboard and purchase an eligible plan in a validated market.

## Entry criteria and dependencies

PI-04 product demonstration exists; commercial offer and provider/market decisions assigned.

## Sprint list

| Sprint | Objective | Feature scope |
|---|---|---|
| [S13 Sales website and guided onboarding](S13-website-onboarding/sprint-plan.md) | Explain and demonstrate the product honestly and guide a business to its first quotation. | EQ-S13-F01, EQ-S13-F02 |
| [S14 Subscriptions, entitlements and usage](S14-billing-entitlements/sprint-plan.md) | Sell supported plans and enforce access/usage without confusing provider billing with Astra runtime metering. | EQ-S14-F01, EQ-S14-F02 |
| [S15 International settings and supported-market qualification](S15-international-release/sprint-plan.md) | Make the shared product configurable internationally while enabling only validated combinations. | EQ-S15-F01, EQ-S15-F02 |

## Modules and Astra dependencies

Product modules: M16, M18, M19, M09, M15, M03, M14, M17.  
Astra reference IDs: A03, A05, A07, A09.

See [module specifications](../../docs/04-module-specifications.md), [coverage matrix](../../docs/12-module-feature-sprint-matrix.md), and [Astra mapping](../../docs/11-astra-llm-feature-mapping.md). Reuse qualified primitives; separately plan missing integration and product-specific acceptance.

## Planned deliverables

Public website; onboarding; provider adapter; usage/entitlements; localized templates and market-readiness matrix.

## PI demonstration and exit gate

Website claims match qualified features; billing lifecycle/usage tests pass; market/language/currency combinations are explicit.

The PI review demonstrates its three sprint outputs together, including one negative/failure case and the relevant cross-company boundary. Record actual contract/model/environment identity, integration results, product-owner review and open defects. A declaration of done requires every required sprint acceptance or a documented scope change; it cannot substitute a mock for a required live result.

## Risks and scope controls

Provider eligibility, pricing and local review can block commerce while sandbox work continues.

Only the first quotation product is included. Do not add unrelated Astra training-engine, coding-agent, browser or computer-use capabilities merely because they exist in the reference. Deferred experiments must be feature-flagged and cannot affect qualified baseline behavior.

## Planning review

At PI planning, assign owners, size each feature, reserve integration/review capacity and decide what fits. At every sprint review update [status](../../_STATUS.md). At PI close publish evidence, remaining dependencies and the next increment's readiness.

[Back to roadmap](../README.md)

