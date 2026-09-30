# Product scope and decisions

## Business outcome

A distributor converts a customer enquiry into a reviewed quotation using its own approved catalogue and prices. The AI proposes interpretations and matches; staff control product selection and approval. Calculations and permissions remain deterministic.

Initial industry suggestion: electrical distributors. Confirm buyer access and representative data in S01 rather than assuming this sector is final.

## Primary user journey

1. Owner creates a workspace and configures company identity, supported market, language, time zone, and document currency.
2. Staff import customers, catalogue items, and approved prices.
3. Salesperson pastes an enquiry or uploads a supported document.
4. A background job extracts requested products, quantities, units, and source references.
5. Staff correct extraction errors and select from candidate catalogue items.
6. The quote builder retrieves authoritative prices, calculates totals, and flags missing information.
7. An authorized approver approves a specific immutable revision.
8. Staff download a source-linked, branded PDF or CSV; optional email delivery requires a separate confirmation.
9. The company sees its usage and manages the subscription.

## Roles

| Role | Allowed scope |
|---|---|
| Owner | Workspace settings, billing, memberships, product administration, quote approval |
| Administrator | Operational configuration and data import; billing only if explicitly granted |
| Salesperson | Customers, enquiries, draft quotations, submit for approval |
| Approver | Review, reject, and approve quote revisions under the workspace policy |
| Viewer | Read authorized records and download allowed outputs |
| Platform operator | Operational support through a distinct audited admin path, without default unrestricted customer document access |

One person may hold multiple roles. For a small pilot, owner and salesperson are enough to demonstrate the separation; approval permissions must still be enforced by the server.

## Release boundaries

Initial release includes CSV catalogue imports, manually entered customers, pasted text, digital PDF and selected image uploads, reviewed extraction/matching, one currency per quote, explicit tax settings, versioned quotations, approval, exports, basic recurring billing through one eligible provider, customer support, and one validated market/language.

Scanned documents require the selected OCR adapter. If OCR quality is inadequate, mark scanning unsupported and provide manual entry; do not silently process bad output.

Defer ERP synchronization, public API resale, automatic outbound messaging, autonomous substitutions, live foreign-exchange conversion, inventory reservation, purchase ordering, payment collection on quotations, and worldwide tax automation. The customer pays for the software subscription; its buyer does not pay for goods through this initial product.

Stock is an informational snapshot with a timestamp, not a promise or reservation. Quote expiry, lead-time wording, and availability require business confirmation.

## Acceptance example

Given two companies with overlapping SKUs, a salesperson in company A uploads an enquiry for company A. They can only retrieve A's catalogue and prices. They review a unit ambiguity, prepare a quote, and submit it. An approver approves revision 2. Exported totals match revision 2 exactly. A later edit creates revision 3 and removes approval for that revision.

## Measurement

Baseline and measure time from enquiry receipt to reviewed quote; correct extraction fields; product-match top-3 coverage; staff edits; pricing correctness; completed quotes; onboarding effort; support cost. AI accuracy targets in the quality plan are proposed pilot gates and must be approved with the sample dataset before evaluating.

## Discovery deliverables

S01 produces a buyer profile, interview notes, sample-data permissions, a workflow map, unsupported cases, first market/language choice, baseline timing, and a pilot success agreement. Unknown facts remain marked unknown.

