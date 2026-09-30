# EQ PI-07: Governed learning and qualified expansion

**Status:** Planned  
**Scope:** Optional post-launch improvement  
**Sprints:** S19, S20, S21  
**Planning duration:** three two-week sprints, subject to actual staffing and sizing

## Business objective

Optional post-launch improvements use consented data, measurable benefit and reversible releases.

## Entry criteria and dependencies

Qualified first release exists; business prioritizes the enhancement and data/compute are authorized.

## Sprint list

| Sprint | Objective | Feature scope |
|---|---|---|
| [S19 Consented feedback and governed memory](S19-consented-feedback/sprint-plan.md) | Turn corrections into governed product improvements without silently training on customer content. | EQ-S19-F01, EQ-S19-F02 |
| [S20 Evaluated model improvement and reversible release](S20-model-improvement/sprint-plan.md) | Evaluate a consented candidate and promote only a demonstrably better, releasable model. | EQ-S20-F01, EQ-S20-F02 |
| [S21 Qualified retrieval, artifacts and market expansion](S21-qualified-expansion/sprint-plan.md) | Add only enhancements justified by measured customer needs and capability evidence. | EQ-S21-F01, EQ-S21-F02 |

## Modules and Astra dependencies

Product modules: M19, M21, M22, M20, M05, M11, M14, M17.  
Astra reference IDs: A05, A07, A09, A10, A11, A12, A13, A14, A15.

See [module specifications](../../docs/04-module-specifications.md), [coverage matrix](../../docs/12-module-feature-sprint-matrix.md), and [Astra mapping](../../docs/11-astra-llm-feature-mapping.md). Reuse qualified primitives; separately plan missing integration and product-specific acceptance.

## Planned deliverables

Governed correction registry; evaluation/canary decision; one independently qualified enhancement or no-adoption report.

## PI demonstration and exit gate

Feedback isolation/deletion passes; each model or capability change passes independent gates or is explicitly rejected/deferred.

The PI review demonstrates its three sprint outputs together, including one negative/failure case and the relevant cross-company boundary. Record actual contract/model/environment identity, integration results, product-owner review and open defects. A declaration of done requires every required sprint acceptance or a documented scope change; it cannot substitute a mock for a required live result.

## Risks and scope controls

No capable candidate, unreviewed fixtures or unsupported optional infrastructure must remain visible rather than being treated as done.

Only the first quotation product is included. Do not add unrelated Astra training-engine, coding-agent, browser or computer-use capabilities merely because they exist in the reference. Deferred experiments must be feature-flagged and cannot affect qualified baseline behavior.

## Planning review

At PI planning, assign owners, size each feature, reserve integration/review capacity and decide what fits. At every sprint review update [status](../../_STATUS.md). At PI close publish evidence, remaining dependencies and the next increment's readiness.

[Back to roadmap](../README.md)

