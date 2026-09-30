# EQ S16: Administration, security and production operations

**Status:** Planned  
**PI:** [PI-06 Production qualification and first-market release](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M01 M08 M09 M13 M18 M19 M20 M22  
**Astra references:** A01 A02 A08 A11 A12 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Prepare a supported deployment boundary, recovery plan and customer-data lifecycle.

## User story and features

As an operator, I can diagnose failures, restore service and support customers without uncontrolled data access.

- EQ-S16-F01: Redacted admin/support tools, audit and data lifecycle
- EQ-S16-F02: Private Astra deployment integration, monitoring, backups and recovery

## Dependencies and entry criteria

S15; target host, operational owner, storage and data-location decisions.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S16-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S16-T02 | React frontend | Operator health/jobs/usage dashboard, customer outage status, export/deletion request screens. |
| EQ-S16-T03 | Next.js/backend | Separate platform roles, scoped support access, durable audit policy, data export/delete jobs, backups and deployment/migration/rollback controls. |
| EQ-S16-T04 | Astra integration | Apply Astra release checklist to chosen locked runtime/model/host; retain native serving. Do not resurrect the stopped Astra Compose profile or expose local UI routes. |
| EQ-S16-T05 | Data/contracts | Release/environment manifests, retention and deletion receipts, incident and restore evidence. |
| EQ-S16-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S16-AC1: Real restore preserves business data and cannot revive unauthorized retrieval.
- [ ] EQ-S16-AC2: Model/storage failure returns typed errors and leaves no duplicate approval/export.
- [ ] EQ-S16-AC3: Supervisor restarts and TLS/private networking are verified on the selected host; durable audit failures follow reviewed policy.
- [ ] EQ-S16-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S16-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S16-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Worker/model outage and recovery, restore, revoked access and end-to-end data deletion trace.

## Exit and handoff

Recovery and security evidence exists for selected topology; outstanding upstream gaps explicitly block unsupported features.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

