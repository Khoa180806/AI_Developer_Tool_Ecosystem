# Decision Log

## D-001 — Tool-first
Build independent tools before shared platform infrastructure.

## D-002 — Quantitative platform triggers
Shared infrastructure is introduced only when documented usage thresholds are met.

## D-003 — Canonical naming
The Tool Catalog is the single source of truth.
- Prompt Cache → Semantic Cache when semantic reuse is intended.
- Impact Analysis → Code Impact Engine.
- Codebase Graph and Codebase Knowledge Graph are distinct capability levels.
- TokenOS / AgentOS are evolution/platform names, not early standalone tools.

## D-004 — Do not clone mature tools
Do not clone GitNexus, Sourcegraph, CodeQL, tree-sitter, or ast-grep. Differentiate through compact agent queries, context composition, benchmarks, provider adapters, and local privacy.

## D-005 — Codebase Graph MVP
Java-only. Tree-sitter Java for syntax parsing. Semantic resolution is a separate layer.

## D-006 — MVP scale
10–500 KLOC, ≤20,000 source files, one local repository. Stretch target 500 KLOC–1 MLOC.

## D-007 — MVP storage
SQLite/local embedded. Escalate only from measured shared-access, concurrency, or benchmark needs.

## D-008 — Compact-response-first
All agent-facing interfaces should return bounded summaries first and details on demand.

## D-009 — Source-code privacy
Local mode does not send source code off machine by default. Remote/cloud mode requires encryption, retention/deletion, tenant isolation, access control, and audit specification before implementation.

## D-010 — Initial ICP
Developer using an AI coding agent on Java/TypeScript repositories.

## D-011 — Benchmark threshold
Pass when ≥20% token reduction with ≤2pp success drop, OR ≥20% latency reduction with equivalent success, OR ≥10pp success improvement with ≤20% token increase.

## D-012 — Codebase Graph kill criterion
After 2 scope-limited benchmark rounds without a meaningful advantage over suitable baselines/providers, stop building a proprietary graph engine and move to adapters/context optimization/orchestration or archive.

## D-013 — Candidate tools
Dependency Explorer, Call Graph, and Semantic Code Search remain candidates and are explicitly marked as not scheduled. Their presence in the catalog does not imply roadmap commitment.

## D-014 — Evolution names
TokenOS, AgentOS, and AI Agent Control Plane are future evolution/platform layers. They must not be treated as ordinary 1★–5★ standalone tools.

## D-015 — Semantic Cache remains one canonical tool

T04 has one canonical ID. 1★ is the exact/normalized-key MVP; 3★ is semantic-similarity
evolution.

## D-016 — ImpactReport follows the common transport envelope

ImpactReport is a data artifact. `truncated` and `next_cursor` are transport metadata
in the common envelope, not duplicate artifact fields.

## D-017 — Fixed benchmark baseline

B1 is a pinned GitNexus release/commit. No per-task provider substitution; unsupported
capabilities are N/A.

## D-018 — Reproducible repository manifest

Three Java repositories and exact commit SHAs must be frozen before measurement.

## D-019 — Solo-builder planning baseline

Roadmap time-boxes assume one solo builder at approximately 10 hours/week.


## D-020 — Operational files must be merged, not patched
Current-state operational documents MUST directly reflect the latest accepted decision.
Historical rationale belongs in the Decision Log; append-only patch sections are not a
valid substitute for updating the authoritative section.

## D-021 — 1★ competitor gate is per tool
Every 1★ tool requires at least three relevant competitor/project entries before coding.
Shared competitor rows do not count unless they explicitly identify the tool overlap.

## D-022 — Index and release naming must match
The root index version and changelog filename are part of the documentation consistency
check. The canonical changelog filename is `V2.3_CHANGELOG.md`.

## D-023 — Tool implementation architecture and technology selection
Tools in the ecosystem are not required to share a single language runtime. Each tool
chooses the most suitable technology stack based on its execution role, developer ICP,
and distribution model. For T01 (Token Diff), TypeScript/Node.js is selected with pure-JS
tokenizer (js-tiktoken) to avoid native compilation dependencies, matching the TypeScript
ICP-1 profile and enabling lightweight CLI and SDK distribution. Development follows a
multi-repo structure where tool repositories remain independent while conforming strictly
to the canonical schemas and integration envelopes.

