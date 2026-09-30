# EQ S14: Subscriptions, entitlements and usage

**Status:** Planned  
**PI:** [PI-05 Website, subscriptions and supported markets](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M09 M15 M19  
**Astra references:** A03 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Sell supported plans and enforce access/usage without confusing provider billing with Astra runtime metering.

## User story and features

As an owner, I can subscribe, see usage, manage renewal and cancel with clear access dates.

- EQ-S14-F01: Eligible-provider checkout and subscription lifecycle
- EQ-S14-F02: Server entitlements, usage accounting and reconciliation

## Dependencies and entry criteria

S07/S13; seller eligibility, provider account and agreed charging policy. Missing account leaves live checkout blocked, not simulated-complete.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S14-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S14-T02 | React frontend | Plan selection, payment-pending/success/failure, billing history, allowance and cancellation/portal controls. |
| EQ-S14-T03 | Next.js/backend | Verify signed provider events, deduplicate/reconcile order, map plan IDs server-side, enforce period boundaries/grace policy and atomic reservations. |
| EQ-S14-T04 | Astra integration | Keep runtime token/time evidence and unavailable counters separate from purchased enquiry units. Uncertain runtime outcomes trigger policy-based reconciliation. |
| EQ-S14-T05 | Data/contracts | Plan, Subscription, Entitlement, WebhookEvent, UsageReservation/Event with currency and period identity. |
| EQ-S14-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S14-AC1: Browser success redirect cannot grant paid access on its own.
- [ ] EQ-S14-AC2: Duplicate/out-of-order events and parallel job requests neither double-charge nor exceed allowance.
- [ ] EQ-S14-AC3: Cancellation retains access until the correct end date and failed jobs follow published charging terms.
- [ ] EQ-S14-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S14-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S14-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Sandbox purchase, renewal failure, cancellation and duplicate-event replay.

## Exit and handoff

Sandbox lifecycle passes; controlled live verification remains launch evidence.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

