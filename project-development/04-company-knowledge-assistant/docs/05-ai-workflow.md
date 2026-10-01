# Permission-aware retrieval, explanations and evaluation

Pipeline: authenticate -> resolve tenant/groups and question context -> select accessible published/effective sources -> retrieve -> assemble authorized evidence -> explain with citations -> check support and current access/freshness -> answer, clarify or report an evidence gap.

Enforce access before scoring and before any passage reaches the model. Filter autocomplete, snippets, counts and analytics too. Use exact identifiers and lexical retrieval as a measured baseline; adopt hybrid/learned retrieval only after a relevant comparison. A broad shared index is acceptable only if its query path proves these guarantees.

Preserve headings, definitions, effective dates, exceptions, conditions, obligations, numbers, units and negation during chunking/summarization. Link cross-section dependencies rather than explaining an exception without its rule. DOCX section anchors and PDF page labels must resolve to the original revision. Parsing success is not publication approval.

Resolve policy applicability through explicit site/audience/effective-date metadata, not upload time or general recency ranking. When scope is ambiguous, ask for necessary non-sensitive context. Conflicting authoritative sources remain visible to authorized users and go to the owner; a model cannot invent precedence. An expired review date follows an explicit freshness policy; do not silently assume the content is current.

Explanations distinguish the cited policy from a summary. Material claims cite supporting passages, and no missing entitlement or exception is inferred. Citation validation checks source IDs/hashes/spans/access; independent support review checks whether the cited text actually entails the claim. If evidence is insufficient, return a useful authorized source result or a gap outcome without fabricated certainty.

Treat uploaded instructions as data; they cannot change grants, publication rules or tools. Revalidate history on follow-ups, group changes and source withdrawals. Never reuse hidden passages from prior answers to answer a now-unauthorized question. Cache invalidation and final delivery checks handle changes during generation.

Gap workflow: retain raw questions privately by default with a defined retention period. Employee submits to an identified owner scope or a disclosed, authorized review policy governs capture. Dashboards show only questions their reviewers may see. Aggregate trends require small-group suppression and restricted drill-down; content managers do not inherit blanket employee-history access. An owner response becomes reusable knowledge only through publication review.

Evaluation: permitted documents and independently labelled employee questions plus synthetic negatives. Split by document family/revision and paraphrase clusters so near-identical questions do not leak. Include group transfers, revoked users, nested or conflicting grants, future/expired policies, site exceptions, adversarial documents, no-answer/conflict questions, citation failures and multi-turn permission changes.

Pre-register numeric thresholds and sample minimums with reviewers. Measure retrieval recall@k, answer accuracy/support, citation correctness, effective-policy selection, correct abstention, critical exception retention, time to locate information, repeated questions resolved, latency and cost. Report denominators, no-answer coverage and breakdowns by audience/topic. Adoption uses privacy-conscious aggregate measures and is not an employee performance score. Any unauthorized disclosure or critical unsupported policy assertion observed in release evaluation blocks release until fixed and re-evaluated. No result or numeric threshold is claimed yet.
