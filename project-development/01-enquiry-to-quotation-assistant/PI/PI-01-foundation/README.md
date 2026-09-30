# EQ PI-01: Product foundation and Astra boundary

**Status:** Planned  
**Scope:** Core first-product delivery  
**Sprints:** S01, S02, S03  
**Planning duration:** three two-week sprints, subject to actual staffing and sizing

## Business objective

An agreed business workflow, authenticated customer identity and isolated workspaces with a private Astra integration contract.

## Entry criteria and dependencies

Existing business documents and Astra reference are available; implementation has not started.

## Sprint list

| Sprint | Objective | Feature scope |
|---|---|---|
| [S01 Product scope and Astra contract baseline](S01-scope-contracts/sprint-plan.md) | Agree the first quotation workflow and establish a truthful Astra integration baseline before committing feature scope. | EQ-S01-F01, EQ-S01-F02 |
| [S02 Identity and secure Astra boundary](S02-identity-astra-boundary/sprint-plan.md) | Plan and deliver authenticated customer sessions and a private Astra client boundary. | EQ-S02-F01, EQ-S02-F02 |
| [S03 Workspaces, roles and business settings](S03-workspaces-roles/sprint-plan.md) | Establish company isolation and regional business context across product and Astra boundaries. | EQ-S03-F01, EQ-S03-F02 |

## Modules and Astra dependencies

Product modules: M01, M19, M20, M22, M02, M03, M17.  
Astra reference IDs: A01, A08, A09, A11, A12, A14, A15.

See [module specifications](../../docs/04-module-specifications.md), [coverage matrix](../../docs/12-module-feature-sprint-matrix.md), and [Astra mapping](../../docs/11-astra-llm-feature-mapping.md). Reuse qualified primitives; separately plan missing integration and product-specific acceptance.

## Planned deliverables

Workflow and wireframes; contract inventory; account/session flows; tenant/role evidence; regional settings baseline.

## PI demonstration and exit gate

Scope and contract gaps are documented; auth and two-workspace authorization pass; unsupported Astra capabilities are clearly marked.

The PI review demonstrates its three sprint outputs together, including one negative/failure case and the relevant cross-company boundary. Record actual contract/model/environment identity, integration results, product-owner review and open defects. A declaration of done requires every required sprint acceptance or a documented scope change; it cannot substitute a mock for a required live result.

## Risks and scope controls

Credential mapping or buyer/model assumptions may remain unverified; resolve or record blockers without claiming live integration.

Only the first quotation product is included. Do not add unrelated Astra training-engine, coding-agent, browser or computer-use capabilities merely because they exist in the reference. Deferred experiments must be feature-flagged and cannot affect qualified baseline behavior.

## Planning review

At PI planning, assign owners, size each feature, reserve integration/review capacity and decide what fits. At every sprint review update [status](../../_STATUS.md). At PI close publish evidence, remaining dependencies and the next increment's readiness.

[Back to roadmap](../README.md)

