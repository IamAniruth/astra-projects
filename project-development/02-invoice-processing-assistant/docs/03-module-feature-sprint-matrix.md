# Module and feature coverage

Each module links to detailed F01/F02 scope, T01-T04 tasks and acceptance. This index is coverage, not implementation evidence.

| Module | Responsibility | Features | Sprint | Status |
|---|---|---|---|---|
| M01 | Buyer discovery and go/no-go | IP-S01-F01/F02 | [S01](../PI/PI-01-foundation/S01-discovery/sprint-plan.md) | Planned |
| M02 | Astra contracts and feasibility | IP-S02-F01/F02 | [S02](../PI/PI-01-foundation/S02-astra-feasibility/sprint-plan.md) | Planned |
| M03 | Accounts and client workspaces | IP-S03-F01/F02 | [S03](../PI/PI-01-foundation/S03-workspaces/sprint-plan.md) | Planned |
| M04 | Invoice and purchase-order intake | IP-S04-F01/F02 | [S04](../PI/PI-02-document-intake/S04-document-intake/sprint-plan.md) | Planned |
| M05 | Parsing OCR and source evidence | IP-S05-F01/F02 | [S05](../PI/PI-02-document-intake/S05-parsing-ocr/sprint-plan.md) | Planned |
| M06 | Durable jobs and allowances | IP-S06-F01/F02 | [S06](../PI/PI-02-document-intake/S06-durable-jobs/sprint-plan.md) | Planned |
| M07 | Header and line-item extraction | IP-S07-F01/F02 | [S07](../PI/PI-03-extraction-validation/S07-field-extraction/sprint-plan.md) | Planned |
| M08 | Normalization and arithmetic checks | IP-S08-F01/F02 | [S08](../PI/PI-03-extraction-validation/S08-normalization-validation/sprint-plan.md) | Planned |
| M09 | Duplicate and purchase-order checks | IP-S09-F01/F02 | [S09](../PI/PI-03-extraction-validation/S09-duplicate-po-checks/sprint-plan.md) | Planned |
| M10 | Review queue and corrections | IP-S10-F01/F02 | [S10](../PI/PI-04-review-export/S10-review-workbench/sprint-plan.md) | Planned |
| M11 | Approval and immutable revisions | IP-S11-F01/F02 | [S11](../PI/PI-04-review-export/S11-approval-revisions/sprint-plan.md) | Planned |
| M12 | Reviewed export workflow | IP-S12-F01/F02 | [S12](../PI/PI-04-review-export/S12-reviewed-export/sprint-plan.md) | Planned |
| M13 | Website onboarding and subscriptions | IP-S13-F01/F02 | [S13](../PI/PI-05-commercial-readiness/S13-commerce/sprint-plan.md) | Planned |
| M14 | Market and export qualification | IP-S14-F01/F02 | [S14](../PI/PI-05-commercial-readiness/S14-market-qualification/sprint-plan.md) | Planned |
| M15 | Operations privacy and recovery | IP-S15-F01/F02 | [S15](../PI/PI-05-commercial-readiness/S15-operations/sprint-plan.md) | Planned |
| M16 | Independent quality evaluation | IP-S16-F01/F02 | [S16](../PI/PI-06-pilot-launch/S16-quality-evaluation/sprint-plan.md) | Planned |
| M17 | Assisted customer pilot | IP-S17-F01/F02 | [S17](../PI/PI-06-pilot-launch/S17-customer-pilot/sprint-plan.md) | Planned |
| M18 | Release and support handover | IP-S18-F01/F02 | [S18](../PI/PI-06-pilot-launch/S18-release-handover/sprint-plan.md) | Planned |
| M19 | Consented feedback dataset | IP-S19-F01/F02 | [S19](../PI/PI-07-controlled-improvement/S19-consented-feedback/sprint-plan.md) | Planned |
| M20 | Evaluated model improvement | IP-S20-F01/F02 | [S20](../PI/PI-07-controlled-improvement/S20-model-improvement/sprint-plan.md) | Planned |
| M21 | Qualified expansion | IP-S21-F01/F02 | [S21](../PI/PI-07-controlled-improvement/S21-qualified-expansion/sprint-plan.md) | Planned |
| M22 | Admin access and client management | IP-S22-F01/F02 | [S22](../PI/PI-08-admin-panel/S22-admin-access-clients/sprint-plan.md) | Planned |
| M23 | Admin invoice and export governance | IP-S23-F01/F02 | [S23](../PI/PI-08-admin-panel/S23-admin-invoice-governance/sprint-plan.md) | Planned |
| M24 | Admin commerce and operational readiness | IP-S24-F01/F02 | [S24](../PI/PI-08-admin-panel/S24-admin-commercial-operations/sprint-plan.md) | Planned |

M22-M24 implement the [admin specification](09-admin-panel-specification.md) through [PI-08](../PI/PI-08-admin-panel/README.md). They own administration screens, action orchestration and integrated acceptance over the original domain services; they do not create duplicate invoice, PO allocation, approval, job or billing authorities.

Client isolation, provenance, audit and errors apply wherever documents are handled. Extraction/normalization changes require evaluation; post-approval edits require a new revision.
