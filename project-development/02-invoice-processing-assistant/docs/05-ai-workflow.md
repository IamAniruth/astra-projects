# Extraction, normalization and evaluation

Pipeline: validate -> parse/OCR -> classify document/pages -> extract structured candidates -> merge with provenance -> normalize -> deterministic checks -> duplicate/PO suggestions -> review -> approve -> export.

Invoice text is data, including embedded instructions. It cannot invoke tools, change system instructions or approve a document. Validate schemas, lengths, source references and candidate values before persistence. Truncation, conflicting candidates, missing evidence and exhausted budgets yield review or explicit failure.

Extract supplier identity, invoice number, issue/due dates, currency, PO references, descriptions/codes, quantities/units, unit prices, discounts, net/tax/gross and amount due where present. Preserve source strings. Do not infer currency from '$', date order from ambiguous dates, jurisdiction from supplier name or due dates from assumed payment terms.

Use decimal arithmetic and versioned reviewer-approved rounding rules. Distinguish line/header discounts, freight, tax-inclusive/exclusive values, withholding and prior payments. Retain both declared and computed totals; discrepancies become exceptions, not silent corrections. Unsupported calculation structures require manual handling. This plan provides no tax-law engine.

Exact hashes detect repeated bytes. Business duplicate suggestions use client-scoped supplier identity, invoice number, amount/currency and supporting date/context. Fuzzy matches never automatically delete, merge or suppress documents. PO comparisons require explicit tolerances, compatible units/currency and cumulative allocations across partial invoices. Concurrent approvals must protect allocations transactionally.

Corpus: synthetic edge cases plus permissioned real invoices, split by supplier/layout to avoid near-duplicate leakage. Cover poor scans, multi-page tables, missing/ambiguous fields, repeated headers, injection attempts, duplicates/non-duplicates, missing POs, partial invoices and arithmetic mismatches.

Before evaluation, S01/S02 register numeric thresholds and sample minimums with the domain reviewer. Report exact-match accuracy by critical field, line-item precision/recall, exception recall, duplicate precision/recall, false-positive rate with denominators, abstention, review time/correction rate, latency and cost per reviewed invoice. Break down by language/layout/scan quality. Thresholds are currently undecided; no result is claimed. S16 independently evaluates the actual release configuration.
