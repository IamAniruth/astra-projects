# DM S17: Target-host capacity, security and restore qualification

**Status:** Planned  
**PI:** [PI-06](../README.md)  
**Module:** M06  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver target-host capacity, security and restore qualification within the explicitly supported migration scope.

- DM-S17-F01: Real-host performance
- DM-S17-F02: Security and disaster recovery

## Dependencies and entry criteria

S15/S16 integrated release candidate. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S17-T01 | Measure representative source load, throughput, memory, storage and maintenance-window fit. |
| DM-S17-T02 | Run complete backup/restore and process-kill/network/disk failure scenarios on the intended host. |
| DM-S17-T03 | Audit local-only data paths, permissions, redaction, retention and upgrade/resume compatibility. |
| DM-S17-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S17-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S17-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S17-AC1: Capacity and recovery claims name measured host, versions, volume and uncertainty.
- [ ] DM-S17-AC2: An actual restored database passes integrity/app checks; a backup exit code alone is insufficient.
- [ ] DM-S17-AC3: Cross-tenant, egress, secret exposure and owned-artifact cleanup tests meet recorded requirements.
- [ ] DM-S17-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S17-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S17-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Restore the target from backup and run the customer acceptance workflows.

## Required PI scope from documents 16-19

**Sources:** [Doc 16](../../../docs/16-local-llm-training-datasets-and-configuration.md), [Doc 17](../../../docs/17-application-readiness-and-data-boundaries.md), [Doc 18](../../../docs/18-operational-lifecycle-and-product-acceptance.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S17-T07 | Qualify actual model/worker capacity, installation preflight, offline boundaries, full-system restore, upgrades and source/resource limits on the target host. |
| DM-S17-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S17-AC7: Recorded real-host tests restore metadata/receipts/ID maps/routing with workers disabled; runtime quality and upgrade compatibility are measured rather than inferred.
- [ ] DM-S17-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
