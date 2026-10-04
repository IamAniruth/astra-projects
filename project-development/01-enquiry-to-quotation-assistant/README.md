# Enquiry-to-Quotation Assistant: PI and sprint documentation

Date: 30 September 2026  
Project ID: EQ  
Status: Planned; documentation only, no application implementation or installations performed  
Frontend: React.js + TypeScript + Vite  
Backend: Next.js App Router Route Handlers + TypeScript

Build a product that lets a distributor import its catalogue, receive an enquiry, review AI-extracted requirements and product matches, prepare an accurate quotation, approve it, and export it. Sell access through a website with paid pilots and subscriptions. Design for configurable international expansion and explicitly supported markets.

## Primary delivery documents

- [PI and sprint status: all 24 sprints](./_STATUS.md)
- [PI roadmap: six core PIs, one optional improvement PI and one admin PI](PI/README.md)
- [Admin panel specification](docs/13-admin-panel-specification.md)
- [PI-08 administration and S22-S24 sprint plans](PI/PI-08-admin-panel/README.md)
- [Module, feature and sprint coverage matrix](docs/12-module-feature-sprint-matrix.md)
- [Astra LLM reference mapping and release dependencies](docs/11-astra-llm-feature-mapping.md)

Each PI has its own folder and sprint list. Each sprint has a separate folder containing a detailed plan with feature IDs, user story, dependencies, React/Next.js/Astra tasks, acceptance checks, evidence and exit criteria. EQ sprint numbers are independent of Astra platform sprint numbers.

The user's Astra status reference resolves to `astra-llm/codebase/command-documentation/7-PI_STATUS.md`. The private Astra Python runtime is the LLM integration baseline; a generic Ollama deployment is not the selected architecture. The mapping document records source limits and what needs new integration or qualification.

## Supporting specifications

1. [Product scope and decisions](docs/01-product-scope.md)
2. [Architecture and recommended stack](docs/02-architecture-and-stack.md)
3. [Installation and developer setup](docs/03-setup-and-installation.md)
4. [Module specifications and sprint mapping](docs/04-module-specifications.md)
5. [Data model and API contracts](docs/05-data-and-api.md)
6. [AI processing and evaluation](docs/06-ai-workflow.md)
7. [Quality, security, and internationalization](docs/07-quality-security-international.md)
8. [Deployment and operations](docs/08-deployment-and-operations.md)
9. [PI roadmap and delivery rules](PI/README.md)
10. [Open decisions and risks](docs/09-decisions-and-risks.md)
11. [Official technical references](docs/10-references.md)

The setup guide and [templates](templates/README.md) are optional background appendices from the initial planning draft. They are not the deliverable's focus or instructions to perform setup now. Product-worker/queue adoption is subject to the Astra execution ownership decision in S01/S07. No Astra deployment profile is supplied here.

## Delivery roadmap

| PI | Outcome | Sprints | Exit milestone |
|---|---|---|---|
| [PI-01](PI/PI-01-foundation/README.md) | Reproducible setup, accounts, isolated workspaces | S01-S03 | Authenticated tenant foundation |
| [PI-02](PI/PI-02-business-data/README.md) | Customers, catalogue, prices, uploads | S04-S06 | Trusted business data and enquiry intake |
| [PI-03](PI/PI-03-ai-processing/README.md) | Jobs, local AI extraction, reviewed matching | S07-S09 | Reviewed enquiry line items |
| [PI-04](PI/PI-04-quotation/README.md) | Calculations, revisions, approvals, export | S10-S12 | Complete pilot workflow |
| [PI-05](PI/PI-05-commerce-international/README.md) | Website, billing, verified market configuration | S13-S15 | Commercial staging candidate |
| [PI-06](PI/PI-06-production-launch/README.md) | Operations, pilot validation, release | S16-S18 | Supported-market production launch |
| [PI-07](PI/PI-07-controlled-improvement/README.md) | Governed feedback, model improvement, qualified expansion | S19-S21 | Optional post-launch improvements |
| [PI-08](PI/PI-08-admin-panel/README.md) | Workspace access, catalogue/quote governance and commercial operations | S22-S24 | Integrated administration readiness |

Planning assumption: three two-week sprints per PI. The original six core PIs plus the admin PI represent 42 nominal sequential weeks, plus six optional weeks for PI-07. This is a scope-sizing aid, not a delivery commitment. PI-08 reuses existing services and overlaps their delivery; required controls precede the S17 paid pilot rather than waiting until after launch. Re-estimate staffing and overlap after S01 and every PI.

## Planning conventions

- Module IDs M01-M22 and sprint IDs S01-S24 are stable references; features use EQ-Sxx-F01/F02 and tasks/acceptance have explicit IDs. PI-08 extends M18 and related existing modules.
- Every sprint file specifies tasks, dependencies, acceptance checks, and demonstration evidence.
- All work starts as **Planned**. Checkboxes and statuses must be updated only from actual evidence.
- Each sprint links back to the detailed module specification and global quality requirements.
- Naming here is descriptive; no brand or domain name has been selected.
- Country settings, interface language, document currency, and subscription billing currency are separate.
- Later products are out of scope.

Business context: [Product opportunities](../../AI-Product-Opportunities-2026-2030.md) and [Website sales plan](../../AI-Product-Website-Sales-and-Subscription/AI-Product-Website-Sales-and-Subscription-Summary.md).

