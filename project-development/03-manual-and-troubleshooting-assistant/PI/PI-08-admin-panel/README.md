# PI-08: Manual and troubleshooting administration

Prepared: 4 October 2026  
Status: Planned | Modules M22-M24 | Sprints S22-S24  
Source: [Admin specification](../../docs/09-admin-panel-specification.md)  
Structure reference: [Support Reply PI-08](../../../05-support-reply-assistant/PI/PI-08-admin-panel/README.md)

## Objective and sprints

Deliver scoped administration for sites/equipment, approved manual lifecycle, procedure governance, team subscriptions and service operations.

| Sprint | Outcome | Status |
|---|---|---|
| [S22](S22-admin-sites-equipment-access/sprint-plan.md) | Admin sites, equipment and access | Planned |
| [S23](S23-admin-manual-procedure-governance/sprint-plan.md) | Admin manual and procedure governance | Planned |
| [S24](S24-admin-commercial-operations/sprint-plan.md) | Admin commerce and operational readiness | Planned |

## Dependencies and scheduling

S01 discovery and S02 feasibility remain gates. S22 uses S03/S13; S23 uses S04-S12 with S14 qualification; S24 uses S06/S13-S15. Earlier sprints own domain services. This PI owns admin UI, authorized orchestration and integrated verification without duplicating source approval, retrieval, procedure, job or usage authorities.

PI numbering is not calendar order. PI-08 does not depend on optional PI-07 or a completed launch. Required controls precede the S17 paid pilot; S18 consumes final administration evidence. S16-S18 readiness records can remain pending during development without circular prerequisites.

Three nominal two-week sprints are sizing containers. Re-estimate overlap with existing service work and staffing, especially S24. Split into tickets/carryovers if needed without waiving checks.

## Coverage

| Specification sections | Owner/evidence |
|---|---|
| 1-4: scope, screens, access and site/equipment onboarding | S22 permission and context-change evidence |
| 5-7: publication, applicability, withdrawal, procedures and escalation | S23 lifecycle/race and domain-review evidence |
| 8-9: jobs, service billing and supported scope | S24 reconciliation, usage and qualification evidence |
| 10: audit, retention and health | S22 access/audit foundation; S24 full operations and recovery |
| 11: quality/improvement | S24 actual-evidence view; optional improvement stays S19-S21 |
| 12-14: API contracts, acceptance and decisions | All three with named owners and versioned records |

## Exit and handoff

Execute the specification checklist and permitted upload-review-publish-query-cite-escalate-withdraw flow. Verify current grants, applicability, mandatory procedure context, withdrawal races, billing/job settlement and restore behavior. Record actual versions, failures, limits and named reviewer decisions.

Critical unsupported procedural guidance or access leaks block applicable release until remediation/re-evaluation. No automatic equipment action, invented repair, expert-feedback publication, external messaging or training is introduced.

See [roadmap](../README.md), [status](../../_STATUS.md), [coverage](../../docs/03-module-feature-sprint-matrix.md) and [quality requirements](../../docs/06-quality-security-operations.md). This PI is planning, not implementation evidence.
