# AI workflow and evaluation

## Processing sequence

1. Authenticate and authorize the enquiry request; reserve usage with the durable job.
2. Validate uploaded file size, detected type, checksum, page count, and parser limits.
3. Extract text and page/line provenance using a sandboxed parser. Invoke OCR only for supported scans.
4. Treat the document as untrusted content. Extract to a constrained schema using the local model adapter.
5. Validate schema, units, numeric strings, source references, and input correspondence. Missing values remain missing.
6. Retrieve candidate products from the same workspace using exact SKU/alias matches, then lexical search and optional semantic retrieval.
7. Rank candidates; display reasons, differences, and source passages. Never accept invented product IDs.
8. Staff correct the extracted requirements and confirm product selections.
9. Fetch authoritative price entries and pass reviewed lines to deterministic quotation logic.

Implement exact/lexical matching first. Introduce embeddings only if a held-out evaluation shows a useful improvement. A separate vector database is unnecessary initially; evaluate PostgreSQL-based options if needed later.

## Extraction contract

Suggested output: source language, customer reference if present, requested delivery text, and line items containing source reference, raw description, quantity as a decimal string or null, unit or null, supplied SKU or null, and requested attributes. Validation disallows arbitrary tools, URLs to fetch, database queries, or hidden instructions.

The model must not invent prices, current stock, tax rates, or delivery promises. Do not rely on a model-generated confidence number as a calibrated probability. Missing or conflicting values go to review.

## Adapter contract

Expose a server-only interface such as `extractEnquiry(input, schema, timeout, cancellation)`. Implement it against the private Astra versioned gateway and inspected schemas; an extraction-specific wrapper may be new integration work. Start with a deterministic mock for application tests, then qualify the actual Astra checkpoint in S08/S17. Do not replace Astra with Ollama or enable an external paid-provider fallback implicitly. See [capability mapping A01-A15](11-astra-llm-feature-mapping.md).

Record model ID/digest where available, prompt version, schema version, generation settings, processing duration, input size, output validation results, and correction outcome. Avoid storing sensitive full prompts in ordinary logs.

## Failure and retry policy

- Model unavailable: show queued/unavailable status, bounded retries, then manual-entry option.
- Invalid structured response: at most one controlled repair attempt initially; otherwise fail visibly for review.
- Oversized input: split with tracked source references within evaluated limits or reject with guidance.
- Missing product: show unmatched; never choose an unrelated product merely to complete the quote.
- Conflicting units/specifications: block approval until reviewed.
- Cancellation/retry: do not consume duplicate usage or commit partial reviewed lines.
- Content requesting data access or external actions: treat as source text; extraction has no tool permissions.

## Evaluation dataset

Create a permitted, versioned dataset of enquiries paired with expert-reviewed line items and catalogue matches. Include exact SKUs, misspellings, similar variants, mixed units, missing quantities, no-match cases, multilingual examples for enabled languages, noisy scans, and prompt-injection-like text. Keep a held-out set separate from prompt tuning.

Proposed pilot gates: at least 95% correctness for required extraction fields on the supported clean-text set; at least 90% top-3 coverage of the correct match for supported matchable requests; all ambiguous/no-match fixtures must remain reviewable; zero cross-workspace retrieval and zero AI-sourced authoritative prices. These are targets to negotiate and measure, not achieved metrics. Report sample count, failure categories, and results by language/input type. Do not hide poor OCR performance inside a combined average.

Measure cold/warm latency, memory, timeouts, queue wait, and maximum sustainable concurrency on actual hardware. Start worker concurrency at one; increase only after measurement. Model changes require evaluation and rollback readiness. Upstream gateway verification checks are not evidence of complete factual correctness; local hash retrieval is not a qualified neural embedding model. PI-07 tracks consented corrections, lineage, evaluation and reversible candidate release separately from ordinary business data updates.

