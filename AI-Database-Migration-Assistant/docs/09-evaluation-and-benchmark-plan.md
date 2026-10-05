# DM evaluation and benchmark plan

All numbers below are proposed qualification targets, not measured results. Register the final corpus, tolerances, severity labels and thresholds before evaluating a release candidate.

## Benchmark construction

Initial target: at least 50 independently authored schema-pair tasks across at least 10 distinct application/schema families, plus at least 30 ambiguity/unsupported-input cases. Include simple renames, type/status conversions, tenant-aware key changes, normalization splits, approved merges, cyclic relationships and an unsupported family. Hold out entire families. Expand based on failures; this minimum is not proof of universal safety.

Each task contains source fixture, target schema/app contract, permitted evidence, expected business interpretation, source-scope manifest, oracle lineage, independent validation queries and explicit ambiguity answers. Execute database cases on real pinned engines; mock tests measure orchestration only.

## Metrics

| Metric | Definition / proposed gate |
|---|---|
| Structured output validity | Parseable and schema-valid proposals / all proposals; report first attempt and repaired separately |
| Supported task success | All independent invariants pass / supported tasks; initial candidate target >=95% before recipe qualification |
| Critical semantic failures | Wrong money, ownership, deletion, status or relationship accepted as correct; zero permitted in qualification suite |
| Ambiguity behavior | Critical unresolved/unsupported cases blocked; zero such cases automatically executed in suite |
| Unattended completion | Correct no-review completions / all in-scope attempted tasks, including failures; do not remove hard cases |
| False escalation | Answerable supported tasks unnecessarily sent for review; report, no initial hard gate |
| Integrity | 100% scoped record disposition, no unexplained loss/duplication, all mandatory invariants pass per migration |
| Recovery correctness | Injected interruption cases recover/resume or stop explicitly without unaccounted effects |
| Performance | Assessment latency, model tokens/time, rows/s, bytes/s, source load, memory/disk, window and recovery duration |

Aggregate 95% task success does not authorize the failing 5%. Automatic production use is restricted to individual qualified recipes and runtime preconditions. Report confidence intervals and task-family breakdowns; zero observed failures is not a proof of zero risk.

## Adversarial and operational cases

Instructions embedded in table comments, code comments and customer text; forged schema identifiers; huge binary fields; invalid UTF-8; secrets in exception strings; changed schema after approval; new enum values; cross-tenant joins; duplicate operation IDs; lease expiry; concurrent workers; loss of commit acknowledgement; disk exhaustion; snapshot expiry; interrupted restore and a cutover crash after routing changes.

## Baselines and ablations

Additional challenge coverage from the [gap review](19-gap-review-and-acceptance-register.md): filtered scope with unauthorized dependent records; lossy transformation disguised as cleanup; required missing attachment; model/recipe revocation with queued work; restored journal older than target receipts; incompatible metadata upgrade; and invented application-ready claims when authentication or derived-state checks have not passed. Model tests grade proposal/abstention/report behavior; real-system tests independently exercise execution and recovery. Passing a text answer about recovery does not prove the recovery implementation works.

Compare manually configured deterministic recipe, current Astra, Astra plus retrieval, and trained Astra plus retrieval under identical budgets and inputs. Separate mapping success from runner bugs. Record reviewer time, retries and total resource cost as well as model latency. Do not train against an evaluation failure then report that same case as unseen.

## Evidence manifest

Corpus/version/hash and split lineage; engine/driver/app versions; model/tokenizer/checkpoint hash; prompt/retrieval/DSL/compiler versions; host configuration; policy; all attempts and discarded candidates; measured results; uncertainty; failures; reviewer. Use [release evidence template](../templates/release-evidence.md).
