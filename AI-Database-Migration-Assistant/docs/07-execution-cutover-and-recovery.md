# DM execution, cutover and recovery

## Durable lifecycle

draft -> discovered -> mapping_review -> plan_ready -> rehearsing -> rehearsal_passed -> authorized -> snapshotting -> loading -> validating -> ready_for_cutover -> cutting_over -> verifying_application -> completed.

Side states: paused, blocked, failed, outcome_unknown, recovery_required, cancelled and rolled_back. Store transition version and actor. Cancellation is a request until the worker reaches a safe boundary; committed batches remain recorded. A cancelled run is not automatically a clean target.

## Preconditions

Validate exact source and target identity, authorization, scope, schema/policy fingerprints, snapshot consistency, disk allowance and restore evidence. The first release requires an empty run-owned destination. Confirm that no second worker owns the run using an expiring lease and fencing token checked at every target commit. Credentials and network boundaries prevent writes to unrelated databases.

## Batch protocol

1. Read an ordered key range from the pinned snapshot; bind cursor and input digest to the run and plan.
2. Transform with the immutable compiled plan; collect typed errors without logging sensitive values.
3. Begin target transaction; verify fencing token and unique (run, step, batch) receipt.
4. Apply target records and lineage/ID mappings; persist checksums, row dispositions and commit receipt in that transaction.
5. Commit. Update control-plane progress from the committed receipt.
6. On lost acknowledgement, query the target receipt. If present and matching, advance; if absent, replay; if inconsistent, stop for investigation.

Use stable keyset cursors, including composite keys. Tables without stable unique keys require an immutable extracted file with record offsets/hashes or a separately qualified strategy. OFFSET against a changing source is not a resume protocol. Scope filters are immutable. External side effects are excluded from this transaction guarantee.

## Snapshot survival and source changes

The write-freeze baseline keeps old application writes and scheduled jobs fenced through final validation and switch. A rehearsal can use an earlier backup, but production must rerun validations on its own final snapshot. If a snapshot expires or source writers bypass the freeze, stop; either rebuild staging from a new snapshot or apply a separately qualified delta process. Never resume an old cursor against a fresh changing source and call it consistent.

## Bounded repair

Transient network/lock errors can retry with configured limits and backoff. Semantic errors return to mapping. Model repair happens only against disposable targets, with a proposed maximum of three candidate attempts and a time/token budget set in S01. A changed mapping invalidates the compiled plan and relevant evidence. The agent cannot loosen checks, drop failed rows, widen scope or edit production directly to make tests pass.

## First-release cutover runbook

1. Confirm accepted rehearsal, verified restore, authorized window and on-call owner.
2. Enter maintenance mode; fence old app, workers, scheduled jobs and integrations. Verify no bypass writers.
3. Capture final source snapshot and identity; run the approved load and complete validation on it.
4. Keep the new application read-only/maintenance-fenced. Check grants, indexes, constraints, sequences and attachment manifests.
5. Persist switch intent and apply versioned connection/routing configuration. Reconcile actual configuration if acknowledgement is lost.
6. Run agreed read-only smoke checks against the new application and migrated data.
7. If accepted, explicitly enable new writes and record this irreversible boundary for the baseline recovery procedure.
8. Monitor agreed invariants and errors. Retain old source read-only for the agreed period; no automatic deletion.

## Recovery boundaries

Before switching: discard only identified run-owned staging if authorized, restore/rebuild staging and keep old application authoritative. After switching but before new writes: restore the old routing/configuration and verify the old app, because the source has remained unchanged.

After new writes begin, switching back to an old backup would lose new records. The first release must enter recovery_required, fence both sides and preserve target changes. Choose a reviewed forward repair or reconcile those new writes before a return. Automatic lossless post-write rollback requires a separately qualified reverse-change capture/reconciliation design and is not promised here.

Database restore and transformation inverse are different operations. Many transforms are lossy and have no inverse. Record RPO/RTO targets per customer and measure them in rehearsal; do not advertise zero loss or a recovery duration before evidence.

## Whole-system recovery and application readiness

The recovery plan also protects control metadata, immutable plans, ID maps, receipts, evidence and routing state; see [operational lifecycle](18-operational-lifecycle-and-product-acceptance.md). Restore with workers disabled and reconcile actual target state before resume. Cutover requires [application readiness](17-application-readiness-and-data-boundaries.md), including required files, authentication, background jobs and an explicit application adapter or assisted procedure. Database completion alone is insufficient.

## Later CDC implementation track

Qualify snapshot/log handoff, ordered transaction application, delete handling, durable offsets, schema changes, log-retention gaps, source failover and final lag drain. Transformations must handle dependent updates across entities. Native replication cannot be assumed to implement arbitrary new-schema business mappings. Release this separately from the maintenance-window product.
