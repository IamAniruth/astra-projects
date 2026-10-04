# Module and feature coverage

Each module links to detailed F01/F02 scope, T01-T04 tasks and acceptance checks. This index is coverage, not evidence of implementation.

| Module | Responsibility | Features | Sprint | Status |
|---|---|---|---|---|
| M01 | Buyer discovery and go/no-go | MT-S01-F01/F02 | [S01](../PI/PI-01-foundation/S01-discovery/sprint-plan.md) | Planned |
| M02 | Astra and retrieval feasibility | MT-S02-F01/F02 | [S02](../PI/PI-01-foundation/S02-astra-feasibility/sprint-plan.md) | Planned |
| M03 | Sites accounts and equipment context | MT-S03-F01/F02 | [S03](../PI/PI-01-foundation/S03-sites-equipment/sprint-plan.md) | Planned |
| M04 | Approved manual registry | MT-S04-F01/F02 | [S04](../PI/PI-02-approved-knowledge/S04-manual-registry/sprint-plan.md) | Planned |
| M05 | Parsing page references and procedures | MT-S05-F01/F02 | [S05](../PI/PI-02-approved-knowledge/S05-parsing-provenance/sprint-plan.md) | Planned |
| M06 | Permissioned indexing and publication | MT-S06-F01/F02 | [S06](../PI/PI-02-approved-knowledge/S06-index-publication/sprint-plan.md) | Planned |
| M07 | Equipment-scoped retrieval | MT-S07-F01/F02 | [S07](../PI/PI-03-grounded-assistance/S07-scoped-retrieval/sprint-plan.md) | Planned |
| M08 | Source-linked answers and abstention | MT-S08-F01/F02 | [S08](../PI/PI-03-grounded-assistance/S08-cited-answers/sprint-plan.md) | Planned |
| M09 | Approved troubleshooting branches | MT-S09-F01/F02 | [S09](../PI/PI-03-grounded-assistance/S09-guided-procedures/sprint-plan.md) | Planned |
| M10 | Expert escalation and unresolved cases | MT-S10-F01/F02 | [S10](../PI/PI-04-review-lifecycle/S10-expert-escalation/sprint-plan.md) | Planned |
| M11 | Technician question and source workspace | MT-S11-F01/F02 | [S11](../PI/PI-04-review-lifecycle/S11-technician-workspace/sprint-plan.md) | Planned |
| M12 | Revision withdrawal and end-to-end workflow | MT-S12-F01/F02 | [S12](../PI/PI-04-review-lifecycle/S12-revision-lifecycle/sprint-plan.md) | Planned |
| M13 | Website onboarding and team plans | MT-S13-F01/F02 | [S13](../PI/PI-05-commercial-readiness/S13-commerce/sprint-plan.md) | Planned |
| M14 | Language and supported-scope qualification | MT-S14-F01/F02 | [S14](../PI/PI-05-commercial-readiness/S14-scope-qualification/sprint-plan.md) | Planned |
| M15 | Operations privacy and recovery | MT-S15-F01/F02 | [S15](../PI/PI-05-commercial-readiness/S15-operations/sprint-plan.md) | Planned |
| M16 | Independent answer and retrieval evaluation | MT-S16-F01/F02 | [S16](../PI/PI-06-pilot-launch/S16-quality-evaluation/sprint-plan.md) | Planned |
| M17 | Assisted maintenance-team pilot | MT-S17-F01/F02 | [S17](../PI/PI-06-pilot-launch/S17-customer-pilot/sprint-plan.md) | Planned |
| M18 | Release and support handover | MT-S18-F01/F02 | [S18](../PI/PI-06-pilot-launch/S18-release-handover/sprint-plan.md) | Planned |
| M19 | Governed feedback and knowledge updates | MT-S19-F01/F02 | [S19](../PI/PI-07-controlled-improvement/S19-governed-feedback/sprint-plan.md) | Planned |
| M20 | Evaluated retrieval and model improvement | MT-S20-F01/F02 | [S20](../PI/PI-07-controlled-improvement/S20-evaluated-improvement/sprint-plan.md) | Planned |
| M21 | Qualified equipment and modality expansion | MT-S21-F01/F02 | [S21](../PI/PI-07-controlled-improvement/S21-qualified-expansion/sprint-plan.md) | Planned |
| M22 | Admin sites, equipment and access | MT-S22-F01/F02 | [S22](../PI/PI-08-admin-panel/S22-admin-sites-equipment-access/sprint-plan.md) | Planned |
| M23 | Admin manual and procedure governance | MT-S23-F01/F02 | [S23](../PI/PI-08-admin-panel/S23-admin-manual-procedure-governance/sprint-plan.md) | Planned |
| M24 | Admin commerce and operational readiness | MT-S24-F01/F02 | [S24](../PI/PI-08-admin-panel/S24-admin-commercial-operations/sprint-plan.md) | Planned |

M22-M24 implement the [admin specification](09-admin-panel-specification.md) through [PI-08](../PI/PI-08-admin-panel/README.md). They own administration surfaces and integrated verification over existing services rather than duplicate source approval, applicability, procedure, job or billing authorities.

Source approval, equipment applicability, permissions, citations and failure handling apply wherever answers or documents are handled. Source withdrawal applies to active jobs, histories, caches and procedure sessions. New model/parser/index configurations require relevant re-evaluation; feedback alone cannot publish an approved procedure.
