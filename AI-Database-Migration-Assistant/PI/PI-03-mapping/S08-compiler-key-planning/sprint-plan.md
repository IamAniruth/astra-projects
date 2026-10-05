# DM S08: Deterministic compiler and identity planning

**Status:** Planned  
**PI:** [PI-03](../README.md)  
**Module:** M03  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver deterministic compiler and identity planning within the explicitly supported migration scope.

- DM-S08-F01: Validated execution plans
- DM-S08-F02: Keys and dependency ordering

## Dependencies and entry criteria

S07 validated mapping contract. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S08-T01 | Compile allowlisted transformations with typed parameters and safe identifier handling. |
| DM-S08-T02 | Plan entity order, composite keys, transactional ID mapping and supported cycle handling. |
| DM-S08-T03 | Bind compiler/plugin/schema/policy hashes and reject nondeterministic or unqualified custom code. |
| DM-S08-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S08-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S08-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S08-AC1: Repeated compilation of the same pinned input has the same semantic plan and declared stable hash.
- [ ] DM-S08-AC2: Money overflow, null violations, ambiguous timezone conversion and dependency cycles fail explicitly.
- [ ] DM-S08-AC3: Generated plans cannot write outside the authorized target scope or execute arbitrary model code.
- [ ] DM-S08-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S08-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S08-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Compile the customer/order recipe and reject an injected SQL identifier and unsafe cast.

## Required PI scope from documents 16-19

**Sources:** [Doc 17](../../../docs/17-application-readiness-and-data-boundaries.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S08-T07 | Compile the accepted loss/scope policy and required dependency closure into executable preconditions. |
| DM-S08-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S08-AC7: Unsafe casts, unapproved cleanup and incompatible mapping/ID namespaces are rejected before target writes.
- [ ] DM-S08-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
