# 01 --- Vision v2.3

## Vision

Xây một hệ sinh thái tool giúp developer và AI Agent: - lấy đúng thông
tin; - với ít bước hơn; - ít token hơn; - ít latency hơn; - có
structured data hơn; - và có khả năng lặp lại/reuse.

## ICP cho giai đoạn đầu

Không phục vụ tất cả developer cùng lúc.

### ICP-1 --- Developer dùng AI coding agent trên repository Java/TypeScript

Đây là người dùng đầu tiên.

Task mẫu: - hiểu một service; - tìm impact của symbol; - tìm
callers/callees; - tạo context cho bug/refactor; - giảm context/token
khi Agent làm việc.

### ICP-2 --- AI Agent builder

Sau khi ICP-1 chứng minh được value: - MCP; - SDK; - context APIs; -
telemetry; - agent integration.

DevOps/SRE/enterprise là phase sau.

## Strategic thesis

Một prompt có thể giải quyết task một lần.

Tool có lợi thế khi nó: - index một lần và query nhiều lần; - duy trì
state; - cache; - tạo graph; - chuẩn hóa dữ liệu; - giảm context; - cung
cấp API/MCP ổn định; - chạy tự động trong workflow.

## Không cạnh tranh với AI coding assistant

Không xây: - chatbot tổng quát; - IDE tổng quát; - coding agent tổng
quát.

Xây lớp capability mà nhiều Agent khác nhau có thể dùng.

## Tại sao không dùng công cụ có sẵn?

Đây là câu hỏi bắt buộc trước khi code.

Hiện đã có các lớp công cụ mạnh: - Tree-sitter cung cấp incremental
parsing và hỗ trợ nhiều ngôn ngữ. citeturn0search0 - ast-grep cung
cấp structural search/rewrite trên AST và hỗ trợ nhiều ngôn ngữ.
citeturn0search10turn0search8 - CodeQL tạo database từ code và cho
phép chạy query phân tích code. citeturn0search2turn0search3 -
GitNexus hiện đã cung cấp graph-powered code intelligence, indexing bằng
Tree-sitter, graph storage, hybrid search và MCP/CLI integration.
citeturn0search1turn0search6

### Vì vậy, không lấy "AST → Graph → MCP" làm differentiation.

Differentiation mục tiêu của ecosystem là:

1.  **Compact-response-first:** mọi query phục vụ Agent phải tối ưu
    output theo context budget.
2.  **Context composition:** kết hợp code graph + impact + tests + API +
    Git diff thành ContextPack có giới hạn rõ.
3.  **Benchmark-driven:** đo token/time savings thay vì chỉ demo graph.
4.  **Provider adapters:** có thể dùng code intelligence engine có sẵn
    thay vì bắt người dùng re-index nếu không cần.
5.  **Cross-tool composition:** Code Intelligence → Context Router →
    Tool Result Compressor → Agent Trace.
6.  **Agent workflow integration:** capability được thiết kế cho vòng
    lặp Agent, không chỉ cho UI khám phá code.
7.  **Privacy/local-first:** source code mặc định không rời máy trong
    local mode.

### Điều không được tuyên bố

Không tuyên bố: \> "Chúng ta có graph tốt hơn mọi tool hiện có."

Chỉ tuyên bố capability nào benchmark chứng minh tốt hơn.

## Success metrics

Mỗi tool phải có baseline và threshold trong benchmark tương ứng.

Các metric chung: - token reduction; - latency; - context precision; -
task success; - cache hit rate; - indexing/query speed; - failure rate.
