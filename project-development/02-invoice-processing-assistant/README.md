# Invoice Processing Assistant: PI and sprint documentation

Date: 1 October 2026  
Project ID: IP | Domain: Accounting | Opportunity rank: 2  
Priority: **Investigate first** | Status: Documentation only; implementation not started

Help accounting firms and finance teams upload invoices and purchase orders, extract and normalize fields and line items, identify potential duplicates and mismatches, review corrections, approve a revision, and export results. Measure field accuracy, review time, missed exceptions and incorrectly flagged duplicates before committing to a commercial build.

## Delivery documents

- [Status: 21 planned sprints](_STATUS.md)
- [Roadmap: six conditional core PIs and one optional improvement PI](PI/README.md)
- [Scope and investigation gates](docs/01-product-scope.md)
- [Architecture and setup prerequisites](docs/02-architecture-and-setup.md)
- [Module, feature and sprint coverage](docs/03-module-feature-sprint-matrix.md)
- [Data model and proposed API contracts](docs/04-data-and-api.md)
- [AI workflow and evaluation](docs/05-ai-workflow.md)
- [Quality, security and operations](docs/06-quality-security-operations.md)
- [Astra capability mapping](docs/07-astra-llm-feature-mapping.md)
- [Decisions, risks and references](docs/08-decisions-and-references.md)
- [Investigation and acceptance templates](templates/README.md)

The structure follows the [Enquiry-to-Quotation Assistant](../01-enquiry-to-quotation-assistant/README.md). Planning baseline: React + TypeScript frontend, Next.js server, and private Astra Python runtime. These are architecture assumptions to validate, not installed components.

Start with reviewed CSV/JSON exports. Automatic ledger posting, payment initiation and autonomous tax determination are outside the initial product. Preserve source evidence and let reviewers resolve uncertain values.

The requested Astra reference resolves to `astra-llm/codebase/command-documentation/7-PI_STATUS.md`. Platform completion is separate from invoice model quality and product readiness. All sprints remain Planned.

Business source: [Product opportunities](../../AI-Product-Opportunities-2026-2030.md).
