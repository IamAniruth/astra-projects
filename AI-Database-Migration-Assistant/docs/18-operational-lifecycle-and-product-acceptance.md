# DM operational lifecycle and product acceptance

**PI delivery status:** Required source for the assigned PI/sprint scope. See [documents 16-19 delivery matrix](../PI/documents-16-19-delivery.md) for task IDs, acceptance criteria and evidence ownership. Requirements remain Planned until implemented and accepted; explicitly optional/deferred items retain that status.

Added: 5 October 2026. Proposed operating requirements; no disaster-recovery run, package, UI or release is implemented by this document.

## 1. Install, preflight and offline operation

Provide a pinned release manifest for the Next.js application, Python migration service, local model/tokenizer, compiler/DSL, drivers and metadata schema. The installer/preflight checks runtime versions, required configuration, allowed filesystem/network boundaries, service health, time synchronization, free storage, model availability and source/target connection identity. An unavailable local model blocks new AI proposals; a pre-qualified stored recipe may run without inference if its explicit policy and all other checks permit it.

Document first-install bootstrap, secret provisioning, backup key custody, service restart and uninstallation boundaries. Avoid demonstration credentials. Offline installations need a verifiable package/model transfer process and dependency inventory; do not promise offline installation merely because inference is local. Artifact checksums prove byte identity, not origin; verify provenance through an authenticated distribution channel and record the authorized release source.

Normal migrations remain UI-operated. Infrastructure privileges, installation and unsupported emergency repair may require an administrator. The readiness screen must identify the actual unmet prerequisite and owner rather than claim 'connected' proves migration readiness.

## 2. Full-system backup and recovery

Protect the control metadata, immutable mapping/plan versions, source-snapshot references, target receipts, ID maps, validation evidence, application routing/write state, compatibility manifests and credential/key references needed for recovery. Model weights may be restored or reacquired from the pinned authorized artifact; never rely on a mutable model alias. Database backup alone is insufficient to resume a partially completed migration.

Record a recovery manifest with backup/checkpoint identifiers and a consistency boundary across components. Restore into an isolated environment first, with workers and scheduled cutovers disabled. Compare control-plane state with actual target receipts and routing/write state before enabling any work. Recovered pending jobs must not automatically reconnect to production or execute a missed cutover.

An older journal combined with a newer target may be reconciled from committed receipts; missing or conflicting evidence yields recovery_required, not a guessed cursor. If required source snapshots or ID maps cannot be recovered, resume is unsupported until an explicit rebuild/reconciliation plan is accepted. Test loss of metadata storage and evidence storage as well as target data, and measure customer-defined RPO/RTO for the whole system.

## 3. Compatibility and schema upgrades

Define a reader/writer compatibility matrix for application, worker, DSL/compiler, metadata schema, connector, model/tokenizer and evidence format. Pin active runs to compatible execution code. Drain or deliberately pause workers before upgrades; back up control state and test upgrade on a copy. Refuse incompatible resume clearly.

An application binary rollback does not automatically reverse a metadata migration. Record whether a metadata change is backward compatible and how to restore it; destructive migrations require a separately tested recovery plan. Validate pending job admission, receipts, mapping history, secret references and report access after upgrade. Never mix mappings or ID namespaces from different recipe versions inside one run.

## 4. Recipe and model lifecycle

Registry states: draft -> evaluated -> qualified -> retired; revoked is a separate exclusion state. Record exact compatibility scope, evidence, actor, reason and effective time. Promotion does not rewrite old plans. An accepted plan must record which model produced proposals, even if the runtime no longer needs that model.

When a critical defect is found, revoke new use of the affected recipe/model/compiler version, identify impacted runs through lineage and perform an impact assessment. Unstarted jobs are blocked. Active jobs reach a safe pause boundary; if the issue requires an immediate stop, use the operator stop procedure and reconcile unknown commits. Do not automatically roll back completed customer migrations or discard new target writes.

Revocation of a model for privacy/authorization reasons may prohibit its further use even on an old plan; a generated mapping is not automatically wrong merely because a newer model exists. The incident owner determines whether accepted mappings need revalidation from the specific defect and evidence. Never silently redirect an in-progress run to a different model or compiler.

Customer corrections enter a review queue, not automatic online training. Separate mapping corrections, product bugs and candidate training examples. Customer data needs its own training permission; reproduce failures with synthetic fixtures where possible. Re-run held-out evaluation and preserve old results when creating a new candidate.

## 5. Resource fairness, budgets and source load

Set per-project concurrent-run, discovery-query, model-token/time, extraction-rate, staging-storage and retry budgets. Pin the accepted limits in the run policy and report consumed/remaining budget. Large discovery queries have deadlines and cancellation; run source-load profiling against a permitted environment before production. Pause safely when disk, source load or execution-window thresholds are crossed.

Use bounded queues/backpressure so one project cannot exhaust worker memory or model capacity. Record operational quota separately from commercial billing. Queue position is not an execution-time guarantee. Estimated completion time shows its measurement basis and uncertainty; a maintenance window includes validation and application checks, not just copying rows.

Scheduled jobs recheck credentials, scope, release revocation, schema/policy drift and window before starting. In the UI display the named timezone and UTC instant, with explicit handling of ambiguous/nonexistent local times. Missed windows remain visible and do not trigger late cutover automatically.

## 6. User interface acceptance

| Area | Required behavior and evidence |
|---|---|
| Large schemas and histories | Server-side filtering/pagination; do not download all sensitive rows to render a table |
| Mapping review | Accessible keyboard navigation, labelled inputs, visible focus, understandable errors and searchable evidence |
| Progress and reconnect | Recover durable state after refresh/API restart; detect stale progress and distinguish pending from effective actions |
| Concurrent edits | Expected-version conflict with a readable diff; never silently overwrite another reviewer's mapping |
| Model failures | Show unavailable, truncated, unsupported and ambiguous results; never convert a failed proposal into a green success state |
| Long reports | Authorized asynchronous export, expiring access where appropriate, redaction and known data-format limits |
| CSV/spreadsheet export | Treat untrusted cell values as data in the selected format; test formula-like content with the chosen spreadsheet workflow |
| Dates and language | Preserve exact typed values; explicit display timezone; locale formatting must not change stored money/date semantics |
| Recovery screens | Explain current write authority, retained changes, supported next action and required operator involvement |

These are functional accessibility/usability requirements, not a certification claim. Initial UI language is an implementation decision; no unsupported localization or language-specific model capability is advertised.

## 7. Incidents, support and post-migration observation

Define incident severities for integrity/tenant exposure, unknown write authority, stalled jobs and noncritical UI failures. Name incident and customer-domain owners in the pilot. The stop control prevents new effects and exposes in-flight/unknown effects; it cannot undo committed transactions. Evidence is preserved with scoped access and retention, not collected as a raw customer database for support.

Use a redacted diagnostic bundle with release IDs, scope-safe counts, state transitions and error categories. Support tools cannot bypass authorization, execute arbitrary customer SQL or download secrets. No support bundle is transmitted externally without the user's/customer's applicable instruction.

After enabling target writes, observe agreed application errors, financial/relationship invariants and delayed background jobs for a customer-defined period. Define ownership transfer, documentation and outstanding issues explicitly. Completing a migration does not authorize deleting the old source or backups; any later decommission is a separate scope decision with retention/recovery checks.

## 8. Acceptance ownership

S02/S03: release boundaries, budgets and access. S10-S12: model/recipe registry and correction handling. S13: queue, stop, receipt reconciliation and controlled recovery. S15: cutover-state recovery. S16: usability/reconnect/export scenarios. S17: install, full-system restore, compatibility upgrades and host/resource tests. S18: incidents, observation and handover. Evidence must be recorded in the existing release pack; none of these requirements is satisfied by documentation alone.
