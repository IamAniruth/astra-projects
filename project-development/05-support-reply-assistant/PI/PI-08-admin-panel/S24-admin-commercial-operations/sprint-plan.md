# SR S24: Admin commerce, operations and readiness

PI-08 | Module M24 | Status: Planned | Conditional administration scope  
Source: [Admin specification sections 8-12 and 14-15](../../../docs/09-admin-panel-specification.md)

## Objective and user story

As an authorized operator, I can manage service access, reconcile processing failures and demonstrate safe recovery without duplicating work, exposing customer content or misrepresenting service readiness.

## Features

- SR-S24-F01: Build seats/usage/subscription oversight, controlled entitlement adjustments and job recovery.
- SR-S24-F02: Build health, audit, data-request and quality-evidence views; qualify the integrated admin workflow.

## Dependencies and entry criteria

S22/S23 admin foundations and governance; S06/S09 durable jobs and remote-ID ownership; S13 billing/usage contracts; S14 configuration qualification; S15 privacy, supervision and recovery services. Confirm payment provider, grace/access policy, seat/usage units, retry charging, retention, support ownership and monitoring thresholds.

S16-S18 quality/pilot/release records populate the evidence view as available; completed release is not required to build it. Required operational checks precede the paid S17 pilot, and S18 consumes final admin readiness evidence. Optional S19-S21 work is not a prerequisite.

## Tasks and ownership

| Task | Deliverable |
|---|---|
| SR-S24-T01 | Product/billing: finalize counting and access rules; build plan, seats, ledger, renewal and reconciliation views with currencies kept separate. |
| SR-S24-T02 | Backend: orchestrate expiring entitlement adjustments and provider reconciliation; preserve payment truth, idempotency and atomic usage settlement. |
| SR-S24-T03 | Operations/backend: expose scoped job attempts and remote IDs; add reconcile/retry/cancel through the owning service with safe diagnostics. |
| SR-S24-T04 | Frontend/operations: build timestamped health, incidents and restricted audit views; distinguish unknown/stale observations and track recovery owners. |
| SR-S24-T05 | Privacy/operations: implement verified export/deletion requests across derived stores and test restore/index rollback against current grants and withdrawals. |
| SR-S24-T06 | QA/support: build pending/failed/accepted quality-evidence views; run the full admin checklist and integrated pilot drill, then deliver runbooks and reviewer decisions. |

Name individual owners. Re-estimate this sprint at kickoff; split delivery if capacity cannot cover its checks. Do not remove recovery or privacy evidence to fit a nominal timebox.

## Data and API work

Reuse subscription/entitlement records, usage reservations/ledger, Job/remote IDs and Audit. Add scoped data requests and operational incidents where needed. Use the specification's usage, entitlement-adjustment, job reconcile/retry/cancel, audit and data-request routes.

Temporary access is a separate expiring record, not a payment edit. Corrections append ledger events. Idempotency keys and concurrency checks cover all mutating operator actions. Keep provider/runtime secrets in backend infrastructure; use the provider dashboard for initially deferred complex financial actions and reconcile outcomes.

## Acceptance

- [ ] SR-S24-AC1: Verified billing events and reconciliation determine paid access; redirects, duplicate and out-of-order events cannot grant duplicate allowance or falsify payment.
- [ ] SR-S24-AC2: Concurrent seats/jobs stay within configured limits; retry/failure/reset rules settle usage once and show consumed/reserved/remaining units consistently.
- [ ] SR-S24-AC3: Temporary entitlement exceptions require permission/reason/expiry and expire without altering payment history.
- [ ] SR-S24-AC4: Unknown Astra outcomes reconcile using remote IDs before retry; repeated clicks cannot duplicate inference, exports or settlement.
- [ ] SR-S24-AC5: Cancellation remains requested until acknowledged/reconciled; retry rechecks grants, input versions, budget and current access.
- [ ] SR-S24-AC6: Suspension, cancellation, service-fee refunds and deletion remain separate; the operator sees actual scope, effective date and outcome.
- [ ] SR-S24-AC7: Health distinguishes stale/unknown observations; runtime outage, old queue work and delayed billing sync are visible without sensitive payloads.
- [ ] SR-S24-AC8: Verified data requests cover originals and derivatives; restore/rollback respects deletions, grants, withdrawals and stale approvals before service resumes.
- [ ] SR-S24-AC9: Audit records attribute changes and sensitive reads, resist ordinary-admin edits and exclude secrets/customer text.
- [ ] SR-S24-AC10: Quality views identify actual versions, thresholds, sample sizes, reviewer and unresolved failures; absent evidence appears pending and never implies measured CSAT.
- [ ] SR-S24-AC11: Integrated onboarding, import, publication, draft review, manual export and failure recovery pass the specification checklist with named reviewers.
- [ ] SR-S24-AC12: Unsupported model/connector configurations cannot be activated through admin; no sending, customer remedy or automatic training is introduced.

## Verification and demonstration

Run billing-provider sandbox scenarios for payment confirmation, renewal, failure, cancellation and repeated/out-of-order notifications; distinguish sandbox evidence from live provider readiness. Record concurrent usage and expiring exception checks.

Simulate a lost response after remote acceptance, reconcile its remote ID, then retry only when eligible. Capture cancellation acknowledgement, recovery outcomes and settlement records. Demonstrate model downtime and stale monitors.

Perform a documented deletion/restore/index rollback drill using permitted fixtures across cases, files, derivatives, indexes, caches and exports. Record backup/audit/billing retention exceptions accurately.

Complete a browser/API operator walkthrough using two tenants and multiple roles. Link real target-host and model evidence from S15/S16 as obtained; mocks cannot close production-readiness gaps. Report blockers to S17/S18 rather than representing a successful UI demonstration as release acceptance.

## Exit and handoff

Deliver runbooks for billing sync, remote-job uncertainty, outage, scoped support access, deletion and restore; link the executed checklist, actual versions and named acceptance decisions. Product, operations, security/privacy and support reviewers approve within their responsibilities.

Update [PI readiness](../README.md), [status](../../../_STATUS.md) and [coverage](../../../docs/03-module-feature-sprint-matrix.md) based on actual evidence. Later quality/pilot outcomes remain with S16-S18, and optional improvement remains with S19-S21.
