# PI-08: Company knowledge administration

Prepared: 4 October 2026  
Status: Planned | Modules M22-M24 | Sprints S22-S24  
Source: [Admin specification](../../docs/09-admin-panel-specification.md)  
Structure reference: [Support Reply PI-08](../../../05-support-reply-assistant/PI/PI-08-admin-panel/README.md)

## Objective and sprints

Deliver scoped workspace/group administration, published-policy lifecycle, private knowledge-gap reporting and service operations.

| Sprint | Outcome | Status |
|---|---|---|
| [S22](S22-admin-identity-access/sprint-plan.md) | Admin identity, groups and access | Planned |
| [S23](S23-admin-publication-private-gaps/sprint-plan.md) | Admin publication and private knowledge gaps | Planned |
| [S24](S24-admin-commercial-operations/sprint-plan.md) | Admin commerce and operational readiness | Planned |

## Dependencies and scheduling

S01 discovery and S02 feasibility remain gates. S22 uses S03/S13; S23 uses S04-S12 with S14 qualification; S24 uses S06/S13-S15. Earlier sprints retain domain-service ownership. This PI owns admin screens, authorized orchestration and integrated verification, not duplicate identity, publication, gap, job or usage authorities.

Numbering is not mandatory calendar order. PI-08 does not depend on optional PI-07 or a completed launch. Required controls precede the S17 paid pilot and feed S18 release. S16-S18 evidence can initially appear pending without circular entry dependencies.

Three nominal two-week sprints are sizing containers. Re-estimate existing-service overlap and staffing, especially S24. Split tasks or record carryovers rather than waive acceptance to fit a timebox.

## Coverage

| Specification sections | Owner/evidence |
|---|---|
| 1-4: scope, navigation, identity and onboarding | S22 permission/revocation and private-history evidence |
| 5-7: publication/applicability, withdrawal and private gaps | S23 source lifecycle, race and privacy-review evidence |
| 8-9: jobs, company billing and qualified scope | S24 remote reconciliation, ledger and qualification |
| 10: audit, data lifecycle and health | S22 access/audit foundation; S24 integrated recovery |
| 11: quality/improvement | S24 actual-evidence view; optional improvement remains S19-S21 |
| 12-14: APIs, acceptance and decisions | All three with named owners and versioned decisions |

## Exit and handoff

Execute the full admin checklist and permitted upload-review-publish-search-explain-submit-gap-withdraw journey. Include multi-turn permission changes, private gap analytics, effective dates, remote-job/usage recovery and withdrawal-aware restore.

Retain actual versions, failures, limits and named reviewer decisions. Unauthorized disclosure or critical unsupported policy assertions block applicable release until remediation/re-evaluation. Search-only qualification cannot satisfy synthesized-answer acceptance.

No automatic HR/finance decision, employee performance scoring, source-system action, connector, public answer link or training is added. See [roadmap](../README.md), [status](../../_STATUS.md), [coverage](../../docs/03-module-feature-sprint-matrix.md) and [quality requirements](../../docs/06-quality-security-operations.md). Documentation does not establish implementation.
