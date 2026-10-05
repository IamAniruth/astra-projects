# DM security and data lifecycle

Local deployment keeps processing under local control only if every dependency follows that boundary. Disable external model fallback, hosted embeddings and content telemetry by default. Record any permitted package-download/update path separately from runtime data egress.

## Trust boundaries

Source data, repository text, database comments and model output are untrusted. Credentials, authorization records and allowed execution capabilities are trusted control inputs. Never combine them in a prompt and treat the resulting answer as authority. Validate tool requests server-side; secrets are resolved inside the worker and never passed to the model.

Separate read-only discovery, staging-write and cutover principals. Restrict destination identity and schema at both application and database levels. Use OS/process/container boundaries suitable for the deployment; a disposable directory alone does not isolate filesystem or network access. Do not execute customer scripts during repository analysis. Custom transform code runs in a qualified sandbox without arbitrary egress.

## Sensitive records

Minimize samples, mask according to field policy and keep reversible mapping keys separately protected. Use synthetic examples where possible. Logs contain source record references and error categories, not values; access to row-level diagnostics is separately controlled. Encrypt stored snapshots/evidence and transport between hosts; keys and backup access require explicit ownership and rotation.

No training on customer data by default. A migration execution permission is not permission to train a model, retain examples or share data externally. If training permission is later granted, track licence, provenance, retention and applicable removal obligations independently.

## Retention inventory

Set per-customer retention for source extracts, staging databases, ID maps, error rows, journals, audit metadata, final reports and backups. Record purpose and owner for each class. Delete only owned artifacts after a retention decision and verified recovery needs; never recursively delete a source path supplied by a model. Deletion may remain pending while immutable backups expire; report that limitation.

## Tenant isolation and abuse cases

Bind every project/run/object to authenticated tenancy. Validate user-supplied project IDs against membership, enforce access in workers and exports, and prevent joining the same source key across tenants. Test revoked access mid-run, support-role misuse, forged evidence, path traversal in exports, injection in identifiers/comments and SSRF through connection configuration.

Customer-specific legal, contractual and residency requirements must be obtained during intake. This plan claims no regulatory certification. Data minimization and permission controls are product behavior, not substitutes for that assessment.
