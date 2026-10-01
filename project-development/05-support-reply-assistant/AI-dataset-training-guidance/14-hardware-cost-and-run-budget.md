# Support training: GPU, CPU, RAM and cost worksheet

Prepared: 1 October 2026. Scope: the planned 10,000-training-record adapter experiment with separate development/evaluation data. Hardware tiers are unmeasured estimates. No GPU, cloud account or instance has been purchased or provisioned.

## Native Astra adapter path

The inspected [PEFT implementation](../../../../astra-llm/codebase/src/astra_llm/training/peft_adapters.py) restores its quantized base to FP32. Plan resident training memory accordingly; an INT4 file does not imply packed low-bit compute.

| Project candidate | Minimum constrained trial: RAM / physical CPU cores / GPU VRAM | Recommended benchmark host | Upper planning tier | Free NVMe |
|---|---|---|---|---|
| 3B-4B lower-resource challenger | 64 GB / 12 cores / 24 GB | 128 GB / 16 cores / 48 GB GPU | 256 GB / 24 cores / 80 GB GPU | 1-2 TB |
| 7B-8B main comparison | 128 GB / 16 cores / 48 GB | 128-256 GB / 16-24 cores / 80 GB GPU | 256 GB / 32 cores / 96 GB or larger GPU | 2 TB |

GPU VRAM is per device, storage is available working capacity, and backups are additional. No compatible 3B-8B Astra checkpoint or measured training fit is established by this table. If the actual existing checkpoint is smaller, size that checkpoint from measurements rather than buying for an assumed future model.

## Optional optimized QLoRA for the same support task

Only applies after separately qualifying a backend/model that keeps the frozen base genuinely packed in 4 bits and trains adapters. It is not current native Astra behavior.

| Project candidate | Minimum constrained trial: RAM / physical CPU cores / GPU VRAM | Recommended benchmark host | Upper planning tier | Free NVMe |
|---|---|---|---|---|
| 3B-4B | 32 GB / 8 cores / 12 GB | 64 GB / 12 cores / 16-24 GB GPU | 128 GB / 16 cores / 48 GB GPU | 500 GB-1 TB |
| 7B-8B | 32-64 GB / 8 cores / 16 GB | 64 GB / 12-16 cores / 24 GB GPU | 128 GB / 24 cores / 48 GB GPU | 1-2 TB |

Compatible quantized layers and hardware must be checked against the chosen implementation. [bitsandbytes documentation](https://huggingface.co/docs/transformers/quantization/bitsandbytes). These table values remain project planning estimates, not source guarantees.

## Assumptions and limits

One adapter-training job; dense model; rank 8-16; microbatch 1; accumulation to effective batch 32; no simultaneous serving/reference model. Initially test 512-2,048 total tokens only where the checkpoint/trainer supports the length, using verified gradient checkpointing if available. More context, adapter coverage, vocabulary or loader copies can exceed these estimates.

The lower tier is an experiment candidate, not guaranteed minimum hardware. Use a supported 64-bit CPU, adequate memory bandwidth/PCIe and pinned GPU drivers/kernels; core count or VRAM alone does not establish throughput. More host RAM does not automatically replace VRAM. Multiple GPUs do not pool memory without validated sharding; no such multi-GPU deployment is selected for this support pilot.

Keep at least 20% measured GPU headroom through load, backward, optimizer step, evaluation and checkpoint serialization. NVMe must cover base weights, two retained checkpoints, temporary copies, tokenized examples and logs. The dataset record count mainly affects training duration; longer examples affect both duration and peak memory.

## Timing this project's dataset

At an illustrative average of 1,000 processed tokens per training example, 10,000 examples represent about 10 million tokens per epoch. Three epochs present about 30 million tokens. Separate validation and release processing is extra. Repeating epochs does not create new unique examples.

Time estimate = processed training tokens / measured training tokens per second. At an illustrative 500 tokens/second, one 10-million-token epoch takes about 5.6 hours before other work. This is arithmetic, not Astra or GPU benchmark evidence. Do not substitute inference throughput.

Run 50-100 optimizer steps including longest supported cases, an evaluation batch and save/reload before committing to full training. Record peak host/device memory, processed tokens/second, checkpoint size, non-finite/OOM behavior and actual compute dtype.

Full-parameter tuning, foundation pretraining, generic cluster sizing and models above 8B are outside this initial support-adapter hardware plan. If the 3B-8B candidates fail after data/retrieval corrections, make a separate evidence-based scope/budget decision. More expensive hardware does not independently improve [factual quality](06-quality-gates.md).

## Weight-only memory bounds for the project candidates

Decimal GB, excluding activations, cache/workspace, adapters, optimizer state, copies and overhead.

| Parameters | FP32 | BF16/FP16 | INT8 | Truly packed 4-bit |
|---|---:|---:|---:|---:|
| 3B | 12 GB | 6 GB | 3 GB | 1.5 GB |
| 4B | 16 GB | 8 GB | 4 GB | 2 GB |
| 7B | 28 GB | 14 GB | 7 GB | 3.5 GB |
| 8B | 32 GB | 16 GB | 8 GB | 4 GB |

Calculation: parameters x bytes per parameter / 1,000,000,000. These are not training fit specifications. The inspected native Astra INT4 path stores values in INT8 containers and restores FP32 for model execution. Do not apply the packed 4-bit column to that path.



Cloud vCPUs are not interchangeable with physical CPU cores. CPU names or GHz alone do not establish preprocessing performance.

## Published cloud price examples

Snapshot checked against [Lambda's official instance page](https://lambda.ai/instances) on 1 October 2026. These are its listed **one-GPU** examples in USD; applicable taxes are extra and availability/region can change. They are price references, not tested Astra hosts or booking quotes.

| One-GPU instance | GPU VRAM | Listed vCPUs | Host RAM | Included SSD | USD/hour | 10 allocated hours | 50 allocated hours |
|---|---:|---:|---:|---:|---:|---:|---:|
| A10 | 24 GB | 30 | 226 GiB | 1.3 TiB | 1.29 | 12.90 | 64.50 |
| A6000 | 48 GB | 14 | 100 GiB | 512 GiB | 1.09 | 10.90 | 54.50 |
| H100 PCIe | 80 GB | 26 | 225 GiB | 1 TiB | 3.29 | 32.90 | 164.50 |

Rows are not performance-ranked. A cheaper GPU-hour can need more hours. Published bundles may miss project targets: the A6000 row has less RAM and disk than the native 3B-4B planning tier; the H100 row has less local disk than the 2 TB working-space target. Qualify or augment the whole instance rather than choosing only by VRAM. A10's price does not make native 7B FP32 fit in 24 GB.

Allocated hours include setup, loading, training, validation, failed attempts and idle time while still billed. These 10/50-hour examples are multiplication only, not predictions of training duration. For another provider, obtain the exact region/instance/billing-type quote and attached-storage costs; avoid comparing inference/serverless rates with training instance rates.

## Calculate the complete experiment cost

Cloud total = allocated instance-hours x instance-hour rate + separately billed storage/backup + transfer charges if applicable + tax + payment/conversion charges + human data-review cost.

For a GPU-hour rate on a multi-GPU bundle, multiply by GPU count before instance-hours. Do not multiply a whole-instance price by GPU count again. Record the quote's units. Do not double-charge RAM/CPU already bundled in the selected price.

Illustration: one H100 PCIe instance at the cited 3.29 USD/hour for 30 allocated hours = 98.70 USD compute. A proposed 20% compute contingency adds 19.74 USD, giving 118.44 USD before unquoted storage, tax and review costs. This is a budget example, not a completed job or cost guarantee. Three such experiments would require three times the compute budget unless actual measured hours differ.

INR payable estimate = quoted USD subtotal x dated provider/card INR-per-USD rate + applicable fees/taxes. No exchange rate or India retail price is invented here. If buying locally, collect INR quotations for exact parts and tax treatment; currency conversion alone is not a local hardware purchase quote.

## Local purchase bill of materials

Record an actual dated supplier quotation for each line. Prices remain unknown until parts, region and warranty are selected.

| Item | Required quote information |
|---|---|
| GPU | Exact model, VRAM, supported precision/kernels, power, cooling, warranty and new/used condition |
| Processor | Model, physical cores, memory support, PCIe capacity and compatibility |
| RAM | Installed usable capacity, DIMM layout, expandability and ECC requirement if selected |
| Motherboard/chassis | GPU fit, slots/lanes, RAM capacity and sustained cooling |
| NVMe and backup | Free working capacity, checkpoint-write needs and separate recovery storage |
| PSU/electrical | Sufficient rated capacity/connectors for sustained machine load |
| Software/support/network | OS/runtime compatibility, installation/support costs and connectivity |
| Tax/shipping/warranty | Included versus additional amounts and coverage period |
| Running cost | Measured whole-system wall power, local electricity rate and expected utilization |

Local operating electricity cost = measured whole-system kW x run hours x electricity price per kWh. For an illustrative 0.6 kW machine over 50 hours, energy is 30 kWh; multiply by the actual local tariff. Do not use GPU TDP alone as total wall power.

Simple break-even hours = purchase cost / (comparable cloud hourly cost - local variable hourly cost), only when the denominator is positive and workload throughput is comparable. Also consider depreciation, downtime and resale. It is not enough to compare one desktop price with an unrelated cloud GPU rate.

## Before approving spending or a long run

1. Identify the actual checkpoint and native/optimized training path.
2. Run the 50-100-step benchmark described above; record peak host/device RAM, tokens/second, checkpoint size and restore behavior.
3. Estimate consumed tokens/updates, validation and experiment count using [document 12](12-dataset-types-reasoning-and-samples.md).
4. Fill the [budget template](templates/training-run-budget.json) with a dated quote, units, hours, storage, tax and review assumptions. Unknown is null, not zero.
5. Confirm data processing permissions for any cloud location, then use a short authorized trial before committing to longer capacity. No upload or provisioning is authorized by this document itself.
6. Recheck prices when booking. Keep actual invoices, hours and measurements separate from this planning estimate.

Repetition penalties operate during reply generation and do not themselves create a training-GPU requirement. Train only when the measured problem is a learnable model skill, not a decoder setting, missing fact or access-control defect.
