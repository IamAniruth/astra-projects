# DM S11: Astra retrieval and migration capability training

**Status:** Planned  
**PI:** [PI-04](../README.md)  
**Module:** M04  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver astra retrieval and migration capability training within the explicitly supported migration scope.

- DM-S11-F01: Evidence-grounded proposals
- DM-S11-F02: Measured candidate training

## Dependencies and entry criteria

S10 corpus and baseline; Astra training ownership. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S11-T01 | Implement the local model adapter with bounded retrieved evidence and externally validated structured output. |
| DM-S11-T02 | Train controlled candidates in Astra under its checkpoint/data gates; record one-change comparisons, actual parameter count, tokenizer/configuration, mask checks, precision support and measured memory/throughput against guide 16's proposed ranges. |
| DM-S11-T03 | Evaluate candidates on frozen tasks and qualify only passing mapping families. |
| DM-S11-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S11-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S11-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S11-AC1: Model outputs have no authority to run arbitrary SQL, widen scope or waive validation.
- [ ] DM-S11-AC2: Candidate reports compare unchanged, retrieval-only and trained results under identical budgets.
- [ ] DM-S11-AC3: Failed capability or ambiguity gates keep the candidate unqualified regardless of training loss.
- [ ] DM-S11-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S11-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S11-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Follow [training/configuration guide 16](../../../docs/16-local-llm-training-datasets-and-configuration.md). Its architecture and hyperparameters are experiments, not existing supported Astra flags. Verify implementation compatibility before each run; retain failure evidence and quantify held-out accuracy, first-attempt structured validity, ambiguity behavior and report fidelity. No own-model replacement or hardware purchase is implied.

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Propose a mapping with grounded evidence and abstain on an undocumented status code.

## Required PI scope from documents 16-19

**Sources:** [Doc 16](../../../docs/16-local-llm-training-datasets-and-configuration.md), [Doc 18](../../../docs/18-operational-lifecycle-and-product-acceptance.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S11-T07 | Run supported Astra configuration experiments with measured parameter/tokenizer/memory/throughput manifests and model lifecycle records. |
| DM-S11-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S11-AC7: Candidate quality, structured validity and ambiguity behavior meet registered gates before promotion; unsupported configs and failed candidates remain unqualified.
- [ ] DM-S11-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
