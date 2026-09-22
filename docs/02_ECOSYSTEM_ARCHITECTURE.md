# Ecosystem Architecture

```text
Developer / AI Agent / CI
          ↓
   CLI / SDK / API / MCP
          ↓
   Specialized Tools
          ↓
 Shared Platform Core
   (only after trigger)
          ↓
Git / DB / Cloud / K8s / External APIs
```

## Architecture rules
- A tool owns its local config, storage, dependencies, and lifecycle until shared usage is proven.
- Shared infrastructure is extracted only when duplication or coordination becomes measurable.
- Local-first is the default architecture for source-code tools.
- Remote mode is a separate security boundary, not merely a deployment flag.

## Quantitative platform triggers
| Capability | Trigger |
|---|---|
| Shared Config | ≥2 tools require the same configuration schema |
| Shared Telemetry | ≥2 production/beta tools need the same telemetry format |
| Shared Cache | ≥2 tools have materially duplicated caching requirements |
| Auth | Tool #2 needs multi-user/remote access, or Tool #1 already has external team users |
| Tool Registry | ≥3 stable tools need discovery/composition |
| Shared Artifact Store | ≥2 tools persist the same artifact type or local lifecycle becomes insufficient |
| Event Bus | ≥3 tools require asynchronous event consumption |
| Plugin System | ≥5 stable tools or external provider/contributor demand |
| Central Platform Deployment | ≥3 stable tools + ≥2 shared platform capabilities |

If a trigger is not met, do not create the platform abstraction merely for architectural elegance.

## Platform extraction sequence
`Standalone tools → Stable contracts → Shared duplication observed → Shared module → Registry/auth/telemetry → Platform`
