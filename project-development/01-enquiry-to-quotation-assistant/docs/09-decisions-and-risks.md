# Decisions and risks

## Decisions already reflected in the plan

- Project 1 only: enquiry-to-quotation assistant.
- React frontend and Next.js backend as requested.
- PostgreSQL for product data and an adapter to the existing private Astra gateway; optional product-owned Node worker/queue only where justified. Astra Python inference and job authority are reused.
- One shared product with explicit country/language/currency settings.
- Human confirmation of catalogue matches and quote approval.
- Deterministic authoritative pricing and calculations.
- Paid pilot, then setup plus subscription as the initial commercial hypothesis.

## Open decisions

| Decision | Owner to assign | Needed by | Default planning assumption |
|---|---|---|---|
| First customer industry and buyer access | Product owner | S01 | Electrical distributor if reachable |
| Team size, hours, budget | Business owner | S01 | Re-estimate; 18 sprints is a scope baseline |
| Existing Astra model/profile/hardware/license | Technical owner | S01/S08 | Inspect source manifest and qualify actual checkpoint; external providers disabled |
| Initial country, language, currency | Product owner | S03/S15 | Explicitly select; no country inferred |
| Auth library/database adapter versions | Backend owner | S02 | Better Auth compatibility spike |
| Parser and OCR | Backend/AI owner | S06/S08 | Narrow supported input formats |
| Tax/discount/rounding policy | Business/domain reviewer | S05/S10 | Versioned reviewed rules |
| Payment provider and eligibility | Business/backend owner | S14 | One sandbox adapter, then eligible live account |
| Prices, allowance units, trial/grace policy | Business owner | S14 | Per-workspace plan with job allowance |
| Hosting region and budget | Operations owner | S16 | One supported region with private model path |
| Privacy/retention/commercial terms | Business reviewer | S15/S18 | Reflect actual deployment and selling arrangement |
| Support coverage and pilot agreement | Product/operations owner | S17 | Explicit availability, no implied 24/7 service |

Owners are roles, not assigned people or extra agents.

## Main risks and responses

| Risk | Response |
|---|---|
| Weak customer demand | Interview and seek paid pilot evidence before broad scope expansion |
| Ambiguous catalogue or bad scans | Import review, data cleaning, source display, and manual correction |
| Unsupported model language/capacity | Per-language benchmark, low initial concurrency, manual fallback |
| Hallucinated match or price | Candidate allowlist, staff selection, authoritative price lookup |
| Incorrect calculations | Decimal arithmetic, domain fixtures, immutable approved snapshots |
| Cross-company leakage | Scoped repositories, constraints, two-tenant integration and worker tests |
| Queue duplicates or lost work | Durable jobs, outbox, idempotency and reconciliation |
| Subscription mismatch | Verified events, reconciliation, atomic usage reservation |
| Multi-country scope expansion | Supported-market matrix and one additional market at a time |
| Personal machine outage | Pilot availability agreement and dedicated production operation plan |

Review risk status each sprint. A blocked dependency can move work within a PI, but money correctness, isolation, and readiness gates cannot be waived silently.

