# EQ S24: Admin commerce and operational readiness

**Status:** Planned  
**PI:** [PI-08 Administration](../README.md)  
**Cadence assumption:** two weeks; estimate and named owners required  
**Modules:** M09 M15 M17 M18 M19 M20 M22  
**Source:** [Admin panel specification](../../../docs/13-admin-panel-specification.md)

## Sprint objective and user story

As an authorized service operator, I can use admin commerce and operational readiness while preserving customer isolation, authoritative business data and accountable actions.

- EQ-S24-F01: Service billing, usage, market controls and reconciled job recovery
- EQ-S24-F02: Health, audit, data requests and integrated admin readiness

## Dependencies and entry criteria

S22/S23 administration, S07 remote-job ownership/budgets, S14 provider and ledger contracts, S15 qualified markets and S16 operational/data-lifecycle services. S17/S18 results populate evidence views as available, not as entry gates. Confirm provider, usage/retry/grace rules, retention and thresholds.

Confirm permitted examples, contract/config versions, individual owners and realistic capacity. Fixtures may enable UI work but cannot satisfy actual provider, model or target-host acceptance. PI-07 is not required.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S24-T01 | Product/domain reviewer | Finalize service-fee policies, usage units, temporary-access expiry, market activation evidence, retention and incident ownership. |
| EQ-S24-T02 | React frontend | Build billing/usage/job views, separate currencies, timestamped health, support/audit/data-request screens and pending/failed/accepted readiness views. |
| EQ-S24-T03 | Next.js/backend | Reconcile provider state, deduplicate verified events, reserve/settle usage atomically and append reasoned adjustments without falsifying payments. |
| EQ-S24-T04 | Astra integration | Use persisted remote Astra IDs to reconcile uncertain outcomes before retry; invoke the existing execution owner and track cancellation acknowledgement. |
| EQ-S24-T05 | Data/contracts | Implement scoped data requests and retention evidence; preserve current revocations/deletions on restore, keep secrets private and audit outcomes. |
| EQ-S24-T06 | QA/operations | Run provider sandbox/concurrency checks, remote-response-loss recovery, deletion/restore drills and a full admin-to-approved-export scenario; deliver runbooks. |

Reuse existing domain APIs under /api/v1 and the proposed additions in the admin specification. Enforce identity and scope on the server; never trust a client workspace or approval flag. Return typed conflicts/validation/access errors with correlation IDs and no sensitive payloads. Privileged mutations need confirmation, reason where applicable, idempotency and audit.

## Acceptance criteria

- [ ] EQ-S24-AC1: Verified provider state governs access; duplicate/out-of-order events and concurrent jobs cannot double-grant or double-settle usage; temporary exceptions expire.
- [ ] EQ-S24-AC2: Unknown remote acceptance reconciles before retry; duplicate requests cannot duplicate inference/export effects; cancellation remains pending until acknowledged.
- [ ] EQ-S24-AC3: Workspace suspension, service cancellation/refund and deletion remain separate; billing is for software access only, with amounts reported by currency.
- [ ] EQ-S24-AC4: Only qualified market configurations activate; existing subscriptions are not silently terminated and interface/document/billing settings stay independent.
- [ ] EQ-S24-AC5: Health exposes stale/unknown data; scoped data-request and restore drills cover originals/derivatives/artifacts and reapply current grants and deletion rules.
- [ ] EQ-S24-AC6: Named reviewers accept integrated permission, pricing, approval, export, audit and recovery evidence; absent model/host/pilot evidence remains pending and blocks applicable release gates.

## Test and evidence plan

Use domain tests for state/calculation invariants, integration tests for actual auth/storage/jobs/billing, and browser tests for changed operator journeys. Include negative direct-API requests and concurrent/stale requests rather than testing only button visibility.

Retain the feature/task checklist, contract/migration changes, redacted API traces or screenshots, results including failures, and reviewer decision. Record actual commit, configuration and relevant model/prompt/data/host versions. Store no credentials or unapproved customer documents in evidence. Sandbox/mocked results must be labelled and cannot establish live readiness.

## Sprint review demonstration

Simulate a verified subscription and duplicate renewal, a lost response after Astra acceptance, cancellation and scoped recovery. Run an outage/deletion/restore drill, then complete a permitted enquiry-to-approved-export journey with correct usage and audit history.

## Exit and handoff

Accept only with linked evidence and named reviewers. Carry incomplete dependencies explicitly; documentation alone leaves this sprint Planned. Required controls precede S17 paid-pilot acceptance; S18 incorporates final administration readiness.

Update [status](../../../_STATUS.md), [feature matrix](../../../docs/12-module-feature-sprint-matrix.md) and [decisions](../../../docs/09-decisions-and-risks.md). Apply the [quality definition of done](../../../docs/07-quality-security-international.md). No automatic outbound messaging or collection of payments for quoted goods is added.
