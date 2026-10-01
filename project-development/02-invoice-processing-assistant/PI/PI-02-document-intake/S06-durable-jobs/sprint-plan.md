# IP S06: Durable jobs and allowances

PI-02 | Module M06 | Status: Planned | Conditional core scope

## Objective and features

As an accounting product stakeholder, I can use durable jobs and allowances with traceable outcomes and explicit limits.

- IP-S06-F01: Persist product/remote IDs and correlation IDs.
- IP-S06-F02: Implement retries, cancellation, reconciliation and allowance rules.

## Dependencies and entry criteria

Review S05 evidence; incomplete dependencies remain explicit. Implementation requires S01 discovery and S02 feasibility decisions. Paid pilots need applicable commercial/operational readiness from S13-S15. Confirm a domain reviewer, sample permissions and sprint capacity.

See [coverage](../../../docs/03-module-feature-sprint-matrix.md), [Astra mapping](../../../docs/07-astra-llm-feature-mapping.md) and [quality requirements](../../../docs/06-quality-security-operations.md).

## Tasks and ownership

| Task | Deliverable |
|---|---|
| IP-S06-T01 | Product/domain: specify examples, exclusions and business acceptance. |
| IP-S06-T02 | Persist product/remote IDs and correlation IDs. |
| IP-S06-T03 | Implement retries, cancellation, reconciliation and allowance rules. |
| IP-S06-T04 | QA/domain: execute acceptance cases, record failures and review evidence. |

React owns screens; Next.js owns access, contracts and persistence; Astra integration owns private adapters; QA/operations verifies recovery. Assign named owners before starting. Necessary upstream changes remain explicit integration work.

## Acceptance

- [ ] IP-S06-AC1: Both features have concrete artifacts or working behavior demonstrated.
- [ ] IP-S06-AC2: Restart/timeout cannot duplicate accepted work or charges; uncertain remote state stays explicit.
- [ ] IP-S06-AC3: Changed data surfaces enforce client scope, roles and invalid/error behavior; record non-applicable cases.
- [ ] IP-S06-AC4: Evidence names actual versions and reviewer decisions; mocks cannot establish model or production readiness.

## Verification and demonstration

Demonstrate feature outcomes and acceptance negatives. Use meaningful domain checks for calculations/state, integration checks for access/jobs/storage and browser checks for changed journeys where applicable. Discovery produces dated interview, baseline and decision records; evaluation produces scorecards with denominators; application work produces traces/screenshots and test results. Preserve failures alongside successes.

AI evidence names checkpoint, prompt, parser, corpus split, host and contract versions. Do not commit unapproved invoices. Missing buyer/model/environment evidence leaves the relevant acceptance pending; historical platform test counts cannot substitute for invoice results.

## Exit and handoff

Accept only with linked evidence and named reviewer. Update [status](../../../_STATUS.md), coverage and dependency records. Open blockers cannot be waived by downstream completion.
