# DM S07: Mapping language and review registry

**Status:** Planned  
**PI:** [PI-03](../README.md)  
**Module:** M03  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver mapping language and review registry within the explicitly supported migration scope.

- DM-S07-F01: Entity and field mapping
- DM-S07-F02: Immutable review and recipe versions

## Dependencies and entry criteria

S06 evidence model. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S07-T01 | Define and validate the DSL schema, entity cardinality, transform allowlist and full field coverage. |
| DM-S07-T02 | Implement immutable mapping versions, provenance, ambiguity questions and reviewer decisions. |
| DM-S07-T03 | Specify recipe fingerprints, configurable fields and compatibility/domain checks. |
| DM-S07-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S07-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S07-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S07-AC1: Missing required target fields, hallucinated columns and unsupported transform operators are rejected.
- [ ] DM-S07-AC2: Changing a resolved business rule creates a new version and invalidates dependent accepted plans.
- [ ] DM-S07-AC3: Duplicate source IDs across tenants remain distinct; email similarity never causes an implicit merge.
- [ ] DM-S07-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S07-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S07-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Review an enum mapping and show how a later new status invalidates recipe reuse.

## Required PI scope from documents 16-19

**Sources:** [Doc 17](../../../docs/17-application-readiness-and-data-boundaries.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S07-T07 | Version dependency-scope, lossy-conversion and application-default decisions with mapping review and compatibility evidence. |
| DM-S07-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S07-AC7: Rounding, truncation, merge and invented-default proposals cannot become accepted executable rules without their explicit disposition.
- [ ] DM-S07-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
