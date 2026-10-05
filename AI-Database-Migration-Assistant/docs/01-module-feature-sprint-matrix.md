# DM module, feature and sprint coverage

All items planned. Feature IDs are local to DM; platform and WS sprint numbers are not reused.

| Module | Sprint | Feature IDs and deliverables | Primary specification |
|---|---|---|---|
| M01 | [S01](../PI/PI-01-foundation/S01-scope-intake/sprint-plan.md) | DM-S01-F01 Scope and intake; DM-S01-F02 Pilot success and exclusions | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M01 | [S02](../PI/PI-01-foundation/S02-architecture-contracts/sprint-plan.md) | DM-S02-F01 Control and data planes; DM-S02-F02 Astra and commercial integration | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M01 | [S03](../PI/PI-01-foundation/S03-access-data-boundaries/sprint-plan.md) | DM-S03-F01 Scoped access; DM-S03-F02 Retention and isolation | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M02 | [S04](../PI/PI-02-discovery/S04-source-connectors/sprint-plan.md) | DM-S04-F01 Catalog discovery; DM-S04-F02 Pinned snapshot extraction | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M02 | [S05](../PI/PI-02-discovery/S05-target-app-contract/sprint-plan.md) | DM-S05-F01 Target schema inventory; DM-S05-F02 Application behavior evidence | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M02 | [S06](../PI/PI-02-discovery/S06-profiling-evidence/sprint-plan.md) | DM-S06-F01 Data quality assessment; DM-S06-F02 Relevant code retrieval | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M03 | [S07](../PI/PI-03-mapping/S07-mapping-registry/sprint-plan.md) | DM-S07-F01 Entity and field mapping; DM-S07-F02 Immutable review and recipe versions | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M03 | [S08](../PI/PI-03-mapping/S08-compiler-key-planning/sprint-plan.md) | DM-S08-F01 Validated execution plans; DM-S08-F02 Keys and dependency ordering | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M03 | [S09](../PI/PI-03-mapping/S09-deterministic-rehearsal/sprint-plan.md) | DM-S09-F01 Batch copy and lineage; DM-S09-F02 Initial reconciliation | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M04 | [S10](../PI/PI-04-model/S10-baseline-training-corpus/sprint-plan.md) | DM-S10-F01 Frozen task benchmark; DM-S10-F02 Licensed training examples | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M04 | [S11](../PI/PI-04-model/S11-capability-development/sprint-plan.md) | DM-S11-F01 Evidence-grounded proposals; DM-S11-F02 Measured candidate training | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M04 | [S12](../PI/PI-04-model/S12-qualified-automation/sprint-plan.md) | DM-S12-F01 Automatic recipe execution; DM-S12-F02 Restricted rehearsal repair | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M05 | [S13](../PI/PI-05-execution/S13-durable-jobs-recovery/sprint-plan.md) | DM-S13-F01 Target commit receipts; DM-S13-F02 Interruption and concurrent worker handling | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M05 | [S14](../PI/PI-05-execution/S14-independent-validation/sprint-plan.md) | DM-S14-F01 Independent integrity checks; DM-S14-F02 Business and application workflows | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M05 | [S15](../PI/PI-05-execution/S15-cutover-recovery/sprint-plan.md) | DM-S15-F01 Write-fenced switch; DM-S15-F02 Before/after-write recovery | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M06 | [S16](../PI/PI-06-qualification/S16-customer-operator-ui/sprint-plan.md) | DM-S16-F01 Mapping and run interface; DM-S16-F02 Evidence and support operations | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M06 | [S17](../PI/PI-06-qualification/S17-host-security-recovery/sprint-plan.md) | DM-S17-F01 Real-host performance; DM-S17-F02 Security and disaster recovery | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |
| M06 | [S18](../PI/PI-06-qualification/S18-pilot-release-handover/sprint-plan.md) | DM-S18-F01 Scoped customer pilot; DM-S18-F02 Release and operating handover | [Product specification](../AI-Database-Migration-Assistant-Specification.md) |

## Cross-cutting coverage

Documents 16-19 are required delivery sources, with explicit added tasks T07-T08 and acceptance checks AC7-AC8 in every assigned sprint. The [document-to-PI/sprint matrix](../PI/documents-16-19-delivery.md) provides the authoritative allocation; each PI README repeats its local scope. These requirements extend the original two feature IDs per sprint rather than creating an unrelated backlog.

The [gap review](19-gap-review-and-acceptance-register.md) adds GAP-01 through GAP-12 acceptance obligations to existing sprints. Detailed scope/evidence links appear in each affected sprint; these are not completed features and require re-estimation.

Owner-confirmed stack and end-to-end UI: S02 architecture, S13 durable execution, S16 complete twelve-step screen coverage and S17 restart/recovery qualification. [Training guide 16](16-local-llm-training-datasets-and-configuration.md): S10 dataset percentages/splits, S11 model/configuration experiments, S12 qualified automation and S17 actual host measurement.

Connector support: S04/S05/S17. Business semantics and transformations: S06-S08/S14. Model development: S10-S12. Durable jobs and unknown outcomes: S09/S13. Cutover and post-write recovery: S15/S17. Security/retention/tenancy: S03/S16/S17. Application acceptance: S05/S14/S18. Local hardware and costs: S10/S17/S18. Commercial ownership: S02/S16/S18. CDC and additional engines are deferred, not silently included in these eighteen sprints.
