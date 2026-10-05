# DM application readiness and data boundaries

**PI delivery status:** Required source for the assigned PI/sprint scope. See [documents 16-19 delivery matrix](../PI/documents-16-19-delivery.md) for task IDs, acceptance criteria and evidence ownership. Requirements remain Planned until implemented and accepted; explicitly optional/deferred items retain that status.

Added: 5 October 2026, planning gap review. Status: requirements only; no new engine, asset-transfer adapter or authentication integration is qualified.

## 1. Scope closure before extraction

A filter such as 'tenant A' or 'orders from this year' is not sufficient by itself. The selected records may reference older customers, shared catalogues, tax definitions, users or attachments. Discovery must build the dependency graph and classify each referenced object: included within authorized scope, an existing target reference validated by an explicit rule, an intentional supported null/exclusion, or an unresolved blocker.

Never widen a customer or tenant scope automatically just to satisfy a foreign key. Show a dependency-scope proposal, its record/field impact and its authority requirements. A previously authorized complete scope needs no repeated confirmation; expansion beyond it requires a new scoped decision. Shared/global lookup records need explicit ownership and deduplication rules. Use the target application's own reference data only when its version and semantics are verified, not merely because the IDs match.

Scope manifest records entity filters, tenant ownership, dependency disposition, excluded historical data, source snapshot and expected inclusion counts. Filters must be deterministic and frozen in the plan. Evaluate referential closure on the full scoped snapshot, not a small sample. A cross-tenant reference is an issue to resolve, not permission to copy another tenant's data.

## 2. Explicit loss and correction policy

For every transformation, classify its effect as value-preserving, representation-changing, lossy or unsupported. Examples of lossy work include rounding beyond target precision, truncating text, dropping history, collapsing statuses, deduplicating people or merging records. The mapping must show the affected scope, proposed rule, rationale, and independent validation; no 'best effort' silent conversion.

The default is zero unapproved data loss. Approved exclusions remain visible in reconciliation and handover. Review loss by business significance, not only percentage: one omitted invoice may be critical. Store original values only where necessary and authorized; row-level provenance can use protected evidence references rather than duplicating sensitive content in logs.

Rules that repair invalid dates, rewrite email addresses or infer missing IDs are data-cleaning decisions, not implicit migration behavior. New required target fields must come from evidence, qualified application defaults or a domain decision. The model cannot invent business values. A new rule creates a new mapping/plan and invalidates affected evidence.

## 3. Objects outside relational rows

| Object class | First-release disposition | Readiness requirement |
|---|---|---|
| Uploaded documents, images and other external files | Inventory and validate references; transfer adapter is separate scope | Owner-selected verified transfer, maintained access to an unchanged permitted store, or accepted exclusion |
| Password hashes and authentication accounts | No generic conversion or plaintext recovery | Compatible import proven by the auth owner, or a tested account reset/re-enrolment plan |
| Roles, memberships and application permissions | Explicit mapping, never inferred from database usernames | Least-privilege app access tests, inactive users and tenant isolation |
| API keys, sessions, tokens and encrypted secrets | Exclude from generic export/import | Reissue/reconnect through the owning system; do not copy into model context |
| Search indexes, caches and derived projections | Rebuild from accepted authoritative data where supported | Rebuild completion and app checks before dependent features are marked ready |
| Scheduled jobs, webhooks and notification queues | Disabled during rehearsals/load | Explicit reconciliation and release sequence that prevents duplicate side effects |
| Audit/history/soft deletes | Preserve or explicitly exclude per business/retention decision | Historical reports and access behavior validated |
| Views, routines, triggers and application defaults | Inventory; qualified rebuild or new-app replacement | Behavioral checks rather than presumed portability |

An excluded asset-transfer implementation does not excuse reporting a complete application migration when essential files are missing. Block the affected application workflow or require the separately verified transfer evidence. No new automatic asset copy, password migration or integration call is introduced by this plan.

## 4. Attachment manifest contract

When attachments are in the accepted application scope, record the source record identity, tenant, opaque source locator/version, size, media type, content checksum algorithm/value, target reference, access policy, transfer/verification status and evidence reference. Credentials and signed download URLs stay outside ordinary reports. Resolve relationship IDs through the same accepted ID map.

Verify all required references, content integrity and authorized retrieval in the new application. Reject traversal paths and references outside authorized storage roots. A missing file, stale source version or wrong tenant permission blocks the affected scope. Do not claim database transactions cover an external object store: use a separate durable transfer receipt, reconcile independently and require readiness of both parts before cutover. Optional transfer adapters need their own retry/cleanup and malicious-file handling qualification.

## 5. Application adapter contract

Cutover requires application-specific actions with pinned versions: test connectivity, report/write-fence all writers, verify fence, read current routing/configuration, apply an expected-version routing change, check read-only workflows, enable target writes, rebuild derived state and report health. The adapter must expose unsupported operations rather than simulate success.

Record how to stop background workers and administrative write paths, not just the public UI. Avoid performing financial transactions or sending notifications as smoke tests; use isolated rehearsals and read-only final checks until the explicit target-write boundary. New-record tests run in rehearsal; any production write probe belongs to the post-write recovery policy.

Manual application cutover is an acceptable supported mode if the actual operator actions, observed state and evidence are recorded through the UI. Mark it assisted, not unattended. Full automation is qualified per application adapter, in addition to database pair and recipe.

## 6. Acceptance scenarios and delivery

S01/S06: filtered tenant export includes permitted dependencies and blocks cross-tenant expansion. S07/S08: lossy conversions and new defaults cannot compile without their recorded disposition. S05/S14: users can access permitted historical data and required files, with no unexpected privilege or missing-reference behavior. S15: background writers remain fenced and external notifications are not replayed. S18: handover distinguishes database completion, application readiness and any separately accepted exclusions.

Use the [compatibility and readiness template](../templates/compatibility-and-readiness.md). These requirements extend the existing [mapping contract](06-mapping-and-transformation-contract.md), [UI workflows](10-user-and-admin-workflows.md) and [release gates](03-quality-and-release-gates.md).
