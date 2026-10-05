# DM database support and connector qualification

Every row is proposed or deferred. No connector is implemented or qualified by this document. A database brand name alone is not a support claim: qualify exact server/driver versions, storage engines, encodings, permissions and data types.

| Pair or input | Stage | Scope |
|---|---|---|
| MySQL 8.4/InnoDB -> PostgreSQL 16 | Proposed first pilot | Relational tables, explicit transforms, empty target, write freeze |
| PostgreSQL -> PostgreSQL | Next profile | Exact versions qualified separately; changed schemas still need mappings |
| CSV/JSON exports -> supported target | Later | Explicit schemas, manifests and typed parsing; exports may lack consistent relationships |
| SQL Server -> PostgreSQL | Later connector | Qualify identity, computed columns, collation, datetime and routine behavior |
| SQLite -> PostgreSQL business applications | Later connector | Dynamic typing and concurrency handled explicitly; Astra's index adapter does not cover this generally |
| MongoDB -> relational target | Later specialist profile | Nested documents/arrays, heterogeneous shapes and entity relationships |
| Oracle, other engines, reverse directions | Out of initial scope | Separate licensing, semantics, connector and recovery assessment |

## Required connector contract

probe(): server identity/version/capabilities without leaking credentials. inspect(): catalog with stable object IDs and fingerprint. profile(): scoped statistics with sample/full-scan distinction. snapshot(): immutable extraction identity and consistency rules. read_batch(): stable deterministic cursor. health(): limits, lag and expiry. The target adds prepare_staging(), write_batch(), commit_receipt(), validate_constraints() and cleanup_owned_staging(). Never execute arbitrary repository instructions through the connector.

Initial source credentials are read-only except narrowly required snapshot/lock privileges separately identified by the chosen backup method. Destination writes are restricted to a run-owned staging database/schema. Source deletion is not an interface.

## Object inventory and dispositions

Inventory tables, primary/composite keys, views, triggers, routines, foreign keys, checks, defaults, sequences/identities, generated columns, partitions, collations, indexes, grants and extensions. Each item is mapped, rebuilt by the new application's schema, explicitly excluded or unsupported. Silently omitting a trigger that enforces a business rule is a failed inventory.

Views/routines/triggers are not mechanically portable. Prefer the new application's intended behavior and prove equivalence where required. Bulk loading must not accidentally send emails or trigger payments; side-effecting integrations stay disabled during rehearsals and load.

## Type conversion hazards

| Source characteristic | Required policy |
|---|---|
| Unsigned integers, wide numeric values | Range analysis and target type choice; reject overflow |
| Decimal money | Exact numeric representation; explicit scale/rounding; currency-specific aggregates |
| Zero/invalid dates and naive timestamps | Quarantine or reviewed correction; named source timezone and DST policy |
| ENUM/status codes | Evidence-backed mapping; unknown values block affected rows |
| Case-insensitive collation and Unicode | Detect collisions under target comparison/normalization semantics |
| JSON, binary and large values | Typed validation, size limits and streaming; preserve bytes where specified |
| Generated IDs and composite keys | Persistent tenant-aware key map, deterministic replay and sequence reset |
| NULL, empty string and absent fields | Separate policies; no blanket conversion |

## Snapshot constraints

For the first release, freeze application writers and DDL, then take a verified consistent snapshot. Pin that snapshot for resume; a lost live transaction cannot be reconstructed from its cursor alone. MySQL documents restrictions around concurrent DDL during a single-transaction dump; qualify the full procedure, not just a command flag. [MySQL 8.4 mysqldump](https://dev.mysql.com/doc/refman/8.4/en/mysqldump.html)

For future low-downtime operation, require a consistent snapshot plus an associated change-log position, ordered inserts/updates/deletes, retention monitoring and a final write fence. Debezium documents snapshot/log coordination for MySQL; adoption is a future implementation choice. [Debezium MySQL connector](https://debezium.io/documentation/reference/stable/connectors/mysql.html)

Do not infer cross-engine schema conversion from the availability of native logical replication. PostgreSQL's native logical replication has its own scope and restrictions; consult the pinned version during qualification. [PostgreSQL logical replication](https://www.postgresql.org/docs/current/logical-replication.html)
