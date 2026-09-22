# AI Developer Tool Ecosystem — v2.3

## Purpose
A tool-first ecosystem for developer and AI-agent infrastructure. The goal is to make agents faster, cheaper, more accurate, more structured, and more reliable — not to build generic CRUD products that an agent can reproduce from one prompt.

## v2.3 principles
1. **Tool-first:** every capability must have an independent job.
2. **Canonical naming:** the Tool Registry is the single source of truth for names, IDs, status, and roadmap mapping.
3. **Contract before implementation:** downstream-facing schemas are defined before dependent tools are built.
4. **Benchmark before promotion:** a tool advances only when measurable evidence supports it.
5. **Do not clone mature primitives:** parsing, generic AST search, static analysis, and generic code search are dependencies/baselines, not differentiation by themselves.
6. **Compact-response-first:** agent-facing interfaces return summaries, IDs, counts, and bounded results before details.
7. **Local-first privacy:** source code stays local by default; remote/cloud modes require explicit security controls.
8. **Platform only after trigger:** shared infrastructure is extracted only when quantitative thresholds are met.

## Boundary test
Ask: **If every other tool disappeared, would this capability still have an independent job for a user or agent?** If not, it is probably a platform capability, an internal module, or an evolution stage — not a standalone tool.

## Source-of-truth hierarchy
1. `11_DECISION_LOG.md`
2. `03_TOOL_CATALOG.md` — canonical Tool Registry
3. `05_INTEGRATION_SPEC.md`
4. Tool-specific specifications
5. `06_ROADMAP.md`
6. Vision and architecture documents

## Reading order
`00 → 01 → 02 → 03 → 04 → 05 → 06 → 07 → 08 → 09 → 10 → 11`

## v2.3 corrections
This release restores operational detail removed during v2 cleanup: tool descriptions, CLI conventions, error codes, coding rules, target users, concrete schemas, benchmark thresholds, security policy, time-boxes, and competitor differentiation.



## Pre-Code Consistency Gate

Before coding a roadmap tool:
1. verify its canonical ID in the Tool Registry;
2. verify its roadmap mapping is unique or explicitly an evolution milestone;
3. pass the relevant competitor gate;
4. validate its schema against the common integration envelope;
5. define a reproducible benchmark baseline before claiming value.
