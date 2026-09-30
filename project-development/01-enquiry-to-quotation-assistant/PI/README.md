# PI roadmap and delivery rules

PI means **Program Increment**. EQ identifiers are separate from Astra's PI and sprint identifiers. For example, EQ S08 consumes parts of Astra Sprint 157 and other capabilities; it is not a renumbering of Astra.

Status: all implementation **Planned**. This is the primary delivery plan. Setup notes are supporting references only; no setup, installation, service start or code implementation is part of this documentation task.

## Roadmap

| PI | Sprints | Business outcome | Release relationship |
|---|---|---|---|
| [PI-01](./PI-01-foundation/README.md) | S01-S03 | An agreed business workflow, authenticated customer identity and isolated workspaces with a private Astra integration contract. | Initial product delivery |
| [PI-02](./PI-02-business-data/README.md) | S04-S06 | Customer, catalogue, price and source-document data are usable and traceable. | Initial product delivery |
| [PI-03](./PI-03-ai-processing/README.md) | S07-S09 | A durable, budgeted Astra workflow produces source-backed, reviewed requirements and catalogue selections. | Initial product delivery |
| [PI-04](./PI-04-quotation/README.md) | S10-S12 | Staff can produce a trustworthy approved quotation and export it end to end. | Initial product delivery |
| [PI-05](./PI-05-commerce-international/README.md) | S13-S15 | A buyer can understand the product, onboard and purchase an eligible plan in a validated market. | Initial product delivery |
| [PI-06](./PI-06-production-launch/README.md) | S16-S18 | The actual product, model and deployment pass quality, recovery and commercial gates before release. | Initial product delivery |
| [PI-07](./PI-07-controlled-improvement/README.md) | S19-S21 | Optional post-launch improvements use consented data, measurable benefit and reversible releases. | Optional after first launch |

## Scheduling and ownership

Suggested cadence: two-week sprints, three sprints per PI. Six core PIs therefore represent 36 nominal weeks and the optional seventh adds six; this is a planning baseline, not an estimate validated against staffing. Do not interpret the earlier business validation month as a full product build schedule.

Each sprint includes two feature IDs, a user story, frontend/backend/Astra/data work, dependencies, acceptance and evidence. Assign actual owners and size stories at planning. Suggested roles: product/domain reviewer, React developer, Next.js/data developer, Astra integration engineer, QA and operations. One person may hold several roles; no additional agents or staff are presumed.

Sprint identifiers are stable. Split a feature into smaller tickets under its existing ID when needed; record spillover and re-estimate rather than marking unfinished scope complete.

## Readiness and completion

Before a sprint: confirm prior dependencies, data permission, acceptance examples, local/upstream capability availability, owner and realistic capacity. A fixture may unlock UI development while the real-model gate remains pending.

Before completion: relevant tests, reviewed business rules, migration/contract changes, access checks, user-visible error states, actual demonstration and retained evidence must pass. Follow [quality definition of done](../docs/07-quality-security-international.md). Documentation written is not implementation complete.

Evidence is stored later under a product-controlled evidence location using commit/model/prompt/data/environment IDs. Plans name expected artifacts; their existence is not asserted here.

## Dependency graph

```text
PI-01 -> PI-02 -> PI-03 -> PI-04 -> PI-05 -> PI-06 (first release)
                                                 |
                                                 v
                                       PI-07 (optional improvements)
```

Some work can overlap after contracts stabilize, but release gates remain. A manual quoting pilot cannot be presented as an AI-qualified release. Upstream Astra model/operations gaps are explicit dependencies in [Astra mapping](../docs/11-astra-llm-feature-mapping.md).

## Navigation

- [Status and full sprint list](../_STATUS.md)
- [Module and feature coverage](../docs/12-module-feature-sprint-matrix.md)
- [Business modules](../docs/04-module-specifications.md)
- [Astra evidence/dependency register](../docs/11-astra-llm-feature-mapping.md)

