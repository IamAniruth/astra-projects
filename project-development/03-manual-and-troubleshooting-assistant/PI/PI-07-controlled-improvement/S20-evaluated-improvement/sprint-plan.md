# MT S20: Evaluated retrieval and model improvement

PI-07 | Module M20 | Status: Planned | Optional after an accepted core release

## Objective and user story

As a product owner, I can rely on evaluated retrieval and model improvement with applicable approved sources and traceable outcomes.

## Features

- MT-S20-F01: Benchmark candidate retrieval/prompt/model changes against pinned baseline.
- MT-S20-F02: Protect holdout and critical procedure cases; stage reversible promotion.

## Dependencies and entry criteria

Review S19 evidence and carry incomplete dependencies explicitly. Application implementation follows S01 go/no-go and S02 feasibility decisions. Paid pilots require applicable S13-S15 commercial and operational readiness. Assign a domain reviewer and confirm document rights, equipment scope and sprint capacity.

See [coverage](../../../docs/03-module-feature-sprint-matrix.md), [Astra dependencies](../../../docs/07-astra-llm-feature-mapping.md) and [quality requirements](../../../docs/06-quality-security-operations.md).

## Tasks and ownership

| Task | Deliverable |
|---|---|
| MT-S20-T01 | Product/domain owner: specify examples, unsupported cases, source authority and acceptance for both features. |
| MT-S20-T02 | Benchmark candidate retrieval/prompt/model changes against pinned baseline. |
| MT-S20-T03 | Protect holdout and critical procedure cases; stage reversible promotion. |
| MT-S20-T04 | QA/domain reviewer: run positive/negative cases, record failures and independently review evidence. |

React owns screens; Next.js owns sessions, equipment identity, approval state and APIs; Astra integration owns private runtime adapters; document owners approve source applicability; QA/operations owns qualification and recovery. Name individual owners before starting. New upstream wrappers remain explicit integration work.

## Acceptance

- [ ] MT-S20-AC1: F01 and F02 produce reviewable artifacts or working behavior with actual evidence.
- [ ] MT-S20-AC2: Candidate passes registered support/applicability/regression gates; rollout cannot revive withdrawn sources; rollback restores a qualified configuration.
- [ ] MT-S20-AC3: Changed surfaces enforce tenant/site/document grants, applicable source revisions and error states; record non-applicable cases.
- [ ] MT-S20-AC4: Reviewer decision names versions, failed/pending checks and scope limits. Mocks cannot establish real-model or production readiness.

## Verification and demonstration

Expected evidence: candidate scorecard and canary/rollback report. Demonstrate the specific outcomes and negative cases above. Use meaningful domain checks for applicability and procedure state, integration checks for access/index/jobs and browser checks for changed journeys where applicable.

For AI-dependent work record checkpoint, prompt, parser, corpus/index hash, supported asset profile, host and manifest versions. Evaluate citation resolution separately from whether the passage supports the claim. Never replace missing real-source evidence with a fabricated success. Do not commit unapproved manuals or site information.

## Exit and handoff

Accept only with linked evidence and named reviewer. Update [status](../../../_STATUS.md), coverage and dependency records. Unresolved critical source, applicability, access or quality failures remain blockers; downstream completion cannot waive them.
