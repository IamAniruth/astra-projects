# MT S04: Approved manual registry

PI-02 | Module M04 | Status: Planned | Conditional core scope

## Objective and user story

As a maintenance-team stakeholder, I can rely on approved manual registry with applicable approved sources and traceable outcomes.

## Features

- MT-S04-F01: Implement immutable upload/revision metadata and equipment applicability rules.
- MT-S04-F02: Build owner review, approval and draft/approved/withdrawn states.

## Dependencies and entry criteria

Review S03 evidence and carry incomplete dependencies explicitly. Application implementation follows S01 go/no-go and S02 feasibility decisions. Paid pilots require applicable S13-S15 commercial and operational readiness. Assign a domain reviewer and confirm document rights, equipment scope and sprint capacity.

See [coverage](../../../docs/03-module-feature-sprint-matrix.md), [Astra dependencies](../../../docs/07-astra-llm-feature-mapping.md) and [quality requirements](../../../docs/06-quality-security-operations.md).

## Tasks and ownership

| Task | Deliverable |
|---|---|
| MT-S04-T01 | Product/domain owner: specify examples, unsupported cases, source authority and acceptance for both features. |
| MT-S04-T02 | Implement immutable upload/revision metadata and equipment applicability rules. |
| MT-S04-T03 | Build owner review, approval and draft/approved/withdrawn states. |
| MT-S04-T04 | QA/domain reviewer: run positive/negative cases, record failures and independently review evidence. |

React owns screens; Next.js owns sessions, equipment identity, approval state and APIs; Astra integration owns private runtime adapters; document owners approve source applicability; QA/operations owns qualification and recovery. Name individual owners before starting. New upstream wrappers remain explicit integration work.

## Acceptance

- [ ] MT-S04-AC1: F01 and F02 produce reviewable artifacts or working behavior with actual evidence.
- [ ] MT-S04-AC2: Draft or inapplicable sources cannot support answers; approval records actor and exact hash; old asset ranges remain explicit.
- [ ] MT-S04-AC3: Changed surfaces enforce tenant/site/document grants, applicable source revisions and error states; record non-applicable cases.
- [ ] MT-S04-AC4: Reviewer decision names versions, failed/pending checks and scope limits. Mocks cannot establish real-model or production readiness.

## Verification and demonstration

Expected evidence: approval transitions and variant/revision fixtures. Demonstrate the specific outcomes and negative cases above. Use meaningful domain checks for applicability and procedure state, integration checks for access/index/jobs and browser checks for changed journeys where applicable.

For AI-dependent work record checkpoint, prompt, parser, corpus/index hash, supported asset profile, host and manifest versions. Evaluate citation resolution separately from whether the passage supports the claim. Never replace missing real-source evidence with a fabricated success. Do not commit unapproved manuals or site information.

## Exit and handoff

Accept only with linked evidence and named reviewer. Update [status](../../../_STATUS.md), coverage and dependency records. Unresolved critical source, applicability, access or quality failures remain blockers; downstream completion cannot waive them.
