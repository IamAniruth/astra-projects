# DM S13: Durable execution, fencing and resume

**Status:** Planned  
**PI:** [PI-05](../README.md)  
**Module:** M05  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver durable execution, fencing and resume within the explicitly supported migration scope.

- DM-S13-F01: Target commit receipts
- DM-S13-F02: Interruption and concurrent worker handling

## Dependencies and entry criteria

S09 protocol; S12 accepted recipe contract. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S13-T01 | Implement worker leases with target-enforced fencing and versioned lifecycle transitions. |
| DM-S13-T02 | Reconcile control-plane checkpoints from target receipts after crashes and lost responses. |
| DM-S13-T03 | Implement pause/resume/cancel and resource-limit handling with honest committed-state reporting. |
| DM-S13-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S13-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S13-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S13-AC1: Process kills before/after commit produce neither duplicates nor falsely completed batches.
- [ ] DM-S13-AC2: A stale worker cannot commit after a replacement worker acquires the fenced lease.
- [ ] DM-S13-AC3: Snapshot loss triggers a deliberate restart/replan, not unsafe cursor reuse.
- [ ] DM-S13-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S13-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S13-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Kill a worker after target commit and resume using the persisted receipt.

## Required PI scope from documents 16-19

**Sources:** [Doc 18](../../../docs/18-operational-lifecycle-and-product-acceptance.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S13-T07 | Implement full-system receipt reconciliation, compatible resume, bounded queues and safe pause of jobs affected by resource limits or revocation. |
| DM-S13-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S13-AC7: Restored stale journals, incompatible versions, worker replacement and quota/stop scenarios have explicit outcomes without duplicate committed effects.
- [ ] DM-S13-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
