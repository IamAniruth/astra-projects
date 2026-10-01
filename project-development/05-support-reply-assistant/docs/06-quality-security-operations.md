# Quality, privacy, security and operations

Definition of done: concrete artifact or implementation, meaningful domain/integration checks, failure/access evidence, actual versions, known limits and named reviewer. AI acceptance needs independent summary/draft review on the selected model and corpus. Mocks and historical platform tests cannot establish support quality.

Enforce tenant/team/case/source grants in imports, search, summaries, histories, drafts, artifacts, feedback and logs. Test two customers with similar names/order numbers, reassigned cases, revoked agents and permissions changed during generation. Agent access to source content does not automatically authorize external disclosure of that content.

Preserve public/private message metadata. Internal notes, private source links, credentials and another customer's data must not enter public exports. Implement scoped diagnostics and audited support access. Parse bounded untrusted inputs and test prompt injection containment. Imported attachments cannot trigger outbound actions.

New messages, policy changes and fact expiry invalidate draft approval. Use optimistic concurrency and current dependency checks at export. Manual handoff does not prove a reply was sent or resolved a case. A later sending integration would require separate authorization, recipient validation, approved-revision binding, idempotency and uncertain-delivery reconciliation; it is not part of this initial scope.

Retention/deletion covers original cases, attachments, derived summaries/drafts, embeddings/indexes, caches, exports and feedback, with documented backup and audit policy. Feedback processing does not imply training permission. Restores and rollbacks respect current deletions, withdrawals and membership grants.

Operational qualification: target-host capacity with actual case lengths/model, bounded queues, budget/cancellation handling, remote-job reconciliation, supervision, TLS, credential rotation, durable audit, restore drills and support ownership. Failure must preserve review state and not duplicate usage settlement.

Release requires accepted discovery/feasibility, supported import/source qualification, independent factuality/disclosure checks, approval/freshness tests, operational recovery, pilot results and applicable Astra dependencies. Languages, ticket connectors, attachments and live queries each require separate qualification.
