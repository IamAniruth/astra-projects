# EQ PI and sprint status

Updated: 30 September 2026. **Documentation prepared; application implementation has not started.**

This status concerns the Enquiry-to-Quotation product, not the Astra platform. Upstream recorded completion is not transferred to EQ. No historical Astra test suite was rerun for this plan.

Legend: Planned / In progress / Blocked / Accepted. All rows begin Planned. Change to Accepted only with linked implementation and acceptance evidence.

| PI | Sprint | Deliverable | Status |
|---|---|---|---|
| PI-01 | [S01](PI/PI-01-foundation/S01-scope-contracts/sprint-plan.md) | Product scope and Astra contract baseline | Planned |
| PI-01 | [S02](PI/PI-01-foundation/S02-identity-astra-boundary/sprint-plan.md) | Identity and secure Astra boundary | Planned |
| PI-01 | [S03](PI/PI-01-foundation/S03-workspaces-roles/sprint-plan.md) | Workspaces, roles and business settings | Planned |
| PI-02 | [S04](PI/PI-02-business-data/S04-customers-catalogue/sprint-plan.md) | Customers and catalogue lifecycle | Planned |
| PI-02 | [S05](PI/PI-02-business-data/S05-prices-units/sprint-plan.md) | Price lists, currencies and units | Planned |
| PI-02 | [S06](PI/PI-02-business-data/S06-enquiry-files/sprint-plan.md) | Enquiry intake and document provenance | Planned |
| PI-03 | [S07](PI/PI-03-ai-processing/S07-jobs-budget/sprint-plan.md) | Durable jobs, progress and runtime budgets | Planned |
| PI-03 | [S08](PI/PI-03-ai-processing/S08-astra-extraction/sprint-plan.md) | Astra enquiry extraction and verification | Planned |
| PI-03 | [S09](PI/PI-03-ai-processing/S09-retrieval-review/sprint-plan.md) | Permission-aware catalogue matching | Planned |
| PI-04 | [S10](PI/PI-04-quotation/S10-quote-calculations/sprint-plan.md) | Quotation builder and deterministic totals | Planned |
| PI-04 | [S11](PI/PI-04-quotation/S11-approval-revisions/sprint-plan.md) | Revisions, approval and audit trail | Planned |
| PI-04 | [S12](PI/PI-04-quotation/S12-artifacts-export/sprint-plan.md) | Approved artifacts and end-to-end pilot workflow | Planned |
| PI-05 | [S13](PI/PI-05-commerce-international/S13-website-onboarding/sprint-plan.md) | Sales website and guided onboarding | Planned |
| PI-05 | [S14](PI/PI-05-commerce-international/S14-billing-entitlements/sprint-plan.md) | Subscriptions, entitlements and usage | Planned |
| PI-05 | [S15](PI/PI-05-commerce-international/S15-international-release/sprint-plan.md) | International settings and supported-market qualification | Planned |
| PI-06 | [S16](PI/PI-06-production-launch/S16-operations-hardening/sprint-plan.md) | Administration, security and production operations | Planned |
| PI-06 | [S17](PI/PI-06-production-launch/S17-quality-pilot/sprint-plan.md) | Quotation quality, capacity and customer pilot | Planned |
| PI-06 | [S18](PI/PI-06-production-launch/S18-launch-handover/sprint-plan.md) | Production release, subscriptions and handover | Planned |
| PI-07 | [S19](PI/PI-07-controlled-improvement/S19-consented-feedback/sprint-plan.md) | Consented feedback and governed memory | Planned |
| PI-07 | [S20](PI/PI-07-controlled-improvement/S20-model-improvement/sprint-plan.md) | Evaluated model improvement and reversible release | Planned |
| PI-07 | [S21](PI/PI-07-controlled-improvement/S21-qualified-expansion/sprint-plan.md) | Qualified retrieval, artifacts and market expansion | Planned |

## Current release blockers to track

These are planning dependencies, not newly verified defects: selected checkpoint quotation quality; authenticated product-to-Astra principal mapping; chosen-path cancellation/metering; target-host locked-environment qualification; durable audit/supervisor operations; payment eligibility; first-market review. See the [reference assessment](docs/11-astra-llm-feature-mapping.md).

The reference's latest Sprint 190 report supports local-cpu/local-cuda platform mechanisms on its development host, while its release checklist still blocks production. The EQ plan must not flatten this into either universal support or no local support.

Next planning entry point: [PI-01](PI/PI-01-foundation/README.md), then its S01 sprint.

