# EQ S13: Sales website and guided onboarding

**Status:** Planned  
**PI:** [PI-05 Website, subscriptions and supported markets](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M16 M18 M19  
**Astra references:** A09 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Explain and demonstrate the product honestly and guide a business to its first quotation.

## User story and features

As a prospective buyer, I can understand the offer and try a sample before requesting a pilot or plan.

- EQ-S13-F01: Product/demo/pricing/help/contact/policy pages
- EQ-S13-F02: Onboarding checklist, sample workspace and support request

## Dependencies and entry criteria

S12 supplies honest demo; final prices and market availability may still be draft.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S13-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S13-T02 | React frontend | Responsive public React pages, accessible navigation, sample-data demo and first-use checklist; verify rendered metadata/content. |
| EQ-S13-T03 | Next.js/backend | Supported offers endpoint, scoped onboarding progress and support-case creation; minimal intentional analytics. |
| EQ-S13-T04 | Astra integration | Describe only qualified features/languages; show human review and model availability limits without marketing unsupported autonomy. |
| EQ-S13-T05 | Data/contracts | Offer drafts, onboarding steps, synthetic demo fixtures and support records. |
| EQ-S13-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S13-AC1: Visitor can explain the product workflow from the page/demo.
- [ ] EQ-S13-AC2: Unsupported or unqualified features are absent from purchase promises.
- [ ] EQ-S13-AC3: Onboarding progresses to first completed sample quote and avoids exposing another customer.
- [ ] EQ-S13-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S13-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S13-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Public visitor to trial/pilot request to first sample quote and support contact.

## Exit and handoff

Reviewable sales experience ready for real billing integration.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

