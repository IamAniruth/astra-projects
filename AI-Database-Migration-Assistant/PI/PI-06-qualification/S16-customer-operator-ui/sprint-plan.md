# DM S16: Customer workflows and operator controls

**Status:** Planned  
**PI:** [PI-06](../README.md)  
**Module:** M06  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver customer workflows and operator controls within the explicitly supported migration scope.

- DM-S16-F01: Mapping and run interface
- DM-S16-F02: Evidence and support operations

## Dependencies and entry criteria

S12/S15 API contracts. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S16-T01 | Build every step in guide 10's end-to-end workflow using React/TypeScript through Next.js: intake, connections, evidence, discovery, mapping/questions, rehearsal, validation, scheduling/authorization, run controls, cutover, recovery, reports and recipe reuse. |
| DM-S16-T02 | Implement operator diagnostics and scoped reports without revealing database secrets or raw data by default. |
| DM-S16-T03 | Connect Next.js application APIs to the authoritative identity and Python migration services plus optional WS adapter; use idempotent operation IDs and durable progress with reconnect. |
| DM-S16-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S16-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S16-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S16-AC1: UI distinguishes suggested, approved, committed, validated and completed states accurately.
- [ ] DM-S16-AC2: Denied/stale/repeated requests are enforced server-side, including report and support access.
- [ ] DM-S16-AC3: A nontechnical reviewer can resolve an ambiguity and understand why cutover is blocked.
- [ ] DM-S16-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S16-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S16-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

UI acceptance includes all twelve steps in [workflow coverage](../../../docs/10-user-and-admin-workflows.md). Demonstrate browser close/reopen and Next.js restart during a running Python job, authorized progress recovery, model unavailability, scheduled-window expiry, stale mapping edits and the distinct post-write recovery state. Normal supported workflows require no terminal; administrator-only infrastructure/emergency boundaries remain explicit.

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Complete a customer journey and attempt an unauthorized support export.

## Required PI scope from documents 16-19

**Sources:** [Doc 16](../../../docs/16-local-llm-training-datasets-and-configuration.md), [Doc 17](../../../docs/17-application-readiness-and-data-boundaries.md), [Doc 18](../../../docs/18-operational-lifecycle-and-product-acceptance.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S16-T07 | Expose all supported model, mapping, readiness, operating and recovery states in the React/Next.js workflow, including large-schema and export behavior. |
| DM-S16-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S16-AC7: Keyboard journey, pagination, concurrent edits, model failure, browser/API restart and protected-export tests pass across the complete migration workflow.
- [ ] DM-S16-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
