# EQ S08: Astra enquiry extraction and verification

**Status:** Planned  
**PI:** [PI-03 Astra-powered extraction and reviewed matching](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M07 M10 M19 M22  
**Astra references:** A01 A03 A04 A06 A08 A09 A13 A14 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Extract structured quotation requirements through the actual Astra boundary with explicit quality gates.

## User story and features

As a salesperson, I receive source-backed line items and clear uncertainty rather than unchecked model text.

- EQ-S08-F01: Versioned schema/prompt and real Astra extraction adapter
- EQ-S08-F02: Source/quantity/unit validation, bounded repair and manual fallback

## Dependencies and entry criteria

S07; real gateway and selected model available. Model-quality gate can remain blocked despite passing adapter tests.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S08-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S08-T02 | React frontend | Review extracted fields alongside source spans; show invalid output, truncation, unavailable model and manual correction. |
| EQ-S08-T03 | Next.js/backend | Versioned contract, server-side validation, timeout/error mapping, scoped inputs and diagnostic metadata; add a narrowly authenticated wrapper only if the current gateway lacks required functionality. |
| EQ-S08-T04 | Astra integration | Use actual selected checkpoint; respect context budget, preserve mandatory fields and negation; classify verified scope accurately. External model fallback remains disabled. |
| EQ-S08-T05 | Data/contracts | ModelRun, schema/prompt/checkpoint identifiers, corrected-vs-generated fields and held-out evaluation records. |
| EQ-S08-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S08-AC1: Schema-invalid, invented-reference and injected-instruction outputs cannot become approved enquiry data.
- [ ] EQ-S08-AC2: Report required-field accuracy by language/input type against preregistered pilot targets.
- [ ] EQ-S08-AC3: Over-context and unavailable-model cases fail visibly and keep manual entry usable.
- [ ] EQ-S08-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S08-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S08-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Real Astra request through Next.js with source-backed output, plus malformed/timeout/low-quality examples.

## Exit and handoff

Adapter evidence and quality verdict recorded separately; AI capability enabled only if its gate passes.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

