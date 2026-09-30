# Project Shortlist: Recurring-Revenue Software

Updated: September 26, 2026

## Current Direction

The founder currently has no customer contacts and wants to sell software to pharmacies or clinics. The earlier service-business booking idea remains an option. In both cases, the business being built is a software company; customers operate the pharmacy, clinic, or service business.

The comparisons and prices below are proposals for customer validation, not measured market rankings or revenue forecasts. India is used as a working market assumption for pricing, subject to confirmation.

## Retained Option: Service-Business Enquiry and Booking Assistant

- **Buyer:** AC installation and maintenance companies with regular inbound enquiries.
- **Workflow:** Capture enquiries, answer approved questions, check service areas, arrange appointments, follow up, and track completed jobs.
- **Initial scope:** One industry, one city, one communication channel, and one scheduling integration.
- **Previous pricing hypothesis:** INR 5,000 per business per month with a defined usage allowance.
- **Evidence:** [Jobber](https://help.getjobber.com/en/articles/receptionistpowered-by-jobber-ai/) supplies AI answering and booking; [Interakt](https://www.interakt.shop/whatsapp-chatbot/) supplies WhatsApp automation and lead qualification. This establishes competition and feature availability, not local willingness to pay.
- **Validation:** Three paid pilots followed by renewal decisions based on useful bookings and customer economics.

## Healthcare Software Candidates

| Candidate | Paying buyer | Proposed recurring value | Main implementation dependency |
| --- | --- | --- | --- |
| Pharmacy inventory and purchasing assistant | Pharmacy owners, especially small chains | Less purchase preparation, visibility into stock risks, follow-through on returns | Reliable batch, stock, purchase, sales, and supplier data |
| Clinic reception and appointment assistant | Clinic owner or administrator | Less booking administration, consistent reminders, easier rescheduling | Access to the clinic's calendar and approved administrative information |
| Diagnostic-lab coordination software | Lab owner or operations manager | Clear sample status, report-ready communication, fewer coordination calls | Integration with the laboratory information system and verified report workflow |
| Medical-supply distributor order assistant | Distributor owner or sales manager | Faster order capture, catalogue matching, stock and quote preparation | Accurate catalogue, customer terms, and inventory integration |

The fourth candidate is an adjacent idea to investigate; its demand has not been established in this research.

## Preferred Pharmacy Hypothesis

**A pharmacy inventory and purchasing assistant that works alongside the existing billing system.** Start by interviewing owners of independent pharmacies and small chains; choose a specific group only after confirming a repeated unmet problem.

Proposed first workflow:

1. Import supported stock, sales, and purchase exports from one existing system.
2. Extract supplier invoice fields with AI, matching products to the store's catalogue for staff review.
3. Build a daily action list for low stock, ageing stock, approaching expiry, and pending supplier returns.
4. Prepare a purchase-list draft using sales history, stock on hand, pack sizes, and supplier terms.
5. Let the owner approve the list and track subsequent purchasing and returns.

Use deterministic calculations for quantities, dates, prices, and totals. AI can assist with extraction, catalogue matching, summaries, and questions about the data. Add demand forecasting when sufficient history exists and its performance has been measured against a simple baseline.

Supported exports are the initial integration method, not a promise of live inventory. Show when each dataset was refreshed. Keep medicine selection, substitutions, prescription decisions, and dispensing with qualified pharmacy staff.

### Competition and Differentiation

[Marg](https://margcompusoft.com/pharmacy-software.html) already provides pharmacy billing, batch tracking, inventory, and expiry management. [Gofrugal's pharmacy case study](https://www.gofrugal.com/customers/sarumam-pharmacy.html) describes AI reordering and expiry controls. Basic alerts or a chat interface alone are therefore weak differentiation.

Possible gaps to investigate include supplier-return follow-through, purchase-list preparation across branches, invoice exceptions, and a daily action list that owners actually use. These gaps must be confirmed with customers rather than assumed to be absent from existing products.

### Commercial Experiment

- Test a monthly subscription of **INR 2,000-3,000 per location** for a narrow add-on, with any setup work quoted separately. This is a pricing hypothesis, not a market benchmark.
- A multi-location owner can buy for several branches through one contract, but may require more integration and support.
- Illustrative arithmetic: 100 locations at INR 2,500 per month produce INR 250,000 in monthly subscription revenue before operating costs. This does not predict acquisition, retention, or profit.
- Measure purchase-preparation time, corrections, stockout events, return completion, and customer support effort. Validate financial savings against the customer's records.

## Clinic Alternative

If pharmacy data access makes the first pilot impractical, investigate an administrative clinic assistant: appointment booking, rescheduling, queue updates, reminders, and staff handoff.

Keep its initial scope administrative. Medical advice and treatment decisions remain with clinicians. Test demand for a specific clinic type before choosing features.

This category also has established competition. [Eka's practice-management plans](https://product.eka.care/practice-management/plan-pricing) include clinic workflows, and [its conversational platform](https://www.eka.care/s/ekaagents) offers appointment-related AI capabilities. [CrelioHealth](https://creliohealth.com/in/lab-software/lims-pricing/) provides a reference for the separate laboratory software category. These vendor pages establish current offerings, not guaranteed customer demand for a new entrant.

## Next Decision

Interview 10 pharmacy owners and 5 clinic administrators. Ask what software they already use, which daily task still requires manual work, what data can be exported, and whether they will pay to fix that task. Use de-identified sample data for early demonstrations.

Choose the workflow that produces three paid pilot commitments and has accessible data. Build one complete workflow, then use renewals and measured support costs to decide whether to expand.
