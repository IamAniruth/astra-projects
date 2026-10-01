# Astra reference and manual-assistant dependencies

Requested reference from the project series: `astra-llm/codebase/command-documentation/7-PI/_STATUS.md` (absent). Resolved source: [7-PI_STATUS.md](../../../../astra-llm/codebase/command-documentation/7-PI_STATUS.md). Read: 1 October 2026. SHA-256: `D2D3FEF52DC61517A26E1ED1723F6DE4EC0D76761335996CFDD807E3307CF8F9`.

Also inspected: [gateway manifest](../../../../astra-llm/codebase/docs/gateway/v1/client-manifest.json) and [release checklist](../../../../astra-llm/codebase/docs/platform-scaling/release-checklist.md). The source changed since project 02 was prepared; this plan records its own snapshot. This is a documentation assessment, not a code audit or test rerun.

PI-36 records integrated permissioned retrieval/context mechanisms, while its later follow-up still describes asserted principal identity, context-local deletion, lexical limitations and unreviewed evaluation fixtures. Product authentication, authoritative-store deletion and independent downstream answer evaluation remain necessary. Do not copy an early summary's missing integration as though later integration never occurred; likewise do not treat integrated fixtures as field qualification.

Sprint 190 and the release checklist record local-cpu/local-cuda development-host qualification, including locked-environment evidence. They retain production-host, served-model, supervision, audit and listener requirements. Local support is neither universal production support nor evidence of troubleshooting answer quality.

| ID | Upstream evidence area | Product adaptation and limits | MT sprints |
|---|---|---|---|
| A01 | PI-16 / 037-038 document/context | Qualify parsing/OCR, page labels, procedure boundaries and cross-page prerequisites | S02, S04, S05 |
| A02 | PI-17 / 044-045; PI-29 / 114-115; PI-36 / 180,182 and integration follow-ups | Approved/applicable retrieval; lexical baseline and independent relevance labels; no assumed semantic quality | S02, S06, S07, S16 |
| A03 | PI-36 / 181 verified compression and follow-ups | Preserve warnings, units, conditions and ordering; do not enable unqualified generative compression | S05, S08, S09, S16 |
| A04 | PI-11 / 027-028; PI-21 / 061-062; PI-36 / 179 | Citation and claim checks require manual-domain evidence; verification badges are not procedural correctness | S08-S10, S16 |
| A05 | PI-27 / 102; PI-32 / 157; PI-37 / 185 gateway | Authenticated scoped adapter; inspect actual schemas; no assumed manual-question or source-approval endpoint | S02, S03, S08 |
| A06 | PI-32 / 158,160; PI-35 / 174; PI-37 / 184-186 jobs/budgets | One owner per effect, cancellation and unknown-outcome reconciliation | S06, S08, S13, S15 |
| A07 | PI-21; PI-27 / 100-101; PI-36 governance/sync follow-ups | Product authenticates principal and enforces source lifecycle; deletion extends beyond context-local indexes | S03, S04, S06, S12, S15 |
| A08 | PI-08; PI-24 / 086; PI-25; PI-31 / 151-156 | Independent approved-manual corpus, domain-reviewed labels and selected checkpoint qualification | S01, S02, S14, S16-S18 |
| A09 | PI-37 / 183-190 serving | Actual release host/model/corpus qualification, supervision, audit and TLS | S02, S15, S16, S18 |
| A10 | PI-19/20/26; PI-34 / 167-170 improvement | Consented, versioned feedback and reversible evaluated changes; expert replies are not automatic training/publishing | S19, S20 |

The manifest includes general chat/generate, embeddings, tools, jobs and evaluation operations. It does not establish a complete approved-manual workflow. Define new authenticated adapters/wrappers explicitly and keep legacy demo routes private.

No external provider fallback is selected. Product ownership includes approval, asset applicability and source freshness even if Astra hosts retrieval. Open release dependencies: actual checkpoint support/citation quality, authenticated principal mapping, corpus withdrawal propagation, chosen-path budgets/recovery and target-host controls. Search-only fallback remains labelled separately from synthesized-answer readiness.
