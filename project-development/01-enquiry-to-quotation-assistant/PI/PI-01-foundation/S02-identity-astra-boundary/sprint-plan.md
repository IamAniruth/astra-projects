# EQ S02: Identity and secure Astra boundary

**Status:** Planned  
**PI:** [PI-01 Product foundation and Astra boundary](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M02 M19 M22  
**Astra references:** A01 A08 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Plan and deliver authenticated customer sessions and a private Astra client boundary.

## User story and features

As a customer, I can sign in without exposing model service credentials or another business's information.

- EQ-S02-F01: Signup, verification, session, logout and account recovery
- EQ-S02-F02: Server-only Astra client and credential lifecycle contract

## Dependencies and entry criteria

S01; compatible auth adapter and credential provisioning decision.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S02-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S02-T02 | React frontend | Auth screens, accessible errors, verification/recovery flow and session-expired behavior; no pasted Astra API key in customer UI. |
| EQ-S02-T03 | Next.js/backend | Integrate the selected auth library, session checks, CSRF/origin controls and throttling; private Astra client validates response envelopes and typed errors. |
| EQ-S02-T04 | Astra integration | Define server-controlled tenant-scoped credential provisioning/rotation/revocation; no generic proxy to legacy chat_server routes. |
| EQ-S02-T05 | Data/contracts | Auth tables and encrypted/secret-store references for credentials; redact keys from audits and traces. |
| EQ-S02-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S02-AC1: Invalid sessions cannot reach protected product endpoints.
- [ ] EQ-S02-AC2: Wrong/revoked Astra credentials return an explicit integration failure with no legacy fallback.
- [ ] EQ-S02-AC3: Browser bundle, URL, storage and logs contain no Astra or billing secret.
- [ ] EQ-S02-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S02-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S02-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Login/logout/recovery journey and a denied private-gateway request shown with a redacted trace.

## Exit and handoff

Identity boundary reviewed; local fixtures may prove wiring but real-gateway evidence remains separately labelled.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

