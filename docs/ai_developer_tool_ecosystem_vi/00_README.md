# AI Developer Tool Ecosystem --- Source of Truth v2.3

## Mục tiêu

Đây là bộ tài liệu nguồn duy nhất cho **AI Developer Tool Ecosystem**.

Chiến lược: \> Xây từng tool có giá trị độc lập → đo lường → chuẩn hóa
contract → tích hợp vào ecosystem.

AI Agent không phải đối thủ của ecosystem. Agent là consumer của các
capability chuyên dụng.

## 4 nguyên tắc bắt buộc

1.  **Tool-first:** không dựng platform core trước khi có trigger định
    lượng.
2.  **Không clone sản phẩm đã giải quyết tốt:** trước khi code phải làm
    competitor/differentiation check.
3.  **Contract trước implementation:** schema và interface của artifact
    phải được chốt trước khi tool downstream phụ thuộc vào nó.
4.  **Benchmark trước khi nâng cấp:** mỗi tool phải có baseline và
    ngưỡng pass.

## Reading order

1.  `01_VISION_VI.md`
2.  `02_ECOSYSTEM_ARCHITECTURE_VI.md`
3.  `03_TOOL_CATALOG_VI.md`
4.  `04_TOOL_LIFECYCLE_VI.md`
5.  `05_INTEGRATION_SPEC_VI.md`
6.  `06_ROADMAP_VI.md`
7.  `07_AI_HANDOFF_VI.md`
8.  `08_CODEBASE_GRAPH_SPEC_VI.md`
9.  `09_COMPETITOR_AND_DIFFERENTIATION_VI.md`
10. `10_BENCHMARK_PLAN_VI.md`
11. `11_DECISION_LOG_VI.md`

## Source-of-truth hierarchy

Khi tài liệu mâu thuẫn:

`11_DECISION_LOG_VI.md` → `05_INTEGRATION_SPEC_VI.md` → tool-specific
spec → `06_ROADMAP_VI.md` → catalog/vision.

Không tự đoán.

## Strategic decision hiện tại

**Không xây một GitNexus clone.**

Codebase intelligence vẫn là flagship, nhưng MVP phải tập trung vào: -
agent-facing compact query; - context budgeting; - impact/context
composition; - measurable token/time savings; - adapter/integration với
code intelligence engines có sẵn khi chúng đã giải quyết tốt phần
indexing/graph.

Nếu sau benchmark phát hiện graph engine riêng thực sự tạo lợi thế rõ
ràng, mới xây sâu hơn.


## Pre-Code Consistency Gate

Trước khi code một roadmap tool:
1. kiểm tra canonical ID trong Tool Registry;
2. xác nhận roadmap mapping là duy nhất hoặc được ghi rõ là evolution milestone;
3. pass competitor gate tương ứng;
4. kiểm tra schema với common transport envelope;
5. xác định benchmark baseline reproducible trước khi tuyên bố tool tạo giá trị.
