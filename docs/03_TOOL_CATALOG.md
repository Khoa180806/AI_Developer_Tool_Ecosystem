# Canonical Tool Catalog / Registry

**This file is the single source of truth for tool names. Roadmap names MUST match this registry exactly.**

Status values: `Scheduled`, `Candidate`, `Evolution`, `Platform`.

| ID | Canonical name | Description | Status | Planned level |
|---|---|---|---|---|
| T01 | Token Diff | Compare token usage between prompts, contexts, tool results, or workflow versions. | Scheduled | 1★ |
| T02 | Context Pack | Produce a bounded, reusable package of the most relevant context for an agent task. | Scheduled | 1★ |
| T03 | Tool Result Compressor | Compress verbose tool output while preserving actionable structure and references. | Scheduled | 1★ |
| T04 | Semantic Cache | Reuse prior results for semantically equivalent requests under explicit freshness rules. | Scheduled | 1★ (MVP) → 3★ (evolution) |
| T05 | SQL Explain Visualizer | Turn SQL execution plans into understandable performance structure and hotspots. | Scheduled | 2★ |
| T06 | HTTP Flow Recorder | Capture and reconstruct HTTP request/response flows for debugging and reproduction. | Scheduled | 2★ |
| T07 | Log Timeline | Normalize logs into a time-oriented diagnostic view. | Scheduled | 2★ |
| T08 | API Contract Explorer | Explore API schemas, endpoints, dependencies, and compatibility information. | Scheduled | 2★ |
| T09 | Context Router | Select and route relevant context among repositories, artifacts, tools, and agents. | Scheduled | 3★ |
| T10 | Agent Trace Viewer | Inspect agent steps, tool calls, latency, tokens, and outcomes. | Scheduled | 3★ |
| T11 | MCP Tool Optimizer | Analyze and optimize MCP tool schemas, descriptions, outputs, and call patterns. | Scheduled | 3★ |
| T12 | Token Budget Manager | Enforce and allocate token budgets across agent workflows. | Scheduled | 3★ / evolution → TokenOS |
| T13 | Codebase Graph | Build a queryable structural graph of a repository. | Scheduled | 4★ foundation |
| T14 | Agent Context Debugger | Explain why context was selected, omitted, duplicated, or truncated. | Scheduled | 4★ |
| T15 | LLM Router | Route tasks to models/providers according to policy, capability, cost, and latency. | Scheduled | 4★ |
| T16 | Agent Memory Engine | Store, retrieve, score, and manage reusable agent memory. | Scheduled | 4★ |
| T17 | Production Replay Tool | Reproduce production/API/agent scenarios from captured artifacts. | Scheduled | 4★ |
| T18 | Code Impact Engine | Compute affected symbols, modules, tests, and dependency regions for a code change. | Scheduled | 5★ |
| T19 | MCP Mesh | Compose and route multiple MCP providers/tools through a controlled interface. | Scheduled | 5★ |
| T20 | Agent Security Sandbox | Execute agent actions under explicit filesystem, network, process, and policy constraints. | Scheduled | 5★ |
| T21 | Agent Cost Profiler | Attribute model/tool/latency costs to agent tasks and workflows. | Scheduled | 5★ |
| T22 | Codebase Knowledge Graph | Higher-level semantic knowledge layer built on code intelligence artifacts; not a synonym for the raw Codebase Graph. | Evolution | 4★+ |
| T23 | Dependency Explorer | Explore dependency relationships interactively. | Candidate / Not yet scheduled | — |
| T24 | Call Graph | Explore caller/callee relationships as a focused view. | Candidate / Not yet scheduled | — |
| T25 | Semantic Code Search | Search code by semantic intent rather than only text/AST patterns. | Candidate / Not yet scheduled | — |
| T26 | TokenOS | Future token/context operating layer combining token measurement, budgeting, routing, caching, and policy. | Evolution / Platform | 6★ |
| T27 | AgentOS | Future operating layer for agent execution, memory, tools, policy, observability, and lifecycle. | Evolution / Platform | 6★ |
| T28 | AI Agent Control Plane | Future control plane for multi-agent/tool policy, routing, identity, governance, and operations. | Platform | 6★ |

## Naming rules
- `Prompt Cache` is **not** canonical. Use `Semantic Cache` when similarity-based reuse is intended.
- `Impact Analysis` is **not** canonical. Use `Code Impact Engine`.
- `Codebase Knowledge Graph` is a distinct higher-level capability; it must not silently replace `Codebase Graph`.
- `TokenOS`, `AgentOS`, and `AI Agent Control Plane` are evolution/platform names, not early standalone tools.
- Candidate tools are intentionally not scheduled. Their presence does not imply implementation commitment.
