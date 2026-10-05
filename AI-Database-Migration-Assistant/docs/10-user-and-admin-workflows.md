# DM customer and operator workflows

## Accepted end-to-end UI requirement

The finished product uses React/TypeScript through Next.js for all supported customer and operator workflows. Next.js application APIs authenticate and authorize requests; Python migration workers perform durable database work; local Astra supplies AI assistance. Ordinary migration operation must not require a terminal. Initial network/credential provisioning and unsupported emergency repairs may still require an administrator, and the UI must describe that boundary honestly.

| Step | UI action and outcome | Primary backend owner | Delivery |
|---|---|---|---|
| 1 | Create project and define customer/scope | Next.js + authoritative identity/project service | S01-S03, S16 |
| 2 | Register source/target connections and test access | Next.js admission; Python connectors | S03-S05, S16 |
| 3 | Select allowed code references, schema inputs and business rules | Python discovery/evidence service | S05-S06, S16 |
| 4 | Run discovery and inspect compatibility/data issues | Python discovery/profiling | S04-S06, S16 |
| 5 | Request mappings, inspect evidence and answer ambiguity questions | Local Astra + Python mapping registry | S07-S08, S10-S12, S16 |
| 6 | Start a disposable rehearsal | Python durable runner | S09, S13, S16 |
| 7 | Review validation, resolve issues and rerun affected checks | Python validators; Astra explains/proposes only | S12-S14, S16 |
| 8 | Select execution window and authorize exact plan | Next.js authorized request; Python policy/state checks | S12-S15, S16 |
| 9 | Run migration, monitor, request pause/cancel and resume | Python worker and target commit receipts | S13, S16 |
| 10 | Perform cutover and inspect new-application checks | Python cutover controller and application adapter | S14-S16 |
| 11 | Follow supported recovery actions and see unresolved limits | Python recovery controller; operator where needed | S15-S17 |
| 12 | Download reports, accept handover and reuse a qualified recipe | Python evidence/recipe service; Next.js authorized delivery | S12, S16-S18 |

Scheduling records a timezone, UTC execution instant, window and authorization expiry. At execution time, the worker rechecks scope and permission; missed windows require a visible decision rather than an unexpected late cutover. Source-code selection is limited to configured allowlisted roots or reviewed uploads, not arbitrary server filesystem access.

UI acceptance must include: browser close/reopen mid-job, Next.js restart, reconnect to actual durable progress, repeated submission, stale mapping edit, denied tenant/report access, revoked authorization, failed validation, missing evidence, a worker crash and post-write recovery_required. Normal workflows need no shell commands; the UI must not label a suggested mapping or copied dataset as a completed migration.

## Screens and user outcomes

| Screen | Primary outcome | Required states |
|---|---|---|
| Project intake | Describe old/new application and permitted scope | Missing inputs, unsupported profile, access denied |
| Connections | Register secret references and verify identity/access | Reachable, insufficient privileges, unavailable, revoked |
| Discovery | See object inventory, volume, compatibility and risks | Queued, partial, completed, failed; partial never shown as complete |
| Mapping workspace | Review entity/field rules and evidence; answer questions | Suggested, resolved, unsupported, stale, accepted |
| Rehearsal | Run against a copy and see useful reconciliation | Progress, paused, errors, pass, failed validation |
| Execution readiness | Understand window, recovery and authorized scope | Ready, waiting on named prerequisite, expired |
| Live run | See committed batches and data disposition | Requested pause versus paused; unknown outcome clearly shown |
| Cutover | Confirm actual application routing/write state | Switching, read-only checks, writes enabled, recovery required |
| Reports and recipes | Export evidence and reuse compatible mapping | Qualified version, incompatible inputs, retired recipe |

Use plain domain language: '12 orders reference missing customers' is more useful than an internal exception class. Preserve detailed redacted diagnostics for operators. Distinguish rows read, transformed, committed, excluded and quarantined; do not report 100% complete when only copying finished.

## Customer journey

Create project -> connect or supply approved snapshots -> inspect assessment -> resolve business questions -> accept mapping scope -> review rehearsal -> authorize the defined execution/window -> monitor migration -> accept application workflows -> receive handover. Existing authorization covers automatic batch/retry actions within its scope.

For a repeat customer recipe, preflight can skip mapping review when every compatibility and policy check passes. It still runs validation and honors the authorized execution boundary. Explain why a changed schema or new enum value needs attention rather than silently falling back to guesses.

## Admin and support

Operators see run health, worker leases, storage pressure, connector failures, model availability and recovery state. Support access is scoped and audited; a public commercial administrator does not gain customer database access. Recovery actions query actual execution state before retrying. No button bypasses mapping/version/authorization checks.

Exports contain schemas/rules, masked diagnostics and aggregate reconciliation by default. Raw row-level evidence is a separately authorized export. Show retention and deletion status truthfully, including backups awaiting expiry.

## Application acceptance examples

Detailed [application readiness](17-application-readiness-and-data-boundaries.md) and [UI/operating acceptance](18-operational-lifecycle-and-product-acceptance.md) add scope/loss review, attachment/authentication dispositions, full-system recovery, recipe/model lifecycle, large-table usability and report-export checks. Expose these as readiness/blocker panels within existing screens. A manual application adapter or infrastructure prerequisite remains visible as assisted work, not simulated automation.

Find an existing customer; view historical orders and invoices; verify totals and tax rules; enforce tenant visibility; preserve archived/deleted semantics; create a new customer/order without ID collision; run a report over historical dates. Password portability requires a compatible authentication contract or a planned reset flow; no model can reconstruct plaintext passwords from hashes.
