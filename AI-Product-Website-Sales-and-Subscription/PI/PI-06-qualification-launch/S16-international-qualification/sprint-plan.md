# WS S16: Supported-market and localization qualification

**Status:** Planned  
**PI:** [PI-06 Market qualification, recovery and launch](../README.md)  
**Module:** M16  
**Cadence assumption:** two weeks; named owners and estimate required  
**Sources:** [Sales/subscription summary](../../../AI-Product-Website-Sales-and-Subscription-Summary.md), [admin specification](../../../AI-Product-Admin-Panel-Specification.md)

## Objective and user story

As a responsible service operator, I can rely on supported-market and localization qualification with explicit scope, correct access and traceable outcomes.

- WS-S16-F01: Full purchase/support journey localization and market gate
- WS-S16-F02: Verified processing-location and product-language evidence

## Dependencies and entry criteria

S04-S15 integrated staging candidate; actual seller/provider/product evidence and named market reviewers.
Confirm permitted examples, actual contract versions, business policy, acceptance owner and capacity. The selected product's domain logic remains product-owned. No price/provider/model/host choice is implied by this sprint.

## Implementation backlog

| Task ID | Workstream / suggested owner | Deliverable |
|---|---|---|
| WS-S16-T01 | Product/domain/commercial | Finalize the two feature scopes, success examples, exclusions and policy decisions; record unresolved gates. |
| WS-S16-T02 | Frontend/product design | Locale/language/currency/time-zone layouts including required Unicode/RTL templates. |
| WS-S16-T03 | Backend/data | Market evidence matrix, qualified combinations and backend blocking for unsupported sales. |
| WS-S16-T04 | Integration/operations | Check full file/database/index/inference/log/backup path and actual regional product quality. |
| WS-S16-T05 | Contracts/security | Version changed records/contracts, identify the authoritative effect owner, enforce permission/retention boundaries and retain safe audit/evidence references. |
| WS-S16-T06 | QA/reviewer | Run acceptance cases below, including applicable denied/stale/repeated/concurrent requests; capture actual failures and approve or carry incomplete scope. |

For discovery/architecture tasks, deliver reviewed decisions, threat/data-flow models and contract examples rather than pretending there is running software. For implemented mutations, use server authorization, validation, idempotency/concurrency and attributable audit; hiding a button is insufficient.

## Acceptance criteria

- [ ] WS-S16-AC1: Billing and document currency remain independent; precision and time-zone/DST cases pass.
- [ ] WS-S16-AC2: Unsupported country/language/provider combinations cannot take unintended payments.
- [ ] WS-S16-AC3: Published location/support/quality claims match evidence; no universal compliance or worldwide-coverage claim.
- [ ] WS-S16-AC4: Relevant tenant/role boundaries and loading/empty/error/conflict behavior pass; planning-only or non-applicable checks are explicitly identified.
- [ ] WS-S16-AC5: Evidence identifies actual source/contract/configuration and, where applicable, application/provider/product/model/host versions; mocks and sandbox results remain labelled.
- [ ] WS-S16-AC6: A named reviewer accepts both features against recorded evidence; unresolved prerequisites or failed checks remain blocked/carried, not silently complete.

## Test and evidence plan

Use meaningful domain checks for money/access/state, integration checks for auth/provider/jobs/storage and browser checks for changed journeys. Discovery produces dated buyer/eligibility/decision records; infrastructure work requires actual target-host and recovery evidence. Apply [quality gates](../../../docs/03-quality-and-release-gates.md).

Retain feature/task checklist, changed contract/migration record, redacted traces/screenshots, test outcomes including failures, demonstration notes and reviewer decision. Do not store secrets or unapproved customer files. Live eligibility, real product quality and deployment cannot be inferred from fixtures, sandbox charges or historical platform tests.

## Sprint review demonstration

Run the complete first-market journey with a different UI language/document currency and reject an unsupported market.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md) from actual evidence. Confirm the next sprint can consume the authoritative contracts without a duplicate service. Final paid-pilot/release acceptance remains S18 with all applicable gates closed.

This plan performs no deployment, payment, outbound message or purchase. Such actions belong to later explicitly authorized implementation and must follow the agreed scope.
