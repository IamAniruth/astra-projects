# Support Reply Assistant: dataset, training and quality guidance

Prepared: 1 October 2026. Status: **Proposed engineering guidance; no model has passed these gates.**

The objective is reliable, evidence-supported drafts that agents review before customer handoff. No parameter count, quantization type or configuration guarantees perfect output. Choose a model by measured task performance and release only the exact evaluated model, data, prompts, retrieval and runtime combination.

## Recommended starting decision

1. Audit and benchmark the actual Astra checkpoint first. Do not start a large training run or hardware purchase from an assumed parameter count.
2. For planning, compare a capable pretrained/instruction-tuned **3B-4B candidate** with a **7B-8B candidate** if compatible checkpoints and resources are available. Use 7B-8B as the main capacity-planning hypothesis, not a minimum requirement or a proven Astra capability. Models above 8B and foundation pretraining are outside this initial support-adapter plan.
3. Establish an unquantized reference on the actual execution path. Astra's inspected quantized loader restores weights to FP32. BF16/FP16 runtime savings require separate path/hardware qualification.
4. Test INT8, then INT4 only after reference quality passes. Astra's current INT4 path is unpacked INT8 storage plus FP32 computation; it is not equivalent to packed NF4/AWQ.
5. Begin with approximately 2,000 independently reviewed development examples, then a 10,000-example SFT pilot if the baseline shows learnable skill gaps. Keep current policies in retrieval and live orders in authorized queries.
6. Use severity-specific gates: **zero observed critical failures**, a proposed **<=2% upper-confidence-bound major failure rate**, and explicit coverage, privacy, factuality and runtime tests. See the complete definitions before using these figures.
7. Keep agent approval mandatory. A zero-failure test result is not a zero-risk guarantee.

The training recipe is **20% summaries, 35% grounded replies, 15% missing-evidence/clarification, 10% policy cases, 10% privacy/injection, 5% structured extraction and 5% multi-turn corrections**. It totals 10,000 training examples inside a proposed 20,000-record collection/evaluation budget; see the training recipe below for all denominators and counts.

These sizes, dataset budgets and thresholds are **our proposed experiment policy**, not industry standards or measured results. Owners should register or revise them before evaluation; never relax a gate after seeing a failing result.

## Reading order

1. [11: Required knowledge, skills, data preparation and review](11-required-knowledge-and-skills.md)
2. [12: Dataset percentages, counts, examples and training configuration](12-dataset-types-reasoning-and-samples.md)
3. [02: Precision and quantization](02-precision-and-quantization.md)
4. [14: Minimum/recommended hardware, GPU costs and run budget](14-hardware-cost-and-run-budget.md)
5. [05: Inference, retrieval and application configuration](05-runtime-configuration.md)
6. [13: Repetition controls and implementation readiness](13-repetition-controls-and-readiness.md)
7. [06: Quality gates and statistical evidence](06-quality-gates.md)
8. [07: Release sequence and ownership](07-release-playbook.md)
9. [08: Local evidence and primary references](08-evidence-and-references.md)
10. [Configuration and dataset templates](templates/README.md)

Overlapping guidance has been consolidated. Retained document numbers stay unchanged so existing links remain stable.

The templates are planning records, not executable Astra launch/training configurations. No models were downloaded, accounts connected, packages installed or training started. Existing project statuses remain Planned.

Return to [project README](../README.md) and [project status](../_STATUS.md).
