# MT S18: Release and support handover

PI-06 | Module M18 | Status: Planned | Conditional core scope

## Objective and user story

As a product owner, I can rely on release and support handover with applicable approved sources and traceable outcomes.

## Features

- MT-S18-F01: Close product and applicable Astra blockers with named evidence owners.
- MT-S18-F02: Pin model/corpus/index/app versions, rehearse rollback and publish support boundaries.

## Dependencies and entry criteria

Review S17 evidence and carry incomplete dependencies explicitly. Application implementation follows S01 go/no-go and S02 feasibility decisions. Paid pilots require applicable S13-S15 commercial and operational readiness. Assign a domain reviewer and confirm document rights, equipment scope and sprint capacity.

See [coverage](../../../docs/03-module-feature-sprint-matrix.md), [Astra dependencies](../../../docs/07-astra-llm-feature-mapping.md) and [quality requirements](../../../docs/06-quality-security-operations.md).

## Tasks and ownership

| Task | Deliverable |
|---|---|
| MT-S18-T01 | Product/domain owner: specify examples, unsupported cases, source authority and acceptance for both features. |
| MT-S18-T02 | Close product and applicable Astra blockers with named evidence owners. |
| MT-S18-T03 | Pin model/corpus/index/app versions, rehearse rollback and publish support boundaries. |
| MT-S18-T04 | QA/domain reviewer: run positive/negative cases, record failures and independently review evidence. |

React owns screens; Next.js owns sessions, equipment identity, approval state and APIs; Astra integration owns private runtime adapters; document owners approve source applicability; QA/operations owns qualification and recovery. Name individual owners before starting. New upstream wrappers remain explicit integration work.

## Acceptance

- [ ] MT-S18-AC1: F01 and F02 produce reviewable artifacts or working behavior with actual evidence.
- [ ] MT-S18-AC2: Release requires independent domain, security, operations and pilot evidence; open blockers prevent a supported-production claim.
- [ ] MT-S18-AC3: Changed surfaces enforce tenant/site/document grants, applicable source revisions and error states; record non-applicable cases.
- [ ] MT-S18-AC4: Reviewer decision names versions, failed/pending checks and scope limits. Mocks cannot establish real-model or production readiness.

## Verification and demonstration

Expected evidence: release manifest, rollback result and support runbooks. Demonstrate the specific outcomes and negative cases above. Use meaningful domain checks for applicability and procedure state, integration checks for access/index/jobs and browser checks for changed journeys where applicable.

For AI-dependent work record checkpoint, prompt, parser, corpus/index hash, supported asset profile, host and manifest versions. Evaluate citation resolution separately from whether the passage supports the claim. Never replace missing real-source evidence with a fabricated success. Do not commit unapproved manuals or site information.

## Exit and handoff

Accept only with linked evidence and named reviewer. Update [status](../../../_STATUS.md), coverage and dependency records. Unresolved critical source, applicability, access or quality failures remain blockers; downstream completion cannot waive them.
