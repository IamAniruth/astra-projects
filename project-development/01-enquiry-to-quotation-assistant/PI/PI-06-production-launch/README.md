# EQ PI-06: Production qualification and first-market release

**Status:** Planned  
**Scope:** Core first-product delivery  
**Sprints:** S16, S17, S18  
**Planning duration:** three two-week sprints, subject to actual staffing and sizing

## Business objective

The actual product, model and deployment pass quality, recovery and commercial gates before release.

## Entry criteria and dependencies

PI-05 staging candidate and target host available; permitted pilot data and reviewers assigned.

## Sprint list

| Sprint | Objective | Feature scope |
|---|---|---|
| [S16 Administration, security and production operations](S16-operations-hardening/sprint-plan.md) | Prepare a supported deployment boundary, recovery plan and customer-data lifecycle. | EQ-S16-F01, EQ-S16-F02 |
| [S17 Quotation quality, capacity and customer pilot](S17-quality-pilot/sprint-plan.md) | Establish actual customer-task quality and capacity with the exact model and release environment. | EQ-S17-F01, EQ-S17-F02 |
| [S18 Production release, subscriptions and handover](S18-launch-handover/sprint-plan.md) | Release the qualified product to a limited market with verified billing, support and rollback. | EQ-S18-F01, EQ-S18-F02 |

## Modules and Astra dependencies

Product modules: M01, M08, M09, M13, M18, M19, M20, M22, M10, M11, M21, M15.  
Astra reference IDs: A01, A02, A03, A06, A08, A09, A10, A11, A12, A13.

See [module specifications](../../docs/04-module-specifications.md), [coverage matrix](../../docs/12-module-feature-sprint-matrix.md), and [Astra mapping](../../docs/11-astra-llm-feature-mapping.md). Reuse qualified primitives; separately plan missing integration and product-specific acceptance.

## Planned deliverables

Operational dashboard; lifecycle/restore evidence; model/capacity evaluation; pilot report; release manifest and handover.

## PI demonstration and exit gate

Source-derived Astra blockers are resolved for the chosen profile; independent product evaluation, restore/recovery and controlled live billing pass; accountable launch signoff recorded.

The PI review demonstrates its three sprint outputs together, including one negative/failure case and the relevant cross-company boundary. Record actual contract/model/environment identity, integration results, product-owner review and open defects. A declaration of done requires every required sprint acceptance or a documented scope change; it cannot substitute a mock for a required live result.

## Risks and scope controls

Development-host capacity is not release-host evidence. Locked environment, experimental checkpoint and audit/supervisor gaps may block launch.

Only the first quotation product is included. Do not add unrelated Astra training-engine, coding-agent, browser or computer-use capabilities merely because they exist in the reference. Deferred experiments must be feature-flagged and cannot affect qualified baseline behavior.

## Planning review

At PI planning, assign owners, size each feature, reserve integration/review capacity and decide what fits. At every sprint review update [status](../../_STATUS.md). At PI close publish evidence, remaining dependencies and the next increment's readiness.

[Back to roadmap](../README.md)

