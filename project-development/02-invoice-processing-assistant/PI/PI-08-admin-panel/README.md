# PI-08: Invoice workspace and platform administration

Prepared: 4 October 2026  
Status: Planned | Modules M22-M24 | Sprints S22-S24  
Source: [Admin specification](../../docs/09-admin-panel-specification.md)  
Structure reference: [Support Reply PI-08](../../../05-support-reply-assistant/PI/PI-08-admin-panel/README.md)

## Objective and sprint list

Deliver scoped administration for accounting workspaces/client companies, invoice governance, service subscriptions and recovery.

| Sprint | Outcome | Status |
|---|---|---|
| [S22](S22-admin-access-clients/sprint-plan.md) | Admin access and client management | Planned |
| [S23](S23-admin-invoice-governance/sprint-plan.md) | Admin invoice and export governance | Planned |
| [S24](S24-admin-commercial-operations/sprint-plan.md) | Admin commerce and operational readiness | Planned |

## Dependencies and scheduling

S01/S02 discovery and feasibility remain gates. S22 uses S03/S13; S23 uses S04-S12 with S14 profile qualification; S24 uses S06/S13-S15. Earlier sprints retain domain-service ownership. This PI owns admin presentation, authorized action orchestration and integrated operator verification, not duplicate approval, PO allocation, job or usage engines.

PI numbering does not require waiting until after launch or optional PI-07. Schedule required access, invoice governance and commercial/operational controls before the S17 paid pilot; S18 consumes final administration evidence. Quality views initially show pending S16-S18 results, avoiding a circular entry dependency.

Three nominal two-week sprints are planning containers. If fully sequential, administration adds six weeks; re-estimate overlap, staffing and capacity at kickoff, especially S24. Carry incomplete work explicitly rather than waive acceptance.

## Specification coverage

| Sections | Owner and evidence |
|---|---|
| 1-4: scope, screens, roles, clients and intake | S22 identity/onboarding; S23 detailed intake diagnostics |
| 5-7: profiles, duplicates, PO allocations, approval/export | S23 domain, concurrency and artifact evidence |
| 8-9: jobs, service billing and markets | S24 reconciliation/ledger/qualification evidence |
| 10: audit, privacy and health | S22 access/audit foundation; S24 recovery/data lifecycle |
| 11: quality/improvement | S24 actual-evidence view; optional improvement remains S19-S21 |
| 12-14: APIs, acceptance and decisions | All three, with named owners and versioned evidence |

## Exit

Run the complete admin checklist plus meaningful access, arithmetic, allocation, approval, export and recovery checks. Retain actual application/configuration/model/parser/host versions and independent reviewer decisions. No cross-client disclosure, unresolved critical approval issue, duplicate allocation/usage effect or unsafe export may be hidden by downstream acceptance.

Administration does not authorize ledger posting, invoice payment, supplier-bank changes, autonomous tax determination or training. These plans do not claim implementation, qualification or deployment.

See [roadmap](../README.md), [status](../../_STATUS.md), [coverage](../../docs/03-module-feature-sprint-matrix.md) and [quality requirements](../../docs/06-quality-security-operations.md).
