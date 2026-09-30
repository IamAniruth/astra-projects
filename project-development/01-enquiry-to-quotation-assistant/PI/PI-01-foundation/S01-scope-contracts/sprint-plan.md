# EQ S01: Product scope and Astra contract baseline

**Status:** Planned  
**PI:** [PI-01 Product foundation and Astra boundary](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M01 M19 M20 M22  
**Astra references:** A01 A09 A12 A14 A15 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Agree the first quotation workflow and establish a truthful Astra integration baseline before committing feature scope.

## User story and features

As the product owner, I can trace every promised AI feature to an available contract, a required integration, or an explicit release gate.

- EQ-S01-F01: Workflow, personas, first-market hypothesis and permitted sample corpus
- EQ-S01-F02: Astra contract/capability inventory and architecture decisions

## Dependencies and entry criteria

None; source documents and buyer access are discovery inputs.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S01-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S01-T02 | React frontend | Specify the React screen map, navigation and low-fidelity enquiry-to-quote wireframes; identify required language/accessibility states. |
| EQ-S01-T03 | Next.js/backend | Document Next.js service boundaries, schemas and tenant identity propagation; inventory gateway manifest endpoints against intended extraction/retrieval operations. |
| EQ-S01-T04 | Astra integration | Read current Astra status and record checkpoint/profile identity and gaps; mark external providers disabled, stage streaming distinct from token streaming, and demo APIs private. |
| EQ-S01-T05 | Data/contracts | Specify synthetic two-company fixtures, permitted customer samples, source version/hash and a held-out split policy. |
| EQ-S01-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S01-AC1: Every planned AI feature has a source ID and responsible EQ sprint.
- [ ] EQ-S01-AC2: No capability is labelled customer-ready solely from an upstream done badge.
- [ ] EQ-S01-AC3: A stakeholder can walk through enquiry, ambiguity review, approval and export from the wireframes.
- [ ] EQ-S01-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S01-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S01-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Present the workflow, contract-gap register, model release blockers and updated estimates.

## Exit and handoff

Scope, architecture boundary and evaluation ownership agreed; unanswered customer/model facts explicitly recorded.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

