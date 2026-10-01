# Company Knowledge Assistant: PI and sprint documentation

Date: 1 October 2026  
Project ID: CK | Domain: Business operations | Opportunity rank: 4  
Priority: **Investigate first** | Status: Documentation only; implementation not started

Help employees retrieve and understand internal policies, handbooks and operating information, using current published sources they are allowed to access. Start with document upload, permission-aware search, source-linked explanations and an administrator view of unanswered questions.

## Delivery documents

- [Status: 21 planned sprints](_STATUS.md)
- [Roadmap: six conditional core PIs and one optional improvement PI](PI/README.md)
- [Scope and investigation gates](docs/01-product-scope.md)
- [Architecture and setup prerequisites](docs/02-architecture-and-setup.md)
- [Module, feature and sprint coverage](docs/03-module-feature-sprint-matrix.md)
- [Data model and proposed API contracts](docs/04-data-and-api.md)
- [Retrieval, explanations and evaluation](docs/05-ai-workflow.md)
- [Quality, privacy, security and operations](docs/06-quality-security-operations.md)
- [Astra source and capability mapping](docs/07-astra-llm-feature-mapping.md)
- [Decisions, risks and references](docs/08-decisions-and-references.md)
- [Investigation and acceptance templates](templates/README.md)

This follows [project 01](../01-enquiry-to-quotation-assistant/README.md), [project 02](../02-invoice-processing-assistant/README.md) and [project 03](../03-manual-and-troubleshooting-assistant/README.md). Planning baseline: React + TypeScript screens, Next.js business APIs and private Astra Python runtime; validate exact choices in S02.

Choose a specialty such as franchise operations or engineering procedures rather than assuming a general company chatbot is differentiated. Measure answer accuracy, adoption, search time and repeated questions resolved. Employees receive explanations, not automatic policy decisions or actions.

Business source: [Product opportunities](../../AI-Product-Opportunities-2026-2030.md). Astra reference: `astra-llm/codebase/command-documentation/7-PI_STATUS.md`. No application, connector, installation or benchmark was created or run by this documentation task.
