# DM S18: Pilot acceptance and qualified release

**Status:** Planned  
**PI:** [PI-06](../README.md)  
**Module:** M06  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver pilot acceptance and qualified release within the explicitly supported migration scope.

- DM-S18-F01: Scoped customer pilot
- DM-S18-F02: Release and operating handover

## Dependencies and entry criteria

All applicable gates; actual customer authorization. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S18-T01 | Execute the scoped pilot with named owners and preserve actual outcomes including failures. |
| DM-S18-T02 | Publish exact support matrix, model/recipe scope, recovery limits, cost and review-time evidence. |
| DM-S18-T03 | Deliver installation/operation/recovery guidance and decide assisted versus unattended release claims. |
| DM-S18-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S18-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S18-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S18-AC1: Every mandatory release gate has actual evidence and a named acceptance decision.
- [ ] DM-S18-AC2: Customer application workflows and row dispositions pass for the final production snapshot.
- [ ] DM-S18-AC3: Published automation claims match qualified recipes; failed/general tasks remain explicitly unsupported.
- [ ] DM-S18-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S18-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S18-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Review the evidence pack with the customer and hand over a reproducible operating procedure.

## Required PI scope from documents 16-19

**Sources:** [Doc 17](../../../docs/17-application-readiness-and-data-boundaries.md), [Doc 18](../../../docs/18-operational-lifecycle-and-product-acceptance.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S18-T07 | Close the scoped pilot with application-readiness evidence, observation, incident ownership, handover and a decision for every applicable gap. |
| DM-S18-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S18-AC7: All applicable GAP-01 through GAP-12 obligations have accepted evidence; unresolved required gaps block release; exclusions and source-decommission boundaries are explicit.
- [ ] DM-S18-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
