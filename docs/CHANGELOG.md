# Changelog

## [2.3] - unknown

### Purpose

v2.3 is a documentation-consistency release. It converts the v2.2 corrective patches
into integrated current-state specifications so the operational files remain authoritative
without requiring readers or agents to mentally apply patch sections.

### Changes

- Integrated the Semantic Cache roadmap mapping directly into the canonical Tool Registry:
  `1★ (MVP) → 3★ (evolution)`.
- Removed the standalone v2.2 patch section from the roadmap.
- Integrated the ImpactReport/common-envelope rule into the Codebase Graph specification.
- Fixed the Java symbol-ID delimiter inconsistency.
- Expanded the 1★ competitor matrix so Token Diff, Context Pack, Tool Result Compressor,
  and Semantic Cache each have at least three relevant alternatives.
- Integrated the reproducibility lock into the benchmark plan.
- Integrated the solo-builder capacity assumption into the lifecycle plan.
- Updated `INDEX.md` to v2.3 and added this changelog.
- Added D-020 through D-022 to the decision history.
- Added an AI handoff rule forbidding append-only corrective patches to operational specs.

### Current hard gates

1. Canonical naming comes from the Tool Registry.
2. Roadmap evolution milestones do not create duplicate tool IDs.
3. Every 1★ tool passes a per-tool ≥3-competitor gate.
4. Schemas must agree with the common transport envelope.
5. Benchmark baselines and repository SHAs must be frozen before evidence is claimed.
6. Operational documentation is merged in place; decision history is append-only.

### Final documentation baseline

This release is the documentation baseline for starting the 1★ implementation track. No documentation gate remains open under the current rules.

## [2.4] - 2026-09-25

### Purpose

v2.4 marks the completion, release, and stabilization of T01 (Token Diff) as the first 1★ Stable tool in the AI Developer Tool Ecosystem.

### Changes

- **T01 (Token Diff) Stable Release (v0.1.1):**
  - Implemented standalone CLI and TypeScript SDK conforming strictly to canonical naming (T01) and the common transport envelope v1.0.
  - Published on npm as package `ai-token-diff` (v0.1.1) with binary aliases `td`, `token-diff`, and `ai-token-diff`.
  - Built with pure JavaScript BPE tokenization via `js-tiktoken` and an in-memory vocabulary cache, achieving <15ms execution latency and <40MB RAM without native C++/WASM build dependencies.
  - Integrated Smart Input fallback: automatically distinguishes between disk file paths and inline prompt text strings, emitting a non-blocking warning to stderr.
  - Formatted terminal output with `picocolors` ANSI tinting and aligned tabular views.
  - Implemented a complete deterministic error model with standard exit codes (0, 1, 2, 3, 4).
  - Configured automated CI/CD pipeline on GitHub Actions across Ubuntu & Windows (Node.js 18, 20, 22) with 20/20 Vitest unit/integration tests passing.
  - Completed documentation and visual assets (pipeline architecture, unclipped terminal screenshots, animated GIF demo, comprehensive FAQ) in both English and Vietnamese.
- **Ecosystem Registry & Lifecycle Updates:**
  - Promoted T01 status from `Scheduled` to `Stable` (1★) in `docs/03_TOOL_CATALOG.md` and `docs/ai_developer_tool_ecosystem_vi/03_TOOL_CATALOG.md`.
  - Updated 1★ Roadmap (`docs/06_ROADMAP.md` and `docs/ai_developer_tool_ecosystem_vi/06_ROADMAP.md`) marking Token Diff as Stable v0.1.1.
  - Updated `tools/T01-token-diff/AGENTS.md` with implementation details, npm distribution, and CLI binaries.
  - Synchronized Decision D-023 into Vietnamese Decision Log (`docs/ai_developer_tool_ecosystem_vi/11_DECISION_LOG.md`).

