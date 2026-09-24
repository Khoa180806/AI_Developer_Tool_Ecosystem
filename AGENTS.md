# AI Developer Tool Ecosystem — Agent Navigation

## Bắt buộc đọc trước MỌI task

1. [docs/00_README.md](docs/00_README.md) — principles, boundaries, source-of-truth hierarchy
2. [docs/03_TOOL_CATALOG.md](docs/03_TOOL_CATALOG.md) — canonical Tool Registry (single source of truth for names and IDs)
3. [docs/11_DECISION_LOG.md](docs/11_DECISION_LOG.md) — binding decisions D-001 → D-023; highest authority

## Trước khi code một tool cụ thể

1. [docs/04_TOOL_LIFECYCLE.md](docs/04_TOOL_LIFECYCLE.md) — lifecycle, gates, time-boxes, stable criteria
2. `tools/<tool-id>/AGENTS.md` — canonical name, applicable decisions, scope
3. `tools/<tool-id>/SPEC.md` — detailed specification (if exists)

## Hard gates — không code nếu chưa qua

1. **Canonical naming:** tool name và ID phải khớp đúng registry trong `docs/03_TOOL_CATALOG.md`.
2. **Competitor gate:** mỗi tool 1★ phải có ≥3 competitor/project entries đã documented (xem `docs/09_COMPETITOR_AND_DIFFERENTIATION.md`).
3. **Schema compliance:** schema khớp common transport envelope tại `docs/05_INTEGRATION_SPEC.md`.
4. **Benchmark baseline:** baseline đã pin theo `docs/10_BENCHMARK_PLAN.md` (repo manifest R1/R2/R3 frozen, B1 = pinned GitNexus).

## Quy tắc sửa tài liệu

- **KHÔNG** tạo file tên có số version (ví dụ: `V2_4_CHANGELOG.md`, `08_SPEC_v2.md`). Mọi thay đổi ghi vào `docs/CHANGELOG.md` bằng cách append section mới. Version thật sự nằm ở git tag/commit, không nằm trong tên file.
- **KHÔNG** thêm section vá kiểu `## v2.x — ...` ở cuối file rồi để đó. Phải sửa trực tiếp vào đúng vị trí nội dung liên quan trong file, và ghi lại quyết định đó thành 1 dòng D-xxx mới trong `docs/11_DECISION_LOG.md`.
