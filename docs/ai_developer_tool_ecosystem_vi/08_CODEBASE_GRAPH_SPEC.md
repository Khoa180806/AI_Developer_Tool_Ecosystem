# 08 --- Codebase Graph / Code Intelligence Spec v2.3

## 1. Strategic position

Đây là flagship direction, nhưng **không mặc định xây lại toàn bộ graph
engine từ số 0**.

MVP phải kiểm chứng: \> specialized code intelligence có giúp Agent giảm
token/time và tăng task success đủ lớn không?

## 2. Competitive baseline

Các công nghệ/sản phẩm đã tồn tại: - Tree-sitter: incremental parsing,
multi-language. citeturn0search0 - ast-grep: AST structural
search/rewrite. citeturn0search10turn0search8 - CodeQL: code
database + query analysis. citeturn0search2turn0search3 - GitNexus:
codebase knowledge graph + Tree-sitter + graph DB + hybrid search +
MCP/CLI. citeturn0search1turn0search6

Do đó: **AST → Graph → MCP không phải differentiation.**

## 3. MVP scope

### Language

**Java only.**

Lý do: - phù hợp skill/roadmap hiện tại; - giảm scope; - cho phép test
sâu framework semantics sau này.

### Parser

**Tree-sitter Java** là parser syntax chính.

Tree-sitter phù hợp cho incremental parsing và có Java binding chính
thức. citeturn0search0

### Semantic resolution

Không coi AST là semantic truth.

MVP tách: - syntax parsing; - symbol extraction; - import resolution; -
call/reference resolution.

Semantic resolver phải là module độc lập để sau này thay implementation
mà không đổi graph contract.

## 4. Không làm trong MVP

-   multi-language;
-   full IDE;
-   full architecture governance;
-   distributed graph service;
-   cloud indexing;
-   graph database bắt buộc;
-   automatic refactor;
-   full semantic understanding của mọi Java framework.

## 5. Quy mô MVP

Target repository benchmark:

-   10--500 KLOC;
-   tối đa 20,000 source files;
-   local developer machine;
-   1 repository tại một thời điểm.

Stretch: - 500 KLOC--1 MLOC.

Nếu vượt 1 MLOC: - benchmark memory/index/query; - không tự động chuyển
graph database.

## 6. Storage decision

### MVP

SQLite/local embedded index.

### Escalation triggers

Chuyển sang PostgreSQL hoặc service storage khi: - shared remote access
cần persistence; - ≥2 consumers cần cùng index; - concurrent
readers/writers trở thành bottleneck; - local DB vượt benchmark
threshold.

Graph DB chỉ dùng khi benchmark chứng minh traversal/query workload cần
nó.

## 7. Graph schema

### Node

``` json
{
  "id": "sym:java:com.example.payment.PaymentService",
  "type": "CLASS",
  "name": "PaymentService",
  "qualified_name": "com.example.payment.PaymentService",
  "file_path": "src/main/java/com/example/payment/PaymentService.java",
  "language": "java",
  "module": "payment-service"
}
```

### Edge

``` json
{
  "id": "edge:sha256:...",
  "type": "CALLS",
  "source": "sym:java:com.example.payment.PaymentService.process",
  "target": "sym:java:com.example.payment.PaymentRepository.save",
  "confidence": 0.98,
  "source_location": {
    "file_path": "src/main/java/com/example/payment/PaymentService.java",
    "start_line": 42,
    "end_line": 42
  }
}
```

`confidence` bắt buộc với relationship có thể mơ hồ.

## 8. ImpactReport schema

``` json
{
  "schema_version": "1.0",
  "target": {
    "id": "sym:java:com.example.payment.PaymentService",
    "type": "CLASS",
    "name": "PaymentService"
  },
  "summary": {
    "direct_dependents": 8,
    "indirect_dependents": 19,
    "callers": 11,
    "tests": 6,
    "affected_modules": 2,
    "confidence": 0.94
  },
  "direct_dependents": [
    {
      "id": "sym:java:com.example.order.OrderService",
      "type": "CLASS",
      "name": "OrderService",
      "file_path": "src/main/java/com/example/order/OrderService.java",
      "relation": "DEPENDS_ON",
      "confidence": 0.99
    }
  ],
  "tests": [
    {
      "id": "sym:java:com.example.payment.PaymentServiceTest",
      "type": "TEST",
      "name": "PaymentServiceTest",
      "file_path": "src/test/java/com/example/payment/PaymentServiceTest.java"
    }
  ],
  "affected_modules": [
    {
      "id": "module:payment-service",
      "name": "payment-service"
    }
  ],
  "truncated": false,
  "next_cursor": null
}
```

## 9. Query contract

Initial:

``` text
find_symbol(name)
get_dependencies(symbol)
get_dependents(symbol)
get_callers(symbol)
get_callees(symbol)
get_implementations(interface)
get_tests(symbol)
get_impact(symbol)
```

## 10. Compact-response-first

Đây là requirement bắt buộc, không phải suggestion.

Mọi query Agent-facing: 1. trả summary; 2. trả IDs; 3. trả counts; 4.
trả references; 5. details theo request; 6. pagination khi cần.

Không có `analyze_entire_repository()` như một tool MCP mặc định.

## 11. Incremental indexing

``` text
Git diff
 ↓
Changed files
 ↓
Changed symbols
 ↓
Affected graph region
 ↓
Incremental update
```

MVP không cam kết rename/move/refactor detection hoàn hảo.

## 12. Differentiation target

Không cạnh tranh bằng: - parser; - graph database; - generic code
search.

Tập trung vào: - agent-first query design; - compact responses; -
context budget; - impact → context composition; - benchmark
token/time; - provider adapters; - local privacy.

## 13. Evolution

1.  Java graph foundation
2.  Impact engine
3.  Context Pack integration
4.  MCP
5.  Benchmark/eval engine
6.  Provider adapters
7.  Multi-language
8.  Code Intelligence Platform


### Quan hệ giữa Artifact và Transport Envelope

`ImpactReport` là schema của artifact dữ liệu, không phải transport envelope độc lập.
API/MCP phải bọc artifact theo envelope chung:

```json
{
  "data": "<ImpactReport>",
  "metadata": {
    "schema_version": "1.0",
    "truncated": false,
    "next_cursor": null
  }
}
```

`truncated` và `next_cursor` chỉ thuộc metadata của transport và không được lặp lại
trong `ImpactReport`.
