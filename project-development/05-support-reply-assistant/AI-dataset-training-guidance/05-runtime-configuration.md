# Inference, retrieval and application configuration

For existing local-chat repetition controls and their difference from the versioned gateway contract, see [repetition controls and readiness](13-repetition-controls-and-readiness.md). Their existence on one path does not establish support on every endpoint.

## Actual Astra boundary

The inspected [chat schema](../../../../astra-llm/codebase/docs/gateway/v1/schemas/chat.request.json) allows max_new_tokens from 1 to 1024, messages, response_format, deadline_seconds and verification_tasks among other fields. It does not expose temperature or top_p and rejects additional properties. The 100,000-character message allowance and 64-message count are transport limits, not proof of usable model context.

The [launch example](../../../../astra-llm/codebase/docs/gateway/v1/launch.example.json) contains checkpoint/device, REST/gRPC listeners, audit path, principal key-environment references and concurrency/rate/deadline limits. Its example broad permissions and numerical limits are not production approval. Use server-managed least-privilege identities and prove tenant/case isolation.

Stack profile names are local-cpu and cuda-cu130 with Python 3.12 in the inspected profile module. These environment profiles do not select a model size or prove reduced-precision execution.

## Proposed initial application settings

| Area | Proposal and boundary |
|---|---|
| Summary output cap | Start with 256 new tokens; increase only if completeness needs it and total context fits |
| Draft output cap | Start with 512 new tokens; maximum current API cap 1024, not an instruction to use all of it |
| Context | Use min(trained limit, measured qualified limit, runtime limit); reserve output and formatting first |
| Retrieval | Initial top-k 4 passages; compare 2/4/6, preserving complete policy exceptions |
| Chunking | Candidate 200-400 tokens with 40-80 overlap only if context fits; otherwise smaller source-aligned spans |
| Decoding | Record actual native behavior; if another qualified engine exposes sampling, test deterministic/low-temperature baseline separately |
| Concurrency | Start at 1; raise only after quality, memory and latency under load pass |
| Deadline | Candidate 60 seconds bounded end-to-end; cap retries and distinguish timeout from no evidence |
| Budget | Count case/history + instructions + evidence + output against actual tokenizer; do not silently drop mandatory context |
| Failure behavior | Typed failure or needs-review; never return truncated text as a complete approved reply |
| Actions | Agent approval required; automatic send/refund/account changes disabled |
| Facts | Authorized customer-bound snapshots with source-specific TTL; missing/expired facts block unsupported claims |

These are proposed application settings, not all native config keys. For a 512-token context, a 512-token output allocation leaves no room for input; it is invalid. Do not apply the illustrative caps without calculating the actual budget.

An 8,192-token *qualified* context could budget 512 instructions + 3,072 case/history + 2,048 evidence + 512 output + 2,048 reserve/formatting. This is an example sum, not a claim that Astra's selected checkpoint supports 8K. Run long-context tests before expanding context; changing RoPE alone is insufficient.

Validate output schema at the product boundary. response_format acceptance does not by itself prove constrained decoding or valid output. Separate summary fields, public reply, internal evidence and review blockers. Generated confidence scores cannot replace checks.

## Freshness, security and latency

Scope retrieval, caches and histories to current tenant/agent/case grants. Bind draft approval to case, source and fact revisions; recheck at export. Never include internal citations in the public reply unless explicitly approved for public disclosure. PII access and external disclosure are different permissions.

Proposed user-experience goals: p95 completed summary <=10 seconds and completed draft <=20 seconds at the registered input distribution/concurrency; total request timeout <=60 seconds. These are product goals, not measured hardware performance. Record queue time, prefill, decode and timeout rates separately. A slower configuration can support a labelled experiment, not a claim that these release targets passed.

Record actual request/config schema versions and disable unsupported controls. The [candidate profile](templates/candidate-profile.json) is deliberately marked non-executable and has unresolved checkpoint/hardware fields.
