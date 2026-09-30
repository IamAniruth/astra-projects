# EQ S15: International settings and supported-market qualification

**Status:** Planned  
**PI:** [PI-05 Website, subscriptions and supported markets](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M03 M14 M16 M17 M19  
**Astra references:** A05 A07 A09 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Make the shared product configurable internationally while enabling only validated combinations.

## User story and features

As an international business, I can use my language, formats and document currency within explicitly supported markets.

- EQ-S15-F01: Locale, currency, time zone, templates and market availability
- EQ-S15-F02: Per-language AI/document qualification and region-accurate sales flow

## Dependencies and entry criteria

S12-S14; first-market domain reviewer and language fixtures. Second market can remain disabled.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S15-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S15-T02 | React frontend | Language/format selectors, Unicode/RTL where selected, readable localized PDF and supported-market messaging. |
| EQ-S15-T03 | Next.js/backend | Versioned market rules, separate billing/document currencies, quote numbering/template variations, signup/checkout restrictions and processing-location records. |
| EQ-S15-T04 | Astra integration | Run Astra-backed quality checks per enabled language and input type; compare retrieval/OCR behavior, not just UI translation. |
| EQ-S15-T05 | Data/contracts | MarketProfile, template and rule versions, qualification records and local reviewer signoff. |
| EQ-S15-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S15-AC1: User language can differ from country; billing currency differs safely from quote currency.
- [ ] EQ-S15-AC2: Ambiguous dates/units are clarified; relevant DST/RTL/currency precision cases pass.
- [ ] EQ-S15-AC3: Unsupported countries/languages cannot buy a falsely advertised capability.
- [ ] EQ-S15-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S15-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S15-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Two configured market examples with only the actually qualified one enabled for sale.

## Exit and handoff

Published market matrix and product behavior agree; no worldwide availability claim.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

