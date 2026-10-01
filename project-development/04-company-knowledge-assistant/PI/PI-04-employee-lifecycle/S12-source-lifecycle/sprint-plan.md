# CK S12: Freshness withdrawal and end-to-end lifecycle

PI-04 | Module M12 | Status: Planned | Conditional core scope

## Objective and user story

As a company knowledge stakeholder, I can use freshness withdrawal and end-to-end lifecycle with authorized current sources and traceable outcomes.

## Features

- CK-S12-F01: Implement source review reminders, supersession and withdrawal across derived stores.
- CK-S12-F02: Demonstrate upload-publish-search-answer-gap-update with current grants.

## Dependencies and entry criteria

Review S11 evidence and carry incomplete dependencies explicitly. Implementation requires S01 go/no-go and S02 feasibility. Paid pilots need applicable S13-S15 commercial/operational readiness. Confirm source rights, reviewer identity, audience and sprint capacity.

See [coverage](../../../docs/03-module-feature-sprint-matrix.md), [Astra mapping](../../../docs/07-astra-llm-feature-mapping.md) and [quality requirements](../../../docs/06-quality-security-operations.md).

## Tasks and ownership

| Task | Deliverable |
|---|---|
| CK-S12-T01 | Product/content owner: define examples, exclusions, access boundaries and feature acceptance. |
| CK-S12-T02 | Implement source review reminders, supersession and withdrawal across derived stores. |
| CK-S12-T03 | Demonstrate upload-publish-search-answer-gap-update with current grants. |
| CK-S12-T04 | QA/content reviewer: run positive/negative cases, record failures and independently review evidence. |

React owns screens; Next.js owns identity, publication, access and business APIs; Astra integration owns private adapters; content owners approve source authority/applicability; QA/operations owns qualification and recovery. Assign named owners before starting. New runtime wrappers remain explicit upstream integration work.

## Acceptance

- [ ] CK-S12-AC1: Both features produce concrete artifacts or demonstrated behavior with actual evidence.
- [ ] CK-S12-AC2: Cached/history answers cannot bypass withdrawal; source corrections regenerate affected answers or label them stale; owner review controls republication.
- [ ] CK-S12-AC3: Changed surfaces enforce tenant/document/conversation scope, source applicability and typed failures; record non-applicable cases.
- [ ] CK-S12-AC4: Reviewer decision names versions, failed/pending checks and limitations. Mocks cannot establish model or production readiness.

## Verification and demonstration

Expected evidence: end-to-end evidence and source/access invalidation tests. Demonstrate the specific feature outcomes and acceptance negatives above. Use domain checks for policy dates/publication state, integration checks for grants/index/jobs and browser checks for changed journeys where applicable.

AI evidence identifies checkpoint, prompt, parser, corpus/index hash, audience/policy configuration, host and manifest. Validate citation resolution separately from source support. Do not commit internal documents or employee questions without permission. Missing buyer/model/host evidence leaves relevant acceptance pending.

## Exit and handoff

Accept only with linked evidence and named reviewer. Update [status](../../../_STATUS.md), coverage and dependency records. Unauthorized disclosure, unresolved critical answer errors and relevant release blockers cannot be waived by later completion.
