# EQ S17: Quotation quality, capacity and customer pilot

**Status:** Planned  
**PI:** [PI-06 Production qualification and first-market release](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M10 M11 M19 M20 M21 M22  
**Astra references:** A03 A06 A09 A10 A12 A13 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Establish actual customer-task quality and capacity with the exact model and release environment.

## User story and features

As a pilot customer, I can see that the product saves work and know where manual review remains necessary.

- EQ-S17-F01: Independent held-out evaluation and representative paid-pilot evidence
- EQ-S17-F02: Capacity/failure qualification and reviewed correction capture

## Dependencies and entry criteria

S08/S09 model gates; S16 environment; permitted customer data and independent reviewer.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S17-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S17-T02 | React frontend | Clear correction controls, evidence-linked AI status and pilot feedback; no hidden training consent. |
| EQ-S17-T03 | Next.js/backend | Capture correction provenance and opt-in training decision separately; run realistic data sizes/concurrency, usage reconciliation and cost measurement. |
| EQ-S17-T04 | Astra integration | Re-run target gates in the locked environment on the served checkpoint. Historical tiny-model platform throughput and narrow verification scores do not qualify this workflow. |
| EQ-S17-T05 | Data/contracts | Reviewed evaluation split, real-run manifests, latency/quality breakdown, pilot baseline and correction records. |
| EQ-S17-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S17-AC1: Preregistered accuracy/retrieval/fidelity gates pass separately for each offered input/language.
- [ ] EQ-S17-AC2: Money and tenant isolation remain exact under load; retries and cancellation preserve ledgers.
- [ ] EQ-S17-AC3: Pilot timing and support effort show results against the agreed baseline; failures are included.
- [ ] EQ-S17-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S17-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S17-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Pilot workflow and measured report including weak cases, capacity limits and go/no-go recommendation.

## Exit and handoff

A supported feature/market profile passes quality and operational gates or is honestly held back. No prompt tuning on the held-out set.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

