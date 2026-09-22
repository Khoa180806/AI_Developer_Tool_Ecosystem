# Roadmap

**All names below are canonical names from `03_TOOL_CATALOG.md`.** Evolution/platform capabilities are explicitly marked and are not treated as ordinary standalone tools.

## 1★ — Instrumentation and Context Basics
- Token Diff
- Context Pack
- Tool Result Compressor
- Semantic Cache

Goal: establish measurement and compact-context primitives.

Exit criteria:
- ≥2 tools reach Stable.
- Benchmark harness exists.
- At least one workflow demonstrates measurable context/token improvement.

## 2★ — Developer Diagnostic Tools
- SQL Explain Visualizer
- HTTP Flow Recorder
- Log Timeline
- API Contract Explorer

Goal: turn common debugging information into structured, reusable artifacts.

Exit criteria:
- ≥2 tools reach Stable.
- At least one real-user validation.
- Schemas can be consumed by another tool or agent.

## 3★ — Agent Context and Observability
- Context Router
- Semantic Cache
- Agent Trace Viewer
- MCP Tool Optimizer
- Token Budget Manager

Goal: optimize agent information flow and make cost/latency measurable.

Exit threshold:
- ≥20% token reduction with task-success drop ≤2 percentage points; OR
- ≥20% latency reduction with equivalent success; OR
- ≥10 percentage-point task-success improvement with token cost ≤+20%.

## 4★ — Code Intelligence and Agent Context
- Codebase Graph
- Agent Context Debugger
- LLM Router
- Agent Memory Engine
- Production Replay Tool
- **Evolution:** Codebase Knowledge Graph

Goal: connect repository structure with context, memory, routing, and replay.

Important: Codebase Knowledge Graph is an evolution layer over code intelligence artifacts, not a replacement name for Codebase Graph.

Exit criteria:
- ≥2 deep tools Stable.
- At least one real composition between 2 tools.
- Codebase Graph passes its benchmark or is replaced by an adapter/provider strategy.

## 5★ — Agent Infrastructure
- Code Impact Engine
- MCP Mesh
- Agent Security Sandbox
- Agent Cost Profiler

Goal: provide production-grade impact, composition, security, and cost controls.

Start condition:
- ≥4 Stable tools.
- ≥2 tools share a dependency or infrastructure need.
- Platform triggers are met.
- ≥3 real repositories/projects or equivalent benchmark environments.

## 6★ — Platform Evolution
These are **not early standalone tools**:
- TokenOS — evolution of Token Diff + Token Budget Manager + related token/context capabilities.
- AgentOS — evolution of agent execution, memory, tools, policy, observability, and lifecycle capabilities.
- AI Agent Control Plane — control-plane evolution for multi-agent/tool routing, identity, policy, governance, and operations.

Start condition:
- ≥5 Stable tools.
- Registry need is demonstrated.
- Shared telemetry exists.
- Auth/policy has a real consumer.
- ≥3 tools compose through shared infrastructure.
- Platform benchmark demonstrates value beyond the individual tools.

## Vertical slices
1. `Codebase Graph → compact query → MCP → Agent`
2. `Code Impact Engine → Context Pack → Agent`
3. `Context Pack → Context Router → Token Diff`
4. `MCP Tool Optimizer → Tool Result Compressor → Agent Trace Viewer`
5. Only after trigger: `Tool Registry → multiple tools → shared auth/config/telemetry`

