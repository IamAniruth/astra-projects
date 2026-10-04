# PI-08: Quotation workspace and platform administration

Prepared: 4 October 2026  
Status: Planned | Sprints S22-S24 | Extends M18 and existing related modules  
Source: [Admin specification](../../docs/13-admin-panel-specification.md)  
Format reference: [Support Reply Assistant PI-08](../../../05-support-reply-assistant/PI/PI-08-admin-panel/README.md)

## Outcome and sprint plan

Deliver scoped administration for distributor onboarding, catalogue/prices, quote governance, subscriptions, job recovery and service operations.

| Sprint | Outcome | Status |
|---|---|---|
| [S22](S22-admin-access-workspaces/sprint-plan.md) | Admin access and workspace management | Planned |
| [S23](S23-admin-catalogue-quote-governance/sprint-plan.md) | Admin catalogue and quotation governance | Planned |
| [S24](S24-admin-commercial-operations/sprint-plan.md) | Admin commerce and operational readiness | Planned |

## Dependencies and ownership

S01/S02 scope and authenticated integration are prerequisites. S22 uses S03/S13 and S14 seat policies where applicable; S23 uses S04-S06/S09-S12; S24 uses S07/S14-S16. Existing sprints retain domain services and invariants. This PI owns administration screens, authorized action orchestration and integrated operator verification, not a second pricing, approval, job or billing engine.

PI numbering is an identifier rather than mandatory calendar order. PI-08 does not depend on optional PI-07. Deliver required access, catalogue/price governance and commercial/operational controls before the S17 paid pilot; S18 includes final admin readiness. S17/S18 evidence can initially appear pending, avoiding circular entry dependencies.

S16 retains infrastructure/recovery service ownership. Coordinate its baseline admin/support work with this PI; reuse existing screens and evidence where available instead of double-counting implementation.

## Scope coverage

| Specification sections | Delivery |
|---|---|
| 1-4: scope, navigation, roles and onboarding | S22 |
| 5-6: catalogue, prices, approval and artifacts | S23 |
| 7-8: jobs, billing, usage and markets | S24 |
| 9-10: support, audit, data lifecycle, health and quality | S22 audit/access foundation; S24 integrated operations |
| 11: APIs | Each sprint's existing service adapters |
| 12-13: acceptance and decisions | All sprints; unresolved decisions stay visible |

## Planning and exit

Three nominal two-week sprints are a sizing convention, not a delivery commitment. Re-estimate overlaps and capacity; split S24 work into tickets or carryovers if necessary without waiving acceptance.

Assign product/domain, frontend, backend/data, Astra integration, QA and operations owners. Every sprint has two feature IDs, six tasks and six acceptance checks. Preserve existing module IDs M01-M22.

Exit requires the admin checklist, tenant/role negative checks, immutable pricing/approval/export evidence, usage/job reconciliation, deletion/restore drill and named reviewer decisions. Model and target-host qualification remain independent release gates. Documentation does not constitute implementation.

See [roadmap](../README.md), [status](../../_STATUS.md), [coverage](../../docs/12-module-feature-sprint-matrix.md) and [quality requirements](../../docs/07-quality-security-international.md).
