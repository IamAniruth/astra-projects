# Execution sequence and sprint ownership

## Evidence-driven sequence

1. Inventory checkpoint/tokenizer/architecture, host, runtime and source permissions. Leave unknown fields unresolved; do not manufacture a 7B configuration by changing dimensions.
2. Build the 2,000-example development corpus and independent review rubric using the [support-specific collection plan](12-dataset-types-reasoning-and-samples.md); reserve its 10,000 training, 2,000 validation, 3,000 release, 1,000 calibration and 2,000 challenge records separately. Register supported specialty/language, failure thresholds and inference budget.
3. Run case-only, oracle-evidence and end-to-end baselines. Classify failures as model, retrieval, missing facts, disclosure, context truncation or workflow.
4. Fix deterministic application/retrieval problems first. Train only for measured learnable behavior gaps; record SFT/LoRA experiments and costs.
5. Choose the best validated unquantized candidate. Qualify the exact serving path and device; then compare quantization variants without changing unrelated components.
6. Freeze a candidate and run untouched representative and targeted evaluation. Record exact denominators and confidence bounds; failed cases cannot remain hidden holdout after remediation.
7. Run access, stale-approval, restore/cancellation and actual target-host capacity checks. Keep drafts agent-reviewed.
8. Pilot with a narrow approved team; measure total handling time and factual corrections. Copy/export remains separate from delivery status.
9. Release only after all applicable gates and named reviewers pass. Preserve immutable prior artifacts; rollback cannot restore revoked sources or permissions.
10. Monitor post-release sampled quality and critical incidents. Requalify meaningful model/prompt/corpus/parser/runtime changes.

No automatic sending, refund, account change or help-desk write action is authorized by this guide.

## Planning links

| Work | Product sprint owner |
|---|---|
| Scope, skills, corpus rights, proposed thresholds | S01 |
| Actual parameter count, host/path inventory and model baseline | S02 |
| Identity, import/publication and source fidelity | S03-S06 |
| Summary/retrieval/draft development evidence | S07-S09 |
| Disclosure, exact-revision approval and reviewed handoff | S10-S12 |
| Entitlements, supported language and operational preparation | S13-S15 |
| Independent quality/statistical release evidence | S16 |
| Assisted pilot and release approval | S17-S18 |
| Optional feedback/training/improvement and integrations | S19-S21 |

See [project sprint status](../_STATUS.md). This guide does not mark any sprint Accepted. Initial capability tuning, if required for S02/S07-S09, is a gated feasibility task; the optional post-launch model-improvement program remains S19-S20.

## Required release record

Checkpoint/base/adapter/tokenizer hashes; actual parameter counts; architecture/context; precision per component and actual load path; dataset rights/hash/splits; training config and consumed tokens; prompt/schema/retrieval/corpus versions; host/driver/runtime; test counts/bounds and independent labels; p95 latency/memory/load; unresolved scope; reviewer decisions; rollback artifact and incident owner.

A current hardware purchase, fixed training budget or customer-ready quality claim cannot be made from this document alone.
