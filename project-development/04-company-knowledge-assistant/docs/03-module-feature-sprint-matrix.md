# Module and feature coverage

Each module links to detailed F01/F02 scope, T01-T04 tasks and acceptance checks. This index establishes planning coverage, not implementation evidence.

| Module | Responsibility | Features | Sprint | Status |
|---|---|---|---|---|
| M01 | Buyer discovery and go/no-go | CK-S01-F01/F02 | [S01](../PI/PI-01-foundation/S01-discovery/sprint-plan.md) | Planned |
| M02 | Astra and knowledge feasibility | CK-S02-F01/F02 | [S02](../PI/PI-01-foundation/S02-astra-feasibility/sprint-plan.md) | Planned |
| M03 | Identity groups and workspaces | CK-S03-F01/F02 | [S03](../PI/PI-01-foundation/S03-identity-groups/sprint-plan.md) | Planned |
| M04 | Document ownership and publication | CK-S04-F01/F02 | [S04](../PI/PI-02-published-knowledge/S04-source-publication/sprint-plan.md) | Planned |
| M05 | Parsing chunks and source locators | CK-S05-F01/F02 | [S05](../PI/PI-02-published-knowledge/S05-parsing-provenance/sprint-plan.md) | Planned |
| M06 | Permissioned indexing and jobs | CK-S06-F01/F02 | [S06](../PI/PI-02-published-knowledge/S06-permissioned-indexing/sprint-plan.md) | Planned |
| M07 | Audience-aware search baseline | CK-S07-F01/F02 | [S07](../PI/PI-03-grounded-explanations/S07-authorized-search/sprint-plan.md) | Planned |
| M08 | Cited explanations and abstention | CK-S08-F01/F02 | [S08](../PI/PI-03-grounded-explanations/S08-cited-explanations/sprint-plan.md) | Planned |
| M09 | Policy applicability and conflicts | CK-S09-F01/F02 | [S09](../PI/PI-03-grounded-explanations/S09-policy-conflicts/sprint-plan.md) | Planned |
| M10 | Private feedback and unanswered questions | CK-S10-F01/F02 | [S10](../PI/PI-04-employee-lifecycle/S10-knowledge-gaps/sprint-plan.md) | Planned |
| M11 | Employee search and conversation workspace | CK-S11-F01/F02 | [S11](../PI/PI-04-employee-lifecycle/S11-employee-workspace/sprint-plan.md) | Planned |
| M12 | Freshness withdrawal and end-to-end lifecycle | CK-S12-F01/F02 | [S12](../PI/PI-04-employee-lifecycle/S12-source-lifecycle/sprint-plan.md) | Planned |
| M13 | Website onboarding and company plans | CK-S13-F01/F02 | [S13](../PI/PI-05-commercial-readiness/S13-commerce/sprint-plan.md) | Planned |
| M14 | Specialty and language qualification | CK-S14-F01/F02 | [S14](../PI/PI-05-commercial-readiness/S14-scope-qualification/sprint-plan.md) | Planned |
| M15 | Operations privacy and recovery | CK-S15-F01/F02 | [S15](../PI/PI-05-commercial-readiness/S15-operations/sprint-plan.md) | Planned |
| M16 | Independent answer and access evaluation | CK-S16-F01/F02 | [S16](../PI/PI-06-pilot-launch/S16-quality-evaluation/sprint-plan.md) | Planned |
| M17 | Assisted company pilot | CK-S17-F01/F02 | [S17](../PI/PI-06-pilot-launch/S17-customer-pilot/sprint-plan.md) | Planned |
| M18 | Release and support handover | CK-S18-F01/F02 | [S18](../PI/PI-06-pilot-launch/S18-release-handover/sprint-plan.md) | Planned |
| M19 | Governed feedback and source improvement | CK-S19-F01/F02 | [S19](../PI/PI-07-controlled-improvement/S19-governed-feedback/sprint-plan.md) | Planned |
| M20 | Evaluated retrieval and model improvement | CK-S20-F01/F02 | [S20](../PI/PI-07-controlled-improvement/S20-evaluated-improvement/sprint-plan.md) | Planned |
| M21 | Qualified connectors and knowledge expansion | CK-S21-F01/F02 | [S21](../PI/PI-07-controlled-improvement/S21-qualified-expansion/sprint-plan.md) | Planned |
| M22 | Admin identity, groups and access | CK-S22-F01/F02 | [S22](../PI/PI-08-admin-panel/S22-admin-identity-access/sprint-plan.md) | Planned |
| M23 | Admin publication and private knowledge gaps | CK-S23-F01/F02 | [S23](../PI/PI-08-admin-panel/S23-admin-publication-private-gaps/sprint-plan.md) | Planned |
| M24 | Admin commerce and operational readiness | CK-S24-F01/F02 | [S24](../PI/PI-08-admin-panel/S24-admin-commercial-operations/sprint-plan.md) | Planned |

M22-M24 implement the [admin specification](09-admin-panel-specification.md) through [PI-08](../PI/PI-08-admin-panel/README.md). They own administration surfaces and integrated verification over existing services rather than duplicate identity, publication, private-gap, job or billing authorities.

Permissions, publication/effective dates, source support and error handling apply throughout. Group/source revocation covers active jobs, histories, caches and gap reports. New retrieval/model/parser configurations need relevant evaluation; employee feedback never automatically changes shared policy.
