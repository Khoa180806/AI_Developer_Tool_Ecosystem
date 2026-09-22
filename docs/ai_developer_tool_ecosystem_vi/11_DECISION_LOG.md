# 11 --- Decision Log

## D-001 --- Tool-first

**Decision:** Xây tool độc lập trước, platform sau.

**Reason:** tránh over-engineering.

**Trigger:** xem `02_ECOSYSTEM_ARCHITECTURE_VI.md`.

------------------------------------------------------------------------

## D-002 --- Platform thresholds

**Decision:** Shared Platform Core có trigger định lượng.

**Current thresholds:** - Auth: tool thứ 2 cần multi-user/remote. -
Registry: ≥3 Stable tools + discovery/composition need. - Shared
telemetry: ≥2 production/beta tools. - Cache: ≥2 tools có cùng cache
requirement. - Event bus: ≥3 async consumers. - Central platform: ≥3
Stable tools + ≥2 shared capabilities.

------------------------------------------------------------------------

## D-003 --- Canonical naming

**Decision:** catalog là nguồn tên chuẩn.

Các tên cũ được chuẩn hóa: - Prompt Cache → Semantic Cache nếu
semantic. - Codebase Knowledge Graph → capability riêng, nằm trên
Codebase Graph. - Impact Analysis → Code Impact Engine. - Agent Context
Engine → Context Engine capability; không dùng như alias tùy tiện. - MCP
Mesh → canonical tool trong catalog.

------------------------------------------------------------------------

## D-004 --- Code intelligence differentiation

**Decision:** Không clone
GitNexus/Sourcegraph/CodeQL/tree-sitter/ast-grep.

**MVP focus:** - compact Agent queries; - context composition; -
token/time benchmarks; - provider adapters; - local privacy.

------------------------------------------------------------------------

## D-005 --- Parser

**Decision:** Java-only MVP; Tree-sitter Java làm syntax parser.

**Reason:** giảm scope và tận dụng incremental parsing.

**Caveat:** semantic resolution là module riêng; Tree-sitter AST không
được coi là semantic truth.

------------------------------------------------------------------------

## D-006 --- MVP scale

**Decision:** 10--500 KLOC, tối đa 20,000 source files, local, 1
repository.

Stretch: 500 KLOC--1 MLOC.

Không tự động escalate storage chỉ vì vượt ngưỡng; phải benchmark.

------------------------------------------------------------------------

## D-007 --- Storage

**Decision:** SQLite/local embedded cho MVP.

Escalate khi benchmark hoặc shared-access requirement chứng minh cần
PostgreSQL/service/graph DB.

------------------------------------------------------------------------

## D-008 --- Compact-response-first

**Decision:** áp dụng cho toàn ecosystem, đặc biệt MCP.

Mặc định: summary → IDs/counts → references → details theo yêu cầu.

------------------------------------------------------------------------

## D-009 --- Privacy

**Decision:** Local mode mặc định không gửi source code ra ngoài máy.

Cloud/remote mode chỉ được triển khai sau khi có spec về: -
encryption; - retention; - deletion; - tenant isolation; - access
control; - audit.

------------------------------------------------------------------------

## D-010 --- ICP

**Decision:** ICP đầu tiên là developer dùng AI coding agent trên
Java/TypeScript repositories.

Các persona khác là phase sau.

------------------------------------------------------------------------

## D-011 --- Benchmark

**Decision:** Mọi tool Stable phải có benchmark.

Initial discovery threshold: - ≥20% token reduction; - hoặc ≥20% latency
reduction; - hoặc ≥10 percentage-point success improvement, với các điều
kiện đã nêu trong `10_BENCHMARK_PLAN_VI.md`.

------------------------------------------------------------------------

## D-012 --- Codebase Graph kill criterion

Nếu sau 2 vòng scope-limited benchmark không chứng minh được gap so với
existing providers: \> Không xây graph engine riêng.

Chuyển sang adapter/context optimization hoặc archive.


## D-020 — File vận hành phải merge, không patch

Các file vận hành phải phản ánh trực tiếp trạng thái mới nhất. Lịch sử và rationale
nằm trong Decision Log; không dùng các section patch rời làm nguồn sự thật.

## D-021 — Competitor gate theo từng tool

Mỗi tool 1★ cần ít nhất 3 competitor/project liên quan trước khi code.

## D-022 — Naming/version phải nhất quán

INDEX, README và changelog phải dùng cùng version và canonical filename.
