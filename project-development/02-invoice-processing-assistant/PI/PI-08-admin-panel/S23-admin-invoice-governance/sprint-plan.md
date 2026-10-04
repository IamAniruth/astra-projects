# IP S23: Admin invoice and export governance

PI-08 | Module M23 | Status: Planned | Conditional administration scope  
Source: [Admin specification](../../../docs/09-admin-panel-specification.md)

## Objective and features

As an authorized invoice reviewer, I can use admin invoice and export governance with explicit client boundaries, source evidence and accountable actions.

- IP-S23-F01: Intake, validation profiles and duplicate/PO exception administration
- IP-S23-F02: Separation-of-duties approval, immutable revisions and mapped export history

## Dependencies and entry criteria

S22 permissions/audit; S04-S06 intake/parsing/jobs, S07-S09 extraction/validation/duplicate/PO services and S10-S12 review/approval/export contracts. S14 supplies qualification for active profiles. Confirm critical fields, resolution authority, duplicate rules, cumulative allocation/reversal and rounding/export policies.

Assign named product/domain, React, Next.js/data, Astra integration and QA/operations owners. Confirm data permissions, contract versions and capacity. Fixtures may unblock UI development but cannot prove real-model/provider/host readiness. PI-07 is not required.

## Tasks and ownership

| Task | Deliverable |
|---|---|
| IP-S23-T01 | Product/domain: approve critical fields, profile applicability, exception resolution rules, duplicate evidence and PO allocation/reversal examples. |
| IP-S23-T02 | React/Next.js: build intake failures, profile versions, duplicate comparisons, PO/exception views and resolution actions with client scope, source evidence and reasoned dispositions. |
| IP-S23-T03 | Backend/data: reuse atomic approval/allocation services, separation of duties, immutable revisions and versioned CSV/JSON exports; retain hashes, raw values, declared/computed totals and provenance. |
| IP-S23-T04 | QA/domain: test false duplicates, missing POs, concurrent partial allocations, ambiguous dates/currencies, OCR failure, post-approval edits and export round-trip/formula safety. |

Reuse the existing domain APIs and records in [data/API contracts](../../../docs/04-data-and-api.md), extending them through the admin specification. Validate client/workspace scope server-side for every nested lookup. Use typed validation, permission, conflict and reconciliation errors with safe correlation IDs. Privileged actions require appropriate confirmation, authorization, idempotency/concurrency and audit, not just hidden buttons.

## Acceptance

- [ ] IP-S23-AC1: Unsupported inputs and uncertain fields remain explicit; profile changes cannot rewrite approved records and missing data is not defaulted to zero.
- [ ] IP-S23-AC2: Duplicate suggestions cannot auto-merge/delete/suppress; PO checks enforce compatible units/currency and transactional cumulative allocations without double counting repeated/revised approvals.
- [ ] IP-S23-AC3: Critical unresolved fields block approval, reviewer policy is enforced server-side and stale edits fail; edits append an unapproved revision instead of mutating approval.
- [ ] IP-S23-AC4: Exports bind exact approved revisions/mapping/hash, preserve leading zeros and decimal/date values, sanitize spreadsheet formulas and remain client-private; no posting, payment or bank-master update occurs.

## Verification and demonstration

Review a poor-scan invoice, distinguish a false duplicate, resolve a missing-PO exception under policy, then race two partial-invoice approvals against one PO. Approve an eligible revision, export CSV/JSON, edit it and demonstrate that the old approval does not transfer.

Use domain checks for arithmetic/state, integration checks for permissions/storage/jobs/allocations and browser checks for changed journeys. Include direct API negatives and races, not only happy-path clicks.

Retain a feature/task checklist, contract/migration record, redacted traces/screenshots, actual results including failures, and named reviewer decision. Record application, policy, mapping and applicable model/prompt/parser/corpus/host versions. No unapproved invoices or secrets belong in evidence. Mocks and provider sandbox results remain labelled and cannot imply live readiness.

## Exit and handoff

Review against the complete [admin checklist](../../../docs/09-admin-panel-specification.md) and [quality requirements](../../../docs/06-quality-security-operations.md). Carry incomplete prerequisites and failed checks explicitly. Required controls precede S17 paid-pilot acceptance and feed S18 release.

Update [status](../../../_STATUS.md), [coverage](../../../docs/03-module-feature-sprint-matrix.md) and [decisions](../../../docs/08-decisions-and-references.md) only from actual evidence. No ledger posting, payment initiation, supplier-bank update or automatic training is enabled by this sprint plan.
