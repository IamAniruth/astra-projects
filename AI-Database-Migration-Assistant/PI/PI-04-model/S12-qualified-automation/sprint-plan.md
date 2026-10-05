# DM S12: Qualified recipes and bounded agent repair

**Status:** Planned  
**PI:** [PI-04](../README.md)  
**Module:** M04  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver qualified recipes and bounded agent repair within the explicitly supported migration scope.

- DM-S12-F01: Automatic recipe execution
- DM-S12-F02: Restricted rehearsal repair

## Dependencies and entry criteria

S11 passing families; S09 runner. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S12-T01 | Implement preflight compatibility checks and automatic execution under existing scoped authorization. |
| DM-S12-T02 | Allow bounded candidate repairs only in disposable environments with fixed independent checks. |
| DM-S12-T03 | Track failed attempts, escalation reasons and unattended completion denominator. |
| DM-S12-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S12-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S12-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S12-AC1: Matching qualified recipes execute without needless repeated mapping approval.
- [ ] DM-S12-AC2: Changed policy, new status, revoked authority or drift stops unattended execution.
- [ ] DM-S12-AC3: The repair loop cannot remove failing assertions, drop unexplained records or alter production.
- [ ] DM-S12-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S12-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S12-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Run a compatible repeat fixture automatically, then stop one with a new status value.

## Required PI scope from documents 16-19

**Sources:** [Doc 16](../../../docs/16-local-llm-training-datasets-and-configuration.md), [Doc 18](../../../docs/18-operational-lifecycle-and-product-acceptance.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S12-T07 | Qualify evidence-grounded recipe automation and implement recipe/model revocation, impact tracing and reviewed correction flow. |
| DM-S12-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S12-AC7: A revoked version cannot admit new affected work; compatible stored recipes honor scoped authority; bounded repairs cannot weaken oracles or auto-train on customer data.
- [ ] DM-S12-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
