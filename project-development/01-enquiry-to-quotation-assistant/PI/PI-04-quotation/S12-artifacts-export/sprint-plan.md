# EQ S12: Approved artifacts and end-to-end pilot workflow

**Status:** Planned  
**PI:** [PI-04 Quotation correctness, approval and artifacts](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M08 M14 M19  
**Astra references:** A07 A08 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Produce customer-usable, privately downloadable quotation artifacts from approved snapshots.

## User story and features

As a salesperson, I can download a branded quote that exactly matches the approved data.

- EQ-S12-F01: PDF and safe CSV export jobs
- EQ-S12-F02: Artifact provenance, readback/render checks and full workflow demonstration

## Dependencies and entry criteria

S11; fonts/template and selected renderer available.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S12-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S12-T02 | React frontend | Template preview, export progress, download and revision labels; no automatic email sending. |
| EQ-S12-T03 | Next.js/backend | Render escaped controlled templates from immutable snapshots; verify file content, totals, currency and revision; store checksum and enforce download scope. |
| EQ-S12-T04 | Astra integration | Use Astra template/artifact concepts where suitable; do not claim Office production support from local PI-36 fixtures. Native DOCX/XLSX remains optional. |
| EQ-S12-T05 | Data/contracts | ExportArtifact with input hash, output digest, template/font version and approval reference. |
| EQ-S12-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S12-AC1: Rendered PDF and CSV match approved line items/totals and survive long text/pagination.
- [ ] EQ-S12-AC2: Injected formula-like CSV strings and HTML are safe.
- [ ] EQ-S12-AC3: Signup/import/enquiry/review/quote/approval/export completes without cross-tenant access.
- [ ] EQ-S12-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S12-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S12-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Export and independently inspect a full quote, a multi-page case and a denied download.

## Exit and handoff

Internal pilot workflow complete; public billing/production launch still requires later PIs.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

