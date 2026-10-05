# DM S01: Customer scope and migration contract

**Status:** Planned  
**PI:** [PI-01](../README.md)  
**Module:** M01  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver customer scope and migration contract within the explicitly supported migration scope.

- DM-S01-F01: Scope and intake
- DM-S01-F02: Pilot success and exclusions

## Dependencies and entry criteria

None; actual customer inputs can replace the proposed pair. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S01-T01 | Inventory the first old/new applications, engines, volume, tenants, side effects and maintenance constraints. |
| DM-S01-T02 | Agree domain ownership, explicit exclusions, recovery objectives and the first supported engine profile. |
| DM-S01-T03 | Register pilot success equations, independent fixtures and unanswered business questions. |
| DM-S01-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S01-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S01-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S01-AC1: A source/target scope manifest names actual versions or marks them unconfirmed; unsupported objects are visible.
- [ ] DM-S01-AC2: Domain and release owners accept success/recovery criteria without assuming zero downtime.
- [ ] DM-S01-AC3: Every material intake unknown has an owner; no production readiness is claimed from assumptions.
- [ ] DM-S01-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S01-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S01-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Walk one customer record and its order from old app meaning to target expectations.

## Required PI scope from documents 16-19

**Sources:** [Doc 17](../../../docs/17-application-readiness-and-data-boundaries.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S01-T07 | Record authorized dependency scope, application-readiness boundaries and GAP-01 ownership in the customer migration contract. |
| DM-S01-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S01-AC7: Filtered-scope examples identify related/shared records and reject unauthorized tenant expansion; assigned gap decisions accompany intake.
- [ ] DM-S01-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
