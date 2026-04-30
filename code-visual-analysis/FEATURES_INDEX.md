# Claude Code 功能点文档索引

> 基于 code-visual-analysis 技能生成的 43 个功能专题文档
> 最后更新：2026-04-26

---

## 文档统计

- **总文档数**：43 个
- **总内容量**：约 450KB
- **覆盖模块**：12 个核心系统
- **Mermaid 图表**：100+ 张

---

## 模块索引

### 1. 工具系统 (Tool System)

| 文档 | 大小 | 核心内容 |
|------|------|----------|
| [[01-tool-orchestration]] | 9.5K | 工具编排、注册发现、权限过滤、MCP集成 |
| [[02-file-tools]] | 8.2K | Read/Edit/Write/Glob/Grep/Notebook |
| [[03-shell-tools]] | 8.7K | Bash/PowerShell、安全策略、沙箱隔离 |
| [[04-agent-tools]] | 9.2K | Agent/Task/Todo/TaskStop、多代理协作 |
| [[05-web-tools]] | 7.1K | WebFetch/WebSearch/WebBrowser、SSRF防护 |
| [[06-lsp-tools]] | 8.7K | LSP集成、定义跳转、诊断 |
| [[07-extension-tools]] | 9.4K | Skill/MCP/Workflow/Config、插件系统 |
| [[08-utility-tools]] | 10K | 交互提问、摘要、消息传递、计划模式、Worktree |

### 2. 对话引擎 (Conversation Engine)

| 文档 | 大小 | 核心内容 |
|------|------|----------|
| [[09-message-processing]] | 11K | 消息处理流程、流式响应、中断控制 |
| [[10-session-state]] | 15K | 会话持久化、历史记录、中断恢复 |
| [[11-context-window]] | 14K | Token预算、上下文压缩、缓存优化 |

### 3. 模型管理 (Model & API)

| 文档 | 大小 | 核心内容 |
|------|------|----------|
| [[12-model-management]] | 6.4K | 模型配置、别名解析、能力检测 |
| [[13-authentication]] | 9.8K | API Key管理、OAuth流程、多平台认证 |
| [[14-streaming]] | 10K | SSE流解析、错误重试、速率限制 |

### 4. 权限安全 (Security & Permissions)

| 文档 | 大小 | 核心内容 |
|------|------|----------|
| [[15-permissions]] | 11K | 权限模型、规则匹配、分类器 |
| [[16-sandbox]] | 9.7K | 沙箱适配器、后端隔离、资源限制 |
| [[17-security-checks]] | 11K | 命令检测、SSRF防护、危险模式 |

### 5. 插件系统 (Plugin System)

| 文档 | 大小 | 核心内容 |
|------|------|----------|
| [[18-plugin-system]] | 9.9K | 插件生命周期、Marketplace集成、热加载 |
| [[19-skill-system]] | 11K | Skill定义与加载、提示词模板、钩子机制 |
| [[20-hook-system]] | 13K | Hook类型与注册、异步执行、前置后置处理 |
| [[21-mcp-integration]] | 14K | MCP服务器管理、资源映射、传输协议 |

### 6. 多代理协作 (Multi-Agent)

| 文档 | 大小 | 核心内容 |
|------|------|----------|
| [[22-agent-types]] | 11K | 主代理、子代理、Coordinator、Worker |
| [[23-agent-communication]] | 12K | Mailbox消息传递、权限同步、状态共享 |
| [[24-agent-backends]] | 14K | InProcess/Tmux/ITerm后端、自动检测 |

### 7. UI终端 (UI & Terminal)

| 文档 | 大小 | 核心内容 |
|------|------|----------|
| [[25-terminal-rendering]] | 17K | Ink框架、ANSI处理、光标管理、BiDi支持 |
| [[26-interactive-components]] | 13K | 输入框、列表、选择器、进度指示器 |
| [[27-vim-mode]] | 17K | Vim键位、模式切换、文本对象、Motion |

### 8. 配置设置 (Configuration)

| 文档 | 大小 | 核心内容 |
|------|------|----------|
| [[28-settings]] | 9.7K | 设置源优先级、迁移机制、MDM覆盖 |
| [[29-feature-flags]] | 9.4K | 环境变量、Feature Flag、GrowthBook集成 |
| [[30-project-config]] | 12K | CLAUDE.md解析、AGENTS.md、Worktree配置 |

### 9. 记忆上下文 (Memory & Context)

| 文档 | 大小 | 核心内容 |
|------|------|----------|
| [[31-session-memory]] | 7.0K | 记忆提取存储、提示词生成、检索注入 |
| [[32-auto-dream]] | 7.2K | 后台整理机制、整理提示词、锁机制 |
| [[33-team-memory]] | 7.8K | 跨代理同步、秘密扫描、文件监视 |

### 10. 监控分析 (Monitoring & Analytics)

| 文档 | 大小 | 核心内容 |
|------|------|----------|
| [[34-analytics]] | 9.1K | 事件埋点、Datadog集成、遥测上报 |
| [[35-error-monitoring]] | 11K | Sentry集成、错误分类、调试日志 |
| [[36-performance]] | 13K | 慢操作追踪、Token统计、成本追踪 |

### 11. 开发者工具 (Developer Tools)

| 文档 | 大小 | 核心内容 |
|------|------|----------|
| [[37-agent-sdk]] | 9.6K | SDK类型定义、运行时API、程序化控制 |
| [[38-repl-mode]] | 7.6K | REPL工具、VM沙箱、交互式调试 |
| [[39-remote-control]] | 11K | WebSocket会话、SDK消息适配、权限桥接 |

### 12. 高级特性 (Advanced Features)

| 文档 | 大小 | 核心内容 |
|------|------|----------|
| [[40-computer-use]] | 12K | 屏幕截图、鼠标键盘控制、UI自动化 |
| [[41-chrome-integration]] | 9.5K | Native Host通信、浏览器扩展、Chrome Use |
| [[42-voice-mode]] | 12K | 语音识别、语音合成、关键词检测、实时转录 |
| [[43-bridge-mode]] | 14K | IDE集成、文件监听、诊断追踪 |

---

## 核心发现汇总

### 架构亮点

1. **工具系统**
   - 统一的 Tool 接口抽象
   - 三层过滤机制：内置工具 → 权限过滤 → MCP合并
   - 延迟加载策略优化Token消耗

2. **安全体系**
   - 多层权限模型：模式分类 + 规则覆盖
   - 沙箱适配器模式：Firecracker/gVisor/Native
   - 命令AST解析：精确安全检测

3. **扩展能力**
   - Skill 技能系统：领域模板 + 钩子机制
   - MCP 协议：标准化外部工具集成
   - Hook 生命周期：8个时机点全覆盖

4. **多代理协作**
   - Fork机制：子代理复用父代理缓存
   - 邮箱模式：文件系统消息传递
   - 三后端架构：InProcess/Tmux/ITerm2

### 性能优化

1. **Token管理**
   - 多层级上下文压缩
   - 文件状态缓存
   - 提示词缓存策略

2. **终端渲染**
   - 双缓冲 + 差异检测
   - DECSTBM硬件滚动优化
   - 对象池避免内存泄漏

3. **成本追踪**
   - 实时Token统计
   - 按模型聚合显示
   - 会话级持久化

---

## 使用建议

### 阅读路径

**初学者路径**：
1. 01-tool-orchestration → 理解工具系统全貌
2. 09-message-processing → 理解对话流程
3. 15-permissions → 理解权限模型
4. 28-settings → 理解配置体系

**开发者路径**：
1. 18-plugin-system → 扩展系统机制
2. 19-skill-system → 技能开发指南
3. 20-hook-system → 钩子机制详解
4. 37-agent-sdk → SDK集成方案

**架构师路径**：
1. 22-agent-types → 多代理架构
2. 25-terminal-rendering → 终端渲染引擎
3. 11-context-window → 上下文优化策略
4. 24-agent-backends → 后端实现对比

---

## 文档规范

每个文档遵循统一结构：
1. **概述**：功能定位、解决的问题
2. **设计原理**：架构决策、设计动机
3. **实现原理**：核心机制、关键算法
4. **功能展开**：按子功能逐个下钻
5. **数据结构**：核心实体、配置结构
6. **组合使用**：与其他功能的协作
7. **小结**：设计取舍、局限、演进方向

---

## 代码证据来源

- **知识图谱**：`graphify-out/wiki/` (12411 nodes · 38767 edges · 1709 communities)
- **源代码**：基于实际代码路径引用（格式：`src/xxx.ts:行号`）
- **架构图**：所有结论可回溯到代码事实

---

*生成于 2026-04-26 · 使用 code-visual-analysis 技能*
