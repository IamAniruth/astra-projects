# DM deployment, capacity and cost

## Deployment options

Selected application components are the Next.js server (React UI and application APIs), durable Python migration services/workers, and the local Astra inference endpoint. They have separate process lifecycles. The Next.js process may restart without losing accepted worker jobs; credentials and model endpoints stay server-side. Worker/metadata/evidence persistence and authenticated internal connectivity are required even on one host. Framework versions and packaging remain unpinned.

First option: customer-controlled single-host installation with control API/UI, local Astra endpoint, worker and restricted evidence storage; connect to source and isolated target over approved networks. For larger jobs, separate model and worker hosts while keeping both within the customer's permitted boundary. GPU availability affects model inference; database transfer throughput depends primarily on storage, CPU, network, target constraints and transformation cost.

Choose a supported Linux/WSL/native profile after checking Astra's actual dependencies. Prefer isolated rehearsal and staging environments over installing unqualified packages in the live database host. Pin driver/runtime/compiler/model versions in a release manifest. Verify installation without external runtime data access.

## Capacity worksheet

- Extracted bytes and target bytes; profile indexes and large-object expansion separately.
- Staging, source snapshot, target data/indexes, backup, temporary transforms, journals and reserve capacity. Avoid a universal '2x database size' rule.
- Batch size and maximum row size; memory is bounded by active batches and transforms, not the entire dataset.
- Model weights, precision, context/KV cache, concurrent requests and actual runtime overhead.
- Sustained source read, transform, target write and validation throughput; the slowest limits end-to-end rate.
- Snapshot/lock duration, source load, maintenance window, final application checks and recovery allowance.

Illustration only: 100 GB at a measured effective 20 MB/s requires about 5,000 seconds (83 minutes using decimal units) for one transfer stage. Profiling, index building, validation, application checks and recovery are additional. This is arithmetic, not a benchmark or customer estimate.

## Cost model

Per migration cost = discovery/review engineering + model compute + database/worker compute + storage/backup + transfer + rehearsal/recovery effort + support. Repeat-recipe cost should be measured separately from first-time mapping development. Track reviewer minutes, repair attempts and failed runs; GPU-hours alone understate cost.

No current hardware prices or purchase recommendation is made. The earlier conversation's budget does not authorize spending and does not establish a training budget for this product. Measure a pilot before allocating hardware. Smaller models can be useful for limited extraction even when they fail general mapping; decide from evaluation.

## Operational indicators

Committed rows/bytes per second, checkpoint age, rejected/quarantined rows, remaining disk, model queue/latency, source connection pressure, target lock time, retry count, unknown commit outcomes and authorization expiry. Alerts must point to an explicit operator action; avoid logging sensitive rows for troubleshooting.

## Upgrade and rollback

Pin the runner for active jobs; drain before changing compiler/DSL or connector versions. A new model may propose future mappings but cannot silently rewrite an accepted plan. Upgrade tests include reading old evidence/journals and explicitly refusing incompatible resume. Keep an installation rollback manifest; it is separate from customer-data recovery.
