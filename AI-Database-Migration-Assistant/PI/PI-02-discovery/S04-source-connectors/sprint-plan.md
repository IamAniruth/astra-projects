# DM S04: Source connector and consistent extraction

**Status:** Planned  
**PI:** [PI-02](../README.md)  
**Module:** M02  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver source connector and consistent extraction within the explicitly supported migration scope.

- DM-S04-F01: Catalog discovery
- DM-S04-F02: Pinned snapshot extraction

## Dependencies and entry criteria

S03 boundaries; S01 engine profile. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S04-T01 | Build the first source connector with version/type/object capability reports and scoped read privileges. |
| DM-S04-T02 | Implement freeze/snapshot identity and stable keyset extraction with a no-stable-key fallback policy. |
| DM-S04-T03 | Test snapshot expiry, DDL drift and revoked connection behavior on the pinned real engine. |
| DM-S04-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S04-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S04-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S04-AC1: Catalog inventory includes keys, triggers, routines and unsupported objects rather than only tables.
- [ ] DM-S04-AC2: A full extraction represents one documented consistent source state with a reproducible identity.
- [ ] DM-S04-AC3: Expired snapshot or schema drift blocks resume instead of continuing an old cursor against new data.
- [ ] DM-S04-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S04-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S04-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Discover a real fixture engine and prove a schema change invalidates the snapshot plan.

## Required PI scope from documents 16-19

**Sources:** [Doc 18](../../../docs/18-operational-lifecycle-and-product-acceptance.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S04-T07 | Implement bounded source queries, extraction limits and source-load monitoring with explicit pause conditions. |
| DM-S04-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S04-AC7: Timeout, slow-source and budget-exhaustion cases stop safely and cannot exceed the authorized source scope.
- [ ] DM-S04-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
