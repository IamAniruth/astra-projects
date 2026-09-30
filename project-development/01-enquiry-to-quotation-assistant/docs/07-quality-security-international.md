# Quality, security, and internationalization

## Quality strategy

| Layer | Required evidence |
|---|---|
| Domain tests | Decimal totals, discounts, units, tax policy, currency precision, rounding, state transitions, and quote expiry |
| Database/API integration | Isolation with two workspaces, role changes, duplicate requests, imports, migration constraints, optimistic concurrency |
| Job integration | Outbox recovery, duplicated delivery, worker restart, cancellation, timeout, usage reservation release/consumption |
| UI | Accessible labels, keyboard navigation, validation messages, responsive layout, empty/loading/error states |
| End-to-end | Signup -> import -> enquiry -> review -> quote -> approval -> PDF; subscription and cancellation journey |
| AI evaluation | Versioned held-out dataset with language/type breakdown; see AI plan |
| Commercial | Provider sandbox tests and controlled live verification after authorized account setup |
| Operational | Backup restore, dependency failures, load tests, rollback and alert exercises |

Use real PostgreSQL and Redis in integration tests when behavior depends on them. Mock providers and the model for repeatable application tests, then separately test real adapters. Test meaningful behavior rather than matching implementation internals.

## Proposed performance targets

For the pilot, use an initial target of p95 under 500 ms for ordinary paginated CRUD APIs excluding uploads, exports, model processing, and external provider latency, at an agreed workload. Measure background job wait and runtime separately; set their published targets after S08/S17 hardware tests. Capacity assumptions must include number of active workspaces, concurrent jobs, file sizes, catalogue size, and prompt lengths.

Any target is provisional until measured on the chosen deployment. Do not sell an unlimited or real-time guarantee based on this plan.

## Access and data protection

Authenticate server-side and check workspace membership and action roles for every object lookup. Include equivalent checks in workers, downloads, support access, and audit views. React route guards only improve navigation; they are not security controls.

Use private storage, short-lived authorized downloads, safe content types, validated uploads, parser resource limits, rate limits, input/output escaping, CSRF protection appropriate to sessions, and secure production cookies. Never execute spreadsheet formulas from imports or render user HTML unsanitized. Export CSV cells safely against formula injection. Treat PDFs and customer text as untrusted input.

Secrets belong in server/worker configuration or a production secret store, never in VITE_ variables, browser bundles, screenshots, or logs. Audit approvals, price overrides, membership changes, exports, and billing overrides. Retain redacted diagnostics without collecting full documents by default.

## International design

Store locale, interface language, workspace country, billing country, document jurisdiction when applicable, named time zone, billing currency, and quote currency as separate fields. Choose a single currency per quotation. Introduce currency conversion only as a later explicit, source-dated feature.

Externalize UI strings from S01. Test Unicode and right-to-left layout before enabling those languages. Use structured numeric/date values and locale-aware formatting; ask for clarification on ambiguous dates/units. Keep public price display and actual charge currency consistent.

Tax and quotation templates are reviewed, versioned market configurations. Initial tax handling is an explicitly configured business rule, not automatic global tax compliance. Use effective dates and snapshot the rule used on a quote. Market availability is checked in signup, billing, and feature access.

Do not infer language or billing country solely from IP. Record where inference, files, indexes, logs, backups, and support access occur. A model on the founder's computer affects that data flow even when the website is hosted elsewhere.

## Release gates

- All critical tenant isolation, money, approval, usage, and billing tests pass.
- No unresolved release-blocking security or data-loss issues.
- A real restore and safe deployment rollback/recovery have been demonstrated.
- AI acceptance criteria and failure handling pass for every enabled language and input type.
- Provider eligibility, commercial model terms, published policies, model licenses, and market assumptions are verified.
- Customers can see usage, manage cancellation, obtain support, and follow export/deletion policies.
- Owner, product reviewer, and operational owner record launch approval and limitations.

## Definition of done for every sprint

Implemented acceptance criteria; reviewed changes; relevant tests pass; migrations/env changes documented; accessibility/error states covered where UI changed; telemetry avoids sensitive leakage; supported-market implications checked; demonstration evidence linked; open defects and deferred scope recorded. Documentation completion alone never marks implementation done.

