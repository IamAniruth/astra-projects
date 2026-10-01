# SR S16: Independent summary and draft evaluation

PI-06 | Module M16 | Status: Planned | Conditional core scope

## Objective and user story

As a product owner, I can use independent summary and draft evaluation with traceable facts, customer isolation and explicit review.

## Features

- SR-S16-F01: Evaluate held-out cases by thread/customer and issue family with independent reviewers.
- SR-S16-F02: Measure summary/support/disclosure errors, review time, factual corrections and capacity.

## Dependencies and entry criteria

Review S15 evidence and carry incomplete dependencies explicitly. Implementation follows S01 go/no-go and S02 feasibility. Paid pilots require applicable S13-S15 commercial/operational readiness. Confirm data rights, support reviewer, channel/language scope and capacity.

See [coverage](../../../docs/03-module-feature-sprint-matrix.md), [Astra mapping](../../../docs/07-astra-llm-feature-mapping.md) and [quality requirements](../../../docs/06-quality-security-operations.md).

## Tasks and ownership

| Task | Deliverable |
|---|---|
| SR-S16-T01 | Product/support owner: define examples, exclusions, customer-disclosure rules and acceptance. |
| SR-S16-T02 | Evaluate held-out cases by thread/customer and issue family with independent reviewers. |
| SR-S16-T03 | Measure summary/support/disclosure errors, review time, factual corrections and capacity. |
| SR-S16-T04 | QA/support reviewer: execute positive/negative cases, record failures and independently review evidence. |

React owns screens; Next.js owns identity, cases, revisions, approvals and business APIs; Astra integration owns private adapters; support/knowledge owners approve source authority and reply rules; QA/operations owns qualification and recovery. Name individual owners before starting. New runtime or business-system wrappers remain explicit integration tasks.

## Acceptance

- [ ] SR-S16-AC1: Both features have concrete artifacts or working behavior with actual evidence.
- [ ] SR-S16-AC2: Registered thresholds pass on actual configuration; cross-customer disclosure or critical unsupported commitment blocks release.
- [ ] SR-S16-AC3: Changed surfaces enforce tenant/team/case/source grants, public/private boundaries, freshness and typed failures; record non-applicable cases.
- [ ] SR-S16-AC4: Reviewer decision records versions, failed/pending checks and limits. Mocks cannot establish real-model or production readiness.

## Verification and demonstration

Expected evidence: independent scorecard, failure corpus and target-host report. Demonstrate the feature outcomes and acceptance negatives above. Use domain checks for chronology/approval/freshness, integration checks for access/jobs/imports and browser checks for changed journeys where applicable.

AI evidence identifies checkpoint, prompt, case versions, source/index hashes, live-fact snapshot when applicable, host and manifest. Check citation resolution separately from claim support. Do not commit customer data without permission. Missing live queries must remain explicit missing facts, not simulated production success.

## Exit and handoff

Accept only with linked evidence and named reviewer. Update [status](../../../_STATUS.md), coverage and dependency records. Cross-customer disclosure, critical unsupported commitments and relevant release blockers cannot be waived by downstream completion.
