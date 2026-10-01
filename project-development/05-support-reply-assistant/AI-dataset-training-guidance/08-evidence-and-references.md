# Evidence and primary references

Read date: 1 October 2026. Local-source inspection and public primary-source research informed this guide. Suggested sizes, sample budgets, hyperparameter search ranges, failure tolerances and latency targets are engineering proposals, not figures validated by the cited papers for this product.

## Local Astra evidence

- [PI status](../../../../astra-llm/codebase/command-documentation/7-PI_STATUS.md), SHA-256 D2D3FEF52DC61517A26E1ED1723F6DE4EC0D76761335996CFDD807E3307CF8F9.
- [Transformer architecture config](../../../../astra-llm/codebase/src/astra_llm/transformer/config.py): architecture/context/LoRA fields; no loaded-checkpoint parameter inventory was run.
- [Quantization](../../../../astra-llm/codebase/src/astra_llm/serving/quantization.py): symmetric per-tensor quantization, INT4 in INT8 container, raw container serialization, FP32 dequantized model loading.
- [PEFT adapters](../../../../astra-llm/codebase/src/astra_llm/training/peft_adapters.py): query/value LoRA and disclosed quantized-then-dequantized base behavior.
- [Precision qualification](../../../../astra-llm/codebase/src/astra_llm/training/precision_profiles.py): separate training precision capability/qualification controls.
- [Instruction tuning config](../../../../astra-llm/codebase/src/astra_llm/training/instruction_tuning/config.py): native fields and defaults, not a production recipe.
- [Stack profiles](../../../../astra-llm/codebase/src/astra_llm/platform/stack_profiles.py): local-cpu/cuda-cu130, Python 3.12 and environment boundaries.
- [Chat request schema](../../../../astra-llm/codebase/docs/gateway/v1/schemas/chat.request.json): max_new_tokens <=1024; no temperature/top_p fields.
- [Gateway launch example](../../../../astra-llm/codebase/docs/gateway/v1/launch.example.json) and [release checklist](../../../../astra-llm/codebase/docs/platform-scaling/release-checklist.md): example controls versus remaining production qualification.
- [Product AI workflow](../docs/05-ai-workflow.md): agent-reviewed drafting and customer/source boundaries.

Findings apply to the inspected paths, not every possible backend in the repository. No training, serving benchmark or hardware qualification was rerun.

## External primary references

- [PyTorch automatic mixed precision](https://docs.pytorch.org/docs/2.14/amp.html): autocast, gradient scaling and numerical-stability caveats; cited documentation version is not an instruction to change Astra's pinned runtime.
- [Transformers GPU memory usage](https://huggingface.co/docs/transformers/model_memory_anatomy): training memory components; concrete host/GPU tiers in document 14 are project estimates and were not benchmarked.
- [Training Compute-Optimal Large Language Models](https://arxiv.org/abs/2203.15556): joint model/data scaling; not a support-specific model-size guarantee.
- [QLoRA](https://arxiv.org/abs/2305.14314): NF4, double quantization and memory-efficient adapter training in its own evaluated setup.
- [AWQ](https://arxiv.org/abs/2306.00978): activation-aware weight-only quantization; not native Astra support.
- [Transformers bitsandbytes documentation](https://huggingface.co/docs/transformers/quantization/bitsandbytes): compatible quantized layers, compute/storage distinctions and hardware requirements. Verify pinned versions at implementation.
- [NIST exact binomial confidence limits](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/exacbino.htm): one-sided/two-sided limits for binomial proportions.

No model provider or external training service is selected, and no package versions are implied by citing current documentation.
