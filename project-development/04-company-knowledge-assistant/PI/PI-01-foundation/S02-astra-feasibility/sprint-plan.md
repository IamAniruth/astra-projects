# CK S02: Astra and knowledge feasibility

PI-01 | Module M02 | Status: Planned | Conditional core scope

## Objective and user story

As a company knowledge stakeholder, I can use astra and knowledge feasibility with authorized current sources and traceable outcomes.

## Features

- CK-S02-F01: Inspect gateway schemas, identity boundary and parser options.
- CK-S02-F02: Run scoped retrieval and cited explanation using the actual selected checkpoint.

## Dependencies and entry criteria

Review S01 evidence and carry incomplete dependencies explicitly. Implementation requires S01 go/no-go and S02 feasibility. Paid pilots need applicable S13-S15 commercial/operational readiness. Confirm source rights, reviewer identity, audience and sprint capacity.

See [coverage](../../../docs/03-module-feature-sprint-matrix.md), [Astra mapping](../../../docs/07-astra-llm-feature-mapping.md) and [quality requirements](../../../docs/06-quality-security-operations.md).

## Tasks and ownership

| Task | Deliverable |
|---|---|
| CK-S02-T01 | Product/content owner: define examples, exclusions, access boundaries and feature acceptance. |
| CK-S02-T02 | Inspect gateway schemas, identity boundary and parser options. |
| CK-S02-T03 | Run scoped retrieval and cited explanation using the actual selected checkpoint. |
| CK-S02-T04 | QA/content reviewer: run positive/negative cases, record failures and independently review evidence. |

React owns screens; Next.js owns identity, publication, access and business APIs; Astra integration owns private adapters; content owners approve source authority/applicability; QA/operations owns qualification and recovery. Assign named owners before starting. New runtime wrappers remain explicit upstream integration work.

## Acceptance

- [ ] CK-S02-AC1: Both features produce concrete artifacts or demonstrated behavior with actual evidence.
- [ ] CK-S02-AC2: Measure support/citation errors and latency; qualify the proposed stack rather than accepting upstream badges.
- [ ] CK-S02-AC3: Changed surfaces enforce tenant/document/conversation scope, source applicability and typed failures; record non-applicable cases.
- [ ] CK-S02-AC4: Reviewer decision names versions, failed/pending checks and limitations. Mocks cannot establish model or production readiness.

## Verification and demonstration

Expected evidence: pinned manifest, parser comparison and scored spike. Demonstrate the specific feature outcomes and acceptance negatives above. Use domain checks for policy dates/publication state, integration checks for grants/index/jobs and browser checks for changed journeys where applicable.

AI evidence identifies checkpoint, prompt, parser, corpus/index hash, audience/policy configuration, host and manifest. Validate citation resolution separately from source support. Do not commit internal documents or employee questions without permission. Missing buyer/model/host evidence leaves relevant acceptance pending.

## Exit and handoff

Accept only with linked evidence and named reviewer. Update [status](../../../_STATUS.md), coverage and dependency records. Unauthorized disclosure, unresolved critical answer errors and relevant release blockers cannot be waived by later completion.
