# Company Knowledge Assistant: admin panel specification

Prepared: 4 October 2026  
Project: CK | Status: Planned; documentation only, implementation not started  
Reference: [Support Reply administration](../../05-support-reply-assistant/docs/09-admin-panel-specification.md) and [Manual Assistant administration](../../03-manual-and-troubleshooting-assistant/docs/09-admin-panel-specification.md)  
Delivery: [PI-08 and S22-S24](../PI/PI-08-admin-panel/README.md)

## 1. Purpose and boundaries

A focused admin area is needed for workspace/group access, document ownership and publication, policy applicability, private knowledge-gap review, subscriptions and operational recovery.

Build within the proposed React/TypeScript frontend and Next.js business APIs with private Astra integration, subject to S02 validation. Workspace administrators configure their organization; platform operators manage the service. Neither role automatically grants access to all documents, employee questions or conversations.

Reuse existing publication, identity, query, gap, job and entitlement services. S01 discovery and S02 feasibility still govern implementation. Administration adds no automatic HR/finance decisions, business actions, eligibility inference from unrelated personal data, external-system changes or unqualified connectors.

Initial scope is permitted uploads, authorized search, cited explanations and restricted gap review. Generated explanations and owner replies do not become company policy without publication review.

## 2. Screens and navigation

Illustrative routes are /settings for workspace administration and /admin for platform operations. Backend checks protect every action, aggregate and artifact independently of navigation.

| Screen | Scope | Purpose |
|---|---|---|
| Overview | Separate workspace/platform | Onboarding, publication backlog, safe gap trends, usage and health |
| People, groups and access | Workspace | Membership, delegated grant ownership, group changes and revocation |
| Document library | Authorized content owners | Drafts, source versions, ownership, audience and effective dates |
| Publication and applicability | Authorized reviewers | Exact-revision review, site/department context, conflicts and withdrawal |
| Parsing and indexing | Scoped workspace; safe platform metadata | Parser failures, locators, index generation and readiness |
| Knowledge gaps | Explicit review audience | Submitted questions, permitted evidence, owner assignment and outcomes |
| Plans and usage | Workspace billing permissions | Seats/document limits, subscription, renewal and allowance ledger |
| Service customers | Platform | Onboarding, billing reconciliation and scoped support |
| Supported scope | Configuration permissions | Qualified specialty, language and input formats |
| Health, audit and data requests | Scope-limited | Incidents, retention, export/deletion, recovery and evidence |

Use searchable paginated lists, accessible labels and keyboard interaction, and explicit loading/empty/error states. Show selected workspace, environment, display time zone and observation time. Titles, snippets, counts, filters and autocomplete must not reveal inaccessible sources.

## 3. Proposed roles and access

Confirm combinations and delegated authority in S03/S04.

| Role | Responsibility | Boundary |
|---|---|---|
| Workspace owner | Organization, membership and separately granted billing | No blanket document or employee-history access |
| Access administrator | Authorized group/member management and delegated source grants | Cannot grant beyond own authority or create platform privileges |
| Content owner/publisher | Review assigned sources, audience, effective dates and lifecycle | Publication does not mean company-wide access |
| Gap reviewer | Questions explicitly shared with the assigned review scope | No default access to private conversations or other reviewers' queues |
| Employee | Search, questions and own history within current grants | Cannot change policy or publish shared knowledge |
| Auditor/viewer | Read specifically permitted audit/evidence | No unrestricted content or mutations |
| Platform operations | Redacted health/job metadata and controlled support | Customer content requires an approved scoped grant |
| Platform billing/access permissions | Service billing or operator membership | No implied content ownership or policy decision authority |

Require individual privileged accounts, MFA, secure sessions and prompt revocation. Derive tenant/group/site/document grants from authenticated authority, not browser claims. Define nested/conflicting grant behavior before release; unresolved identity or grant state cannot broaden access.

Support access records purpose, scope, approving authority, operator and expiry. Audit grants and sensitive reads. Exclude unrestricted impersonation; diagnostic logs omit personal questions and document text by default.

## 4. Onboarding and identity lifecycle

Track permitted corpus/questions, selected specialty/language, content/access owners, publication rules, a named gap-review audience, supported parsers and first authorized source-linked explanation or explicitly labelled search-only result.

Group transfers, seat revocation and document access changes propagate to search, citations, histories, active jobs, caches and gap evidence. Recheck before answer delivery and source viewing; filter inaccessible/obsolete history before every follow-up prompt. Old answer links cannot bypass recipient authorization. Initial scope has no public answer links.

Keep company country, interface/source language, site/department context, time zone, subscription currency and processing region independent. Seat/invitation counting is a commercial policy to confirm in S13; concurrent membership actions must enforce the selected rule.

An onboarding checkmark or paid subscription does not establish answer quality or grant wider source access.

## 5. Source publication and parsing

Each immutable revision records owner, source hash, format/language, original locator, allowed users/groups, applicable site/department, effective dates, review/expiry policy and version identity.

Workflow:
1. Upload privately as draft with processing rights and provenance.
2. Parse a qualified PDF/DOCX/text format with bounded workers and stable page/section locators.
3. Review the exact revision, intended audience, effective dates and applicability.
4. Validate the eligible index generation and access/publication revisions.
5. Publish atomically through the authorized service; enforce effective dates at serving time.

Parsing success is not publication approval. A reviewed future policy is not current. Scans require separately qualified OCR; spreadsheets, email/chat archives, private personnel records, crawling and connectors stay outside initial scope.

Preserve headings, definitions, exceptions, obligations, conditions, numbers and negation, including cross-section dependencies. A citation must resolve to the original revision; resolving a locator does not establish that the explanation is supported.

## 6. Applicability, conflicts and withdrawal

Policy selection uses explicit audience/site/department/effective-date metadata rather than upload time. Unknown context requests necessary non-sensitive clarification. Conflicts require a documented precedence rule or responsible owner review; the model cannot invent priority or employee eligibility.

Provide a scoped impact preview for audience changes, withdrawal and supersession, without leaking private conversations. Record expected version, affected scope, actor and reason.

Withdrawal and narrowed grants immediately block affected source use during retrieval and answer delivery even while index cleanup is pending. Recheck saved answers, citations, follow-ups, caches and gap evidence. Do not reuse previously authorized hidden passages after access changes.

Older revisions may remain applicable to another site or an explicit historical question. Historical mode must identify the requested period and not imply that old policy applies now. Historical access still obeys current grants and retention.

Restore/index rollback cannot resurrect withdrawn or expired sources, deleted content or revoked access. Re-publication follows the reviewed lifecycle; an operator retry is not a publication override.

## 7. Private knowledge-gap reporting

Raw employee questions and conversations are private by default with defined retention. A gap submission identifies the receiving review audience, or follows an explicitly disclosed and authorized capture policy. Content administration alone does not authorize question capture or unrestricted history.

Gap records contain permitted question/evidence, category, assigned reviewer, status, follow-up and outcome. Recheck grants on evidence links and reassignment; moving a case cannot silently widen its audience. Redact or withhold evidence that is no longer accessible.

Aggregate trends need a documented minimum-group threshold, small-group suppression and restricted drill-down. Filtering by site/topic/time or comparing overlapping reports must not defeat suppression. Define thresholds and review the disclosure risk before enabling analytics; do not invent a numeric privacy guarantee.

Use gaps to improve sources, not score individual employee performance. Reviewer responses become reusable knowledge only after authorized source publication. Feedback or service processing permission does not imply training consent. No unsolicited messaging or external ticket integration is added.

## 8. Jobs and recovery

Show safe job metadata: workspace, type, input/source/access revisions, corpus generation, attempts, remote Astra ID, queue age, typed outcome, budget and usage settlement. Content requires separate authorization.

Astra owns accepted inference jobs and budgets; product workers may own ingestion/indexing. Persist remote IDs and reconcile uncertain acceptance before replay. A timeout is not proof of remote failure.

Retry only eligible work after current grants, source state, applicability, input version, entitlement, budget and active-attempt checks. Idempotency/concurrency prevent duplicate effects and usage. Retries cannot restore withdrawn content or expose a now-private question.

Cancellation remains requested until acknowledged or reconciled. Distinguish runtime unavailable from insufficient evidence, conflicting sources and needs clarification, using inaccessible responses that do not reveal hidden documents.

## 9. Plans, usage and supported scope

Preserve the commercial hypothesis: company subscription based on seats or document volume. Confirm active/invited-seat counting, document/page/storage/query limits, failed/retried work treatment and allowance reset rules before sale.

Server-verified provider state governs paid access. Verify webhook authenticity, deduplicate events, reconcile out-of-order/missed updates and enforce allowances at admission and execution. Display reserved, consumed, released and adjusted units with an append-only correction ledger.

Temporary entitlement exceptions need authority, reason and expiry without falsifying payment history. Keep service suspension, subscription cancellation, service-fee refunds and data deletion distinct. Initially use the eligible provider's authorized dashboard for complex transactions and reconcile outcomes.

Version offers and retain agreed terms unless explicitly migrated. Report revenue by currency, distinguish one-time fees and label estimated costs. Credentials remain server-side.

Activate only qualified specialty/language/input combinations under S14 and applicable release gates. Search-only scope stays labelled; failed audience/source qualification cannot disappear into an aggregate score. Optional connector/knowledge expansion remains S21 and adds no connector credentials in this plan.

## 10. Audit, retention and operations

Audit actor, role/scope, target, operation ID, time, outcome, reason and safe before/after values for grant changes, publication/withdrawal, sensitive reads, gap assignment, recovery and entitlement adjustments. Ordinary admins cannot edit history; audit views themselves require authorization.

Verified data requests identify requester, scope, owner and completion evidence. Cover originals, parsed text, chunks, indexes, prompts/cached answers, histories, feedback and source-bearing gap records, plus documented backup expiry and justified audit/billing retention. Removing a UI row is not completed deletion.

Restore/rebuild must apply current tombstones, grants and publication/effective-date rules before serving results. Reconcile jobs and allowances after restart. Preserve only justified restricted historical metadata.

Monitor API/Astra/workers, oldest queue age, leases, index validation, storage, error rates, billing-sync lag, backups and last restore drill. Display observation times and distinguish stale/unknown from healthy. Incidents have named owners and recovery evidence.

Sensitive actions show target/effect confirmation and enforce backend validation, request-forgery protection where applicable, rate limits, idempotency and stale-version checks.

## 11. Quality and readiness evidence

Show actual checkpoint/prompt/parser/corpus/index/access-policy/host versions, thresholds, sample sizes, denominators, reviewer and pending/failed/accepted state. Track answer support, citations, effective-policy selection, mandatory exception retention, abstention, retrieval, search time and privacy-conscious adoption.

S16-S18 supply actual evaluation/pilot/release results. UI completion, citation resolution or upstream tests cannot establish product answer quality. Unauthorized disclosure or critical unsupported policy assertions remain blockers under the existing quality plan.

Optional S19/S20 improvement needs separate permission, evaluated benefit and reversible release. No automatic publication, training, external model fallback or policy decision is enabled.

## 12. Proposed records and APIs

Reuse [existing contracts](04-data-and-api.md) for source access/publication/withdrawal, questions, answers and gaps. Add scoped support grants, onboarding records, privacy-reviewed analytics configuration, entitlement adjustments, incidents and data requests as needed.

| Proposed route | Contract |
|---|---|
| GET /api/admin/workspaces | Platform-safe customer metadata |
| GET /api/workspaces/{id}/admin/overview | Authorized aggregates only |
| PATCH /api/workspaces/{id}/memberships/{memberId} | Expected-version membership/group grant update |
| GET /api/documents/{id}/revisions/{revision}/impact | Scoped lifecycle impact without private-history leakage |
| POST /api/admin/support-access | Approved scoped access with expiry |
| PATCH /api/gaps/{id}/assignment | Authorized receiving audience and version check |
| GET /api/workspaces/{id}/gap-trends | Suppressed aggregates under reviewed access/privacy rules |
| POST /api/jobs/{id}/reconcile | Resolve outcome through existing owner |
| POST /api/jobs/{id}/retry | Eligible idempotent recovery |
| GET /api/workspaces/{id}/usage | Authorized service ledger |
| POST /api/admin/workspaces/{id}/entitlement-adjustments | Reasoned expiring adjustment |
| GET /api/admin/audit | Permission-filtered redacted events |
| POST /api/workspaces/{id}/data-requests | Verified scoped export/deletion |
| GET /api/admin/health | Restricted timestamped service observations |

These are proposed endpoints, not implemented capabilities. Derive grants from authenticated membership, return typed validation/access/conflict/reconciliation failures, and avoid restricted metadata in errors. Reuse the existing authorities instead of creating duplicate publication, conversation, job or billing stores.

## 13. Delivery and acceptance

| Sprint | Administration outcome | Existing dependencies |
|---|---|---|
| [S22](../PI/PI-08-admin-panel/S22-admin-identity-access/sprint-plan.md) | Identity/groups, workspace onboarding and scoped support | S03; S13 commercial onboarding |
| [S23](../PI/PI-08-admin-panel/S23-admin-publication-private-gaps/sprint-plan.md) | Source lifecycle/applicability and private gap governance | S04-S12; S14 qualification |
| [S24](../PI/PI-08-admin-panel/S24-admin-commercial-operations/sprint-plan.md) | Jobs, billing, scope controls, audit, data lifecycle and readiness | S06/S13-S15; consumes S16-S18 results |

Earlier sprints own domain services; PI-08 owns admin surfaces and integrated verification. Optional PI-07 is not required. Required controls precede the S17 paid pilot and feed S18 release; evidence views can show pending S16-S18 results during development.

- [ ] Tenant/group/document/conversation grants protect lists, snippets, counts, citations, history, gaps and audit.
- [ ] Revoked access and expired support grants block old links, in-flight output and follow-up prompt reuse.
- [ ] Publication respects audience, effective dates and index readiness; future policy is not served as current.
- [ ] Withdrawal/restriction propagates immediately while historical use remains explicit and authorized.
- [ ] Private questions require an authorized review scope; aggregates resist small-group/filter disclosure.
- [ ] Owner responses and feedback do not automatically publish policy or authorize training.
- [ ] Job uncertainty reconciles before retry without duplicate usage or restored hidden content.
- [ ] Verified billing and expiring adjustments preserve payment truth.
- [ ] Data deletion/restore applies to source-bearing histories/gaps and current tombstones/grants.
- [ ] Readiness and supported scope reflect actual evidence, with critical access/policy failures unresolved until fixed.
- [ ] A permitted upload-review-publish-search-explain-submit-gap-withdraw journey passes with named reviewers.

## 14. Open decisions

Confirm identity/group authority, nested/conflicting grant rules, delegated ownership, support-access approver, policy precedence/effective dates, historical-use rules, private-gap capture/disclosure policy, aggregate suppression configuration, commercial counting/provider/grace terms, retention and first specialty/language/input scope.

Record outcomes in [decisions](08-decisions-and-references.md). These documents supply no application code, connector access, benchmark or deployment.
