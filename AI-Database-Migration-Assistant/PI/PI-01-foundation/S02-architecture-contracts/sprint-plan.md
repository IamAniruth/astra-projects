# DM S02: Service architecture and integration ownership

**Status:** Planned  
**PI:** [PI-01](../README.md)  
**Module:** M01  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver service architecture and integration ownership within the explicitly supported migration scope.

- DM-S02-F01: Control and data planes
- DM-S02-F02: Astra and commercial integration

## Dependencies and entry criteria

S01 scope. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S02-T01 | Inspect actual Astra job, evaluation, retrieval and adapter interfaces before deciding reuse. |
| DM-S02-T02 | Define immutable plan, execution, evidence and API contracts with explicit authority per component. |
| DM-S02-T03 | Implement contracts for the accepted React/Next.js UI, Next.js application APIs, Python migration workers and local Astra; pin versions/deployment options and enforce model-no-write and worker-scope boundaries. |
| DM-S02-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S02-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S02-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S02-AC1: Every state/effect has one owner, including target commit receipts versus control-plane projections.
- [ ] DM-S02-AC2: No second identity, billing or usage authority is introduced alongside adopted WS services.
- [ ] DM-S02-AC3: Contract examples distinguish unsupported, stale, ambiguous and unknown-outcome errors.

Additional stack acceptance: job admission returns a durable operation ID; closing the browser or restarting Next.js does not terminate accepted Python work; repeated submissions reconcile to one logical operation. Python remains the migration execution authority and Next.js exposes authorized commands/progress. See [accepted architecture](../../../docs/02-architecture-and-integration.md).
- [ ] DM-S02-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S02-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S02-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Trace discovery through model proposal, plan compiler, target worker and evidence report.

## Required PI scope from documents 16-19

**Sources:** [Doc 18](../../../docs/18-operational-lifecycle-and-product-acceptance.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S02-T07 | Define release/metadata compatibility, install preflight contracts and the delivery/evidence owner for operating requirements. |
| DM-S02-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S02-AC7: Architecture identifies pinned artifact identities, upgrade/resume rules and accountable evidence owners for GAP-06/GAP-11.
- [ ] DM-S02-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
