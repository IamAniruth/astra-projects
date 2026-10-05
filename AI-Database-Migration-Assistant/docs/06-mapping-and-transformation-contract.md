# DM mapping and transformation contract

## Evidence-first proposals

Each suggested rule carries source objects, target objects, source/target code evidence, transformation ID, assumptions, affected rows and unresolved questions. Evidence includes repository commit, path and symbol or database catalog snapshot. A model confidence score is advisory only. Repository comments and row text can contain instructions; the agent treats them as untrusted evidence, never permission to execute tools.

Map entities before fields: an old customer may split into an organization, contact and billing account. Declare business keys, tenant scope, cardinality, merge/split relationships and load dependency graph. Detect cycles and use a qualified two-pass or deferrable-constraint method; do not globally disable constraints and call the result valid.

## Bounded transformation language

Initial allowlist: copy, rename, exact cast with range checks, literal default with evidence, explicit enum lookup, null policy, decimal rescale with declared rounding, timezone conversion with ambiguity policy, deterministic concatenation/splitting, foreign-key lookup and explicit exclusion. Joins require declared keys/cardinality. Fuzzy entity matching, arbitrary expressions, runtime eval and per-row LLM generation are out of the initial executable language.

Custom transformations are separately reviewed code modules with a pinned hash, deterministic behavior, resource limits, fixtures and an independent validator. The model cannot add a plugin to an execution environment on its own.

## Contract fields

Mapping version and schema version; workspace/project; source/target profile and fingerprints; repository commits; scope filters; entities and field rules; key strategy; dependencies; explicit exclusions; unsupported objects; unresolved questions; evidence; validation equations; compiler compatibility; author/reviewer records. Compiled plan adds snapshot reference, runtime constraints, credentials by reference and exact code hashes.

See [illustrative mapping JSON](../templates/mapping.example.json). It is deliberately unapproved and has a null status mapping requiring customer input. It is not an executable product artifact and no JSON Schema validator exists yet; S07 defines that contract.

## Keys and identity

Use (recipe version, source system, tenant, entity, original typed primary key) as the source identity. Never merge customers solely because emails match. Store source-to-target IDs with target writes in the same transaction. Composite keys use canonical typed tuples, not ambiguous string concatenation. Replayed batches must resolve to the same target identity.

For an empty target, generated IDs may be allocated and persisted transactionally or derived with an approved namespace strategy. Reset target sequences/identity allocation after loading where required, and test inserting a new application record. Existing-target merges require separate conflict policies and are deferred.

## Coverage and ambiguity

Source-field coverage alone is insufficient: every required target field needs an evidence-backed value or supported default. Enumerate every observed status code, not only sampled values. Record unsupported outliers discovered during full execution as blocked/quarantined; do not silently invent fallbacks.

Critical examples: status meanings, money units, tenant ownership, soft-delete meaning, timezone, password compatibility and historical tax treatment. Require explicit domain rules when code/docs disagree. Resolving one question creates a new mapping version and invalidates affected compiled plans and prior rehearsal results.

## Recipe reuse

Before compiling filtered migrations, prove authorized dependency closure and classify lossy transformations under [application/data boundaries](17-application-readiness-and-data-boundaries.md). Recipe/model lifecycle and revocation follow [operating requirements](18-operational-lifecycle-and-product-acceptance.md). New versions cannot mix ID maps or rules inside an active run.

A qualified recipe identifies engine versions, schema fingerprints, relevant application commits or verified compatibility range, transform/plugin hashes, invariant suite, critical data-domain checks and allowed configuration parameters. Reuse first runs preflight and full required domain checks. Schema equality does not prove identical business semantics; versioned business policies must also match. New unknown status values stop the affected run even if column types are unchanged.
