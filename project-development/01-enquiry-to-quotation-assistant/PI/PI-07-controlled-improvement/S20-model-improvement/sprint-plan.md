# EQ S20: Evaluated model improvement and reversible release

**Status:** Planned  
**PI:** [PI-07 Governed learning and qualified expansion](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Optional post-launch enhancement  
**Modules:** M19 M20 M21 M22  
**Astra references:** A09 A10 A12 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Evaluate a consented candidate and promote only a demonstrably better, releasable model.

## User story and features

As the product owner, I can compare a candidate to the current model and roll back safely.

- EQ-S20-F01: Versioned candidate/evaluation evidence and regression gates
- EQ-S20-F02: Signed canary, promotion and rollback integration

## Dependencies and entry criteria

S19 and qualified candidate/training resources; upstream PI-31/34 release gaps may block promotion.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S20-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S20-T02 | React frontend | Restricted operator quality comparison and canary status; customers are informed of meaningful supported-feature changes. |
| EQ-S20-T03 | Next.js/backend | Bind candidate lineage, model artifacts, evaluation reports and release decision; preserve known-good model/prompt compatibility and rollback route. |
| EQ-S20-T04 | Astra integration | Reuse Astra evaluation/promotion contracts; training remains an Astra-owned workstream requiring a capable candidate and real resources. Never treat registry entry as trained/released model. |
| EQ-S20-T05 | Data/contracts | Candidate manifest, permitted dataset snapshot, independent evaluation, canary metrics and release signatures. |
| EQ-S20-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S20-AC1: Quality, regression, tenant/privacy and cost gates are declared before comparison.
- [ ] EQ-S20-AC2: Failed/unsupported candidate stays unreleased; model rollback restores known output/contract profile.
- [ ] EQ-S20-AC3: Canary evidence comes from the actual chosen checkpoint and environment, not fixtures alone.
- [ ] EQ-S20-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S20-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S20-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

A rejected candidate plus a promotion/rollback exercise when a qualifying candidate exists.

## Exit and handoff

Evidence-backed release decision; it is acceptable to reject all candidates and keep the existing model.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

