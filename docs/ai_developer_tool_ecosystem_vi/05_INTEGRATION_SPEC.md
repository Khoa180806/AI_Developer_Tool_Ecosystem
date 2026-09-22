# 05 --- Integration Specification v2.3

## 1. Interface

Một tool có thể expose: - Library - CLI - SDK/API - MCP

## 2. Compact-response-first --- QUY TẮC CHUNG

Đây là chuẩn bắt buộc cho mọi tool phục vụ AI Agent.

### Mặc định

Tool phải trả: 1. summary; 2. identifiers; 3. counts/metrics; 4.
references/handles; 5. details chỉ khi Agent yêu cầu.

Không trả toàn bộ raw payload nếu Agent không cần.

### Ví dụ

Không tốt:

``` json
{
  "all_files": [/* 20,000 files */]
}
```

Tốt:

``` json
{
  "summary": {
    "match_count": 27
  },
  "items": [
    {"id": "sym:PaymentService", "name": "PaymentService"}
  ],
  "next_cursor": "..."
}
```

### Quy tắc

Mỗi MCP tool phải có: - summary mode; - bounded output; -
pagination/cursor khi cần; - explicit detail expansion.

## 3. API envelope

``` json
{
  "data": {},
  "metadata": {
    "source": "...",
    "duration_ms": 10,
    "truncated": false,
    "schema_version": "1.0"
  }
}
```

## 4. Artifact schema rule

Không dùng `{}` hoặc `[]` placeholder cho artifact contract nếu
downstream đã phụ thuộc.

Artifact schema phải định nghĩa: - field; - type; - required/optional; -
identifier format; - semantics; - version.

## 5. Tool identity

``` json
{
  "tool_id": "codebase.graph",
  "version": "0.1.0"
}
```

## 6. Error codes

-   INVALID_INPUT
-   NOT_FOUND
-   PERMISSION_DENIED
-   TIMEOUT
-   RATE_LIMITED
-   DEPENDENCY_UNAVAILABLE
-   INTERNAL_ERROR

## 7. Security

Không đưa secret vào: - prompt; - tool result; - logs.

Mỗi remote integration phải có auth/authorization/tenant boundary.

## 8. Versioning

Breaking schema changes require a new schema/API version.

Không sửa field semantics âm thầm.
