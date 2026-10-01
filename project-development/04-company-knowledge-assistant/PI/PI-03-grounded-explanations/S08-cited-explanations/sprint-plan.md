# CK S08: Cited explanations and abstention

PI-03 | Module M08 | Status: Planned | Conditional core scope

## Objective and user story

As a company knowledge stakeholder, I can use cited explanations and abstention with authorized current sources and traceable outcomes.

## Features

- CK-S08-F01: Generate bounded source-supported explanations with claim citations.
- CK-S08-F02: Check spans, current grants/freshness, runtime budgets and typed failures.

## Dependencies and entry criteria

Review S07 evidence and carry incomplete dependencies explicitly. Implementation requires S01 go/no-go and S02 feasibility. Paid pilots need applicable S13-S15 commercial/operational readiness. Confirm source rights, reviewer identity, audience and sprint capacity.

See [coverage](../../../docs/03-module-feature-sprint-matrix.md), [Astra mapping](../../../docs/07-astra-llm-feature-mapping.md) and [quality requirements](../../../docs/06-quality-security-operations.md).

## Tasks and ownership

| Task | Deliverable |
|---|---|
| CK-S08-T01 | Product/content owner: define examples, exclusions, access boundaries and feature acceptance. |
| CK-S08-T02 | Generate bounded source-supported explanations with claim citations. |
| CK-S08-T03 | Check spans, current grants/freshness, runtime budgets and typed failures. |
| CK-S08-T04 | QA/content reviewer: run positive/negative cases, record failures and independently review evidence. |

React owns screens; Next.js owns identity, publication, access and business APIs; Astra integration owns private adapters; content owners approve source authority/applicability; QA/operations owns qualification and recovery. Assign named owners before starting. New runtime wrappers remain explicit upstream integration work.

## Acceptance

- [ ] CK-S08-AC1: Both features produce concrete artifacts or demonstrated behavior with actual evidence.
- [ ] CK-S08-AC2: Unsupported answers abstain; fabricated citations fail; revoked access during generation blocks delivery.
- [ ] CK-S08-AC3: Changed surfaces enforce tenant/document/conversation scope, source applicability and typed failures; record non-applicable cases.
- [ ] CK-S08-AC4: Reviewer decision names versions, failed/pending checks and limitations. Mocks cannot establish model or production readiness.

## Verification and demonstration

Expected evidence: answer-support report and citation/cancellation/race traces. Demonstrate the specific feature outcomes and acceptance negatives above. Use domain checks for policy dates/publication state, integration checks for grants/index/jobs and browser checks for changed journeys where applicable.

AI evidence identifies checkpoint, prompt, parser, corpus/index hash, audience/policy configuration, host and manifest. Validate citation resolution separately from source support. Do not commit internal documents or employee questions without permission. Missing buyer/model/host evidence leaves relevant acceptance pending.

## Exit and handoff

Accept only with linked evidence and named reviewer. Update [status](../../../_STATUS.md), coverage and dependency records. Unauthorized disclosure, unresolved critical answer errors and relevant release blockers cannot be waived by later completion.
