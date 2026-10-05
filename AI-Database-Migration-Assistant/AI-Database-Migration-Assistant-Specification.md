# DM product specification

Status: Proposed; no implementation or measured product results.

## Customer problem and outcome

A customer has useful records in an old application, while a replacement application expects different tables, identifiers and rules. A database copy alone cannot reconcile split entities, changed status values, ownership, relationships or business calculations. The product discovers these differences, records explicit decisions, migrates consistently and proves that the replacement application uses the data correctly.

Primary users: implementation engineer, customer domain owner, database operator and release owner. The customer domain owner resolves business meaning; the operator controls infrastructure; the release owner accepts the final reconciliation. Small teams may combine roles, but the audit records the actual actor.

## Automation contract

| Mode | Permitted automation | Mandatory stopping conditions |
|---|---|---|
| Assessment | Read permitted schemas/code, profile allowed samples, suggest mappings | Unavailable evidence, forbidden objects or unidentified source ownership |
| Assisted migration | Compile reviewed mappings, rehearse, validate, prepare execution | Unresolved field/relationship, drift, unexpected loss or failed validation |
| Qualified recipe | Execute a previously accepted mapping automatically within a pre-authorized scope | Schema/version/policy mismatch, changed critical distributions, revoked credentials or failed gates |
| New-project autonomous candidate | Propose and test a new mapping in disposable environments | Ambiguity, unsupported transformation, exhausted retry budget; production requires an execution authorization |

Automation permission is a scoped record, not a new confirmation dialog for every batch. Authorization binds source, destination, tenant, mapping, supported connector versions, execution window, destructive-action limits and evidence requirements. A material change invalidates it. Model self-confidence cannot grant permission.

## Inputs and outputs

Inputs: source and target schemas; selected repository commits; relevant ORM models and migrations; business-rule descriptions; allowed sample/profiling policy; database version and collation; snapshot identity; target-application version; maintenance window; data ownership; retention and recovery requirements.

Outputs: compatibility report; object inventory; mapping with evidence and unresolved questions; immutable executable plan; rehearsal report; row disposition and lineage; execution journal; reconciliation report; application acceptance results; cutover/recovery record; downloadable handover pack.

No raw production database is required in the model context. Read schemas and relevant code in bounded chunks; provide only authorized, minimized samples. The database runner streams the real records directly.

## Functional requirements

1. Register source/target profiles with secret references and test scoped access.
2. Inventory tables, views, keys, types, constraints, indexes, triggers, routines, sequences, generated columns, encodings and relevant application dependencies.
3. Profile nulls, uniqueness, ranges, relationship coverage and tenant boundaries without treating sampled statistics as full-data proof.
4. Retrieve source and target code evidence; suggest field/entity/status/relationship mappings and identify conflicts.
5. Review mappings with side-by-side schema and provenance; resolve questions and record intentional exclusions.
6. Compile a bounded transformation language into validated, parameterized execution steps. Custom code requires separate qualification.
7. Run a consistent snapshot into disposable target storage; manage keys, ordering, batching, retries and resumable checkpoints.
8. Verify row disposition, values, relationships, domain totals, authorization and target-application behavior.
9. Prepare and execute a fenced cutover inside the permitted window, with a rehearsed recovery procedure.
10. Export evidence; reuse recipes only when their exact compatibility checks pass.

## Nonfunctional requirements

Owner-confirmed stack: React/TypeScript UI through Next.js; Next.js application-facing backend; durable Python migration services/workers; local Astra inference. Every supported step from intake through cutover, recovery, reporting and recipe reuse must be operable through the UI. A closed browser or restarted application API must not terminate an accepted migration. See [screen-to-workflow coverage](docs/10-user-and-admin-workflows.md).

All processing can run on customer-controlled machines, with no external inference or telemetry by default. Enforce tenant isolation and separate model, discovery, runner and cutover privileges. Preserve auditability across crashes. Pause safely on resource exhaustion. Define capacity limits from measurements and customer requirements rather than promising unlimited rows or zero downtime.

## First-release exclusions

No arbitrary engine/version support; no unattended interpretation of undocumented business semantics; no automatic rewriting of the whole new application; no source deletion; no merge into a populated production target; no live dual-write migration; no automatic migration of database users, vendor licences, payment tokens or password algorithms. External files need a separate manifest and transfer validation. Unsupported objects block affected scope until resolved.

## Definition of useful delivery

Additional acceptance is detailed in [application readiness](docs/17-application-readiness-and-data-boundaries.md), [operational lifecycle](docs/18-operational-lifecycle-and-product-acceptance.md) and the [gap register](docs/19-gap-review-and-acceptance-register.md). These clarify dependencies and operating behavior without adding generic attachment transfer, password conversion, new engines or post-write reverse replication to first-release scope.

A pilot counts as successful only when all in-scope source records have an explained disposition, target invariants pass, the customer's new application completes agreed workflows, a real restore rehearsal succeeds, and a named owner accepts the evidence. A generated SQL script, running chat endpoint or green framework test suite is insufficient.
