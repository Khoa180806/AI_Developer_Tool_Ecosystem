# 10 --- Benchmark Plan

## Mục tiêu

Không dùng cảm giác để quyết định tool có giá trị.

Benchmark đầu tiên phải chứng minh: \> Tool giúp Agent hoàn thành task
với ít token/time hơn hoặc success rate cao hơn.

## Benchmark 1 --- Code Context

### Task set

Tạo 30 task từ 3 repository Java open-source:

-   10 task tìm symbol/dependency;
-   10 task impact/refactor;
-   10 task bug/debug context.

Mỗi task phải có: - question; - expected relevant files/symbols; -
expected result; - difficulty; - repository commit SHA.

## Baselines

### B0 --- Agent không có code intelligence tool

Agent chỉ có: - repository filesystem/search; - terminal; - model/tool
set cố định.

### B1 --- Agent dùng existing provider

Ví dụ GitNexus nếu capability/task phù hợp.

### B2 --- Ecosystem prototype

Dùng: - compact query; - ImpactReport; - ContextPack.

Không dùng model khác giữa các baseline.

## Metrics

### Primary

1.  Task success rate.
2.  Input tokens.
3.  Total tokens.
4.  Number of tool calls.
5.  Wall-clock latency.

### Secondary

-   context precision;
-   irrelevant files;
-   duplicate retrieval;
-   error rate.

## Initial thresholds

Prototype được xem là có signal nếu:

-   **≥20% token reduction** so với B0 mà task success không giảm \>2
    percentage points;
-   hoặc **≥20% latency reduction** với task success tương đương;
-   hoặc **≥10 percentage-point task success improvement** với token
    cost tăng không quá 20%.

Đây là threshold discovery, không phải marketing claim.

## Measurement rules

-   Cố định model/version.
-   Cố định temperature/config nếu có.
-   Cố định repository commit.
-   Warm-up riêng.
-   Chạy mỗi task ≥5 lần nếu variance cao.
-   Báo median và p95.
-   Lưu raw run metadata.

## Artifact

Mỗi benchmark run lưu:

``` json
{
  "run_id": "uuid",
  "task_id": "java-impact-07",
  "baseline": "B0",
  "model": "...",
  "repository_commit": "...",
  "success": true,
  "input_tokens": 1234,
  "total_tokens": 5678,
  "tool_calls": 12,
  "latency_ms": 2300
}
```

## Go / No-Go

### GO

Có ít nhất một metric primary đạt threshold mà không hy sinh nghiêm
trọng metric khác.

### NO-GO

Không đạt threshold sau 2 vòng scope-limited iteration.

Khi NO-GO: - đổi differentiation; - chuyển sang adapter; - hoặc archive
tool.

## Benchmark đầu tiên cho 1★

Nếu bắt đầu ecosystem bằng 1★ tool, ưu tiên **Token Diff** vì nó là
instrumentation tool.

Token Diff không tự chứng minh ecosystem value; nó cung cấp measurement
foundation cho các tool sau.


## Khóa reproducibility

### B1 cố định

**B1 = GitNexus tại release/commit được pin trong benchmark manifest.**
Không đổi provider giữa các task. Nếu B1 không hỗ trợ capability của task, ghi **N/A**
cho B1 và vẫn giữ task đó cho B0/B2.

### Repository manifest

Trước lần chạy benchmark đầu tiên phải freeze 3 Java open-source repositories và exact
commit SHA:

| repo_id | repository | commit_sha | size_band | task_count |
|---|---|---|---|---:|
| R1 | **PIN BEFORE RUN** | **PIN SHA** | 10–100 KLOC | 10 |
| R2 | **PIN BEFORE RUN** | **PIN SHA** | 100–300 KLOC | 10 |
| R3 | **PIN BEFORE RUN** | **PIN SHA** | 300–500 KLOC | 10 |

Placeholder không phải benchmark evidence. Benchmark chỉ reproducible sau khi 3 repo
và SHA được freeze.

### Raw metadata bắt buộc

`run_id`, `repo_id`, `commit_sha`, `task_id`, `difficulty`, `model`, `model_version`,
`temperature/config`, `baseline`, `success`, `input_tokens`, `output_tokens`,
`total_tokens`, `tool_calls`, `wall_clock_ms`, `timestamp`, error information.
