# CK S22: Admin identity, groups and access

PI-08 | Module M22 | Status: Planned | Conditional administration scope  
Source: [Admin specification](../../../docs/09-admin-panel-specification.md)

## Objective and features

As an authorized workspace/access administrator, I can use admin identity, groups and access while preserving source authority, current grants and employee-question privacy.

- CK-S22-F01: Workspace/platform shell, group administration and onboarding
- CK-S22-F02: Revocation and scoped support access across documents and conversations

## Dependencies and entry criteria

Accepted S01 discovery and S02 feasibility; S03 identity/group/workspace contracts and S13 onboarding/counting policy where applicable. Confirm delegated ownership, nested/conflicting grants, MFA, role combinations and support-access authority.

Assign named product/content/privacy, React, Next.js/data, Astra integration and QA/operations owners. Confirm permitted documents/questions, contracts and capacity. Fixtures support development but cannot establish actual model/provider/host quality. Optional PI-07 is not a prerequisite.

## Tasks and ownership

| Task | Deliverable |
|---|---|
| CK-S22-T01 | Product/security: approve role-action-resource matrix, identity authority, onboarding, group conflict rules and scoped support expiry. |
| CK-S22-T02 | React/Next.js: build workspace/group/member screens and authorized overview; enforce server grants on counts/IDs and reject privilege escalation or stale writes. |
| CK-S22-T03 | Backend/data: implement session/seat revocation and expiring support grants; propagate permission revisions through retrieval, citations, caches, history and follow-up prompt construction. |
| CK-S22-T04 | QA/security: test multiple tenants/groups, private conversations, old answer links, group transfer during generation, concurrent grant edits and support-grant expiry. |

Reuse [data/API contracts](../../../docs/04-data-and-api.md) and the admin specification's extensions. Authorize nested records, aggregates and artifacts server-side. Return typed validation, permission, stale-version, unavailable and reconciliation failures without restricted metadata. Confirmations supplement backend authorization, idempotency/concurrency and audit.

## Acceptance

- [ ] CK-S22-AC1: Workspace/platform administration does not confer blanket document or employee-question access; lists, counts, snippets and errors do not reveal restricted records.
- [ ] CK-S22-AC2: Group/seat revocation blocks sessions, shared-link recipients, cached/in-flight output and prior hidden history before follow-up generation.
- [ ] CK-S22-AC3: Support grants require approved purpose/scope/expiry and audited reads; delegated access changes cannot broaden authority beyond the actor's permission.
- [ ] CK-S22-AC4: Accessible onboarding and loading/error/empty/forbidden states are demonstrated with direct-API/race evidence; missing service or quality prerequisites remain explicit.

## Verification and demonstration

Create two workspaces and multiple groups, show one employee's permitted source and private history, then transfer groups during a query and attempt an old answer link and follow-up. Verify an ordinary admin and expired support grant cannot read that history.

Use domain checks for effective policy/state, integration tests for grants/indexes/history/jobs and browser checks for changed journeys. Include direct API negatives, concurrent changes and filter combinations. Check citation resolution separately from actual claim support.

Retain feature/task checklist, contract/migration changes, redacted traces/screenshots, results including failures and named reviewer decision. Record application, parser, model/prompt, source/index/access-policy, corpus and host versions as applicable. Do not put secrets, unapproved internal documents or employee questions into evidence. Mocks and sandbox results remain labelled.

## Exit and handoff

Apply the [admin checklist](../../../docs/09-admin-panel-specification.md) and [quality requirements](../../../docs/06-quality-security-operations.md). Carry incomplete dependencies explicitly. Required controls precede S17 paid-pilot acceptance and feed S18 readiness.

Update [status](../../../_STATUS.md), [coverage](../../../docs/03-module-feature-sprint-matrix.md) and [decisions](../../../docs/08-decisions-and-references.md) only from actual evidence. Critical access/policy failures cannot be waived by downstream completion. No business decision/action, employee scoring, automatic publication or training is enabled.
