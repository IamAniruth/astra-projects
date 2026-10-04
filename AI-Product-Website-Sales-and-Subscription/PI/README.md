# WS roadmap and delivery rules

PI means Program Increment. WS identifiers are independent of product and Astra identifiers. All implementation is Planned.

| PI | Outcome | Sprints | Exit evidence |
|---|---|---|---|
| [PI-01](PI-01-foundation/README.md) | Commercial scope and secure foundation | S01-S03 | Named scope/service owners and enforced access |
| [PI-02](PI-02-website-offers/README.md) | Sales website and versioned offers | S04-S06 | Truthful website, pilot funnel and validated offers |
| [PI-03](PI-03-billing-usage/README.md) | Payments, subscriptions and usage | S07-S09 | Verified lifecycle and concurrent usage accounting |
| [PI-04](PI-04-customer-product/README.md) | Customer onboarding and product integration | S10-S12 | Actual entitled product journey and self-service |
| [PI-05](PI-05-admin-operations/README.md) | Owner administration and support | S13-S15 | Role-scoped operating controls and recovery actions |
| [PI-06](PI-06-qualification-launch/README.md) | Market qualification, recovery and launch | S16-S18 | Market, restore, pilot and release evidence |

## Dependencies and sequencing

PI-01 -> PI-02 -> PI-03 -> PI-04 -> PI-05 -> PI-06 is the baseline. Tasks can overlap after contracts stabilize; sprint plans name actual prerequisites. Market eligibility research starts S01, and final end-to-end market qualification is S16. Do not wait until S16 to discover the provider cannot onboard the seller.

Admin authentication/audit is S03, offer administration S06, and full operator workflows S13-S15. Required customer/admin/commercial/recovery gates must pass before the S18 paid pilot and public launch. A lead-only website can be published earlier with truthful scope, no unsupported checkout and its own authorized release review.

The chosen product's implementation and quality are external dependencies. S11 integrates it; S18 cannot substitute website or payment success for a useful reviewed result. S02 assigns one owner per shared service and maps reused product tasks/evidence to this backlog, avoiding duplicate subscriptions, quota stores or job execution.

Three nominal two-week sprints per PI imply 36 sequential weeks for 18 sprints, not a staffing-validated commitment. Size at kickoff; reuse existing services and split/carry work when needed.

## Readiness and definition of done

Before starting, confirm owners, contracts, permitted data, sample cases and realistic capacity. Before acceptance, retain actual versions, meaningful domain/integration/browser evidence, negative cases, failures and reviewer decision. Mock/sandbox results remain labelled and cannot establish live provider/model/host readiness.

Use [quality gates](../docs/03-quality-and-release-gates.md), [coverage](../docs/01-module-feature-sprint-matrix.md), [status](../_STATUS.md) and [templates](../templates/README.md). Documentation and a completed checklist template are not implementation evidence.
