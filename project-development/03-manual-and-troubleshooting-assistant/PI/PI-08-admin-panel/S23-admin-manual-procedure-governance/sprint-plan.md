# MT S23: Admin manual and procedure governance

PI-08 | Module M23 | Status: Planned | Conditional administration scope  
Source: [Admin specification](../../../docs/09-admin-panel-specification.md)

## Objective and features

As an authorized document owner or domain reviewer, I can use admin manual and procedure governance with current access, applicable approved sources and attributable actions.

- MT-S23-F01: Manual review, applicability, index publication and withdrawal administration
- MT-S23-F02: Approved procedure lifecycle and internal expert escalation governance

## Dependencies and entry criteria

S22 authorization/audit; S04-S06 manual registry/parsing/publication, S07-S09 retrieval/answer/procedure services and S10-S12 escalation/history/withdrawal contracts. S14 qualifies enabled scope. Confirm source authority, applicability precedence, mandatory context and procedure/expert review ownership.

Assign named product/domain, React, Next.js/data, Astra integration and QA/operations owners. Confirm permitted documents, contract versions and capacity. Fixtures support development but do not qualify equipment guidance, actual model or production host. Optional PI-07 is not a dependency.

## Tasks and ownership

| Task | Deliverable |
|---|---|
| MT-S23-T01 | Document/domain owners: define exact-revision approval, applicability/precedence, serial-range supersession and procedure review examples. |
| MT-S23-T02 | React/Next.js: build source/index state views, page mapping and scoped impact previews; orchestrate approval/withdrawal through existing services with version checks. |
| MT-S23-T03 | Backend/Astra integration: enforce immediate current-state gates during retrieval/delivery/viewing; preserve procedure dependencies and invalidate affected sessions/history/caches while retaining valid older ranges. |
| MT-S23-T04 | QA/domain: test withdrawal races, index delay, wrong variants, conflicting sources, missing prerequisites, asset switching and escalation feedback remaining unpublished. |

Reuse [existing data/API contracts](../../../docs/04-data-and-api.md) and the admin specification's proposed extensions. Enforce tenant/site/document grants on nested lookups and artifacts. Use typed permission, validation, stale-version, unavailable and reconciliation failures with safe correlation IDs. Confirmations supplement backend authorization, idempotency and audit rather than replacing them.

## Acceptance

- [ ] MT-S23-AC1: Publication requires authorized exact-revision review plus index validation; parser success or upload recency cannot imply source authority/applicability.
- [ ] MT-S23-AC2: Withdrawal immediately blocks affected sources at retrieval, answer/citation delivery, history and active procedures even during cleanup; older valid serial ranges remain eligible.
- [ ] MT-S23-AC3: Procedures preserve approved version, prerequisites, warnings, order and stop conditions; unknown observations/conflicts pause or escalate without invented steps or force-continue bypass.
- [ ] MT-S23-AC4: Escalations expose only current authorized evidence; expert replies need separate document approval before publication, and no equipment actuation or external message is triggered.

## Verification and demonstration

Approve two manual revisions for different serial ranges, publish validated indexes, ask a cited question, start an approved branch and escalate uncertainty. Withdraw one source during a query/session and verify blocking while the other valid range still works.

Use domain checks for applicability/procedure transitions, integration tests for grants/indexes/jobs and browser checks for operator journeys. Include direct requests and races, not only visible buttons. Verify citation resolution separately from whether a passage supports a generated claim.

Retain feature/task checklist, contract/migration changes, redacted traces/screenshots, test outcomes including failures and reviewer decision. Record application, parser, model/prompt, corpus/index, asset profile, policy and host versions as applicable. No secrets or unapproved manuals/site information belong in evidence. Mocks and provider sandbox results stay labelled.

## Exit and handoff

Apply the [admin checklist](../../../docs/09-admin-panel-specification.md) and [quality requirements](../../../docs/06-quality-security-operations.md). Carry incomplete dependencies explicitly. Required controls precede S17 paid-pilot acceptance and feed S18 release.

Update [status](../../../_STATUS.md), [coverage](../../../docs/03-module-feature-sprint-matrix.md) and [decisions](../../../docs/08-decisions-and-references.md) only from actual evidence. Critical source/applicability/access failures cannot be waived by downstream completion. This sprint adds no equipment control, invented procedure or automatic feedback publication.
