# Quality, security and operations

Definition of done: implementation, meaningful domain/integration checks, authorization/failure coverage, relevant user-journey evidence, limitations and named reviewer. AI acceptance additionally identifies model/prompt/parser/data versions and held-out results. Mocks or historical upstream test counts cannot establish product readiness.

Test client isolation in uploads, object URLs, jobs, search, approvals, exports and audit. Cover revoked access during processing. Apply retention/deletion to originals, OCR, fields, indexes and temporary files, with a documented backup policy. Restrict sensitive logs/support access. Training permission is separate from service processing.

Review displays original evidence and uncertainty accessibly. Audit corrections and exception decisions; reject stale revisions. Sanitize formula-leading spreadsheet text through a documented export mapping and verify round-trip values. Invoice content and links cannot execute actions.

Production qualification includes target-host capacity on the selected model, bounded queues, cancellation, uncertain-outcome recovery, restore drills, process supervision, TLS, credential rotation, durable audit, support ownership and rollback. Reconcile jobs and allowance settlement after restarts. Changes to model/host can require renewed qualification.

Release needs accepted discovery/feasibility, supported-input qualification, independent quality thresholds, validated export imports, security/recovery evidence, pilot outcomes and applicable Astra blockers closed. Regional fields, retention and calculation profiles need domain review when the initial market is chosen; no universal compliance claim follows from this documentation.
