# IP PI and sprint status

Updated: 4 October 2026. **Documentation prepared; application implementation has not started.** Priority: Investigate first. There are 24 planned sprints, including PI-08 administration. No interviews, extraction benchmarks, installations or upstream test reruns were performed for this plan.

Legend: Planned / In progress / Blocked / Accepted. Acceptance requires implementation and reviewer evidence; upstream completion never transfers to this product.

| PI | Sprint | Deliverable | Status |
|---|---|---|---|
| PI-01 | [S01](PI/PI-01-foundation/S01-discovery/sprint-plan.md) | Buyer discovery and go/no-go | Planned |
| PI-01 | [S02](PI/PI-01-foundation/S02-astra-feasibility/sprint-plan.md) | Astra contracts and feasibility | Planned |
| PI-01 | [S03](PI/PI-01-foundation/S03-workspaces/sprint-plan.md) | Accounts and client workspaces | Planned |
| PI-02 | [S04](PI/PI-02-document-intake/S04-document-intake/sprint-plan.md) | Invoice and purchase-order intake | Planned |
| PI-02 | [S05](PI/PI-02-document-intake/S05-parsing-ocr/sprint-plan.md) | Parsing OCR and source evidence | Planned |
| PI-02 | [S06](PI/PI-02-document-intake/S06-durable-jobs/sprint-plan.md) | Durable jobs and allowances | Planned |
| PI-03 | [S07](PI/PI-03-extraction-validation/S07-field-extraction/sprint-plan.md) | Header and line-item extraction | Planned |
| PI-03 | [S08](PI/PI-03-extraction-validation/S08-normalization-validation/sprint-plan.md) | Normalization and arithmetic checks | Planned |
| PI-03 | [S09](PI/PI-03-extraction-validation/S09-duplicate-po-checks/sprint-plan.md) | Duplicate and purchase-order checks | Planned |
| PI-04 | [S10](PI/PI-04-review-export/S10-review-workbench/sprint-plan.md) | Review queue and corrections | Planned |
| PI-04 | [S11](PI/PI-04-review-export/S11-approval-revisions/sprint-plan.md) | Approval and immutable revisions | Planned |
| PI-04 | [S12](PI/PI-04-review-export/S12-reviewed-export/sprint-plan.md) | Reviewed export workflow | Planned |
| PI-05 | [S13](PI/PI-05-commercial-readiness/S13-commerce/sprint-plan.md) | Website onboarding and subscriptions | Planned |
| PI-05 | [S14](PI/PI-05-commercial-readiness/S14-market-qualification/sprint-plan.md) | Market and export qualification | Planned |
| PI-05 | [S15](PI/PI-05-commercial-readiness/S15-operations/sprint-plan.md) | Operations privacy and recovery | Planned |
| PI-06 | [S16](PI/PI-06-pilot-launch/S16-quality-evaluation/sprint-plan.md) | Independent quality evaluation | Planned |
| PI-06 | [S17](PI/PI-06-pilot-launch/S17-customer-pilot/sprint-plan.md) | Assisted customer pilot | Planned |
| PI-06 | [S18](PI/PI-06-pilot-launch/S18-release-handover/sprint-plan.md) | Release and support handover | Planned |
| PI-07 | [S19](PI/PI-07-controlled-improvement/S19-consented-feedback/sprint-plan.md) | Consented feedback dataset | Planned |
| PI-07 | [S20](PI/PI-07-controlled-improvement/S20-model-improvement/sprint-plan.md) | Evaluated model improvement | Planned |
| PI-07 | [S21](PI/PI-07-controlled-improvement/S21-qualified-expansion/sprint-plan.md) | Qualified expansion | Planned |
| PI-08 | [S22](PI/PI-08-admin-panel/S22-admin-access-clients/sprint-plan.md) | Admin access and client management | Planned |
| PI-08 | [S23](PI/PI-08-admin-panel/S23-admin-invoice-governance/sprint-plan.md) | Admin invoice and export governance | Planned |
| PI-08 | [S24](PI/PI-08-admin-panel/S24-admin-commercial-operations/sprint-plan.md) | Admin commerce and operational readiness | Planned |

PI-08 reuses existing domain services and does not depend on optional PI-07. Required administration controls precede the S17 paid pilot; S18 consumes final readiness evidence. See [PI-08 scheduling](PI/PI-08-admin-panel/README.md). All sprint statuses remain Planned.

## Open gates

Buyer access and permitted samples; market/export target; checkpoint/OCR quality; authenticated isolation; durable jobs/allowances; target-host operations and pilot outcomes. See [decisions](docs/08-decisions-and-references.md) and [Astra mapping](docs/07-astra-llm-feature-mapping.md).

Next step: [S01 discovery](PI/PI-01-foundation/S01-discovery/sprint-plan.md), then S02 feasibility. Implementation is conditional on these decisions.
