# EQ S07: Durable jobs, progress and runtime budgets

**Status:** Planned  
**PI:** [PI-03 Astra-powered extraction and reviewed matching](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M09 M15 M19 M22  
**Astra references:** A02 A03 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Orchestrate asynchronous product work without duplicating Astra's durable execution authority.

## User story and features

As a user, I can see processing progress and cancel or retry safely without duplicate work.

- EQ-S07-F01: Product job/outbox, remote Astra job mapping and progress
- EQ-S07-F02: Idempotency, cancellation and budget/allowance reservation contract

## Dependencies and entry criteria

S06; Astra job profile/operation inspected and chosen in S01.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S07-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S07-T02 | React frontend | Progress, retry/cancel, timeout and uncertain-outcome states; distinguish queued from running. |
| EQ-S07-T03 | Next.js/backend | Commit durable product intent before acknowledgement; persist remote job IDs, reconcile before retry, lease/fence product-owned jobs and reserve usage atomically. |
| EQ-S07-T04 | Astra integration | Integrate supported Astra jobs/cancel operations for qualified tools/DAGs; if extraction is synchronous, product worker owns one bounded call and does not invent a remote job capability. |
| EQ-S07-T05 | Data/contracts | Job/Attempt/Outbox, remote references and usage reservations; explicit state and effect ownership. |
| EQ-S07-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S07-AC1: Duplicate submission and worker loss do not duplicate business effects.
- [ ] EQ-S07-AC2: Remote uncertain completion is held for reconciliation instead of blindly replayed.
- [ ] EQ-S07-AC3: Cancellation, timeout and failed work follow the declared reservation policy.
- [ ] EQ-S07-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S07-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S07-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Restart during a job, observe recovery and show a cancelled/uncertain case with correlated records.

## Exit and handoff

One authoritative execution owner per operation; real-process fault evidence retained for chosen path.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

