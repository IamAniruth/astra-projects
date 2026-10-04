# WS S13: Admin overview, customers and support

**Status:** Planned  
**PI:** [PI-05 Owner administration and support](../README.md)  
**Module:** M13  
**Cadence assumption:** two weeks; named owners and estimate required  
**Sources:** [Sales/subscription summary](../../../AI-Product-Website-Sales-and-Subscription-Summary.md), [admin specification](../../../AI-Product-Admin-Panel-Specification.md)

## Objective and user story

As a responsible service operator, I can rely on admin overview, customers and support with explicit scope, correct access and traceable outcomes.

- WS-S13-F01: Role-filtered dashboard and customer/workspace detail
- WS-S13-F02: Assigned onboarding, incidents/support and controlled processing suspension

## Dependencies and entry criteria

S03 admin/audit foundation; S10/S12 records; S08/S09 billing/usage read services.
Confirm permitted examples, actual contract versions, business policy, acceptance owner and capacity. The selected product's domain logic remains product-owned. No price/provider/model/host choice is implied by this sprint.

## Implementation backlog

| Task ID | Workstream / suggested owner | Deliverable |
|---|---|---|
| WS-S13-T01 | Product/domain/commercial | Finalize the two feature scopes, success examples, exclusions and policy decisions; record unresolved gates. |
| WS-S13-T02 | Frontend/product design | Searchable customer list and overview/member/onboarding/billing/usage/job/support tabs. |
| WS-S13-T03 | Backend/data | Scoped aggregates, reasoned suspend/restore, rate-limited invites and support assignment. |
| WS-S13-T04 | Integration/operations | Use product-safe metadata and existing entitlements; internal notes stay separate from customer replies. |
| WS-S13-T05 | Contracts/security | Version changed records/contracts, identify the authoritative effect owner, enforce permission/retention boundaries and retain safe audit/evidence references. |
| WS-S13-T06 | QA/reviewer | Run acceptance cases below, including applicable denied/stale/repeated/concurrent requests; capture actual failures and approve or carry incomplete scope. |

For discovery/architecture tasks, deliver reviewed decisions, threat/data-flow models and contract examples rather than pretending there is running software. For implemented mutations, use server authorization, validation, idempotency/concurrency and attributable audit; hiding a button is insufficient.

## Acceptance criteria

- [ ] WS-S13-AC1: Operations/support/billing/read-only roles see only permitted actions and data.
- [ ] WS-S13-AC2: Onboarding, subscription and processing states remain distinct under suspension.
- [ ] WS-S13-AC3: Dashboard shows refresh time and unknown data; revenue separates currencies/setup fees.
- [ ] WS-S13-AC4: Relevant tenant/role boundaries and loading/empty/error/conflict behavior pass; planning-only or non-applicable checks are explicitly identified.
- [ ] WS-S13-AC5: Evidence identifies actual source/contract/configuration and, where applicable, application/provider/product/model/host versions; mocks and sandbox results remain labelled.
- [ ] WS-S13-AC6: A named reviewer accepts both features against recorded evidence; unresolved prerequisites or failed checks remain blocked/carried, not silently complete.

## Test and evidence plan

Use meaningful domain checks for money/access/state, integration checks for auth/provider/jobs/storage and browser checks for changed journeys. Discovery produces dated buyer/eligibility/decision records; infrastructure work requires actual target-host and recovery evidence. Apply [quality gates](../../../docs/03-quality-and-release-gates.md).

Retain feature/task checklist, changed contract/migration record, redacted traces/screenshots, test outcomes including failures, demonstration notes and reviewer decision. Do not store secrets or unapproved customer files. Live eligibility, real product quality and deployment cannot be inferred from fixtures, sandbox charges or historical platform tests.

## Sprint review demonstration

Locate a blocked pilot, assign support and suspend processing without silently cancelling billing.

## Exit and handoff

Update [status](../../../_STATUS.md), [coverage](../../../docs/01-module-feature-sprint-matrix.md) and [decisions](../../../docs/04-decisions-and-dependencies.md) from actual evidence. Confirm the next sprint can consume the authoritative contracts without a duplicate service. Final paid-pilot/release acceptance remains S18 with all applicable gates closed.

This plan performs no deployment, payment, outbound message or purchase. Such actions belong to later explicitly authorized implementation and must follow the agreed scope.
