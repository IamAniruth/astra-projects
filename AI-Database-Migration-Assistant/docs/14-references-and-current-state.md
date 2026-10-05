# DM references and current-state assessment

Reviewed 5 October 2026. This package used relevant sections of large local documents; it is not a complete code audit or fresh runtime qualification.

## Local primary references

- [Astra full-stack setup](../../../astra-llm/codebase/command-documentation/6-FULL_STACK_NEW_MACHINE_SETUP.md): section 41 describes a repository-task evaluator, including migration tasks. It validates supplied candidate artifacts; its presence does not demonstrate model-generated migration success.
- [Astra PI status](../../../astra-llm/codebase/command-documentation/7-PI_STATUS.md): Sprint 187 describes a tested PostgreSQL adapter and migration for the permission-aware index, with explicit product integration and recovery limits. The October 4 model-size section identifies the served 53,870,592-parameter checkpoint and distinguishes capacity probes from trained models. October 5 training/evaluation speed work does not establish new migration reasoning ability.
- [Reference delivery plan](../../AI-Product-Website-Sales-and-Subscription/README.md), [architecture](../../AI-Product-Website-Sales-and-Subscription/docs/02-architecture-and-integration.md), and [sample sprint](../../AI-Product-Website-Sales-and-Subscription/PI/PI-01-foundation/S02-architecture-contracts/sprint-plan.md): used for documentation structure, ownership boundaries, evidence and sprint format.

## Reuse assessment

| Existing capability described in Astra docs | Candidate use | Verification still needed |
|---|---|---|
| Repository/code task evaluator | Run migration benchmark fixtures | Real engine integration, isolation and independent oracles |
| Durable jobs/gateway | Migration operations and UI progress | Per-target receipts, fencing, long-run recovery and authorization |
| Permission-aware retrieval/index | Retrieve schema and code evidence | Customer tenancy, allowed source paths, stale evidence and prompt injection |
| PostgreSQL index migration | Reference for shadow loading and verification | General application mapping, new connectors and post-write recovery |
| Model/checkpoint governance | Version and promote migration-capable candidates | Migration-specific unseen task evidence |

Reuse implementations only after inspecting their actual interfaces and tests in S02. Do not copy platform support claims into the product's compatibility matrix.

## External primary references

- [Next.js backend-for-frontend guidance](https://nextjs.org/docs/app/guides/backend-for-frontend): application API responsibilities and long-running handler limitations; accepted stack separates durable Python work from requests.
- [Training/data/model guide](16-local-llm-training-datasets-and-configuration.md): links to primary Spider/BIRD/Spider 2.0 dataset sources, the compute-optimal training study, Qwen coder report and PEFT quantization documentation. These inform proposed experiments and alternatives; no external model/dataset is adopted by citation.

- [MySQL 8.4 mysqldump](https://dev.mysql.com/doc/refman/8.4/en/mysqldump.html): snapshot/privilege/concurrent-DDL constraints relevant to first-pair qualification.
- [PostgreSQL logical replication](https://www.postgresql.org/docs/current/logical-replication.html): native replication concepts and linked restrictions; not an arbitrary-schema conversion service.
- [Debezium MySQL connector](https://debezium.io/documentation/reference/stable/connectors/mysql.html): consistent snapshot and log coordination for a possible later CDC track.
- [PostgreSQL backup and restore](https://www.postgresql.org/docs/current/backup.html): native recovery reference for target-specific runbook development.

Versioned official manuals must be pinned when implementation selects engines. The 'current' and 'stable' URLs may change. External tools are reference options, not installed dependencies or evidence of end-to-end DM correctness.
