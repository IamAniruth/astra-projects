# DM S05: Target database and application contract

**Status:** Planned  
**PI:** [PI-02](../README.md)  
**Module:** M02  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver target database and application contract within the explicitly supported migration scope.

- DM-S05-F01: Target schema inventory
- DM-S05-F02: Application behavior evidence

## Dependencies and entry criteria

S04 catalog format; target app commit available. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S05-T01 | Inspect target schema/ORM/migrations, required fields, identity allocation, constraints and external side effects. |
| DM-S05-T02 | Create isolated run-owned target provisioning and exact target identity checks. |
| DM-S05-T03 | Define target application acceptance scenarios and prevent side effects during rehearsal. |
| DM-S05-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S05-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S05-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S05-AC1: All required target fields and supported object types have a recorded requirement or unresolved question.
- [ ] DM-S05-AC2: A populated or incorrectly identified destination is rejected under the first-release policy.
- [ ] DM-S05-AC3: Rehearsals cannot send emails, charge payments or mutate unrelated application services.
- [ ] DM-S05-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S05-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S05-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Create disposable target storage and run the target app against synthetic records.

## Required PI scope from documents 16-19

**Sources:** [Doc 17](../../../docs/17-application-readiness-and-data-boundaries.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S05-T07 | Define required attachment/authentication/derived-state dispositions and the application fence/routing/readiness adapter. |
| DM-S05-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S05-AC7: The target readiness contract includes all required non-row objects and distinguishes qualified automation from assisted cutover.
- [ ] DM-S05-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
