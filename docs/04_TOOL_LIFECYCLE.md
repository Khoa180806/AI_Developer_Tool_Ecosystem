# Tool Lifecycle

## Lifecycle
`Idea → Competitive check → Contract → Prototype → Benchmark → Stable → Composition → Evolution/Archive`

## Mandatory gate before coding
For every proposed tool:
1. Identify at least 3 related existing tools/products.
2. Document overlap and commodity capabilities.
3. State the measurable differentiation hypothesis.
4. Define a benchmark or validation task set.
5. If no meaningful differentiation can be measured, change scope or NO-GO.

## Time-box by maturity
| Level | Time-box | Expected evidence |
|---|---:|---|
| 1★ | 1–2 weeks | standalone prototype + benchmark harness |
| 2★ | 2–4 weeks | usable standalone tool + real validation |
| 3★ | 3–6 weeks | stable agent-facing contract + measurable workflow gain |
| 4★ | 1–2 months | deep capability + composition with another stable tool |
| 5★ | 2–4 months/module | production-grade infrastructure + security/scale evidence |
| 6★ | only after foundations | ecosystem/platform evidence; no automatic deadline |

If implementation exceeds the time-box by >50% without benchmark progress, reduce scope, change implementation, or archive.

## Stable criteria
A tool is Stable only when it has:
- independent standalone use
- canonical name and ID
- versioned input/output schema
- tests
- benchmark results
- documented failure modes
- security/privacy notes
- at least one real user validation OR a benchmark task set meeting the required threshold

## Promotion rule
A tool does not advance because it “feels useful.” It advances because evidence shows useful behavior under a defined workload.

## Platform rule
Do not create Registry/Auth/Event Bus/Plugin/Central Platform abstractions until the quantitative triggers in `02_ECOSYSTEM_ARCHITECTURE.md` are met.



## Planning Capacity Baseline

All roadmap time-boxes assume **1 solo builder at approximately 10 hours/week**.

| Level | Calendar time-box | Baseline effort |
|---|---:|---:|
| 1★ | 1–2 weeks | ~10–20 hours |
| 2★ | 2–4 weeks | ~20–40 hours |
| 3★ | 3–6 weeks | ~30–60 hours |
| 4★ | 1–2 months | ~40–80 hours |
| 5★ | 2–4 months | ~80–160 hours |

These are planning ceilings, not promises. Different team capacity should be converted
to builder-hours rather than interpreted as equivalent calendar effort.
