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
