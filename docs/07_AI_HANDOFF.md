# AI Handoff / Coding Rules

## Before coding
The implementing AI MUST read:
1. `00_README.md`
2. `03_TOOL_CATALOG.md`
3. `04_TOOL_LIFECYCLE.md`
4. relevant tool specification
5. `11_DECISION_LOG.md`

Then it MUST check:
- canonical tool name
- existing competitors
- platform trigger status
- existing schemas/contracts
- benchmark requirements

## Coding rules
1. Do not invent a new canonical tool name without updating the Tool Registry.
2. Do not rename an existing canonical tool casually.
3. Do not create a platform abstraction before its trigger is met.
4. Do not replace a real schema with `{}` or `[]` when downstream code depends on it.
5. Prefer a vertical slice over broad unfinished architecture.
6. Do not add dependencies without a concrete reason.
7. Keep secrets and credentials out of logs, fixtures, examples, and tool results.
8. Preserve local-first source-code privacy.
9. Record assumptions when requirements are uncertain.
10. Update the decision log when a design choice changes architecture, naming, scope, or benchmark methodology.
11. Keep outputs compact and machine-readable where an agent consumes them.
12. Do not claim differentiation without benchmark evidence.

## Codebase Graph rule
Do not assume that building a graph engine is itself the competitive advantage. Existing parser, AST, static-analysis, code-search, and graph capabilities are baselines. Focus the implementation on agent-facing queries, compact responses, context composition, measurable token/time savings, and provider adapters.

## Definition of done
A feature is not done when code compiles. It is done when:
- contract exists
- tests exist
- failure modes are documented
- benchmark/validation exists where applicable
- security/privacy behavior is explicit
- docs and Tool Registry are consistent


### Documentation maintenance rule
Do not append a corrective patch section when changing an authoritative operational
document. Merge the change into the existing canonical section and record the historical
decision in `11_DECISION_LOG.md`.
