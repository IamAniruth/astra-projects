# PI-08: Workspace and platform administration

Prepared: 4 October 2026  
Status: Planned | Modules M22-M24 | Sprints S22-S24  
Source: [Admin panel specification](../../docs/09-admin-panel-specification.md)

## Objective

Deliver the authenticated workspace and platform administration surfaces for Support Reply Assistant: scoped access, approved knowledge, review history, safe recovery, entitlements and operational accountability.

| Sprint | Outcome | Status |
|---|---|---|
| [S22](S22-admin-access-workspaces/sprint-plan.md) | Admin shell, scoped access, teams and workspace onboarding | Planned |
| [S23](S23-admin-knowledge-governance/sprint-plan.md) | Knowledge publication, imports and reply-governance controls | Planned |
| [S24](S24-admin-commercial-operations/sprint-plan.md) | Jobs, billing, usage, audit, recovery and readiness | Planned |

## Dependencies and scheduling

S01 discovery and S02 feasibility remain entry gates. PI numbering identifies the planning package, not mandatory calendar order: PI-08 does not depend on optional PI-07 or require waiting until after launch.

S22 depends on S03 identity/grant contracts; S23 depends on S04-S12 ingestion, knowledge, job and review contracts; S24 depends on S06/S09 job ownership, S13 entitlements, S14 qualified settings and S15 operations. Quality views consume S16-S18 evidence as it becomes available; they must display pending states before that evidence exists.

Earlier sprints own domain services and their invariants. This PI owns the administration screens, authorized action orchestration, and integrated operator acceptance. Reuse accepted services and evidence rather than rebuild or double-count them. Coordinate work with the owning sprints; missing dependencies stay explicit.

Required access, knowledge, recovery and applicable commercial/operational controls must be accepted before the S17 paid pilot. S18 includes the integrated admin release decision. Admin readiness evidence can feed S16-S18; their completed acceptance is not an entry dependency, avoiding a circular gate.

Three sprints are planning containers, not a capacity guarantee. If two-week sprints are selected, this is six nominal weeks of additional admin work if staffed sequentially. Re-estimate or split S24 after scope and staffing review; do not waive checks to fit the timebox.

## Scope and boundaries

Use the proposed React/TypeScript frontend, Next.js business APIs and private Astra runtime subject to S02 decisions. Keep workspace and platform permissions separate, preserve case/source grants, and audit privileged reads and changes.

No automatic sending, customer refunds/account changes, ticket closure, unrestricted impersonation, arbitrary model-console commands or automatic training is added. Subscription billing concerns this service's fees only. Optional feedback/model improvement/connectors remain in S19-S21.

## Specification coverage

| Specification sections | Owner | Evidence |
|---|---|---|
| 1-5: scope, navigation, roles, workspace and teams | S22 | Route/API permission matrix, revocation and onboarding demonstrations |
| 6-7: imports, publication, review and handoff | S23 | Publication races, conflict handling and exact-revision export evidence |
| 8-10: jobs, commerce, audit and operations | S24; audit foundations in S22 | Reconciliation, concurrent usage, restore/deletion and incident drills |
| 11: quality and later improvement | S24 evidence view; optional S19-S21 controls deferred | Qualified configuration and pending/failed/accepted evidence states |
| 12: backend contracts | Each sprint for its surfaces | Typed API failures, authorization and idempotency checks |
| 13-15: delivery, acceptance and decisions | All three | Checklist traceability and named decisions |

## Exit and handoff

All three sprint records need concrete implementation evidence, actual versions, named reviewers and outstanding limitations. Run the specification's complete admin checklist and an end-to-end permitted pilot scenario. Any access leak, stale export, duplicate settlement or critical unsupported commitment remains a blocker.

Update [status](../../_STATUS.md), [coverage](../../docs/03-module-feature-sprint-matrix.md) and [roadmap](../README.md) only as evidence supports. This PI document establishes no completed implementation.
