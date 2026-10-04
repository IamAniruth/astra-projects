# MT S22: Admin sites, equipment and access

PI-08 | Module M22 | Status: Planned | Conditional administration scope  
Source: [Admin specification](../../../docs/09-admin-panel-specification.md)

## Objective and features

As an authorized site administrator, I can use admin sites, equipment and access with current access, applicable approved sources and attributable actions.

- MT-S22-F01: Workspace/platform shell, site/equipment management and onboarding
- MT-S22-F02: Administrative grants, revocation and controlled support access

## Dependencies and entry criteria

Accepted S01 discovery and S02 feasibility; S03 identity/site/equipment contracts and S13 commercial onboarding. Confirm asset verification, role combinations, support-access approval/expiry, MFA and team/site counting policy.

Assign named product/domain, React, Next.js/data, Astra integration and QA/operations owners. Confirm permitted documents, contract versions and capacity. Fixtures support development but do not qualify equipment guidance, actual model or production host. Optional PI-07 is not a dependency.

## Tasks and ownership

| Task | Deliverable |
|---|---|
| MT-S22-T01 | Product/domain/security: agree role-action-site/document matrix, equipment identity fields, onboarding and support-access authority. |
| MT-S22-T02 | React/Next.js: build scoped navigation, counts, site/asset detail and expected-version edits; derive grants server-side and prevent privilege escalation. |
| MT-S22-T03 | Backend/data: enforce MFA/session revocation, expiring support grants, audited reads/changes and equipment-context invalidation across jobs, answers and procedures. |
| MT-S22-T04 | QA/domain: exercise two tenants/sites, restricted manuals, ambiguous asset identity, concurrent asset edits, revoked in-flight access and expired support grants. |

Reuse [existing data/API contracts](../../../docs/04-data-and-api.md) and the admin specification's proposed extensions. Enforce tenant/site/document grants on nested lookups and artifacts. Use typed permission, validation, stale-version, unavailable and reconciliation failures with safe correlation IDs. Confirmations supplement backend authorization, idempotency and audit rather than replacing them.

## Acceptance

- [ ] MT-S22-AC1: Workspace owners cannot access platform operations or unauthorized sites/documents through IDs, counts, source titles, cached results or old links.
- [ ] MT-S22-AC2: Unknown serial/firmware/model context does not become a match; versioned asset edits invalidate incompatible queries/answers/procedure context.
- [ ] MT-S22-AC3: Revocation and support-grant expiry block current/in-flight access; permitted sensitive reads are audited and operators see safe metadata by default.
- [ ] MT-S22-AC4: Accessible loading/error/empty/forbidden states and onboarding are demonstrated with actual versions; missing commercial/model evidence stays pending.

## Verification and demonstration

Create two sites with similar equipment names, assign a technician one site's manuals, reject the other site and unknown serial range, then change an asset context and revoke access while a query runs.

Use domain checks for applicability/procedure transitions, integration tests for grants/indexes/jobs and browser checks for operator journeys. Include direct requests and races, not only visible buttons. Verify citation resolution separately from whether a passage supports a generated claim.

Retain feature/task checklist, contract/migration changes, redacted traces/screenshots, test outcomes including failures and reviewer decision. Record application, parser, model/prompt, corpus/index, asset profile, policy and host versions as applicable. No secrets or unapproved manuals/site information belong in evidence. Mocks and provider sandbox results stay labelled.

## Exit and handoff

Apply the [admin checklist](../../../docs/09-admin-panel-specification.md) and [quality requirements](../../../docs/06-quality-security-operations.md). Carry incomplete dependencies explicitly. Required controls precede S17 paid-pilot acceptance and feed S18 release.

Update [status](../../../_STATUS.md), [coverage](../../../docs/03-module-feature-sprint-matrix.md) and [decisions](../../../docs/08-decisions-and-references.md) only from actual evidence. Critical source/applicability/access failures cannot be waived by downstream completion. This sprint adds no equipment control, invented procedure or automatic feedback publication.
