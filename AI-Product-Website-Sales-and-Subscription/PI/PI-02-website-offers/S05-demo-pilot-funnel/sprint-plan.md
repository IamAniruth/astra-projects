# WS S05: Demonstration and paid-pilot enquiry

**Status:** Planned  
**PI:** [PI-02 Sales website and versioned offers](../README.md)  
**Module:** M05  
**Cadence assumption:** two weeks; named owners and estimate required  
**Sources:** [Sales/subscription summary](../../../AI-Product-Website-Sales-and-Subscription-Summary.md), [admin specification](../../../AI-Product-Admin-Panel-Specification.md)

## Objective and user story

As a customer or authorized service owner, I can rely on demonstration and paid-pilot enquiry with explicit scope, correct access and traceable outcomes.

- WS-S05-F01: Permitted sample demo and pilot request workflow
- WS-S05-F02: Lead/funnel measurement and assisted-sales handoff

## Dependencies and entry criteria

S04 content, S01 pilot terms and permitted samples; real product evidence if claiming measured results.
Confirm permitted examples, actual contract versions, business policy, acceptance owner and capacity. The selected product's domain logic remains product-owned. No price/provider/model/host choice is implied by this sprint.

## Implementation backlog

| Task ID | Workstream / suggested owner | Deliverable |
|---|---|---|
| WS-S05-T01 | Product/domain/commercial | Finalize the two feature scopes, success examples, exclusions and policy decisions; record unresolved gates. |
| WS-S05-T02 | Frontend/product design | Demo/sample journey, pilot-scope request and confirmation. |
| WS-S05-T03 | Backend/data | Idempotent lead capture with owner/status, retention and privacy-conscious funnel events. |
| WS-S05-T04 | Integration/operations | Create an internal onboarding handoff; no unsolicited campaigns or automatic purchases. |
| WS-S05-T05 | Contracts/security | Version changed records/contracts, identify the authoritative effect owner, enforce permission/retention boundaries and retain safe audit/evidence references. |
| WS-S05-T06 | QA/reviewer | Run acceptance cases below, including applicable denied/stale/repeated/concurrent requests; capture actual failures and approve or carry incomplete scope. |

For discovery/architecture tasks, deliver reviewed decisions, threat/data-flow models and contract examples rather than pretending there is running software. For implemented mutations, use server authorization, validation, idempotency/concurrency and attributable audit; hiding a button is insufficient.

## Acceptance criteria

- [ ] WS-S05-AC1: Demo labels synthetic, recorded or live behavior accurately.
- [ ] WS-S05-AC2: Repeated submission does not create duplicate leads and private samples stay protected.
- [ ] WS-S05-AC3: Funnel metrics have definitions/denominators and cannot imply invented customer outcomes.
- [ ] WS-S05-AC4: Relevant tenant/role boundaries and loading/empty/error/conflict behavior pass; planning-only or non-applicable checks are explicitly identified.
- [ ] WS-S05-AC5: Evidence identifies actual source/contract/configuration and, where applicable, application/provider/product/model/host versions; mocks and sandbox results remain labelled.
- [ ] WS-S05-AC6: A named reviewer accepts both features against recorded evidence; unresolved prerequisites or failed checks remain blocked/carried, not silently complete.

## Test and evidence plan

Use meaningful domain checks for money/access/state, integration checks for auth/provider/jobs/storage and browser checks for changed journeys. Discovery produces dated buyer/eligibility/decision records; infrastructure work requires actual target-host and recovery evidence. Apply [quality gates](../../../docs/03-quality-and-release-gates.md).

Retain feature/task checklist, changed contract/migration record, redacted traces/screenshots, test outcomes including failures, demonstration notes and reviewer decision. Do not store secrets or unapproved customer files. Live eligibility, real product quality and deployment cannot be inferred from fixtures, sandbox charges or historical platform tests.

## Sprint review demonstration

Submit a pilot request twice and show one traceable internal follow-up record.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md) from actual evidence. Confirm the next sprint can consume the authoritative contracts without a duplicate service. Final paid-pilot/release acceptance remains S18 with all applicable gates closed.

This plan performs no deployment, payment, outbound message or purchase. Such actions belong to later explicitly authorized implementation and must follow the agreed scope.
