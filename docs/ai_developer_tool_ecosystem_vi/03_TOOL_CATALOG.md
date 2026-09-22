# 03 --- Tool Catalog v2.3

Tên trong catalog là **canonical names**. Roadmap bắt buộc dùng đúng tên
này.

## 1. Code Intelligence

### Codebase Graph

Canonical base capability: repository → symbols → relationships →
graph/query.

### Code Impact Engine

Canonical capability: từ changed symbol/file/commit → affected
code/tests/APIs/services.

### Codebase Knowledge Graph

Canonical capability: graph + semantic relationships + higher-level code
concepts.

### Code Intelligence Platform

Canonical 6★ aggregation of graph, impact, context, MCP and
integrations.

## 2. Context

### Token Diff

So sánh token usage.

### Context Pack

Tạo context có giới hạn và có mục đích.

### Context Router

Chọn context source.

### Context Compressor

Nén context.

### Tool Result Compressor

Nén output tool.

### Semantic Cache

Cache theo semantic similarity.

### Token Budget Manager

Giới hạn token/cost.

### TokenOS

Long-term 6★ system combining
routing/cache/compression/budget/telemetry.

## 3. Agent

### Agent Trace Viewer

Quan sát Agent run.

### Agent Memory Engine

Quản lý memory.

### MCP Tool Optimizer

Tối ưu schema/description/result.

### LLM Router

Route model.

### Agent Cost Profiler

Phân tích cost.

### MCP Mesh

Long-term routing/discovery/policy layer for many MCP servers.

### Agent Security Sandbox

Sandbox execution.

### AgentOS

Long-term agent runtime.

### AI Agent Control Plane

Long-term governance/control layer.

## 4. Developer

### SQL Explain Visualizer

### HTTP Flow Recorder

### Log Timeline

### API Contract Explorer

### Production Replay Tool

## 5. Cache / Prompt

### Prompt Cache

**Đã đổi tên canonical thành `Semantic Cache` khi capability dựa trên
semantic similarity.**

Nếu sau này có một capability cache prefix/exact prompt khác biệt thật
sự, phải tạo tên riêng; không dùng Prompt Cache như alias.

## 6. Non-tool projects

Mỗi star tối đa một non-tool project. Chỉ dùng để validate ecosystem.


## Quy tắc trạng thái hiện tại

Bảng này là nguồn chân lý cho ID canonical, tên, trạng thái và mapping roadmap.
Một milestone tiến hóa không tạo ra một tool/ID thứ hai.
