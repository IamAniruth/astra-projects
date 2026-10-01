# Precision and quantization

For a plain-language FP32/BF16/FP16 comparison and the support project's proposed training choice, see [the practical training recipe](12-dataset-types-reasoning-and-samples.md). Greater numerical precision alone does not establish better reply quality.

## What the inspected Astra code actually does

[serving/quantization.py](../../../../astra-llm/codebase/src/astra_llm/serving/quantization.py) supports fp16, bf16, int8 and int4 stored weights. Its integer scheme is symmetric per-tensor scaling. INT4 values occupy an INT8 tensor/container; serialization writes that container directly. load_quantized_model dequantizes parameters to FP32 before loading them. Thus smaller artifacts do not establish low-bit resident memory or low-bit kernel acceleration.

[training/peft_adapters.py](../../../../astra-llm/codebase/src/astra_llm/training/peft_adapters.py) describes its QLoRA path as a frozen quantized-then-dequantized FP32 base with LoRA adapters. It is not the NF4 low-memory execution described in the external QLoRA paper. Its adapted modules are query/value, not an arbitrary all-linear selection.

[precision_profiles.py](../../../../astra-llm/codebase/src/astra_llm/training/precision_profiles.py) separately provides precision qualification mechanisms. That does not prove the quantized serving loader or the deployed gateway uses those modes. Check the selected training and serving paths separately.

## Proposed decision matrix

| Format/method | Use | Qualification |
|---|---|---|
| FP32 | Current-path reference and numerical diagnosis | Establish support-task quality and memory first |
| BF16 | Candidate unquantized training/inference baseline on a qualified path/device | Prove actual execution dtype and task parity |
| FP16 | Alternative on compatible devices/path | Check overflow/underflow and training loss scaling; no universal preference |
| INT8 | First compression experiment after reference acceptance | Compare actual served outputs, memory and latency |
| Packed 4-bit AWQ or another compatible weight-only method | Optional memory-constrained serving experiment | New engine/model integration unless demonstrated; calibrate and retest |
| NF4 QLoRA | Optional adapter training with a frozen low-bit base in a compatible backend | New integration; not a drop-in Astra scheme name |
| 2-bit/3-bit or unqualified KV quantization | Deferred | Do not include in the first supported release |

NF4, double quantization and paged optimizers are techniques described by the original [QLoRA paper](https://arxiv.org/abs/2305.14314). They do not establish a particular support-domain accuracy. Weight storage, compute dtype, activation dtype, KV dtype and optimizer-state precision are separate settings. The [Transformers bitsandbytes documentation](https://huggingface.co/docs/transformers/quantization/bitsandbytes) describes compatible quantized layers and hardware requirements; compatibility with Astra's custom model must be established independently.

AWQ is a weight-only quantization method with its own implementation/calibration requirements, not a synonym for every INT4 checkpoint. [AWQ paper](https://arxiv.org/abs/2306.00978).

## Experiment order and gates

1. Freeze an accepted reference checkpoint, tokenizer, prompts, retrieval corpus and held-out protocol.
2. Use an initial 200-500 sequences from the separately reserved 1,000-case calibration pool where a method requires calibration. The remainder supports calibration validation; it never becomes release evidence. Cover long tickets, numbers, negation, private notes and policy exceptions; never use release holdout for calibration.
3. Quantize one candidate at a time. Compare identical requests and retrieved evidence to isolate quantization; then re-run full end-to-end tests.
4. Measure actual artifact size, loaded device/host memory, prefill/decode latency, p95 end-to-end latency and generated quality. Record the dequantization/copy path and startup peak.
5. Proposed non-inferiority gate: at most 0.5 percentage-point loss in the primary case-pass rate, with a one-sided 95% paired confidence bound on the degradation no greater than 0.5 points. All absolute release gates also apply; zero observed new critical failures.
6. Use a paired case-level bootstrap or another pre-registered paired method; clusters are complete cases, not individual claims/tokens. If evidence is too weak to resolve a 0.5-point margin, collect more independent cases or retain the reference. An unchanged score on a tiny set is inconclusive.
7. If INT4 fails, retain INT8 or the reference. Do not lower quality targets solely to fit available hardware.

Quantization calibration data and release evaluation data are separate. If LoRA adapters are merged into a base and the result is requantized, evaluate that final artifact again. A passing adapter on one base/precision does not qualify another combination.
