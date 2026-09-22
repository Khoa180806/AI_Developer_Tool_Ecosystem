# Vision

## Vision statement
Build a family of specialized developer tools that improve the information flow between codebases, developer workflows, and AI agents.

The ecosystem should help an agent answer the right question with fewer files, fewer tool calls, fewer tokens, lower latency, and more reliable structure.

## Initial ICP
### ICP-1 — AI-assisted Java/TypeScript developer
A developer working in a real repository with an AI coding agent and repeatedly spending time on repository exploration, context selection, debugging, impact analysis, and tool-output noise.

### ICP-2 — AI Agent builder
A developer building coding/repository agents who needs predictable context, compact tool results, caching, observability, and cost control.

ICP-2 becomes primary only after ICP-1 validates the core value proposition.

## Main problems
- Agents repeatedly rediscover the same repository relationships.
- Large tool results waste context and tokens.
- Context selection is often broader than necessary.
- Impact analysis requires repeated searches across files.
- Agent workflows are difficult to benchmark and compare.
- Tool output formats vary and are difficult to compose.
- Source-code privacy makes uncontrolled cloud indexing undesirable for some teams.

## Strategic thesis
The durable value is not simply “AI can understand code.” The value is infrastructure that provides:

`Index once → query many times → return compact structure → compose artifacts → measure outcome → reuse/cache`

## Differentiation hypotheses
1. Compact-response-first agent interfaces.
2. ContextPack quality and measurable context reduction.
3. Token/time savings measured against real agent tasks.
4. Provider-neutral adapters instead of dependence on one graph engine.
5. Composition between specialized tools.
6. Local-first privacy.
7. Reproducible benchmark/evaluation infrastructure.

## Success metrics
At ecosystem level:
- ≥20% token reduction with task-success drop ≤2 percentage points; OR
- ≥20% latency reduction with equivalent success; OR
- ≥10 percentage-point task-success improvement with token cost ≤+20%.

Supporting metrics:
- tool calls/task
- irrelevant files retrieved
- duplicate retrieval
- context precision
- p50/p95 latency
- cache hit rate

## Example
Without code intelligence:
`Agent → search files → open files → search references → open more files → infer impact`

With the ecosystem:
`Agent → get_impact(symbol) → compact ImpactReport → ContextPack → targeted files only`

The second flow is valuable only if benchmark data proves it improves tokens, latency, success, or some combination without unacceptable trade-offs.
