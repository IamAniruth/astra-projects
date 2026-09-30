# EQ PI-03: Astra-powered extraction and reviewed matching

**Status:** Planned  
**Scope:** Core first-product delivery  
**Sprints:** S07, S08, S09  
**Planning duration:** three two-week sprints, subject to actual staffing and sizing

## Business objective

A durable, budgeted Astra workflow produces source-backed, reviewed requirements and catalogue selections.

## Entry criteria and dependencies

PI-02 data available; actual Astra gateway, checkpoint and scoped credentials identified.

## Sprint list

| Sprint | Objective | Feature scope |
|---|---|---|
| [S07 Durable jobs, progress and runtime budgets](S07-jobs-budget/sprint-plan.md) | Orchestrate asynchronous product work without duplicating Astra's durable execution authority. | EQ-S07-F01, EQ-S07-F02 |
| [S08 Astra enquiry extraction and verification](S08-astra-extraction/sprint-plan.md) | Extract structured quotation requirements through the actual Astra boundary with explicit quality gates. | EQ-S08-F01, EQ-S08-F02 |
| [S09 Permission-aware catalogue matching](S09-retrieval-review/sprint-plan.md) | Suggest only authorized, current catalogue candidates and require review of ambiguous matches. | EQ-S09-F01, EQ-S09-F02 |

## Modules and Astra dependencies

Product modules: M09, M15, M19, M22, M07, M10, M05, M11.  
Astra reference IDs: A01, A02, A03, A04, A05, A06, A08, A09, A11, A13, A14.

See [module specifications](../../docs/04-module-specifications.md), [coverage matrix](../../docs/12-module-feature-sprint-matrix.md), and [Astra mapping](../../docs/11-astra-llm-feature-mapping.md). Reuse qualified primitives; separately plan missing integration and product-specific acceptance.

## Planned deliverables

Remote-job mapping; budget/cancel evidence; extraction schemas and runs; matching review UI; held-out metrics.

## PI demonstration and exit gate

Job failure/recovery and tenant boundaries pass; real-model extraction and candidate retrieval are evaluated; only qualified AI paths can be enabled.

The PI review demonstrates its three sprint outputs together, including one negative/failure case and the relevant cross-company boundary. Record actual contract/model/environment identity, integration results, product-owner review and open defects. A declaration of done requires every required sprint acceptance or a documented scope change; it cannot substitute a mock for a required live result.

## Risks and scope controls

Model quality may fail despite sound integration. Keep manual processing usable and do not label AI release-ready.

Only the first quotation product is included. Do not add unrelated Astra training-engine, coding-agent, browser or computer-use capabilities merely because they exist in the reference. Deferred experiments must be feature-flagged and cannot affect qualified baseline behavior.

## Planning review

At PI planning, assign owners, size each feature, reserve integration/review capacity and decide what fits. At every sprint review update [status](../../_STATUS.md). At PI close publish evidence, remaining dependencies and the next increment's readiness.

[Back to roadmap](../README.md)

