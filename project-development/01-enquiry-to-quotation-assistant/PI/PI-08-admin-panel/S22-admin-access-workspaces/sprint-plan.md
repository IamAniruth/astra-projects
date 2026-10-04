# EQ S22: Admin access and workspace management

**Status:** Planned  
**PI:** [PI-08 Administration](../README.md)  
**Cadence assumption:** two weeks; estimate and named owners required  
**Modules:** M02 M03 M16 M18 M19  
**Source:** [Admin panel specification](../../../docs/13-admin-panel-specification.md)

## Sprint objective and user story

As an authorized workspace administrator or platform operator, I can use admin access and workspace management while preserving customer isolation, authoritative business data and accountable actions.

- EQ-S22-F01: Workspace/platform shell, onboarding and permission-filtered overviews
- EQ-S22-F02: Administrative membership, revocation and controlled support access

## Dependencies and entry criteria

S01 contracts, S02 authenticated identity and S03 workspace roles; S13 onboarding contracts. Integrate S14 seat rules before releasing seat-limited invitations. Confirm support-access authority, role combinations, MFA/session policy and named owners.

Confirm permitted examples, contract/config versions, individual owners and realistic capacity. Fixtures may enable UI work but cannot satisfy actual provider, model or target-host acceptance. PI-07 is not required.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S22-T01 | Product/domain reviewer | Finalize role/action/resource matrix, onboarding checklist, support-grant authority/expiry and invitation-counting rule. |
| EQ-S22-T02 | React frontend | Build /settings and /admin shells, workspace lists/details, scoped counts, onboarding and accessible loading/error states. |
| EQ-S22-T03 | Next.js/backend | Reuse membership APIs with server role checks, atomic seat checks, expiring invitations and optimistic concurrency; block platform privilege escalation. |
| EQ-S22-T04 | Astra integration | Keep Astra credentials private and propagate current workspace/principal grants; revoked users cannot receive queued/in-flight output. |
| EQ-S22-T05 | Data/contracts | Persist scoped support-access grants and onboarding metadata; audit privileged changes and content reads with safe values. |
| EQ-S22-T06 | QA/operations | Exercise two tenants, overlapping customer/SKU names, direct API requests, stale sessions, concurrent invitations and support-grant expiry. |

Reuse existing domain APIs under /api/v1 and the proposed additions in the admin specification. Enforce identity and scope on the server; never trust a client workspace or approval flag. Return typed conflicts/validation/access errors with correlation IDs and no sensitive payloads. Privileged mutations need confirmation, reason where applicable, idempotency and audit.

## Acceptance criteria

- [ ] EQ-S22-AC1: Ordinary workspace owners cannot invoke platform operations; IDs, counts, search and files never cross tenant scope.
- [ ] EQ-S22-AC2: Revocation blocks active sessions, historical links and in-flight output while preserving actor attribution in historical approvals.
- [ ] EQ-S22-AC3: Support content access requires approved purpose/scope/expiry; ordinary operators receive redacted metadata and all permitted reads are audited.
- [ ] EQ-S22-AC4: Concurrent invitations honor the selected seat policy; stale membership writes conflict instead of overwriting changes.
- [ ] EQ-S22-AC5: Onboarding, billing and processing states remain distinct; missing service dependencies appear pending and cannot be bypassed.
- [ ] EQ-S22-AC6: Keyboard/browser/API demonstrations cover loading, empty, error and forbidden states; named reviewers accept actual evidence and document remaining blockers.

## Test and evidence plan

Use domain tests for state/calculation invariants, integration tests for actual auth/storage/jobs/billing, and browser tests for changed operator journeys. Include negative direct-API requests and concurrent/stale requests rather than testing only button visibility.

Retain the feature/task checklist, contract/migration changes, redacted API traces or screenshots, results including failures, and reviewer decision. Record actual commit, configuration and relevant model/prompt/data/host versions. Store no credentials or unapproved customer documents in evidence. Sandbox/mocked results must be labelled and cannot establish live readiness.

## Sprint review demonstration

Onboard workspace A, invite permitted staff, reject access to workspace B, grant and expire scoped support access, then revoke a member and attempt an old artifact link.

## Exit and handoff

Accept only with linked evidence and named reviewers. Carry incomplete dependencies explicitly; documentation alone leaves this sprint Planned. Required controls precede S17 paid-pilot acceptance; S18 incorporates final administration readiness.

Update [status](../../../_STATUS.md), [feature matrix](../../../docs/12-module-feature-sprint-matrix.md) and [decisions](../../../docs/09-decisions-and-risks.md). Apply the [quality definition of done](../../../docs/07-quality-security-international.md). No automatic outbound messaging or collection of payments for quoted goods is added.
