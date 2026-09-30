# EQ S21: Qualified retrieval, artifacts and market expansion

**Status:** Planned  
**PI:** [PI-07 Governed learning and qualified expansion](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Optional post-launch enhancement  
**Modules:** M05 M11 M14 M17 M19 M20 M21 M22  
**Astra references:** A05 A07 A11 A12 A13 A14 A15 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Add only enhancements justified by measured customer needs and capability evidence.

## User story and features

As a growing customer, I receive improved retrieval or regional support without losing correctness or isolation.

- EQ-S21-F01: Evidence-led retrieval/context/storage evaluation
- EQ-S21-F02: Optional artifact or next-market release under separate feature gates

## Dependencies and entry criteria

S18; S19/S20 only for enhancements depending on governed learning. Scope each experiment before implementation.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S21-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S21-T02 | React frontend | Expose only accepted enhancements: improved match evidence, optional approved format, or newly qualified language/market. |
| EQ-S21-T03 | Next.js/backend | Register an experiment backlog and separate release flags; assess migration/recovery before pgvector or other storage changes; retain exact-search fallback. |
| EQ-S21-T04 | Astra integration | Benchmark Astra learned retrieval/compression against lexical/raw-source baseline. vLLM/owner replication/Office/MCP remain deferred unless their own gates and a concrete need pass. |
| EQ-S21-T05 | Data/contracts | Versioned experiment results, permissions/deletion parity, artifact fidelity and market-readiness record. |
| EQ-S21-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S21-AC1: An improvement cannot trade away mandatory fields, authorization or quote accuracy.
- [ ] EQ-S21-AC2: Migration/rollback preserves identities, permissions and tombstones if an adapter is adopted.
- [ ] EQ-S21-AC3: Each enabled enhancement has its own quality, cost, compatibility and customer acceptance evidence.
- [ ] EQ-S21-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S21-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S21-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

One justified enhancement with baseline comparison, or a documented no-adoption decision.

## Exit and handoff

Qualified expansion decision; deferred optional experiments do not block the already-qualified initial release.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

