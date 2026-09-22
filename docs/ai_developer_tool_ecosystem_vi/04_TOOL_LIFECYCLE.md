# 04 --- Tool Lifecycle v2.3

## Nguyên tắc

Build tool độc lập trước. Platform sau.

## 1. Discovery

Xác định user/problem/input/output và baseline.

## 2. Competitive check --- bắt buộc

Trước khi code: - tìm ít nhất 3 sản phẩm/tool liên quan; - xác định
overlap; - xác định capability đã commodity; - ghi differentiation; -
nếu không có differentiation đo được → **NO-GO** hoặc đổi scope.

## 3. MVP

Tool chạy độc lập, ưu tiên local.

## 4. Contract

Chốt input/output schema trước khi tool downstream phụ thuộc.

## 5. Benchmark

Chạy baseline + tool.

## 6. Integration

CLI/SDK/API/MCP tùy use case.

## 7. Observability

Latency, error, size, cache, token/cost.

## 8. Registry/composition

Chỉ sau khi platform trigger đạt.

## 9. Platform trigger

Không tự động đi qua bước này.

Chỉ dựng shared component khi đạt ngưỡng trong
`02_ECOSYSTEM_ARCHITECTURE_VI.md`.

## Definition of Done

Một tool chỉ được gọi là `Stable` khi: - có standalone usage; - có
schema; - có version; - có tests; - có benchmark; - có documented
failure modes; - có security/privacy notes; - có ít nhất một real user
hoặc benchmark task set đạt threshold.

## Time-box

Mỗi tool phải có time-box trước khi bắt đầu.

Mặc định: - 1★: 1--2 tuần/tool; - 2★: 2--4 tuần/tool; - 3★: 3--6
tuần/tool; - 4★: 1--2 tháng/tool; - 5★: 2--4 tháng/module; - 6★: chỉ bắt
đầu sau khi các capability nền đã chứng minh value.

Nếu vượt time-box \>50% mà chưa đạt benchmark: - giảm scope; - đổi
implementation; - hoặc archive.

Không mở rộng scope để "cứ làm tiếp".


## Baseline năng lực lập kế hoạch

Roadmap giả định **1 solo builder, khoảng 10 giờ/tuần**.

| Level | Time-box | Effort baseline |
|---|---:|---:|
| 1★ | 1–2 tuần | ~10–20 giờ |
| 2★ | 2–4 tuần | ~20–40 giờ |
| 3★ | 3–6 tuần | ~30–60 giờ |
| 4★ | 1–2 tháng | ~40–80 giờ |
| 5★ | 2–4 tháng | ~80–160 giờ |

Đây là planning ceiling, không phải cam kết.
