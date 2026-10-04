# PI-04: Customer onboarding and product integration

Status: Planned | Project WS | Modules M10-M12  
Sources: [sales/subscription summary](../../AI-Product-Website-Sales-and-Subscription-Summary.md) and [admin specification](../../AI-Product-Admin-Panel-Specification.md)

## Outcome and sprints

Bring a paid customer through assisted setup to the selected product's reviewed output and ongoing self-service.

| Sprint | Outcome | Status |
|---|---|---|
| [S10](S10-assisted-onboarding/sprint-plan.md) | Customer workspace and assisted setup | Planned |
| [S11](S11-product-workflow-adapter/sprint-plan.md) | Entitled AI workflow and reviewed result integration | Planned |
| [S12](S12-customer-self-service/sprint-plan.md) | Customer billing, history and support lifecycle | Planned |

## Dependencies and ownership

Consume the accepted prior PI contracts and the specific dependencies named in each sprint; missing prerequisites stay explicit.
S11 requires the chosen product's actual workflow and quality evidence; an adapter mock cannot close this PI.

Assign named product/commercial, frontend, backend/data, integration, QA/security and operations owners. Three nominal two-week sprints are a sizing convention; re-estimate capacity and carry incomplete work explicitly.

## Exit and handoff

Accept each sprint only with actual artifacts, versioned evidence and reviewer decision. Include denied access, failure/retry/concurrency and user-visible error behavior relevant to its surfaces. Provider sandbox, fixture UI and upstream model claims do not replace real qualification.

Exit with actual product handoff, reviewed result, customer billing/history and honest data-request states.

Update [status](../../_STATUS.md) and [coverage](../../docs/01-module-feature-sprint-matrix.md) only from evidence. See [roadmap](../README.md) and [quality gates](../../docs/03-quality-and-release-gates.md).
