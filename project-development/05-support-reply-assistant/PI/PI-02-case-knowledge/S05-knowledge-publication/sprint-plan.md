# SR S05: Approved help knowledge and examples

PI-02 | Module M05 | Status: Planned | Conditional core scope

## Objective and user story

As a support-team stakeholder, I can use approved help knowledge and examples with traceable facts, customer isolation and explicit review.

## Features

- SR-S05-F01: Import help sources with owner, version, product/language scope and effective dates.
- SR-S05-F02: Review publication and redacted reusable examples separately from raw prior tickets.

## Dependencies and entry criteria

Review S04 evidence and carry incomplete dependencies explicitly. Implementation follows S01 go/no-go and S02 feasibility. Paid pilots require applicable S13-S15 commercial/operational readiness. Confirm data rights, support reviewer, channel/language scope and capacity.

See [coverage](../../../docs/03-module-feature-sprint-matrix.md), [Astra mapping](../../../docs/07-astra-llm-feature-mapping.md) and [quality requirements](../../../docs/06-quality-security-operations.md).

## Tasks and ownership

| Task | Deliverable |
|---|---|
| SR-S05-T01 | Product/support owner: define examples, exclusions, customer-disclosure rules and acceptance. |
| SR-S05-T02 | Import help sources with owner, version, product/language scope and effective dates. |
| SR-S05-T03 | Review publication and redacted reusable examples separately from raw prior tickets. |
| SR-S05-T04 | QA/support reviewer: execute positive/negative cases, record failures and independently review evidence. |

React owns screens; Next.js owns identity, cases, revisions, approvals and business APIs; Astra integration owns private adapters; support/knowledge owners approve source authority and reply rules; QA/operations owns qualification and recovery. Name individual owners before starting. New runtime or business-system wrappers remain explicit integration tasks.

## Acceptance

- [ ] SR-S05-AC1: Both features have concrete artifacts or working behavior with actual evidence.
- [ ] SR-S05-AC2: Old tickets cannot override current policy; unpublished/inapplicable sources cannot support customer commitments.
- [ ] SR-S05-AC3: Changed surfaces enforce tenant/team/case/source grants, public/private boundaries, freshness and typed failures; record non-applicable cases.
- [ ] SR-S05-AC4: Reviewer decision records versions, failed/pending checks and limits. Mocks cannot establish real-model or production readiness.

## Verification and demonstration

Expected evidence: publication transitions and prior-ticket counterexamples. Demonstrate the feature outcomes and acceptance negatives above. Use domain checks for chronology/approval/freshness, integration checks for access/jobs/imports and browser checks for changed journeys where applicable.

AI evidence identifies checkpoint, prompt, case versions, source/index hashes, live-fact snapshot when applicable, host and manifest. Check citation resolution separately from claim support. Do not commit customer data without permission. Missing live queries must remain explicit missing facts, not simulated production success.

## Exit and handoff

Accept only with linked evidence and named reviewer. Update [status](../../../_STATUS.md), coverage and dependency records. Cross-customer disclosure, critical unsupported commitments and relevant release blockers cannot be waived by downstream completion.
