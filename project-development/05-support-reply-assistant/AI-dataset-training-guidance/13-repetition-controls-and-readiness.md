# Repetition controls and what is still required

Scope: Support Reply Assistant. Inspected 1 October 2026. This is documentation only; no shared decoder, gateway schema, environment variable or runtime process was changed.

## Repetition penalty is a serving control

A repetition penalty adjusts generated-token scores during decoding. It can reduce loops without changing model weights, but cannot guarantee factuality or repair a weak base model. Test it before assuming every loop requires retraining. Also investigate prompt/chat formatting, EOS handling, context truncation, duplicated training examples and checkpoint quality.

The statement 'changes serving code that every model uses' is too broad for the inspected repository:

| Path | Observed behavior |
|---|---|
| [reasoning_runtime.py](../../../../astra-llm/codebase/src/astra_llm/reasoning/reasoning_runtime.py) | Implements discourage_repeats; penalizes generated tokens, not the prompt; supports repetition_penalty 1.0-2.0 and no_repeat_ngram_size 0 or 2-32 |
| [chat constants](../../../../astra-llm/codebase/src/astra_llm/chat_server/_constants.py) | Reads ASTRA_CHAT_REPETITION_PENALTY, default 1.1, and ASTRA_CHAT_NO_REPEAT_NGRAM, default 6 |
| [local chat runtime](../../../../astra-llm/codebase/src/astra_llm/chat_server/runtime.py) | Passes those settings to its bounded reasoning runtime |
| [versioned chat schema](../../../../astra-llm/codebase/docs/gateway/v1/schemas/chat.request.json) | Does not expose either field; additional properties are rejected |

Thus a control already exists on one path. Its presence does not prove every model, endpoint or worker uses it. The local chat settings are process-level values; an eventual change can affect other users/checkpoints of that path. No product-wide global change is recommended without regression evidence.

## Proposed support-specific experiment

1. Freeze checkpoint, tokenizer, prompt, retrieved evidence, token cap and test cases. Record the actual endpoint/decoder.
2. Capture current-path behavior: local chat defaults are 1.1/6, while the underlying generator defaults are 1.0/0. Do not confuse these baselines.
3. On a qualified isolated experiment path compare penalty 1.0, 1.05 and 1.1 with n-gram blocking disabled (0). These are trial settings, not a promised fix.
4. If loops persist, separately compare no-repeat n-gram 6 against 0 at the selected penalty. Do not change model, dataset, precision and decoder together.
5. Score loops, supported reply quality, exact product/order identifiers, policy negation, citations, JSON validity and repeated wording that is legitimately necessary.
6. Retain only settings that reduce loops without violating existing quality gates. Repeated words can be necessary in support replies; aggressive penalties or hard blocking can damage them.
7. If these controls are needed on the versioned gateway, design typed contract validation, path wiring, per-request/profile scope, tests and rollback explicitly. Do not just send unknown JSON fields or expose the local demo API.

Use developer cases containing real looping failures plus normal controls, not the hidden release set for tuning. Define an unacceptable-loop rubric before scoring; record case-level incidence and length-limit versus EOS finishes. A loop-free but invented refund promise is still a critical failure. No repetition experiment was run for this document.

## Do we need more files?

The folder now covers the main planning topics. The missing work is evidence and actual implementation inputs, not an unlimited number of generic documents.

| Required artifact | Current situation / next step |
|---|---|
| Approved dataset and split manifests | Recipes/examples exist; real permitted, reviewed records still need collection |
| Actual checkpoint/tokenizer inventory | Record hashes, total/trainable parameters and qualified context |
| Native training input adapter | Map annotation JSONL to the actual loader with verified target masking |
| Executable training configuration | Derive from verified trainer fields; existing JSON templates remain planning-only |
| Executable serving configuration | Pin model, identity, budgets and supported decoder controls; no default broad permissions |
| Host and budget record | Populate [hardware/cost worksheet](14-hardware-cost-and-run-budget.md) from actual quotes and benchmarks |
| Baseline and training evaluation results | Run the documented summary/oracle-evidence/retrieval comparisons |
| Release scorecard and restore/rollback evidence | Keep pending until the exact deployed combination passes |

Keep runtime configuration separate from dataset content. A dataset example should not modify global serving settings. GPU size and repetition controls are necessary engineering decisions, but neither certifies reply quality.
