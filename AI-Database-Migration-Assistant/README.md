# Astra AI Database Migration Assistant: delivery plan

Prepared: 5 October 2026  
Project ID: DM | Status: Planned; documentation only

## Purpose

Move a customer's existing application data into a newly created application's database, using a local Astra model to assist understanding and a deterministic migration engine to execute verified transformations. Support repeated customer onboarding through reusable, versioned migration recipes.

Automatic migration is achievable within a qualified scope. This plan does not claim arbitrary-database compatibility or that the current Astra model can already infer reliable mappings. Unknown business meaning must remain unresolved rather than become invented data.

## Start here

- [Product specification](AI-Database-Migration-Assistant-Specification.md)
- [Status and next action](_STATUS.md)
- [Six PIs and eighteen sprints](PI/README.md)
- [Documents 16-19: mandatory PI tasks and acceptance](PI/documents-16-19-delivery.md)
- [Feature and sprint coverage](docs/01-module-feature-sprint-matrix.md)
- [Architecture and integration](docs/02-architecture-and-integration.md)
- [Quality and release gates](docs/03-quality-and-release-gates.md)
- [Decisions and dependencies](docs/04-decisions-and-dependencies.md)
- [Connector support and scope](docs/05-supported-databases-and-connectors.md)
- [Mapping and transformation design](docs/06-mapping-and-transformation-contract.md)
- [Execution, cutover and recovery](docs/07-execution-cutover-and-recovery.md)
- [Astra capability development](docs/08-astra-model-capability-and-training.md)
- [Independent evaluation](docs/09-evaluation-and-benchmark-plan.md)
- [Customer and operator workflows](docs/10-user-and-admin-workflows.md)
- [Security and data lifecycle](docs/11-security-and-data-lifecycle.md)
- [Deployment and capacity](docs/12-deployment-capacity-and-cost.md)
- [Pilot and commercial integration](docs/13-pilot-and-commercial-integration.md)
- [Sources and reuse assessment](docs/14-references-and-current-state.md)
- [Worked migration example](docs/15-worked-customer-migration.md)
- [Local LLM datasets, percentages, model sizes and configuration](docs/16-local-llm-training-datasets-and-configuration.md)
- [Application readiness, attachments, identity and scope boundaries](docs/17-application-readiness-and-data-boundaries.md)
- [Operational lifecycle, upgrades, full-system recovery and UI acceptance](docs/18-operational-lifecycle-and-product-acceptance.md)
- [Gap review and acceptance register](docs/19-gap-review-and-acceptance-register.md)
- [Evidence and operational templates](templates/README.md)

## Reference and boundaries

Organization follows [AI Product Website, Sales, Subscription and Admin](../AI-Product-Website-Sales-and-Subscription/README.md): dedicated specification, status, cross-cutting documents, PI READMEs and sprint plans. DM identifiers are independent of WS and Astra's platform sprint numbers.

Technical baseline: [Astra setup](../../astra-llm/codebase/command-documentation/6-FULL_STACK_NEW_MACHINE_SETUP.md) and [Astra PI status](../../astra-llm/codebase/command-documentation/7-PI_STATUS.md). Their existing tools are candidates for reuse, not proof of this product's readiness.

The deliverable here is a plan. No application, trained model, database connection, migration, installation or deployment has been performed. Initial database versions, real customer schemas and runtime choices require qualification during implementation.

## Recommended first slice

Accepted stack: React/TypeScript through Next.js for the UI, Next.js for application APIs, Python services/workers for durable database operations, and local Astra for AI assistance. The UI covers intake through mapping, rehearsal, execution, cutover, recovery and reporting; see [workflow coverage](docs/10-user-and-admin-workflows.md). Implementation and supported migration profiles still require qualification.

Proposed baseline: a single customer's relational data, MySQL 8.4/InnoDB source into PostgreSQL 16 target, an empty isolated target, an agreed maintenance window and an explicit reviewed mapping. These are planning choices, not the user's confirmed database engines. Adapt S01 to the first actual customer before implementation. Include PostgreSQL-to-PostgreSQL only after its own connector evidence passes.

First prove deterministic migration and recovery with human-authored mappings. Then benchmark Astra-generated proposals against the same fixtures. Subsequent customers using an unchanged qualified recipe can run without repeated mapping review when the pre-authorized scope and all preconditions still hold.

## Delivery sizing

Six PIs of three sprints each. At a nominal two weeks per sprint this is 36 sequential weeks, a scope-sizing convention only. The first deterministic demonstration ends at S09; the model's qualification may take longer or fail. No launch date, staffing, hardware purchase or guaranteed model improvement is assumed.
