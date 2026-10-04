# Astra LLM reference and product feature mapping

## Source identification

Requested path: `D:\tool\AI-workspace\astra-llm\codebase\command-documentation\7-PI\_STATUS.md` (not present).  
Resolved existing source: [7-PI_STATUS.md](../../../../astra-llm/codebase/command-documentation/7-PI_STATUS.md).  
Read date: 30 September 2026.  
Source SHA-256: `B3C1C92FDFC595570CD7CA47CC6C500E18477F8286217B21C6B71FDAA5E6EF49`.  
Repository HEAD observed: `8110f27d91e3a056f35bdb53c61e7c287fe714c7`; this is provenance, not a claim the working tree exactly matches it.

Also read: [gateway client manifest](../../../../astra-llm/codebase/docs/gateway/v1/client-manifest.json), [supported-profile release checklist](../../../../astra-llm/codebase/docs/platform-scaling/release-checklist.md), [PI-32 plan](../../../../astra-llm/astra-llm-roadmap/pis/PI-32-live-agent-runtime/README.md), [Sprint 157 plan](../../../../astra-llm/astra-llm-roadmap/pis/PI-32-live-agent-runtime/157-live-versioned-gateway/technical-approach.md), and [PI-36 plan](../../../../astra-llm/astra-llm-roadmap/pis/PI-36-professional-workflow-completeness/README.md).

## Evidence interpretation

This is a documentation-based dependency assessment, not a fresh audit or rerun of Astra's tests. The status file is cumulative: later detailed follow-ups can supersede earlier summary rows. In particular, Sprint 190's older table says no profile supported, while its latest entries qualify two development-host profiles and still explicitly block production release. Preserve that distinction.

All EQ product sprints are **Planned**, regardless of an upstream Astra sprint's status. Reuse implementation where suitable; perform application integration and product-specific acceptance separately. Source test counts and narrow checkpoint timing are not customer-quality or production-throughput promises.

The source records a 512-token experimental served checkpoint and an earlier prompt-echoing baseline. These facts justify testing the actual selected checkpoint; they do not prove every future checkpoint fails or passes. A capability-qualified quotation model remains a release dependency. Do not silently replace it with an external paid model.

## Capability-to-sprint register

| ID | Capability | Astra source | Product sprint owners |
|---|---|---|---|
| A01 | Authenticated Astra service | PI-27/102; PI-32/157; PI-37/185 | S01, S02, S03, S08, S16 |
| A02 | Durable execution | PI-32/158; PI-37/186 | S07, S16, S18 |
| A03 | Budgets and cancellation | PI-32/160; PI-35/174; PI-37/184-185 | S07, S08, S14, S17 |
| A04 | Document intelligence | PI-16/037-038 | S06, S08 |
| A05 | Retrieval and product matching | PI-17/044-045; PI-29/114-115; PI-31/155; PI-36/180,182; PI-37/187 | S04, S09, S15, S21 |
| A06 | Verification and abstention | PI-11/027-028; PI-21/061-062; PI-36/179 | S05, S08, S09, S10, S11, S17 |
| A07 | Templates and artifacts | PI-22/063-065; PI-36/175-177 | S05, S10, S12, S15, S21 |
| A08 | Safety, permissions and containment | PI-21/055-062; PI-27/100-101; PI-29/129-134; PI-35/171 | S02, S03, S06, S08, S11, S12, S16, S18 |
| A09 | Quality and language evaluation | PI-08/021-023; PI-24/086; PI-25/087-091; PI-28/109-110; PI-31/151-156 | S01, S08, S13, S15, S17, S18, S20 |
| A10 | Feedback and controlled model improvement | PI-19/047-048; PI-20/049-054; PI-26/092-099; PI-34/167-170 | S17, S19, S20 |
| A11 | Scoped memory and deletion | PI-17/044; PI-18/046; PI-34/169; PI-36/180-182 and follow-ups | S03, S09, S16, S19, S21 |
| A12 | Serving and capacity | PI-16/040-043; PI-35/172-174; PI-37/183-190 | S01, S16, S17, S18, S20, S21 |
| A13 | Context compression | PI-22/070-072; PI-36/180-182 and follow-ups | S08, S09, S17, S21 |
| A14 | External providers and MCP | PI-33/162-166 | S01, S08, S21 |
| A15 | Browser, computer use and agents | PI-12-15; PI-29; PI-32/159,161 | S01, S21 |

## A01 Authenticated Astra service

**Source:** PI-27/102; PI-32/157; PI-37/185, detailed headings in the status reference.  
**Recorded evidence and limits:** Versioned live gateway and client manifest exist. Some legacy UI/API surfaces remain unsuitable for public customer access; client and hosting gaps remain.  
**Product work:** Use private versioned gateway from Next.js with server-managed tenant-scoped credentials; validate exact schemas and typed failures. Never proxy legacy demo APIs publicly.  
**EQ sprints:** S01, S02, S03, S08, S16.

## A02 Durable execution

**Source:** PI-32/158; PI-37/186, detailed headings in the status reference.  
**Recorded evidence and limits:** SQLite durable jobs, fencing and effect-reconciliation have local evidence. Temporal is not implemented/adopted; routing and deployment qualification are bounded.  
**Product work:** Reuse Astra job authority for Astra tool/DAG work. Product job tracks the remote ID; product queue must not independently retry uncertain side effects.  
**EQ sprints:** S07, S16, S18.

## A03 Budgets and cancellation

**Source:** PI-32/160; PI-35/174; PI-37/184-185, detailed headings in the status reference.  
**Recorded evidence and limits:** Measured token/time ledgers and cancellation exist on selected paths. Owner-backed gateway wiring has disclosed metering/deadline limits; some counters are unavailable.  
**Product work:** Qualify chosen path end to end; distinguish software subscription allowance from runtime token budget. Unknown settlement blocks automatic duplicate charging/retry.  
**EQ sprints:** S07, S08, S14, S17.

## A04 Document intelligence

**Source:** PI-16/037-038, detailed headings in the status reference.  
**Recorded evidence and limits:** Document/context primitives are reported implemented; quotation-specific OCR, field quality and long-context fidelity are not established.  
**Product work:** Adapt bounded parsing with source spans; preserve quantities, units, product codes, and exclusions through chunking; add only necessary authenticated wrapper endpoints.  
**EQ sprints:** S06, S08.

## A05 Retrieval and product matching

**Source:** PI-17/044-045; PI-29/114-115; PI-31/155; PI-36/180,182; PI-37/187, detailed headings in the status reference.  
**Recorded evidence and limits:** BM25/hash baselines and experimental learned adapters exist. Permissioned indexing has follow-up integration; PostgreSQL adapter is not product-wired, approximate retrieval failed registered gates.  
**Product work:** Start exact SKU and authorized lexical retrieval; benchmark reuse adapters against product fixtures. No blanket semantic or pgvector production claim.  
**EQ sprints:** S04, S09, S15, S21.

## A06 Verification and abstention

**Source:** PI-11/027-028; PI-21/061-062; PI-36/179, detailed headings in the status reference.  
**Recorded evidence and limits:** Verification mechanisms exist; gateway verified means supplied checks passed. Claim verification is narrow and fixture review remains open.  
**Product work:** Check schema, source spans, units and catalogue identity; expose needs-review/insufficient evidence. Quote money always comes from deterministic product logic.  
**EQ sprints:** S05, S08, S09, S10, S11, S17.

## A07 Templates and artifacts

**Source:** PI-22/063-065; PI-36/175-177, detailed headings in the status reference.  
**Recorded evidence and limits:** Office authoring/readback and bounded formula/style mechanisms have local evidence and disclosed scope limits; Office routes and production qualification are incomplete.  
**Product work:** Deliver PDF/CSV from approved product snapshots first. Validate actual rendered output. DOCX/XLSX are optional later behind explicit feature qualification.  
**EQ sprints:** S05, S10, S12, S15, S21.

## A08 Safety, permissions and containment

**Source:** PI-21/055-062; PI-27/100-101; PI-29/129-134; PI-35/171, detailed headings in the status reference.  
**Recorded evidence and limits:** Policy/permissions/privacy tools are reported; hardened execution and local-UI security limitations remain profile-dependent.  
**Product work:** Derive identity from authenticated server state, restrict tools, isolate parsing, enforce product authorization, and test injection. Do not expose arbitrary code/browser tools.  
**EQ sprints:** S02, S03, S06, S08, S11, S12, S16, S18.

## A09 Quality and language evaluation

**Source:** PI-08/021-023; PI-24/086; PI-25/087-091; PI-28/109-110; PI-31/151-156, detailed headings in the status reference.  
**Recorded evidence and limits:** Infrastructure and scorecards do not establish quotation capability. Reference records experimental/unqualified checkpoints and narrow evidence.  
**Product work:** Create independent product fixtures by language/input type; register gates before running. AI launch waits for the chosen checkpoint to pass.  
**EQ sprints:** S01, S08, S13, S15, S17, S18, S20.

## A10 Feedback and controlled model improvement

**Source:** PI-19/047-048; PI-20/049-054; PI-26/092-099; PI-34/167-170, detailed headings in the status reference.  
**Recorded evidence and limits:** Candidate, evaluation and promotion mechanisms exist; candidate capture is not proof of training or deployed model improvement.  
**Product work:** Store consented corrections with lineage; separate retrieval updates from training candidates; evaluation and signed canary/rollback required before model changes.  
**EQ sprints:** S17, S19, S20.

## A11 Scoped memory and deletion

**Source:** PI-17/044; PI-18/046; PI-34/169; PI-36/180-182 and follow-ups, detailed headings in the status reference.  
**Recorded evidence and limits:** Scoped memory/index integration exists but source-store deletion, backups, authenticating asserted principals and wider lineage have documented gaps.  
**Product work:** Authenticate principals in product boundary, sync permissioned sources with revisions, propagate deletion beyond context-local indexes, avoid cross-customer learning.  
**EQ sprints:** S03, S09, S16, S19, S21.

## A12 Serving and capacity

**Source:** PI-16/040-043; PI-35/172-174; PI-37/183-190, detailed headings in the status reference.  
**Recorded evidence and limits:** Latest 2026-09-30 entry qualifies local-cpu/local-cuda mechanisms on development host; release checklist still blocks production. vLLM not adopted, Astra Compose sprint stopped/removed.  
**Product work:** Keep native Astra serving baseline. Re-run in locked environment with served model and target host; choose supervisor, audit durability, TLS and measured capacity.  
**EQ sprints:** S01, S16, S17, S18, S20, S21.

## A13 Context compression

**Source:** PI-22/070-072; PI-36/180-182 and follow-ups, detailed headings in the status reference.  
**Recorded evidence and limits:** Ranked context and extractive verified compression exist; fidelity and independent-review limits remain, generative profile is unqualified.  
**Product work:** Preserve mandatory SKU/quantity/unit/negation facts; fall back to raw chunks or explicit budget conflict; assess before enabling compression.  
**EQ sprints:** S08, S09, S17, S21.

## A14 External providers and MCP

**Source:** PI-33/162-166, detailed headings in the status reference.  
**Recorded evidence and limits:** Recorded owner decision keeps external providers disabled/unreleased; external accounts and third-party MCP evidence absent.  
**Product work:** No paid-model fallback in this plan. Native authenticated Astra first; MCP is deferred until a concrete authorized integration justifies it.  
**EQ sprints:** S01, S08, S21.

## A15 Browser, computer use and agents

**Source:** PI-12-15; PI-29; PI-32/159,161, detailed headings in the status reference.  
**Recorded evidence and limits:** Scoped primitives and fixtures have evidence, with environment and capability limits.  
**Product work:** Out of initial quotation-product scope: no autonomous browsing, computer control, code execution, or multi-agent business actions. Revisit only for a specific later requirement.  
**EQ sprints:** S01, S21.

## Product/Astra ownership boundary

React owns customer screens. Next.js owns customer sessions, workspaces, catalogue/prices, quote calculations, approval, subscriptions and public APIs. Astra remains an independent Python/PyTorch inference/runtime service; do not rewrite it in Next.js.

Create a private TypeScript Astra client in EQ. The server resolves an authenticated workspace/principal to a narrowly scoped Astra credential or qualified authenticated identity mechanism. Never use a browser-supplied tenant claim with a shared unrestricted key. Credential provisioning, rotation and revocation need explicit integration evidence.

Published manifest operations include `POST /v1/chat`, `POST /v1/generate`, `GET /v1/models`, `POST /v1/embeddings`, `POST /v1/tools`, `POST /v1/jobs`, job status/cancel/resolve, `POST /v1/evaluate`, and `POST /v1/confirmations`. Their existence does not prove a catalogue retrieval, quote extraction, or professional artifact operation is already exposed. Inspect schemas in S01. Add a reviewed authenticated Astra wrapper or product adapter where required; mark it new integration work.

The product owns its business workflow and customer allowance ledger. Astra owns its accepted remote job and runtime budget. Persist both IDs and a correlation ID. Reconcile remote uncertain outcomes before replay. Do not run one AI task under two competing worker authorities. A product Node worker/queue is optional for product-owned parsing/export/email only, with a documented boundary.

## Model size planning estimate (2026-10-04)

Planning estimate, not a measurement or a qualification. Source: [Model size and training time guide](../../../../astra-llm/codebase/command-documentation/14-MODEL_SIZE_AND_TRAINING_TIME_GUIDE.md), section 10.

- **Task the model owns:** extract line items (product, quantity, unit, specification, exclusions) from enquiry emails and PDFs. Catalogue matching is retrieval (A05); quote money is deterministic product logic (A06); a person approves every quotation.
- **Size estimate:** about 100-350 M parameters may be workable if trained only on this extraction task with many examples; 1-3 B is comfortable for paying customers. The currently served Astra checkpoint (`checkpoint-dolly-54m-12k`, 53.9 M, general instruction data, 512-token context) is not expected to qualify.
- **Owner direction:** Astra's own from-scratch model, small budget, one 6 GB GPU (GTX 1660 Ti, ceiling about 1.25 B for training). Path: collect enquiry -> line-item examples for one customer group (real where available, synthetic from the catalogue); pretrain an Astra model of about 100-200 M on licensed general text; fine-tune it on extraction only; measure on held-out product fixtures (A09); step up to about 1 B on rented compute only if the measurement falls short.
- **Release effect:** none. The S08/S17 dependency below is unchanged: launch waits for the selected checkpoint to pass the registered product gates, whatever its size.

## Explicit release dependencies

- Qualified selected checkpoint for quotation extraction, supported languages and context sizes: S08/S17.
- Tenant/principal propagation and no legacy unauthenticated API exposure: S02/S03/S08.
- Chosen inference path's budget, cancellation and restart behavior: S07/S17.
- Target-host locked-runtime capacity, supervision, TLS, durable audit and recovery: S16-S18.
- Reviewed regional product/policy settings and accurate public claims: S15/S18.
- Independent evaluation and trained-candidate release evidence before learned improvements: S19/S20, optional after launch.

A failing dependency may leave AI disabled and manual quoting usable. It must not be represented as a completed AI release. The EQ plan does not instruct changes to the Astra repository during this documentation task.

