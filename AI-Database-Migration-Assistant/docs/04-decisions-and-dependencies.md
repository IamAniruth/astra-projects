# DM decisions, assumptions and dependencies

Status: Planning baseline as of 5 October 2026. The user requested detailed product planning and intends to improve the local Astra model. No hardware purchase or production migration was requested.

| ID | Decision or assumption | State / next owner action |
|---|---|---|
| D01 | Keep inference local; no cloud model fallback by default | User direction; test the complete data path |
| D02 | Astra's own model is the intended assistant | User direction; capability must be measured, not presumed |
| D03 | Start with MySQL 8.4/InnoDB to PostgreSQL 16, empty target, maintenance window | Proposed baseline; replace with first customer's actual pair in S01 |
| D04 | First deterministic runner accepts human-reviewed mappings | Proposed sequencing; unblocks product development from model training |
| D05 | No production permission from model confidence | Product invariant; authorization is externally supplied and scope-bound |
| D06 | Automatic repeat runs use qualified recipe compatibility checks | Proposed product behavior; no repeated approval if existing authority still applies |
| D07 | Live CDC and populated-target merges are later separate qualifications | Deferred; downtime requirement may change priority |
| D08 | React/TypeScript through Next.js UI; Next.js application APIs; Python migration services/workers; local Astra inference | Accepted by owner, 5 October 2026. Framework/runtime versions, queue, drivers and deployment topology remain open in S02 |
| D09 | Source volume, data sensitivity, legal basis and retention | Customer-specific; open in S01/S03 |
| D10 | Recovery time, tolerable loss, execution window and capacity | Customer-specific acceptance targets; rehearse before cutover |
| D11 | Training examples may use customer material | Not permitted by default; requires separate explicit permission and licence review |
| D12 | Prices, paid pilot terms and WS integration | Unselected; costs must be measured before quoting |
| D13 | Model size, tokenizer, training data, GPU and budget | Open; preserve Astra platform ownership and its data/promotion gates |
| D14 | Attachments, passwords, stored procedures and external integrations | Inventory first; individual migration policies required |
| D15 | End-to-end UI for every supported migration workflow, including recovery and recipe reuse | Accepted by owner, 5 October 2026; infrastructure setup and unsupported emergency recovery may need an administrator |
| D16 | Training mix, size ladder and candidate hyperparameters in guide 16 | Proposed experiments, not a proven recipe or authorization to download data, train or buy hardware |

## Dependency order

S01 scope -> S02 contracts -> S03 access -> S04/S05 inventory -> S06 evidence and profiling -> S07/S08 mapping/compiler -> S09 deterministic rehearsal. Model S10/S11 depends on this independently verifiable harness; S12 adds qualified automation. S13/S14 harden execution and validation, S15 qualifies cutover, S16 provides complete operating workflows, S17 qualifies recovery/capacity and S18 accepts a pilot.

Some implementation streams can overlap after contracts are accepted; no staffing or parallel-agent execution is assumed. Astra training remains a dependency owned by the Astra project, with DM acceptance evidence required here. Do not mark Astra roadmap sprints complete because this plan exists.

## Open customer intake

Old/new engines and exact versions; tables and stored routines; source and target repository locations; business entity examples; database size and largest table; tenant model; write traffic; acceptable downtime; attachments; target pre-existing data; hosting/network access; backup/restore facilities; domain reviewer and release owner.

These are inputs to implementation, not reasons to leave this planning package unfinished. Use the proposed scope until actual intake replaces it. Record each decision with actor, date, alternatives, evidence, impact and affected plan versions.
