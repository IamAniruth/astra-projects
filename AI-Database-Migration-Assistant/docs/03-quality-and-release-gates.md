# DM quality and release gates

All gates below are proposed acceptance requirements, not achieved results. Freeze numerical targets before evaluation; changing them requires a recorded new evaluation version.

| Gate | Required evidence | Failure behavior |
|---|---|---|
| G01 Scope and authority | Engine/version/objects/tenants identified; permitted access; clear source and target ownership | No execution |
| G02 Complete mapping | Every in-scope source field and required target field has a rule or explicit accepted disposition; zero unresolved critical semantics | Return to mapping |
| G03 Plan integrity | Pinned fingerprints, compiled-rule allowlist, collision checks, code/policy hashes, restricted privileges | Reject stale/unsupported plan |
| G04 Rehearsal | Full scoped copy on isolated storage, no unexplained record loss, all transformation checks pass | No production run |
| G05 Data reconciliation | Full disposition accounting; exact domain totals and relationship checks; independent transformed-value verification | Hold cutover |
| G06 Application acceptance | Customer workflows and tenant access tests on target application commit | Hold cutover |
| G07 Recovery | Restored backup verified; interrupted-run reconciliation demonstrated; post-cutover recovery limits accepted | Hold cutover |
| G08 Operational fit | Measured disk/RAM/throughput, source load and maintenance-window fit on representative host and volume | Resize/replan |
| G09 Model recipe qualification | Frozen unseen tasks and negative cases pass; mapping family/version recorded | Use human-reviewed mappings |
| G10 Cutover | Valid execution authority, source-write fence, no schema drift, final checks, target writers still fenced | Abort before switch or enter recovery_required |
| G11 Release | All mandatory gates accepted with evidence and known limitations | Pilot remains unreleased |

## Reconciliation beyond row counts

For each source entity record, persist a stable source identity and one terminal disposition: migrated, intentionally excluded or quarantined. The three sets must be disjoint and cover the complete authorized scope. Merges and splits use lineage links; output row counts need not equal input row counts. Quarantined critical records block release. Intentional exclusions require recorded reasons and must not break relationships.

Check all foreign keys, uniqueness, nullability, value ranges, currency/decimal precision, totals by tenant/currency/date/status, temporal conversions and target sequence allocation. Use canonical typed serialization to compare expected transformed rows with target rows; specify timezone, decimal scale, Unicode policy and null representation. Plain raw-source versus raw-target hashes are invalid when representations change.

Independent validation must not merely rerun the same transformation code. Use human-authored expected fixtures, separately written queries, source/target application workflows and reviewed business equations. A model-generated validator alone cannot certify its own generated migration.

## Failure-injection requirements

Kill a worker before commit, after commit before acknowledgement and during checkpoint persistence. Revoke credentials; fill storage; break connectivity; submit concurrent runs; insert schema drift; expire source snapshots; invalidate authorization; introduce duplicate natural keys and cross-tenant references. Confirm explicit status, no duplicate effects and correct resumption or deliberate restart.

Recovery tests must kill processes, not only raise catchable exceptions. Test a cutover-controller crash between each persisted phase. Evidence records the actual engine versions, volumes, runtime, model/checkpoint hash and failures, not only a passed count.

## Additional gate evidence from the planning review

G01/G02 include full authorized dependency closure and explicit loss/exclusion decisions. G06 requires application readiness for essential files, authentication, roles and derived state, not just rows loaded. G07 includes isolated restoration of control metadata, receipts, ID maps and routing state with workers disabled. G08 includes source-load limits, fair resource budgets and missed-window behavior. G09 includes model/recipe revocation and correction-data boundaries. G10 requires a qualified application fence/routing adapter or an explicitly assisted procedure. G11 includes install/upgrade compatibility, end-to-end UI usability and post-migration observation/handover.

Use the [gap register](19-gap-review-and-acceptance-register.md) for exact sprint and evidence ownership. Additional scope requires re-estimation; no existing gate is marked passed by this update.

## Acceptance owners and responsibility

Database engineer: integrity and connector correctness. Customer domain owner: semantics and intentional exclusions. Application owner: target workflows. Operations owner: capacity and recovery. Release owner: final scope and evidence. Names remain unassigned; assign in S01. Model speed improvements and platform test totals cannot substitute for these gates.
