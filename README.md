Staff engineer building ingestion pipelines for observability platforms. I own the data plane from edge collectors to queryable storage.

## Ocie Durgan

I design and operate high-throughput ingestion systems that absorb telemetry from thousands of hosts. I own the full lifecycle: schema evolution, queue backpressure, partition rebalancing, and storage tiering. My operational priority is keeping the pipeline healthy during traffic spikes and migrations; I accept occasional data lag over dropped writes. I trade strict consistency for availability and favor explicit, boring designs over clever ones.

### 🛠 Tech & Infrastructure

**Core** — `TypeScript`, `Node.js`, `PostgreSQL`, `Redis`

**Data** — `Kafka`, `ClickHouse`, `Parquet`, `Flink`

**Infra** — `Kubernetes`, `Terraform`, `Prometheus`, `Grafana`

**Tooling** — `GitHub Actions`, `Docker`, `ESLint`, `Jest`

### ⚙️ Engineering Areas

- **Schema evolution** — rolling out Avro-compatible changes without breaking older producers or consumers.
- **Backpressure handling** — tuning queue limits and consumer lag so slow downstreams don't cascade into OOM kills.
- **Partitioning strategies** — choosing keys that balance load and preserve ordering for time-series writes.
- **Storage tiering** — moving hot data to object storage with retention policies that keep queries fast and costs predictable.

### 🔭 Current Focus

- Reducing rebalance storms in a 200-partition Kafka cluster when consumers join or leave.
- Cutting p99 query latency for range scans on ClickHouse by experimenting with sparse indexes and pre-aggregations.
- Migrating a monolith batch loader to a streaming pipeline without losing exactly-once semantics.
- Standardizing trace context propagation across internal RPCs and HTTP APIs.

### 📌 Engineering Notes

- Testing: unit tests for pure logic, integration tests for real queues and databases; avoid mocks that mirror the implementation.
- Boundaries/migrations: keep schema migrations additive and reversible; never couple a data migration to a code deploy.
- Error handling/retries: retry idempotent operations with exponential backoff; fail fast on non-retryable errors and alert immediately.
- Observability/deployments/on-call: every service ships metrics, traces, and structured logs; use canary deployments and roll back on SLO burn.

### 🧭 How I Work

- Design for the failure case first: what happens when a dependency is slow, down, or returns garbage?
- Prefer small, reversible changes over big-bang rewrites; every PR should be deployable independently.
- Write code that reads like prose: clear names, short functions, and comments only when the why isn't obvious.

*The best pipeline is the one that keeps running while you sleep.*