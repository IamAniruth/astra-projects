# EQ S04: Customers and catalogue lifecycle

**Status:** Planned  
**PI:** [PI-02 Trusted business data and enquiry intake](../README.md)  
**Cadence assumption:** two weeks; team estimate and named owners to be assigned  
**Release scope:** Initial product  
**Modules:** M04 M05 M19  
**Astra references:** A05 in [capability register](../../../docs/11-astra-llm-feature-mapping.md)

## Sprint objective

Make trusted customer and product data available before AI proposes matches.

## User story and features

As a salesperson, I can import and search my company's catalogue and associate enquiries with real customers.

- EQ-S04-F01: Customer/contact CRUD and archive behavior
- EQ-S04-F02: CSV mapping, preview, validation and idempotent catalogue import

## Dependencies and entry criteria

S03; catalogue sample and field mapping agreed.

Confirm sample data, contract versions, permission to use it, responsible reviewers and sprint capacity before starting. Open Astra capability gaps stay visible; mocks are labelled and cannot satisfy real-environment acceptance.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S04-T01 | Product/domain reviewer | Finalize the two feature scopes, examples, unsupported cases and business acceptance. |
| EQ-S04-T02 | React frontend | Customer pages, import wizard, row error report, product list/editor and search. |
| EQ-S04-T03 | Next.js/backend | Scoped customer/product endpoints; SKU uniqueness, import staging and atomic commit; version and checksum records. |
| EQ-S04-T04 | Astra integration | Define the source version/permission metadata later required by Astra retrieval; implement exact SKU/alias baseline without claiming semantic capability. |
| EQ-S04-T05 | Data/contracts | Customers, products, aliases, attributes and import batches; document archived-product behavior for historical quotes. |
| EQ-S04-T06 | QA/operations | Execute the acceptance cases below, capture failures and verify relevant recovery/access behavior. |

Tasks describe work to implement later. Python runtime extensions, when necessary, remain in Astra's ownership and must be tracked explicitly; this document does not imply existing gateway endpoints for every library feature.

## Acceptance criteria

- [ ] EQ-S04-AC1: Repeated import commit does not duplicate products.
- [ ] EQ-S04-AC2: Malformed rows report location/reason and cannot partially corrupt the chosen import transaction.
- [ ] EQ-S04-AC3: Another company's same SKU is not a candidate in search.
- [ ] EQ-S04-AC4: Relevant role/tenant boundaries and invalid/empty/loading/error behavior are exercised for the changed surface.
- [ ] EQ-S04-AC5: Evidence names the actual application commit, contract/config versions and, where applicable, Astra checkpoint/prompt/data/environment. Unsupported cases remain labelled.
- [ ] EQ-S04-AC6: The reviewer accepts the demonstration and records any incomplete feature as blocked or carried over.

## Test and evidence plan

Use meaningful domain tests for calculations/state, integration tests for storage/auth/jobs, and browser tests for the user journey as applicable. Real Astra adapter and quality tests are separate from deterministic mock application tests.

Expected artifacts: feature/task checklist, changed contract or migration record, acceptance results (including negatives), representative screenshots or API traces, demonstration notes, and an updated dependency/risk record. Never store credentials or unapproved customer documents in evidence.

For an AI-dependent acceptance criterion, a missing checkpoint, false-quality gate, unavailable provider/host or unsupported interface leaves that criterion pending/blocked. Do not replace it with a fabricated result.

## Sprint review demonstration

Import mixed-validity data, fix rows, commit once and find a product for a customer.

## Exit and handoff

Catalogue/customer source of truth is stable enough for prices and matching.

Update [product status](../../../_STATUS.md), [feature coverage](../../../docs/12-module-feature-sprint-matrix.md), and the [Astra dependency register](../../../docs/11-astra-llm-feature-mapping.md) with actual evidence. Apply the shared [definition of done](../../../docs/07-quality-security-international.md); all unchecked work remains incomplete.

