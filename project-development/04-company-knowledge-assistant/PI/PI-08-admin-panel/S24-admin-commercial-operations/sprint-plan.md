# CK S24: Admin commerce and operational readiness

PI-08 | Module M24 | Status: Planned | Conditional administration scope  
Source: [Admin specification](../../../docs/09-admin-panel-specification.md)

## Objective and features

As an authorized service operator, I can use admin commerce and operational readiness while preserving source authority, current grants and employee-question privacy.

- CK-S24-F01: Company billing, usage, qualified scope and reconciled jobs
- CK-S24-F02: Health, audit, data lifecycle and integrated readiness evidence

## Dependencies and entry criteria

S22/S23 administration; S06 jobs/indexing, S13 commerce, S14 specialty/language qualification and S15 operations/retention. S16-S18 results populate readiness views as available rather than being entry gates. Confirm counting/retry/reset/provider/grace rules, retention and thresholds.

Assign named product/content/privacy, React, Next.js/data, Astra integration and QA/operations owners. Confirm permitted documents/questions, contracts and capacity. Fixtures support development but cannot establish actual model/provider/host quality. Optional PI-07 is not a prerequisite.

## Tasks and ownership

| Task | Deliverable |
|---|---|
| CK-S24-T01 | Product/backend: build plan/usage and verified provider reconciliation, atomic allowances and reasoned expiring adjustments; retain separate operational/billing states. |
| CK-S24-T02 | React/Astra integration: build safe job reconcile/retry/cancel and supported-scope controls using existing effect owners and current publication/access checks. |
| CK-S24-T03 | Operations/data: implement timestamped health, incidents, restricted audit and verified data requests; restore current grants/tombstones before serving sources/history/gaps and reconcile usage. |
| CK-S24-T04 | QA/privacy/operations: test duplicate/out-of-order billing, concurrent limits, lost remote acceptance, deletion/restore of source-bearing history/gaps and full employee lifecycle; deliver runbooks and readiness evidence. |

Reuse [data/API contracts](../../../docs/04-data-and-api.md) and the admin specification's extensions. Authorize nested records, aggregates and artifacts server-side. Return typed validation, permission, stale-version, unavailable and reconciliation failures without restricted metadata. Confirmations supplement backend authorization, idempotency/concurrency and audit.

## Acceptance

- [ ] CK-S24-AC1: Verified billing controls access; repeated events and concurrent work cannot overgrant or double-settle allowances, and temporary exceptions expire without altering payment truth.
- [ ] CK-S24-AC2: Uncertain remote acceptance reconciles before retry; current grants/source state are rechecked, withdrawn/private content cannot return, and cancellation remains pending until confirmed.
- [ ] CK-S24-AC3: Health distinguishes unknown/stale/outage states; deletion/restore covers originals and derived histories/gap evidence under current tombstones/grants with attributable audit.
- [ ] CK-S24-AC4: Only qualified scope activates; integrated access/publication/private-gap/recovery evidence has named reviewers while absent model/host/pilot results remain pending and critical access/policy failures block release.

## Verification and demonstration

Simulate duplicate renewal and remote response loss, reconcile without replaying inference, then restore an older corpus after withdrawal and group revocation. Verify old conversations/gap evidence cannot leak restored content and complete an authorized source-to-explanation/gap workflow.

Use domain checks for effective policy/state, integration tests for grants/indexes/history/jobs and browser checks for changed journeys. Include direct API negatives, concurrent changes and filter combinations. Check citation resolution separately from actual claim support.

Retain feature/task checklist, contract/migration changes, redacted traces/screenshots, results including failures and named reviewer decision. Record application, parser, model/prompt, source/index/access-policy, corpus and host versions as applicable. Do not put secrets, unapproved internal documents or employee questions into evidence. Mocks and sandbox results remain labelled.

## Exit and handoff

Apply the [admin checklist](../../../docs/09-admin-panel-specification.md) and [quality requirements](../../../docs/06-quality-security-operations.md). Carry incomplete dependencies explicitly. Required controls precede S17 paid-pilot acceptance and feed S18 readiness.

Update [status](../../../_STATUS.md), [coverage](../../../docs/03-module-feature-sprint-matrix.md) and [decisions](../../../docs/08-decisions-and-references.md) only from actual evidence. Critical access/policy failures cannot be waived by downstream completion. No business decision/action, employee scoring, automatic publication or training is enabled.
