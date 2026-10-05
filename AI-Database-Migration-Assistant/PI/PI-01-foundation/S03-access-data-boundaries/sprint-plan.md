# DM S03: Access, secrets and local data boundaries

**Status:** Planned  
**PI:** [PI-01](../README.md)  
**Module:** M01  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver access, secrets and local data boundaries within the explicitly supported migration scope.

- DM-S03-F01: Scoped access
- DM-S03-F02: Retention and isolation

## Dependencies and entry criteria

S02 contracts. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S03-T01 | Implement tenant/project roles and secret references separate from prompts, plans and browser state. |
| DM-S03-T02 | Enforce scoped source/target connection policies and worker/model network boundaries. |
| DM-S03-T03 | Implement audit/redaction and per-artifact retention with source-safe cleanup boundaries. |
| DM-S03-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S03-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S03-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S03-AC1: A cross-tenant project ID or destination substitution is rejected server-side and in worker execution.
- [ ] DM-S03-AC2: Secrets and sensitive sample values do not appear in model requests, ordinary logs or exported reports.
- [ ] DM-S03-AC3: Revocation and untrusted repository instructions cannot grant database-write or network privileges.
- [ ] DM-S03-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S03-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S03-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Attempt forbidden destination access and inspect the redacted audit trail.

## Required PI scope from documents 16-19

**Sources:** [Doc 18](../../../docs/18-operational-lifecycle-and-product-acceptance.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S03-T07 | Implement bootstrap/secret ownership, backup-key custody and scoped diagnostic/retention access from the operating lifecycle. |
| DM-S03-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S03-AC7: Bootstrap, key recovery and support access are reviewed and denied-access checks pass without credentials appearing in diagnostics.
- [ ] DM-S03-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
