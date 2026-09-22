# Codebase Graph Specification

## Strategic position
Codebase Graph is a flagship capability, but the MVP does **not** attempt to clone GitNexus, CodeQL, Sourcegraph, ast-grep, or tree-sitter functionality. The purpose is to prove that specialized, compact code-intelligence queries can improve agent workflows.

## MVP scope
- Language: Java only.
- Syntax parser: **Tree-sitter Java grammar**.
- Semantic resolution: separate module; AST is not treated as semantic truth.
- Repository: one local repository.
- Storage: SQLite/local embedded.
- Target size: 10–500 KLOC, ≤20,000 source files.
- Stretch: 500 KLOC–1 MLOC.

Not in MVP:
- multi-language support
- distributed graph service
- mandatory graph database
- cloud indexing
- full IDE
- automatic refactoring
- complete Java framework semantic understanding

## Data model
### CodeGraph node
```json
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

### CodeGraph edge
```json
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

## Initial node types
`FILE`, `PACKAGE`, `CLASS`, `INTERFACE`, `ENUM`, `METHOD`, `FIELD`, `CONSTRUCTOR`, `PARAMETER`, `TEST`

## Initial edge types
`CONTAINS`, `IMPORTS`, `EXTENDS`, `IMPLEMENTS`, `CALLS`, `REFERENCES`, `OVERRIDES`, `TESTS`

## Query contract
### find_symbol
Input:
```json
{"query":"PaymentService","limit":20}
```

### get_dependencies
Input:
```json
{"symbol_id":"sym:java:com.example.payment.PaymentService","depth":2,"limit":100}
```

### get_dependents
Input:
```json
{"symbol_id":"sym:java:com.example.payment.PaymentService","depth":2,"limit":100}
```

### get_callers / get_callees
Input:
```json
{"symbol_id":"sym:java:com.example.payment.PaymentService.process","limit":100}
```

### get_implementations
Input:
```json
{"symbol_id":"sym:java:com.example.payment.PaymentGateway","limit":100}
```

### get_tests
Input:
```json
{"symbol_id":"sym:java:com.example.payment.PaymentService","limit":100}
```

### get_impact
Input:
```json
{"symbol_id":"sym:java:com.example.payment.PaymentService.process","depth":3,"limit":100}
```

### Artifact vs transport envelope

`ImpactReport` is a data artifact, not a standalone transport envelope. The common API/MCP response MUST wrap it as `{"data": <ImpactReport>, "metadata": {"schema_version": "...", "truncated": false, "next_cursor": null}}`. `truncated` and `next_cursor` belong only to transport metadata and MUST NOT be duplicated inside `ImpactReport`.

ImpactReport schema
```json
{
  "schema_version": "1.0",
  "target": {
    "id": "sym:java:com.example.payment.PaymentService.process",
    "type": "METHOD",
    "file_path": "src/main/java/com/example/payment/PaymentService.java"
  },
  "summary": {
    "direct_dependents": 4,
    "transitive_dependents": 17,
    "affected_modules": 3,
    "related_tests": 6,
    "confidence": 0.91
  },
  "direct_dependents": [
    {
      "id": "sym:java:com.example.payment.PaymentController.create",
      "type": "METHOD",
      "file_path": "src/main/java/com/example/payment/PaymentController.java",
      "relationship": "CALLS",
      "confidence": 0.99
    }
  ],
  "tests": [
    {
      "id": "sym:java:com.example.payment.PaymentServiceTest.process_should_save",
      "file_path": "src/test/java/com/example/payment/PaymentServiceTest.java"
    }
  ],
  "affected_modules": ["payment-service", "checkout-service"],
  "truncated": false,
  "next_cursor": null
}
```

## Compact-response rule
Default response returns summary + bounded IDs/references. Full source details require explicit expansion.

## Incremental indexing
`Git diff → changed files → changed symbols → affected graph region → incremental update`

The MVP does not promise perfect rename/move/refactor detection.

## Storage escalation
Stay on SQLite/local storage until at least one condition is demonstrated:
- shared remote access is required
- ≥2 consumers need the same persistent index
- concurrency becomes a measured bottleneck
- local DB fails the benchmark target

A graph database is optional and must be justified by traversal/query benchmarks.

## Success metrics
Primary:
- task success
- input tokens
- total tokens
- wall-clock latency
- tool calls

Secondary:
- context precision
- irrelevant files retrieved
- duplicate retrieval
- relationship false-positive rate
- index build time
- incremental update time
- query p50/p95
- response size

The first release should report concrete measurements on the benchmark task set rather than generic claims.

## Privacy/security
### Local mode — default
- Source code is processed locally.
- No source code is transmitted to a cloud service by default.
- Index files remain in the local workspace/application storage.

### Remote/cloud mode — opt-in only
Must define before implementation:
- authentication
- authorization
- encryption in transit and at rest
- tenant isolation
- retention period
- deletion semantics
- audit logs
- repository access boundaries
- data export policy

Never silently upload repository source code or indexes.

## Evolution
`Java Codebase Graph → Code Impact Engine → Context Pack → MCP → benchmark/eval → provider adapters → multi-language → Codebase Knowledge Graph / Code Intelligence Platform`

## Kill criterion
After 2 scope-limited benchmark rounds, if the implementation does not demonstrate a meaningful advantage over available providers/baselines, stop building a proprietary graph engine. Move to provider adapters, context optimization, orchestration, or archive the capability.

