# T01 — Token Diff

**Canonical name:** Token Diff
**ID:** T01
**Status:** Stable (v0.1.1 released) | **Level:** 1★
**Package:** `ai-token-diff` (npm) | **CLI Binaries:** `td`, `token-diff`, `ai-token-diff`
**Repository:** https://github.com/Khoa180806/token-diff.git

## Applicable decisions

- D-001 — Tool-first
- D-003 — Canonical naming
- D-008 — Compact-response-first
- D-011 — Benchmark threshold
- D-019 — Solo-builder planning baseline
- D-021 — 1★ competitor gate is per tool
- D-023 — Tool implementation architecture and technology selection

## Scope & Implementation Notes

- **Mô hình triển khai:** Độc lập tại repo `Khoa180806/token-diff` theo mô hình multi-repo.
- **Công nghệ & Kiến trúc (D-023):** TypeScript 5.6 / Node.js >= 18 (ESM), tokenizer thuần JS `js-tiktoken` (zero native WASM/C++ build dependencies), `commander` CLI, `picocolors` ANSI tinting, `vitest` unit/integration test suite.
- **Tính năng cốt lõi:**
  - `diff <before> <after>`: So sánh token deltas, tỷ lệ phần trăm chênh lệch, ký tự, số dòng và tóm tắt.
  - `count <input>`: Đếm token cho tệp, chuỗi prompt thô hoặc luồng pipe.
  - Smart Input: Tự động phát hiện đường dẫn tệp vs. chuỗi prompt thô (kèm cảnh báo nhẹ ra stderr nếu không tìm thấy tệp).
  - Stdin support (`-`): Hỗ trợ nhận luồng dữ liệu pipe tiêu chuẩn Unix.
  - Dual-mode formatting: Bảng terminal căn lề thẳng hàng hoặc cấu trúc JSON envelope (`--json`) chuẩn metadata/duration cho AI agent.
  - Deterministic exit codes: 0 (thành công), 1 (lỗi nội bộ/pipe), 2 (sai tham số/unsupported model), 3 (không tìm thấy tệp), 4 (không có quyền đọc).
- **Trạng thái kiểm thử & CI/CD:** 20/20 tests passed, GitHub Actions CI/CD workflow tự động kiểm tra trên Ubuntu & Windows (Node 18, 20, 22).

