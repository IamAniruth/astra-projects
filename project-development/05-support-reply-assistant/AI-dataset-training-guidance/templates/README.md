# Templates and how to use them

- [Training run budget](training-run-budget.json): dated hardware/cloud quote, GPU/CPU/RAM, run hours and total-cost assumptions. Unknown costs remain null; see [cost guidance](../14-hardware-cost-and-run-budget.md).
- [Eight synthetic learning examples](support-learning-examples.jsonl): one JSON record per line, covering every primary skill plus knowledge-use and communication subgroups. Illustration only; independent review and a native-loader adapter are required before training. See [brief sample guide](../12-dataset-types-reasoning-and-samples.md).
- [Dataset mixture](dataset-mixture.json): proposed skill, topic, provenance and collection percentages. Each dimension has its own denominator; no data has been collected.
- [Candidate profile](candidate-profile.json): proposed settings plus unresolved checkpoint/host fields. **Not accepted by Astra CLI**; map only verified fields to the actual trainer/launch/request schemas.
- [Synthetic dataset example](synthetic-example.json): illustrates case visibility, evidence, missing live facts and expected behavior. It is not a production training record or a native Astra instruction schema; implement/verify an adapter before ingestion.
- [Release scorecard](release-scorecard.json): empty observations and pending verdicts. A threshold is not a measurement; do not replace unknown counts with zero.

Copy records for each experiment, keep source templates unchanged and store sensitive evidence outside this documentation folder. Register dataset rights, split grouping and metric protocol before collecting release evidence.

Each observed gate needs eligible denominator, failure count, confidence method/bound where applicable, supported slices, evidence path and reviewer decision. Keep quantization paired-difference analysis separate from binomial failure bounds. Runtime outage correlation and non-independent cases need additional analysis.

Templates do not launch training, grant access or enable any automatic customer action. See [quality gates](../06-quality-gates.md) and [training plan](../12-dataset-types-reasoning-and-samples.md).
