# EQ S05: Price lists, currencies and units

**Status:** Planned  
**PI:** [PI-02 Trusted business data and enquiry intake](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M06 M12 M17 M19  
**Astra references:** A06 A07 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Establish authoritative price and unit rules independently of AI.

## User story and features

As a business owner, I can define valid prices and rounding rules so a quote never uses invented amounts.

- EQ-S05-F01: Effective price lists, customer overrides and inventory timestamps
- EQ-S05-F02: Currency precision, units and reviewed tax/discount rule contract

## Dependencies and entry criteria

S04; business reviewer supplies price precedence and local calculation policy.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S05-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S05-T02 | React frontend | Price/validity editor, missing-price warnings, override reason and stock-as-of display. |
| EQ-S05-T03 | Next.js/backend | Decimal domain functions, overlapping-price validation and precedence; reject unknown unit conversions and mixed quote currencies. |
| EQ-S05-T04 | Astra integration | Keep Astra formula/claim primitives advisory; they never supply authoritative prices, exchange rates or local tax rules. |
| EQ-S05-T05 | Data/contracts | PriceList/PriceEntry, effective ranges, unit mappings, snapshot schema and versioned regional rule configuration. |
| EQ-S05-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S05-AC1: Known quantity/unit/price fixtures resolve exactly.
- [ ] EQ-S05-AC2: Expired/ambiguous price entries and unsupported conversions require correction.
- [ ] EQ-S05-AC3: Document currency can differ from future subscription billing currency without conversion.
- [ ] EQ-S05-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S05-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S05-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Compare valid, expired and ambiguous pricing cases with approved expected totals.

## Exit and handoff

Reviewed calculation inputs and fixtures ready for quotation implementation.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

