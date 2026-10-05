# DM S10: Astra baseline and licensed migration corpus

**Status:** Planned  
**PI:** [PI-04](../README.md)  
**Module:** M04  
**Cadence:** nominal two weeks; owner/capacity estimate not assigned  
**Source:** [Product specification](../../../AI-Database-Migration-Assistant-Specification.md)

## Objective and features

Deliver astra baseline and licensed migration corpus within the explicitly supported migration scope.

- DM-S10-F01: Frozen task benchmark
- DM-S10-F02: Licensed training examples

## Dependencies and entry criteria

S09 executable oracle; Astra checkpoint access. Confirm permitted fixture/customer inputs, named reviewers, exact interface versions and environment. Planning assumptions are not implementation evidence.

## Implementation backlog

| Task | Deliverable |
|---|---|
| DM-S10-T01 | Register independent schema-family splits, critical negative cases and evaluation budgets. |
| DM-S10-T02 | Measure the unchanged Astra checkpoint against human-authored template baseline. |
| DM-S10-T03 | Build provenance-tracked training/validation examples while isolating locked test families; register guide 16's proposed category mix, sample and token counts, licence decisions and realized family split. |
| DM-S10-T04 | Version the affected contracts/configuration; bind evidence to exact source, target, mapping and implementation identities. |
| DM-S10-T05 | Exercise the sprint-specific negative cases and relevant stale/concurrent/repeated/denied operations; retain failures and recovery outcomes. |
| DM-S10-T06 | Review both features with the responsible domain/engineering owner; update status, evidence and unresolved dependencies from actual results. |

Suggested ownership: product/domain owner for meaning and scope, database/backend engineer for execution contracts, model engineer for inference/training work, QA for independent checks and operator for host/recovery. Assign actual people before starting; model work does not authorize changes to Astra platform roadmap status.

## Acceptance criteria

- [ ] DM-S10-AC1: Baseline reports all failures and abstentions with actual model/tokenizer hashes and host details.
- [ ] DM-S10-AC2: Renamed or generated variants of a schema family cannot cross train/test boundaries.
- [ ] DM-S10-AC3: No customer examples are used for training without distinct recorded permission.
- [ ] DM-S10-AC4: Evidence identifies exact inputs, versions, scope and real versus simulated environment; no unrun check is marked passed.
- [ ] DM-S10-AC5: Applicable authority, data minimization and failure/recovery requirements pass; non-applicable checks have an explicit reason.
- [ ] DM-S10-AC6: A named owner accepts both features against evidence; unresolved prerequisites remain visible and block dependent production claims.

## Test and evidence plan

Use [training guide 16](../../../docs/16-local-llm-training-datasets-and-configuration.md) for separately accounted foundation-token, SFT-example and optional preference-pair percentages. Start with a reviewed small corpus, audit primary-category counts and overlapping tags, and document deviations from proposed ratios. Public SQL benchmarks do not replace independent migration fixtures.

Apply [release gates](../../../docs/03-quality-and-release-gates.md) and [benchmark design](../../../docs/09-evaluation-and-benchmark-plan.md). Use real pinned database engines for connector/transaction claims; mocks only for isolated orchestration. Planning-only tasks produce reviewed contracts and decisions, not fabricated test outcomes. Capture fixture hashes, actual checks/results, failure traces with redaction, known limitations and reviewer decision in the [evidence template](../../../templates/release-evidence.md).

## Sprint demonstration

Show a current-model failure and the independent oracle that detected it.

## Required PI scope from documents 16-19

**Sources:** [Doc 16](../../../docs/16-local-llm-training-datasets-and-configuration.md), [Doc 18](../../../docs/18-operational-lifecycle-and-product-acceptance.md), [Doc 19](../../../docs/19-gap-review-and-acceptance-register.md)  
**PI traceability:** [Document delivery matrix](../../documents-16-19-delivery.md)

| Task | Deliverable |
|---|---|
| DM-S10-T07 | Register separate pretraining-token, SFT-example and optional preference-pair mixes, family splits, licence/provenance records and correction-data policy. |
| DM-S10-T08 | Attach actual evidence and named decisions for the assigned document/gap requirements to this sprint review and the PI exit record. |

- [ ] DM-S10-AC7: Each chosen stage totals 100%; held-out families stay isolated; actual sample/token counts and baseline results are recorded; unconsented corrections stay outside training.
- [ ] DM-S10-AC8: All applicable document/gap requirements assigned here have evidence and a reviewer decision; unresolved mandatory work prevents sprint acceptance.

These extend the two existing feature scopes. They are mandatory implementation/qualification work, not already-completed documentation. Re-estimate sprint capacity; optional/deferred items in the source documents remain optional/deferred and must not be reported as implemented.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md). Preserve incomplete scope and the next consumer's prerequisites. No source cleanup, deployment or production access is implied by accepting a documentation artifact.
