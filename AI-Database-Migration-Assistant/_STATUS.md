# DM PI and sprint status

Updated: 5 October 2026. **Documentation prepared; implementation not started.**

No trained migration model, qualified connector, benchmark result, production migration or deployment is claimed.

Owner update, 5 October 2026: React/Next.js UI, Next.js application APIs, Python migration workers and local Astra responsibilities are now confirmed; end-to-end UI coverage is specified. [Training guide 16](docs/16-local-llm-training-datasets-and-configuration.md) adds proposed dataset percentages, model-size experiments, training/inference configurations and measurable response-quality requirements. All eighteen sprints remain Planned; no training or application implementation was performed.

| PI | Sprint | Deliverable | Status |
|---|---|---|---|
| PI-01 | [S01](PI/PI-01-foundation/S01-scope-intake/sprint-plan.md) | Customer scope and migration contract | Planned |
| PI-01 | [S02](PI/PI-01-foundation/S02-architecture-contracts/sprint-plan.md) | Service architecture and integration ownership | Planned |
| PI-01 | [S03](PI/PI-01-foundation/S03-access-data-boundaries/sprint-plan.md) | Access, secrets and local data boundaries | Planned |
| PI-02 | [S04](PI/PI-02-discovery/S04-source-connectors/sprint-plan.md) | Source connector and consistent extraction | Planned |
| PI-02 | [S05](PI/PI-02-discovery/S05-target-app-contract/sprint-plan.md) | Target database and application contract | Planned |
| PI-02 | [S06](PI/PI-02-discovery/S06-profiling-evidence/sprint-plan.md) | Data profiling and code-grounded evidence | Planned |
| PI-03 | [S07](PI/PI-03-mapping/S07-mapping-registry/sprint-plan.md) | Mapping language and review registry | Planned |
| PI-03 | [S08](PI/PI-03-mapping/S08-compiler-key-planning/sprint-plan.md) | Deterministic compiler and identity planning | Planned |
| PI-03 | [S09](PI/PI-03-mapping/S09-deterministic-rehearsal/sprint-plan.md) | Deterministic migration vertical slice | Planned |
| PI-04 | [S10](PI/PI-04-model/S10-baseline-training-corpus/sprint-plan.md) | Astra baseline and licensed migration corpus | Planned |
| PI-04 | [S11](PI/PI-04-model/S11-capability-development/sprint-plan.md) | Astra retrieval and migration capability training | Planned |
| PI-04 | [S12](PI/PI-04-model/S12-qualified-automation/sprint-plan.md) | Qualified recipes and bounded agent repair | Planned |
| PI-05 | [S13](PI/PI-05-execution/S13-durable-jobs-recovery/sprint-plan.md) | Durable execution, fencing and resume | Planned |
| PI-05 | [S14](PI/PI-05-execution/S14-independent-validation/sprint-plan.md) | Complete reconciliation and target app acceptance | Planned |
| PI-05 | [S15](PI/PI-05-execution/S15-cutover-recovery/sprint-plan.md) | Cutover controller and recovery boundaries | Planned |
| PI-06 | [S16](PI/PI-06-qualification/S16-customer-operator-ui/sprint-plan.md) | Customer workflows and operator controls | Planned |
| PI-06 | [S17](PI/PI-06-qualification/S17-host-security-recovery/sprint-plan.md) | Target-host capacity, security and restore qualification | Planned |
| PI-06 | [S18](PI/PI-06-qualification/S18-pilot-release-handover/sprint-plan.md) | Pilot acceptance and qualified release | Planned |

## Open gates and next action

Owner integration, 5 October 2026: documents 16-19 are now mandatory sources in all assigned PI/sprint scopes. The [delivery matrix](PI/documents-16-19-delivery.md), six PI READMEs and all eighteen sprint plans identify ownership and explicit T07-T08/AC7-AC8 deliverables. Each sprint now has eight tasks and eight acceptance checks. No implementation acceptance is claimed; scope/capacity must be re-estimated.

Planning review, 5 October 2026: [twelve gaps](docs/19-gap-review-and-acceptance-register.md) now have explicit requirements and sprint/evidence ownership, including scope closure, attachments/login readiness, full-system restore, release revocation and operating acceptance. All are specified only. Re-estimate affected sprints; the original nominal duration has not been validated.

Next implementation step: S01 intake for one real old/new application. Confirm engine/version, schema/repository access, business owner, data scope, downtime, recovery targets and pilot permissions. Then build the human-mapped deterministic slice through S09 while the Astra model remains explicitly unqualified for arbitrary migration.

No results exist yet for model migration accuracy, real-host throughput, recovery duration or customer pilot. Proposed evaluation thresholds are requirements, not measurements. Full implementation requires the evidence and owners described in the sprint plans.
