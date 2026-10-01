# CK S01: Buyer discovery and go/no-go

PI-01 | Module M01 | Status: Planned | Conditional core scope

## Objective and user story

As a company knowledge stakeholder, I can use buyer discovery and go/no-go with authorized current sources and traceable outcomes.

## Features

- CK-S01-F01: Interview employees, operations/content owners and buyer; measure repeated questions and search time.
- CK-S01-F02: Select specialty, permitted samples, reviewers and measurable success hypotheses.

## Dependencies and entry criteria

Buyer access and permitted internal documents/questions are discovery inputs. Implementation requires S01 go/no-go and S02 feasibility. Paid pilots need applicable S13-S15 commercial/operational readiness. Confirm source rights, reviewer identity, audience and sprint capacity.

See [coverage](../../../docs/03-module-feature-sprint-matrix.md), [Astra mapping](../../../docs/07-astra-llm-feature-mapping.md) and [quality requirements](../../../docs/06-quality-security-operations.md).

## Tasks and ownership

| Task | Deliverable |
|---|---|
| CK-S01-T01 | Product/content owner: define examples, exclusions, access boundaries and feature acceptance. |
| CK-S01-T02 | Interview employees, operations/content owners and buyer; measure repeated questions and search time. |
| CK-S01-T03 | Select specialty, permitted samples, reviewers and measurable success hypotheses. |
| CK-S01-T04 | QA/content reviewer: run positive/negative cases, record failures and independently review evidence. |

React owns screens; Next.js owns identity, publication, access and business APIs; Astra integration owns private adapters; content owners approve source authority/applicability; QA/operations owns qualification and recovery. Assign named owners before starting. New runtime wrappers remain explicit upstream integration work.

## Acceptance

- [ ] CK-S01-AC1: Both features produce concrete artifacts or demonstrated behavior with actual evidence.
- [ ] CK-S01-AC2: Record buyer access, corpus rights and go/narrow/stop before implementation.
- [ ] CK-S01-AC3: Changed surfaces enforce tenant/document/conversation scope, source applicability and typed failures; record non-applicable cases.
- [ ] CK-S01-AC4: Reviewer decision names versions, failed/pending checks and limitations. Mocks cannot establish model or production readiness.

## Verification and demonstration

Expected evidence: interview notes, baseline and differentiation decision. Demonstrate the specific feature outcomes and acceptance negatives above. Use domain checks for policy dates/publication state, integration checks for grants/index/jobs and browser checks for changed journeys where applicable.

AI evidence identifies checkpoint, prompt, parser, corpus/index hash, audience/policy configuration, host and manifest. Validate citation resolution separately from source support. Do not commit internal documents or employee questions without permission. Missing buyer/model/host evidence leaves relevant acceptance pending.

## Exit and handoff

Accept only with linked evidence and named reviewer. Update [status](../../../_STATUS.md), coverage and dependency records. Unauthorized disclosure, unresolved critical answer errors and relevant release blockers cannot be waived by later completion.
