# DM S06: Data profiling and code-grounded evidence

**Status:** Planned  
**PI:** [PI-02](../README.md)  
**Module:** M02  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver data profiling and code-grounded evidence within the explicitly supported migration scope.

- DM-S06-F01: Data quality assessment
- DM-S06-F02: Relevant code retrieval

## Dependencies and entry criteria

S04/S05 inventories. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S06-T01 | Profile nulls, ranges, key collisions, tenant links and observed status domains with sample/full labels. |
| DM-S06-T02 | Retrieve bounded schema/code fragments with repository commits and stable evidence identifiers. |
| DM-S06-T03 | Produce assessment reports identifying contradictions, sensitive fields and missing semantics. |
| DM-S06-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S06-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S06-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S06-AC1: Sampled uniqueness or relationship coverage is never presented as a complete-data guarantee.
- [ ] DM-S06-AC2: Every retrieved code assertion resolves to an allowed pinned repository location.
- [ ] DM-S06-AC3: Unknown statuses, case-fold collisions and cross-tenant relationships appear as explicit issues.
- [ ] DM-S06-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S06-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S06-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Assess the worked fixture including its missing customer and unexpected status.

## Required PI scope from documents 16-19

**Sources:** [Doc 17](../../../docs/17-application-readiness-and-data-boundaries.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S06-T07 | Compute full-snapshot dependency closure and expose unauthorized references or missing application-readiness inputs. |
| DM-S06-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S06-AC7: Tenant/date-filter fixtures find missing or cross-tenant dependencies without silently widening extraction scope.
- [ ] DM-S06-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
