# 07 --- AI Handoff v2.3

## Đây là luật vận hành cho AI Agent

Trước khi coding/research: 1. Đọc source-of-truth docs. 2. Kiểm tra
decision log. 3. Kiểm tra competitor nếu thay đổi product scope. 4.
Không tự tạo platform component nếu trigger chưa đạt. 5. Không đổi
canonical tool name. 6. Không tạo artifact schema placeholder nếu
downstream phụ thuộc.

## Product thesis

AI Agents là workers.

Tools là capability/infrastructure giúp workers: - ít token hơn; - ít
latency hơn; - có structured knowledge; - deterministic hơn; - dễ
observe hơn.

## Competitive rule

Nếu một capability đã được sản phẩm mature giải quyết tốt: - không clone
mặc định; - cân nhắc adapter; - hoặc tìm differentiation rõ ràng; - hoặc
đổi scope.

## Architecture rule

Nếu AI đề xuất: - Registry; - Auth; - Event Bus; - Plugin System; -
Central Platform;

AI phải kiểm tra trigger định lượng trong
`02_ECOSYSTEM_ARCHITECTURE_VI.md` trước.

## Codebase Graph rule

Không được mô tả Codebase Graph như một graph visualizer đơn thuần.

Nhưng cũng không được giả định rằng graph engine tự xây là lợi thế.

MVP hiện tại ưu tiên: - agent-facing queries; - compact response; -
context composition; - benchmarks; - adapters.

## When uncertain

Không đoán. Nêu: - assumption; - evidence; - affected document; -
proposed decision.

Sau khi quyết định, cập nhật `11_DECISION_LOG_VI.md`.


### Quy tắc bảo trì tài liệu

Không append corrective patch vào cuối file vận hành. Phải merge thay đổi vào section
canonical hiện tại và ghi lịch sử trong `11_DECISION_LOG.md`.
