# SR PI and sprint status

Updated: 4 October 2026. **Documentation prepared; application implementation has not started.** Priority: Investigate first. There are 24 planned sprints, including PI-08 administration. No buyer interviews, case ingestion, model benchmarks, external account access, installations or upstream test reruns were performed for this plan.

Legend: Planned / In progress / Blocked / Accepted. Acceptance requires evidence and reviewer decision; upstream completion does not transfer to this product.

| PI | Sprint | Deliverable | Status |
|---|---|---|---|
| PI-01 | [S01](PI/PI-01-foundation/S01-discovery/sprint-plan.md) | Buyer discovery and go/no-go | Planned |
| PI-01 | [S02](PI/PI-01-foundation/S02-astra-feasibility/sprint-plan.md) | Astra and drafting feasibility | Planned |
| PI-01 | [S03](PI/PI-01-foundation/S03-agent-access/sprint-plan.md) | Agent teams and customer-case isolation | Planned |
| PI-02 | [S04](PI/PI-02-case-knowledge/S04-case-import/sprint-plan.md) | Ticket import and case chronology | Planned |
| PI-02 | [S05](PI/PI-02-case-knowledge/S05-knowledge-publication/sprint-plan.md) | Approved help knowledge and examples | Planned |
| PI-02 | [S06](PI/PI-02-case-knowledge/S06-index-jobs/sprint-plan.md) | Permissioned indexing and durable jobs | Planned |
| PI-03 | [S07](PI/PI-03-grounded-drafting/S07-case-summaries/sprint-plan.md) | Attributable case summaries | Planned |
| PI-03 | [S08](PI/PI-03-grounded-drafting/S08-retrieval-facts/sprint-plan.md) | Approved retrieval and live-fact boundary | Planned |
| PI-03 | [S09](PI/PI-03-grounded-drafting/S09-reply-drafting/sprint-plan.md) | Source-supported reply drafting | Planned |
| PI-04 | [S10](PI/PI-04-review-handoff/S10-agent-review/sprint-plan.md) | Disclosure checks and agent review | Planned |
| PI-04 | [S11](PI/PI-04-review-handoff/S11-approval-revisions/sprint-plan.md) | Revision approval and concurrency | Planned |
| PI-04 | [S12](PI/PI-04-review-handoff/S12-reviewed-handoff/sprint-plan.md) | Reviewed export and end-to-end handoff | Planned |
| PI-05 | [S13](PI/PI-05-commercial-readiness/S13-commerce/sprint-plan.md) | Website onboarding and support plans | Planned |
| PI-05 | [S14](PI/PI-05-commercial-readiness/S14-scope-qualification/sprint-plan.md) | Language tone and policy qualification | Planned |
| PI-05 | [S15](PI/PI-05-commercial-readiness/S15-operations/sprint-plan.md) | Operations privacy and recovery | Planned |
| PI-06 | [S16](PI/PI-06-pilot-launch/S16-quality-evaluation/sprint-plan.md) | Independent summary and draft evaluation | Planned |
| PI-06 | [S17](PI/PI-06-pilot-launch/S17-customer-pilot/sprint-plan.md) | Assisted support-team pilot | Planned |
| PI-06 | [S18](PI/PI-06-pilot-launch/S18-release-handover/sprint-plan.md) | Release and support handover | Planned |
| PI-07 | [S19](PI/PI-07-controlled-improvement/S19-governed-feedback/sprint-plan.md) | Governed corrections and examples | Planned |
| PI-07 | [S20](PI/PI-07-controlled-improvement/S20-evaluated-improvement/sprint-plan.md) | Evaluated model and retrieval improvement | Planned |
| PI-07 | [S21](PI/PI-07-controlled-improvement/S21-qualified-integrations/sprint-plan.md) | Qualified help-desk and fact integrations | Planned |
| PI-08 | [S22](PI/PI-08-admin-panel/S22-admin-access-workspaces/sprint-plan.md) | Admin access, teams and workspace onboarding | Planned |
| PI-08 | [S23](PI/PI-08-admin-panel/S23-admin-knowledge-governance/sprint-plan.md) | Admin knowledge publication and reply governance | Planned |
| PI-08 | [S24](PI/PI-08-admin-panel/S24-admin-commercial-operations/sprint-plan.md) | Admin commerce, recovery and operational readiness | Planned |

PI-08 reuses existing domain services and does not depend on optional PI-07. Schedule required controls before the paid pilot; see [PI-08 dependencies](PI/PI-08-admin-panel/README.md). All statuses remain Planned.

## Open gates

Buyer/specialty selection; permitted cases/articles; stable import and visibility semantics; actual summary/draft quality; approved source authority; customer-bound live facts or explicit missing-fact workflow; private-data checks; revision approval; pilot thresholds and target-host operations. See [decisions](docs/08-decisions-and-references.md) and [Astra mapping](docs/07-astra-llm-feature-mapping.md).

Next step: [S01 discovery](PI/PI-01-foundation/S01-discovery/sprint-plan.md), then S02 feasibility. Later implementation is conditional on these decisions.
