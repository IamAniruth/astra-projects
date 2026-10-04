# SR S22: Admin access and workspace management

PI-08 | Module M22 | Status: Planned | Conditional administration scope  
Source: [Admin specification sections 1-5, 10 and 12](../../../docs/09-admin-panel-specification.md)

## Objective and user story

As a workspace administrator or authorized platform operator, I can manage the teams and workspaces within my responsibility without gaining unrelated case content or platform privileges.

## Features

- SR-S22-F01: Build authenticated workspace/platform navigation, scoped overview and onboarding detail.
- SR-S22-F02: Implement administrative permissions, membership changes, revocation and audited support-access grants.

## Dependencies and entry criteria

Accepted S01/S02 decisions and available S03 identity, team and case/source authorization contracts. Confirm individual role owners, role combinations, support-access approving authority, MFA/session approach and whether agents may approve their own replies.

Seat controls integrate with S13; invitation acceptance cannot be released commercially until its counting rule and atomic limit checks exist. Use explicit unavailable/pending states for unfinished dependencies.

## Tasks and ownership

| Task | Deliverable |
|---|---|
| SR-S22-T01 | Product/security: approve role-action-resource matrix, scope boundaries, support-access expiry and invitation rules. |
| SR-S22-T02 | Frontend: build settings/admin shell, search/filter/pagination, scoped overview, workspace detail, onboarding checklist and loading/empty/error states. |
| SR-S22-T03 | Backend: authorize list/detail/aggregate queries; add invitation and versioned membership actions; prevent privilege escalation and enforce configured seat policy. |
| SR-S22-T04 | Backend/security: enforce privileged MFA, session revocation, expiring scoped support grants and audit writes for changes/content reads. |
| SR-S22-T05 | QA: exercise two tenants, restricted cases, direct API requests, simultaneous membership changes, stale sessions and in-flight output revocation. |

Name individual owners at kickoff. Reuse S03 domain services; this sprint owns their admin presentation and orchestration.

## Data and API work

Use Workspace, Team, Agent and Membership; extend with explicit permissions, onboarding records and support-access grants where needed. Implement the proposed workspace list, admin overview, invitation and membership routes from the specification.

Derive identity and grants server-side. Use optimistic concurrency for edits, idempotency for invitations and safe typed errors. Counts and search results obey the same grants as detail pages. Record actor, reason, target, version, request ID and outcome without storing sensitive payloads.

## Acceptance

- [ ] SR-S22-AC1: Agents and workspace administrators cannot invoke platform actions through direct requests or altered IDs.
- [ ] SR-S22-AC2: Team/case/source restrictions hold for lists, counts, search, details and artifact links across two tenants.
- [ ] SR-S22-AC3: Removing a member invalidates sessions and prevents cached, historical and in-flight output access while retaining historical reviewer attribution.
- [ ] SR-S22-AC4: Expired or unapproved support-access grants deny content access; permitted reads are audited.
- [ ] SR-S22-AC5: Concurrent invitations cannot exceed the selected seat rule; stale membership edits produce a conflict instead of overwriting another change.
- [ ] SR-S22-AC6: Workspace, subscription and onboarding states remain distinct; unfinished commercial dependencies are visible.
- [ ] SR-S22-AC7: Privileged actions require appropriate authentication, confirmation and backend checks; audit history cannot be edited by ordinary administrators.
- [ ] SR-S22-AC8: Navigation and forms expose accessible labels, keyboard operation and comprehensible loading/error/permission states.

## Verification and demonstration

Produce the permission matrix, API negative-test traces, browser walkthrough, revocation race results and redacted audit samples. Demonstrate an administrator onboarding their workspace, inviting an allowed member and losing access after revocation. An operator account without a scoped content grant must see safe metadata only.

Tests may use synthetic two-tenant fixtures. Mocked identity or billing cannot establish production authentication or commercial readiness; record actual integration evidence when available.

## Exit and handoff

Review evidence with security and product owners. Carry available authorization/audit contracts into S23/S24. Link actual artifacts and unresolved S13 dependencies in the acceptance record; leave sprint status Planned until execution begins.

See [PI plan](../README.md), [status](../../../_STATUS.md) and [quality requirements](../../../docs/06-quality-security-operations.md).
