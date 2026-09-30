# EQ S11: Revisions, approval and audit trail

**Status:** Planned  
**PI:** [PI-04 Quotation correctness, approval and artifacts](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M12 M13 M19  
**Astra references:** A06 A08 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Bind approval to an exact quotation revision and prevent unauthorized changes.

## User story and features

As an approver, I can review changes, approve or reject, and know the exported quote is the approved version.

- EQ-S11-F01: Submit/approve/reject state machine and permissions
- EQ-S11-F02: Immutable approved revisions, optimistic concurrency and audit

## Dependencies and entry criteria

S10 and role policy from S03.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S11-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S11-T02 | React frontend | Approval inbox, revision comparison, decision reason and locked approved view. |
| EQ-S11-T03 | Next.js/backend | Transactional approval and audit; content/revision identity; conflict responses; new draft for edits; reasoned privileged overrides. |
| EQ-S11-T04 | Astra integration | Reuse consequential-action principles, but product quote approval is a product permission check, not an automatic Astra verification badge. |
| EQ-S11-T05 | Data/contracts | Approval, AuditEvent, immutable revision hash and version counter. |
| EQ-S11-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S11-AC1: Sales-only user cannot approve; concurrent stale edits are rejected.
- [ ] EQ-S11-AC2: Changing an approved line creates a new unapproved revision.
- [ ] EQ-S11-AC3: Approval trace records actor, time, exact revision and reason without leaking unrelated data.
- [ ] EQ-S11-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S11-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S11-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Submit, reject, revise, approve, then edit again to demonstrate approval does not carry forward.

## Exit and handoff

No export-ready state exists without approval of the exact content under the chosen policy.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

