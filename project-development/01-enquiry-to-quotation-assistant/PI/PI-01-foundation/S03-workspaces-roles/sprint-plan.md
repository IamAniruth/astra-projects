# EQ S03: Workspaces, roles and business settings

**Status:** Planned  
**PI:** [PI-01 Product foundation and Astra boundary](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M01 M02 M03 M17 M19 M22  
**Astra references:** A01 A08 A11 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Establish company isolation and regional business context across product and Astra boundaries.

## User story and features

As an owner, I can invite staff and configure my business while other companies remain inaccessible.

- EQ-S03-F01: Workspace onboarding, invitations and role permissions
- EQ-S03-F02: Explicit business/locale settings and Astra tenant mapping

## Dependencies and entry criteria

S02; selected first-market configuration may remain pilot-only.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S03-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S03-T02 | React frontend | Workspace creation/switching, members and role editor, flexible address fields, locale/time-zone settings. |
| EQ-S03-T03 | Next.js/backend | Scoped repositories and composite constraints; single-use invitations; owner/admin/sales/approver/viewer checks; audited revocation. |
| EQ-S03-T04 | Astra integration | Bind authenticated product principals to Astra scope; deny body-injected tenant/role claims; specify rechecks for jobs and retrieval. |
| EQ-S03-T05 | Data/contracts | Workspace, membership, invitations, market settings and integration identity mapping; seed overlapping SKUs in two companies. |
| EQ-S03-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S03-AC1: Cross-tenant reads/writes and forged object references fail.
- [ ] EQ-S03-AC2: Revoked staff cannot retrieve files or start jobs, including through worker/gateway adapters.
- [ ] EQ-S03-AC3: Interface language, business country and time zone are stored separately.
- [ ] EQ-S03-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S03-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S03-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Two isolated business sessions, invitation acceptance, role revocation and settings update.

## Exit and handoff

Two-company isolation suite and scoped credential contract pass; no public customer-data path bypasses checks.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

