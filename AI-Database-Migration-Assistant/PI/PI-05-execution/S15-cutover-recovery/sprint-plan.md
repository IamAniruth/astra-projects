# DM S15: Cutover controller and recovery boundaries

**Status:** Planned  
**PI:** [PI-05](../README.md)  
**Module:** M05  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver cutover controller and recovery boundaries within the explicitly supported migration scope.

- DM-S15-F01: Write-fenced switch
- DM-S15-F02: Before/after-write recovery

## Dependencies and entry criteria

S14 passed checks; measured restore evidence. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S15-T01 | Implement maintenance/write fencing and durable routing-switch intent/state reconciliation. |
| DM-S15-T02 | Test read-only post-switch acceptance before explicitly enabling target writes. |
| DM-S15-T03 | Implement pre-write return and post-write recovery-required flows with retained target changes. |
| DM-S15-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S15-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S15-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S15-AC1: Any bypass source writer or stale plan blocks cutover before target writes are enabled.
- [ ] DM-S15-AC2: A crash at each switch phase is reconciled from actual routing and database write state.
- [ ] DM-S15-AC3: Post-write recovery never silently discards new target records by restoring the old source.
- [ ] DM-S15-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S15-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S15-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Fail read-only checks and return safely; then demonstrate the distinct post-write recovery state.

## Required PI scope from documents 16-19

**Sources:** [Doc 17](../../../docs/17-application-readiness-and-data-boundaries.md), [Doc 18](../../../docs/18-operational-lifecycle-and-product-acceptance.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S15-T07 | Implement qualified or explicitly assisted application cutover, integration fences and recovered routing/write-authority reconciliation. |
| DM-S15-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S15-AC7: Crash and bypass-writer scenarios preserve known authority; post-write recovery retains new records and never reports an unverified lossless rollback.
- [ ] DM-S15-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
