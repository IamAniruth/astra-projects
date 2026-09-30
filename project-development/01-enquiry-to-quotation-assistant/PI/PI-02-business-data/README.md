# EQ PI-02: Trusted business data and enquiry intake

**Status:** Planned  
**Scope:** Core first-product delivery  
**Sprints:** S04, S05, S06  
**Planning duration:** three two-week sprints, subject to actual staffing and sizing

## Business objective

Customer, catalogue, price and source-document data are usable and traceable.

## Entry criteria and dependencies

PI-01 identity/isolation gate passed; representative permitted catalogue and enquiry samples available.

## Sprint list

| Sprint | Objective | Feature scope |
|---|---|---|
| [S04 Customers and catalogue lifecycle](S04-customers-catalogue/sprint-plan.md) | Make trusted customer and product data available before AI proposes matches. | EQ-S04-F01, EQ-S04-F02 |
| [S05 Price lists, currencies and units](S05-prices-units/sprint-plan.md) | Establish authoritative price and unit rules independently of AI. | EQ-S05-F01, EQ-S05-F02 |
| [S06 Enquiry intake and document provenance](S06-enquiry-files/sprint-plan.md) | Capture enquiries and extract safe, traceable source text for later AI processing. | EQ-S06-F01, EQ-S06-F02 |

## Modules and Astra dependencies

Product modules: M04, M05, M19, M06, M12, M17, M07, M08, M22.  
Astra reference IDs: A04, A05, A06, A07, A08.

See [module specifications](../../docs/04-module-specifications.md), [coverage matrix](../../docs/12-module-feature-sprint-matrix.md), and [Astra mapping](../../docs/11-astra-llm-feature-mapping.md). Reuse qualified primitives; separately plan missing integration and product-specific acceptance.

## Planned deliverables

Customer/catalogue modules; import reports; price/unit rule fixtures; source-linked enquiry intake.

## PI demonstration and exit gate

Catalogue import and prices are deterministic, enquiries preserve source provenance, and unsupported documents fail safely.

The PI review demonstrates its three sprint outputs together, including one negative/failure case and the relevant cross-company boundary. Record actual contract/model/environment identity, integration results, product-owner review and open defects. A declaration of done requires every required sprint acceptance or a documented scope change; it cannot substitute a mock for a required live result.

## Risks and scope controls

Data quality and local pricing rules can dominate effort; reduce accepted format scope transparently.

Only the first quotation product is included. Do not add unrelated Astra training-engine, coding-agent, browser or computer-use capabilities merely because they exist in the reference. Deferred experiments must be feature-flagged and cannot affect qualified baseline behavior.

## Planning review

At PI planning, assign owners, size each feature, reserve integration/review capacity and decide what fits. At every sprint review update [status](../../_STATUS.md). At PI close publish evidence, remaining dependencies and the next increment's readiness.

[Back to roadmap](../README.md)

