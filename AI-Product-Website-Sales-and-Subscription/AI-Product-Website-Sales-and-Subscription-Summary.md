# Selling Your AI Application Through a Website

Prepared: 30 September 2026  
Status: Business and product planning summary; no website or payment system has been deployed.  
Companion: [AI Product Opportunities 2026-2030](../AI-Product-Opportunities-2026-2030.md)

Delivery plan added 4 October 2026: [combined website and admin roadmap](PI/README.md), [18-sprint status](_STATUS.md) and [source coverage](docs/01-module-feature-sprint-matrix.md). All implementation remains Planned.

## 1. Executive summary

Build an internationally adaptable website where customers in supported markets can understand your AI product, see a demonstration, choose an offer, pay, and access their own application workspace.

The recommended initial business model is **a setup fee plus a monthly subscription with a defined usage allowance**. This suits business customers who need help importing documents, catalogues, or other information. Once onboarding becomes simple, offer direct online signup and payment.

Launch one product for one customer group first. For example, sell an enquiry-to-quotation assistant to electrical distributors. The same sales and account foundation can support invoice processing or document assistants later.

Your local LLM runs behind the application. Customers use a browser and do not need to install the model. The website, business application, billing service, and model hosting are separate components, even if they appear as one service to the customer.

This plan assumes a business-to-business application that can expand across countries. The final product, seller's business location, initial customer markets, supported languages and currencies, budget, model, hardware, and payment providers remain undecided. Prices and capacity must be validated before publication. Use one shared website and application with configurable market support; do not claim availability in all countries before validating it. See section 13 for international sales and hosting requirements.

## 2. Ways to sell the application

| Model | What the customer buys | Suitable situation | Recommendation |
|---|---|---|---|
| Monthly subscription | Continued access with defined features and usage | Recurring business workflows | Start here |
| Setup fee plus subscription | Data import and onboarding, followed by ongoing access | Products needing catalogues, document setup, or configuration | Best initial offer for the shortlisted business products |
| Annual subscription | A year of access under stated terms | Customers already confident in the product | Add after pilot validation |
| Usage packs | A defined number of documents, jobs, or audio minutes | Irregular or seasonal usage | Add if customer demand supports it |
| Paid pilot | A limited evaluation with an agreed scope and success measures | First customers needing proof before commitment | Use for the initial launch |
| Private installation | Deployment on the customer's infrastructure, with support and updates | Customers requiring their own hosting | Offer as a separately quoted service |
| One-time software license | A defined software version and license scope | Downloadable or customer-hosted software | Specify hosting, updates, and support separately |

A one-time purchase should not silently include indefinite hosted AI processing: processing and support continue to cost money. Likewise, unlimited usage should not be promised before capacity and economics are understood.

## 3. What the customer sees

The service has three areas:

1. **Public website:** Explains the problem, product, benefits, examples, pricing, and how to start.
2. **Customer application:** Provides the actual workflow, saved results, team access, usage, and billing management after login.
3. **Owner administration:** Lets you manage customer onboarding, billing status, support, job failures, and service health.

An illustrative address structure is `yourbrand.com` for the public website and `app.yourbrand.com` for the application. These are placeholders; a single domain with separate paths also works.

### Essential website pages

| Page | Purpose | Main customer action |
|---|---|---|
| Home | State who the product helps and the result it delivers | View demo or request a pilot |
| Product | Show the workflow, supported inputs, outputs, and limitations | Try an example |
| Pricing | Explain plans, billing period, allowances, setup fees, and extra charges | Select a plan or request a quote |
| Demo | Show a short video or interactive example using sample data | Book a demonstration or start |
| About / Contact | Explain who operates the service and how to reach support | Contact the business |
| FAQ / Help | Explain setup, supported files, data handling, and billing | Resolve a question |
| Terms / Privacy / Billing policies | Explain service terms, data practices, cancellation, and refunds | Review before purchasing |
| Login / Signup | Provide account access and recovery | Enter the application |

Policy content must describe your actual service and selling locations. This document does not determine jurisdiction-specific legal or tax requirements.

### Example positioning for the quotation product

**Headline:** Turn customer enquiries into review-ready quotations.

**Explanation:** Upload your product catalogue, add a customer enquiry, review suggested product matches, and export a quotation using your approved prices.

**Initial action:** Request a paid pilot.

Use a real sample workflow and measured results as they become available. Do not publish invented customer logos, testimonials, savings percentages, or response-time promises.

## 4. Customer purchase and onboarding flow

```text
Visit website
      |
View product example and offer
      |
Choose a pilot or subscription
      |
Create account and business workspace
      |
Complete secure provider checkout
      |
Backend verifies billing status and enables access
      |
Upload data or complete assisted setup
      |
Complete first useful task and review the result
      |
Continue using the product; manage usage and subscription
```

For the first customers, assisted onboarding is appropriate: agree the scope, collect payment through a configured provider, help import data, and verify the first result. Self-service onboarding can follow when those steps are repeatable.

The customer should always be able to find their current plan, usage, renewal information, invoices, cancellation controls, and support contact.

## 5. Suggested plan structure

This is a proposed packaging structure, not a published price list. Avoid offering every plan at launch; a paid pilot and one standard plan may be sufficient.

| Offer | Intended customer | Included value | Commercial structure |
|---|---|---|---|
| Paid pilot | First-time buyer evaluating fit | Defined workflow, limited usage, assisted setup, results review | Fixed fee and agreed duration |
| Starter | Small business with routine needs | One product, small team allowance, standard exports and support | Monthly subscription |
| Business | Team with greater volume | Higher allowance, more seats, shared workflows, selected integrations | Higher monthly or annual subscription |
| Private deployment | Business needing its own environment | Installation, configuration, agreed maintenance and support | Quoted setup and recurring support fees |

Choose a usage unit customers understand:

- Quotation assistant: processed enquiries or quotation jobs.
- Invoice assistant: processed documents, with defined page limits.
- Knowledge assistant: questions plus document-storage allowances.
- Transcription product: audio minutes.

Define what counts as one job, the treatment of retries and failures, allowance resets, and whether unused usage expires. Track model tokens internally if useful, but show customer-facing units that match the work being purchased.

Warn customers before reaching their allowance. Initially pause new jobs or offer an explicit upgrade/top-up; enable automatic overage charges only with clearly agreed terms. Set prices after measuring delivery costs and discussing value with buyers.

## 6. Payments and subscription management

Use a payment provider's supported checkout to collect payment information. Your application stores customer, plan, subscription, invoice-reference, and access records; it should not collect raw card details itself.

Stripe and Razorpay are examples to evaluate, not a final provider selection or evidence of worldwide coverage. Confirm support for your seller business location, customer locations, currencies, recurring payment methods, and account approval before choosing. Provider fees and eligibility are not assumed here. Keep the billing integration replaceable so a supported regional provider can be added without rewriting the product.

Payment confirmation must happen on the server. A browser redirect to a success page alone is not sufficient evidence of payment.

Providers send **webhooks**, which are automatic server notifications about payments and subscription changes. Stripe documents handling subscription changes, payment failures, and verified incoming events. Razorpay documents recurring subscription payment flows. [Stripe subscription webhooks](https://docs.stripe.com/billing/subscriptions/webhooks), [Razorpay subscriptions](https://razorpay.com/docs/payments/subscriptions/)

### Proposed access policy

| Situation | Application behavior |
|---|---|
| Checkout incomplete or awaiting confirmation | Show payment status; do not grant paid access solely from a browser response |
| Valid trial, if offered | Grant only the trial features and usage allowance |
| Payment confirmed and subscription eligible | Activate the purchased features and limits |
| Renewal succeeds | Continue access and apply the plan's allowance-reset rules |
| Renewal fails | Notify the customer and apply the clearly stated grace-period policy |
| Customer cancels at period end | Keep paid access until the confirmed end date, then stop renewal and paid processing |
| Subscription ends | Disable paid processing; offer data export or read-only access according to the stated policy |
| Refund or dispute occurs | Reconcile billing and access against the applicable policy; do not assume one automatically updates the other |

The implementation should verify webhook signatures, handle repeated events without duplicate effects, reconcile current provider state when events arrive out of order, and periodically check for missed updates. Feature access and quotas belong in backend checks, including when queued jobs start.

## 7. Hosting the website and local LLM

Hosting a marketing website does not automatically host an AI model. Ordinary website hosting and GPU-based model processing have different requirements.

```text
Customer browser
      |
      v
Public website and authenticated application
      |
      v
Backend: accounts, company access, subscriptions, quotas
      |                 |                  |
      v                 v                  v
Database and files   Payment provider    Job queue
                                           |
                                           v
                                   Private model server
                                           |
                                           v
                                   Saved, reviewed result
```

| Stage | Website and application | Model location | Condition for use |
|---|---|---|---|
| Development | Local development environment | Your existing machine | Suitable for building and testing |
| Controlled pilot | Hosted website and backend | Your machine through a secured private connection, or a dedicated server | Agree pilot availability and measure capacity |
| Public paid service | Monitored hosted application | Dedicated owned or rented inference infrastructure | Reliable operation, tested capacity, backups, and recovery procedures |
| Private customer installation | Customer-specific deployment | Customer-controlled infrastructure | Defined installation and support responsibilities |

Keep the raw model endpoint private and put authentication, quotas, and access checks in the backend. Company data must be separated in database queries, file access, document retrieval, and job processing.

If a pilot relies on your personal computer, sleeping, restarting, or losing internet can interrupt AI work. A public paid service needs an operating plan for these failures. No hardware capacity or monthly hosting cost is estimated until the actual model and workload are known.

## 8. Minimum application features to sell a useful first version

### Customer workspace

- Account creation, login, and recovery.
- One complete product workflow, such as enquiry upload through quotation export.
- Input validation and clear supported-file limits.
- Job progress, saved results, and a review/correction screen.
- Current plan, remaining usage, and billing management.
- Simple onboarding instructions and support access.

### Owner administration

- Customer and workspace management with restricted administrative access.
- Plan, payment, and subscription visibility.
- Usage and processing-cost visibility.
- Failed-job review and controlled retry tools.
- Service monitoring and support tracking.

Add team roles when required by the initial buyers. Delay a large multi-product catalogue, complex bundles, and advanced integrations until customers validate the main workflow.

## 9. Launch and sales approach

| Phase | Deliverable | Evidence needed to proceed |
|---|---|---|
| Define the offer | One buyer group, one workflow, sample demo, pilot terms | Buyers recognize the problem and agree to evaluate it |
| Publish the sales website | Product explanation, demo, contact, offer, and relevant policies | Visitors understand the value and next step |
| Run paid pilots | Working application, payment collection, assisted onboarding | Customers complete useful tasks with acceptable review effort |
| Launch subscriptions | Reliable billing, usage limits, cancellation, support, and monitoring | Buyers want ongoing use and costs are sustainable |
| Expand | Self-service onboarding and selected integrations | Repeated customer demand and operating capacity |

The website is where customers evaluate and buy; it does not create demand by itself. Start with demonstrations to reachable businesses, industry contacts, and relevant partners. Build useful product-specific content and publish genuine case studies with customer permission. Consider advertising after you can measure conversion and retention.

## 10. Costs and business measures

Budget for the domain, website/backend hosting, model compute, database and file storage, backups, payment processing, transactional email, optional OCR or speech services, onboarding, support, and maintenance.

Track:

- Website visitors who become qualified enquiries or signups.
- Customers who complete their first useful task.
- Pilot-to-subscription conversion and renewal rates.
- Revenue collected and recurring revenue, separately from setup fees.
- Processing cost and support effort per customer.
- Successful-job rate, correction rate, and response time under real load.

For planning, monthly contribution is subscription revenue minus the costs of delivering and supporting that customer. Full profitability also depends on fixed costs, customer acquisition, and other business expenses. Do not choose a price based only on the absence of an external LLM API bill.

## 11. Launch readiness checks

Before taking general public subscriptions, demonstrate that:

1. A new customer can pay, receive the right access, and complete the core workflow.
2. Payment failures, duplicate notifications, cancellation, renewal, and plan changes produce the intended access and charges.
3. One company cannot access another company's documents or results.
4. Usage limits, failed jobs, refunds, exports, and data deletion follow the published policies.
5. Backups can be restored and model downtime is visible to the operator and customer.
6. The chosen model and components permit the intended commercial deployment.
7. Actual processing speed and cost support the published offer.
8. Each enabled market has tested language, formatting, checkout, renewal, cancellation, support, and data-location arrangements as described in section 13.

## 12. Recommended initial version

Launch a focused website selling **one AI business application**, with a short demonstration and a paid-pilot offer. Use **setup plus a monthly subscription** when customer data needs configuration. Provide secure checkout, a private workspace, the complete core workflow, usage visibility, and cancellation support.

For the quotation assistant, the end-to-end promise is:

> A business signs up, pays for an agreed offer, imports its catalogue, submits an enquiry, reviews product matches, and exports a quotation using its own approved prices.

Final decisions before implementation: chosen product and customer group; seller location and initial customer markets; supported languages and billing currencies; model and hardware; hosting regions and budget; payment-provider eligibility; pilot scope; prices and allowances; and support availability.

## 13. International website, billing, and hosting design

### International by design, available market by market

The website can present a global brand while selling only in markets you currently support. Keep one shared product and configurable market settings. Add countries as payment, product quality, operational, and applicable local requirements are validated.

For an unsupported market, explain availability and provide a contact or waitlist option instead of accepting payment for a service you cannot deliver. Geographic reach of the website is not the same as payment eligibility or product readiness.

### Customer and market settings

| Setting | Required behavior |
|---|---|
| Seller entity | Record which business sells the service and receives payment |
| Customer business and billing country | Collect explicitly and use for the applicable checkout and billing process |
| Interface language | Allow the user to select a supported language; do not force it based on country |
| Locale and time zone | Display regional formats and deadlines correctly; account for users in different time zones |
| Billing currency | Show the actual charge currency, amount, billing period, and applicable charges before purchase |
| Product document currency | Configure separately; a customer's quotations may use a different currency from their subscription |
| Market offer | Keep regional prices, allowances, available features, and provider mappings explicit and versioned |
| Hosting region | Offer only verified processing locations, with limitations explained accurately |
| Support | Publish actual languages, support hours, and expected response arrangements |

Use flexible international names, addresses, and phone fields. Support Unicode and, for relevant languages, right-to-left layout and appropriate fonts. Translate the whole purchase journey, including checkout explanations, billing notifications, help, and cancellation screens, rather than only the home page.

### Pricing and payment strategy

Start with a small number of supported currencies and payment methods. Expand based on actual buyer needs and provider eligibility. Do not display a converted estimate as though it were the final charge amount.

Maintain internal plan and subscription records independently of a provider's identifiers. Map each supported market's offer to the appropriate provider price or plan. Keep payment events and customer access consistent if you later add another provider; do not create duplicate active subscriptions during migrations.

For each market, validate seller onboarding, payment methods, recurring-payment support, customer authentication, settlement, refunds, disputes, fees, and renewal behavior using current provider documentation. Provider availability can change and must be checked during implementation.

A merchant-of-record arrangement may be another option to evaluate where eligible. Clarify contractually who is the seller and which billing, tax, refund, and customer-service responsibilities each party accepts; do not assume all responsibilities transfer. This document selects neither that model nor a provider.

Determine applicable invoicing, tax, privacy, consumer or business subscription, and refund requirements for the actual seller/customer arrangement before enabling a market. These are market-validation tasks, not a claim that one universal policy satisfies every country.

### Hosting and AI quality

Record where customer files, database records, document indexes, inference, logs, and backups are processed or stored, including relevant third-party services and administrative access. Routing customer data to a model on your own computer still makes that computer's location part of the data flow.

Regional hosting requires the complete data path to match the stated commitment. Do not promise that data stays in a country if inference, backups, telemetry, or another component sends it elsewhere. Keep any region-specific infrastructure choices separate from language and currency preferences.

Measure latency from target markets and test the model on representative regional language and document examples. Offer a language or workflow only when its quality meets your stated acceptance criteria. A worldwide signup page alone does not make a local LLM suitable for every language.

### International rollout and acceptance checks

| Stage | Scope | Evidence before expansion |
|---|---|---|
| Initial launch | One validated market, narrow buyer group, explicit language and currency support | Successful paid workflow, renewals, support, and acceptable operating cost |
| Next market | One additional market using the same product foundation | Local buyer validation, quality testing, eligible payments, reviewed regional terms, and support readiness |
| Broader availability | Further validated markets and selected regional deployments | Repeatable onboarding, reliable provider operations, and sustainable support and infrastructure |

Test at least these scenarios before enabling each new market:

1. Signup, checkout, payment confirmation, renewal, payment failure, cancellation, and refund handling with the supported provider configuration.
2. Localized amounts and formats, including currencies with different decimal conventions and ambiguous date inputs.
3. A user language different from their business country, and a document currency different from billing currency.
4. Time-zone changes, daylight-saving transitions where relevant, and clear billing-period boundaries.
5. Representative regional documents, international characters, relevant layout direction, and verified AI output quality.
6. Accurate processing-location statements, company-data separation, exports, and deletion behavior.
7. Clear handling of unsupported country/language/payment combinations without taking an unintended payment.

The resulting promise is **one product designed for international expansion, with clearly published supported markets**. Both this sales plan and the companion product document use that scope.
