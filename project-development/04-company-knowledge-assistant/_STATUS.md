# CK PI and sprint status

Updated: 4 October 2026. **Documentation prepared; application implementation has not started.** Priority: Investigate first. There are 24 planned sprints, including PI-08 administration. No buyer interviews, source ingestion, retrieval/answer benchmarks, connector access, installations or upstream test reruns were performed for this plan.

Legend: Planned / In progress / Blocked / Accepted. Acceptance needs evidence and reviewer decision; Astra completion does not transfer to this product.

| PI | Sprint | Deliverable | Status |
|---|---|---|---|
| PI-01 | [S01](PI/PI-01-foundation/S01-discovery/sprint-plan.md) | Buyer discovery and go/no-go | Planned |
| PI-01 | [S02](PI/PI-01-foundation/S02-astra-feasibility/sprint-plan.md) | Astra and knowledge feasibility | Planned |
| PI-01 | [S03](PI/PI-01-foundation/S03-identity-groups/sprint-plan.md) | Identity groups and workspaces | Planned |
| PI-02 | [S04](PI/PI-02-published-knowledge/S04-source-publication/sprint-plan.md) | Document ownership and publication | Planned |
| PI-02 | [S05](PI/PI-02-published-knowledge/S05-parsing-provenance/sprint-plan.md) | Parsing chunks and source locators | Planned |
| PI-02 | [S06](PI/PI-02-published-knowledge/S06-permissioned-indexing/sprint-plan.md) | Permissioned indexing and jobs | Planned |
| PI-03 | [S07](PI/PI-03-grounded-explanations/S07-authorized-search/sprint-plan.md) | Audience-aware search baseline | Planned |
| PI-03 | [S08](PI/PI-03-grounded-explanations/S08-cited-explanations/sprint-plan.md) | Cited explanations and abstention | Planned |
| PI-03 | [S09](PI/PI-03-grounded-explanations/S09-policy-conflicts/sprint-plan.md) | Policy applicability and conflicts | Planned |
| PI-04 | [S10](PI/PI-04-employee-lifecycle/S10-knowledge-gaps/sprint-plan.md) | Private feedback and unanswered questions | Planned |
| PI-04 | [S11](PI/PI-04-employee-lifecycle/S11-employee-workspace/sprint-plan.md) | Employee search and conversation workspace | Planned |
| PI-04 | [S12](PI/PI-04-employee-lifecycle/S12-source-lifecycle/sprint-plan.md) | Freshness withdrawal and end-to-end lifecycle | Planned |
| PI-05 | [S13](PI/PI-05-commercial-readiness/S13-commerce/sprint-plan.md) | Website onboarding and company plans | Planned |
| PI-05 | [S14](PI/PI-05-commercial-readiness/S14-scope-qualification/sprint-plan.md) | Specialty and language qualification | Planned |
| PI-05 | [S15](PI/PI-05-commercial-readiness/S15-operations/sprint-plan.md) | Operations privacy and recovery | Planned |
| PI-06 | [S16](PI/PI-06-pilot-launch/S16-quality-evaluation/sprint-plan.md) | Independent answer and access evaluation | Planned |
| PI-06 | [S17](PI/PI-06-pilot-launch/S17-customer-pilot/sprint-plan.md) | Assisted company pilot | Planned |
| PI-06 | [S18](PI/PI-06-pilot-launch/S18-release-handover/sprint-plan.md) | Release and support handover | Planned |
| PI-07 | [S19](PI/PI-07-controlled-improvement/S19-governed-feedback/sprint-plan.md) | Governed feedback and source improvement | Planned |
| PI-07 | [S20](PI/PI-07-controlled-improvement/S20-evaluated-improvement/sprint-plan.md) | Evaluated retrieval and model improvement | Planned |
| PI-07 | [S21](PI/PI-07-controlled-improvement/S21-qualified-expansion/sprint-plan.md) | Qualified connectors and knowledge expansion | Planned |
| PI-08 | [S22](PI/PI-08-admin-panel/S22-admin-identity-access/sprint-plan.md) | Admin identity, groups and access | Planned |
| PI-08 | [S23](PI/PI-08-admin-panel/S23-admin-publication-private-gaps/sprint-plan.md) | Admin publication and private knowledge gaps | Planned |
| PI-08 | [S24](PI/PI-08-admin-panel/S24-admin-commercial-operations/sprint-plan.md) | Admin commerce and operational readiness | Planned |

PI-08 reuses existing domain services and does not depend on optional PI-07. Required administration controls precede the S17 paid pilot; S18 consumes final readiness evidence. See [PI-08 scheduling](PI/PI-08-admin-panel/README.md). All statuses remain Planned.

## Open gates

Buyer/specialty selection; permitted internal sources and questions; identity/group authority; publication/effective-date rules; selected-checkpoint support quality; grants/withdrawal through caches and history; private gap analytics; pilot thresholds and target-host operations. See [decisions](docs/08-decisions-and-references.md) and [Astra mapping](docs/07-astra-llm-feature-mapping.md).

Next step: [S01 discovery](PI/PI-01-foundation/S01-discovery/sprint-plan.md), then S02 feasibility. Later implementation is conditional on those decisions.
