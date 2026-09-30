# AI Product Opportunities: 2026–2030

Prepared: 30 September 2026  
Purpose: Help a new business choose an internationally adaptable AI product, using an existing local LLM where appropriate.

## Executive summary

This document describes 32 product opportunities across major industries. It includes the buyer, problem, first version, role of a local LLM, commercial approach, and pilot measures for each product.

The recommended starting points are:

1. **Enquiry-to-quotation assistant:** for distributors that repeatedly prepare quotations from customer enquiries.
2. **Invoice processing assistant:** for accounting firms and finance teams handling repetitive document entry and checking.
3. **Manual and troubleshooting assistant:** for equipment service teams that need reliable access to approved technical information.

Choose the opportunity where you can reach real buyers and obtain representative data. Start with one industry and one workflow in an explicitly supported market, while keeping the product configurable for expansion. A paid pilot with measurable results is stronger evidence than a high position in this list.

**International scope:** These product concepts are not restricted to one country. Build a shared application with configurable languages, currencies, regional formats, document templates, integrations, and deployment regions. International adaptability is a design goal; availability in every country is not assumed. Validate each market before selling there. See [International product design and country rollout](#international-product-design-and-country-rollout) and the companion [Website Sales and Subscription Summary](AI-Product-Website-Sales-and-Subscription-Summary.md).

These priorities are a qualitative recommendation for a small startup, not a market-size ranking or a guarantee of future demand. The list covers major domains but is not exhaustive. Actual feasibility depends on the founder's skills, customer access, budget, model, hardware, and data availability, which have not yet been assessed. The order is a starting baseline; reassess it for each country's buyers, alternatives, language needs, and cost of localization.

## Evidence and ranking method

The broader direction is informed by OECD research on small-business AI adoption and the World Economic Forum's employment and skills outlook through 2030. These sources support investigating AI-assisted business workflows; they do not validate demand for each product below.

- [OECD: AI adoption by small and medium-sized enterprises](https://www.oecd.org/en/publications/ai-adoption-by-small-and-medium-sized-enterprises_426399c1-en.html) identifies adoption prerequisites including connectivity, data and compute, skills, and finance.
- [OECD: Empowering SMEs in the age of AI, 2026](https://www.oecd.org/en/publications/empowering-smes-in-the-age-of-ai_bf5a9816-en.html) examines AI use and barriers in a non-representative sample of over 2,000 SMEs across 12 OECD countries.
- [World Economic Forum: Future of Jobs Report 2025](https://www.weforum.org/publications/the-future-of-jobs-report-2025/digest/) presents employer expectations for 2025–2030, including growing technology skills and changes in care, education, and energy-related work. Employment growth does not automatically imply software purchasing demand.

Priority balances five considerations: a clear paying customer, frequency and cost of the problem, measurable benefit, achievable development scope, and suitability for a local LLM. Adjacent ranks should not be treated as precise differences.

## Product shortlist

| Rank | Domain | Product | Starting priority | Local LLM role |
|---|---|---|---|---|
| 1 | Wholesale / distribution | Enquiry-to-quotation assistant | Investigate first | Interpret enquiries and draft quotations |
| 2 | Accounting | Invoice processing assistant | Investigate first | Extract and normalize document fields |
| 3 | Manufacturing / maintenance | Manual and troubleshooting assistant | Investigate first | Answer from approved source passages |
| 4 | Business operations | Company knowledge assistant | Investigate first | Retrieve and explain internal information |
| 5 | Customer service | Support reply assistant | Investigate first | Summarize cases and draft replies |
| 6 | Construction | Tender preparation assistant | Investigate first | Extract requirements and draft responses |
| 7 | Local services | Enquiry and booking assistant | Investigate first | Understand enquiries and collect booking details |
| 8 | Procurement | Supplier quotation comparison tool | Investigate first | Normalize descriptions and summarize differences |
| 9 | Logistics | Shipment document assistant | Investigate first | Extract and compare document information |
| 10 | Property management | Maintenance request assistant | Investigate first | Classify requests and draft work orders |
| 11 | Education | Teacher preparation workspace | Validate with domain access | Draft teaching materials from approved content |
| 12 | Sales | Sales follow-up assistant | Validate with domain access | Summarize conversations and draft follow-ups |
| 13 | HR | Onboarding and policy assistant | Validate with domain access | Explain policies and guide onboarding |
| 14 | IT services | Help-desk investigation assistant | Validate with domain access | Connect tickets with runbooks |
| 15 | Legal operations | Contract comparison workspace | Validate with domain access | Extract obligations and explain differences |
| 16 | Healthcare administration | Clinic administration assistant | Validate with domain access | Organize intake and administrative drafts |
| 17 | Insurance operations | Claims document assistant | Validate with domain access | Organize evidence and identify missing items |
| 18 | Software development | Codebase onboarding assistant | Validate with domain access | Explain code with repository references |
| 19 | Hospitality | Guest enquiry assistant | Validate with domain access | Answer property-specific questions |
| 20 | E-commerce | Product catalogue assistant | Validate with domain access | Normalize descriptions and attributes |
| 21 | Quality management | Audit evidence organizer | Validate with domain access | Link evidence to a defined checklist |
| 22 | Research | Research document workspace | Validate with domain access | Compare and summarize source documents |
| 23 | Retail / inventory | Demand and replenishment planner | Build with additional capabilities | Explain forecasts from a separate forecasting system |
| 24 | Cybersecurity | Security alert investigation assistant | Build with additional capabilities | Summarize evidence for analysts |
| 25 | Energy / buildings | Energy usage analyst | Build with additional capabilities | Explain computed anomalies and trends |
| 26 | Agriculture | Farm records and advisory assistant | Build with additional capabilities | Organize records and retrieve regional guidance |
| 27 | Finance operations | Cash-flow planning assistant | Build with additional capabilities | Explain calculated financial scenarios |
| 28 | Government / public services | Application completeness assistant | Build with additional capabilities | Explain published requirements |
| 29 | Environmental reporting | Sustainability evidence assistant | Build with additional capabilities | Organize evidence and draft reports |
| 30 | Manufacturing inspection | Visual defect inspection product | Build with additional capabilities | Explain outputs from a vision system |
| 31 | Industrial maintenance | Predictive maintenance system | Build with additional capabilities | Explain sensor-based alerts |
| 32 | Accessibility / languages | Specialized transcription and translation tool | Build with additional capabilities | Refine transcripts and translate text |

## Priority 1: Products to investigate first

### 1. Enquiry-to-quotation assistant

- **Buyer and problem:** Distributors and suppliers spend staff time interpreting customer enquiries, finding catalogue items, and preparing quotations.
- **First version:** Upload a catalogue and an enquiry; extract requested items and quantities; suggest catalogue matches; flag ambiguous items; generate an editable quotation for approval.
- **Local LLM and other components:** The LLM interprets language and drafts text. A database supplies approved prices and stock; ordinary code calculates totals. Scanned enquiries may require OCR.
- **Commercial approach:** Setup fee for catalogue preparation plus a monthly business subscription with usage limits.
- **Pilot measures:** Minutes per quotation, item-match accuracy, staff correction rate, and quotations completed.
- **Main difficulty:** Messy catalogues, similar product names, units, and customer-specific pricing. Start with one category such as electrical supplies.

### 2. Invoice processing assistant

- **Buyer and problem:** Accounting firms and finance teams manually enter invoice data and check it against purchase records.
- **First version:** Upload invoices and purchase orders; extract fields and line items; identify potential duplicates and mismatches; review and export results.
- **Local LLM and other components:** Use OCR or document parsers, structured extraction, and field validation. Use deterministic calculations for totals and rule-based matching where possible.
- **Commercial approach:** Subscription with document allowances and optional onboarding fees.
- **Pilot measures:** Field accuracy, review time per invoice, missed exceptions, and incorrectly flagged duplicates.
- **Main difficulty:** Supplier layout variation, poor scans, and accounting integrations. Begin with reviewed exports rather than automatic ledger posting.

### 3. Manual and troubleshooting assistant

- **Buyer and problem:** Equipment service firms and maintenance teams spend time searching long manuals and previous service notes.
- **First version:** Index approved manuals for one equipment family; answer questions with page references; show missing information and route unresolved issues to an expert.
- **Local LLM and other components:** Document retrieval, model/version filtering, and source-linked answers. Diagrams and scanned pages may need separate processing.
- **Commercial approach:** Per-site or team subscription plus document onboarding.
- **Pilot measures:** Time to locate information, supported-answer accuracy, source correctness, and unanswered-question rate.
- **Main difficulty:** Outdated manuals, equipment variants, and consequences of incorrect instructions. Keep answers grounded in approved procedures.

### 4. Company knowledge assistant

- **Buyer and problem:** Businesses repeatedly answer employee questions spread across policies, handbooks, and internal documents.
- **First version:** Document upload, permission-aware search, source-linked answers, and an administrator view of unanswered questions.
- **Local LLM and other components:** Retrieval and summarization, with document permissions enforced before information reaches the model.
- **Commercial approach:** Company subscription based on seats or document volume.
- **Pilot measures:** Answer accuracy, employee adoption, time spent searching, and repeated questions resolved.
- **Main difficulty:** Differentiation and keeping documents current. Choose a specialty such as franchise operations or engineering procedures.

### 5. Support reply assistant

- **Buyer and problem:** Support teams repeatedly search product information and previous tickets before answering customers.
- **First version:** Import help articles and selected tickets; summarize a case; draft a source-supported reply for an agent to approve.
- **Local LLM and other components:** Summarization and response drafting; live order details come from authorized business-system queries.
- **Commercial approach:** Per-agent subscription or usage-based business plan.
- **Pilot measures:** Handling time, draft acceptance rate, factual corrections, and customer satisfaction.
- **Main difficulty:** Existing alternatives and integrations. Differentiate through one industry, language, or difficult support workflow.

### 6. Tender preparation assistant

- **Buyer and problem:** Contractors must extract requirements from lengthy tender documents and assemble complete submissions.
- **First version:** Upload a tender package; extract deadlines and requirements; produce a checklist; match approved company evidence; prepare editable response drafts.
- **Local LLM and other components:** Document extraction, source references, version tracking, and a reusable evidence library.
- **Commercial approach:** Per-project pricing or a team subscription.
- **Pilot measures:** Preparation time, missed requirements, source accuracy, and reviewer corrections.
- **Main difficulty:** Amendments, inconsistent document structure, and domain-specific requirements. Humans verify eligibility, commitments, and the final submission.

### 7. Enquiry and booking assistant

- **Buyer and problem:** Service businesses miss enquiries or spend time collecting basic booking information.
- **First version:** Website chat that answers approved FAQs, collects service details, retrieves available slots, and requests a booking with a staff handoff.
- **Local LLM and other components:** Conversational interpretation; a calendar integration determines availability and booking state.
- **Commercial approach:** Setup plus monthly subscription, with messaging or voice costs accounted for separately.
- **Pilot measures:** Completed enquiries, booking conversion, handoff rate, and booking errors.
- **Main difficulty:** Reliability, calendar conflicts, and channel integration costs. Start with text and one service category.

### 8. Supplier quotation comparison tool

- **Buyer and problem:** Procurement teams compare differently formatted supplier quotations with inconsistent descriptions and units.
- **First version:** Upload quotations for one request; align comparable items; display price, delivery, and specification differences with source references.
- **Local LLM and other components:** Normalize descriptions and suggest matches. Code handles currency conversion inputs, units, taxes, and calculations.
- **Commercial approach:** Buyer-team subscription or document-volume plan.
- **Pilot measures:** Comparison time, matching accuracy, and reviewer corrections.
- **Main difficulty:** Apparent matches may hide specification differences. Require confirmation of uncertain equivalence and keep award decisions with buyers.

### 9. Shipment document assistant

- **Buyer and problem:** Freight forwarders repeatedly check information across invoices, packing lists, and transport documents.
- **First version:** Extract shipment fields; compare names, references, quantities, and weights; produce an exception list for staff review.
- **Local LLM and other components:** OCR, field extraction, normalization, and explicit consistency rules.
- **Commercial approach:** Per-shipment allowance or operations-team subscription.
- **Pilot measures:** Review time, extraction accuracy, and missed document inconsistencies.
- **Main difficulty:** Document formats and workflow variation. Begin with completeness checking for a defined shipment process.

### 10. Maintenance request assistant

- **Buyer and problem:** Property managers receive incomplete requests and repeatedly ask tenants for details before arranging repairs.
- **First version:** Collect issue details, classify requests, retrieve property information, draft work orders, and route them to staff.
- **Local LLM and other components:** Conversation and classification; a database tracks properties, vendors, and request status.
- **Commercial approach:** Per-property portfolio subscription.
- **Pilot measures:** Time to create a work order, missing-information rate, and routing corrections.
- **Main difficulty:** Urgent requests and vendor coordination. Use explicit escalation rules and staff confirmation for dispatch or spending.

## Priority 2: Opportunities requiring customer access or domain expertise

### 11. Teacher preparation workspace

- **Buyer and problem:** Schools and training centres spend time adapting course content into lessons and practice material.
- **First version:** Generate editable lesson plans, quizzes, and explanations from approved materials for one subject and learner level.
- **Local LLM and other components:** Retrieval, controlled drafting, and an educator review interface.
- **Commercial approach:** Institution or teaching-team subscription.
- **Pilot measures:** Preparation time, factual corrections, and teacher acceptance.
- **Main difficulty:** Curriculum alignment, pedagogical quality, and willingness to pay. Start with teacher preparation rather than automated high-stakes grading.

### 12. Sales follow-up assistant

- **Buyer and problem:** Sales teams lose time updating records and preparing follow-ups after customer conversations.
- **First version:** Import notes or transcripts; draft a summary, next steps, follow-up message, and CRM update for approval.
- **Local LLM and other components:** Summarization and extraction; audio needs transcription and CRM writes need an integration.
- **Commercial approach:** Per-salesperson subscription.
- **Pilot measures:** Administration time, draft acceptance, and completion of agreed follow-ups.
- **Main difficulty:** Integration reliability and avoiding invented commitments. Focus on a particular sales process.

### 13. Onboarding and policy assistant

- **Buyer and problem:** HR teams repeatedly explain policies and track routine onboarding tasks.
- **First version:** Answer questions using current approved policies and guide employees through a role-specific checklist.
- **Local LLM and other components:** Permission-aware document retrieval plus a workflow database.
- **Commercial approach:** Company subscription scaled by employee count.
- **Pilot measures:** Repeated enquiries resolved, onboarding completion time, and policy-answer accuracy.
- **Main difficulty:** Policy versions, employee confidentiality, and overlap with existing HR software.

### 14. Help-desk investigation assistant

- **Buyer and problem:** IT support providers spend time understanding tickets and finding relevant runbooks.
- **First version:** Summarize tickets, suggest categories, retrieve approved diagnostic steps, and draft a technician response.
- **Local LLM and other components:** Search and summarization with ticket-system integration.
- **Commercial approach:** Per-technician or managed-service-provider subscription.
- **Pilot measures:** Triage time, useful suggestion rate, and technician corrections.
- **Main difficulty:** Customer-specific environments and sensitive logs. Keep initial diagnostic suggestions separate from command execution.

### 15. Contract comparison workspace

- **Buyer and problem:** Legal teams compare contract versions and extract obligations for review.
- **First version:** Side-by-side differences, obligation tables, and clause observations linked to source text and a customer-approved playbook.
- **Local LLM and other components:** Clause extraction and explanation, supported by deterministic document comparison.
- **Commercial approach:** Team subscription plus private deployment or onboarding services.
- **Pilot measures:** Review time, missed changes, and professional correction rate.
- **Main difficulty:** Domain accuracy and confidentiality. Professionals retain interpretation and approval responsibility.

### 16. Clinic administration assistant

- **Buyer and problem:** Clinic staff repeatedly organize intake information and handle administrative enquiries.
- **First version:** Check form completeness, prepare staff-reviewed administrative summaries, and route appointment requests.
- **Local LLM and other components:** Structured extraction and drafting, with restricted access and practice-system integrations.
- **Commercial approach:** Per-clinic subscription plus setup.
- **Pilot measures:** Staff time per intake, missing fields, and correction rate.
- **Main difficulty:** Sensitive information and workflow integration. Keep the first product focused on administration.

### 17. Claims document assistant

- **Buyer and problem:** Claims administrators organize submissions and repeatedly request missing evidence.
- **First version:** Classify documents, create a source-linked timeline, compare against a configured checklist, and draft missing-information requests.
- **Local LLM and other components:** Document extraction, retrieval, and workflow tracking.
- **Commercial approach:** Team subscription or claim-volume allowance.
- **Pilot measures:** Preparation time, document classification accuracy, and missing-item detection.
- **Main difficulty:** Different claim types and sensitive records. Staff retain coverage and settlement decisions.

### 18. Codebase onboarding assistant

- **Buyer and problem:** Developers joining an unfamiliar repository struggle to locate components and understand behavior.
- **First version:** Index one repository and its documentation; answer questions with file and symbol references; explain relevant code paths.
- **Local LLM and other components:** Code search, parsing, revision tracking, and a model suitable for code.
- **Commercial approach:** Team subscription or private installation and support.
- **Pilot measures:** Time to answer onboarding questions, reference accuracy, and developer usefulness ratings.
- **Main difficulty:** Repository scale, stale indexes, model quality, and differentiation from established developer tools.

### 19. Guest enquiry assistant

- **Buyer and problem:** Hotel staff repeatedly answer questions about amenities, check-in, and property services.
- **First version:** Answer approved property FAQs and create staff-visible service requests with multilingual text where validated.
- **Local LLM and other components:** Retrieval and conversation; booking availability and prices must come from live systems.
- **Commercial approach:** Per-property subscription.
- **Pilot measures:** Routine enquiries resolved, staff handoffs, and answer accuracy.
- **Main difficulty:** Language quality, changing property information, and reservation integrations.

### 20. Product catalogue assistant

- **Buyer and problem:** Stores receive inconsistent supplier descriptions and incomplete product attributes.
- **First version:** Import supplier data, map it to a defined schema, draft consistent descriptions, and flag unsupported or missing attributes.
- **Local LLM and other components:** Extraction and rewriting, with schema validation and an approval interface.
- **Commercial approach:** Subscription based on catalogue size or processed items.
- **Pilot measures:** Minutes per listing, attribute accuracy, and edits before publication.
- **Main difficulty:** Incorrect specifications and duplicate products. Generate claims only from supplied evidence.

### 21. Audit evidence organizer

- **Buyer and problem:** Quality teams gather documents manually before internal or customer audits.
- **First version:** Configure a checklist, upload evidence, suggest mappings, and identify missing or expired documents for review.
- **Local LLM and other components:** Evidence retrieval, classification, dates, and version management.
- **Commercial approach:** Per-site subscription plus checklist setup.
- **Pilot measures:** Preparation time, mapping accuracy, and missing evidence found.
- **Main difficulty:** Interpreting requirements and keeping evidence current. The tool supports preparation; it does not certify compliance.

### 22. Research document workspace

- **Buyer and problem:** Research teams compare information spread across papers and reports.
- **First version:** Upload a defined corpus; search it; create source-linked comparison tables and summaries; display conflicting findings.
- **Local LLM and other components:** Retrieval, citation verification, metadata extraction, and optional table parsing.
- **Commercial approach:** Team subscription or private deployment.
- **Pilot measures:** Search time, citation correctness, and unsupported-statement rate.
- **Main difficulty:** Long documents, complex tables, and overconfident synthesis. Separate source statements from generated interpretation.

## Priority 3: Opportunities requiring additional capabilities

### 23. Demand and replenishment planner

- **Buyer and problem:** Retailers and distributors must balance stockouts against excess inventory.
- **First version:** Import sales, stock, and lead-time data; generate forecasts and reviewed reorder suggestions for one category.
- **Local LLM and other components:** A separate forecasting system produces estimates. The LLM explains them and supports questions.
- **Commercial approach:** Subscription based on stores or catalogue size.
- **Pilot measures:** Forecast error against a simple baseline, stockouts, and excess inventory over an adequate observation period.
- **Main difficulty:** Data quality, seasonality, promotions, and limited history.

### 24. Security alert investigation assistant

- **Buyer and problem:** Security teams spend time collecting context and writing summaries for alerts.
- **First version:** Read authorized alerts and logs; create source-linked incident summaries; retrieve runbooks; draft investigation steps.
- **Local LLM and other components:** Security-tool integrations and established detection systems supply evidence; the model assists interpretation.
- **Commercial approach:** Analyst-team subscription or private installation.
- **Pilot measures:** Triage time, evidence accuracy, and analyst acceptance.
- **Main difficulty:** Security expertise, adversarial content in logs, and consequences of incorrect conclusions. Start with read-only assistance.

### 25. Energy usage analyst

- **Buyer and problem:** Building operators have consumption data but limited time to investigate unusual usage.
- **First version:** Import meter data, identify anomalies using analytical methods, and produce a reviewed explanation report.
- **Local LLM and other components:** Time-series analysis calculates trends; the LLM explains findings and relevant operational context.
- **Commercial approach:** Per-building subscription plus data onboarding.
- **Pilot measures:** Useful anomalies found, false-alert rate, and investigation time.
- **Main difficulty:** Meter coverage, weather and occupancy effects, and proving attributable savings.

### 26. Farm records and advisory assistant

- **Buyer and problem:** Cooperatives and farm businesses need organized records and access to locally relevant information.
- **First version:** Record activities and costs; retrieve approved guidance for one crop and region; prepare summaries for an agronomist or manager.
- **Local LLM and other components:** Structured records and retrieval; weather or price information needs current data feeds.
- **Commercial approach:** Cooperative or agribusiness subscription and onboarding.
- **Pilot measures:** Record completeness, time saved, and expert-rated answer quality.
- **Main difficulty:** Regional variation, connectivity, language quality, and access to paying buyers.

### 27. Cash-flow planning assistant

- **Buyer and problem:** Finance teams spend time combining receivables, payables, and assumptions into cash-flow scenarios.
- **First version:** Import approved accounting exports, calculate scenarios, and explain projected cash movements with links to inputs.
- **Local LLM and other components:** Deterministic financial calculations and explicit assumptions generate figures; the model explains them.
- **Commercial approach:** Business or accountant subscription.
- **Pilot measures:** Preparation time, reconciliation accuracy, and scenario traceability.
- **Main difficulty:** Incomplete data, uncertain payment dates, and unreliable assumptions. Keep scenarios distinct from guaranteed outcomes.

### 28. Application completeness assistant

- **Buyer and problem:** Agencies and service organizations repeatedly explain application requirements and identify missing attachments.
- **First version:** Cover one application process using current official requirements; explain fields; check completeness; route exceptions to staff.
- **Local LLM and other components:** Source-controlled retrieval and deterministic completeness rules.
- **Commercial approach:** Institutional license, deployment, and support contract.
- **Pilot measures:** Incomplete submissions, staff handling time, and accuracy against current requirements.
- **Main difficulty:** Rule updates, accessibility, institutional procurement, and ensuring the tool does not imply official approval.

### 29. Sustainability evidence assistant

- **Buyer and problem:** Businesses collect fragmented operational evidence for customer questionnaires and environmental reports.
- **First version:** Organize documents, extract supported activity data, map evidence to a defined template, and draft a traceable response.
- **Local LLM and other components:** Extraction and drafting; separate validated methods calculate quantitative metrics.
- **Commercial approach:** Per-business subscription plus template onboarding.
- **Pilot measures:** Preparation time, evidence completeness, and reviewer corrections.
- **Main difficulty:** Method selection, changing reporting requirements, and unsupported claims.

### 30. Visual defect inspection product

- **Buyer and problem:** Manufacturers need consistent inspection of a defined part or production step.
- **First version:** Detect a small set of defects from controlled images and present findings for inspector review.
- **Local LLM and other components:** A vision model, cameras, lighting, and labelled examples are central. An LLM can explain results or prepare reports.
- **Commercial approach:** Per-inspection-station deployment plus support.
- **Pilot measures:** Missed defects, false rejects, and inspection throughput on representative production images.
- **Main difficulty:** Rare defects, image variation, hardware integration, and costly mistakes.

### 31. Predictive maintenance system

- **Buyer and problem:** Industrial operators want earlier indication of equipment problems and better inspection planning.
- **First version:** Monitor one equipment type, detect sensor anomalies, and show alerts with contextual maintenance records.
- **Local LLM and other components:** Sensor analytics and predictive models produce alerts; the LLM summarizes evidence and retrieves approved procedures.
- **Commercial approach:** Per-asset or site subscription plus integration fees.
- **Pilot measures:** False alarms, missed events, useful warning time, and maintenance-team acceptance.
- **Main difficulty:** Sufficient history, rare failures, changing operating conditions, and long validation periods.

### 32. Specialized transcription and translation tool

- **Buyer and problem:** Organizations need accurate transcripts or translations containing industry terminology or regional languages.
- **First version:** Support a narrow language pair or audio setting, apply an approved glossary, and provide a reviewer correction interface.
- **Local LLM and other components:** Speech recognition produces transcripts; language models assist translation and formatting. Preserve the original for comparison.
- **Commercial approach:** Usage allowance based on audio minutes or text volume, plus team plans.
- **Pilot measures:** Word error rate for speech, terminology accuracy, translation review scores, and correction time.
- **Main difficulty:** Accent and noise variation, language quality, and separating transcription errors from later model edits.

## How a local LLM becomes a shared product

Users do not need to install your model when you host it. They use your website or application, which communicates with your backend. Your backend verifies access, retrieves permitted information, calls the model, validates results, and returns a response.

```text
User's browser or mobile application
                 |
                 v
Backend: login, company permissions, usage limits, workflow rules
        |                    |                    |
        v                    v                    v
Business database     Document retrieval     Local LLM server
        |                    |                    |
        +--------------------+--------------------+
                             |
                             v
                 Reviewed output or approved action
```

The shared foundation normally needs:

- User accounts and company-level data separation.
- Document upload, parsing, and OCR when needed.
- Retrieval that selects relevant authorized source passages.
- Model calls with structured output validation.
- Source references and a review screen for important outputs.
- Deterministic calculations for prices, totals, dates, and other exact rules.
- Request queues, usage limits, monitoring, backups, and failure handling.
- Integrations and explicit authorization for actions such as updating records or sending messages.

A local model is not automatically a private end-to-end system. Document storage, logs, backups, OCR, embeddings, and external integrations also determine where information goes.

### Deployment choices

| Deployment | Suitable use | Main operational consideration |
|---|---|---|
| Existing computer | Development and controlled pilot | Must remain available; capacity and connectivity are limited by that machine |
| Dedicated owned or rented server | Shared hosted product | Requires operating budget, monitoring, and tested capacity |
| Customer's own server | Internal business deployment | Requires installation, updates, and support for each customer environment |

Registered-user count is not the same as simultaneous generation capacity. Benchmark the actual model, prompt lengths, hardware, and workload before promising response times or user limits. For example, Ollama documents memory-dependent parallel processing and request queueing: [Ollama FAQ](https://github.com/ollama/ollama/blob/main/docs/faq.mdx).

The model name, runner, RAM, GPU, and expected workload are still unknown. No capacity estimate is implied by this document. Before commercial deployment, also verify the terms of the specific model and any bundled components.

## Selecting and validating the first product

Use these questions to compare your top three ideas:

1. Can you speak to at least five potential buyers in this industry?
2. Does the task happen frequently enough to justify a subscription?
3. Can the buyer show actual examples and describe the current time or cost?
4. Can you obtain permission to use representative data in a pilot?
5. Can the first version provide value before extensive integrations?
6. Can a person verify the output and correct mistakes easily?
7. Will the buyer pay for a successful pilot and continue if it meets agreed measures?

Prefer the idea with the strongest answers, even if it ranks lower in the shortlist.

### Suggested first-month plan

| Period | Work | Reviewable result |
|---|---|---|
| Week 1 | Interview buyers in one industry and observe the current process | Defined customer, recurring problem, sample inputs, baseline effort |
| Week 2 | Build a narrow prototype using permitted sample data | One complete workflow with visible review and corrections |
| Week 3 | Arrange a small paid pilot and agree success measures | Pilot scope, usage limits, price, and measurement plan |
| Week 4 | Run the pilot and review accuracy, effort, and costs | Evidence for continuing, changing scope, or stopping |

This is a planning outline, not a guaranteed delivery schedule. Integrations, domain review, or difficult documents can take longer.

## Commercial model and operating costs

A practical starting offer is a setup fee plus a monthly subscription with defined usage and support. Document-heavy products can use document allowances; internal tools can use team or site plans. Validate pricing with buyers rather than deriving it only from model costs.

Track hardware or server costs, electricity, storage and backups, OCR or speech services, external APIs, onboarding time, support, and ongoing maintenance. Self-hosting removes some third-party model API charges but does not make operation free.

During a pilot, compare both customer value and delivery cost. A product that saves work but requires extensive manual support from you may need narrower scope or a different price.

## International product design and country rollout

### Shared product, configurable markets

Maintain one product foundation and introduce country or regional configuration where the workflow needs it. Avoid separate codebases for every country. Country settings must not replace customer-specific settings: two businesses in the same country may use different languages, currencies, document templates, and operating regions.

| Area | Design requirement |
|---|---|
| Language | Keep interface text translatable; allow the user to choose a language; test model answers, retrieval, OCR, and speech separately for each supported language |
| Writing systems | Support Unicode, international names and addresses, and right-to-left layouts when launching relevant languages |
| Regional formats | Store structured values; display dates, numbers, units, and addresses using the selected locale; ask about ambiguous dates instead of guessing |
| Time | Store event timestamps consistently and preserve the applicable named time zone for appointments, deadlines, and recurring schedules |
| Currency | Store the currency with every amount, use appropriate precision, and keep document currency separate from subscription billing currency |
| Pricing and calculations | Use configured price lists, units, rounding, and reviewed calculation rules; the LLM must not invent exchange rates or tax treatment |
| Documents | Provide versioned templates and field mappings for regional invoices, quotations, forms, and terminology |
| Sources and rules | Tag regional guidance and requirements with their source, jurisdiction, version, and effective period; use reviewed rules for exact decisions |
| Integrations | Use replaceable connectors for regional accounting, messaging, calendars, and business systems |
| Deployment | Offer only hosting regions or private installations you can operate; account for storage, inference, logs, backups, and support access together |
| Availability | Maintain an explicit supported-market list and feature availability by market rather than claiming universal support |

A multilingual interface does not prove that the model is accurate in those languages. Evaluate representative customer tasks and provide a clear unsupported-language or human-review path when quality is insufficient. Model selection can vary by language without changing the customer workflow.

### Country adaptation across the product list

These are planning assessments of adaptation effort, not determinations of local obligations.

| Product ranks | Products | Main localization work |
|---|---|---|
| 1, 8, 20 | Quotations, supplier comparisons, catalogues | Product terminology, units, currencies, catalogue conventions, document templates, and local business systems |
| 2, 27 | Invoices and cash-flow planning | Regional document fields, accounting exports, verified calculation rules, and currency handling |
| 3, 4, 18, 22 | Manuals, company knowledge, codebase onboarding, research | Source and interface languages, permissions, technical terminology, and deployment preferences; often a practical starting point for expansion |
| 5, 7, 12, 19 | Support, bookings, sales follow-up, guest enquiries | Languages, communication channels, time zones, business hours, and local calendar or CRM integrations |
| 6, 9, 28 | Tenders, shipment documents, public applications | Jurisdiction-specific processes, current forms and requirements, deadlines, and official sources |
| 10, 13, 21 | Property maintenance, HR onboarding, audit evidence | Local operating policies, escalation procedures, terminology, and approved regional checklists |
| 11, 26 | Teacher preparation and farm assistance | Curriculum or crop/region relevance, local language quality, and review by suitable domain experts |
| 15, 16, 17 | Contracts, clinic administration, claims | Local professional workflows, sensitive-data handling, templates, and domain review before launch |
| 14, 24 | IT help desk and security investigations | Customer environments, access permissions, regional hosting needs, language, and integration coverage |
| 23, 25, 29 | Replenishment, energy analysis, sustainability evidence | Local units, seasons, operating data, calculation methods, and applicable reporting templates |
| 30, 31 | Visual inspection and predictive maintenance | Site-specific hardware, equipment, representative training/evaluation data, and local support capability |
| 32 | Transcription and translation | Explicit language-pair, accent, terminology, script, and audio-quality evaluation |

For easier international expansion, investigate knowledge, catalogue, and support workflows using customer-provided material. Products built around local official requirements may still be valuable but need more work for each market. The quotation assistant remains a strong starting choice where you have buyer access; invoice processing needs more regional accounting adaptation.

### Market readiness record

For each proposed market, document:

1. Target industry, reachable buyers, and evidence of willingness to pay.
2. Supported interface and document languages with task-quality results.
3. Formats, currencies, units, templates, and integrations tested.
4. Domain requirements and qualified local review where needed.
5. Supported billing arrangements and published commercial terms.
6. Actual data-processing locations and customer deployment commitments.
7. Support language, hours, and capacity.
8. Status: research, pilot, commercially available, or unavailable.

Country settings should be explicit and editable by authorized users. Do not infer billing country, document jurisdiction, language, or data region solely from an IP address. A business may operate across several countries.

Validate one initial market, then add markets individually using this record. Test cross-border cases such as a buyer billed in one currency while producing quotations in another, users working in different time zones, and bilingual source documents. Publish only the combinations that the product actually supports.

## Recommended decision

Start with an **enquiry-to-quotation assistant for one distributor category** if you can access those buyers. Its first workflow can be limited to catalogue upload, enquiry input, item matching, quotation draft, and approval.

Choose the **invoice processing assistant** instead if your strongest contacts are accountants. Choose the **manual and troubleshooting assistant** if you can work with equipment service teams and obtain approved manuals.

Build and validate one product in an initial supported market before expanding across domains and countries. Reuse the technical foundation, while keeping each industry's workflow and each market's settings and quality checks explicit. International flexibility should be built into the design from the start; commercial availability should expand as markets are validated.
