# EQ PI-04: Quotation correctness, approval and artifacts

**Status:** Planned  
**Scope:** Core first-product delivery  
**Sprints:** S10, S11, S12  
**Planning duration:** three two-week sprints, subject to actual staffing and sizing

## Business objective

Staff can produce a trustworthy approved quotation and export it end to end.

## Entry criteria and dependencies

Reviewed line data from PI-03 or explicitly manual entry; authoritative pricing rules approved.

## Sprint list

| Sprint | Objective | Feature scope |
|---|---|---|
| [S10 Quotation builder and deterministic totals](S10-quote-calculations/sprint-plan.md) | Convert reviewed requirements into editable quotations with trustworthy monetary calculations. | EQ-S10-F01, EQ-S10-F02 |
| [S11 Revisions, approval and audit trail](S11-approval-revisions/sprint-plan.md) | Bind approval to an exact quotation revision and prevent unauthorized changes. | EQ-S11-F01, EQ-S11-F02 |
| [S12 Approved artifacts and end-to-end pilot workflow](S12-artifacts-export/sprint-plan.md) | Produce customer-usable, privately downloadable quotation artifacts from approved snapshots. | EQ-S12-F01, EQ-S12-F02 |

## Modules and Astra dependencies

Product modules: M06, M12, M19, M13, M08, M14.  
Astra reference IDs: A06, A07, A08.

See [module specifications](../../docs/04-module-specifications.md), [coverage matrix](../../docs/12-module-feature-sprint-matrix.md), and [Astra mapping](../../docs/11-astra-llm-feature-mapping.md). Reuse qualified primitives; separately plan missing integration and product-specific acceptance.

## Planned deliverables

Quote builder; calculation engine; revision/approval audit; branded PDF/safe CSV; full workflow evidence.

## PI demonstration and exit gate

Money fixtures, revision authorization and artifact readback/render checks pass; complete internal workflow demonstrated.

The PI review demonstrates its three sprint outputs together, including one negative/failure case and the relevant cross-company boundary. Record actual contract/model/environment identity, integration results, product-owner review and open defects. A declaration of done requires every required sprint acceptance or a documented scope change; it cannot substitute a mock for a required live result.

## Risks and scope controls

Astra Office capability is narrower than a universal export service; PDF/CSV first, unsupported formats remain deferred.

Only the first quotation product is included. Do not add unrelated Astra training-engine, coding-agent, browser or computer-use capabilities merely because they exist in the reference. Deferred experiments must be feature-flagged and cannot affect qualified baseline behavior.

## Planning review

At PI planning, assign owners, size each feature, reserve integration/review capacity and decide what fits. At every sprint review update [status](../../_STATUS.md). At PI close publish evidence, remaining dependencies and the next increment's readiness.

[Back to roadmap](../README.md)

