# 06 --- Roadmap v2.3

## Canonical rule

Roadmap chỉ được dùng tên có trong `03_TOOL_CATALOG_VI.md`.

## ⭐ 1 --- Foundation

Tools: 1. Token Diff 2. Context Pack 3. Tool Result Compressor 4.
Semantic Cache

Non-tool duy nhất: - Dev Workspace

### Exit

Tất cả 4 tool không bắt buộc phải hoàn thành. Chỉ cần ≥2 tool đạt Stable
theo Definition of Done và có benchmark đạt threshold.

## ⭐⭐ 2 --- Developer Utility

Tools: 1. SQL Explain Visualizer 2. HTTP Flow Recorder 3. Log Timeline
4. API Contract Explorer

Non-tool: - Developer Collaboration Platform

### Exit

≥2 tool Stable + ít nhất 1 tool có real-user validation.

## ⭐⭐⭐ 3 --- AI-Aware

Tools: 1. Context Router 2. Semantic Cache 3. Agent Trace Viewer 4. MCP
Tool Optimizer 5. Token Budget Manager

Non-tool: - Agent Observability Platform

### Exit

Có benchmark chứng minh ít nhất một trong: - ≥20% token reduction; -
≥20% latency reduction; - hoặc ≥10% task success improvement trên task
set được định nghĩa trong `10_BENCHMARK_PLAN_VI.md`.

## ⭐⭐⭐⭐ 4 --- Deep Intelligence

Tools: 1. Codebase Knowledge Graph 2. Agent Context Debugger 3. LLM
Router 4. Agent Memory Engine 5. Production Replay Tool

Non-tool: - Production Replay Platform

### Exit

≥2 deep tools Stable + có composition thật giữa ít nhất 2 tool.

## ⭐⭐⭐⭐⭐ 5 --- Infrastructure

Tools: 1. Code Impact Engine 2. Context Router / Context Engine
capabilities 3. MCP Mesh 4. Agent Security Sandbox 5. Agent Cost
Profiler

Non-tool: - Agent Security Platform

### Exit

Chỉ bắt đầu khi: - ≥4 tools Stable; - ≥2 tools có cùng shared
dependency; - platform triggers trong `02` đạt; - có ít nhất 3 real
repositories/projects hoặc equivalent benchmark environments.

## ⭐⭐⭐⭐⭐⭐ 6 --- Ecosystem Platform

Core: 1. Code Intelligence Platform 2. TokenOS 3. AgentOS 4. AI Agent
Control Plane

Non-tool: - AI Developer Infrastructure Platform

### Exit

6★ không có deadline cố định.

Chỉ được gọi là 6★ khi: - ≥5 Stable tools; - registry có lý do thực
tế; - auth/policy có consumer thật; - có shared telemetry; - có
integration giữa ≥3 tool; - benchmark cho thấy ecosystem tạo value vượt
tool độc lập.

## Vertical slices

### Slice 1

Code intelligence provider → compact query → MCP → Agent.

### Slice 2

Impact → Context Pack → Agent.

### Slice 3

Context Pack → Context Router → Token Diff.

### Slice 4

MCP Optimizer → Result Compressor → Trace.

### Slice 5

Chỉ khi trigger đạt: Tool Registry → multiple tools → shared
auth/config/telemetry.


## Mapping Semantic Cache

T04 Semantic Cache chỉ có **một canonical ID**:
- **1★:** MVP — exact/normalized-key cache.
- **3★:** Tiến hóa — semantic similarity / embedding-based lookup.

Mục 3★ là milestone tiến hóa, không phải tool thứ hai.
