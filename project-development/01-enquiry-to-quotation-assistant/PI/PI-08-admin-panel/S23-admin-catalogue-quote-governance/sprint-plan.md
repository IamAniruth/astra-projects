# EQ S23: Admin catalogue and quotation governance

**Status:** Planned  
**PI:** [PI-08 Administration](../README.md)  
**Cadence assumption:** two weeks; estimate and named owners required  
**Modules:** M04 M05 M06 M12 M13 M14 M18 M19  
**Source:** [Admin panel specification](../../../docs/13-admin-panel-specification.md)

## Sprint objective and user story

As an authorized catalogue administrator or quote approver, I can use admin catalogue and quotation governance while preserving customer isolation, authoritative business data and accountable actions.

- EQ-S23-F01: Catalogue and effective-price administration with conflict review
- EQ-S23-F02: Quote policy, exact-revision approval and artifact provenance administration

## Dependencies and entry criteria

S22 admin permissions; S04/S05 customer/catalogue/price contracts, S06 file provenance, S09 reviewed matching, S10 deterministic calculations and S11/S12 revision approval/export. Confirm price override, repricing, archive and expiry policies.

Confirm permitted examples, contract/config versions, individual owners and realistic capacity. Fixtures may enable UI work but cannot satisfy actual provider, model or target-host acceptance. PI-07 is not required.

## Implementation backlog

| Task ID | Workstream / suggested owner | Work to deliver |
|---|---|---|
| EQ-S23-T01 | Product/domain reviewer | Agree import conflict examples, permitted overrides, effective price rules and handling of changed/withdrawn products and expired quotes. |
| EQ-S23-T02 | React frontend | Build import preview/conflict detail, catalogue/price history, unit/currency diagnostics, revision comparison and artifact history. |
| EQ-S23-T03 | Next.js/backend | Reuse idempotent import and effective-price services; validate intervals, overrides and units; retain immutable approved snapshots and transactional approvals. |
| EQ-S23-T04 | Astra integration | Expose extraction/matching provenance without turning retrieval scores into confidence or model suggestions into accepted prices/substitutions. |
| EQ-S23-T05 | Data/contracts | Preserve source rows, price/rule snapshots, decimal totals, revision hashes, approval actor and artifact checksum; version settings and edits. |
| EQ-S23-T06 | QA/operations | Test overlapping SKUs across tenants, duplicate imports, price overlaps, unit/currency errors, concurrent edits, repricing and private PDF/CSV export. |

Reuse existing domain APIs under /api/v1 and the proposed additions in the admin specification. Enforce identity and scope on the server; never trust a client workspace or approval flag. Return typed conflicts/validation/access errors with correlation IDs and no sensitive payloads. Privileged mutations need confirmation, reason where applicable, idempotency and audit.

## Acceptance criteria

- [ ] EQ-S23-AC1: Repeated import commits do not duplicate records; conflicting rows and overlapping effective prices cannot silently overwrite authoritative data.
- [ ] EQ-S23-AC2: Cross-workspace products/prices are rejected; model text never supplies authoritative prices, tax, totals or automatic product selection.
- [ ] EQ-S23-AC3: Price changes leave approved quote snapshots untouched; repricing or editing produces unapproved content with a visible comparison.
- [ ] EQ-S23-AC4: Sales-only/platform-support users cannot approve quotes; stale edits/approvals fail and approval binds to exact content under policy.
- [ ] EQ-S23-AC5: Exported PDF/CSV matches approved totals/revision and uses private access; expired/superseded artifacts stay labelled historical rather than being repriced.
- [ ] EQ-S23-AC6: Review evidence covers decimal rounding, unit validation, price override audit and provenance; no inventory reservation, goods payment or unconfirmed sending is introduced.

## Test and evidence plan

Use domain tests for state/calculation invariants, integration tests for actual auth/storage/jobs/billing, and browser tests for changed operator journeys. Include negative direct-API requests and concurrent/stale requests rather than testing only button visibility.

Retain the feature/task checklist, contract/migration changes, redacted API traces or screenshots, results including failures, and reviewer decision. Record actual commit, configuration and relevant model/prompt/data/host versions. Store no credentials or unapproved customer documents in evidence. Sandbox/mocked results must be labelled and cannot establish live readiness.

## Sprint review demonstration

Import a catalogue and prices, resolve a bad unit, review an enquiry match, submit and approve a quote, then change the price list. Export the original snapshot unchanged and demonstrate that an explicitly repriced revision needs new approval.

## Exit and handoff

Accept only with linked evidence and named reviewers. Carry incomplete dependencies explicitly; documentation alone leaves this sprint Planned. Required controls precede S17 paid-pilot acceptance; S18 incorporates final administration readiness.

Update [status](../../../_STATUS.md), [feature matrix](../../../docs/12-module-feature-sprint-matrix.md) and [decisions](../../../docs/09-decisions-and-risks.md). Apply the [quality definition of done](../../../docs/07-quality-security-international.md). No automatic outbound messaging or collection of payments for quoted goods is added.
