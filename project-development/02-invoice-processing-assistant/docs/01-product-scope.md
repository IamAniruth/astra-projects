# Product scope and discovery gates

Buyer hypothesis: accounting firms serving multiple client companies and finance teams entering supplier invoices. Validate one segment first. Interview preparers, reviewers and the budget owner; record invoice volumes, supplier/layout diversity, current import formats, review effort and recurring exception costs.

Journey: choose authorized client -> upload invoice/PO -> inspect processing -> review extracted fields beside source -> resolve duplicate/PO/totals exceptions -> approve immutable revision -> download reviewed export. Screens include client dashboard, upload batch, job detail, document review, exception queue, approval history, export history and settings.

Candidate input scope: native PDF and printed scanned PDF/JPEG/PNG in one supported language. S01/S02 qualify exact classes and limits. Handwriting, password-protected files, credit notes, receipts, statements, mixed-document bundles and cross-currency matching remain unsupported until separately qualified. Identify unsupported documents instead of treating every file as an invoice. Missing PO is a visible exception; three-way receipt matching is deferred.

S01 go/narrow/stop gate requires a reachable buyer, permitted samples, a domain reviewer, current-workflow baseline and provisional measurable success thresholds. S02 requires actual selected-checkpoint extraction results, feasible parsing/OCR and an authenticated integration design. Failure narrows scope, defers AI or stops the build. A manual-only prototype must be labelled accordingly.

Pilot questions: Does review become faster without more missed exceptions? Are duplicate alerts useful? Can reviewed exports be imported without retyping? Will a buyer pay enough to cover measured processing and support costs? Record negative findings too.

Initial commercial hypothesis, from the opportunity document: subscription with document allowances and optional onboarding fees. No price, demand level or return on investment is established by this plan.
