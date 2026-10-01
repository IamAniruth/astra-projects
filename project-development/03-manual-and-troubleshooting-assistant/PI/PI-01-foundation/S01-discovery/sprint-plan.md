# MT S01: Buyer discovery and go/no-go

PI-01 | Module M01 | Status: Planned | Conditional core scope

## Objective and user story

As a maintenance-team stakeholder, I can rely on buyer discovery and go/no-go with applicable approved sources and traceable outcomes.

## Features

- MT-S01-F01: Interview technicians, document owners and buyer; measure lookup and escalation baseline.
- MT-S01-F02: Select equipment family, permitted corpus, domain reviewer and numeric pilot hypotheses.

## Dependencies and entry criteria

Buyer access and permitted manuals are discovery inputs. Application implementation follows S01 go/no-go and S02 feasibility decisions. Paid pilots require applicable S13-S15 commercial and operational readiness. Assign a domain reviewer and confirm document rights, equipment scope and sprint capacity.

See [coverage](../../../docs/03-module-feature-sprint-matrix.md), [Astra dependencies](../../../docs/07-astra-llm-feature-mapping.md) and [quality requirements](../../../docs/06-quality-security-operations.md).

## Tasks and ownership

| Task | Deliverable |
|---|---|
| MT-S01-T01 | Product/domain owner: specify examples, unsupported cases, source authority and acceptance for both features. |
| MT-S01-T02 | Interview technicians, document owners and buyer; measure lookup and escalation baseline. |
| MT-S01-T03 | Select equipment family, permitted corpus, domain reviewer and numeric pilot hypotheses. |
| MT-S01-T04 | QA/domain reviewer: run positive/negative cases, record failures and independently review evidence. |

React owns screens; Next.js owns sessions, equipment identity, approval state and APIs; Astra integration owns private runtime adapters; document owners approve source applicability; QA/operations owns qualification and recovery. Name individual owners before starting. New upstream wrappers remain explicit integration work.

## Acceptance

- [ ] MT-S01-AC1: F01 and F02 produce reviewable artifacts or working behavior with actual evidence.
- [ ] MT-S01-AC2: Record a reachable buyer, sample rights and go/narrow/stop decision before implementation.
- [ ] MT-S01-AC3: Changed surfaces enforce tenant/site/document grants, applicable source revisions and error states; record non-applicable cases.
- [ ] MT-S01-AC4: Reviewer decision names versions, failed/pending checks and scope limits. Mocks cannot establish real-model or production readiness.

## Verification and demonstration

Expected evidence: interview notes, corpus inventory and decision record. Demonstrate the specific outcomes and negative cases above. Use meaningful domain checks for applicability and procedure state, integration checks for access/index/jobs and browser checks for changed journeys where applicable.

For AI-dependent work record checkpoint, prompt, parser, corpus/index hash, supported asset profile, host and manifest versions. Evaluate citation resolution separately from whether the passage supports the claim. Never replace missing real-source evidence with a fabricated success. Do not commit unapproved manuals or site information.

## Exit and handoff

Accept only with linked evidence and named reviewer. Update [status](../../../_STATUS.md), coverage and dependency records. Unresolved critical source, applicability, access or quality failures remain blockers; downstream completion cannot waive them.
