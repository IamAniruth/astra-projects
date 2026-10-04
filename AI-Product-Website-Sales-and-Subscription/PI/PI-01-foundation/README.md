# PI-01: Commercial scope and secure foundation

Status: Planned | Project WS | Modules M01-M03  
Sources: [sales/subscription summary](../../AI-Product-Website-Sales-and-Subscription-Summary.md) and [admin specification](../../AI-Product-Admin-Panel-Specification.md)

## Outcome and sprints

Establish one validated offer, authoritative service boundaries and customer/operator security.

| Sprint | Outcome | Status |
|---|---|---|
| [S01](S01-scope-provider-gates/sprint-plan.md) | Offer, buyer and market discovery | Planned |
| [S02](S02-architecture-contracts/sprint-plan.md) | Architecture and shared-service ownership | Planned |
| [S03](S03-identity-admin-access/sprint-plan.md) | Identity, workspaces and privileged access | Planned |

## Dependencies and ownership

Start from both source specifications; S01 resolves business/eligibility gates before S02/S03 contracts and access.
Reuse any existing chosen-product services under S02 ownership decisions rather than creating competing authorities.

Assign named product/commercial, frontend, backend/data, integration, QA/security and operations owners. Three nominal two-week sprints are a sizing convention; re-estimate capacity and carry incomplete work explicitly.

## Exit and handoff

Accept each sprint only with actual artifacts, versioned evidence and reviewer decision. Include denied access, failure/retry/concurrency and user-visible error behavior relevant to its surfaces. Provider sandbox, fixture UI and upstream model claims do not replace real qualification.

Exit with agreed offer/market questions, service ownership and demonstrated tenant/operator boundaries.

Update [status](../../_STATUS.md) and [coverage](../../docs/01-module-feature-sprint-matrix.md) only from evidence. See [roadmap](../README.md) and [quality gates](../../docs/03-quality-and-release-gates.md).
