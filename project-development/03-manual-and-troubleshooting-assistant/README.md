# Manual and Troubleshooting Assistant: PI and sprint documentation

Date: 1 October 2026  
Project ID: MT | Domain: Manufacturing / maintenance | Opportunity rank: 3  
Priority: **Investigate first** | Status: Documentation only; implementation not started

Help equipment service firms and maintenance teams find information in approved manuals for one equipment family. Answer from applicable source passages with page references, preserve procedure prerequisites and warnings, identify missing information, and route unresolved questions to an expert.

## Delivery documents

- [Status: 21 planned sprints](_STATUS.md)
- [Roadmap: six conditional core PIs and one optional improvement PI](PI/README.md)
- [Scope and investigation gates](docs/01-product-scope.md)
- [Architecture and setup prerequisites](docs/02-architecture-and-setup.md)
- [Module, feature and sprint coverage](docs/03-module-feature-sprint-matrix.md)
- [Data model and proposed API contracts](docs/04-data-and-api.md)
- [Retrieval, answers and evaluation](docs/05-ai-workflow.md)
- [Quality, safety, security and operations](docs/06-quality-security-operations.md)
- [Astra source and capability mapping](docs/07-astra-llm-feature-mapping.md)
- [Decisions, risks and references](docs/08-decisions-and-references.md)
- [Investigation and acceptance templates](templates/README.md)

The structure follows [project 01](../01-enquiry-to-quotation-assistant/README.md) and [project 02](../02-invoice-processing-assistant/README.md). Planning baseline: React + TypeScript screens, Next.js business APIs and the private Astra Python runtime. No packages or application components were installed.

First-version scope is approved-source lookup and bounded troubleshooting support. Equipment operation, remote control, invented repair procedures and interpreting unqualified diagrams are outside scope. Measure information-location time, supported-answer accuracy, source correctness and unanswered-question rate before committing to commercial delivery.

Business source: [Product opportunities](../../AI-Product-Opportunities-2026-2030.md). Astra reference: `astra-llm/codebase/command-documentation/7-PI_STATUS.md`. Upstream completion does not qualify this product.
