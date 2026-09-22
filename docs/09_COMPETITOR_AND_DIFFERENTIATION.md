# Competitor and Differentiation Analysis

## Baseline landscape
| Technology/product | Relevant capability | What we should NOT clone |
|---|---|---|
| Tree-sitter | Fast incremental syntax parsing and syntax trees | Parser runtime/grammar ecosystem as a competitive moat |
| ast-grep | Structural AST search/rewrite | Generic AST search/rewrite core |
| CodeQL | Code database and query-based analysis | Generic static-analysis/query platform |
| GitNexus | Code knowledge graph and agent/MCP-oriented code intelligence | Generic repository graph + MCP clone |
| Sourcegraph | Large-scale code search and code intelligence | General-purpose code search platform |

## Differentiation hypotheses
### 1. ContextPack quality
The system should return the smallest useful context set for a task rather than merely expose more repository data.

### 2. Token efficiency
Measure whether structured results reduce agent input/output tokens while preserving task success.

### 3. Latency
Precompute expensive relationships so repeated agent queries are faster than repeated raw search/exploration.

### 4. Composition
`ImpactReport → ContextPack → Token Diff → Trace` should create value that an isolated code graph does not provide.

### 5. Provider neutrality
Code intelligence should support multiple providers/backends when practical. The ecosystem should not depend on one proprietary graph implementation.

### 6. Local privacy
Provide a useful local mode for repositories that cannot be uploaded to third-party services.

## Competitive test
For each capability:
1. Select the closest existing provider.
2. Define identical tasks.
3. Compare task success, tokens, latency, tool calls, and result precision.
4. Record where our system wins, ties, or loses.
5. Do not claim superiority unless measured.

## Kill rule
If two scope-limited benchmark rounds show no meaningful gap, do not continue building the same core. Prefer an adapter, orchestration layer, context optimization, or archive.


## Context / Agent Tooling Competitor Coverage

The competitor gate applies to every tool before implementation, not only Code Intelligence.
The following matrix covers the first 1★ tools and their closest documented alternatives.

| Tool | Competitor / project | Relevant capability | Overlap | Differentiation hypothesis |
|---|---|---|---|---|
| Token Diff | Langfuse | LLM tracing, token/cost observability | High | Small, local-first token-diff artifact focused on before/after context efficiency |
| Token Diff | Helicone | LLM request/token observability | High | Provider-neutral local measurement rather than a hosted observability suite |
| Token Diff | PromptLayer | Prompt/request tracking and observability | Medium | Measure context/tool-result efficiency rather than prompt lifecycle management |
| Context Pack | LangChain | Retrieval and contextual-compression abstractions | High | Framework-neutral, bounded context artifact with explicit token budget |
| Context Pack | LlamaIndex | Node postprocessors / retrieval post-processing | High | Stable cross-framework context contract and compact agent-facing output |
| Context Pack | Continue | Context providers and code-context assembly for coding agents | High | Standalone machine-readable context artifact that can compose across agents/tools |
| Tool Result Compressor | LangChain | Contextual compression / retrieval compression | High | Tool-output-specific compression with deterministic size/quality accounting |
| Tool Result Compressor | LlamaIndex | Node postprocessors and response-context reduction | High | Generic tool-result contract independent of one retrieval framework |
| Tool Result Compressor | Continue | Agent context selection/assembly | Medium | Explicit compression artifact, bounded output, and measurable token savings |
| Semantic Cache | GPTCache | LLM response caching with similarity-based reuse | High | Stable cache contract with explicit invalidation, namespace and observability semantics |
| Semantic Cache | Redis semantic caching | Vector/similarity-backed semantic cache patterns | High | Tool-first cache behavior rather than infrastructure-only primitives |
| Semantic Cache | Portkey | Managed semantic caching for LLM requests | High | Local-first/provider-neutral implementation with portable cache artifacts |


## 1★ Competitor Gate

For every 1★ tool, the pre-code review MUST record **at least 3 relevant existing
products/projects** in the matrix above or an updated equivalent. It must also record:
1. exact overlap;
2. commodity capability we will reuse rather than rebuild;
3. differentiation hypothesis;
4. one benchmark capable of falsifying the hypothesis.

If fewer than three relevant alternatives can be identified, the gate is not passed.
If measurable differentiation cannot be demonstrated, the tool is NO-GO or must be rescoped.

### Source notes
The current matrix uses public product/project documentation and is intentionally
treated as a hypothesis map, not a claim that every competitor provides identical
functionality. For example, Portkey publicly documents semantic caching and its
cache/observability behavior; those claims should be rechecked at benchmark time.
