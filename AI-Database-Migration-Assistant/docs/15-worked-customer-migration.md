# DM worked example: old customer/orders app to new accounts app

Synthetic design example only. It makes the intended automation concrete without claiming a real migration has run.

## Schemas

Old: customers(tenant_id, id, full_name, email); orders(tenant_id, id, customer_id, status_code, total_paise, created_at). Customer and order keys are composite (tenant_id, id). The old app's reviewed code establishes status 1=draft, 2=paid, 3=cancelled; created_at is a naive Asia/Kolkata wall-clock time; total_paise is INR minor units.

New: accounts(id UUID, tenant_id, display_name, email, legacy_customer_id); purchases(id UUID, tenant_id, account_id, status, amount NUMERIC(18,2), currency, created_at TIMESTAMPTZ, legacy_order_id). The target app expects these semantics; UUIDs are allocated and stored in the ID map.

## Mapping

| Old field | New field | Rule |
|---|---|---|
| customers.full_name | accounts.display_name | Copy exact approved text policy |
| customers.email | accounts.email | Preserve value; collisions assessed under target uniqueness rules |
| customers.(tenant_id,id) | accounts.id | Persistent tenant-aware ID allocation |
| orders.customer_id + tenant_id | purchases.account_id | Lookup matching customer ID map within same tenant |
| orders.status_code | purchases.status | Explicit 1->draft, 2->paid, 3->cancelled |
| orders.total_paise | purchases.amount | Exact division by 100 with range/scale validation |
| implicit source currency | purchases.currency | INR only because the reviewed business rule establishes it |
| orders.created_at | purchases.created_at | Interpret source wall-clock in named zone then store the instant |

## Synthetic fixture and expected outcome

Tenant A customer 7 'Anita'; tenant B customer 7 'Bala'. They must receive different account IDs. A's order 100 references customer 7, status 2, total 125050 and timestamp 2026-10-01 10:00:00. Expected: account belonging to A, status paid, INR 1250.50, instant 2026-10-01T04:30:00Z.

A second A order referencing nonexistent customer 99 must not be attached to B's account or silently dropped. It is quarantined and blocks cutover under the pilot's no-missing-orders rule. Status 9 similarly requires business clarification. Duplicate emails cannot justify merging the two tenants.

## Automated flow

Discovery extracts schemas and finds the relevant old status/time/money rules and target models. Astra proposes mappings with their evidence. The compiler checks object references, supported operations and target coverage. The runner loads customers before orders and journals the ID map. Independent SQL checks money totals and tenant relationships; the new application displays order 100 and can create a new order without key collision.

Tests deliberately introduce an incorrect divide-by-1000 rule, cross-tenant ID lookup and unknown status fallback. Independent expected results must catch all three. The model is not allowed to change those expected results to pass.

## Repeat-customer behavior

Once qualified, the recipe may accept another dataset from the same verified application/schema/policy versions. It automatically checks engine compatibility, scope, keys, observed statuses, tenant boundaries and authorization. If all pass, it can migrate without another field-by-field review. A changed money unit or new status invalidates compatibility even when the table schema is unchanged.
