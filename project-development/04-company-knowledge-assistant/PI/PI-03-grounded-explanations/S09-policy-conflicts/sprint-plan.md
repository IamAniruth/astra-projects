# CK S09: Policy applicability and conflicts

PI-03 | Module M09 | Status: Planned | Conditional core scope

## Objective and user story

As a company knowledge stakeholder, I can use policy applicability and conflicts with authorized current sources and traceable outcomes.

## Features

- CK-S09-F01: Resolve effective dates, site exceptions and documented source authority.
- CK-S09-F02: Present source conflicts and clarification without inventing precedence.

## Dependencies and entry criteria

Review S08 evidence and carry incomplete dependencies explicitly. Implementation requires S01 go/no-go and S02 feasibility. Paid pilots need applicable S13-S15 commercial/operational readiness. Confirm source rights, reviewer identity, audience and sprint capacity.

See [coverage](../../../docs/03-module-feature-sprint-matrix.md), [Astra mapping](../../../docs/07-astra-llm-feature-mapping.md) and [quality requirements](../../../docs/06-quality-security-operations.md).

## Tasks and ownership

| Task | Deliverable |
|---|---|
| CK-S09-T01 | Product/content owner: define examples, exclusions, access boundaries and feature acceptance. |
| CK-S09-T02 | Resolve effective dates, site exceptions and documented source authority. |
| CK-S09-T03 | Present source conflicts and clarification without inventing precedence. |
| CK-S09-T04 | QA/content reviewer: run positive/negative cases, record failures and independently review evidence. |

React owns screens; Next.js owns identity, publication, access and business APIs; Astra integration owns private adapters; content owners approve source authority/applicability; QA/operations owns qualification and recovery. Assign named owners before starting. New runtime wrappers remain explicit upstream integration work.

## Acceptance

- [ ] CK-S09-AC1: Both features produce concrete artifacts or demonstrated behavior with actual evidence.
- [ ] CK-S09-AC2: Future/expired policy cannot silently appear current; material exceptions remain in explanations; historical mode is explicit.
- [ ] CK-S09-AC3: Changed surfaces enforce tenant/document/conversation scope, source applicability and typed failures; record non-applicable cases.
- [ ] CK-S09-AC4: Reviewer decision names versions, failed/pending checks and limitations. Mocks cannot establish model or production readiness.

## Verification and demonstration

Expected evidence: conflict/date/exception fixtures and content-owner review. Demonstrate the specific feature outcomes and acceptance negatives above. Use domain checks for policy dates/publication state, integration checks for grants/index/jobs and browser checks for changed journeys where applicable.

AI evidence identifies checkpoint, prompt, parser, corpus/index hash, audience/policy configuration, host and manifest. Validate citation resolution separately from source support. Do not commit internal documents or employee questions without permission. Missing buyer/model/host evidence leaves relevant acceptance pending.

## Exit and handoff

Accept only with linked evidence and named reviewer. Update [status](../../../_STATUS.md), coverage and dependency records. Unauthorized disclosure, unresolved critical answer errors and relevant release blockers cannot be waived by later completion.
