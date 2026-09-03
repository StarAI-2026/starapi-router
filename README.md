# StarAPI Router

本地优先的统一 AI API 网关：把商业大模型、OAuth 订阅账号和本地开源模型集中到你自己的电脑上，用一把本地统一 Key 驱动 Claude Code、Codex、Cursor、Windsurf、OpenCode 等客户端。

本仓库只用于公开分发、版本说明和下载。产品源码不在此仓库。

## 它解决什么问题

- 多个客户端各自保存上游 Key，容易泄露、难同步。
- 上游 429 / 欠费 / 断网会直接打断编码。
- 第三方中转可能降智或调包，难以及时发现。
- 换电脑后要重新配套餐、模型和客户端。

StarAPI Router 把路由、密钥、降级链、客户端接管和用量统计收口到本机面板。客户端只访问本地接口，真实凭据不出电脑。

## 核心能力

### 客户端管理中心

覆盖 Codex、Claude Code、Gemini CLI、Cursor、Windsurf、OpenCode、Hermes、PI、OpenClaw、DeepSeek Harness 等客户端。可识别本机安装情况，一键启动/重启，并把模型与路由配置同步进目标客户端。

同时支持：

- Sub-Agent 子代理：独立设置思考强度和上下文
- 视觉自动路由：纯文本主模型遇到图片时转给视觉模型
- Ollama / llama.cpp 本地引擎纳管
- Skill 与 MCP 统一仓库：扫描本机技能和工具，一键分发到工作区

### 套餐、通道与降级链

- 统一本地接口：`http://127.0.0.1:1991/v1` + 可刷新的本地 API Key
- 三种套餐：自定义 HTTP、OAuth 厂商直连、本地开源模型
- 同一地址可挂多把密钥，分别设置代理、协议、RPM/TPM
- 降级链：主通道 429 或异常时，无感切到备用模型，任务不中断
- 通道大盘：查看正常、冷却、熔断状态，并可探测降级链路

### OAuth、认证文件与配额

- 主流厂商一键授权，获取当前订阅可用模型
- 认证文件可单独配代理
- 查看套餐重置时间和分时段用量

### 用量、成本和体检

- Token、请求次数、缓存命中率和预估成本
- 最近调用流水、供应商成功率和平均延迟
- 可自定义每个模型单价
- 内置题库做模型体检，辅助判断降智或调包

### 版本授权

免费版适合个人基础使用；专业版和旗舰版提供更多账号、设备席位、降级链和体检次数。购买入口见下方渠道。

## 下载与启动

推荐绿色便携版：解压后双击 `StarAPI Router.exe` 即可，无需安装程序。

1. 夸克网盘（国内高速）：<https://pan.quark.cn/s/94d378032710>
2. GitHub 最新发布页：<https://github.com/StarAI-2026/starapi-router/releases/latest>
3. 购买授权：<https://catfk.com/shop/starapi>

Windows 首次运行若出现“Windows 已保护你的电脑”：点「更多信息」→「仍要运行」。这是未购买商业代码签名证书时的 SmartScreen 提示，不是安装失败。

当前公开 Windows 包是绿色便携版。macOS / Linux / ARM 需要对应架构的便携包，不能直接使用 Windows zip。

## 首次使用

1. 解压绿色包，运行 `StarAPI Router.exe`
2. 用 GitHub Device Flow 登录（浏览器输入设备码即可）
3. 在面板中添加套餐 / OAuth / 本地模型
4. 生成统一 API Key
5. 在客户端填写：

```text
Base URL: http://127.0.0.1:1991/v1
API Key:  面板生成的统一 Key
Model:    面板中已启用的模型
```

管理面板：`http://127.0.0.1:1990` 或 `http://127.0.0.1:1991/panel/`

## 安全

不要公开本机 `config.yaml`、`.env`、`auths/`、认证文件、数据库、日志或授权材料。只从本仓库 Release 或官方网盘下载，并核对发布页校验和。

## 反馈

使用问题请开 Issue，写明系统、复现步骤和期望结果。不要在 Issue 或截图中提交 Key、认证文件或完整配置。

本仓库不接收功能代码 Pull Request。核心功能在私有开发仓库完成后再通过公开 Release 分发。
