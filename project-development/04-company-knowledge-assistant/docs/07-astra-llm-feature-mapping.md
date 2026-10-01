# Astra reference and company-knowledge dependencies

Resolved source: [7-PI_STATUS.md](../../../../astra-llm/codebase/command-documentation/7-PI_STATUS.md). The original project-series path `7-PI/_STATUS.md` is absent. Read: 1 October 2026. SHA-256: `D2D3FEF52DC61517A26E1ED1723F6DE4EC0D76761335996CFDD807E3307CF8F9`.

Supporting sources: [gateway manifest](../../../../astra-llm/codebase/docs/gateway/v1/client-manifest.json) and [release checklist](../../../../astra-llm/codebase/docs/platform-scaling/release-checklist.md). The status hash matches the project 03 snapshot reviewed in this session. This is a documentation assessment, not a code audit, benchmark or platform test rerun.

PI-36 follow-ups report integrated permissioned retrieval/context mechanisms, but asserted identity, context-local deletion, lexical limitations and unreviewed fixtures remain explicit boundaries. Product authentication, authoritative-source lifecycle and independent downstream evaluation are still necessary. Do not treat an early missing-integration summary as the current state, or later integrated fixtures as production knowledge quality.

The Sprint 190 checklist records local-cpu/local-cuda qualification on the development host with locked-environment evidence. Actual production-host/model, supervision, durable audit and listener requirements remain open. Preserve that distinction.

| ID | Upstream area | Company-knowledge adaptation and limits | CK sprints |
|---|---|---|---|
| A01 | PI-16 / 037-038 document/context | Qualify PDF/DOCX/text parsing, locators and preservation of policy exceptions | S02, S04, S05 |
| A02 | PI-17 / 044-045; PI-29 / 114-115; PI-36 / 180,182 and follow-ups | Authorized retrieval before scoring/prompting; independent relevance labels; no assumed semantic quality | S02, S06, S07, S16 |
| A03 | PI-36 / 181 compression and follow-ups | Preserve effective dates, obligations, exceptions and negation; unqualified compression stays disabled | S05, S08, S09, S16 |
| A04 | PI-11 / 027-028; PI-21 / 061-062; PI-36 / 179 | Claim/citation checks plus independent policy-support review; verified does not mean authoritative | S08, S09, S16 |
| A05 | PI-27 / 102; PI-32 / 157; PI-37 / 185 gateway | Authenticated product principal and scoped adapter; no assumed company-search/publication endpoint | S02, S03, S08 |
| A06 | PI-32 / 158,160; PI-35 / 174; PI-37 / 184-186 jobs | One owner per effect, budgets, cancellation and reconciliation | S06, S08, S13, S15 |
| A07 | PI-21; PI-27 / 100-101; PI-36 governance/sync | Real identity, source/group revocation, private histories and deletion beyond context-local stores | S03, S04, S06, S10-S12, S15 |
| A08 | PI-08; PI-24 / 086; PI-25; PI-31 / 151-156 quality | Reviewer-labelled internal-question corpus and release-checkpoint qualification | S01, S02, S14, S16-S18 |
| A09 | PI-37 / 183-190 serving | Qualify actual host/model/corpus and operational controls | S02, S15, S16, S18 |
| A10 | PI-19/20/26; PI-34 / 167-170 improvement | Permissioned feedback and reversible evaluated improvement; questions are not automatic training data | S19, S20 |

The manifest provides general chat/generate, embeddings, tools, jobs and evaluation operations, not a complete knowledge publication/ACL workflow. New adapters and wrappers are explicit integration tasks. Product approval and authoritative access checks remain product responsibilities even when Astra hosts retrieval.

Native private Astra remains the baseline. No external paid-model fallback or connector is enabled. Open gates include selected-checkpoint support quality, proven caller identity, publication/group revocation through caches/history, protected gap analytics, chosen-path budgets/recovery and target-host release controls.
