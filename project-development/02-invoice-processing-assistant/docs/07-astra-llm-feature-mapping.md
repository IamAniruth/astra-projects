# Astra reference and invoice dependencies

Requested reference: `astra-llm/codebase/command-documentation/7-PI/_STATUS.md` (absent). Resolved source: [7-PI_STATUS.md](../../../../astra-llm/codebase/command-documentation/7-PI_STATUS.md). Read: 1 October 2026. SHA-256: `41AADFC7F967AF2489D00089FEB18791F34D21FF5FE54316226DA92BD35D3DF7`.

Also inspected: [gateway manifest](../../../../astra-llm/codebase/docs/gateway/v1/client-manifest.json) and [release checklist](../../../../astra-llm/codebase/docs/platform-scaling/release-checklist.md). This is a local documentation assessment, not a code audit, platform test rerun or invoice benchmark.

The cumulative source includes superseded summary rows. Latest Sprint 190 follow-ups record local-cpu/local-cuda qualification on the development host, including locked Python 3.12 capacity evidence and gateway extras. Locked-environment measurement is no longer an open gap there. This does not qualify invoice extraction or production release: target-host/model, supervision, audit and listener posture dependencies remain in the checklist.

| ID | Upstream area | Invoice-specific work and limits | Product sprints |
|---|---|---|---|
| A01 | PI-16 / 037-038 document/context primitives | Qualify native parsing, OCR and source fidelity; no established invoice accuracy | S02, S04, S05, S07 |
| A02 | PI-27 / 102; PI-32 / 157; PI-37 / 185 gateway | Inspect schemas/errors and authenticate client identity; no assumed invoice extraction endpoint | S02, S03, S06, S07 |
| A03 | PI-32 / 158,160; PI-35 / 174; PI-37 / 184-186 execution | Qualify selected-path retries, budgets, cancellation and settlement; one owner per effect | S06, S13, S15, S16 |
| A04 | PI-11 / 027-028; PI-21 / 061-062 verification | Schema/evidence checks plus product decimal rules; gateway verification is not accounting correctness | S07, S08, S11, S16 |
| A05 | PI-17 / 044-045; PI-29 / 114-115 retrieval | Optional scoped candidates; deterministic supplier/invoice/PO keys first; no assumed trained embeddings | S09, S21 |
| A06 | PI-22 / 063-065; PI-36 / 175-177 artifacts | Product-approved CSV/JSON; artifact primitives do not establish accounting connectors | S12, S14, S21 |
| A07 | PI-21; PI-27 / 100-101; PI-35 / 171 security | Customer authentication, client isolation, parser containment and injection checks | S03-S07, S15, S18 |
| A08 | PI-08; PI-24 / 086; PI-25; PI-31 / 151-156 quality | Invoice corpus and served-checkpoint qualification, independent of platform badges | S01, S02, S16-S18 |
| A09 | PI-37 / 183-190 serving | Preserve local support evidence; qualify actual release host, supervision, audit and TLS | S02, S15, S16, S18 |
| A10 | PI-19/20/26; PI-34 / 167-170 improvement | Consented data, regression gates and reversible promotion; collection is not training evidence | S19, S20 |

Private native Astra remains the baseline; external fallback is not enabled. Invoice schemas, parser adapters, authorization and business checks are integration work. New authenticated wrapper operations require explicit contracts; do not silently route through legacy demo APIs.

Open dependencies: selected-checkpoint quality (S02/S16), scoped credentials (S03), parsing/OCR qualification (S05), recovery/budgets (S06), target-host controls (S15/S18). A manual prototype cannot satisfy AI release acceptance. No changes to Astra are performed by creating this plan.
