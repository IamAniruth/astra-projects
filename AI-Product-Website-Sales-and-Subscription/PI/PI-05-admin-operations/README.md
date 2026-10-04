# PI-05: Owner administration and support

Status: Planned | Project WS | Modules M13-M15  
Sources: [sales/subscription summary](../../AI-Product-Website-Sales-and-Subscription-Summary.md) and [admin specification](../../AI-Product-Admin-Panel-Specification.md)

## Outcome and sprints

Give authorized operators customer, billing, job and service controls with attributable effects.

| Sprint | Outcome | Status |
|---|---|---|
| [S13](S13-admin-customers-onboarding/sprint-plan.md) | Admin overview, customers and support | Planned |
| [S14](S14-admin-billing-markets/sprint-plan.md) | Admin billing, offers and market controls | Planned |
| [S15](S15-admin-jobs-health/sprint-plan.md) | Admin processing recovery and service monitoring | Planned |

## Dependencies and ownership

Consume the accepted prior PI contracts and the specific dependencies named in each sprint; missing prerequisites stay explicit.
Reuse any existing chosen-product services under S02 ownership decisions rather than creating competing authorities.

Assign named product/commercial, frontend, backend/data, integration, QA/security and operations owners. Three nominal two-week sprints are a sizing convention; re-estimate capacity and carry incomplete work explicitly.

## Exit and handoff

Accept each sprint only with actual artifacts, versioned evidence and reviewer decision. Include denied access, failure/retry/concurrency and user-visible error behavior relevant to its surfaces. Provider sandbox, fixture UI and upstream model claims do not replace real qualification.

Exit with authorized support/billing/recovery actions, expiring overrides and timestamped health without secret/content leakage.

Update [status](../../_STATUS.md) and [coverage](../../docs/01-module-feature-sprint-matrix.md) only from evidence. See [roadmap](../README.md) and [quality gates](../../docs/03-quality-and-release-gates.md).
