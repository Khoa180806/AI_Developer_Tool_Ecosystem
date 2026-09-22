# 02 --- Ecosystem Architecture v2.3

## Kiến trúc logic

``` text
Developer / AI Agent / CI
          |
    CLI / SDK / API / MCP
          |
   Specialized Tools
          |
   (chỉ khi đủ trigger)
    Shared Platform Core
          |
 Git / DB / Cloud / K8s / APIs
```

## Quan trọng: Platform Core không tồn tại ngay từ ngày đầu

Architecture diagram có thể mô tả platform core như **future layer**,
nhưng implementation không được dựng nó sớm.

### Trigger định lượng

  -----------------------------------------------------------------------
  Component                           Chỉ được dựng khi
  ----------------------------------- -----------------------------------
  Shared Config                       ≥2 tools cần đọc cùng một config
                                      schema

  Shared Telemetry                    ≥2 tools đã có production/beta
                                      usage và cần cùng format telemetry

  Shared Cache                        ≥2 tools cùng có cache requirement
                                      và duplication bắt đầu đáng kể

  Auth                                Tool thứ 2 cần multi-user/remote
                                      access; hoặc một tool đầu tiên đã
                                      có external team users

  Tool Registry                       ≥3 tools đã pass Definition of Done
                                      **và** có nhu cầu
                                      discovery/composition

  Shared Artifact Store               ≥2 tools cần persist cùng một
                                      artifact type hoặc artifact vượt
                                      local lifecycle

  Event Bus                           ≥3 tools cần asynchronous event
                                      consumption; synchronous API không
                                      còn phù hợp

  Plugin System                       ≥5 tools stable hoặc đã có external
                                      contributors/providers

  Central Platform Deployment         ≥3 stable tools + ≥2 shared
                                      platform capabilities
  -----------------------------------------------------------------------

Nếu chưa đạt trigger: \> tool tự quản lý dependency/config/storage của
mình.

## Nguyên tắc

Không xây infrastructure vì "sau này sẽ cần".

Xây khi: - có consumer thật; - có repeated need; - có measurable
duplication; - hoặc có reliability/security requirement rõ.

## Local-first

Giai đoạn đầu:

``` text
Developer machine
 ├── Tool
 ├── Index
 ├── Cache
 └── MCP
```

Không yêu cầu cloud.

Khi có remote mode: - auth; - encryption; - retention; - tenant
isolation; - audit phải được spec riêng trước implementation.

## Platform evolution

``` text
Tool 1
Tool 2
Tool 3
   ↓
Shared contract
   ↓
Shared telemetry/config
   ↓
Registry
   ↓
Auth / policy
   ↓
Event / plugin platform
```
