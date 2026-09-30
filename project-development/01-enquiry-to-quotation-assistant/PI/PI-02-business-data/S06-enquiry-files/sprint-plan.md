# EQ S06: Enquiry intake and document provenance

**Status:** Planned  
**PI:** [PI-02 Trusted business data and enquiry intake](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M07 M08 M19 M22  
**Astra references:** A04 A08 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Capture enquiries and extract safe, traceable source text for later AI processing.

## User story and features

As a salesperson, I can paste or upload an enquiry and inspect its source before processing.

- EQ-S06-F01: Enquiry CRUD, supported uploads and private previews
- EQ-S06-F02: Bounded parsing/OCR adapter with page and line provenance

## Dependencies and entry criteria

S03-S05; selected parser profile and representative document fixtures.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S06-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S06-T02 | React frontend | Enquiry list/intake/detail, upload progress, supported-format guidance, source preview and actionable errors. |
| EQ-S06-T03 | Next.js/backend | Private storage authorization, MIME/size/page limits, parsing adapter, versions and retention metadata; no arbitrary URL ingestion. |
| EQ-S06-T04 | Astra integration | Assess Astra document-intelligence reuse; document any missing authenticated interface as new integration work. Unsupported scans get manual-entry guidance. |
| EQ-S06-T05 | Data/contracts | FileAsset, Enquiry and SourceSpan records with digest, source version, media type and parser/OCR version. |
| EQ-S06-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S06-AC1: Corrupt, oversized or forbidden files fail with no unsafe parser side effect.
- [ ] EQ-S06-AC2: Unauthorized downloads fail even with a guessed storage ID.
- [ ] EQ-S06-AC3: Source text and page references survive a representative multi-page enquiry.
- [ ] EQ-S06-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S06-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S06-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Pasted text, a valid PDF, unsupported scan and malicious/invalid upload handling.

## Exit and handoff

Accepted source formats are explicit; extraction quality and security evidence recorded before AI use.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

