# MT S24: Admin commerce and operational readiness

PI-08 | Module M24 | Status: Planned | Conditional administration scope  
Source: [Admin specification](../../../docs/09-admin-panel-specification.md)

## Objective and features

As an authorized service operator, I can use admin commerce and operational readiness with current access, applicable approved sources and attributable actions.

- MT-S24-F01: Team/site billing, usage, supported-scope controls and job recovery
- MT-S24-F02: Health, audit, data requests and integrated readiness evidence

## Dependencies and entry criteria

S22/S23 admin controls; S06 execution/publication ownership, S13 commerce, S14 supported-scope qualification and S15 operations/retention. S16-S18 results populate evidence views when available, not as entry gates. Confirm counting/retry/reset rules, provider/grace policy, retention and monitoring thresholds.

Assign named product/domain, React, Next.js/data, Astra integration and QA/operations owners. Confirm permitted documents, contract versions and capacity. Fixtures support development but do not qualify equipment guidance, actual model or production host. Optional PI-07 is not a dependency.

## Tasks and ownership

| Task | Deliverable |
|---|---|
| MT-S24-T01 | Product/backend: build plan/usage views, provider event reconciliation, atomic allowances, reasoned expiring adjustments and qualified scope activation. |
| MT-S24-T02 | React/Astra integration: expose safe jobs and reconcile/retry/cancel actions using existing effect owners; validate source/access/applicability before recovery. |
| MT-S24-T03 | Operations/data: implement timestamped health/incidents, scoped audit/support and verified data requests; reapply grants/deletions/withdrawal tombstones before restore/index rollback publication. |
| MT-S24-T04 | QA/domain/operations: run billing concurrency, lost-remote-response recovery, withdrawal-aware restore drills and end-to-end source lifecycle; deliver runbooks and honest readiness states. |

Reuse [existing data/API contracts](../../../docs/04-data-and-api.md) and the admin specification's proposed extensions. Enforce tenant/site/document grants on nested lookups and artifacts. Use typed permission, validation, stale-version, unavailable and reconciliation failures with safe correlation IDs. Confirmations supplement backend authorization, idempotency and audit rather than replacing them.

## Acceptance

- [ ] MT-S24-AC1: Verified billing governs access; repeated/out-of-order events and concurrent work cannot duplicate allowances/settlement, and temporary exceptions expire without changing payment truth.
- [ ] MT-S24-AC2: Unknown Astra outcomes reconcile before replay; retries recheck current grants, applicability and source state and cannot republish withdrawals; cancellation stays pending until confirmed.
- [ ] MT-S24-AC3: Health separates unknown/stale from healthy and outages from knowledge gaps; deletion/restore covers original and source-bearing derived stores without resurrecting revoked/withdrawn content.
- [ ] MT-S24-AC4: Only qualified scope activates; named reviewers accept full access/source/procedure/escalation/audit/recovery evidence, while missing model/host/pilot results remain pending and critical procedural/access failures block release.

## Verification and demonstration

Simulate a duplicate renewal and remote response loss, reconcile without duplicate inference, then restore an old index after a manual withdrawal and access revocation. Confirm those restrictions hold and complete the permitted source-to-answer/escalation workflow.

Use domain checks for applicability/procedure transitions, integration tests for grants/indexes/jobs and browser checks for operator journeys. Include direct requests and races, not only visible buttons. Verify citation resolution separately from whether a passage supports a generated claim.

Retain feature/task checklist, contract/migration changes, redacted traces/screenshots, test outcomes including failures and reviewer decision. Record application, parser, model/prompt, corpus/index, asset profile, policy and host versions as applicable. No secrets or unapproved manuals/site information belong in evidence. Mocks and provider sandbox results stay labelled.

## Exit and handoff

Apply the [admin checklist](../../../docs/09-admin-panel-specification.md) and [quality requirements](../../../docs/06-quality-security-operations.md). Carry incomplete dependencies explicitly. Required controls precede S17 paid-pilot acceptance and feed S18 release.

Update [status](../../../_STATUS.md), [coverage](../../../docs/03-module-feature-sprint-matrix.md) and [decisions](../../../docs/08-decisions-and-references.md) only from actual evidence. Critical source/applicability/access failures cannot be waived by downstream completion. This sprint adds no equipment control, invented procedure or automatic feedback publication.
