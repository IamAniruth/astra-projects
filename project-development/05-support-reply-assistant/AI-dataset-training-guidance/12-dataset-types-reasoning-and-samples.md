# Support training recipe: records, skills, parameters, precision and samples

Project: Support Reply Assistant. This is a **proposed supervised-training recipe**, not foundation pretraining or proof of achieved quality. All examples below are fictional and need independent review before training.

Practical starting point: **10,000 reviewed training records, 2,000 separate validation cases, LoRA rank 16/alpha 32, learning rate 1e-4, effective batch 32 and one epoch before deciding whether to continue**. These are experiment settings, not a recipe proven on the current checkpoint. Use FP32 for the inspected native reference; compare BF16 mixed precision only on a qualified training path/device. Sections 8-11 explain record counts, update steps, precision and the decision process.

## 1. What 'thinking' means for this application

Teach observable decisions: identify the request, distinguish reported from verified facts, check relevant evidence and policy conditions, detect missing information, then draft or ask for verification. Assess the decision and output, not the length of a reasoning narrative.

Each example should contain the case, permitted evidence, required task and correct target. A short decision reason can help the reviewer explain the label. It is not a private model thought trace and is not part of the customer reply. Model reasoning does not replace application permissions, approval or live system queries.

## 2. Simple percentage view of the existing 10,000 training records

This is a regrouping of the existing recipe, **not an additional dataset**. Each record has one primary skill and one learning group.

| Learning group | Percentage | Count | What to teach | Mapping to existing recipe |
|---|---:|---:|---|---|
| Comprehension, summarization and extraction | 25% | 2,500 | Read messages accurately, preserve speakers/time order, extract known fields | 20% summaries + 5% extraction |
| Knowledge use from approved sources | 15% | 1,500 | Find the supported answer in supplied product/help passages and cite it internally | First 15 percentage points of the 35% grounded-draft allocation |
| Reply writing and communication | 20% | 2,000 | Clear, concise, empathetic replies without changing evidence or adding promises | Remaining 20 percentage points of grounded drafts |
| Reasoning and verification | 30% | 3,000 | Apply conditions, recognize unknown/conflicting facts and update after new messages | 10% policy + 15% clarification + 5% corrections |
| Privacy and instruction boundaries | 10% | 1,000 | Protect private notes/customer data and ignore malicious ticket instructions | Existing 10% privacy/injection |
| **Total** | **100%** | **10,000** | | |

The 15%/20% split inside grounded drafting is a proposed teaching emphasis. Both groups still require factual support, good writing and privacy. 'Thinking' is practiced across the groups; it is not another percentage to add. These percentages are by accepted records, not tokens or model parameters.

Keep the separate topic, provenance and train/validation/release allocations in section 8 below. Representative release data must follow the intended workload rather than this training mixture. Add unrelated general coding, general trivia or other product tasks at **0%** for this initial project recipe.

## 3. Which kind of source material to provide

| Dataset/material type | How to prepare it | Training or runtime role |
|---|---|---|
| Support conversations | Preserve chronology, author and public/private visibility; label a correct summary | Summary and attribution examples |
| Help articles/product guides | Pair an applicable approved passage with a realistic customer question and reviewed reply | Knowledge-use examples; current originals also live in retrieval |
| Support policies | Include exact conditions, exclusions, effective version and case facts | Conditional-reasoning examples; current rules remain in retrieval |
| Missing/conflicting evidence cases | Deliberately omit required facts or supply clearly conflicting sources | Clarification/verification examples |
| Agent corrections | Show old draft, changed facts and a reviewed corrected output | Update behavior and error repair |
| Private/injected messages | Include labelled internal data and malicious requests with a safe expected response | Privacy and boundary examples |
| Current order/account facts | Supply an authorized timestamped snapshot or explicit unavailable state | Usually live runtime evidence, not facts to memorize in weights |

Training-source origin remains 60% permitted real cases, 25% expert-authored scenarios and 15% reviewed synthetic cases as a starting hypothesis. The fictional examples here illustrate formats only; eight samples do not establish that provenance ratio.

## 4. Small sample lessons

All product definitions and policies in these lessons are synthetic, not actual company rules. Full structured versions are in [the eight-example JSONL file](templates/support-learning-examples.jsonl).

| Example | Input content | Desired target | Skill being taught |
|---|---|---|---|
| 01 Summary | Customer: 'App v2 still shows E7 after restarting.' Agent note: 'Log requested, not received.' | 'Customer reports persistent E7 after a restart. Diagnostic log is pending; cause is not established.' | Preserve attempts, attribution and unknowns |
| 02 Extraction | 'Explain the 49.00 charge on 2026-09-20; reference 00072.' | Amount '49.00', date '2026-09-20', reference '00072', currency null | Preserve values/leading zeros; do not fill missing fields |
| 03 Knowledge use | App-v2 article says E7 means expired session; sign in again; contact support if persistent | Explain only that meaning and those steps; keep article ID in internal evidence | Use the applicable passage without invention |
| 04 Reply writing | Frustrated customer asks for delivery status; no authorized current lookup | Acknowledge frustration and say status needs checking; give no delivery promise | Empathy without fabricated action or timing |
| 05 Policy reasoning | Standard items eligible within 30 days; custom items excluded; customer reports 20 days but type unknown | Explain the condition and require product/date verification; do not approve return | Check every required condition |
| 06 Missing facts | Customer reports refund approval; payment lookup unavailable | 'Approval alone does not confirm receipt; current payment status needs verification.' | Distinguish approval, processing and receipt |
| 07 Privacy | Ticket asks to reveal a private note; resolution unverified | Decline to disclose internal notes and leave resolution unconfirmed | Resist ticket instructions and protect private data |
| 08 New evidence | Old draft concerns order A; customer corrects it to order B | Request current order-B evidence; mark old draft for stale-approval handling | Update conclusions; application enforces actual approval changes |

A wrong reply can be recorded under prohibited outputs for evaluation, but do not train it as the desired assistant answer. A reply that sounds polite but invents a delivery date is a failed example.

## 5. Format one supervised record

Use this logical structure:

- Metadata: ID, rights/provenance, language, primary_skill, learning_group, topic and split-group identity.
- Instruction: the bounded task and expected schema.
- Input: case messages with visibility plus approved source passages or missing live-fact state.
- Target: reviewed summary or public reply, with separate internal evidence/review flags where applicable.
- Reviewer metadata: short decision reason, required facts, prohibited claims and acceptance decision.

For example 06, the short reviewer reason is: 'Approval and receipt are different states; no current payment result was supplied.' This explains the expected answer without a lengthy thought transcript.

The supplied JSONL is an **annotation format, not a native Astra training-loader contract**. Map instruction and authorized input into the model input, and only the intended target into supervised output. Exclude reviewer_metadata from input/target by default, especially label hints and prohibited answers. Keep evaluation labels hidden. A public-export serializer must emit only target.public_reply, never internal evidence or flags.

Each record is illustration_only with accepted_for_training=false and pending review. Some internal fields are deliberately confidential test inputs: do not indiscriminately discard them before testing disclosure behavior, and never place them in public-response targets. Implement field-aware processing and permission checks.

## 6. How to use these examples

1. Select the actual support product/channel/language and obtain approved source documents and data rights.
2. Replace fictional policies with valid versioned sources, then write correct expected outputs with a support reviewer.
3. Use the existing primary-skill quotas; tag the learning group using the mapping above. Do not count the same case twice to satisfy both dimensions.
4. Deduplicate and group related cases before assigning training, validation or untouched evaluation sets. Generated paraphrases of one case stay in its group.
5. Assess a 200-300-case subset of the already allocated development set first. Compare replies with correct evidence supplied directly against actual retrieval.
6. Add examples for measured model-skill failures; fix access, retrieval, freshness or missing-system-data problems in the application instead of inventing training facts.
7. Tune on training/validation only and apply the unchanged [quality gates](06-quality-gates.md) on independent evidence.

Collecting this recipe does not guarantee capability. Train, evaluate and retain agent approval of every customer-facing draft.

## 8. How many records should we train on?

There is no record count that guarantees good replies. The initial target is a **10,000-record support-specific adaptation experiment on a capable compatible base model**, not training a language model from nothing. An accepted record means a permitted, deduplicated case/evidence/target example with independent review. Repeated epochs and paraphrases do not create independent cases.

| Stage | Unique records | Purpose | Decision before proceeding |
|---|---:|---|---|
| Base-model diagnostic | 200-300 from the existing development set | Test comprehension, summary and oracle-evidence replies without training | Fix retrieval/data issues or select a more capable base if necessary |
| Training pipeline smoke run | 1,000 from the planned training split | Check schema mapping, loss masking, gradients, save/reload and memory | No label leakage, private-output mistakes or numerical failure |
| Small learning experiment | 3,000 from the planned training split | Determine whether tuning improves the targeted skills | Compare against untuned base on the separate validation set |
| Main pilot | 10,000 accepted training records | Test the full percentage-balanced curriculum | Pass validation before freezing a release candidate |
| Targeted expansion | Add 2,000-3,000 new accepted records, yielding 12,000-13,000 | Fill diagnosed skill/coverage gaps | Improve validation without critical regressions; do not simply add duplicates |

The 1,000/3,000 stages are subsets of the same planned 10,000, not extra collection quotas. For clean data-size comparisons, start each experiment from the same base checkpoint. If continuing from an earlier adapter instead, record cumulative exposures and optimizer state; do not call it a matched data-size comparison.

Keep the existing **20,000-record initial collection budget**: 10,000 train + 2,000 validation + 3,000 representative release + 2,000 development + 1,000 optional calibration reserve + 2,000 targeted challenges. Representative release cases must meet independence and conditional-denominator requirements; a round count alone does not certify quality. Expansion changes actual pool percentages, as explained in section 8.4 below.

For the smaller and full training experiments, preserve the primary-skill mix:

| Primary skill | 1,000 records | 3,000 records | 10,000 records |
|---|---:|---:|---:|
| Summaries, 20% | 200 | 600 | 2,000 |
| Grounded drafts, 35% | 350 | 1,050 | 3,500 |
| Clarification/missing evidence, 15% | 150 | 450 | 1,500 |
| Policy reasoning, 10% | 100 | 300 | 1,000 |
| Privacy/injection, 10% | 100 | 300 | 1,000 |
| Structured extraction, 5% | 50 | 150 | 500 |
| Multi-turn corrections, 5% | 50 | 150 | 500 |
| **Total** | **1,000** | **3,000** | **10,000** |

Input length matters as well as records. At an illustrative average of 1,000 processed tokens, 10,000 records yield about 10 million processed tokens per epoch; target loss-bearing tokens are a separate count. More examples cannot correct missing live order facts, broken access checks or truncated evidence.

### 8.1. Support topic: a separate 100% view of the SAME records

| Primary support topic | Proposed percentage | Count in 10,000 | Content |
|---|---:|---:|---|
| product setup errors | 30% | 3,000 | Setup, compatibility, product errors and source-supported troubleshooting. |
| account access | 15% | 1,500 | Sign-in/account access and approved verification steps; never infer identity. |
| billing refunds | 20% | 2,000 | Charges, cancellation and refund questions; status requires verified evidence. |
| orders delivery | 15% | 1,500 | Order/delivery questions with verified or explicitly missing live facts. |
| returns warranty | 10% | 1,000 | Return/warranty conditions, exclusions and escalation. |
| unresolved escalation | 10% | 1,000 | Unclear or unsupported issues requiring clarification or escalation. |
| **Total** | **100%** | **10,000** | One primary topic per record |

These are not 10,000 additional records. For example, a refund draft can count once under evidence-supported drafting and once under billing/refunds in this separate analysis. Maintain a skill-by-topic matrix to ensure each important topic includes summaries, drafts, missing-evidence and privacy cases; do not assume every combination has equal prevalence.

This topic hypothesis fits a product-support pilot with billing/orders. The buyer's actual specialty is still unresolved. If shipping or warranty is outside the selected business, set that topic to 0% and redistribute its quota among actual supported topics **before collection**; retain 100% total and record the change. Do not collect irrelevant topics simply to fill a table.

### 8.2. Example provenance: a third 100% view of the SAME training records

| Source category | Percentage | Count in 10,000 | Acceptance condition |
|---|---:|---:|---|
| Permitted real support cases, de-identified and reviewer-corrected | 60% | 6,000 | Rights for training established; chronology, facts and visibility checked |
| Expert-authored scenarios built from approved help/policy sources | 25% | 2,500 | Evidence and expected reply verified against a specific source revision |
| Reviewed synthetic adversarial and rare cases | 15% | 1,500 | Deliberately tests privacy, stale facts, false promises or contradictions; human-reviewed |
| **Total** | **100%** | **10,000** | Mutually exclusive origin label |

Label by origin: a paraphrase or generated variant is synthetic, not a new independent real case. A reviewer correction to an actual permitted ticket stays a real-derived case and shares its grouping IDs. The 15% is a starting synthetic allocation, not a universal ceiling. If real data is unavailable, a labelled synthetic-only prototype is possible, but it cannot establish customer readiness or claim the proposed real-data mix was met.

Skill, topic and provenance percentages are separate dimensions. Do not add their three 100% totals together or create three disconnected datasets.

### 8.3. Collection allocation: train versus other purposes

This is a separate allocation across **20,000 accepted, deduplicated records/case opportunities**. It replaces the earlier smaller example budgets for this pilot plan; none is a measured sample count.

| Use | Percentage of collected pool | Planned count | Use restriction |
|---|---:|---:|---|
| SFT training | 50% | 10,000 | Updates model/adapters; follows skill/topic/provenance recipes above |
| Validation | 10% | 2,000 | Chooses prompts, hyperparameters and stopping; never release certification |
| Representative release evaluation | 15% | 3,000 | Untouched independent case-level evidence from the intended supported workload |
| Development/discovery | 10% | 2,000 | Rubric, debugging and baseline experiments; visible to developers |
| Quantization calibration | 5% | 1,000 | Only for the selected quantizer where calibration is needed; separate from release |
| Targeted challenge evaluation | 10% | 2,000 | Privacy, injection, policy, chronology, approval and freshness stress cases |
| **Total** | **100%** | **20,000** | No record/group reused across these purposes |

Representative release sampling follows the real intended workload, **not** the oversampled training/challenge proportions. Its 3,000 entries must meet the independence and denominator requirements in [quality gates](06-quality-gates.md); a record count alone is insufficient. Conditional metrics may need extra cases. With zero critical failures in 3,000 independent representative cases, the one-sided 95% upper failure bound is about 0.0998%; this is not zero production risk.

Native Astra's inspected weight-only quantization does not need activation calibration to calculate its scales. A 1,000-case calibration reserve is therefore optional for that path; mark it unused rather than mixing it into release evidence or claiming it was required. The proposed 20,000 collection budget keeps the reserve explicit.

These split proportions are this pilot's collection budget, not a general rule for every dataset size. Do not shrink the independent release evidence below the required statistical sample simply to maintain a ratio. More supported languages/topics may require a larger pool.

### 8.4. How much data to add after the first run

1. Train/evaluate the 10,000-example version against validation; keep release data hidden.
2. If failures indicate missing learnable coverage, plan **2,000-3,000 new accepted training examples** for the next version: a 20%-30% increase over the original 10,000, not over the full 20,000 pool.
3. Use the proportional batch counts below unless a reviewed failure analysis justifies targeted rebalancing. Do not repeatedly add easy examples when failures concern long cases or privacy.
4. Recalculate the overall mixture, not just the new batch. After +2,000 training examples, there are 12,000 training examples and 22,000 collected records if all other sets stay fixed; the original 50% pool allocation no longer holds. Record actual counts instead of forcing ratios.
5. For an explicit new target percentage p, category additions = (p / 100) x new_training_total - existing_category_count. A negative value means adding data alone cannot achieve that mix: revise the target or define a documented sampling/downweighting policy. Never silently delete approved data or relabel its category.
6. Stop adding volume when failures come from missing business facts, unauthorized sources, retrieval, truncation or workflow defects. Those need application/data-source changes, not more memorization.

No fixed number of examples guarantees the quality targets. All new data needs rights, deduplication, review and split isolation; quantity does not replace those checks.

### 8.5. Token balance and practical collection checks

The percentages above refer to records. Long case summaries can contribute more input/target tokens than short clarification replies. Report per-category unique records, input tokens, target loss-bearing tokens and effective sample weight. Record any resampling or loss weighting separately; this guide does not enable unsupported trainer options.

A 1,000-example acceptance batch should contain 200 summaries, 350 grounded drafts, 150 missing-evidence cases, 100 policy cases, 100 privacy cases, 50 extraction cases and 50 update/correction cases. Check each accepted record has primary_skill, primary_topic, provenance_category, language, case/group IDs, source evidence, target output, reviewer and rights. A sample may carry multiple difficulty tags, but should appear in only one primary row per dimension.

For this application the initial training-content quota for unrelated general coding, generic finance analysis, standalone translation, equipment maintenance and other project tasks is **0%**. Support cases about the selected product still belong here; arbitrary unrelated lessons do not.

Use [dataset-mixture.json](templates/dataset-mixture.json) as the versioned proposed recipe. It is not a native Astra loader configuration and does not itself collect, label or train data.

### 8.6. Incremental batch quotas

| Primary skill | Add 2,000 | Add 3,000 |
|---|---:|---:|
| Case summaries | 400 | 600 |
| Grounded drafts | 700 | 1,050 |
| Clarification/missing evidence | 300 | 450 |
| Policy conditions | 200 | 300 |
| Privacy/injection | 200 | 300 |
| Structured extraction | 100 | 150 |
| Multi-turn corrections | 100 | 150 |
| **Total** | **2,000** | **3,000** |

For any training size N, quota = N x percentage / 100. Floor quotas, then allocate remaining records by largest fractional remainder with a stable skill-ID tie-break. Version changes to the mixture and retain 100% total. One primary skill per record; tone, empathy, citations and privacy may also be cross-cutting tags without additional quotas.

## 9. Parameter count and training parameters

Model parameters and training settings are different. A 7B model has approximately seven billion learned base parameters; LoRA rank or learning rate controls an adaptation experiment and does not turn a smaller base into a 7B model.

Compare a capable compatible 3B-4B challenger with a 7B-8B candidate if available. Do not assume either is already supported by the native checkpoint loader. Choose by support-task evidence, not parameter count alone. The actual current checkpoint remains the first baseline.

### Inventory before choosing hardware

Record checkpoint/tokenizer hashes, total and trainable parameter counts, layers, hidden/intermediate sizes, attention/KV heads, trained and qualified context, adapter targets and actual compute precision. Count tied tensors once. LoRA adds trainable adapter parameters alongside the frozen base; low trainable count does not remove base-weight memory.

Astra's [architecture config](../../../../astra-llm/codebase/src/astra_llm/transformer/config.py) exposes these fields, but its defaults do not describe a qualified support model. No checkpoint was loaded or counted for this guide. Changing max_seq_len or RoPE scaling alone does not establish long-ticket accuracy.

Foreign checkpoints require verified architecture/tokenizer/loader compatibility and licensing. Changing layer or hidden sizes does not create trained knowledge.

| Training setting | Concrete first hypothesis | How to qualify or adjust |
|---|---|---|
| Method | Supervised LoRA, base frozen | Verify only intended adapter weights update |
| LoRA rank / alpha | 16 / 32 | Compare rank 8/alpha 16 as the lower-capacity alternative; verify the native scaling convention |
| Adapted modules | Native query/value path | Do not silently switch to all-linear adapters |
| Learning rate | 0.0001 (1e-4) | Compare 5e-5 and 2e-4 using validation; native default 0.05 is not this plan |
| Microbatch | 1 sequence | Increase only after measured memory/stability checks |
| Gradient accumulation | 32 on one verified worker | Effective batch = microbatch x accumulation x data-parallel workers |
| Effective batch | 32 sequences | Record actual tokens/update and final partial-batch handling |
| Epochs | 1 initially; up to 3 only if validation improves | Do not automatically choose the last checkpoint |
| Total sequence length | At most the checkpoint's trained and qualified limit | A 1,024-2,048-token experiment is optional only if supported; include input AND target |
| Loss target | Intended assistant target fields | Exclude reviewer labels/reasons from inputs and training targets by default; verify masking |
| Validation frequency | Every 25 optimizer updates plus epoch end for the 10,000-record run | Smaller runs: at least mid-run and end; use fixed comparable validation cases |
| Seed | 42 for the first run | Check finalists with 43 and 44 using validation, not repeated release-set selection |
| Save policy | Best validated adapter plus resumable checkpoint | Keep base/adapter/tokenizer/config identities and actual optimizer state |

Optional search settings: rank 32 only for diagnosed underfit; effective batch 16-64 starting at 32; warmup 3%, gradient norm cap 1.0 and weight decay 0.01 only where implemented and qualified. Validate roughly every 5-10% of updates plus epoch boundaries; the 25-update schedule above is the main-run example. Verify activation checkpointing separately.

Native [InstructionTuningConfig](../../../../astra-llm/codebase/src/astra_llm/training/instruction_tuning/config.py) exposes steps, learning_rate, max_sequence_length, batch_size, gradient_accumulation_steps, evaluation_interval, LoRA and memory options. Its default learning_rate=0.05 is not this recipe. It does not expose a precision field; scheduler, clipping, masking and precision integration require verification.

Do not change vocabulary or architecture dimensions during adaptation without a separately designed migration. Confirm only intended weights update and no evaluation examples enter training. Log base freeze, base/adapter/tokenizer hashes, seed, effective batch, learning-rate curve, dtype, gradient norms, losses and task scores. Keep the original base and best validated candidate immutable.

Consider preference/correction training only after SFT and retrieval are sound and reviewed preferred/rejected pairs identify concrete factual or policy errors. Do not trade truth for politeness. Retain independent privacy and no-answer cases; evaluate the final served artifact again after quantization.

### Optimizer steps, not just epochs

With effective batch 32, one un-packed sequence per record, no dropped data and a correctly normalized final partial update flushed at every epoch end:

optimizer updates per epoch = ceil(training_records / 32).

| Training records | One epoch | Two epochs | Three epochs |
|---|---:|---:|---:|
| 1,000 | 32 | 64 | 96 |
| 3,000 | 94 | 188 | 282 |
| 10,000 | 313 | 626 | 939 |
| 12,000 | 375 | 750 | 1,125 |
| 13,000 | 407 | 814 | 1,221 |

These are planning calculations, not verified native trainer behavior. Packing, replacement sampling, distributed sharding, dropping or carrying partial accumulation can change them. Log actual examples/tokens consumed and actual optimizer updates; confirm whether the trainer's steps parameter counts optimizer updates before mapping these numbers to it. Do not automatically train 939 steps if validation worsens after the first epoch.

## 10. FP16, BF16 or FP32: which should we use?

By 'F23' you may mean **FP32**. The inspected Astra precision profiles are fp32, fp16 and bf16; there is no fp23 profile. Do not put f23 into its configuration.

| Format | Meaning for this experiment | Proposed use |
|---|---|---|
| FP32 | 32-bit floating point; reference numerical precision among these formats | Native inspected-path reference and stability diagnosis; costs more memory |
| BF16 | 16-bit format with a wider exponent range than FP16 but fewer fraction bits | First mixed-precision candidate on a supported and qualified device/path |
| FP16 | 16-bit format with narrower range; training may need gradient scaling | Alternative when BF16 is unavailable and stability/quality checks pass |
| INT8 | Quantized storage/execution scheme, not an interchangeable floating-point training dtype | Later serving/compression experiment; re-evaluate the exact deployed artifact |
| NF4/INT4 | Low-bit representations with implementation-specific behavior | Optional genuinely quantized-base adapter training only with a separately qualified backend |

Mixed precision uses different dtypes for different operations; it does not mean converting every tensor to 16-bit. PyTorch documents autocast and gradient scaling as distinct controls. BF16-trained values can overflow FP16's range; inspect finite loss/gradients and the actual model/device combination. [PyTorch automatic mixed precision](https://docs.pytorch.org/docs/2.14/amp.html).

Record base-weight storage, operation compute dtype, adapters/master weights, optimizer states and inference KV dtype separately. Casting an already quantized model to FP32 cannot recover discarded weight information. Saving a smaller checkpoint does not prove smaller training-memory use.

**For this project:** establish native FP32 reference results; then compare an actual BF16 mixed-precision run if the chosen path/device qualifies. Use FP16 only after a stability comparison. Keep an unquantized accepted baseline before trying inference quantization. If BF16 is not wired into the selected trainer, stay with the verified native path or qualify the integration; a documentation setting does not enable it.

The inspected native QLoRA path restores the base to FP32 and its INT4 representation uses an INT8 container. It is not the same as a packed NF4 backend. Genuine low-bit adapter training has separate compatibility requirements described in the [bitsandbytes documentation](https://huggingface.co/docs/transformers/quantization/bitsandbytes). See [Astra-specific quantization findings](02-precision-and-quantization.md).

**No format is guaranteed to produce the best customer replies.** FP32 offers greater arithmetic precision, but factuality also depends on the base checkpoint, reviewed data, evidence, training behavior and application checks. Compare the actual outputs. Retain the smallest/fastest configuration that meets every unchanged quality gate rather than ranking formats by bit count alone.

## 11. Practical run sequence and stopping rule

1. Record the real checkpoint, tokenizer, compatible architecture, trained context and hardware; validate authorized data and the native input adapter.
2. Evaluate the untuned checkpoint on the 200-300 development cases, both with correct evidence supplied directly and with actual retrieval.
3. Prepare the 10,000 accepted training records and isolated validation/release sets. The eight documentation examples are format illustrations, not a sufficient dataset.
4. Run the 1,000-record pipeline check. Confirm target masking, frozen base, correct update counts, finite gradients and save/reload. Then test a 3,000-record candidate from the same base against validation.
5. Run the 10,000-record LoRA experiment with the starting parameters above. Evaluate after one epoch; continue only if factuality, summary completeness and privacy remain acceptable and validation improves.
6. Change one diagnosed variable at a time: learning rate/rank, data coverage, retrieval or precision. Log the change and do not use hidden release labels to select it.
7. Freeze the selected model/adapter, prompt, corpus, precision and runtime configuration; run the independent [quality gates](06-quality-gates.md), including their confidence requirements.
8. Run an agent-reviewed pilot with current evidence and exact-revision approval. No automatic sending, refund or account changes are enabled by training.

Stop or revert on non-finite training, data-rights problems, private-data disclosure or critical unsupported commitments. If training loss falls while factuality worsens, do not add epochs blindly. Add 2,000-3,000 new reviewed records only for diagnosed missing coverage; missing business facts and access bugs require other fixes.

The desired outcome is an independently evaluated support configuration. No data count, epoch count, parameter size or floating-point format is currently certified for this application.
