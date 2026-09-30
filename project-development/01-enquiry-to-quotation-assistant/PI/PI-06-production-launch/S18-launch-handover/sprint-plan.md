# EQ S18: Production release, subscriptions and handover

**Status:** Planned  
**PI:** [PI-06 Production qualification and first-market release](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M15 M18 M19 M20 M22  
**Astra references:** A02 A08 A09 A12 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Release the qualified product to a limited market with verified billing, support and rollback.

## User story and features

As a paying customer, I can complete the full quotation workflow and manage my account reliably.

- EQ-S18-F01: Controlled production release and commercial smoke journey
- EQ-S18-F02: Release evidence, customer handover and operational ownership

## Dependencies and entry criteria

S17 pass and business/operator approval; live provider/hosting prerequisites are not bypassed.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S18-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S18-T02 | React frontend | Final public copy, onboarding, billing/cancellation and status/support experience matching available features. |
| EQ-S18-T03 | Next.js/backend | Deploy reviewed artifacts, validate migrations, run authorized controlled live payment test, set quotas and enable only approved workspaces/markets. |
| EQ-S18-T04 | Astra integration | Pin model/prompt/schema profile and documented fallback; no unqualified auto-upgrade. Record current Astra release blockers and closed evidence. |
| EQ-S18-T05 | Data/contracts | Release manifest, provider reconciliation, restore/rollback runbook, known limitations and support contacts. |
| EQ-S18-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S18-AC1: Real customer-shaped journey completes from signup/payment to approved artifact.
- [ ] EQ-S18-AC2: Cancellation, webhook reconciliation, failed model and rollback procedures work on release topology.
- [ ] EQ-S18-AC3: Every mandatory release gate has evidence and accountable signoff; open critical gaps block launch.
- [ ] EQ-S18-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S18-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S18-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Release walkthrough, operator handover and signed go/no-go record.

## Exit and handoff

Qualified first-market release, or an explicit blocked release record with remaining actions.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

