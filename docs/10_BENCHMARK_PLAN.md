# Benchmark Plan

## Objective
Prove that the ecosystem improves AI-agent work through lower token usage, lower latency, higher task success, or a useful combination.

## First benchmark task set
30 tasks from 3 Java open-source repositories:
- 10 symbol/dependency tasks
- 10 impact/refactor tasks
- 10 bug/debug-context tasks

Each task stores:
- repository
- commit SHA
- question/task instruction
- expected relevant files/symbols
- expected result
- difficulty
- timeout

## Baselines
### B0 — Agent without code intelligence
The agent uses the normal repository tools available to the baseline setup.

### B1 — Agent with existing provider
Use a suitable existing provider when its capability matches the task, for example an established code-intelligence/graph provider.

### B2 — Ecosystem prototype
Use our compact query + ImpactReport + ContextPack workflow.

Keep model, model version, task prompt, repository commit, and non-tested capabilities as constant as practical.

## Metrics
### Primary
- Task success rate
- Input tokens
- Total tokens
- Tool calls
- Wall-clock latency

### Secondary
- Context precision
- Irrelevant files retrieved
- Duplicate retrieval
- Relationship false positives
- Error rate
- Result size
- Cache hit rate where applicable

## Pass thresholds
A release passes if at least one primary condition is met:

**A. Token efficiency**
≥20% token reduction vs B0 with task-success drop ≤2 percentage points.

**B. Latency**
≥20% latency reduction with equivalent task success.

**C. Task success**
≥10 percentage-point task-success improvement with token cost ≤+20%.

A result that meets a threshold but creates a serious privacy, correctness, or reliability regression does not qualify as a pass.

## Measurement rules
- Fixed model/version per benchmark round.
- Fixed repository commit.
- Fixed task instructions.
- Warm-up runs separated from measured runs.
- If variance is high, run ≥5 repetitions/task.
- Report median and p95 for latency.
- Save raw metadata for reproducibility.

## First 1★ benchmark recommendation
`Token Diff` should be built first as measurement infrastructure, but it is not considered proof of ecosystem value by itself.

The first end-to-end proof should be:
`Codebase/Context task → baseline agent → compact tool result → Token Diff → task outcome`

## Go / no-go
GO if a threshold is met without unacceptable trade-offs.

NO-GO after 2 scope-limited iterations if thresholds are not met. Then change differentiation, use an adapter, narrow the task class, or archive the capability.



## Reproducibility Lock

### Fixed B1 baseline
**B1 = GitNexus at a pinned release/commit recorded in the benchmark manifest.**
Do not substitute another provider per task. If the pinned B1 provider does not expose
a capability required by a task, mark that B1 result **N/A** and retain the same task
for B0 and B2.

### Fixed repository manifest
Before the first measurement run, freeze three Java open-source repositories and exact
commit SHAs. Selection criteria: Java, reproducible build, meaningful symbols,
dependencies and tests, and combined coverage across approximately 10–500 KLOC.

| repo_id | repository | commit_sha | size_band | task_count |
|---|---|---|---|---:|
| R1 | **PIN BEFORE RUN** | **PIN SHA** | 10–100 KLOC | 10 |
| R2 | **PIN BEFORE RUN** | **PIN SHA** | 100–300 KLOC | 10 |
| R3 | **PIN BEFORE RUN** | **PIN SHA** | 300–500 KLOC | 10 |

The placeholders are a pre-run control, not benchmark evidence. The benchmark is not
reproducible until all three names and SHAs are frozen.

### No provider substitution
- B0: agent without code-intelligence capability.
- B1: agent + pinned GitNexus baseline.
- B2: agent + our implementation.

Unsupported B1 capabilities are N/A; never replace B1 with another provider for an
individual task.

### Required raw metadata
Every run records: `run_id`, `repo_id`, `commit_sha`, `task_id`, `difficulty`, `model`,
`model_version`, `temperature/config`, `baseline`, `success`, `input_tokens`,
`output_tokens`, `total_tokens`, `tool_calls`, `wall_clock_ms`, `timestamp`, and
error information.
