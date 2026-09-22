# 09 --- Competitor & Differentiation

## Mục đích

Không được bắt đầu một tool nếu chưa biết capability đó đã được giải
quyết đến đâu.

## Competitor landscape

  -----------------------------------------------------------------------
  Công cụ                 Mạnh ở                  Không nên clone
  ----------------------- ----------------------- -----------------------
  Tree-sitter             incremental parsing,    parser runtime
                          syntax tree, nhiều      
                          language                

  ast-grep                structural              AST search/rewrite core
                          search/rewrite          

  CodeQL                  code database +         generic static-analysis
                          powerful                engine
                          queries/security        
                          analysis                

  GitNexus                code knowledge graph +  generic repo graph +
                          MCP + agent integration MCP clone

  Sourcegraph             large-scale code        general code search
                          search/code             platform
                          intelligence            
  -----------------------------------------------------------------------

Tree-sitter là incremental parser và có mục tiêu parse nhanh, robust
trên nhiều ngôn ngữ. citeturn0search0

ast-grep cung cấp structural search/rewrite dựa trên AST và hỗ trợ nhiều
ngôn ngữ. citeturn0search10turn0search8

CodeQL xây database từ code và cho phép chạy query để phân tích code.
citeturn0search2turn0search3

GitNexus hiện đã kết hợp Tree-sitter, resolution, graph, hybrid search
và MCP/CLI cho AI coding tools. citeturn0search1turn0search6

## Differentiation hypothesis

Đây là **hypothesis**, chưa phải fact:

> Ecosystem có thể tạo giá trị nếu trở thành lớp agent-context
> optimization nằm trên hoặc bên cạnh các code intelligence providers,
> thay vì cố thay thế chúng.

### Testable differentiators

1.  **ContextPack quality**
    -   Với cùng task, context được chọn có precision/recall tốt hơn
        baseline.
2.  **Token efficiency**
    -   Agent đạt cùng task success với ít token hơn.
3.  **Latency**
    -   Giảm số round-trip search/read/tool.
4.  **Composition**
    -   Impact → tests → API → Git diff → ContextPack trong một
        workflow.
5.  **Provider neutrality**
    -   Có thể lấy graph từ provider A/B mà không khóa ecosystem.
6.  **Local privacy**
    -   Local mode không upload source code.

## Kill criterion

Nếu benchmark cho thấy: - không đạt token/time threshold; - không có
workflow composition advantage; - hoặc GitNexus/Sourcegraph/CodeQL đã
cung cấp capability tương đương mà không có gap đáng kể;

thì **không tiếp tục xây graph engine riêng**.

Chuyển sang: - adapter; - context optimization; - tool orchestration; -
hoặc một tool khác.

Đây là một quyết định hợp lệ, không phải thất bại.


## Ma trận đối thủ Context / Agent Tooling

| Tool | Đối thủ / dự án | Capability liên quan | Mức overlap | Giả thuyết khác biệt |
|---|---|---|---|---|
| Token Diff | Langfuse | tracing LLM/agent, token/cost | Cao | artifact token diff nhỏ, local-first |
| Token Diff | Helicone | observability request/token | Cao | provider-neutral, local |
| Token Diff | PromptLayer | prompt/request tracking | Trung bình | tập trung đo hiệu quả context/tool-result |
| Context Pack | LangChain | contextual compression/retrieval | Cao | framework-neutral, bounded context artifact |
| Context Pack | LlamaIndex | retrieval/post-processing | Cao | contract context ổn định, dùng được qua nhiều framework |
| Context Pack | Continue | context providers / context assembly | Cao | artifact context độc lập, machine-readable |
| Tool Result Compressor | LangChain | contextual compression | Cao | nén tool-result với giới hạn và metric rõ |
| Tool Result Compressor | LlamaIndex | node post-processing | Cao | contract độc lập framework |
| Tool Result Compressor | Continue | agent context assembly | Trung bình | artifact compression đo được token savings |
| Semantic Cache | GPTCache | semantic/LLM caching | Cao | contract cache rõ, local-first |
| Semantic Cache | Redis semantic caching | similarity cache | Cao | tool behavior hoàn chỉnh thay vì primitive hạ tầng |
| Semantic Cache | Portkey | managed semantic caching | Cao | provider-neutral/local-first |

### Gate competitor cho 1★

Mỗi tool 1★ phải có **ít nhất 3 đối thủ/dự án liên quan** trước khi code:
1. overlap chính xác;
2. capability commodity có thể tái sử dụng;
3. giả thuyết khác biệt;
4. benchmark có khả năng bác bỏ giả thuyết.

Không đạt khác biệt định lượng → NO-GO hoặc rescope.
