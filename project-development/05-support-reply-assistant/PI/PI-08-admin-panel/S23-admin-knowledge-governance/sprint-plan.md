# SR S23: Admin knowledge and reply governance

PI-08 | Module M23 | Status: Planned | Conditional administration scope  
Source: [Admin specification sections 6-7 and 12](../../../docs/09-admin-panel-specification.md)

## Objective and user story

As a knowledge owner or authorized support reviewer, I can manage source publication and inspect review history while preserving current evidence, private information and exact-revision approval.

## Features

- SR-S23-F01: Build import reconciliation, approved-source publication and index-readiness administration.
- SR-S23-F02: Build qualified reply-setting controls, approval history and manual-handoff inspection.

## Dependencies and entry criteria

S22 authorization/audit foundations; S04-S06 import, publication and indexing contracts; S07-S12 summary/draft dependencies, revision approval and export contracts. S14 supplies qualification evidence for enabled language/tone settings.

Confirm knowledge owners, source authority, import IDs/format, public/private semantics and approved configuration versions. Missing upstream services remain blocked dependencies rather than alternate admin implementations.

## Tasks and ownership

| Task | Deliverable |
|---|---|
| SR-S23-T01 | Knowledge/support owner: define publication review, applicability, example redaction and qualified reply-setting transitions. |
| SR-S23-T02 | Frontend/backend: build import errors/conflicts, immutable revision detail, publication review and separate index readiness. |
| SR-S23-T03 | Backend: orchestrate publish/withdraw through existing services; invalidate dependencies immediately and display scoped impact while cleanup runs. |
| SR-S23-T04 | Frontend/backend: expose revision-bound approval/handoff history and versioned qualified settings; retain internal evidence in the protected workbench. |
| SR-S23-T05 | QA/domain reviewer: verify import conflicts, withdrawal races, stale revisions, disclosure filtering and missing live-fact handling. |

Name individual owners. Reuse existing publication, draft approval and export contracts; do not add an administrative bypass.

## Data and API work

Use KnowledgeRevision, Publication, ReusableExample, CaseRevision, DraftRevision, Approval and Handoff. Retain hashes, applicability, audience, effective dates, index generation and provenance. Store qualified settings as reviewed versions with owner/effective time.

Reuse knowledge publish/withdraw and draft approval/export APIs in the data/API plan. Apply current grants and optimistic revision checks. Index cleanup must not be the mechanism that determines immediate publication eligibility.

## Acceptance

- [ ] SR-S23-AC1: Only authorized knowledge owners can publish an exact reviewed revision; unpublished/expired/inapplicable sources remain ineligible.
- [ ] SR-S23-AC2: Withdrawal immediately blocks retrieval/use and invalidates dependent approval even with delayed index cleanup or generation in flight.
- [ ] SR-S23-AC3: Identical import retries do not duplicate messages; conflicting IDs require reconciliation, preserving chronology and private visibility.
- [ ] SR-S23-AC4: Raw prior tickets cannot become policy; reusable examples require separate review/redaction and do not confer training permission.
- [ ] SR-S23-AC5: New messages, changed facts/policy and edits make affected approvals stale; direct admin requests cannot force export.
- [ ] SR-S23-AC6: Public artifacts contain only approved public text and allowlisted links, excluding internal notes/private URLs and other customer data.
- [ ] SR-S23-AC7: Handoff history says copied/exported only; no action sends, closes a ticket or executes a customer remedy.
- [ ] SR-S23-AC8: Missing or expired live facts remain blockers; operator approval cannot turn an unsupported claim into verified truth.
- [ ] SR-S23-AC9: Unqualified setting versions cannot activate; evidence/history/impact views remain restricted by current grants.

## Verification and demonstration

Use permitted or synthetic cases with similar customer identities, private notes, conflicting import IDs, unpublished articles and changed policies. Demonstrate publication, index readiness, reviewed drafting and manual export; then withdraw a cited policy during generation and attempt an old export.

Capture browser/API traces, revision/hash dependency records, conflict outcomes and redacted audit events. Include races between approval/export and new messages, publication withdrawal and grant revocation. Real-model factuality requires separate S16 evidence; fixtures establish workflow behavior only.

## Exit and handoff

Knowledge owner, support reviewer and QA sign the evidence record with failures and limits. Hand the governed workflow and typed blocker states to S24 for the integrated pilot drill. Required governance controls must be available before S17; optional feedback/training/integration controls remain S19-S21.

See [PI plan](../README.md), [status](../../../_STATUS.md) and [AI workflow](../../../docs/05-ai-workflow.md).
