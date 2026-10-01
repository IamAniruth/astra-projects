# SR S10: Disclosure checks and agent review

PI-04 | Module M10 | Status: Planned | Conditional core scope

## Objective and user story

As a support-team stakeholder, I can use disclosure checks and agent review with traceable facts, customer isolation and explicit review.

## Features

- SR-S10-F01: Build separate internal evidence and customer-facing reply views.
- SR-S10-F02: Check private notes, unrelated customer data, internal links and edited draft content.

## Dependencies and entry criteria

Review S09 evidence and carry incomplete dependencies explicitly. Implementation follows S01 go/no-go and S02 feasibility. Paid pilots require applicable S13-S15 commercial/operational readiness. Confirm data rights, support reviewer, channel/language scope and capacity.

See [coverage](../../../docs/03-module-feature-sprint-matrix.md), [Astra mapping](../../../docs/07-astra-llm-feature-mapping.md) and [quality requirements](../../../docs/06-quality-security-operations.md).

## Tasks and ownership

| Task | Deliverable |
|---|---|
| SR-S10-T01 | Product/support owner: define examples, exclusions, customer-disclosure rules and acceptance. |
| SR-S10-T02 | Build separate internal evidence and customer-facing reply views. |
| SR-S10-T03 | Check private notes, unrelated customer data, internal links and edited draft content. |
| SR-S10-T04 | QA/support reviewer: execute positive/negative cases, record failures and independently review evidence. |

React owns screens; Next.js owns identity, cases, revisions, approvals and business APIs; Astra integration owns private adapters; support/knowledge owners approve source authority and reply rules; QA/operations owns qualification and recovery. Name individual owners before starting. New runtime or business-system wrappers remain explicit integration tasks.

## Acceptance

- [ ] SR-S10-AC1: Both features have concrete artifacts or working behavior with actual evidence.
- [ ] SR-S10-AC2: Accessible internal material is not automatically disclosable; agent edits receive checks and risky content blocks approval.
- [ ] SR-S10-AC3: Changed surfaces enforce tenant/team/case/source grants, public/private boundaries, freshness and typed failures; record non-applicable cases.
- [ ] SR-S10-AC4: Reviewer decision records versions, failed/pending checks and limits. Mocks cannot establish real-model or production readiness.

## Verification and demonstration

Expected evidence: disclosure fixtures and review-workbench walkthrough. Demonstrate the feature outcomes and acceptance negatives above. Use domain checks for chronology/approval/freshness, integration checks for access/jobs/imports and browser checks for changed journeys where applicable.

AI evidence identifies checkpoint, prompt, case versions, source/index hashes, live-fact snapshot when applicable, host and manifest. Check citation resolution separately from claim support. Do not commit customer data without permission. Missing live queries must remain explicit missing facts, not simulated production success.

## Exit and handoff

Accept only with linked evidence and named reviewer. Update [status](../../../_STATUS.md), coverage and dependency records. Cross-customer disclosure, critical unsupported commitments and relevant release blockers cannot be waived by downstream completion.
