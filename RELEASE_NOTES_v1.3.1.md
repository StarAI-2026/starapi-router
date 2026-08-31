# StarAPI Router v1.3.1

## 修复与改进

### MTP 加速开关修复（llama.cpp 0.3.0+）

此前开启套餐的「MTP 加速」不会真正启用推测解码：llama.cpp 0.3.0 起 `--spec-type` 默认值为 `none`，而旧版只注入了从属参数。本版开启后自动注入 `--spec-type draft-mtp`，并按实测调整默认值（`--spec-draft-n-max 3`、`--draft-p-min 0.5`；旧默认组合实测反而更慢）。面板文案同步改为如实说明：单窗口聊天场景通常不提速，请按需开启。

### KV 量化支持 K / V 分开设置

编辑套餐的「KV 量化」新增「K 精度（-ctk）」与「V 精度（-ctv）」两个独立下拉（F16 / BF16 / Q8_0 / Q5_0 / Q4_0 / IQ4_NL / F32），可组合出长上下文最优配置（例如 K=Q4_0 + V=Q8_0：读得准、记得稳、显存省）。原快捷预设保留为一键组合；自定义参数框与下拉双向同步；修复混合 K/V 在编辑「高级额外参数」时被悄悄重置为单一档位的问题。

### 下载说明

- Windows 常见电脑请下载 `StarAPI_1.3.1_windows_amd64.zip`（解压后运行 starapi-router.exe）。
- ARM 架构设备（如骁龙笔记本）请下载 `StarAPI_1.3.1_windows_aarch64.zip`。
- macOS Intel 机型选 `darwin_amd64`，Apple Silicon 选 `darwin_aarch64`。
- Linux 按架构选 `amd64` / `aarch64`；OpenWrt 等 musl 系统选 `no-plugin` 版本。
- 完整性校验请使用 `checksums.txt`（SHA-256）。

> Public source archive contains only public docs.
