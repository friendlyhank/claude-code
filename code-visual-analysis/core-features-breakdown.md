# Claude Code 核心功能知识地图

> 本文档作为 Claude Code 项目的功能索引与导航，基于代码事实构建，提供系统化的知识入口。

---

## 1. 工具系统 (Tool System)
> **代码入口**: `src/tools.ts` · **工具数量**: 55+ 内置工具 + MCP 动态扩展
> **核心抽象**: `src/Tool.ts` — 统一的 Tool 接口定义

Claude Code 拥有一个高度可扩展的工具系统，所有工具遵循统一的接口规范，支持 MCP 协议动态扩展。

### 1.1 工具架构与编排
- **文档**: [[01-tool-system-architecture]]
- 工具注册与发现机制 (`src/tools.ts:getAllBaseTools`)
- 工具权限过滤与黑白名单 (`filterToolsByDenyRules`)
- MCP 工具集成与合并 (`assembleToolPool`)
- 工具搜索延迟加载策略 (`ToolSearchTool`)

### 1.2 文件操作工具集
- **文档**: [[02-file-tools]]
- `FileReadTool` — 文件读取，支持图片/PDF、行范围、编码检测
- `FileEditTool` — 精确字符串替换编辑
- `FileWriteTool` — 文件写入与覆盖
- `GlobTool` — 文件模式匹配搜索
- `GrepTool` — 正则内容搜索（内置 ripgrep）
- `NotebookEditTool` — Jupyter Notebook 编辑

### 1.3 Shell 执行工具集
- **文档**: [[03-shell-tools]]
- `BashTool` — Bash 命令执行，沙箱隔离、权限控制、超时管理
- `PowerShellTool` — Windows PowerShell 支持
- Shell 安全策略：危险命令检测、操作符权限、路径验证

### 1.4 代理与任务工具集
- **文档**: [[04-agent-tools]]
- `AgentTool` — 子代理启动与管理
- `TaskCreateTool/TaskGetTool/TaskUpdateTool/TaskListTool` — 任务管理 (Todo V2)
- `TaskStopTool` — 任务终止控制
- `TaskOutputTool` — 任务输出收集
- `TodoWriteTool` — 待办事项追踪

### 1.5 Web 与网络工具集
- **文档**: [[05-web-tools]]
- `WebFetchTool` — 网页内容获取（支持 Defuddle 清理）
- `WebSearchTool` — Web 搜索集成
- `WebBrowserTool` — 浏览器自动化（实验性）

### 1.6 LSP 与代码智能工具集
- **文档**: [[06-lsp-tools]]
- `LSPTool` — 语言服务器协议集成，支持跳转定义、查找引用、补全
- 代码诊断与修复建议

### 1.7 扩展与集成工具集
- **文档**: [[07-extension-tools]]
- `SkillTool` — 技能加载与执行
- `MCPTool` — Model Context Protocol 服务器通信
- `ListMcpResourcesTool/ReadMcpResourceTool` — MCP 资源访问
- `ConfigTool` — 配置管理（Ant-only）
- `WorkflowTool` — 工作流脚本执行

### 1.8 辅助工具集
- **文档**: [[08-utility-tools]]
- `AskUserQuestionTool` — 交互式用户提问
- `BriefTool` — 上下文摘要
- `SendMessageTool` — 消息发送（多代理通信）
- `EnterPlanModeTool/ExitPlanModeV2Tool` — 计划模式切换
- `EnterWorktreeTool/ExitWorktreeTool` — Git Worktree 管理
- `ScheduleCronTool` — 定时任务调度

---

## 2. 对话引擎与会话管理 (Conversation Engine)
> **代码入口**: `src/query.ts` · `src/QueryEngine.ts`
> **核心流程**: 用户输入 → 消息处理 → API 调用 → 响应流式输出

### 2.1 消息处理流程
- **文档**: [[09-message-processing]]
- 用户消息解析与附件处理
- 上下文窗口管理与 Token 预算
- 系统提示词组装与缓存策略
- 流式响应处理与中断控制

### 2.2 会话状态管理
- **文档**: [[10-session-state]]
- 会话持久化与恢复 (`src/utils/conversationRecovery.ts`)
- 历史记录管理 (`src/history.ts`)
- 多轮对话上下文追踪
- 会话标题自动生成

### 2.3 上下文窗口优化
- **文档**: [[11-context-window]]
- Token 预算计算 (`src/query/tokenBudget.ts`)
- 上下文压缩策略
- 文件状态缓存 (`src/utils/fileStateCache.ts`)
- 提示词缓存优化

---

## 3. 模型管理与 API 集成 (Model & API)
> **代码入口**: `src/utils/model/` · `src/services/api/`
> **支持模型**: Claude 系列、OpenAI 兼容、Bedrock、Vertex AI

### 3.1 模型配置与选择
- **文档**: [[features/12-model-management]] ✓ 已完成
- 模型别名与解析 (`src/utils/model/model.ts:62-99` - 选择优先级, `446-507` - 别名解析)
- 模型能力检测（扩展思考、视觉等）
- 模型成本追踪 (`src/cost-tracker.ts`)
- 多提供商适配 (`src/utils/model/providers.ts:7-22` - 提供商检测)

### 3.2 API 认证与授权
- **文档**: [[features/13-authentication]] ✓ 已完成
- API Key 管理 (`src/utils/auth.ts:152-205` - 认证源检测)
- OAuth 流程 (`src/utils/auth.ts:1254-1299` - 令牌读取, `src/services/oauth/client.ts` - OAuth流程)
- AWS/GCP 凭证管理 (`src/utils/auth.ts:604-1013` - AWS/GCP凭证刷新)
- 自定义平台登录

### 3.3 流式响应处理
- **文档**: [[features/14-streaming]] ✓ 已完成
- SSE 流解析 (`src/services/api/claude.ts:165-352` - 事件处理)
- 工具调用流式处理
- 错误重试与熔断 (`src/services/api/withRetry.ts:85-267` - 重试机制, `src/services/api/errors.ts:784-883` - 错误处理)
- 速率限制处理

---

## 4. 权限与安全系统 (Security & Permissions)
> **代码入口**: `src/utils/permissions/` · `src/tools/BashTool/bashSecurity.ts`
> **安全策略**: 沙箱隔离、权限规则、危险操作检测

### 4.1 权限模型
- **文档**: [[15-permissions]]
- 权限规则定义与匹配
- 用户确认机制
- 权限持久化与继承
- MCP 工具权限隔离

### 4.2 沙箱隔离
- **文档**: [[16-sandbox]]
- 命令沙箱执行 (`src/utils/sandbox/`)
- 文件系统访问控制
- 网络访问限制
- 进程隔离

### 4.3 安全检测
- **文档**: [[17-security-checks]]
- 危险命令识别
- 敏感数据扫描 (`src/services/teamMemorySync/secretScanner.ts`)
- SSRF 防护 (`src/utils/hooks/ssrfGuard.ts`)
- 自动模式安全控制

---

## 5. 插件与扩展系统 (Plugin System)
> **代码入口**: `src/utils/plugins/` · `src/skills/`
> **扩展机制**: Marketplace、MCP、Skill、Hook

### 5.1 插件架构
- **文档**: [[18-plugin-architecture]]
- 插件生命周期管理 (`src/utils/plugins/pluginLoader.ts`)
- Marketplace 集成 (`src/utils/plugins/marketplaceManager.ts`)
- 插件依赖解析
- 插件热加载

### 5.2 Skill 技能系统
- **文档**: [[19-skill-system]]
- Skill 定义与加载 (`src/skills/loadSkillsDir.ts`)
- 内置技能 (`src/skills/bundled/`)
- 技能提示词模板
- 技能钩子机制

### 5.3 Hook 钩子系统
- **文档**: [[20-hook-system]]
- Hook 类型与注册 (`src/utils/hooks.ts`)
- 异步 Hook 执行 (`src/utils/hooks/AsyncHookRegistry.ts`)
- HTTP/Agent/Prompt Hook
- 前置/后置处理

### 5.4 MCP 集成
- **文档**: [[21-mcp-integration]]
- MCP 服务器管理 (`src/services/mcp/`)
- 资源与工具映射
- 传输协议适配
- 服务生命周期

---

## 6. 多代理协作 (Multi-Agent)
> **代码入口**: `src/utils/swarm/` · `src/coordinator/`
> **协作模式**: Team、Coordinator-Worker、In-Process

### 6.1 代理类型与角色
- **文档**: [[22-agent-types]]
- 主代理与子代理
- Teammate 协作代理
- Coordinator 协调代理
- Worker 工作代理

### 6.2 代理通信
- **文档**: [[23-agent-communication]]
- Mailbox 消息传递 (`src/utils/teammateMailbox.ts`)
- 权限同步 (`src/utils/swarm/permissionSync.ts`)
- 状态共享
- 任务分发

### 6.3 后端实现
- **文档**: [[24-agent-backends]]
- InProcessBackend (`src/utils/swarm/backends/InProcessBackend.ts`)
- TmuxBackend (`src/utils/swarm/backends/TmuxBackend.ts`)
- ITermBackend (`src/utils/swarm/backends/ITermBackend.ts`)
- 后端自动检测与选择

---

## 7. UI 与终端交互 (UI & Terminal)
> **代码入口**: `src/ink/` · `src/main.tsx`
> **UI 框架**: Ink (React for CLI)

### 7.1 终端渲染引擎
- **文档**: [[25-terminal-rendering]]
- Ink 框架集成 (`src/ink/`)
- ANSI 转义序列处理
- 光标与选择管理
- 双向文本支持 (BiDi)

### 7.2 交互组件
- **文档**: [[26-interactive-components]]
- 输入框与编辑器
- 列表与选择器
- 确认对话框
- 进度指示器

### 7.3 Vim 模式
- **文档**: [[27-vim-mode]]
- Vim 键位模拟 (`src/vim/`)
- 模式切换（Normal/Insert/Visual）
- 文本对象与操作符
- Motion 与跳转

---

## 8. 配置与设置 (Configuration)
> **代码入口**: `src/utils/settings/` · `src/utils/config.ts`
> **配置层级**: 全局 → 项目 → 会话

### 8.1 设置管理
- **文档**: [[28-settings]]
- 设置源与优先级 (`src/utils/settings/settings.ts`)
- 迁移机制 (`src/migrations/`)
- MDM 配置覆盖
- 验证与类型安全

### 8.2 环境与特性开关
- **文档**: [[29-feature-flags]]
- 环境变量解析 (`src/utils/envUtils.ts`)
- Feature Flag 系统 (`feature()` 函数)
- GrowthBook 集成 (`src/services/analytics/growthbook.ts`)
- 动态特性开关

### 8.3 项目配置
- **文档**: [[30-project-config]]
- CLAUDE.md 文件解析 (`src/utils/claudemd.ts`)
- AGENTS.md 项目指令
- .claude/ 目录结构
- Worktree 配置隔离

---

## 9. 记忆与上下文增强 (Memory & Context)
> **代码入口**: `src/services/SessionMemory/` · `src/services/autoDream/`
> **记忆类型**: Session Memory、Auto Dream、Team Memory

### 9.1 会话记忆
- **文档**: [[31-session-memory]]
- 记忆提取与存储 (`src/services/SessionMemory/`)
- 记忆提示词生成
- 记忆检索与注入

### 9.2 自动整理 (Auto Dream)
- **文档**: [[32-auto-dream]]
- 后台整理机制 (`src/services/autoDream/`)
- 整理提示词 (`consolidationPrompt.ts`)
- 锁机制防止冲突
- 定期触发策略

### 9.3 团队记忆
- **文档**: [[33-team-memory]]
- 跨代理记忆同步 (`src/services/teamMemorySync/`)
- 秘密扫描与脱敏
- 文件监视与更新

---

## 10. 监控与分析 (Monitoring & Analytics)
> **代码入口**: `src/services/analytics/` · `src/utils/log.ts`
> **监控平台**: Datadog、GrowthBook、Sentry

### 10.1 事件追踪
- **文档**: [[34-analytics]]
- 事件埋点 (`src/services/analytics/`)
- First-party 事件日志
- Datadog 集成
- 遥测数据上报

### 10.2 错误监控
- **文档**: [[35-error-monitoring]]
- Sentry 集成
- 错误分类与上报
- 调试日志系统 (`src/utils/debug.ts`)
- 崩溃恢复

### 10.3 性能监控
- **文档**: [[36-performance]]
- 慢操作追踪 (`src/utils/slowOperations.ts`)
- Token 使用统计
- 成本追踪 (`src/cost-tracker.ts`)
- 响应时间监控

---

## 11. 开发者工具 (Developer Tools)
> **代码入口**: `src/entrypoints/` · `packages/`
> **SDK**: Agent SDK、REPL 模式

### 11.1 Agent SDK
- **文档**: [[37-agent-sdk]]
- SDK 类型定义 (`src/entrypoints/agentSdkTypes.ts`)
- 运行时 API
- 嵌入式使用
- 程序化控制

### 11.2 REPL 模式
- **文档**: [[38-repl-mode]]
- REPL 工具 (`src/tools/REPLTool/`)
- VM 沙箱执行
- 交互式调试
- 脚本化操作

### 11.3 远程控制
- **文档**: [[39-remote-control]]
- WebSocket 会话管理 (`src/remote/`)
- SDK 消息适配
- 远程权限桥接
- 跨进程通信

---

## 12. 高级特性 (Advanced Features)
> **代码入口**: 各 Feature Flag 控制的模块

### 12.1 Computer Use
- **文档**: [[40-computer-use]]
- 屏幕截图与分析
- 鼠标键盘控制
- UI 自动化 (`packages/@ant/computer-use-swift/`)

### 12.2 Chrome 集成
- **文档**: [[41-chrome-integration]]
- Native Host 通信
- 浏览器扩展协议
- Chrome Use 工具

### 12.3 Voice Mode
- **文档**: [[42-voice-mode]]
- 语音识别 (`src/services/voice.ts`)
- 语音合成
- 关键词检测 (`src/services/voiceKeyterms.ts`)
- 实时转录

### 12.4 Bridge Mode
- **文档**: [[43-bridge-mode]]
- IDE 集成模式
- 文件变更监听
- 诊断追踪 (`src/services/diagnosticTracking.ts`)

---

## 13. 全局状态管理 (Global State Management)
> **代码入口**: `src/bootstrap/state.ts`
> **设计原则**: 单例模式、最小化状态、原子性更新

### 13.1 会话状态管理
- **文档**: [[features/44-global-state-management]]
- 会话 ID 生成与切换 (`src/bootstrap/state.ts:435-479`)
- 会话链追踪 (parentSessionId)
- 会话项目目录管理 (sessionProjectDir)
- 会话恢复机制 (`setCostStateForRestore`)

### 13.2 成本与性能追踪
- 成本统计 (totalCostUSD, modelUsage)
- Token 统计 (inputTokens, outputTokens, cacheReadTokens)
- Turn 级预算管理 (`snapshotOutputTokensForTurn`)
- API 持续时间追踪 (totalAPIDuration)

### 13.3 特性开关与模式状态
- Kairos 激活状态 (kairosActive)
- 严格工具结果配对 (strictToolResultPairing)
- 自动模式/快速模式状态
- Beta Header 锁存机制 (afkModeHeaderLatched 等)

### 13.4 缓存状态管理
- 提示词缓存 1h TTL (promptCache1hAllowlist)
- CLAUDE.md 内容缓存 (cachedClaudeMdContent)
- 系统提示词片段缓存 (systemPromptSectionCache)
- 会话稳定性设计（首次评估后锁定）

### 13.5 OpenTelemetry 集成
- Meter Provider 管理
- 指标计数器 (sessionCounter, locCounter, costCounter 等)
- Logger Provider 管理
- Tracer Provider 管理

---

## 14. Cron 定时任务系统 (Scheduled Tasks)
> **代码入口**: `src/utils/cronTasks.ts`
> **持久化**: `.claude/scheduled_tasks.json`

### 14.1 Cron 表达式解析
- 标准 5 字段语法支持
- Cron 表达式验证 (`src/utils/cronTasks.ts:302-314`)
- 下次执行时间计算 (`nextCronRunMs`)
- 错过任务检测 (`findMissedTasks`)

### 14.2 任务调度与执行
- 持久化任务管理 (`getCronFilePath`)
- 会话级临时任务 (sessionCronTasks)
- 任务锁机制 (`src/utils/cronTasksLock.ts`)
- 任务 ID 生成与管理

### 14.3 抖动策略 (Jitter)
- Thundering Herd 避免 (`DEFAULT_CRON_JITTER_CONFIG`)
- 抖动配置 (`CronJitterConfig`)
- 单次抖动计算 (`oneShotJitteredNextCronRunMs`)
- 周期性抖动 (`jitteredNextCronRunMs`)

---

## 15. 迁移系统 (Migration System)
> **代码入口**: `src/migrations/`
> **触发时机**: 版本升级自动执行

### 15.1 模型迁移
- Sonnet 1m → Sonnet 4.5 (`migrateSonnet1mToSonnet45.ts`)
- Sonnet 4.5 → Sonnet 4.6 (`migrateSonnet45ToSonnet46.ts`)
- Fennec → Opus (`migrateFennecToOpus.ts`)
- Opus 版本迁移 (`migrateOpusToOpus1m.ts`)

### 15.2 设置迁移
- 自动更新设置迁移 (`migrateAutoUpdatesToSettings.ts`)
- 权限绕过接受迁移 (`migrateBypassPermissionsAcceptedToSettings.ts`)
- REPL Bridge 启用迁移 (`migrateReplBridgeEnabledToRemoteControlAtStartup.ts`)
- MCP 服务器启用迁移 (`migrateEnableAllProjectMcpServersToSettings.ts`)

### 15.3 迁移架构
- 迁移脚本组织
- 版本检测机制
- 迁移执行顺序
- 回滚策略

---

## 16. 提示词工程系统 (Prompt Engineering)
> **代码入口**: `src/utils/messages/systemInit.ts`, `src/services/compact/prompt.ts`
> **缓存策略**: Prompt Cache, 片段缓存

### 16.1 系统提示词组装
- 系统提示词初始化 (`src/utils/messages/systemInit.ts`)
- 角色定义与工具使用指南
- 输出格式规范
- 条件化提示词注入

### 16.2 功能提示词
- 压缩提示词 (`src/services/compact/prompt.ts`)
- 整理提示词 (`src/services/autoDream/consolidationPrompt.ts`)
- 记忆提取提示词 (`src/services/extractMemories/prompts.ts`)
- 分类器提示词

### 16.3 提示词缓存优化
- 1h TTL 缓存策略
- 片段级缓存 (systemPromptSectionCache)
- Beta Header 锁存避免 Cache 失效
- 缓存命中率优化

---

## 17. 自动模式系统 (Auto Mode)
> **代码入口**: `src/utils/planModeV2.ts`, `src/services/autoDream/autoDream.ts`
> **模式类型**: Normal, Auto, Plan, Fast

### 17.1 模式类型与切换
- Normal Mode (默认交互模式)
- Auto Mode (自动执行模式)
- Plan Mode (计划模式)
- Fast Mode (快速模式)

### 17.2 模式转换管理
- Plan Mode 转换 (`handlePlanModeTransition`)
- Auto Mode 转换 (`handleAutoModeTransition`)
- 模式状态追踪 (hasExitedPlanMode)
- 一次性通知机制 (needsPlanModeExitAttachment)

### 17.3 自动模式安全控制
- 自动模式权限检查
- 操作限制策略
- 自动模式退出附件
- 熔断机制 (`isAutoModeCircuitBroken`)

---

## 18. 技能搜索系统 (Skill Search)
> **代码入口**: `src/services/skillSearch/`
> **搜索范围**: 本地索引、远程仓库

### 18.1 远程技能搜索
- 远程技能加载 (`remoteSkillLoader.ts`)
- 技能仓库连接
- 技能元数据获取
- 搜索结果排序

### 18.2 本地索引搜索
- 本地技能索引 (`localSearch.ts`)
- 快速全文搜索
- 索引更新策略
- 搜索结果过滤

### 18.3 预加载与缓存
- 技能预加载 (`prefetch.ts`)
- 远程技能状态 (`remoteSkillState.ts`)
- 搜索遥测 (`telemetry.ts`)
- 特性检查 (`featureCheck.ts`)

---

## 19. 可观测性架构 (Observability)
> **代码入口**: OpenTelemetry 集成, `src/utils/slowOperations.ts`
> **三大支柱**: Metrics, Traces, Logs

### 19.1 指标收集 (Metrics)
- 会话计数 (sessionCounter)
- 代码行数统计 (locCounter)
- Token 使用统计 (tokenCounter)
- 成本追踪 (costCounter)
- 活跃时间统计 (activeTimeCounter)

### 19.2 分布式追踪 (Traces)
- Tracer Provider 管理
- 请求 ID 追踪 (lastMainRequestId)
- API 调用时间戳 (lastApiCompletionTimestamp)
- 压缩后标记 (pendingPostCompaction)

### 19.3 结构化日志 (Logs)
- Logger Provider 管理
- 事件日志 (eventLogger)
- 错误日志缓冲 (inMemoryErrorLog)
- 慢操作追踪 (`src/utils/slowOperations.ts`)

---

## 20. 并发会话管理 (Concurrent Sessions)
> **代码入口**: `src/utils/concurrentSessions.ts`, `src/bootstrap/state.ts`
> **会话隔离**: sessionId, sessionProjectDir

### 20.1 会话生命周期
- 会话创建 (`regenerateSessionId`)
- 会话切换 (`switchSession`)
- 会话信号订阅 (`onSessionSwitch`)
- 会话清理策略

### 20.2 会话隔离机制
- 会话 ID 管理 (sessionId, parentSessionId)
- 项目目录隔离 (sessionProjectDir)
- 状态原子性切换
- 会话恢复支持

### 20.3 会话持久化
- 会话 Transcript (.jsonl)
- 成本状态恢复 (`setCostStateForRestore`)
- 会话持久化禁用 (sessionPersistenceDisabled)
- PID 文件管理

---

## 21. CLI 系统与命令路由 (CLI System)
> **代码入口**: `src/cli/`, `src/commands.ts`, `src/main.tsx`
> **子命令**: claude, claude config, claude model, claude resume

### 21.1 命令行参数解析
- 参数解析与验证
- 子命令路由 (`src/commands.ts`)
- 帮助信息生成
- 版本信息显示

### 21.2 子命令实现
- 默认 REPL 模式 (`claude`)
- 配置管理 (`claude config`)
- 模型选择 (`claude model`)
- 会话恢复 (`claude resume`)
- 环境诊断 (`claude doctor`)

### 21.3 启动流程
- 主入口 (`src/main.tsx`)
- 初始化序列
- 交互模式检测 (isInteractive)
- 客户端类型识别 (clientType)

---

## 22. 优雅关闭系统 (Graceful Shutdown)
> **代码入口**: `src/utils/gracefulShutdown.ts`
> **信号处理**: SIGINT, SIGTERM

### 22.1 信号处理
- 中断信号捕获
- 清理钩子注册
- 强制退出处理
- 多次中断处理

### 22.2 清理流程
- 停止接受新请求
- 执行清理钩子
- 保存会话状态
- 关闭网络连接

### 22.3 资源释放
- 文件句柄关闭
- 子进程终止
- 缓存刷新
- 日志缓冲刷新

---

## 附录：架构概览图

```mermaid
graph TB
    subgraph "用户层"
        CLI[CLI 入口]
        REPL[REPL 模式]
        SDK[Agent SDK]
    end

    subgraph "核心引擎"
        QueryEngine[查询引擎]
        ToolOrchestrator[工具编排器]
        PermissionSystem[权限系统]
    end

    subgraph "工具层"
        FileTools[文件工具]
        ShellTools[Shell 工具]
        WebTools[Web 工具]
        AgentTools[代理工具]
        MCPTools[MCP 工具]
    end

    subgraph "扩展层"
        Plugins[插件系统]
        Skills[技能系统]
        Hooks[钩子系统]
        MCP[MCP 服务器]
    end

    subgraph "模型层"
        ModelManager[模型管理]
        APIProvider[API 提供商]
        CostTracker[成本追踪]
    end

    subgraph "存储层"
        SessionStore[会话存储]
        ConfigStore[配置存储]
        MemoryStore[记忆存储]
    end

    CLI --> QueryEngine
    REPL --> QueryEngine
    SDK --> QueryEngine

    QueryEngine --> ToolOrchestrator
    QueryEngine --> ModelManager
    ToolOrchestrator --> PermissionSystem

    PermissionSystem --> FileTools
    PermissionSystem --> ShellTools
    PermissionSystem --> WebTools
    PermissionSystem --> AgentTools
    PermissionSystem --> MCPTools

    FileTools --> Plugins
    ShellTools --> Hooks
    AgentTools --> Skills
    MCPTools --> MCP

    ModelManager --> APIProvider
    ModelManager --> CostTracker

    QueryEngine --> SessionStore
    PermissionSystem --> ConfigStore
    QueryEngine --> MemoryStore
```

---

## 23. CLI 命令系统 (CLI Commands)
> **代码入口**: `src/commands/`, `src/cli.ts`
> **设计模式**: 命令模式，子命令独立模块

### 23.1 命令路由与解析
- **文档**: [[features/45-cli-commands]]
- 主入口 (`src/cli.ts`)
- 子命令分发器 (`src/commands.ts`)
- 参数解析与验证
- 帮助信息生成

### 23.2 核心子命令
- **claude** — 默认 REPL 交互模式
- **claude config** — 配置管理
- **claude model** — 模型选择
- **claude resume** — 会话恢复
- **claude doctor** — 环境诊断

### 23.3 扩展子命令
- **claude assistant** — Assistant 模式 (`src/commands/assistant/`)
- **claude vim** — Vim 编辑器模式 (`src/commands/vim/`)
- **claude upgrade** — 版本升级 (`src/commands/upgrade/`)
- **claude tasks** — 任务管理 (`src/commands/tasks/`)
- **claude fork** — 会话分支 (`src/commands/fork/`)

### 23.4 命令上下文
- Client Type 检测 (clientType)
- 交互模式判断 (isInteractive)
- Remote 模式支持
- Sandbox 切换 (`src/commands/sandbox-toggle/`)

---

## 24. Cron 定时任务系统 (Scheduled Tasks)
> **代码入口**: `src/utils/cronTasks.ts`, `src/utils/cronTasksLock.ts`
> **持久化**: `.claude/scheduled_tasks.json`

### 24.1 Cron 表达式解析
- **文档**: [[features/46-cron-tasks]]
- 标准 5 字段语法 (`src/utils/cronTasks.ts:302-314`)
- 下次执行时间计算 (`nextCronRunMs`)
- 错过任务检测 (`findMissedTasks`)
- 任务验证与错误处理

### 24.2 任务调度架构
- 持久化任务管理 (`getCronFilePath`)
- 会话级临时任务 (sessionCronTasks)
- 任务 ID 生成
- 任务元数据存储

### 24.3 任务锁机制
- **代码入口**: `src/utils/cronTasksLock.ts`
- 分布式锁防止重复执行
- 锁超时与释放
- 任务状态追踪

### 24.4 抖动策略 (Jitter)
- Thundering Herd 问题避免
- DEFAULT_CRON_JITTER_CONFIG
- 单次抖动计算 (`oneShotJitteredNextCronRunMs`)
- 周期性抖动 (`jitteredNextCronRunMs`)

---

## 25. 迁移系统 (Migration System)
> **代码入口**: `src/migrations/`
> **触发时机**: 版本升级自动执行

### 25.1 模型迁移
- **文档**: [[features/47-migration-system]]
- Sonnet 1m → Sonnet 4.5 (`migrateSonnet1mToSonnet45.ts`)
- Sonnet 4.5 → Sonnet 4.6 (`migrateSonnet45ToSonnet46.ts`)
- Fennec → Opus (`migrateFennecToOpus.ts`)
- Opus 版本升级 (`migrateOpusToOpus1m.ts`)

### 25.2 设置迁移
- 自动更新设置 (`migrateAutoUpdatesToSettings.ts`)
- 权限绕过接受 (`migrateBypassPermissionsAcceptedToSettings.ts`)
- REPL Bridge 启用 (`migrateReplBridgeEnabledToRemoteControlAtStartup.ts`)
- MCP 服务器启用 (`migrateEnableAllProjectMcpServersToSettings.ts`)

### 25.3 迁移执行框架
- 版本检测机制
- 迁移脚本注册
- 迁移顺序管理
- 错误处理与回滚

### 25.4 Community 3 关联
- 迁移系统位于 Community 3 (390 nodes)
- 与 Settings 系统紧密关联
- 迁移触发点: `src/entrypoints/init.ts`

---

## 26. 提示词工程系统 (Prompt Engineering)
> **代码入口**: `src/utils/messages/systemInit.ts`, `src/services/compact/prompt.ts`
> **缓存策略**: Prompt Cache, 片段缓存

### 26.1 系统提示词组装
- **文档**: [[features/48-prompt-engineering]]
- 系统初始化提示词 (`src/utils/messages/systemInit.ts`)
- 角色定义与工具使用指南
- 输出格式规范
- 条件化提示词注入

### 26.2 功能提示词库
- 压缩提示词 (`src/services/compact/prompt.ts`)
- 整理提示词 (`src/services/autoDream/consolidationPrompt.ts`)
- 分类器提示词
- 工具专属提示词 (`src/tools/*/prompt.ts`)

### 26.3 提示词缓存优化
- 1h TTL 缓存策略 (promptCache1hAllowlist)
- 片段级缓存 (systemPromptSectionCache)
- Beta Header 锁存机制
- 缓存命中率优化

### 26.4 Community 9 关联
- 提示词系统关联 Community 9 (206 nodes)
- FileStateCache 用于缓存管理
- Tool 抽象支持提示词生成

---

## 27. 自动模式与计划模式 (Auto & Plan Mode)
> **代码入口**: `src/utils/planModeV2.ts`, `src/services/autoDream/autoDream.ts`
> **模式类型**: Normal, Auto, Plan, Fast

### 27.1 模式类型定义
- **文档**: [[features/49-auto-plan-modes]]
- Normal Mode — 默认交互模式
- Auto Mode — 自动执行模式
- Plan Mode — 计划模式（确认后执行）
- Fast Mode — 快速模式（轻量级）

### 27.2 模式转换管理
- Plan Mode 转换 (`handlePlanModeTransition`)
- Auto Mode 转换 (`handleAutoModeTransition`)
- 模式状态追踪 (hasExitedPlanMode)
- 一次性通知机制 (needsPlanModeExitAttachment)

### 27.3 自动模式安全控制
- 自动模式权限检查
- 操作限制策略
- 自动模式退出附件
- 熔断机制 (`isAutoModeCircuitBroken`)

### 27.4 Community 0 关联
- Auto Mode 位于 Community 0 (883 nodes)
- 与全局状态管理紧密关联
- kairosActive 状态控制

---

## 28. 技能搜索系统 (Skill Search)
> **代码入口**: `src/services/skillSearch/`
> **搜索范围**: 本地索引、远程仓库

### 28.1 远程技能搜索
- **文档**: [[features/50-skill-search]]
- 远程技能加载器 (`remoteSkillLoader.ts`)
- 技能仓库连接
- 技能元数据获取
- 搜索结果排序

### 28.2 本地索引搜索
- 本地全文搜索 (`localSearch.ts`)
- 快速索引查询
- 索引更新策略
- 搜索结果过滤

### 28.3 预加载与状态管理
- 技能预加载 (`prefetch.ts`)
- 远程技能状态 (`remoteSkillState.ts`)
- 特性检查 (`featureCheck.ts`)
- 搜索遥测 (`telemetry.ts`)

### 28.4 Community 2 关联
- 技能搜索关联 Community 2 (392 nodes)
- Plugin 系统协作
- Marketplace 集成

---

## 29. 可观测性架构 (Observability)
> **代码入口**: OpenTelemetry 集成, `src/utils/slowOperations.ts`
> **三大支柱**: Metrics, Traces, Logs

### 29.1 指标收集 (Metrics)
- **文档**: [[features/51-observability]]
- 会话计数 (sessionCounter)
- 代码行数统计 (locCounter)
- Token 使用统计 (tokenCounter)
- 成本追踪 (costCounter)
- 活跃时间统计 (activeTimeCounter)

### 29.2 分布式追踪 (Traces)
- Tracer Provider 管理
- 请求 ID 追踪 (lastMainRequestId)
- API 调用时间戳 (lastApiCompletionTimestamp)
- 压缩后标记 (pendingPostCompaction)

### 29.3 结构化日志 (Logs)
- Logger Provider 管理
- 事件日志 (eventLogger)
- 错误日志缓冲 (inMemoryErrorLog)
- 慢操作追踪 (`src/utils/slowOperations.ts`)

### 29.4 Community 0 关联
- 可观测性位于 Community 0 (883 nodes)
- slowOperations 监控性能
- debug_log 用于调试日志

---

## 30. 优雅关闭系统 (Graceful Shutdown)
> **代码入口**: `src/utils/gracefulShutdown.ts`
> **信号处理**: SIGINT, SIGTERM

### 30.1 信号处理
- **文档**: [[features/52-graceful-shutdown]]
- 中断信号捕获 (SIGINT)
- 终止信号处理 (SIGTERM)
- 多次中断处理策略
- 强制退出机制

### 30.2 清理流程
- 停止接受新请求
- 清理钩子执行
- 保存会话状态
- 关闭网络连接

### 30.3 资源释放
- 文件句柄关闭
- 子进程终止
- 缓存刷新
- 日志缓冲刷新

### 30.4 清理钩子注册
- 清理回调注册
- 钩子执行顺序
- 超时处理
- 错误隔离

---

## 附录：架构概览图
