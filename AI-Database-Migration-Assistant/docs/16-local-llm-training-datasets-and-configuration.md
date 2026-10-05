# DM local LLM: datasets, training percentages, model sizes and configuration

**PI delivery status:** Required source for the assigned PI/sprint scope. See [documents 16-19 delivery matrix](../PI/documents-16-19-delivery.md) for task IDs, acceptance criteria and evidence ownership. Requirements remain Planned until implemented and accepted; explicitly optional/deferred items retain that status.

Prepared: 5 October 2026. Status: proposed research/engineering plan; no training run or migration-quality result is claimed.

## 1. Recommendation and limits

Use Astra as a specialized local migration assistant inside the deterministic system described in [architecture](02-architecture-and-integration.md). Develop its ability to understand evidence, propose mappings, ask precise questions and explain failures. Database connectors, transformations, durable execution, integrity validation and cutover remain software responsibilities.

There is no dataset percentage or parameter count that guarantees correct migration of every database. A good response is grounded, structurally valid, semantically correct and honest about missing information. A fluent answer or syntactically valid SQL is insufficient. Production autonomy is granted to qualified recipes, not to a model merely because it has a high benchmark average.

The intended model remains Astra's own locally trained model. Its documented served checkpoint is approximately 54M parameters, not a demonstrated general migration model. Start with an unchanged baseline, then a 100M-350M development experiment if resources permit; consider a roughly 1B candidate only after data quality and held-out gains justify scaling. A 3B-8B class is an experimental longer-term capability target, not a guaranteed minimum or a recommendation to train it from scratch on the current machine. Never equate a randomly initialized 7B model with a well-pretrained 7B model.

The alternative of locally adapting a licensed pretrained coding model is described separately below for comparison only. It does not change the owner's own-model direction.

## 2. Separate the three data stages

| Stage | Purpose | Unit for percentages |
|---|---|---|
| A: foundation/domain pretraining | Learn language, code, SQL and database concepts; particularly important for random-initialized Astra | Tokens actually sampled by the training tokenizer |
| B: supervised instruction tuning (SFT) | Learn the migration task/output contract, evidence use and clarification behavior | Training examples by primary task category; also monitor token shares |
| C: optional preference/correction training | Prefer grounded, safe, correct responses over plausible wrong ones | Reviewed preference pairs; separate dataset and objective |

Do not add percentages across these stages. Train/validation/test allocation is another independent split, not a topic category. Retrieval documents are runtime context unless separately licensed and admitted to a training stage. Serving a large database never requires training on every customer row.

## 3. Stage A: proposed foundation mix (100% of sampled tokens)

| Category | Share | Example material and expected skill |
|---|---:|---|
| Licensed application code and tests | 30% | Python, TypeScript/JavaScript, ORM models, migrations, domain tests, transaction handling |
| SQL, DDL and relational exercises | 25% | Schemas, joins, keys, constraints, typed expressions, query explanations and results |
| General technical language and problem explanations | 20% | Reading instructions, structured explanations, ambiguity and precise terminology |
| Database/ETL documentation and operational procedures | 15% | Transactions, snapshots, backup/restore, type differences, integrity and data pipelines |
| Structured data and contracts | 10% | JSON/YAML schemas, typed records, API/tool contracts and validation examples |
| **Total** | **100%** | Proposed starting mixture, tune through controlled experiments |

These are not known optimal weights. Deduplicate before sampling; record unique tokens and repeated exposures separately. Do not repeat a tiny SQL corpus thousands of times to claim a large corpus. Preserve useful general code/language behavior with regression evaluation. Public visibility does not establish training permission.

For arithmetic only, a planning yardstick of 20 training tokens per parameter gives approximately 2B tokens for 100M parameters, 7B for 350M, 20B for 1B and 140B for 7B. This is a rough compute-planning reference, not a minimum, optimum for Astra, or sufficiency claim. Modern specialized models may use very different data budgets. Model/data scaling depends on compute and objective; see the original [compute-optimal training study](https://arxiv.org/abs/2203.15556).

If the licensed corpus and training budget are far below the proposed scale, shrink the experiment and task scope rather than promise general coding competence from SFT alone. Measure tokens/sec on the actual training path before estimating duration.

## 4. Stage B: proposed migration SFT mix (100% of examples)

The example counts below illustrate a future **100,000-example training partition**, after holding out validation/test families. They are not a required minimum or a claim that these examples already exist.

| Primary category | Share | Examples at 100k | Required content |
|---|---:|---:|---|
| Schema understanding and dependency discovery | 10% | 10,000 | Entities, types, composite keys, cycles, constraints and unsupported objects |
| Old-to-new entity/field mapping | 20% | 20,000 | Renames, normalization splits, explicit merges, required-target coverage and lineage |
| Business-rule and code grounding | 15% | 15,000 | ORM/query evidence, status meanings, money units, soft deletes and contradictions |
| Typed transformation and dialect differences | 10% | 10,000 | Decimal precision, dates/timezones, nulls, encodings, enum lookup and range checks |
| Mapping DSL and allowed tool use | 10% | 10,000 | Valid structured proposals, object references, restricted discovery/rehearsal requests |
| Independent validation and reconciliation | 10% | 10,000 | Business equations, foreign-key checks, transformed-value comparisons and disposition accounting |
| Failure diagnosis and bounded correction | 10% | 10,000 | Real execution errors, evidence-backed fixes, retries versus mapping changes |
| Clarification, abstention and unsupported scope | 5% | 5,000 | Missing status meaning, uncertain ownership, contradictory evidence, impossible conversion |
| Security and tenant isolation | 5% | 5,000 | Prompt injection, credential avoidance, tenant-aware keys and rejected scope expansion |
| Cutover/recovery explanations and reports | 5% | 5,000 | Evidence-based readiness, write boundaries, recovery limitations and accurate outcome summaries |
| **Total** | **100%** | **100,000** | One primary category per example |

Cross-cutting tags such as privacy, ambiguity and money can overlap any category; their percentages are not added to this table. In particular, include negative/ambiguous examples inside mapping and code-grounding categories, not only the 5% dedicated clarification bucket. A model must learn when clarification is unnecessary as well as when it is mandatory.

Start with roughly 1,000-2,000 carefully reviewed examples to debug ingestion, masking, output schemas and execution oracles. A later 10k-20k training set can test whether quality improves on unseen families. Expand toward 50k-100k only when measured gains justify annotation/generation cost. These are experiment sizes, not delivery guarantees. Family diversity and correctness matter more than producing thousands of paraphrases.

Long error traces can dominate tokens despite a 10% example share. Report both example distribution and assistant-loss-token distribution; cap oversized contexts, retrieve focused excerpts and investigate mixture changes before adjusting weights.

## 5. Database/domain coverage and data splits

For the first migration product, prioritize the qualified source/target profile. A provisional Stage B database tag allocation is 70% proposed MySQL-to-PostgreSQL cases, 20% engine-independent relational reasoning and 10% correctly identifying unsupported/mismatched engine behavior. This is a separate axis over the same examples, not an additional topic mix. If S01 selects another first pair, replace the 70% allocation accordingly. PostgreSQL-to-PostgreSQL or any other executable profile still requires its own qualification.

Represent multiple business domains: customers/orders, billing/accounting, inventory, HR/payroll, bookings, support, multi-tenant SaaS and audit/history. Domain variety does not imply commercial support for all those applications. Include small and large schema contexts and cases where a correct mapping cannot be inferred from available evidence.

Aim for **80% training / 10% validation / 10% locked test by independent family groups**. Grouping takes priority over exact sample percentages; report realized family and example counts. Split by application/repository/customer/schema lineage before generating variants. Keep similar schemas, forks, renamed copies and teacher-generated derivatives in the same partition. Maintain the separate manually authored challenge suite from [guide 09](09-evaluation-and-benchmark-plan.md); never feed its hidden answers into training or repair.

Use validation for tuning. Once a locked-test result informs changes, retain that result honestly and qualify on a new untouched test version for a new release claim. Hash source records, prompts and splits; audit near-duplicate code/schema graphs, not only identical strings.

## 6. Dataset sources and acquisition policy

| Source family | Use | Restriction |
|---|---|---|
| Project-owned synthetic paired applications/databases | Main migration SFT corpus and independent test fixtures | Generate from reviewed business rules; execute fixtures and verify oracle independence |
| Licensed application repositories and their migration histories | Realistic code/ORM/schema evolution evidence | Admit explicit licences and versions; review repository and bundled data separately |
| Official database and framework documentation | Grounded operational/type behavior; local retrieval | Reference access is not permission to redistribute/train; check exact terms before corpus inclusion |
| [Spider](https://yale-lily.github.io/spider) | Supplementary SQL/schema reasoning | Respect released splits and licence; text-to-SQL is not an end-to-end migration dataset |
| [BIRD](https://bird-bench.github.io/) | Supplementary database-grounded SQL evaluation/training where permitted | Check exact subset/asset terms; preserve hidden evaluation; includes different scope from migration |
| [Spider 2.0](https://spider2-sql.github.io/) | External SQL workflow evaluation | Keep released gold tasks out of SFT when using it as a benchmark; authors discourage gold-SQL SFT |
| Explicitly permitted customer cases | Later domain-specific examples | Separate permission for training, minimization, access control and lineage; migration permission is insufficient |

No single public dataset supplies the full paired-schema, transformation, operational and business-rule evidence needed here. Build the core dataset from executable paired applications and reviewed scenarios; use public SQL datasets as supplements, not the entire curriculum. No dataset was downloaded in this documentation update.

Store per dataset: source URL/revision, owner, licence/terms version, permitted use and distribution, approval basis, sensitive-data scan, domain/engine tags, unique family IDs, sample/token counts, deduplication report, checksums, split manifest and quality decision. Unknown licence means excluded pending review. Do not label the entire public web a licensed corpus.

Synthetic data generated by another model needs the same provenance/terms checks plus independent correctness verification. Do not trust a teacher model's confidence or generate both candidate and final oracle with the same prompt. Distillation from a teacher is an optional separate choice, not automatically authorized by this own-model plan.

## 7. What one training example contains

Required fields: example ID; family ID; stage/task tags; provenance; source and target engine versions; schema/code/evidence references; allowed tools/DSL version; minimized input; expected structured response; unresolved questions where applicable; independent oracle; result disposition; sensitive-data policy; split; reviewer and validation state.

```json
{
  "example_id": "synthetic-inr-orders-001",
  "family_id": "owned-orders-v1",
  "primary_category": "business_rule_grounding",
  "source_evidence": "Reviewed source code stores total_paise as INR minor units.",
  "target_contract": "amount is exact decimal rupees; currency is required",
  "input": {"total_paise": 125050},
  "expected_response": {
    "operation": "decimal_rescale",
    "divisor": 100,
    "currency": "INR",
    "evidence_refs": ["owned-source-money-rule"],
    "unresolved_questions": []
  },
  "independent_expected_value": {"amount": "1250.50", "currency": "INR"},
  "status": "illustration_only_not_a_training_artifact"
}
```

Pair this with counterexamples: absent currency evidence; ambiguous units; decimal overflow; target scale incompatible with source precision. The correct response to missing units is a question, not a guessed divisor. Validation checks must distinguish those examples.

Training pipeline: provenance/licence admission -> privacy filtering -> deduplication -> family split -> reviewed schema/rule generator -> candidate examples -> real-engine execution checks -> human review of semantics -> versioned corpus -> tokenization -> training. Use concise evidence-backed rationales and observable tool steps; do not require fabricated hidden reasoning traces as training labels.

For SFT, compute loss on intended assistant targets; mask user, padding and tool-result tokens according to the chosen objective. Retain those tokens as context where needed. Verify masking and truncation so that a clipped schema or missing answer cannot silently become a positive example. In packed instruction sequences, enforce the intended example attention boundaries. Record tokenization and formatting changes as dataset/model compatibility changes.

## 8. Model type and parameter-size options

Recommended experimental type: a dense decoder-only causal language model with code/SQL competence, instruction tuning, evidence retrieval and validated structured outputs. A mixture-of-experts design adds routing/training complexity and is not required for the first product. Retrieval embeddings can be a separate local component; an embedding model does not replace the reasoning/generation model.

| Size class | Experimental role | Limitation |
|---|---|---|
| Current ~54M | Baseline and pipeline tests | No evidence of general migration competence |
| 100M-350M | Lower-cost experiments in schema extraction, classification and constrained output | Treat open-ended mapping as unproven; may be useful only for narrow tasks |
| ~1B | Candidate for restricted evidence-grounded mapping families | Requires substantial learning and independent evaluation; no guaranteed autonomy |
| 3B-8B | Longer-term experiment for harder code/schema reasoning | From-scratch compute/data burden is much larger; quality depends on training, not size alone |
| 14B-32B | Optional later capacity/quality comparison | Higher memory/latency; unnecessary unless measured gains justify it |

### Illustrative own-Astra architecture candidate

This is a design experiment, **not a supported Astra config or command**. Check actual implementation support before creating a checkpoint. Never change architecture/tokenizer on an existing checkpoint in place.

```yaml
status: proposed_not_executable
model_type: dense_decoder_only
layers: 20
hidden_size: 2048
attention_heads: 16
kv_heads: 4
head_dimension: 128
feed_forward: swiglu
intermediate_size: 5632
vocabulary_size: 32768
tie_input_output_embeddings: true
normalization: rmsnorm
position_encoding: rope
initial_training_context: 2048
later_context_target: 8192
```

With conventional bias-free projections and tied embeddings, this is roughly 0.97B parameters: per layer approximately 2*d^2 + 2*d*d_kv + 3*d*f, plus vocabulary*d and small norm terms. Verify the actual instantiated parameter count. The 8k context target requires explicit training/adaptation and evaluation; changing a config number does not establish usable long-context quality. Start smaller if measured training memory/throughput cannot support this candidate.

Choose tokenizer from SQL/code coverage experiments: compare identifier, punctuation, Unicode and numeric tokenization; provisionally compare 16k and 32k vocabularies. Tokens/parameter estimates change with tokenizer. Maintain the exact tokenizer with every checkpoint and never silently reuse incompatible embeddings.

### Optional local pretrained comparison

A licensed pretrained coder plus local SFT/LoRA could provide a stronger starting point with less pretraining work, but this is not the selected own-Astra path. As a concrete reference, the published [Qwen2.5-Coder family report](https://arxiv.org/abs/2409.12186) describes multiple parameter sizes and extensive pretraining. That is evidence that '7B parameters' carries a training history, not evidence of migration reliability. A comparison would pin a checkpoint, licence, tokenizer/runtime and local-only deployment, then run exactly the same DM evaluation. No model is downloaded or adopted here.

## 9. Memory and hardware planning

Raw weight arithmetic below uses decimal GB, with no scales, buffers, KV cache or runtime overhead. Actual quantization formats require extra metadata and not every tensor is quantized. Do not use these figures as a GPU shopping specification.

| Parameters | FP32 weights | FP16/BF16 weights | Ideal 4-bit weights |
|---|---:|---:|---:|
| 350M | 1.40 GB | 0.70 GB | 0.175 GB |
| 1B | 4 GB | 2 GB | 0.5 GB |
| 3B | 12 GB | 6 GB | 1.5 GB |
| 7B | 28 GB | 14 GB | 3.5 GB |
| 14B | 56 GB | 28 GB | 7 GB |
| 32B | 128 GB | 64 GB | 16 GB |

Inference needs weights + KV cache + activations/workspaces + framework/reserve memory; context and concurrent sequences can dominate. Measure quality after quantization because small numerical changes can alter mappings. Training additionally needs gradients, optimizer state and activations. Common full AdamW/mixed-precision arrangements can use roughly 12-16 bytes per parameter for model/gradient/optimizer/master-weight state before activations, depending on implementation. Calculate from the actual optimizer and dtype; Astra's experimental stateless optimizers have different tradeoffs and cannot inherit AdamW quality claims.

The reference documents describe a 6GB GTX 1660 Ti and distinguish training fit probes from capability. BF16/quantized-kernel support is hardware/runtime-specific; do not presume it here. Profile full training and inference separately on the actual host. CPU/offload can increase capacity but latency must be measured. No GPU purchase or price estimate is included.

## 10. Proposed training configurations

These are starting search ranges for controlled experiments, not validated Astra flags. Exact support for optimizer, precision, LoRA or QLoRA must be checked in the local implementation before use.

| Setting | Own-model pretraining | Full-weight migration SFT | Optional compatible pretrained LoRA/QLoRA |
|---|---|---|---|
| Optimizer | AdamW reference; alternatives compared separately | AdamW reference | AdamW-family adapter optimizer supported by selected stack |
| Peak learning-rate search | 1e-4, 3e-4, 6e-4; revise with size/stability | 5e-6, 1e-5, 3e-5 | 5e-5, 1e-4, 2e-4 |
| Schedule | Warmup then cosine; token-count based | Warmup then decay | Warmup then decay |
| Warmup | Initially 1-3% of token budget | Initially 3-5% of optimizer updates | Initially 3-5% of optimizer updates |
| Weight decay | Initial 0.1 on appropriate weights | Compare 0.01 and 0.1 | Compare 0 and 0.01 on trainable adapters |
| Gradient clipping | Initial global norm 1.0 | Initial global norm 1.0 | Initial global norm 1.0 |
| Context | Begin 2,048; extend only with evidence | 2,048-4,096 first; later 8,192 if supported | Within base model's qualified context; same DM evidence budgets |
| Microbatch | Largest measured stable size; start 1 | Start 1-2; accumulate | Start 1-2; accumulate |
| Effective batch | Record actual non-padding tokens; initial experiment 32k-128k/update if feasible | Initial 8k-32k assistant loss tokens/update if feasible | Same token-accounting principle |
| Duration | Explicit unique/exposure token budget | Start 1 epoch; consider up to 3 using validation | Start 1 epoch; consider up to 3 using validation |

Batch targets are experiment options, not requirements; long accumulation windows may be impractical. Compute effective tokens from actual masked lengths, devices and accumulation, not examples alone. Perform a short stability/throughput probe first; halt on nonfinite loss, corrupted masks, tokenizer mismatch or resource spill. Save model, tokenizer, optimizer/scheduler state, RNG state and dataset cursor for reproducible resume. Choose checkpoints by validation execution quality plus existing Astra gates, not training loss alone.

Optional LoRA starting grid: rank 16 or 32; alpha 2*rank; dropout 0.05; target supported attention/MLP linear projections with module names verified in the actual architecture. QLoRA uses a quantized frozen base and trainable adapters; it does not train a randomly initialized foundation cheaply or guarantee compatibility with Astra's custom model. Four-bit NF4/double-quantization and compute dtype are options only where supported. [PEFT quantization guidance](https://huggingface.co/docs/peft/v0.19.0/developer_guides/quantization)

Stage C is optional and follows a solid SFT baseline. A proposed preference-pair mix is 35% semantic correctness, 25% evidence/appropriate clarification, 20% correct versus prohibited tool behavior, 10% repair without weakening checks and 10% faithful reports. These sum to 100% of preference pairs only. Both alternatives need reviewed labels and oracle evidence; preference training cannot replace missing foundation skills or execute a safe migration by itself. Choose its objective/hyperparameters in a separate experiment plan.

## 11. Inference, retrieval and response configuration

| Setting | Proposed initial policy |
|---|---|
| Deployment | Local Astra endpoint; no external inference/embedding fallback |
| Generation | Greedy decoding where supported; otherwise low-temperature controlled decoding with recorded parameters |
| Context budget | Respect trained/qualified context; retrieve relevant tables/code rather than the entire repository |
| Output budget | Reserve an explicit output allowance; for a 4k context example, up to 1k output and at most 3k total input |
| Evidence retrieval | Start with 4-8 focused chunks, adjusted to measured tokenizer lengths and task coverage |
| Output contract | Mapping DSL JSON plus evidence refs, unresolved questions and limitations; validate outside model |
| Tools | Allowlisted read-only discovery and disposable rehearsal through policy service; no write credentials in model |
| Candidate repair | At most three proposals initially, within token/time budget; never edit independent oracle to pass |
| Reuse | Persist accepted mapping; no per-row generative inference during transfer |
| Failure | Explicit unsupported/ambiguous/unavailable result, not fabricated success |

Greedy decoding does not imply byte-identical results across runtime/hardware changes. Pin model/tokenizer/prompt/retrieval/runtime versions and store actual proposals. Detect output truncation or missing required evidence and reject incomplete plans. If context is too small, split the task by dependency groups and reconcile global relationships with deterministic checks; never silently discard required schema edges.

Good user-facing answers explain what maps where, the evidence, what cannot yet be inferred, what checks ran and their actual result. Example: 'Status 2 maps to paid because source function X defines it; status 9 is unresolved and blocks this recipe.' Avoid ungrounded 'migration completed' language.

## 12. Quality targets and staged promotion

Keep [guide 09](09-evaluation-and-benchmark-plan.md) and [release gates](03-quality-and-release-gates.md) authoritative. Additional initial candidate targets below are proposed and must be registered before evaluation:

| Dimension | Proposed target / enforcement |
|---|---|
| First-attempt structured validity | >=99% on the frozen supported proposal suite; report repaired results separately |
| Grounded mapping proposals | Every executed rule references valid evidence or an explicitly reviewed rule; missing refs block compilation |
| End-to-end supported task success | >=95% candidate-level target from guide 09; every actual released migration must pass all mandatory checks |
| Critical money/tenant/status/relationship errors | Zero accepted failures in qualification; report uncertainty and restrict scope |
| Critical ambiguity and unsupported scope | All challenge cases block unattended execution until resolved |
| Data outcomes | 100% scoped disposition accounting; no unexplained loss, duplication or orphan relationships |
| Report fidelity | No unsupported completion/validation claims; all reported counts reconcile to evidence |
| Runtime behavior | Browser/API restart independent of worker completion; recovery and privilege checks still pass |

An external JSON validator guarantees rejection of invalid structure, not that the model will generate valid structure 100% of the time. An aggregate success target does not authorize the remaining failures. Include model uncertainty, family-level scores, confidence intervals, reviewer minutes, inference cost and false escalations in the report.

Promotion ladder: baseline only -> useful read-only assessment -> reviewed mapping assistant -> qualified repeat-recipe automation -> additional recipe/engine families after new evidence. Do not promise the last stage merely because training finishes. A smaller model that asks the right question can be more useful than a larger model that invents an answer.

## 13. Delivery checklist and sprint integration

The [gap review](19-gap-review-and-acceptance-register.md) adds examples for scope dependencies, lossy cleanup, external-object readiness and truthful operating reports to the existing Stage B categories. It does not create extra percentage buckets; keep each stage's primary-category total at 100%. Apply [model/recipe lifecycle and correction handling](18-operational-lifecycle-and-product-acceptance.md): user corrections are not automatically training data, and retired/revoked artifacts cannot silently serve new jobs.

- S10: licensed dataset inventory, family splits, primary-task percentage/count report, token exposure report, current-model baseline and independent oracle.
- S11: model architecture/config manifest, tokenizer audit, supported-feature check, training stability/throughput evidence, controlled candidate comparisons, retrieval/output contract and quality results.
- S12: recipe qualification, evidence-backed clarification, bounded repairs and automatic execution only within accepted scope.
- S16: full React/Next.js migration UI with local model unavailable/ambiguous/failed states and durable progress.
- S17: measured host memory/latency/throughput, quantized versus reference quality if used, local data boundary and recovery proof.
- S18: actual customer application acceptance and truthful supported-scope release.

No dataset acquisition, model download, training, framework installation or production migration has been performed by this documentation update. The next model action is to measure the existing checkpoint on a small independent migration suite, while the deterministic migration engine is developed separately.
