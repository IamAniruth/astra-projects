# EQ S10: Quotation builder and deterministic totals

**Status:** Planned  
**PI:** [PI-04 Quotation correctness, approval and artifacts](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M06 M12 M19  
**Astra references:** A06 A07 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Convert reviewed requirements into editable quotations with trustworthy monetary calculations.

## User story and features

As a salesperson, I can prepare a quote from confirmed products and see reproducible totals.

- EQ-S10-F01: Quote line editor and authoritative price snapshots
- EQ-S10-F02: Decimal subtotal, discounts, tax, rounding and validity rules

## Dependencies and entry criteria

S05/S09; agreed jurisdiction-specific calculation fixtures.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S10-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S10-T02 | React frontend | Quote editor, server total refresh, pricing warnings and complete calculation breakdown. |
| EQ-S10-T03 | Next.js/backend | Domain calculation service, versioned input/output snapshot, unit checks, price-override policy and explicit quote currency. |
| EQ-S10-T04 | Astra integration | AI can draft descriptive wording only. Astra verifier/formula checks supplement but never replace the tested money engine. |
| EQ-S10-T05 | Data/contracts | Quote/Revision/Line and calculation-rule versions; price effective time, customer identity and stock-as-of snapshots. |
| EQ-S10-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S10-AC1: All approved money fixtures match exactly, including fractional quantities and rounding order.
- [ ] EQ-S10-AC2: Browser-modified totals and model-generated prices are ignored/rejected.
- [ ] EQ-S10-AC3: Missing prices, unmatched lines and unsupported tax/unit settings prevent submission.
- [ ] EQ-S10-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S10-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S10-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Generate a quote from reviewed enquiry lines and verify totals against independent expected values.

## Exit and handoff

Calculation correctness and line provenance demonstrated before approval workflow.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

