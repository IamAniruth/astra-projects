# DM gap review and acceptance register

**PI delivery status:** Required source for the assigned PI/sprint scope. See [documents 16-19 delivery matrix](../PI/documents-16-19-delivery.md) for task IDs, acceptance criteria and evidence ownership. Requirements remain Planned until implemented and accepted; explicitly optional/deferred items retain that status.

Reviewed: 5 October 2026. Purpose: close planning omissions without claiming implementation or broadening the advertised database support.

## Findings and required evidence

| ID | Gap in initial planning | Added requirement | Delivery owner/sprints | Acceptance evidence |
|---|---|---|---|---|
| GAP-01 | Filters lacked explicit dependency-scope closure | Resolve related/shared records without unauthorized scope expansion | Domain/database; S01/S06/S07 | Tenant-only and date-filter fixtures with missing and cross-tenant dependencies |
| GAP-02 | Lossy conversion and cleanup decisions were scattered | Classify conversion loss and require an explicit accepted disposition | Domain/compiler; S07/S08/S14 | Rounding, truncation, merge and invalid-value cases cannot silently pass |
| GAP-03 | Attachments/login/integrations were mentioned but not tied to app readiness | Add per-object disposition and independent readiness evidence | Application; S05/S14/S15/S18 | Required files, user access and side-effect controls pass or block scope |
| GAP-04 | Generic cutover lacked an application adapter contract | Declare supported fence/routing/check methods and assisted fallback | Application/operations; S05/S15 | Background writer and lost routing-acknowledgement fixtures |
| GAP-05 | Restore focus was on target database | Restore metadata, receipts, ID maps and routing evidence with workers disabled | Operations; S13/S15/S17 | Full-system isolated restore and mismatch detection |
| GAP-06 | Runtime/metadata upgrades lacked explicit compatibility evidence | Pin readers/writers and refuse incompatible job resume | Backend/operations; S02/S13/S17 | Upgrade and rollback on copied metadata with pending jobs |
| GAP-07 | Qualified recipes/models lacked retirement/defect response | Lifecycle/revocation and affected-run lineage review | Model/backend; S11/S12/S13 | Revoke a defective release and safely block/pause impacted work |
| GAP-08 | Source impact and per-project fairness were implicit | Bounded queries, quotas, backpressure, window checks and safe resource pause | Database/operations; S04/S13/S17 | Competing jobs, full disk, slow source and missed-window scenarios |
| GAP-09 | End-to-end UI lacked explicit usability/large-scale/export checks | Add accessibility, pagination, edit conflict and untrusted export acceptance | UI/QA; S16/S17 | Full keyboard journey, large inventory, concurrent edit and export fixtures |
| GAP-10 | Model correction feedback could be mistaken for automatic training | Separate reviewed correction, incident and permitted training flows | Model/privacy; S10-S12 | Unconsented customer correction stays outside training corpus |
| GAP-11 | Installation/local-only claim lacked package/recovery procedure | Preflight and pinned artifact/provenance inventory | Platform; S02/S17 | Reproducible install and offline/runtime boundary evidence on target host |
| GAP-12 | Pilot exit lacked delayed-effect observation and decommission boundaries | Observe jobs/invariants, transfer ownership, keep source cleanup separate | Release/application; S18 | Dated observation/handover with named owners and retained-source policy |

All findings are **specified, not implemented**. Requirements attach to the existing eighteen sprints; they do not count as accepted features or a promise of the original nominal duration. Re-estimate affected sprints before implementation; split them if capacity warrants. No additional agent work, source-data access or deployment is implied.

## New detailed references

- [Application readiness and data boundaries](17-application-readiness-and-data-boundaries.md)
- [Operational lifecycle and product acceptance](18-operational-lifecycle-and-product-acceptance.md)
- [Compatibility/readiness evidence template](../templates/compatibility-and-readiness.md)

## Deferred scope remains deferred

CDC/low downtime, populated-target merges, new engines, generic attachment transfer, password conversion, automatic whole-codebase rewriting and lossless post-write rollback still require separate implementation/qualification. This review adds checks that expose those dependencies; it does not claim to implement them.

No finite documentation review establishes that nothing else is missing. S01 must still review actual source/target applications, data rights, business semantics and operating requirements; new discovered gaps enter this register with affected gates, owner and evidence.
