# Integration Specification

## Supported interfaces
Every stable tool should expose the smallest useful interface first:
- CLI
- SDK/library
- HTTP API when remote use is justified
- MCP adapter for agent-facing capabilities

## CLI conventions
Every CLI SHOULD support:
```text
--help       Show usage
--version    Show version
--json       Emit machine-readable output
```

Rules:
- Human-readable output → stdout.
- Machine-readable result → stdout when `--json` is used.
- Diagnostics/errors → stderr.
- Non-zero exit code on operational failure.
- Deterministic exit codes should be documented.
- CLI output must remain bounded by default.

Recommended exit codes:
```text
0  success
1  general failure
2  invalid usage/input
3  not found
4  permission denied
5  dependency unavailable
6  timeout
7  rate limited
```

## Compact-response-first
Agent-facing calls MUST prefer:
`summary → IDs → counts/metrics → references/handles → details on demand`

Every MCP-facing query SHOULD support:
- summary mode
- bounded output
- pagination/cursor
- explicit detail expansion
- truncation metadata

## API envelope
```json
{
  "data": {},
  "metadata": {
    "schema_version": "1.0",
    "source": "codebase-graph",
    "duration_ms": 12,
    "truncated": false,
    "next_cursor": null
  }
}
```

## Error model
```text
INVALID_INPUT
NOT_FOUND
PERMISSION_DENIED
TIMEOUT
RATE_LIMITED
DEPENDENCY_UNAVAILABLE
INTERNAL_ERROR
UNSUPPORTED_OPERATION
SCHEMA_VERSION_UNSUPPORTED
```

Example:
```json
{
  "error": {
    "code": "INVALID_INPUT",
    "message": "symbol_id is required",
    "details": {
      "field": "symbol_id"
    }
  },
  "metadata": {
    "schema_version": "1.0"
  }
}
```

## Versioning
- Schemas use explicit `schema_version`.
- Breaking changes require a major version.
- Additive fields should remain backward compatible where practical.
- Tool IDs and canonical names must not be casually renamed.

## Security
- Never return secrets by default.
- Never place credentials in tool results.
- Respect repository access boundaries.
- Validate paths and external inputs.
- Remote mode requires authentication, authorization, encryption, retention/deletion policy, tenant isolation, and auditability.
