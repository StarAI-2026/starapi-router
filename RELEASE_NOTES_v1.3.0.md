# StarAPI Router v1.3.0

## [1.3.0] - 2026-08-31

### Fixed
- **Antigravity 推理回放空指针崩溃**：internal/runtime/executor/antigravity_reasoning_replay.go:observeResponsePayload 未对 *antigravityReasoningReplayAccumulator 判空，TestAntigravityReasoningReplaySeparatesClaudeSessionTitleFromResumedTranscript 等用例在 scope 无效时直接 panic。现已增加 if a == nil { return } 保护，全量 go test ./internal/runtime/executor 通过。

### Changed
- **品牌与文档统一（配置/Docker/模块名）**：`go.mod` 从 `内部模块路径整理` 迁至 `内部模块`，全仓 import 与示例/文档同步；`config.example.yaml` 默认 `auth-dir: auths`、`panel-github-repository: ""`、`disable-auto-update-panel: true`；`ResolveAuthDir` 对 `auths` 空目录自动回退 `~/.cli-proxy-api`，`~/.starapi-router` 证书目录同样回退，现有登录不丢；`DefaultPanelGitHubRepository=""`、`DefaultDisableAutoUpdatePanel=true`，空仓库不再回落上游 `内部面板源`/`内部面板源`，UA 改为 `StarAPI-management-updater`；Docker/Compose 镜像改 `starapi-router`、工作目录 `/starapi-router`、示例端口 1991；`FUNDING.yml`/`AGENTS.md`/SDK 文档示例 GitHub 链接同步；插件 ABI `cliproxy_plugin_init`、OAuth client_id、缓存键 `cli-proxy-api:` 与 `LICENSE` 原版权保持不变。



### Notes
- 本版为去品牌化收尾与回归修复，私有仓验证通过后可打 1.3.0 标签；公开仓仅发布最小公开包。

## [1.2.9]

> Public source archive contains only public docs.
