# CK S23: Admin publication and private knowledge gaps

PI-08 | Module M23 | Status: Planned | Conditional administration scope  
Source: [Admin specification](../../../docs/09-admin-panel-specification.md)

## Objective and features

As an authorized content owner or gap reviewer, I can use admin publication and private knowledge gaps while preserving source authority, current grants and employee-question privacy.

- CK-S23-F01: Source publication, effective-policy selection and withdrawal governance
- CK-S23-F02: Authorized gap review and privacy-preserving trend administration

## Dependencies and entry criteria

S22 authorization/audit; S04-S06 publication/parsing/indexing, S07-S09 search/explanations/applicability and S10-S12 gaps/history/freshness. S14 qualifies enabled scope. Confirm precedence, historical modes, review authority, disclosed gap capture and aggregate suppression rules.

Assign named product/content/privacy, React, Next.js/data, Astra integration and QA/operations owners. Confirm permitted documents/questions, contracts and capacity. Fixtures support development but cannot establish actual model/provider/host quality. Optional PI-07 is not a prerequisite.

## Tasks and ownership

| Task | Deliverable |
|---|---|
| CK-S23-T01 | Content/privacy owners: define exact-revision publication, audience/effective dates, historical rules, gap receiving scopes and disclosure tests for aggregates. |
| CK-S23-T02 | React/Next.js: build source/index review and scoped lifecycle impact views; orchestrate publish/access/withdraw through current services with expected-version checks. |
| CK-S23-T03 | Backend/data: enforce immediate serving/follow-up invalidation and private gap assignment; prevent unrestricted history access and small-group/filter/differencing disclosure in trends. |
| CK-S23-T04 | QA/content/privacy: test future/expired/site-specific policies, conflicts, withdrawal races, revised group grants, unauthorized gap reassignment and owner replies remaining unpublished. |

Reuse [data/API contracts](../../../docs/04-data-and-api.md) and the admin specification's extensions. Authorize nested records, aggregates and artifacts server-side. Return typed validation, permission, stale-version, unavailable and reconciliation failures without restricted metadata. Confirmations supplement backend authorization, idempotency/concurrency and audit.

## Acceptance

- [ ] CK-S23-AC1: Only reviewed audience-appropriate and effective sources with validated indexes support current answers; future policies and ambiguous conflicts cannot be silently treated as current authority.
- [ ] CK-S23-AC2: Withdrawal/narrowed grants block affected retrieval, answer delivery, citation viewing and follow-ups during asynchronous cleanup; explicit historical use still enforces current grants.
- [ ] CK-S23-AC3: Gap questions/evidence appear only to the authorized review audience; assignment cannot silently widen scope and small-group/filter/overlapping report tests enforce the reviewed suppression policy.
- [ ] CK-S23-AC4: Feedback/owner replies never auto-publish policy, trigger HR/finance decisions or imply training permission; actual versions and privacy/access negatives receive named reviewer decisions.

## Verification and demonstration

Publish site-specific current and future policies, generate a cited explanation, submit a private question to a named owner scope and attempt unauthorized reassignment/drill-down. Withdraw a source during generation and verify history cannot reintroduce it on a follow-up.

Use domain checks for effective policy/state, integration tests for grants/indexes/history/jobs and browser checks for changed journeys. Include direct API negatives, concurrent changes and filter combinations. Check citation resolution separately from actual claim support.

Retain feature/task checklist, contract/migration changes, redacted traces/screenshots, results including failures and named reviewer decision. Record application, parser, model/prompt, source/index/access-policy, corpus and host versions as applicable. Do not put secrets, unapproved internal documents or employee questions into evidence. Mocks and sandbox results remain labelled.

## Exit and handoff

Apply the [admin checklist](../../../docs/09-admin-panel-specification.md) and [quality requirements](../../../docs/06-quality-security-operations.md). Carry incomplete dependencies explicitly. Required controls precede S17 paid-pilot acceptance and feed S18 readiness.

Update [status](../../../_STATUS.md), [coverage](../../../docs/03-module-feature-sprint-matrix.md) and [decisions](../../../docs/08-decisions-and-references.md) only from actual evidence. Critical access/policy failures cannot be waived by downstream completion. No business decision/action, employee scoring, automatic publication or training is enabled.
