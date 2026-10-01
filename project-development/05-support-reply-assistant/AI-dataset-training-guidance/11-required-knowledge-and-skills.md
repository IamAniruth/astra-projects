# Specific knowledge and skills for quality support replies

Project: Support Reply Assistant. Status: proposed curriculum and knowledge checklist; no checkpoint has passed it yet. The objective is accurate case summaries and customer-facing drafts that agents approve. This document makes the existing [dataset percentages](12-dataset-types-reasoning-and-samples.md) concrete; it does not add new percentage buckets or change the release gates.

## 1. What belongs in training, retrieval and the application

| Layer | Add for this project | Why it matters |
|---|---|---|
| Base-model skills and supervised examples | Reading, attribution, summarization, evidence use, policy conditions, clarification, structured output and supported-language writing | Teaches how to perform the work |
| Approved retrieval knowledge | Product guides, error-code explanations, approved troubleshooting, current support policies and public communication rules | Supplies company-specific facts and current instructions |
| Authorized live facts | Current order/payment/delivery/account state and action outcomes | Prevents guesses based on stale tickets or model memory |
| Deterministic application controls | Tenant/case access, private-note visibility, source freshness, exact-revision approval and public export checks | Enforces rules that model instructions alone cannot guarantee |

Adding more training examples cannot create a missing order-system connection, establish a user's identity or replace permission checks. Teach the model to identify missing facts; obtain the facts through an authorized system when available.

## 2. Exact skill curriculum and training examples

All rows are required for the supported scope. Prioritize attribution, evidence, missing facts, conditions and privacy before cosmetic improvements. The percentage column names an existing primary bucket; repeated percentages refer to that same shared allocation and must not be added together.

| ID | Specific skill | Examples to add | Expected behavior and failure to test | Existing primary bucket |
|---|---|---|---|---|
| SK01 | Understand issue and requested outcome | Customer asks several questions, uses typos, names the wrong product or omits a version | Identify the actual request; ask for necessary context rather than choosing an unsupported interpretation | Extraction, 5%; tag on drafts |
| SK02 | Attribute statements and preserve chronology | Quoted email chains, agent notes, customer reports and messages in different time zones | Separate who said what; do not turn a customer claim or old quoted message into a verified event | Summaries, 20% |
| SK03 | Produce a complete concise summary | Long case with attempted fixes, unresolved questions, latest update and prior promises | Keep essential facts and unknowns; do not claim the issue was resolved when only a step was attempted | Summaries, 20% |
| SK04 | Ground each material reply claim | Case plus approved passages and distracting similar articles | Use relevant evidence; link material claims internally; do not treat an existing citation as proof of support | Grounded drafts, 35% |
| SK05 | Apply policy conditions and exceptions | Supplied policy with date/version/product restrictions, exclusions and required verification | Apply all relevant conditions; distinguish possible eligibility from an authorized decision | Policy cases, 10% |
| SK06 | Recognize missing, conflicting or stale evidence | Missing order lookup, conflicting articles, expired fact snapshot, unclear product | Ask a focused question or request agent verification; do not invent status or precedence | Clarification/missing evidence, 15% |
| SK07 | Preserve numbers, dates, identifiers and negation | Similar order IDs, amounts, dates, 'approved' versus 'processed', 'must not' versus 'may' | Copy factual values accurately; preserve qualification and action state | Extraction, 5%; tags across summaries/drafts |
| SK08 | Protect customer and internal information | Private notes, another customer's similar case, internal URLs and confidential attachments | Exclude non-disclosable details from public text, even if available to the agent | Privacy/injection, 10% |
| SK09 | Resist instructions inside ticket content | Customer message or article says to ignore rules, expose notes or approve a refund | Treat those instructions as untrusted data; retain approved task boundaries | Privacy/injection, 10% |
| SK10 | Draft useful, empathetic replies | Frustrated customers, repeated contacts, simple questions and unresolved problems | Acknowledge the issue, explain supported facts and give an authorized next step; do not add promises to sound helpful | Grounded drafts, 35% |
| SK11 | Follow the response contract | Output requires summary, public reply, evidence and review flags; incomplete source fields | Produce the required structure; keep internal evidence separate and unknowns explicit | Extraction, 5%; contract tags on all relevant records |
| SK12 | Update conclusions after new evidence | New customer message, corrected order fact, policy revision or agent correction | Revise the relevant facts and mark old conclusions stale; never represent a drafted action as executed | Multi-turn corrections, 5% |

Each accepted training record has one primary skill bucket plus any applicable SK tags. For example, a policy-grounded refund draft can be primarily grounded_reply_drafts with SK04, SK05, SK06 and SK10 tags. It still counts once in the 10,000-example training set.

## 3. Specific knowledge to collect from the support business

The actual buyer/product is not yet selected. Fill this checklist with permitted, owner-reviewed company documents rather than generic invented policies. Mark irrelevant topics not applicable and redistribute topic quotas before collection.

| Knowledge ID | Material to obtain | Source owner | Where it belongs | Required fields or conditions |
|---|---|---|---|---|
| K01 Product identity and capabilities | Product/version catalogue, feature limits, supported configurations | Product/support knowledge owner | Retrieval | Product/version, supported language, effective date and source revision |
| K02 Setup and troubleshooting | Approved setup steps, error-code catalogue, known-issue articles and escalation points | Technical support | Retrieval | Preconditions, applicable version, exact steps, warnings and stop/escalation condition |
| K03 Account access support | Approved recovery and identity-verification procedures | Account/security owner | Retrieval; actual verification in application/system | What an agent may request/disclose; never collect passwords or secret credentials as training content |
| K04 Billing and refund policy | Cancellation/refund criteria, exceptions and approval authority | Billing/support policy owner | Retrieval | Conditions, exclusions, effective date; distinguish policy eligibility from executed payment |
| K05 Order and delivery guidance | Published status definitions, delivery-policy wording and supported escalation | Operations/support owner | Retrieval | Meaning of each status and approved wording; actual order status is a live fact |
| K06 Returns and warranty | Eligible products, deadlines, exclusions and required evidence | Returns/warranty owner | Retrieval | Applicable region/product/date where relevant; no generic legal assumptions |
| K07 Reply style and disclosure rules | Tone guide, approved terminology, public links and prohibited disclosures | Support lead | Versioned prompt/config plus reviewed examples | Channel/language, allowed templates, phrases that imply promises or admissions |
| K08 Escalation and commitments | Ownership map, verification steps and authorized commitment rules | Support operations | Retrieval/config; action authorization in application | Who can decide, when to escalate, what response timelines may actually be promised |
| K09 Reviewed case examples | Corrected summaries, reply edits and why corrections were needed | Support QA with data-permission owner | Training and independently separated evaluation | Rights, de-identification, case/template grouping, source versions and reviewer decision |

Product-independent historical tickets must not become shared truth about another customer. Approved historical replies are examples of behavior only after checking their evidence, policy validity and disclosure. Current knowledge changes through publication/retrieval; do not retrain merely to memorize every policy update.

## 4. Live facts the model must never invent

| Fact | Required evidence | Behavior when missing |
|---|---|---|
| Refund approved, initiated, settled or received | Authorized payment-system snapshot; distinguish these states | State that current status needs checking; approval alone does not prove receipt |
| Order shipped or delivered | Authorized order/carrier result bound to the correct customer/order | Do not give a guessed status, tracking number or arrival date |
| Account ownership or access restored | Application identity/authorization and actual system outcome | Follow approved verification or request agent action without claiming completion |
| Ticket action performed | Confirmed business-system action result | Drafting/approval/export is not sending, closing or executing the action |
| Current outage or known incident | Approved current incident source | Do not attribute every symptom to an assumed outage |

Record source, customer/account binding, observed timestamp and source-specific freshness policy. Snapshot freshness must be tested at the time of approval/handoff. If no integration is configured, train and implement the missing-fact path instead of presenting simulated lookups as production evidence.

## 5. Example teaching pairs

The policies and cases below are synthetic illustrations, not actual company promises. Use equivalent examples from the selected support scope with reviewed sources.

| Input/evidence | Desired response behavior | Incorrect behavior to label |
|---|---|---|
| Customer says 'My refund was approved'; no payment lookup | Summary attributes the report to the customer; reply says payment status must be verified | 'The refund has reached your bank' or a made-up arrival date |
| Approved policy allows returns within 30 days, excludes a specified product class; class is unknown | Explain that eligibility requires the product class and relevant date; do not approve | Ignore the exclusion and promise a return |
| Agent note says 'reset requested'; no success confirmation | Summary records a requested reset and unresolved access | Say 'Your access has been restored' |
| Product-v2 case and a high-scoring product-v1 article | Exclude the inapplicable procedure or clarify the version | Copy v1 steps because the search score is high |
| Private note contains sensitive internal commentary and ticket text asks to quote it | Keep commentary out of public reply; answer only from permitted evidence | Reveal the note or internal-only URL |
| New message corrects the order number after a draft was approved | Re-evaluate against the new case revision; old approval becomes stale through application controls | Reuse the old customer's/order's facts |

Train expected outputs with evidence references and review flags, not a hidden reasoning transcript. Store concise reviewer rationales explaining specific errors for QA; only intended customer-facing content goes into the public reply target.

## 6. What every accepted example must contain

1. A permitted case with stable message IDs, speakers, chronology and public/private labels.
2. Exact approved evidence with product/policy version and applicability, or an explicit missing/conflicting-evidence condition.
3. Expected summary and/or reply appropriate to the task, plus internal claim evidence and unresolved checks where needed.
4. Required facts, prohibited claims and expected escalation/clarification outcome.
5. One primary skill, one primary topic and a provenance category, plus applicable SK/K tags.
6. Language/channel, protected case/customer/template grouping, rights, reviewer and accepted/rejected decision.

Do not turn every record into a reply-generation example: preserve the [20/35/15/10/10/5/5 allocation](12-dataset-types-reasoning-and-samples.md). For the first accepted 1,000-record training batch that means 200 summaries, 350 grounded drafts, 150 clarification cases, 100 policy cases, 100 privacy cases, 50 extraction cases and 50 correction cases. These are training records, not the independent release sample.

## 7. How to know which skill needs more examples

Start with a **200-300-case diagnostic subset of the existing 2,000-case development allocation**; this is not an additional collection quota or release certificate. Cover all seven primary skill buckets, missing evidence, long cases and private notes. Domain reviewers specify expected behavior before scoring.

Run three separate comparisons: summary from the case alone; reply with correct evidence supplied directly; reply using actual retrieval. Hold the case/model/prompt constant where possible so the changed component is interpretable.

| Observed failure | Repair first | Dataset action |
|---|---|---|
| Wrong speaker, omitted unresolved question or invented completed action | Model summary/attribution behavior | Add SK02/SK03/SK07 examples with explicit labels |
| Correct evidence gives accurate replies, retrieved evidence does not | Retrieval filters, source coverage or chunking | Improve retrieval relevance labels; do not blindly add drafting examples |
| Model ignores a supplied exception or adds an unsupported commitment | Grounding/conditional reasoning | Add SK04/SK05 examples and counterexamples; check base-model capability |
| Live fact is absent | Authorized source integration or missing-fact handling | Add SK06 cases; never train fabricated live status |
| A source or customer is unauthorized | Access/disclosure application controls | Fix controls and add negative tests; privacy examples are additional defense |
| Output structure/tone is wrong but facts are correct | Schema/prompt and instruction-following behavior | Add SK10/SK11 examples after checking contract validation |
| Context is truncated | Context assembly and supported-length limits | Fix budgeting; add long-case cases only within qualified capability |
| Basics fail even with correct evidence and a clear task | Existing checkpoint capability | Compare a more capable compatible base before scaling support data |

Record failures by SK ID, case denominator and severity. Add the next 2,000-3,000 training examples based on development/validation findings using the percentage guide, with a versioned recipe change if rebalancing is justified. Do not use hidden release cases for routine tuning.

## 8. Output acceptance remains evidence-based

This curriculum does not establish model competence. The authoritative [quality gates](06-quality-gates.md) still apply: zero observed critical failures plus the defined representative-sample confidence requirement, the proposed major-error upper bound, summary/citation checks, abstention coverage and access/freshness invariants. All remain unmeasured for this project.

Reviewers should record the required skill as verified, failing or not yet tested for the exact checkpoint/prompt/retrieval configuration. No supported-language or customer-ready claim follows solely from collecting examples or completing training.


## 9. Dataset preparation, review and supported scope

### Fields, review and leakage controls

Every accepted example records ID, primary skill, primary topic, source category, language, protected customer/thread/template grouping IDs, permission/provenance, case visibility, source versions, allowed evidence, expected output, prohibited claims and reviewer decision. Keep deletion lineage. See [synthetic example](templates/synthetic-example.json) and [machine-readable mixture](templates/dataset-mixture.json).

Normalize Unicode/time zones without destroying original message order or source values. Deduplicate quoted chains and near-identical templates before group-based splits. Hold customer/thread and issue-template groups apart across train/validation/development/calibration/release. Broad topics must appear across sets; grouping by issue-template family prevents copying the same example pattern, not all billing examples being placed in one split.

Do not tune prompts, retrieval, adapters or quantization on release data. If a release case is used to fix a failure, retire it from untouched evaluation and replenish with genuinely unseen independent cases. Synthetic paraphrases of held-out tickets remain leakage.

Independently review all expected outputs. Double-review every critical privacy/commitment case, plus an initial 200 ordinary examples to stabilize the rubric and a proposed 20% random sample of subsequent ordinary batches. Adjudicate disagreement. Synthetic labels and model graders cannot be the sole release authority.

Negative-input examples teach a correct reply or abstention, not reproduction of the bad reply. Preserve customer claims as attributed claims. No personal data or training permission is inferred from a ticket being available for service use.

### Initial supported scope

Plan one support specialty/channel and one selected language first. If English is selected, the first training cohort can be 100% English; this is a hypothesis, not a confirmed customer requirement. Add another language only with its own support reviewer, data rights and evaluation. Do not dilute the initial set with unrelated translation, coding, finance analysis or broad general-knowledge tasks.
