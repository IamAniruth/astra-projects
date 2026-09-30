# EQ S09: Permission-aware catalogue matching

**Status:** Planned  
**PI:** [PI-03 Astra-powered extraction and reviewed matching](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M05 M07 M11 M19 M22  
**Astra references:** A05 A06 A11 A13 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Suggest only authorized, current catalogue candidates and require review of ambiguous matches.

## User story and features

As a salesperson, I can compare the requested specification with candidate items and choose the correct one.

- EQ-S09-F01: Exact/alias/lexical retrieval and scoped Astra retrieval adapter
- EQ-S09-F02: Candidate comparison, correction, abstention and stale-result invalidation

## Dependencies and entry criteria

S04-S08; chosen indexing interface and sample catalogue; learned retrieval remains optional.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S09-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S09-T02 | React frontend | Top-candidate comparison with unit/attribute differences; select, reject, search manually or leave unmatched. |
| EQ-S09-T03 | Next.js/backend | Versioned catalogue index sync and invalidation; authorize before retrieval and again before committing selected product; no model-invented IDs. |
| EQ-S09-T04 | Astra integration | Benchmark Astra lexical/hash and any learned retrieval separately. Compression must preserve SKU, quantity, units and exclusions; raw-source fallback is valid. |
| EQ-S09-T05 | Data/contracts | MatchCandidate, ReviewedSelection and catalogue/permission revisions; tombstones for deleted sources. |
| EQ-S09-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S09-AC1: Cross-company/revoked records cannot affect accessible matches or leak snippets.
- [ ] EQ-S09-AC2: Top-3 match coverage is measured on held-out supported requests; no-match cases stay unresolved.
- [ ] EQ-S09-AC3: Catalogue or permission changes invalidate stale candidates before quote generation.
- [ ] EQ-S09-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S09-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S09-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Exact SKU, ambiguous variant, unmatched product and a permission-revoked candidate.

## Exit and handoff

Reviewed enquiry lines are safe inputs to deterministic quotation logic.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

