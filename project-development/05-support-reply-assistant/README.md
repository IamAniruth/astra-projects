# Support Reply Assistant: PI and sprint documentation

Date: 1 October 2026  
Project ID: SR | Domain: Customer service | Opportunity rank: 5  
Priority: **Investigate first** | Status: Documentation only; implementation not started

Help support teams import approved help articles and selected tickets, summarize a case, retrieve relevant evidence and draft a reply for an agent to review and approve. Start with one industry, language or difficult support workflow and measure handling time, draft acceptance, factual corrections and customer satisfaction.

## Delivery documents

- [Status: 21 planned sprints](_STATUS.md)
- [Roadmap: six conditional core PIs and one optional improvement PI](PI/README.md)
- [Scope and investigation gates](docs/01-product-scope.md)
- [Architecture and setup prerequisites](docs/02-architecture-and-setup.md)
- [Module, feature and sprint coverage](docs/03-module-feature-sprint-matrix.md)
- [Data model and proposed API contracts](docs/04-data-and-api.md)
- [Summaries, retrieval, drafting and evaluation](docs/05-ai-workflow.md)
- [Quality, privacy, security and operations](docs/06-quality-security-operations.md)
- [Astra source and capability mapping](docs/07-astra-llm-feature-mapping.md)
- [Decisions, risks and references](docs/08-decisions-and-references.md)
- [Investigation and acceptance templates](templates/README.md)

This follows the structure of [project 04](../04-company-knowledge-assistant/README.md) and the earlier plans. Planning baseline: React + TypeScript screens, Next.js business APIs and private Astra Python runtime; validate exact choices in S02.

The initial deliverable is an agent-reviewed draft with explicit handoff. Approval does not send a message or execute a refund. Live order/account facts require an authorized business-system query; imported tickets and model memory cannot establish their current state.

Business source: [Product opportunities](../../AI-Product-Opportunities-2026-2030.md). Astra reference: `astra-llm/codebase/command-documentation/7-PI_STATUS.md`. No application, integration, installation or benchmark was created or run by this documentation task.
