# T02 — Context Pack

**Canonical name:** Context Pack
**ID:** T02
**Status:** Stable (v0.1.1 released) | **Level:** 1★
**Package:** `ai-context-pack` (npm) | **CLI Binaries:** `cx`, `cpack`, `context-pack`, `ai-context-pack`
**Repository:** https://github.com/Khoa180806/context-pack.git

## Applicable decisions

- D-001 — Tool-first
- D-003 — Canonical naming
- D-008 — Compact-response-first
- D-009 — Source-code privacy (100% local, no telemetry)
- D-011 — Benchmark threshold (-20% token reduction gate verified: achieved -75.2%)
- D-019 — Solo-builder planning baseline
- D-021 — 1★ competitor gate is per tool
- D-023 — Tool implementation architecture and technology selection

## Scope & Implementation Notes

- **Mô hình triển khai:** Độc lập tại repository `Khoa180806/context-pack` theo mô hình multi-repo.
- **Công nghệ & Kiến trúc (D-023):** TypeScript 5.6 / Node.js >= 18 (ESM), tokenizer thuần JS `js-tiktoken` (zero WASM/node-gyp dependencies), `fast-glob`, `commander` CLI, `picocolors` ANSI tinting, `vitest` unit/integration test suite (42/42 tests green).
- **Tính năng cốt lõi:**
  - `cx` / `cpack` / `context-pack`: Đóng gói context thông minh dựa trên token budget trần.
  - TF-IDF & BM25 Relevance Scoring: Tính điểm liên quan giữa task instruction và AST/file slices.
  - Greedy Knapsack Packing: Trích xuất các lát cắt tối ưu nhất mà không vượt quá ngân sách token.
  - Multi-line & Glob Resolution: Hỗ trợ nạp hàng loạt tệp và mẫu glob.
  - Dual-mode formatting: Giao diện terminal ANSI trực quan hoặc cấu trúc JSON envelope (`--json`) chuẩn metadata/duration cho AI coding agents.
  - Deterministic exit codes: 0 (thành công), 1 (lỗi hệ thống), 2 (sai tham số/missing flag), 3 (không tìm thấy tệp), 4 (không có quyền đọc).
- **Kết quả Benchmark (D-011):** Đã kiểm thử thực tế trên codebase `token_diff`, đạt mức cắt giảm token **-75.2%** (vượt xa chỉ tiêu -20% của D-011) với thời gian phản hồi dưới 400ms. Xem chi tiết tại [BENCHMARK_RESULTS.md](BENCHMARK_RESULTS.md).
- **Trạng thái CI/CD:** GitHub Actions CI matrix trên Ubuntu & Windows (Node 18, 20, 22).
