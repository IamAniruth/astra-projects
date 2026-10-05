# DM roadmap

Six PIs, eighteen planned sprints. Dependency order follows the product risk: prove deterministic migration before depending on model-generated rules.

| PI | Outcome | Sprints |
|---|---|---|
| [PI-01](PI-01-foundation/README.md) | Scope, architecture and access | S01-S03 |
| [PI-02](PI-02-discovery/README.md) | Source, target and evidence discovery | S04-S06 |
| [PI-03](PI-03-mapping/README.md) | Deterministic mapping and rehearsal | S07-S09 |
| [PI-04](PI-04-model/README.md) | Astra capability and qualified automation | S10-S12 |
| [PI-05](PI-05-execution/README.md) | Durable execution, validation and cutover | S13-S15 |
| [PI-06](PI-06-qualification/README.md) | Customer experience, host qualification and pilot | S16-S18 |

## Documents 16-19 are part of PI delivery

The owner has included documents 16-19 in the delivery scope. See the [mandatory document-to-PI/sprint matrix](documents-16-19-delivery.md). Document 16 is led by PI-04 with PI-06 qualification; document 17 spans scope, discovery, mapping and application acceptance; document 18 spans foundation, execution and operations with PI-06 qualification; document 19 supplies gap acceptance obligations across all six PIs.

Each PI README identifies its source documents. All eighteen sprint plans include explicit T07-T08 and AC7-AC8 for the assigned requirements, bringing each sprint to eight tasks and eight acceptance checks under its two existing feature IDs. These are required deliverables, not optional reading. No extra PI or duplicate implementation track is created. Re-estimate capacity before committing dates; all work remains Planned.

## Delivery milestones

- S03: scoped local foundation and secret handling.
- S06: useful read-only customer assessment.
- S09: deterministic migration demonstration with human-authored mappings.
- S12: model-assisted/qualified recipe automation, only if capability evidence passes.
- S15: rehearsed cutover and explicit recovery boundaries.
- S18: accepted pilot and accurately scoped release.

At two weeks per sprint the nominal sequential total is 36 weeks; it is not a forecast. Measure the first slice, staffing and Astra training dependencies before scheduling. Later work needs separate plans for CDC/low downtime, populated-target merges, additional engines and broader semantic mapping families.
