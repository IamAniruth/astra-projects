# MT PI and sprint status

Updated: 4 October 2026. **Documentation prepared; application implementation has not started.** Priority: Investigate first. There are 24 planned sprints, including PI-08 administration. No buyer interviews, manual ingestion, retrieval/answer benchmarks, installations or upstream test reruns were performed for this plan.

Legend: Planned / In progress / Blocked / Accepted. Acceptance requires evidence and reviewer decision. Upstream Astra completion never transfers to this product.

| PI | Sprint | Deliverable | Status |
|---|---|---|---|
| PI-01 | [S01](PI/PI-01-foundation/S01-discovery/sprint-plan.md) | Buyer discovery and go/no-go | Planned |
| PI-01 | [S02](PI/PI-01-foundation/S02-astra-feasibility/sprint-plan.md) | Astra and retrieval feasibility | Planned |
| PI-01 | [S03](PI/PI-01-foundation/S03-sites-equipment/sprint-plan.md) | Sites accounts and equipment context | Planned |
| PI-02 | [S04](PI/PI-02-approved-knowledge/S04-manual-registry/sprint-plan.md) | Approved manual registry | Planned |
| PI-02 | [S05](PI/PI-02-approved-knowledge/S05-parsing-provenance/sprint-plan.md) | Parsing page references and procedures | Planned |
| PI-02 | [S06](PI/PI-02-approved-knowledge/S06-index-publication/sprint-plan.md) | Permissioned indexing and publication | Planned |
| PI-03 | [S07](PI/PI-03-grounded-assistance/S07-scoped-retrieval/sprint-plan.md) | Equipment-scoped retrieval | Planned |
| PI-03 | [S08](PI/PI-03-grounded-assistance/S08-cited-answers/sprint-plan.md) | Source-linked answers and abstention | Planned |
| PI-03 | [S09](PI/PI-03-grounded-assistance/S09-guided-procedures/sprint-plan.md) | Approved troubleshooting branches | Planned |
| PI-04 | [S10](PI/PI-04-review-lifecycle/S10-expert-escalation/sprint-plan.md) | Expert escalation and unresolved cases | Planned |
| PI-04 | [S11](PI/PI-04-review-lifecycle/S11-technician-workspace/sprint-plan.md) | Technician question and source workspace | Planned |
| PI-04 | [S12](PI/PI-04-review-lifecycle/S12-revision-lifecycle/sprint-plan.md) | Revision withdrawal and end-to-end workflow | Planned |
| PI-05 | [S13](PI/PI-05-commercial-readiness/S13-commerce/sprint-plan.md) | Website onboarding and team plans | Planned |
| PI-05 | [S14](PI/PI-05-commercial-readiness/S14-scope-qualification/sprint-plan.md) | Language and supported-scope qualification | Planned |
| PI-05 | [S15](PI/PI-05-commercial-readiness/S15-operations/sprint-plan.md) | Operations privacy and recovery | Planned |
| PI-06 | [S16](PI/PI-06-pilot-launch/S16-quality-evaluation/sprint-plan.md) | Independent answer and retrieval evaluation | Planned |
| PI-06 | [S17](PI/PI-06-pilot-launch/S17-customer-pilot/sprint-plan.md) | Assisted maintenance-team pilot | Planned |
| PI-06 | [S18](PI/PI-06-pilot-launch/S18-release-handover/sprint-plan.md) | Release and support handover | Planned |
| PI-07 | [S19](PI/PI-07-controlled-improvement/S19-governed-feedback/sprint-plan.md) | Governed feedback and knowledge updates | Planned |
| PI-07 | [S20](PI/PI-07-controlled-improvement/S20-evaluated-improvement/sprint-plan.md) | Evaluated retrieval and model improvement | Planned |
| PI-07 | [S21](PI/PI-07-controlled-improvement/S21-qualified-expansion/sprint-plan.md) | Qualified equipment and modality expansion | Planned |
| PI-08 | [S22](PI/PI-08-admin-panel/S22-admin-sites-equipment-access/sprint-plan.md) | Admin sites, equipment and access | Planned |
| PI-08 | [S23](PI/PI-08-admin-panel/S23-admin-manual-procedure-governance/sprint-plan.md) | Admin manual and procedure governance | Planned |
| PI-08 | [S24](PI/PI-08-admin-panel/S24-admin-commercial-operations/sprint-plan.md) | Admin commerce and operational readiness | Planned |

PI-08 reuses existing domain services and does not depend on optional PI-07. Required administration controls precede the S17 paid pilot; S18 consumes final readiness evidence. See [PI-08 scheduling](PI/PI-08-admin-panel/README.md). All statuses remain Planned.

## Open gates

Buyer and equipment-family selection; permitted approved manuals and applicability rules; domain reviewer; parser/retrieval/checkpoint qualification; authenticated source access and withdrawal propagation; pilot thresholds; target-host operations and actual customer outcomes. See [decisions](docs/08-decisions-and-references.md) and [Astra mapping](docs/07-astra-llm-feature-mapping.md).

Next step: [S01 discovery](PI/PI-01-foundation/S01-discovery/sprint-plan.md), then S02 feasibility. Later implementation is conditional on those decisions.
