# Deployment and operations

## Environments

Development uses fictional data and local infrastructure. Staging uses separate credentials, storage, database, queue, and payment sandbox. Production has a distinct domain/origin, credentials, billing configuration, backups, and reviewed access.

Do not connect a staging worker to production jobs or the production model's customer data path accidentally. Tag jobs and resources by environment and workspace.

## Initial production recommendation

Host React static assets behind HTTPS; route /api to a long-lived Next.js Node service. Retain Astra as a separate private Python runtime and reuse its versioned authenticated gateway. Product workers and Redis are optional for product-owned jobs, not replacements for Astra's job authority. Use PostgreSQL for business records and private file storage. Inspect the Astra release checklist before selecting the actual deployment; a product database is not evidence that Astra's optional PostgreSQL retrieval adapter is adopted.

The reference records Astra Compose Sprint 188 as stopped and removed, vLLM as not adopted, and local-cpu/local-cuda capacity qualification on a development host with remaining production gates. Do not reverse those decisions in setup instructions. S16-S18 qualifies the locked environment, actual served model, target host, TLS, process supervision, audit durability and recovery. No production capacity is inherited from tiny-model benchmarks.

A single properly operated deployment may serve the initial market. Multi-region replication, Kubernetes, and microservice decomposition are deferred until measured needs justify them. Do not use serverless request lifetimes as the sole execution environment for long AI/PDF/OCR jobs.

## Deployment sequence

1. Build immutable API, worker, and frontend artifacts from the same reviewed commit and lockfile.
2. Run unit/integration checks and the critical end-to-end staging workflow.
3. Verify environment variables without printing secrets; confirm auth origin and webhook URLs.
4. Back up relevant data and apply reviewed, backward-compatible migrations using a dedicated migration process.
5. Deploy API and frontend; deploy compatible worker; run live/readiness checks.
6. Execute a fictional-data smoke quote, verify private export access, and inspect queue/job health.
7. Enable selected workspaces/markets through feature flags and monitor failure/latency metrics.
8. Record release version, schema version, model/prompt version, configuration version, and operator.

## Recovery

Use backward-compatible schema changes so application rollback does not require blindly reversing a data migration. Document forward-fix and restore choices for destructive changes. Stop job claiming before a worker maintenance event; let active jobs finish or resume through checkpoints. Reconcile the durable job/outbox table after queue loss.

Restore PostgreSQL and file storage together to a consistent recoverable point. Proposed pilot objectives: recovery point no more than 24 hours and recovery time no more than 4 hours; validate the backup schedule and restore drill, then agree actual customer commitments. These are targets, not an SLA already achieved.

## Monitoring

Observe API errors, job backlog/oldest age, running-job leases, worker/model availability, memory, validation failures, usage ledger discrepancies, webhook failures, backups, storage capacity, and support tickets. Use correlation IDs across API/job/model/export without logging source documents by default.

Alert an identified owner and define response hours. Provide customer-facing status and retry guidance for outages. Track model and prompt changes independently of application changes.

## Commercial operations

Reconcile provider subscription state, local entitlements, and usage periodically. Handle cancellation dates and grace periods consistently. Failed/duplicated jobs follow the published charging rule. Owner/admin overrides require a reason and audit record.

Enforce published data export, deletion, and retention policies through scheduled jobs. Retention includes source documents, extracted text, AI records, indexes, and exports; backups follow documented expiry. Support access is scoped, time-limited where feasible, and audited.

## Launch evidence

S18 records actual deployment links, release checklist, test results, model benchmark, market availability, pricing/allowances, on-call/support contacts, restore evidence, and known limits. No production purchase, domain registration, paid service provisioning, or deployment has been performed by this planning task.

