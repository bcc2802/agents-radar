# AI CLI 工具社区动态日报 2026-06-28

> 生成时间: 2026-06-28 03:43 UTC | 覆盖工具: 9 个

- [Claude Code](https://github.com/anthropics/claude-code)
- [OpenAI Codex](https://github.com/openai/codex)
- [Gemini CLI](https://github.com/google-gemini/gemini-cli)
- [GitHub Copilot CLI](https://github.com/github/copilot-cli)
- [Kimi Code CLI](https://github.com/MoonshotAI/kimi-cli)
- [OpenCode](https://github.com/anomalyco/opencode)
- [Pi](https://github.com/badlogic/pi-mono)
- [Qwen Code](https://github.com/QwenLM/qwen-code)
- [DeepSeek TUI](https://github.com/Hmbown/DeepSeek-TUI)
- [Claude Code Skills](https://github.com/anthropics/skills)

---

## 横向对比

好的，作为专注于 AI 开发工具生态的资深技术分析师，我已仔细审阅了您提供的 2026-06-28 各主流 AI CLI 工具的社区动态日报。以下是根据这些数据生成的横向对比分析报告。

---

### **AI CLI 工具生态横向对比分析报告 (2026-06-28)**

#### **1. 生态全景**

当前 AI CLI 工具生态呈现出 **“高速迭代、安全觉醒、成本为王”** 的态势。各工具均在积极修复 Bug 和推出新功能，但社区反馈的焦点已从单纯的功能“魔法”转向稳定性、可预测性和成本效益。**Opus 4.7 思考摘要渲染失败**（Claude Code）与 **GPT-5.5 配额异常消耗**（Codex CLI）成为两大标志性事件，反映出前沿模型与工具集成间的新摩擦。同时，**安全性**（SSRF、路径遍历、恶意包）和 **Agent 行为可靠性**（任务范围蔓延、误报成功）成为跨工具的普遍关注点，用户对 AI Agent 的“信任”和“控制”需求正空前强烈。

#### **2. 各工具活跃度对比**

| 工具名称 | 社区热度 (Issues+PRs) | 热点问题/趋势 | 版本发布 | 关键信号 |
| :--- | :--- | :--- | :--- | :--- |
| **Claude Code** | 极高 (15+ Issues/PRs) | Opus 4.7 新模型兼容性 Bug | 无 | 新模型集成阵痛，用户反馈强烈 |
| **OpenAI Codex CLI** | 极高 (20+ Issues/PRs) | 配额消耗异常、MCP 进程泄漏 | 3 个 Rust Alpha | 计费与性能是核心痛点 |
| **Gemini CLI** | 高 (20+ Issues/PRs) | Agent 行为可靠性、安全加固 | 1 个 Nightly 安全修复 | 安全与可控性成为最高优先级 |
| **GitHub Copilot CLI** | 中 (15 Issues, 3 PRs) | Windows 兼容性崩塌、终端渲染 | 无 (但报告回归) | 平台稳定性压倒一切 |
| **Kimi Code CLI** | 低 | 无活动 | 无 | - |
| **OpenCode** | 高 (10+ Issues/PRs) | 内存泄漏、WSL 兼容、模型行为 | 无 | 性能与跨平台体验是主要短板 |
| **Pi** | 极高 (20+ Issues/PRs，大量CLOSED) | TUI 渲染、扩展 API、恶意包 | 无 | 社区贡献活跃，Bug修复高效 |
| **Qwen Code** | 高 (10+ Issues/PRs) | 成本优化、状态持久化、后台任务 | 1 个快照 | 从功能开发转向体验与成本优化 |
| **DeepSeek TUI** | 极高 (10+ Issues/PRs) | 缓存命中率、Token 消耗、插件系统 | 无 (密集开发中) | 性能与成本是用户最尖锐的痛点 |

**注释**：
- **社区热度**：基于提供的 Issue/PR 数量及评论活跃度定性判断。
- **趋势**：指当前社区最热议的 1-2 个核心话题。

#### **3. 共同关注的功能方向**

多个工具的社区均表达了对以下方向的强烈需求，表明这是行业级痛点：

- **成本优化与 Token 透明化（Codex CLI, Qwen Code, DeepSeek TUI）**：
    - **诉求**：实时、准确的配额/Token 消耗明细；避免后台无感知的 Token 浪费；降低缓存未命中率。
    - **原因**：API 调用成本直接影响用户留存，不透明的计费模型严重损害信任。

- **Agent 行为可预测性与控制力（Claude Code, Gemini CLI, DeepSeek TUI）**：
    - **诉求**：防止 Agent 擅自扩大任务范围；提供更精细的权限与控制配置；避免“虚假成功”报告。
    - **原因**：Agent 的“黑盒”行为和不可预测性是开发者接受其进入生产工作流的最大障碍。

- **跨平台稳定性与兼容性（GitHub Copilot CLI, OpenCode, Qwen Code）**：
    - **诉求**：尤其是在 Windows (WSL) 和 ARM64 架构上，需要更稳定的基础命令、路径处理和剪贴板功能。
    - **原因**：开发者环境的多样性要求工具具备健壮的跨平台能力，频繁的兼容性 Bug 会严重破坏工作流。

- **上下文与持久化能力（Claude Code, Qwen Code, DeepSeek TUI）**：
    - **诉求**：跨会话、跨设备的“记忆”能力；将任务、计划等状态持久化到项目而非本地；可配置的手动上下文压缩功能。
    - **原因**：用户期望 AI CLI 从“一次性对话”进化为“持续参与项目的智能伙伴”。

#### **4. 差异化定位分析**

- **Claude Code & Qwen Code**：**“模型能力先行”**。与自家旗舰模型深度绑定（Opus, Qwen），社区问题多源自新模型与工具的适配摩擦。更新迭代受模型发布节奏驱动。
- **OpenAI Codex CLI**：**“生态平台”**。依托 OpenAI 强大的 API 生态和模型系列，重点在于`gpt-5.5`等通用模型的性能、计费和稳定性。
- **Gemini CLI**：**“安全与 Agent 可靠性”**。在防止 SSRF、路径遍历和 Agent 行为控制上投入大量 PR/Issue，突出 Google 对安全和负责任 AI 的重视。
- **GitHub Copilot CLI**：**“IDE 外围助手”**。定位为 Copilot 在终端内的扩展，其核心问题（剪贴板、终端渲染）表明其离“独立 Agent”还有距离，更依赖 IDE 生态。
- **OpenCode**：**“开源社区驱动”**。社区贡献者活跃，PR 涵盖面广（Agent 工具、WSL 修复），但稳定性（内存泄漏）和核心模型兼容性是主要短板。
- **Pi**：**“高扩展性核心”**。发展重心是打造强大的**扩展 API 系统**（允许第三方调用内部工具、报告成本），目标是成为一个可编程的平台而非单一应用。
- **DeepSeek TUI**：**“性能优化先锋”**。社区讨论深度集中于“缓存”、“Token消耗”等底层计算优化，展现出鲜明的技术硬核风格，对高端和成本敏感型开发者有巨大吸引力。

#### **5. 社区热度与成熟度**

- **高度活跃，快速迭代期**：**Claude Code, OpenAI Codex CLI, Pi, DeepSeek TUI**。这些工具有大量 Issue/PR 涌入，Bug 修复和新功能引入速度快，社区反馈强烈，但也意味着产品形态尚不稳定。
- **活跃发展期**：**Gemini CLI, OpenCode, Qwen Code**。社区活跃，有明确的发展方向（安全、性能、成本），产品功能相对完备，正在解决核心体验问题。
- **平稳期或平台期**：**GitHub Copilot CLI, Kimi Code CLI**。Copilot CLI 虽有 Bug 反馈，但整体定位清晰，变化不大；Kimi Code CLI 当天无活动，可能处于维护或内部开发阶段。

#### **6. 值得关注的趋势信号**

1.  **“Post-Magic”时代来临**：开发者对 AI 带来的“魔法”已习以为常，现在他们对工具的**可预测性、稳定性和经济性**提出了更高要求。Bug 报告和功能请求不再聚焦于“能不能做”，而是“能不能做好、做稳、做省钱”。
2.  **模型与工具的“集成鸿沟”**：Opus 4.7 和 GPT-5.5 的例子表明，最先进的模型与成熟工具间仍存在显著的集成鸿沟。工具的适配速度、参数传递（如 thinking summaries）和计费模型（quota 消耗）都可能成为瓶颈。**开发者不应盲目追求最新模型，而应关注其与工具链的磨合成熟度。**
3.  **Agent 安全与伦理成为硬性需求**：Gemini CLI 对 SSRF、路径遍历的修复，以及 Pi 对恶意包的快速响应，表明安全不再是可选项。**“默认安全”和“用户可控”** 是赢得企业级信心的关键。
4.  **缓存与上下文管理的竞争白热化**：降低 API 成本和提高响应速度成为核心竞争点。DeepSeek TUI 的“缓存最大化模式”、Qwen Code 的“自动压缩阈值”等，预示着**未来的 AI CLI 将不再是简单的提示词工程，而是复杂的系统级缓存、上下文和状态管理引擎**。这是当前最值得跟踪的下一个技术爆发点。
5.  **平台化与扩展性需求抬头**：Pi 和 OpenCode 通过扩展 API、插件系统等方式，向“平台”演进。这表明开发者社区不仅满足于单一工具，更希望**建设自己的 AI 工作流**。AI CLI 工具的角色将从“单兵作战”转变为“部队的核心调度器”。

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)

好的，作为一名专注于 Claude Code 生态的技术分析师，以下是基于您提供的数据（截止 2026-06-28）生成的社区热点报告。

---

### Claude Code Skills 社区热点报告 (截至 2026-06-28)

#### 1. 热门 Skills 排行 (Top 5-8 PRs)

以下是社区讨论最活跃、关注度最高的 Skills 动态：

1.  **`fix(skill-creator): run_eval.py` 全面修复 (#1298)**
    *   **功能**：对 `skill-creator` 核心评估脚本 `run_eval.py` 进行重大修复，解决其在 Windows 下的兼容性、触发检测逻辑以及并行工作线程问题。目标是让技能描述优化循环不再“对着噪音优化”。
    *   **热点**：这是当前社区最核心的痛点。大量用户（#556）报告 `recall=0%` 的 bug，使得技能创建和优化流程彻底失效。该 PR 是目前最受期待的修复方案，社区在急切等待其合并。
    *   **状态**: **OPEN**
    *   **链接**: [PR #1298](https://github.com/anthropics/skills/pull/1298)

2.  **`fix(skill-creator):` Windows 子进程与编码错误修复 (#1050)**
    *   **功能**：专门修复 `skill-creator` 在 Windows 平台上的两个关键问题：`subprocess.Popen` 无法找到 `claude.cmd`，以及 `cp1252` 编码导致 Unicode 解码失败。
    *   **热点**：与 #1298 类似，此 PR 反映了 Windows 用户面临的严峻兼容性问题。这是让 `skill-creator` 在 Windows 上可用的基础性修复。
    *   **状态**: **OPEN**
    *   **链接**: [PR #1050](https://github.com/anthropics/skills/pull/1050)

3.  **`skill-creator: fix run_eval.py` Windows 管道读取崩溃 (#1099)**
    *   **功能**：修复 `run_eval.py` 在 Windows 上从子进程管道读取数据时的崩溃问题，该问题会导致所有查询都被标记为“未触发”。
    *   **热点**：与 #1298 和 #1050 共同构成了对 `skill-creator` 在 Windows 平台的全方位修复需求，说明该工具在 Windows 上几乎无法使用。
    *   **状态**: **OPEN**
    *   **链接**: [PR #1099](https://github.com/anthropics/skills/pull/1099)

4.  **`fix(skill-creator): run_eval` 触发检测与技能名识别修复 (#1323)**
    *   **功能**：进一步修复 `run_eval.py` 无法正确检测技能被触发的问题，特别是当技能名字较为复杂或遇到的第一个非技能工具时，导致 `recall=0%`。
    *   **热点**：这是对 `skill-creator` 核心评估逻辑的又一次精准打击，表明社区很关注评估系统的准确性和可靠性。
    *   **状态**: **OPEN**
    *   **链接**: [PR #1323](https://github.com/anthropics/skills/pull/1323)

5.  **`fix(skill-creator):` 检测未引用的 YAML 特殊字符 (#539)**
    *   **功能**：在 `quick_validate.py` 中添加预解析校验，检测 `description` 字段中未加引号的 YAML 特殊字符（如 `:`）。
    *   **热点**：这是一个小而关键的“体验优化”，解决了因 YAML 解析错误导致技能描述被截断或解析失败的静默问题。类似的 PR #361 也同样活跃，说明社区对技能创建过程的健壮性有共同诉求。
    *   **状态**: **OPEN**
    *   **链接**: [PR #539](https://github.com/anthropics/skills/pull/539)

6.  **`fix(pdf):` 更正大小写敏感文件引用 (#538)**
    *   **功能**：修复 `skills/pdf/SKILL.md` 中对其他文件（如 `reference.md`）的大小写引用问题，以兼容大小写敏感的文件系统。
    *   **热点**：虽然是一个小修复，但揭示了技能在跨平台分发和部署时可能存在的隐藏兼容性问题。类似的还有对 ODT (#486) 和 DOCX (#541) 技能的修复，表明社区对已有技能的稳定性和跨平台适配性有较高要求。
    *   **状态**: **OPEN**
    *   **链接**: [PR #538](https://github.com/anthropics/skills/pull/538)

7.  **`Add document-typography` 排印质量技能 (#514)**
    *   **功能**：新增一个专门用于控制 AI 生成文档排印质量的技能，解决孤行、寡段、编号错位等常见问题。
    *   **热点**：这是一个非常实用的技能，直接针对 AI 生成文档的“一眼就能看出是 AI 写的”痛点，获得了社区的关注，体现了对“输出质量”的精细化追求。
    *   **状态**: **OPEN**
    *   **链接**: [PR #514](https://github.com/anthropics/skills/pull/514)

#### 2. 社区需求趋势 (From Issues)

从 Issues 中可以提炼出社区最迫切的几个需求方向：

*   **安全与信任 (Security & Trust)** (#492)：社区最大的担忧来自于命名空间问题。用户担心 `anthropic/` 下的社区技能会冒充官方技能，构成信任边界滥用。**对 Skill 的签名、来源验证和权限控制的需求正在迅速增长。**
*   **共享与协作 (Sharing & Collaboration)** (#228)：用户迫切需要一种简单的方式在组织内部分享 Skills，而不是通过手动下载文件、发送消息再上传的笨拙流程。**企业级 Skill 库或分享链接是明确的业务需求。**
*   **工具稳定性与兼容性 (Tool Stability & Compatibility)** (#556, #202, #1061)：`skill-creator` 工具链的稳定性（尤其是 `run_eval.py` 的 `0% recall` bug）是压倒性的社区痛点。此外，Windows 平台的兼容性问题是实现跨平台普及的最大障碍。**用户期望官方提供一个开箱即用、稳定可靠的开发者工具。**
*   **高价值技能类型（High-Value Skill Types）**：
    *   **代理治理 (Agent Governance)** (#412)：用户希望有成熟的模式和最佳实践来构建安全、可控的 AI Agent 系统，包括策略执行、威胁检测和审计。
    *   **安全分析 (Security Analyzer)** (PR #83)：元技能（如安全分析器）的提出，表明社区不仅需要业务技能，更需要提升 Skill 本身质量和安全性的“工具”。
    *   **开发工作流 (Development Workflow)** (PR #147， #723)：代码库审计、测试模式等技能的提出，展示了用户希望将 Claude Skill 更深地嵌入到标准软件开发流程中。

#### 3. 高潜力待合并 Skills

以下 PR 评论活跃且尚未合并，表明社区对这些新技能有强烈兴趣，但官方仍在审查或优化中：

*   **`odt` 技能 (#486)**：支持创建、填充和解析 ODT/OpenDocument 格式。这填补了文档处理能力的一个重要空白，特别是对于开源和国际化场景有巨大价值。**链接**: [PR #486](https://github.com/anthropics/skills/pull/486)
*   **`testing-patterns` 技能 (#723)**：一个全面的测试模式技能，覆盖单元测试、React 组件测试等。如果合并，将成为开发者的重要助手，对提升代码质量意义重大。**链接**: [PR #723](https://github.com/anthropics/skills/pull/723)
*   **`shodh-memory` 技能 (#154)**：一个持久化记忆系统，用于在跨会话间维护 AI Agent 的上下文。这触及了 Agent 能力的核心，如果能通过 Skill 优雅实现，将极大提升 Agent 的实用性。**链接**: [PR #154](https://github.com/anthropics/skills/pull/154)
*   **`appdeploy` 技能 (#360)**：允许 Claude 直接部署和管理全栈 Web 应用。这代表了从“代码生成”到“一键部署”的关键一步，是提升 AI 编程闭环能力的高潜力技能。**链接**: [PR #360](https://github.com/anthropics/skills/pull/360)

#### 4. Skills 生态洞察

**当前社区最集中的诉求已从“创造更多技能”转向“让技能生态系统稳定、可靠且安全地运行”，特别是核心工具（如 `skill-creator`）在非理想环境（如 Windows）下的健壮性，以及对技能来源和权限的信任机制。**

---

好的，这是 2026 年 6 月 28 日的 Claude Code 社区动态日报。

---

## 🗞️ 2026-06-28 Claude Code 社区动态日报

### 今日速览

今日社区动态高度集中，**Opus 4.7 模型的思考摘要（Thinking Summaries）在 VS Code 扩展中渲染失败**是绝对热点，三个高赞 bug 累计获得超 150 个 👍。此外，Windows 平台的原生通知、Cowork 模式下的人工压缩功能，以及 MCP 插件路径不一致等问题也引发了开发者关注。

---

### 社区热点 Issues

本周社区最关注的焦点无疑是 **Opus 4.7 思考摘要缺失**，以下 10 个 Issue 值得重点关注：

1.  **🔥 [#49268] Opus 4.7 缺少思考摘要——核心问题根源**
    -   开发者 `yusufmo1` 深入调查发现，Claude Code 的 harness 在调用 Opus 4.7 时，没有设置 `display: "summarized"` 参数，导致模型返回的思考摘要未被正确渲染。
    -   **社区反应**: 极高热度 (👍 75)，评论 46 条。这是关于该问题的根源分析，被众多用户引用和确认。这是理解和解决该问题的关键 Issue。
    -   **链接**: [https://github.com/anthropics/claude-code/issues/49268](https://github.com/anthropics/claude-code/issues/49268)

2.  **🔥 [#49322] Opus 4.7 思考摘要未在 VS Code 扩展中渲染 (macOS)**
    -   用户 `ChefJulio` 报告在 macOS 系统的 VS Code 扩展中，Opus 4.7 的思考摘要无法正常显示。这是该问题在特定平台上的重现报告。
    -   **社区反应**: 极高热度 (👍 41)，评论 47 条。表明该 Bug 在 macOS 上影响广泛，是本文所有 Issue 中讨论最活跃的。
    -   **链接**: [https://github.com/anthropics/claude-code/issues/49322](https://github.com/anthropics/claude-code/issues/49322)

3.  **🔥 [#49902] Opus 4.7 思考摘要未渲染 (VS Code & WSL)**
    -   用户 `joshlizana` 报告在 WSL2 环境下，VS Code 扩展同样无法渲染 Opus 4.7 的思考摘要，确认了该问题的跨平台性，不仅是 macOS 独有。
    -   **社区反应**: 极高热度 (👍 41)，评论 14 条。与上一个 Issue 互为补充，证实了问题的普遍性。
    -   **链接**: [https://github.com/anthropics/claude-code/issues/49902](https://github.com/anthropics/claude-code/issues/49902)

4.  **🔥 [#59844] `showThinkingSummaries: true` 配置在非交互场景下无效**
    -   用户 `ojura` 发现，即使在 `settings.json` 中设置了 `"showThinkingSummaries": true`，该配置在 VS Code 扩展的聊天面板、SDK 调用及 `--print` 模式下依然无效，API 返回的 thinking 块内容为空。
    -   **社区反应**: 较高热度 (👍 6)，评论 10 条。指出了该 Bug 影响的不仅仅是 TUI，而是所有非交互式界面，影响范围广泛。
    -   **链接**: [https://github.com/anthropics/claude-code/issues/59844](https://github.com/anthropics/claude-code/issues/59844)

5.  **⬆️ [#70622] 【功能请求】添加选项以禁用终端中可点击的“是/否”提示**
    -   用户 `antonyscott-codurance` 强烈反馈新引入的“可点击 Yes/No”权限功能因误触导致操作被意外取消或批准，希望提供配置项恢复键盘操作。
    -   **社区反应**: 需求强烈 (👍 24)，评论 8 条。反映了部分用户对新交互方式的不适应，以及对于安全和精确控制的需求。
    -   **链接**: [https://github.com/anthropics/claude-code/issues/70622](https://github.com/anthropics/claude-code/issues/70622)

6.  **🐛 [#39636] Cowork VM 在 Snapdragon X Plus (ARM64) 上无法启动**
    -   用户 `ivangc1` 报告在 Snapdragon X Plus (ARM64) 架构的 Windows 设备上使用 Cowork 功能时，VM 内核引导超时，完全无法使用。
    -   **社区反应**: 评论 32 条。这是一个影响特定硬件平台的严重 Bug，对于使用 ARM64 Windows 设备的开发者是致命问题。
    -   **链接**: [https://github.com/anthropics/claude-code/issues/39636](https://github.com/anthropics/claude-code/issues/39636)

7.  **⬆️ [#57230] VS Code 扩展：添加原生系统通知功能**
    -   用户 `mengshengwu` 请求为 VS Code 扩展增加原生 Toast 通知，当 Claude 需要用户关注（如权限审批、任务完成）时能主动提醒，而非仅依赖状态栏图标。
    -   **社区反应**: 需求强烈 (👍 14)，评论 4 条。这是一个提升 IDE 内体验的重要改进，能解决开发者切换窗口后错过 Claude 请求的问题。
    -   **链接**: [https://github.com/anthropics/claude-code/issues/57230](https://github.com/anthropics/claude-code/issues/57230)

8.  **🐛 [#69950] 安全分类器故障导致所有 Bash/tool 调用被阻塞**
    -   用户 `Naloku` 报告在自动审批模式下，一个“暂时不可用”的安全分类器错误阻塞了所有 Bash 和 MCP 工具调用，导致功能完全瘫痪。
    -   **社区反应**: 这是一个关键性的故障，虽然评论不多，但其影响面极大，属于“致命” Bug 级别。
    -   **链接**: [https://github.com/anthropics/claude-code/issues/69950](https://github.com/anthropics/claude-code/issues/69950)

9.  **🐛 [#57102] macOS 上 Worktree 中使用时残留 .git/index.lock 文件**
    -   用户 `pmatseykanets` 报告在使用 Git Worktrees 时，Claude Code 的常规 CLI 操作会留下陈旧的 `.git/index.lock` 文件，导致后续操作失败。
    -   **社区反应**: 这是一个影响 Git 高级用户工作流的隐蔽 Bug，对于依赖 Worktrees 的开发者是核心痛点。
    -   **链接**: [https://github.com/anthropics/claude-code/issues/57102](https://github.com/anthropics/claude-code/issues/57102)

10. **⬆️ [#65114] Cowork：为用户提供手动压缩（/compact）功能**
    -   用户 `Jason26214` 请求在 Cowork 模式中提供用户手动触发上下文压缩的 `/compact` 命令，因为自动压缩时机不可控，影响使用体验。
    -   **社区反应**: 评论 5 条。体现了用户希望获得对会话上下文的更多主动控制权，而非完全依赖自动策略。
    -   **链接**: [https://github.com/anthropics/claude-code/issues/65114](https://github.com/anthropics/claude-code/issues/65114)

---

### 重要 PR 进展

过去24小时 PR 活动较少，以下为值得关注的 2 个更新：

1.  **🛠️ [#68787] 修复脚本：为 `edit-issue-labels.sh` 添加错误提示**
    -   贡献者 `AZERDSQ131` 修复了一个小但有用的问题。当 `edit-issue-labels.sh` 脚本在没有提供任何标签参数（如 `--add-label`）时，会静默退出并返回错误码 1。此 PR 为其添加了清晰的错误信息输出到 stderr，方便 CI 流程或手动运行时调试。
    -   **链接**: [https://github.com/anthropics/claude-code/pull/68787](https://github.com/anthropics/claude-code/pull/68787)

---

### 功能需求趋势

从今日的 Issue 和 PR 中，可以明显看出社区需求的几个核心方向：

-   **IDE & 通知集成**
    -   **需求**: VS Code 扩展功能增强是热门话题。主要需求包括增加**原生系统/Toast 通知**、**终端可点击按钮的配置选项**，以及为**移动端提供可操作的审批通知**。
    -   **动因**: 开发者希望在 IDE 中更流畅地工作，减少切换成本，并能及时响应 Claude 的请求。

-   **性能与稳定性**
    -   **需求**: 大量 Bug 报告指向 **Opus 4.7** 模型的兼容性问题（思考摘要缺失、模型 ID 错误等）和** Git 工作流** 中的稳定性问题（残留 lock 文件）。此外，**ARM64 平台** 的兼容性问题仍是痛点。
    -   **动因**: 用户（尤其是高级开发者）对工具的稳定性和新模型的无缝集成有很高要求。

-   **用户体验与控制**
    -   **需求**: 用户希望获得更多控制权，例如 **Cowork 模式下手动触发压缩**、**配置可点击按钮行为**。
    -   **动因**: 工具越来越智能，但用户不希望失去对关键流程（如权限审批、上下文管理）的主动权。

-   **MCP 生态**
    -   **需求**: **MCP 服务器** 相关的 Bug 依旧频繁，包括初始化指令未传递给模型、指令被截断、环境变量缺失等。
    -   **动因**: MCP 生态作为 Claude Code 扩展能力的核心，其稳定性和功能的正确性对开发者至关重要。

---

### 开发者关注点

综合今日数据，开发者反馈中最突出的痛点和需求是：

-   **Opus 4.7 思考摘要失效是当前最强烈的痛点**。这直接影响了使用最新模型进行复杂推理时的用户体验，社区反馈热度极高，且已有人定位到根本原因，团队应优先响应。
-   **权限审批交互的争议**。新引入的“可点击”审批功能引发了部分用户的不满，核心在于**误操作风险**和**缺乏配置选项**。这表明任何 UI 交互的变革都应提供回退方案或可配置性。
-   **Cowork 和 ARM64 等特定场景的兼容性问题**依然存在。这表明 Claude Code 在多平台、多架构的支持上仍需持续打磨。
-   **用户对“通知”类功能的呼声很高**。无论是 IDE 内还是 OS 级通知，开发者都希望工具能更主动地“找到”他们，而不是被动等待用户检查状态。

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# 2026-06-28 OpenAI Codex 社区动态日报

## 今日速览

今日社区最突出的问题是**速率限制与配额消耗异常**，有用户反馈 Plus 计划的 `gpt-5.5` 模型配额在 2-3 条消息内耗尽，触发广泛讨论（186 条评论）。同时，**MCP 进程泄漏**和 **SQLite 日志写入量过大** 等稳定性 bug 持续发酵。值得关注的是，新版 OAuth 支持相关 PR 已形成多个依赖栈，正在快速推进中。

## 版本发布

过去 24 小时内发布了 **3 个 Rust Alpha 版本**：
- [rust-v0.143.0-alpha.29](https://github.com/openai/codex/releases/tag/rust-v0.143.0-alpha.29)
- [rust-v0.143.0-alpha.28](https://github.com/openai/codex/releases/tag/rust-v0.143.0-alpha.28)
- [rust-v0.143.0-alpha.27](https://github.com/openai/codex/releases/tag/rust-v0.143.0-alpha.27)

三者均为维护性发布，未附带详细变更日志。

## 社区热点 Issues（Top 10）

### 1. #28879 - GPT-5.5 速率限制成本暴涨 10–20 倍
- **热度**: 🔥 334 👍, 186 条评论
- **摘要**: Plus 用户反馈，自 6 月 16 日起，`gpt-5.5` 模型的每 token 配额消耗率暴涨 10-20 倍，原本支持 20+ 次对话的 5h 预算现在 2-3 条消息即耗尽。用户贴出了 session 日志中的 `token_count` 和 `rate_limits` 事件佐证。
- **链接**: https://github.com/openai/codex/issues/28879

### 2. #11023 - 强烈需求的 Linux 桌面应用
- **热度**: 650 👍, 130 条评论
- **摘要**: 社区对 Linux 版 Codex 桌面应用的呼声极高。用户因 Mac 版耗电严重，希望在 Linux 桌面获得原生体验。
- **链接**: https://github.com/openai/codex/issues/11023

### 3. #28224 - SQLite 日志可写 640TB/年，消耗 SSD 寿命（已修复）
- **热度**: 400 👍, 93 条评论
- **摘要**: 用户报告 Codex SQLite 反馈日志写入量异常巨大（估算 640TB/年）。作者于 6 月 23 日更新确认，3 个相关 PR 已合并，可避免约 85% 的日志写入。已建议关闭。
- **链接**: https://github.com/openai/codex/issues/28224

### 4. #2847 - 请求敏感文件排除机制（`.codexignore`）
- **热度**: 414 👍, 79 条评论
- **摘要**: 用户需要一个 `.gitignore` 式的机制来标记“禁止 agent 读取/发送的文件”，支持仓库级和全局配置，比如保留 `node_modules/` 的可搜索性但禁止上传。
- **链接**: https://github.com/openai/codex/issues/2847

### 5. #30224 - `X-OpenAI-Internal-Codex-Responses-Lite` 模型不支持错误
- **热度**: 18 👍, 52 条评论
- **摘要**: 用户在使用自定义模型时，API 返回 `This model is not supported when using X-OpenAI-Internal-Codex-Responses-Lite`。大量用户出现类似问题。
- **链接**: https://github.com/openai/codex/issues/30224

### 6. #29955 - Pro*5 用户 100 额度 1 条消息耗尽
- **热度**: 29 条评论
- **摘要**: Pro*5 订阅用户反馈，5 小时配额在 1 条消息后瞬间归零，与 #28879 类似，涉及 gpt-5.5 配额计算问题。
- **链接**: https://github.com/openai/codex/issues/29955

### 7. #29532 - macOS 下 SQLite 日志仍持续写入（v0.142.0 后）
- **热度**: 22 条评论
- **摘要**: 用户升级至 `rust-v0.142.0` 后，`~/.codex/logs_2.sqlite` 仍持续产生日志。PR #29432 已缓解一部分，但 #29457 修复无效。
- **链接**: https://github.com/openai/codex/issues/29532

### 8. #25744 - macOS 上 MCP 辅助进程泄漏导致 HID 卡顿
- **热度**: 8 条评论
- **摘要**: macOS 长期会话中，Codex 积累了大量未回收的 Computer Use / MCP 子进程（僵尸进程），导致 HID（人机交互）延迟和 WindowServer/TCC 阻塞。
- **链接**: https://github.com/openai/codex/issues/25744

### 9. #26984 - MCP stdio 服务器泄漏 pipe fd 导致 EMFILE
- **热度**: 7 条评论
- **摘要**: MCP stdio 服务器长期运行后，未关闭的 pipe 文件描述符和孤儿进程累积触发 `EMFILE`（文件描述符耗尽），表现为 `Too many open files` 错误。
- **链接**: https://github.com/openai/codex/issues/26984

### 10. #30390 - Windows 桌面端 `ambient_suggestions` 后台消耗 ~70k tokens
- **热度**: 3 条评论（今日最新）
- **摘要**: 用户报告 Windows 版 Codex Desktop 在后台自动生成 `ambient_suggestions` 时，未开启新会话即消耗约 70,000 个 token，导致意外配额消耗。
- **链接**: https://github.com/openai/codex/issues/30390

## 重要 PR 进展（Top 10）

### 1. #30395 - 显示使用额度重置到期细节
- **状态**: OPEN | 作者: jayp-oai
- **内容**: 增加 `rateLimitResetCredits` 的过期时间显示，支持客户端同时获取可用数量和到期日期。回复 #29618。
- **链接**: https://github.com/openai/codex/pull/30395

### 2. #30334 - 记录工具调用和推理时序事件
- **状态**: OPEN | 作者: bolinfest
- **内容**: 在 JSON 日志中增加工具延迟的细粒度信息（区分分派/排队时间与处理时间），便于运维诊断。
- **链接**: https://github.com/openai/codex/pull/30334

### 3. #30269 - 禁用 Rendezvous WebSocket 的 Nagle 算法
- **状态**: OPEN | 作者: richardopenai
- **内容**: 对 exec-server 的 Rendezvous WebSocket 连接禁用 Nagle 算法，降低交互延迟，无需特性标记或灰度。
- **链接**: https://github.com/openai/codex/pull/30269

### 4. #29691 - 在运行时强制执行 Marketplace 源策略
- **状态**: CLOSED | 作者: xl-openai
- **内容**: 企业版支持通过源策略禁用被屏蔽的插件，过滤插件列表/发现/CLI 报告。
- **链接**: https://github.com/openai/codex/pull/29691

### 5. #30291 - 暴露环境信息 RPC
- **状态**: CLOSED | 作者: maxj-oai
- **内容**: 提供 RPC 接口让客户端发现执行环境的 shell 和工作目录，解决跨平台环境选择问题。
- **链接**: https://github.com/openai/codex/pull/30291

### 6. #30292–#30296 - MCP OAuth 支持栈（5 个 PR）
- **状态**: OPEN | 作者: stevenlee-oai
- **内容**: 一系列 PR 组成 **MCP OAuth 序列化与恢复** 功能栈，包含：序列化共享凭据存储 (#30292)、序列化刷新事务 (#30293)、序列化登录/登出 (#30295)、路由 MCP OAuth 恢复 (#30294)、报告凭据漂移 (#30296)。该栈替代了早期的 #29017–#29021。
- **链接**: https://github.com/openai/codex/pull/30292

### 7. #30327 - 稳定合成调用输出 ID
- **状态**: CLOSED | 作者: bolinfest
- **内容**: 修复 `ContextManager::for_prompt` 中合成"中止"输出的 ID 生成逻辑，确保重试和修复时可稳定引用。
- **链接**: https://github.com/openai/codex/pull/30327

### 8. #30384 - 增加 currentTime/read 超时
- **状态**: CLOSED | 作者: rka-oai
- **内容**: 将外部 `currentTime/read` 请求超时从 5 秒提升至 10 秒，应对网络波动。
- **链接**: https://github.com/openai/codex/pull/30384

### 9. #30399 - 非阻塞可观测的启动/MCP/子代理编排（新 Issue/PR）
- **状态**: OPEN | 作者: Nicolas0315
- **内容**: 提议将 Codex 启动、MCP 和子代理编排改为非阻塞且可观测，支持多机工作流。这是一个综合讨论发起，非单一修复。
- **链接**: https://github.com/openai/codex/issues/30399

### 10. #30408 - MCP 服务器进程泄漏（9+ GB RSS）
- **状态**: OPEN | 作者: kkkayye
- **内容**: Codex app-server 每创建一个新线程/对话时，会生成全套 MCP 服务器进程，但线程归档/关闭后不清理，导致内存泄漏累积至 9+ GB。
- **链接**: https://github.com/openai/codex/issues/30408

## 功能需求趋势

1. **速率限制透明度**: 近期 #28879、#29955 等高频 Issue 显示，用户强烈要求平台提供**实时、准确的配额消耗明细**，包括 token 级别、重置时间等。PR #30395 正在回应此需求。

2. **`.codexignore` / 敏感文件排除**: #2847、#24993 等多个 Issue 持续要求引入类似 `.gitignore` 的排除机制，防止敏感文件被 agent 读取或上传到模型。

3. **Linux 桌面应用**: #11023 以 650 个 👍 高居需求榜，社区对 Linux 原生 Codex 桌面应用有强烈期待。

4. **MCP / 子进程生命周期管理**: #25744、#26984、#30408 等 Issue 报告了 MCP 相关进程泄漏，社区对 **可靠、可清理的子进程管理** 有明确需求。

5. **环境配置透明度**: #30291 PR 以及 #30399 表明，社区希望在多机/多环境中拥有**可观测、可配置的执行环境**。

## 开发者关注点

- **配额与计费问题**（最突出）: `gpt-5.5` 模型的配额消耗异常（10-20 倍增加）是当前开发者最高频的痛点，影响 Plus、Pro、Pro*5 各层级用户。社区呼吁紧急回滚或修复。
- **Windows 平台兼容性**: #21863（VS Code 空白面板）、#20570（CreateProcessAsUserW 失败）、#29408（git.exe 卡死）等 Issue 表明 Windows 平台稳定性问题仍较多。
- **后台 token 浪费**: #30390 显示 `ambient_suggestions` 等后台功能无用户感知地消耗大量 token，开发者希望**默认关闭或增加提示**。
- **OAuth 刷新失败**: #27165 指出桌面端启动时从 Keychain 读取过期 token，不发刷新请求直接导致认证失败，影响 MCP 功能。
- **Intel Mac 支持**: #29422 指出 Intel Mac 上 "Attach App Snapshot" 功能完全不可用，因为 Computer Use 服务未包含在 x64 包中。

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

好的，作为专注于AI开发工具的技术分析师，我已根据您提供的GitHub数据，为您生成了2026年6月28日的Gemini CLI社区动态日报。

---

## Gemini CLI 社区动态日报 | 2026-06-28

### 📈 今日速览

今日社区动态聚焦**安全加固**与**Agent行为可靠性**。夜间版 v0.51.0 主要修复了一个安全相关的路径阻断逻辑问题。社区讨论热度集中在 **SubAgent（子代理）报告机制不透明**（如因达到最大轮次而被报告为成功）以及 **Agent任务执行中的范围蔓延**问题，多个相关PR正在被积极修复。

### 🚀 版本发布

#### v0.51.0-nightly.20260628.gae0a3aa7b

- **内容**: 主要是一个安全修复。
- **关键修复**:
    - `fix(security)`: 强制对敏感路径阻断列表和VS Code HITL（人在回路中）功能进行大小写不敏感匹配，增强了安全策略的健壮性。
- **链接**: [查看完整更新日志](https://github.com/google-gemini/gemini-cli/compare/v0.51.0-nightly.20260626.gb14416447...v0.51.0-nightly.20260628.gae0a3aa7b)

### 🔥 社区热点 Issues (Top 10)

1.  **SubAgent恢复后误报成功状态**
    - **Issue**: [#22323](https://github.com/google-gemini/gemini-cli/issues/22323)
    - **重要性**: **极高**。这是一个典型的“虚假安全感”Bug。SubAgent因达到`MAX_TURNS`被中断，却向用户报告`success`和`GOAL`，这完全误导了用户对任务实际完成情况的判断。
    - **社区反应**: 获得 2 个赞，8 条评论，说明该问题已引起维护者和用户的共鸣。

2.  **通用Agent挂起**
    - **Issue**: [#21409](https://github.com/google-gemini/gemini-cli/issues/21409)
    - **重要性**: **极高**。核心Agent功能的严重Bug，导致用户需要等待数小时或取消任务。这是用户日常工作流的阻塞点，影响范围广。
    - **社区反应**: 获得 8 个赞，评论较多，表明这是一个广泛存在的痛点。

3.  **Shell命令执行后卡死**
    - **Issue**: [#25166](https://github.com/google-gemini/gemini-cli/issues/25166)
    - **重要性**: **高**。直接影响用户交互体验的根本性问题。简单命令执行完毕但界面仍显示“等待输入”，破坏了对工具的基本信任。
    - **社区反应**: 3 个赞，4 条评论，用户已多次遇到此问题。

4.  **Shell参数扩展安全策略（相关PR）**
    - **Issue**: [#28175](https://github.com/google-gemini/gemini-cli/issues/28175) (PR)
    - **重要性**: **高**。针对终端安全的重要修复。需要用户确认才能执行带有`$`变量的命令，防止恶意或意外的参数注入，并严格禁止在无交互模式下执行此类命令。
    - **社区反应**: 一个新提出的PR，体现了对安全细节的关注。

5.  **Agent“自我意识”不足，不使用自定义技能**
    - **Issue**: [#21968](https://github.com/google-gemini/gemini-cli/issues/21968)
    - **重要性**: **高**。这关乎Agent的智能水平和工具使用效率。用户花费精力配置的技能和SubAgent，Agent却“视而不见”，导致功能未被充分利用。
    - **社区反应**: 6 条评论，表明用户对Agent决策逻辑的“黑盒”状态感到困惑。

6.  **Agent任务执行范围悄悄扩大**
    - **Issue**: [#28172](https://github.com/google-gemini/gemini-cli/pulls?q=is%3Apr+28172) & [#28171](https://github.com/google-gemini/gemini-cli/pulls?q=is%3Apr+28171) (PRs)
    - **重要性**: **高**。用户要求审查特定代码行，Agent却擅自运行脚本阅读整个文件，这违反了用户意图，降低了可控性。
    - **社区反应**: 这是今天刚被提交的修复PR，表明社区和开发团队正在严肃处理Agent的执行边界问题。

7.  **SubAgent权限问题**
    - **Issue**: [#22093](https://github.com/google-gemini/gemini-cli/issues/22093)
    - **重要性**: **高**。用户明确禁用Agent功能后，升级后SubAgent却开始自动运行。这是严重的配置失效问题，可能带来安全隐患。
    - **社区反应**: 2 条评论，虽然讨论不多，但问题性质严重。

8.  **`bugreport`不包含SubAgent上下文**
    - **Issue**: [#21763](https://github.com/google-gemini/gemini-cli/issues/21763)
    - **重要性**: **中-高**。反馈Bug时，如果错误发生在SubAgent内部，提交的报告却“只字不提”，这给开发者定位和修复问题带来巨大困难。
    - **社区反应**: 2 条评论，是改善用户-开发者协作流程的关键诉求。

9.  **Symlink不被识别为Agent**
    - **Issue**: [#20079](https://github.com/google-gemini/gemini-cli/issues/20079)
    - **重要性**: **中**。这是一个对特定用户群（如使用dotfiles管理工具的用户）影响较大的功能Bug。不支持符号链接限制了配置方式的灵活性。
    - **社区反应**: 4 条评论。

10. **AST感知的文件读取/搜索探索**
    - **Issue**: [#22745](https://github.com/google-gemini/gemini-cli/issues/22745)
    - **重要性**: **中**。这是一个前瞻性的EPIC，旨在通过理解代码结构来提高Agent的“智商”和效率。能减少错误读取、turns（交互轮数）和token消耗，对提升Agent深层理解代码库的能力至关重要。
    - **社区反应**: 7 条评论和 1 个赞，代表了社区对Agent能力升级的长期期待。

### 🛠️ 重要 PR 进展 (Top 10)

1.  **[Open] 修复DNS重绑定绕过SSRF保护**
    - **PR**: [#28181](https://github.com/google-gemini/gemini-cli/pull/28181)
    - **重要性**: **安全-致命**。`web_fetch`工具的SSRF防护存在严重漏洞，会被DNS重绑定攻击绕过。此修复通过异步DNS解析来彻底解决，是目前修复优先级最高的安全补丁。

2.  **[Open] 恢复防御性路径解析**
    - **PR**: [#28180](https://github.com/google-gemini/gemini-cli/pull/28180)
    - **重要性**: **安全-严重**。上一个版本的修复`#27943`被回退后，文件读写相关工具重新暴露在符号连接路径遍历漏洞下。此PR是重新加固文件系统安全的关键步骤。

3.  **[Open] 防止无声的Scope扩展**
    - **PR**: [#28171](https://github.com/google-gemini/gemini-cli/pull/28171) & [#28172](https://github.com/google-gemini/gemini-cli/pull/28172)
    - **重要性**: **Agent行为可靠性**。针对用户反馈的“Agent擅自扩大任务范围”问题，通过修复`mandateConfirm`函数，增加明确指令来防止Agent在未通知用户的情况下切换策略或读取额外文件。

4.  **[Open] 要求Shell参数扩展需确认**
    - **PR**: [#28175](https://github.com/google-gemini/gemini-cli/pull/28175)
    - **重要性**: **安全加固**。在交互模式下，要求用户确认后，脚本才能执行包含`$`的shell命令。在无人值守（YOLO）模式下，直接禁止，有效防止命令注入风险。

5.  **[Closed] MCP OAuth刷新修复**
    - **PR**: [#27889](https://github.com/google-gemini/gemini-cli/pull/27889)
    - **重要性**: **集成健康**。修复了当MCP服务器通过自动发现（没有静态配置`clientId`）时，OAuth令牌刷新失败的问题。确保与外部工具集成的稳定性。

6.  **[Closed] MCP工具Schema标准化**
    - **PR**: [#27888](https://github.com/google-gemini/gemini-cli/pull/27888)
    - **重要性**: **兼容性修复**。一些MCP服务器提供的工具输入Schema不符合标准JSON Schema（缺少根`type: “object”`），导致Vertex AI等严格验证器报错。此修复动态添加`type`，提高了与其他API的兼容性。

7.  **[Closed] 尊重 `.gitignore` 和 `.geminiignore`**
    - **PR**: [#27886](https://github.com/google-gemini/gemini-cli/pull/27886)
    - **重要性**: **用户体验优化**。确保`<session_context>`目录树和主CLI一样遵循忽略规则，避免在会话上下文中暴露本应被忽略的敏感或无关文件。

8.  **[Closed] MCP图片MIME类型识别**
    - **PR**: [#27878](https://github.com/google-gemini/gemini-cli/pull/27878)
    - **重要性**: **跨模型功能修复**。修复了Figma MCP集成返回的WebP图片被错误识别为PNG，导致Gemini API请求失败的问题。通过本地检测文件头来正确识别图片格式。

9.  **[Open] 提升Node.js `google-auth-library`版本**
    - **PR**: [#28065](https://github.com/google-gemini/gemini-cli/pull/28065)
    - **重要性**: **依赖安全性**。跟进上游修复，升级认证库版本以包含一个已修复的Bug，确保Gemini CLI与其他Google Cloud服务的交互稳定安全。

10. **[Open] 新增Eval覆盖率报告命令**
    - **PR**: [#28169](https://github.com/google-gemini/gemini-cli/pull/28169)
    - **重要性**: **QA/DevOps**。新增`eval:coverage`命令，可交叉引用测试用例和内置工具，帮助开发者轻松了解自动化测试覆盖了哪些工具，发现测试盲区。

### 📊 功能需求趋势

- **安全性与沙箱隔离**: 社区高度关注代码执行的安全性。包括防止SSRF、路径遍历、命令注入（`$`变量），以及探索“零依赖操作系统沙箱”来安全地利用模型的Bash亲和性。
- **Agent自主权与可靠性**: 核心矛盾在于Agent“能做”更多事（如调用SubAgent）和用户希望它“做得正确、透明”之间。需求包括：**防止任务范围无声扩大**、**准确报告任务（失败/成功）状态**、**主动使用用户配置的自定义技能**。
- **上下文感知与精细化操作**: 社区期望Agent能更“聪明”地理解代码库，例如通过AST（抽象语法树）来精准定位方法、搜索代码，而非逐行读取全文，从而减少Token消耗和交互轮数。
- **低层级工具稳定性**: 频繁出现的诸如Shell卡死、交互式进程挂起等问题，表明基础工具链的健壮性仍是重中之重。

### 👨‍💻 开发者关注点 (痛点与高频需求)

1.  **“虚假的”成功感**: 开发者明显不满于Agent报告的错误状态。SubAgent超时被中断却报成功，是当前最受诟病的痛点。
2.  **Agent不可预测性**: Agent有时拒绝使用已配置的技能，有时又“自作主张”扩大任务范围。这种不可预测性严重影响开发者的信任感，他们需要更强的指令跟随能力。
3.  **基础但恼人的交互Bug**: Shell命令执行后UI卡死、窗口缩放时的闪烁等问题，虽然不致命，但频繁打断工作流程，带来糟糕的体验。
4.  **调试与排错困难**: 当问题发生在SubAgent中时，`/bug`报告缺乏详细上下文，使开发者难以定位问题根源，严重阻碍了社区贡献和Bug修复流程。
5.  **配置与集成灵活性**: 不支持符号链接、.env文件不可读导致扩展加载失败等小问题，折射出开发者希望工具能更灵活地适应其个性化的工作环境配置。

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI 社区动态日报 | 2026-06-28

## 今日速览

昨日社区活跃度极高，共更新 15 个 Issue 和 3 个 PR。**Windows 兼容性问题集中爆发**：包括 MCP 服务器启动失败（v1.0.66 回归）、复制功能失效、路径错误等。同时，**终端渲染与交互问题**（alt-screen、视觉残留、回滚滚动）成为第二大关注焦点。功能需求方面，社区对**会话生命周期管理**和**上下文记忆能力**的需求呼声渐高。

---

## 版本发布

**无新版本发布。** 当前最新稳定版为 v1.0.66，但已有用户报告回归问题（见 #3958）。

---

## 社区热点 Issues（10 条精选）

1. **[#2165] Ubuntu keychain 支持损坏** 🔥（👍20）
   - **重要性**：高点赞、高影响，影响 Linux 用户核心认证体验。文档与实现不符，`secret-tool` 集成存在两个独立 bug。
   - 🔗 [Issue #2165](https://github.com/github/copilot-cli/issues/2165)

2. **[#1799] 如何禁用 alt-screen 视图？**（👍7）
   - **重要性**：持续高关注。alt-screen 模式引入后导致大量用户不适应，社区期望提供回退选项。
   - 🔗 [Issue #1799](https://github.com/github/copilot-cli/issues/1799)

3. **[#3958] Windows: v1.0.66 启动 MCP 服务器失败**（回归）
   - **重要性**：严重回归。`.bat`/`.cmd` 文件作为 MCP 命令时直接崩溃，影响 Windows 用户启用自定义工具链。
   - 🔗 [Issue #3958](https://github.com/github/copilot-cli/issues/3958)

4. **[#3949] Windows 11 复制失效**
   - **重要性**：基础功能缺失。Copilot 声称已复制到剪贴板，但实际未写入，严重误导用户调试流程。
   - 🔗 [Issue #3949](https://github.com/github/copilot-cli/issues/3949)

5. **[#3964] 软换行复制时空格丢失（修复不完整）**
   - **重要性**：社区测试发现 v1.0.49 修复的 #3666 在 v1.0.65 上仍未完全解决，说明测试覆盖不足。
   - 🔗 [Issue #3964](https://github.com/github/copilot-cli/issues/3964)

6. **[#3959] TUI 中删除文本后出现“幽灵”字符**
   - **重要性**：界面渲染 bug，删除文本后残留字符，影响交互体验，属于低优先级但高频触发的视觉问题。
   - 🔗 [Issue #3959](https://github.com/github/copilot-cli/issues/3959)

7. **[#3957] MBP 触控板无法滚动历史记录**
   - **重要性**：Mac 用户痛点。触控板手势被错误识别为选择历史命令而非滚动窗口。
   - 🔗 [Issue #3957](https://github.com/github/copilot-cli/issues/3957)

8. **[#3962] v1.0.65 完全无法使用**
   - **重要性**：用户报告启动后即卡死或无法正常交互，需紧急排查。
   - 🔗 [Issue #3962](https://github.com/github/copilot-cli/issues/3962)

9. **[#3815] Windows 调试日志路径缺少反斜杠**
   - **重要性**：小但烦人的 UI 错误，复制路径到资源管理器会报错，反映字符串拼接缺乏合法性校验。
   - 🔗 [Issue #3815](https://github.com/github/copilot-cli/issues/3815)

10. **[#3963] 功能请求：显示会话保留/过期日期**
    - **重要性**：社区对会话“莫名其妙被清空”感到困惑，希望透明化会话生命周期管理策略。
    - 🔗 [Issue #3963](https://github.com/github/copilot-cli/issues/3963)

---

## 重要 PR 进展（3 条，仅昨日更新）

1. **[#3928] [开放] 添加 .gitignore 和 settings 配置**
   - **内容**：提升项目模板化与配置标准化。
   - 🔗 [PR #3928](https://github.com/github/copilot-cli/pull/3928)

2. **[#570] [已关闭] 添加 macOS 安装说明到 README.md**
   - **内容**：基于 Copilot 自主生成的 PR，虽已关闭但可能作为自动化生成文档的参考。
   - 🔗 [PR #570](https://github.com/github/copilot-cli/pull/570)

3. **[#3737] [开放] Jigg empire ai**
   - **内容**：功能不明，但标题与摘要暗示可能涉及新 AI 方法探索。
   - 🔗 [PR #3737](https://github.com/github/copilot-cli/pull/3737)

> 注：本日报所述“10 个重要 PR”因数据中仅 3 条有更新，已如实列出全部。

---

## 功能需求趋势

从过去 24 小时 Issues 中提炼出以下社区聚焦方向：

1. **会话生命周期管理**：用户希望看到会话过期日期，明确“何时会被清除”，提升可预测性。
2. **上下文记忆增强**：参考 Claude Code 的 `/btw` 功能，期望 Copilot 在非活跃状态下仍可无侵入查询上下文。
3. **自定义模型提供商**：用户要求使用第三方模型时，配额应走第三方而非 GitHub 配额。
4. **终端 UI 自定义**：alt-screen 模式可配置、输入区域清除、滚动行为优化。

---

## 开发者关注点（痛点与高频需求）

- **痛点第一名：Windows 兼容性崩塌**
  - MCP 服务器因命令格式错误崩溃（#3958）
  - 剪贴板功能完全无效（#3949）
  - 调试路径格式错误无法导航（#3815）

- **痛点第二名：终端交互体验欠佳**
  - 删除文本后残留字符（#3959）
  - Mac 触控板滚动失灵（#3957）
  - 软换行复制空格丢失（#3964）

- **痛点第三名：认证与配置**
  - Linux keychain 故障（#2165）
  - 文档与实际行为不一致

- **高频需求**
  - 恢复传统模式（#1799）
  - 会话过期透明化（#3963）
  - 上下文随时查询（#2778）

---

**总结：** 昨日社区呈现“平台稳定压倒一切”的呼声，Windows 和 Mac 的终端渲染与剪贴板功能需优先修复。功能侧，用户对于会话生命周期和上下文记忆的期待已超越“纯代码补全”，正朝着“持久化 AI 助理”方向演进。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

好的，这是为您生成的 2026-06-28 OpenCode 社区动态日报。

---

# OpenCode 社区动态日报 | 2026-06-28

## 📈 今日速览
今日社区动态呈现出“**问题集中爆发，解决方案密集落地**”的态势。官方与社区贡献者提交了大量 PR，直指近期困扰用户的多个核心 Bug，包括**WSL/Windows 兼容性**、**运行时内存泄漏**和**模型兼容性**。同时，关于 **PayGo 加密货币支付** 和 **llms.txt文档支持** 的呼声极高，反映了社区对平台扩展性的强烈需求。

## 🐛 社区热点 Issues

1.  **[Feature] 提供 llms.txt 及 Markdown 格式文档** (#8816)
    -   **热度**: 💬 15 评论 | 👍 34 点赞
    -   **重要性**: 点赞数最高，说明社区对将 OpenCode 文档以标准格式提供给 AI 解析有强烈需求，期望提升 AI 工具的上下文理解和代码生成精准度。
    -   [查看详情](https://github.com/anomalyco/opencode/issues/8816)

2.  **[Feature] 支持加密货币支付** (#23153)
    -   **热度**: 💬 13 评论 | 👍 24 点赞
    -   **重要性**: 高点赞数与评论数表明，有相当一部分用户希望获得更灵活的支付选项，以绕过传统的信用卡或区域限制。
    -   [查看详情](https://github.com/anomalyco/opencode/issues/23153)

3.  **[Bug] Desktop App 向 WSL 服务器发送 UNC 路径导致所有 bash 工具调用失败** (#19473)
    -   **热度**: 💬 7 评论 | 已提供 **WORKAROUND**
    -   **重要性**: Windows 用户痛点。此问题影响所有使用 WSL 后端的开发者，导致项目无法正常运行。虽已有临时方案，但仍需官方彻底修复。
    -   [查看详情](https://github.com/anomalyco/opencode/issues/19473)

4.  **[Bug] Bun 1.3.14 在 Linux x86_64 上发生 SIGILL 段错误** (#33890)
    -   **热度**: 💬 6 评论 | 👍 5 点赞
    -   **重要性**: 严重的运行时崩溃问题。在特定 CPU (AMD EPYC Zen4) 上触发，导致 TUI 无法启动，对早期采用者和服务器部署影响较大。
    -   [查看详情](https://github.com/anomalyco/opencode/issues/33890)

5.  **[Bug] 服务模式长时间运行后，匿名 JS 堆/交换内存累积** (#33213)
    -   **热度**: 💬 5 评论
    -   **重要性**: 服务器端稳定性问题。内存持续增长至 26.8 GiB 峰值，不符合生产环境的长期稳定运行要求，是 `opencode serve` 用户的关键痛点。
    -   [查看详情](https://github.com/anomalyco/opencode/issues/33213)

6.  **[Bug] 项目对模型暴露的技能集不稳定、不完整** (#34228)
    -   **热度**: 💬 5 评论
    -   **重要性**: 影响 AI 代码生成的核心功能。项目技能作用于模型行为，如果技能集在不同会话间不一致，将导致 AI 行为不可预测，严重影响用户体验。
    -   [查看详情](https://github.com/anomalyco/opencode/issues/34228)

7.  **[Bug] 模型选择在回答问题后静默重置** (#34207)
    -   **热度**: 💬 4 评论
    -   **重要性**: 交互流程中的严重 Bug。用户手动选择的模型在 AI 发问后会被静默切换，意味着用户无法在整个对话中保持对特定模型的控制。
    -   [查看详情](https://github.com/anomalyco/opencode/issues/34207)

8.  **[Bug] 无法调用 GitHub Copilot 中企业添加的第三方模型** (#34030)
    -   **热度**: 💬 4 评论
    -   **重要性**: 企业级用户的关键需求。对于使用 GitHub Copilot Enterprise 的组织，无法使用其定制的私有模型，阻碍了 OpenCode 在企业内部的推广。
    -   [查看详情](https://github.com/anomalyco/opencode/issues/34030)

9.  **[Bug] Desktop 版高 CPU 占用** (#34236)
    -   **热度**: 💬 3 评论 | 最新更新
    -   **重要性**: 资源占用问题，影响用户体验。CPU 占用率高达 30%-50%，相比 CLI 版本异常，可能导致笔记本降频和风扇噪音。
    -   [查看详情](https://github.com/anomalyco/opencode/issues/34236)

10. **[Bug] GLM-5.2 会话因模型尝试查看截图而中断** (#34113)
    -   **热度**: 💬 3 评论
    -   **重要性**: 反映了模型功能与平台功能不匹配的问题。当模型不支持图像输入，但平台技能或系统提示触发了相关操作时，会导致会话错误中断。
    -   [查看详情](https://github.com/anomalyco/opencode/issues/34113)

## 🚀 重要 PR 进展

1.  **[贡献者] feat(app): 增加 agent 工具 (git, format, diagnostics, LSP rename等)** (#34273)
    -   **核心内容**: 新增一套 Agent 工具和子系统，社区贡献者扩展了 OpenCode 的核心能力。
    -   [查看详情](https://github.com/anomalyco/opencode/pull/34273)

2.  **[贡献者] fix(agent): 当模型为 “inherit” 时跳过解析，并修剪空白** (#33202)
    -   **核心内容**: 修复了子代理配置中的一个关键 Bug，当模型设置为`inherit`时会导致解析异常，解决了多个相关 Issue。
    -   [查看详情](https://github.com/anomalyco/opencode/pull/33202)

3.  **[贡献者] fix: 在 message() 管道中添加最终的空内容保护** (#34272)
    -   **核心内容**: 提供一种通用方法，防止模型返回空消息导致下游处理出错，提升了平台的健壮性。
    -   [查看详情](https://github.com/anomalyco/opencode/pull/34272)

4.  **[核心] feat(tui): 添加会话重命名功能** (#34264)
    -   **核心内容**: 端到端实现了会话重命名功能，从 Schema 到 TUI，这是一个用户呼声较高的基础功能。
    -   [查看详情](https://github.com/anomalyco/opencode/pull/34264)

5.  **[核心] feat(tui): 为 V2 会话接入撤销/重做和回滚功能** (#34263)
    -   **核心内容**: 破除了之前“未实现”的占位符，将 V2 会话的撤销、重做和回滚功能真正集成到 TUI 中。
    -   [查看详情](https://github.com/anomalyco/opencode/pull/34263)

6.  **[贡献者] fix(server): 在实例查找前拒绝 foreign 目录提示** (#34256)
    -   **核心内容**: 关键修复。解决了 WSL 路径冲突问题的根源，通过拒绝非本机的目录暗示，防止路径拼接错误。
    -   [查看详情](https://github.com/anomalyco/opencode/pull/34256)

7.  **[贡献者] feat(client): 生成完整的协议客户端** (#34164)
    -   **核心内容**: 自动生成客户端代码，极大地简化了开发者为 OpenCode 编写集成的工作，是 API 展示的重要改进。
    -   [查看详情](https://github.com/anomalyco/opencode/pull/34164)

8.  **[贡献者] fix(tui): 阻止 piped stdin 破坏 UI 和键盘输入** (#34242)
    -   **核心内容**: 修复了 Unix 管道输入导致 TUI 界面混乱和键盘失效的 Bug，解决了多个相关 Issue。
    -   [查看详情](https://github.com/anomalyco/opencode/pull/34242)

9.  **[贡献者] fix(llm): 当插件追加单条系统消息时折叠系统消息** (#34267)
    -   **核心内容**: 修复了系统消息管理逻辑，当插件只添加一条消息时不再进行错误的合并，避免模型配置错误。
    -   [查看详情](https://github.com/anomalyco/opencode/pull/34267)

10. **[贡献者] fix(app): 限定会话页面错误的作用域** (#34254)
    -   **核心内容**: 引入错误边界，防止单个会话加载失败导致整个标签页崩溃，提升了应用的稳定性。
    -   [查看详情](https://github.com/anomalyco/opencode/pull/34254)

## 💡 功能需求趋势
-   **🔌 平台扩展性与集成**: 社区非常关注将 OpenCode 与外部平台集成，例如**支持 Open WebUI** (`#18306`)、**读取 GitHub Copilot 企业第三方模型** (`#34030`) 和使用 **Cloudflare Workers AI** (`#34269`)。
-   **💰 支付与商业模式**: **加密货币支付** (`#23153`) 成为最受关注的功能需求之一，表明社区期待更开放、去中心化的支付体验。
-   **📚 文档智能化**: **提供 llms.txt 格式文档** (`#8816`) 的需求表明，开发者们希望 OpenCode 的文档能更好地被 AI 理解，从而提升“AI 辅助使用 OpenCode”的体验。
-   **🖥️ 跨平台与本地化体验**: **WSL 兼容性**、**Windows ARM64 支持** (`#19130`) 和 **Wayland 粘贴支持** (`#29881`) 等需求频出，反映了用户对原生桌面体验的追求。

## 🔧 开发者关注点
-   **内存泄漏与性能**: 服务器端**内存泄漏** (`#33213`) 和桌面端**高 CPU 占用** (`#34236`) 是当前最突出的稳定性问题，严重影响了长时间使用体验。
-   **模型兼容性与行为**: **模型选择自动回退** (`#34207`)、**模型不支持图像导致会话崩溃** (`#34113`)、**技能集不一致** (`#34228`) 等问题，说明模型与平台功能的交互仍存在不少边界情况。
-   **核心工具链稳定性**: **Bun 运行时 segfault** (`#33890`)、**Shell 工具 SIGTRAP 崩溃** (`#34054`) 表明底层运行时的稳定性仍然是开发者在使用过程中的明显痛点。
-   **路径错误与 WSL**: **UNC 路径** (`#19473`) 和 **路径转换** (`#30895`) 问题是 Windows+WSL 用户的“老大难”，社区期待更彻底的路径处理逻辑。

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi 社区动态日报 | 2026-06-28

## 1. 今日速览

今日社区活跃度极高，大量 Issues 和 PR 在短时间内被创建并迅速关闭（超过20条），展现了核心团队高效的响应能力。重点集中在 **TUI 渲染体验修复**（如滚动、闪烁）、**扩展 API 能力增强**（如成本报告、工具执行）以及 **模型兼容性更新**（如 Together.ai 模型废弃、Azure OpenAI 模型重命名）。此外，一个关于 **不可信第三方包** 的恶意举报引发了社区对安全的关注。

---

## 2. 版本发布

无新版本发布。

---

## 3. 社区热点 Issues

### #5825 [OPEN] Streaming markdown 强制滚动到底部
- **链接**: [Issue #5825](https://github.com/earendil-works/pi/issues/5825)
- **重要性**: 严重影响阅读体验。当启用 `clear on shrink` 设置时，AI 回复的流式 Markdown 内容会强制将视图滚动到底部，导致用户无法回溯阅读内容。
- **社区反应**: 已获34条评论，属于热门讨论。

### #5763 [OPEN]  Provider 吞掉 HTTP 错误体
- **链接**: [Issue #5763](https://github.com/earendil-works/pi/issues/5763)
- **重要性**: 底层架构问题。当 API 代理（如网关）返回非2xx错误时，Pi 的 SDK 会丢弃错误响应体，导致不同 Provider 展现同样晦涩的 `UnknownError`，严重阻碍问题定位。
- **社区反应**: 已标记为“进行中”，并有对应的修复 PR。

### #6129 [CLOSED] 恶意包报告: @hypabolic/pi-hypa
- **链接**: [Issue #6129](https://github.com/earendil-works/pi/issues/6129)
- **重要性**: 安全风险。社区成员举报一个外部扩展包通过不正当手段刷安装量，即使当前无直接恶意代码，但其行为破坏了生态信任。
- **社区反应**: 已迅速关闭处理，体现了项目维护者对生态安全的重视。

### #6131 [CLOSED] 多工具调用时全屏闪烁重绘
- **链接**: [Issue #6131](https://github.com/earendil-works/pi/issues/6131)
- **重要性**: 高影响 Bug。当模型在一次响应中返回多个工具调用时，TUI 界面会频繁闪烁，完全清屏并从上到下重新绘制，严重影响操作连贯性。
- **社区反应**: 已快速关闭，表明可能有简单修复或已排查。

### #6130 [CLOSED] renderCall/renderResult 静默忽略异常
- **链接**: [Issue #6130](https://github.com/earendil-works/pi/issues/6130)
- **重要性**: 调试困难度+1。渲染函数静默降级而不抛出异常，导致开发者花费数小时排查错误的导入问题。
- **社区反应**: 用户情绪痛苦，希望不要“悄悄地失败”。

### #6124 [CLOSED] 天城文输入破坏 UI
- **链接**: [Issue #6124](https://github.com/earendil-works/pi/issues/6124)
- **重要性**: Unicode 兼容性问题。输入例如 `नेटवर्क` 的天城文（常用于印地语、梵语）会导致 TUI 界面显示混乱，这是国际化支持的关键点。
- **社区反应**: 已关闭处理。

### #6105 [CLOSED] 用户输入转义错误
- **链接**: [Issue #6105](https://github.com/earendil-works/pi/issues/6105)
- **重要性**: 核心逻辑 Bug。用户输入 `"\"` 被错误地转义显示为 `""`，影响代码片段和特殊字符交互。
- **社区反应**: 用户已自行排查确认可复现。

### #6132 [CLOSED] 移除 Together.ai 废弃模型
- **链接**: [Issue #6132](https://github.com/earendil-works/pi/issues/6132)
- **重要性**: 模型更新。Together.ai 将在7月10日废弃两款模型，社区及时代理请求更新模型列表并建议替代方案。
- **社区反应**: 快速被处理。

### #6112 [CLOSED] pi install 在无写权限时报告成功
- **链接**: [Issue #6112](https://github.com/earendil-works/pi/issues/6112)
- **重要性**: 用户信任问题。当 `settings.json` 为只读时，`pi install` 显示“已安装”，但命令实际并未注册，造成困惑。
- **社区反应**: 已修复并合并对应 PR。

### #6116 [CLOSED] opencode-go 流式及工具调用忽略“禁止思考”设置
- **链接**: [Issue #6116](https://github.com/earendil-works/pi/issues/6116)
- **重要性**: Provider 兼容性和用户控制权。用户明确关闭思考模式，但模型仍输出推理过程，最终定位为上游（opencode-go gateway）的 Bug。
- **社区反应**: 排查过程清晰，最终归因正确。

---

## 4. 重要 PR 进展

### #5735 [OPEN] fix(coding-agent): 安全推迟扩展重载请求
- **链接**: [PR #5735](https://github.com/earendil-works/pi/pull/5735)
- **内容**: 修复扩展上下文（`ctx.reload()`）的安全性和可用性。该 PR 确保重载操作仅在安全的边界点执行，避免并发问题。

### #5678 [OPEN] 为自定义消息添加 excludeFromContext
- **链接**: [PR #5678](https://github.com/earendil-works/pi/pull/5678)
- **内容**: 允许创建“不进入模型上下文”的自定义消息。此类消息正常渲染，但不会被模型看到，非常适合脚手架、提示词模板或内部调试。

### #6123 [CLOSED] feat(coding-agent): 为 Ctrl+G 添加 externalEditor 设置
- **链接**: [PR #6123](https://github.com/earendil-works/pi/pull/6123)
- **内容**: 应社区请求，新增 `settings.json` 配置项，允许绕过不可变的 `$EDITOR` 环境变量，灵活指定外部编辑器。

### #6119 [CLOSED] feat: 添加 reportUsage API 用于扩展贡献会话成本
- **链接**: [PR #6119](https://github.com/earendil-works/pi/pull/6119)
- **内容**: 新增 API 允许沙箱扩展（如子代理）将自身的 token 消耗和费用信息回传给主会话页脚和 `/session` 命令，使总费用透明化。

### #5832 [OPEN] fix(ai): 透传 Provider HTTP 错误体
- **链接**: [PR #5832](https://github.com/earendil-works/pi/pull/5832)
- **内容**: 针对 Issue #5763 的修复。不再丢弃 Provider 返回的 HTTP 错误体，显示原始错误内容，极大提升调试体验。

### #6115 [OPEN] feat(coding-agent): 添加可配置的聊天区域边距
- **链接**: [PR #6115](https://github.com/earendil-works/pi/pull/6115)
- **内容**: 回应社区对 TUI 布局的讨论，尝试引入配置项来减少或去除聊天区域的边距。这是一个长期的 UI 调整。

### #6099 [CLOSED] 将模型 key 'gpt-5.2-chat-latest' 重命名为 'gpt-5.2-chat'
- **链接**: [PR #6099](https://github.com/earendil-works/pi/pull/6099)
- **内容**: 修正了 Azure OpenAI 模型列表，将不存在的 `gpt-5.2-chat-latest` 更正为正确的 `gpt-5.2-chat` 和 `gpt-5.2`，确保兼容性。

### #6111 [CLOSED] fix(coding-agent): 报告 install/remove 时的设置写入失败
- **链接**: [PR #6111](https://github.com/earendil-works/pi/pull/6111)
- **内容**: 修复了 Issue #6112。当 `settings.json` 无法写入时，`pi install` 和 `pi remove` 将明确报告错误，而非静默失败。

### #6121 [CLOSED] Feat: 允许扩展执行已注册的工具
- **链接**: [PR #6121](https://github.com/earendil-works/pi/pull/6121)
- **内容**: 扩展 API 的重要增强。现在第三方扩展可以调用 Pi 内部已注册的工具（如文件编辑、代码运行等），极大的增强了自动化能力。

### #6120 [CLOSED] Extension API: reportUsage() 
- **链接**: [PR #6120](https://github.com/earendil-works/pi/pull/6120)
- **内容**: 与 #6119 关联，提供了子代理成本报告的基础管道。

---

## 5. 功能需求趋势

从今日的 Issues 和 PR 中可以提炼出以下核心功能方向：

1. **扩展 API 深化**:
   - **工具执行**: 允许扩展调用内部工具（#6121）是最强烈的信号。
   - **成本透明**: 扩展开销回传主会话（#6119, #6120）。
   - **API 的稳定性**: 外部 SDK 用户要求 `createAgentSession` 等 API 使用稳定的索引路径（#6117）。
   - **自定义编辑器**配置（#6123）。

2. **用户界面与体验**:
   - **布局自定义**: 聊天区域间距可配置（#6115）。
   - **滚动与闪烁修复**: 解决流式内容强制滚动和多工具调用闪烁（#5825, #6131）。
   - **国际化支持**: 修复非拉丁字符（如天城文）导致的 UI 破坏（#6124）。

3. **模型支持与兼容**:
   - **跟进上游模型废弃**: 主动更新模型列表（#6132）。
   - **Provider 错误透明化**: 不丢弃网关/HTTP 错误体（#5763, #5832）。
   - **准确模型命名**: 更正 Azure OpenAI 模型 key（#6099）。
   - **支持新型模型功能**: 如 diffusiongemma 的“思考块”渲染（#6128）。

4. **包管理与安全性**:
   - **恶意包检测与响应**: 社区和团队对可疑扩展的敏感度提高（#6129）。
   - **可配置安装参数**: 社区希望为扩展安装过程增加更细致的控制（#6126, #6125）。

---

## 6. 开发者关注点

- **调试之痛**: 错误被静默吞掉（`#6130`）和 Provider 错误体被丢弃（`#5763`）是开发者最头疼的问题之一，他们希望每个错误都能被准确暴露。
- **稳定可靠的包管理**: `pi install` 在无写权限时成功（`#6112`）和恶意包刷量（`#6129`）都表明开发者对扩展生态的可靠性高度敏感。
- **控制权与灵活性**: 开发者希望有更多配置项绕过系统限制（如编辑器环境变量`#6123`），并希望扩展 API 提供更精细的控制（如子代理成本汇报、内部工具调用）。
- **流畅交互体验**: 流式内容的强制滚动（`#5825`）和 UI 闪烁（`#6131`）是最容易被用户感知并报告的 Bug，直接影响日常使用满意度。
- **上游依赖问题**: 多个 Issue 最终定位为上游 Provider 的 Bug（如 `#6116` 的 opencode-go 和 `#4106` 的模型定义），体现了开发者不仅关注 Pi 本身，也关注其对接的整个生态的健壮性。

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

好的，各位开发者朋友，早上好。今天是2026年6月28日，欢迎收看本期Qwen Code社区动态日报。我是你们的技术分析师，让我们一起来看看过去24小时社区里有哪些值得关注的变化。

---

### **1. 今日速览**

Qwen Code 社区在 v0.19.2 正式版发布后，开发热度不减。今日焦点集中在两项核心体验优化上：**一是解决了困扰多用户的大模型输出被默认截断（8K tokens）导致的任务循环失败问题；二是社区开始着手解决“跨设备同步”这一关键痛点，提出了持久化任务清单、团队级记忆等方案。** 此外，`/loop` 后台任务的透明度和可见性也成为讨论热点，多个相关的 Issues 和 PR 正在积极推进中。

### **2. 版本发布**

- **[v0.19.2-nightly.20260628.714513df2]**: 这是一个基于 `release/v0.19.2` 分支的日常快照版本。本次发布主要包含一个功能性修复：
    - **修复**：`web_fetch` 工具在 JSON 解析失败时的回退处理逻辑。([#5660](https://github.com/QwenLM/qwen-code/pull/5660))
    - **其他**：同步了 v0.19.2 正式版的改动。

### **3. 社区热点 Issues（精选 10 条）**

1.  **[[#5920] /rewind记录的parentUuid为null，导致恢复对话时聊天历史丢失](https://github.com/QwenLM/qwen-code/Issue/5920)**
    - **重要性**：这是一个影响会话恢复体验的严重bug。用户发现 `/rewind` 后，除了最后一轮对话，整个历史记录在侧边栏中消失。尽管数据存储在本地，但 `parentUuid` 字段错误地被设为 `null`，导致无法正确重建对话树。这是个 `welcome-pr`，社区新人可以尝试。
    - **状态**：[CLOSED] - 已迅速关闭，问题得到确认或已修复。

2.  **[[#5819] 升级后默认使用高价模型并自动修改配置，导致token浪费](https://github.com/QwenLM/qwen-code/Issue/5819)**
    - **重要性**：**高昂的成本问题**。用户反馈在自动升级后，`setting.json` 中的模型被静默替换为更贵的版本（如 DeepSeek-4 Pro），导致其账户余额耗尽。同时，还发现了简体中文输入被转换为繁体中文输出的问题，额外消耗了token。这直接影响用户的钱包，引发了关于自动升级安全性和成本控制的热烈讨论。
    - **状态**：[CLOSED]

3.  **[[#5942] Anthropic提供商：可避免的prompt-cache未命中导致成本增加](https://github.com/QwenLM/qwen-code/Issue/5942)**
    - **重要性**：**又一个成本优化问题**。该Issue指出，在使用Anthropic协议的后端时，Qwen Code存在两个独立的prompt-cache问题，导致每次请求都会产生大量冗余的cache写入操作，增加了成本。而同样配置的Claude Code则没有此问题。这对使用Anthropic API的用户是一个重要的性能/成本关注点。
    - **状态**：[OPEN]

4.  **[[#5941] 大模型输出时向上滚动滚轮会直接跳到最上方](https://github.com/QwenLM/qwen-code/Issue/5941)**
    - **重要性**：**影响用户体验的UI Bug**。在Windows平台上，模型正在输出流式内容时，用户向上滚动滚轮会触发意外的“跳到最顶部”行为，而非正常的逐行滚动。这是一个高频交互场景下的严重UI Bug。
    - **状态**：[OPEN]

5.  **[[#5836] 创建任务清单时能否指定持久化到项目内以便跨设备同步？](https://github.com/QwenLM/qwen-code/Issue/5836)**
    - **重要性**：**协作与状态同步的核心需求**。用户提出，当前的 `todos`、`plans`、`memories` 都存储在本地 `~/.qwen/` 目录下，不支持Git版本控制，导致切换设备或团队协作时状态丢失。社区强烈呼吁增加“项目内持久化”的选项，例如将任务清单保存到项目仓库的 `.qwen/todos` 目录下。
    - **状态**：[OPEN]

6.  **[[#5867] 新增一个Git共享的“团队”层到自动记忆功能](https://github.com/QwenLM/qwen-code/Issue/5867)**
    - **重要性**：**多人协作的基础设施**。当前自动记忆分为“用户级”和“项目级”，但都是私有的。该Issue提议增加一个“团队”层，记忆可以存储在Git共享目录中（如`docs/memories/`），让整个团队都能受益于累积的上下文知识。
    - **状态**：[CLOSED] - 想法受到关注，可能已进入设计或实现阶段。

7.  **[[#5823] /loop cron任务静默触发，无可见性，模型无法列出或停止自己的定时任务](https://github.com/QwenLM/qwen-code/Issue/5823)**
    - **重要性**：**后台任务管理与安全**。用户发现 `/loop` 创建的cron任务会在后台静默运行，甚至在新会话中自动启动。模型无法看到自己创建了哪些定时任务，也无法停止它们。这严重缺乏透明度和控制权，可能导致不可预期的行为和资源浪费。
    - **状态**：[OPEN]

8.  **[[#5756] 默认8K输出上限截断大输出，导致反复重试失败循环](https://github.com/QwenLM/qwen-code/Issue/5756)**
    - **重要性**：**核心功能缺陷**。这个持续了数天的Issue造成了广泛影响：由于默认的8K tokens输出上限，当模型需要生成大型文件（如Wiki页面）时会被截断，然后系统错误地认为工具调用失败，从而触发无限重试，永远无法完成任务。这在当时是社区的焦点问题。该Issue已被关闭，说明相关修复（如更改默认`max_tokens`行为）已被合并或解决。
    - **状态**：[CLOSED]

9.  **[[#5939] 为高输出模型跳过无意义的max_tokens提升](https://github.com/QwenLM/qwen-code/Issue/5939)**
    - **重要性**：**修复`#5756`后的性能优化**。该Issue是上一条的后续优化。在修复了默认`max_tokens`过低的问题后，对于本身就已支持高输出限制的模型，代码中仍存在不必要的`max_tokens`提升逻辑。此Issue旨在移除这种“无操作”，使代码更简洁高效。
    - **状态**：[OPEN]

10. **[[#5894] 编辑工具的结果摘要被重复追加到后续每个响应中](https://github.com/QwenLM/qwen-code/Issue/5894)**
    - **重要性**：**对话污染Bug**。用户反馈，使用编辑工具修改文件后，“File changed”的差异摘要会持续附加到之后的所有模型回复中，严重污染对话界面。这是一个很影响阅读和使用体验的问题。
    - **状态**：[CLOSED]

### **4. 重要 PR 进展（精选 10 条）**

1.  **[[#5890] feat(loop): 在触发时注入一个.qwen/loop.md任务文件](https://github.com/QwenLM/qwen-code/pull/5890)**
    - **说明**：这是对“`/loop`任务可见性”问题的直接解决方案。通过创建一个 `.qwen/loop.md` 文件，用户可以在循环运行期间随时编辑任务列表，并且模型在每次触发时都会重新读取此文件，实现了动态、可持久的任务管理。

2.  **[[#5928] feat(config): 新增项目本地待办事项持久化设置 `todosDirectory`](https://github.com/QwenLM/qwen-code/pull/5928)**
    - **说明**：与热点Issue [#5836](https://github.com/QwenLM/qwen-code/Issue/5836) 直接对应。此PR增加了配置项，允许将`todos`保存到项目目录下（如`.qwen/todos`），从而支持Git版本控制和跨设备同步。

3.  **[[#5868] feat(core): 添加可配置的自动压缩阈值和Stop钩子上下文使用量](https://github.com/QwenLM/qwen-code/pull/5868)**
    - **说明**：一个重要且高质量的增强。当对话上下文接近模型窗口限制时，该PR允许用户配置一个阈值，自动触发对话压缩（Summarization），避免上下文溢出导致模型“失忆”。同时提供了`Stop`钩子，让用户可以在压缩前保存关键信息。

4.  **[[#5848] feat(ui): 新增 `ui.history.collapsePreviewCount` 设置](https://github.com/QwenLM/qwen-code/pull/5848)**
    - **说明**：优化会话恢复体验。该PR在“折叠历史”功能上增加了新设置，允许用户在恢复一个大会话时，保留最近的N轮对话可见，而折叠其余部分。这样既能快速了解当前上下文，又能避免超长历史带来的视觉负担。

5.  **[[#5946] fix(core): 隔离Anthropic SDK中断监听器泄露](https://github.com/QwenLM/qwen-code/pull/5946)**
    - **说明**：修复一个潜在的**资源泄露问题**。针对Anthropic提供商的SDK，在每次请求时创建一个“子控制器”来监听中断信号，并在请求完成后立即销毁，避免了因监听器堆积导致的内存泄漏或异常回调。

6.  **[[#5945] fix(serve): 拒绝非正数的sessionRecapAwayThresholdMinutes值](https://github.com/QwenLM/qwen-code/pull/5945)**
    - **说明**：健壮性修复。修复了后台服务API允许用户设置无意义（如0或负数）的会话复盘阈值问题，确保用户配置的有效性。

7.  **[[#5856] feat(desktop): 桌面应用中的语音听写功能](https://github.com/QwenLM/qwen-code/pull/5856)**
    - **说明**：将CLI和Web Shell中的 `/voice` 语音交互功能带到了桌面客户端，现在桌面用户也可以通过麦克风进行语音输入，多端体验趋于一致。

8.  **[[#5879] feat(web-shell): 在/mcp对话框中浏览MCP服务器资源](https://github.com/QwenLM/qwen-code/pull/5879)**
    - **说明**：增强Web Shell的MCP功能，使其能与终端UI的MCP资源浏览器功能对齐。用户现在可以在Web端直接浏览MCP服务器提供的资源和提示。

9.  **[[#5835] fix(core): 重新应用提供商安装计划时保留已选模型](https://github.com/QwenLM/qwen-code/pull/5835)**
    - **说明**：一个很贴心的体验修复。以前重新进行提供商认证或刷新Token时，选择的模型会被重置。此PR确保了模型选择在重新配置过程中得以保留，减少了用户的重复操作。

10. **[[#5912] fix(daemon): 跨连接解析ACP权限投票](https://github.com/QwenLM/qwen-code/pull/5912)**
    - **说明**：修复了后台服务中ACP协议的一个权限管理问题。解决了当权限请求通过HTTP流式传输时，回复投票只能在同一连接中才能生效的限制，实现了跨连接的权限响应，使架构更健壮。

### **5. 功能需求趋势**

从过去24小时的Issues和PR中，我们可以清晰地看到社区最关注的三大功能趋势：

- **状态持久化与跨设备同步**: 这是今日最强烈的呼声。用户不再满足于单机工作，他们希望 `todos`、`memories`、`plans` 等关键数据能**受Git版本控制**，以便在不同电脑之间无缝切换工作状态，甚至实现团队共享。相关的PR #5928、Issue #5836、Issue #5867 都是这一趋势的体现。

- **后台任务的可视化与管理**: 随着 `/loop` 等后台自动化功能的上线，用户开始意识到**透明度和控制权的重要性**。他们希望能看到所有正在运行的定时任务，能够中止它们，并能编辑任务的指令。PR #5890 和 Issue #5823 / #5889 直接针对这个问题。

- **成本优化与智能控制**: 一连串关于token浪费、默认输出上限截断、prompt-cache未命中的报告表明，开发者对“成本”高度敏感。他们不仅要求功能强大，更要求Qwen Code能**智能、高效地使用Token**，避免因配置不当或代码缺陷导致无意义的API调用和费用支出。

### **6. 开发者关注点**

- **高优先级Bug修复**: 开发者目前最痛恨的是**“坏了的”核心交互**。例如：
    - 会话历史因`parentUuid`错误而丢失 ([#5920](https://github.com/QwenLM/qwen-code/Issue/5920))
    - 滚动UI在输出时行为异常 ([#5941](https://github.com/QwenLM/qwen-code/Issue/5941))
    - 工具编辑结果污染后续对话 ([#5894](https://github.com/QwenLM/qwen-code/Issue/5894))
    这些问题的共同点是，它们并非功能缺失，而是直接破坏了日常的流畅使用体验，需要开发团队优先修复。

- **“隐形”的自动行为**: 用户对**静默发生的、不受控制的行为**有强烈的反感。例如，静默升级并更换高价模型 ([#5819](https://github.com/QwenLM/qwen-code/Issue/5819))、静默创建和运行后台任务 ([#5823](https://github.com/QwenLM/qwen-code/Issue/5823))。开发者们普遍呼吁，任何涉及资源消耗或配置变更的自动行为，都应该有**明确的提示、确认步骤或关闭选项**。

---
以上是今天的Qwen Code社区动态日报。如果你对某个条目感兴趣，欢迎直接点击链接参与讨论。我们明天见！

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

好的，作为专注于 AI 开发工具的技术分析师，我将根据您提供的 GitHub 数据，生成 2026-06-28 的 DeepSeek TUI 社区动态日报。

---

# DeepSeek TUI 社区动态日报 | 2026-06-28

## 今日速览

项目在 `v0.8.66` 版本发布前夕迎来密集开发冲刺，大量与**缓存命中率、Token消耗、上下文管理**相关的核心性能问题获得极高关注。社区贡献者积极提交 PR，修复了工具调用失败重试、验证器逻辑等多个 Bug，并引入了**插件系统**和**基础提示词可配置化**等重要新功能。开发者对项目性能退化、智能体（Agent）行为失控的反馈尤为集中。

## 版本发布

无新版本发布。当前主要版本线为 `v0.8.66`，大量 PR 正在为该版本的最终发布做准备。

## 社区热点 Issues

挑选了 10 个最受关注的 Issue，反映了社区对性能、稳定性和可用性的核心关切。

1.  **[#1177] 输入缓存命中率太低了**
   - **重要性**: 性能问题，讨论最激烈。用户对比同类工具，指出本项目缓存命中率（约95%+）存在巨大差距，严重影响 API 使用成本和响应速度。
   - **社区反应**: 21条评论，热度极高，明确表达了社区对此性能瓶颈的强烈不满和急切改善需求。
   - **链接**: `Hmbown/CodeWhale Issue #1177`

2.  **[#1120] There still seems to be some problems with cache hits（缓存命中方面似乎还是有些问题）**
   - **重要性**: 持续跟踪 #1177 的同源问题，确认缓存问题在 `v0.8.17` 版本后仍未完全解决。
   - **社区反应**: 用户持续跟进并提供分析思路，开发者正积极寻找导致缓存命中率低的根本原因。
   - **链接**: `Hmbown/CodeWhale Issue #1120`

3.  **[#743] token消耗增大了很多**
   - **重要性**: 直接反映用户成本问题。用户报告半天消耗了4亿 Token，质疑交互请求过于密集，对话信息交互重复，急需优化。
   - **社区反应**: 引发了对交互设计的讨论，用户普遍期望更高效的对话上下文管理机制。
   - **链接**: `Hmbown/CodeWhale Issue #743`

4.  **[#3275] CodeWhale 过度参与代码修改，自问自答并偏离用户意图**
   - **重要性**: 核心体验问题。报告指出 Agent 在无需确认的情况下进入“自循环”，超出用户请求范围，导致代码被误改，严重影响控制感和信任度。
   - **社区反应**: 用户反馈强烈，认为是回归性Bug，破坏了用户对 Agent 行为的预期。
   - **链接**: `Hmbown/CodeWhale Issue #3275`

5.  **[#3568] plan 和 agent 模式混合的问题似乎仍然存在**
   - **重要性**: 关键功能缺陷。用户举出具体实例，证明在“plan”模式下，AI 仍会像“agent”模式一样尝试执行多个文件操作，导致模式混淆，使用体验割裂。
   - **社区反应**: 用户提供了详细的对话记录作为证据，开发者对此问题表示关注，并持续追踪。
   - **链接**: `Hmbown/CodeWhale Issue #3568`

6.  **[#3192] 将其提名为 agentclientprotocol/registry**
   - **重要性**: 集成与生态扩展。用户强烈希望项目能被 **Agent Client Protocol (ACP)** 官方注册表收录，从而能更便捷地与 **Zed** 等支持 ACP 的编辑器集成。
   - **社区反应**: 获得了开发者积极响应，已有相关 PR 提交，是社区呼声最高的功能需求之一。
   - **链接**: `Hmbown/CodeWhale Issue #3192`

7.  **[#3495] 采用 Moraine 作为 CodeWhale 的内存后端（摄取适配器 + MCP 回忆）**
   - **重要性**: 宏伟的功能计划。计划引入第三方记忆系统，实现无损会话持久化、可搜索的 MCP 回忆工具，旨在解决 Agent 长期会话中上下文丢失的问题。
   - **社区反应**: 开发者主导的设计，标志着项目在Agent长期记忆能力上的探索，预期将带来巨大的体验提升。
   - **链接**: `Hmbown/CodeWhale Issue #3495`

8.  **[#528] 缓存最大化的上下文模式：重新读取活动文件而非进行摘要**
   - **重要性**: 性能与上下文管理的激进优化。主张利用 DeepSeek V4 的低成本缓存，直接保留活动文件完整内容而非摘要，避免 Agent 反复读取文件，从而提升效率和准确性。
   - **社区反应**: 开发者提出的设计思路，受到关注，显示了项目在“缓存优先”方向上的探索。
   - **链接**: `Hmbown/CodeWhale Issue #528`

9.  **[#1641] Agent 模式：工具调用失败时的降级策略**
   - **重要性**: 可靠性问题。当依赖外部服务的工具调用失败时，Agent 会陷入死循环，持续重试直至任务失败。社区呼吁提供更智能的降级方案。
   - **社区反应**: 被标记为 `enhancement`，已有相关 PR 开始引入“失败提示”作为第一步，表明开发者正在积极解决此问题。
   - **链接**: `Hmbown/CodeWhale Issue #1641`

10. **[#3638] 暴露主提示词以供更广泛的使用场景使用**
    - **重要性**: 功能灵活性。用户希望将 CodeWhale TUI 应用于文学创作等非软件工程场景，这就需要能够方便地替换或修改系统级的基础提示词（personality/constiute）。
    - **社区反应**: 社区贡献者已提交 PR 实现该功能，展示了项目向通用性 Agent 应用发展的可能性。
    - **链接**: `Hmbown/CodeWhale Issue #3638`

## 重要 PR 进展

社区贡献和开发者修复在今天异常活跃，以下 10 个 PR 涵盖了功能、性能和稳定性方面的关键进展。

1.  **[#3702] feat(acp): 流式传输会话/提示增量** (#3192)
    - **功能**: 核心 ACP 适配器改进。将原本缓冲等待整个回复后才发送的状态更新，改为**流式传输**。这对于 Zed 等编辑器至关重要，能实现**实时、增量式**的 Agent 响应渲染，提升交互体验。
    - **链接**: `Hmbown/CodeWhale PR #3702`

2.  **[#3696] feat(prompts): 允许从配置目录覆盖基础提示词** (#3638)
    - **功能**: 实现了用户强烈要求的功能。现在用户可以**自由替换**系统级基础提示词，将工具从代码开发扩展到文学创作、文档审查等**非软件工程用例**。
    - **链接**: `Hmbown/CodeWhale PR #3696`

3.  **[#3699 / #3692] feat(plugins): 添加轻量级插件系统**
    - **功能**: 引入了全新的**插件系统架构**，支持从文件系统自动发现、注册和管理插件。内置了 `rust-toolkit` 插件作为示例，为未来丰富的生态拓展奠定了基础。
    - **链接**: `Hmbown/CodeWhale PR #3699`

4.  **[#3697] feat(working-set): 缓存最大化的上下文模式** (#528)
    - **功能**: 实现了备受关注的 #528 提议。通过添加一个**可选模式**，使工作集中的活动文件内容能直接注入到提示词中，避免 Agent 反复调用工具读取文件，推动**缓存优先**的上下文管理策略。
    - **链接**: `Hmbown/CodeWhale PR #3697`

5.  **[#3705] fix(engine): 在重复搜索错误后建议直接URL** (#1641)
    - **功能**: 针对 #1641 的改进。当 Agent 重复进行失败的 Web 搜索时，现在会从失败的查询中提取域名，并提示 Agent 是否尝试**直接访问该 URL** 作为降级方案。
    - **链接**: `Hmbown/CodeWhale PR #3705`

6.  **[#3703] fix(engine): 在重复工具错误后提供降级提示** (#1641)
    - **功能**: 另一项解决 #1641 的措施。在 Agent 连续遭遇可恢复的工具错误（如超时、网络问题）后，会追加模型可见的**降级指导提示**，避免其继续执行相同的失败调用。
    - **链接**: `Hmbown/CodeWhale PR #3703`

7.  **[#3701] fix(engine): 为临时工具错误添加降级提示**
    - **功能**: 进一步精细化工具错误处理。专门针对临时的超时、网络请求失败等错误，追加了**模型可见的降级指导**，引导 Agent 切换工具或缩小请求范围。
    - **链接**: `Hmbown/CodeWhale PR #3701`

8.  **[#3700] fix(verifier): 生成 hunt 裁决映射** (#2093)
    - **功能**: 完善验证器逻辑。将验证器对结果的评价（通过/部分通过/失败）与“狩猎”游戏中的裁决（被捕/受伤/逃脱）进行**结构化映射**，增强了目标状态的可读性和逻辑一致性。
    - **链接**: `Hmbown/CodeWhale PR #3700`

9.  **[#3698] feat(acp): 在 session/cancel 上取消进行中的会话/提示** (#3192)
    - **功能**: 修复了 ACP 适配器的一个关键缺陷。现在，当编辑器发送 `session/cancel` 请求时，正在运行的 Agent 会话能被**及时取消**，而不是必须等待当前操作完成，大幅提升了用户对 Agent 的控制。
    - **链接**: `Hmbown/CodeWhale PR #3698`

10. **[#3706 / #3607] 文档、清理与流程改进**
    - **功能**: 包括调整 CI 流程使轻量级 PR 也能保持检查通过、清理废弃 Issue 标签、以及修复贡献指南中的过时路径。这些**基础设施优化**表明项目正更加关注维护的规范性和可持续性。
    - **链接**: `Hmbown/CodeWhale PR #3706`

## 功能需求趋势

从所有活跃 Issues 中，可以提炼出社区关注的几个主要功能方向：

-   **性能与成本优化（核心）**: **缓存命中率**和**Token消耗**是目前压倒性的痛点。大量 Issue 和 PR 都围绕如何“减少输入 Token”、“提高缓存命中率”、“精简提示词”展开，这是决定项目能否被规模采用的关键。
-   **IDE/编辑器深度集成**: 社区强烈期望项目能通过 **Agent Client Protocol (ACP)** 无缝集成到主流编辑器（特别是 **Zed**）中，成为日常开发的一部分。
-   **Agent 行为可控性与可靠性**: 用户对 Agent **“自作主张”**、模式混乱、工具调用失败后死循环等问题反馈强烈，需求主要集中在**行为边界、恢复策略和用户确认机制**上。
-   **多模型/外部服务兼容性**: 用户希望项目不仅能使用本地模型，也能更好地与 `OpenAI Codex`、`ChatGPT OAuth`、以及自定义 API 端点集成，提供更灵活的选择。
-   **上下文与记忆管理**: 开发者正在积极探索“**缓存最大化上下文模式**”和引入外部记忆系统，这表明社区希望 Agent 拥有比传统“对话窗口”更强大、更经济的上下文处理能力。

## 开发者关注点

社区开发者反馈中的痛点和高频需求可以总结为以下几点：

-   **“缓存命中率低”是最大的痛点**: 用户明确表示这是一个**体验和成本的双重灾难**，与同类竞品（如 DeepSeek-Reasonix）的差距巨大，是当前最迫切需要解决的问题。
-   **“Token消耗超预期”引发不满**: 用户对 Token 的消耗速度感到震惊和不安，认为是交互设计缺陷导致的无意义请求和重复上下文，要求开发者从根本上优化对话效率。
-   **“Agent 行为不可控”是最糟糕的体验**: 开发者最担心的莫过于工具失去控制。Agent 在没有明确指令和确认的情况下修改代码或自行问答，严重破坏了信任感和工作流程。
-   **“Plan 和 Agent 模式混淆”造成功能割裂**: 用户希望工具的模式切换能严格遵守规则，当前“Plan”模式仍表现出“Agent”行为的 Bug，让用户感到困惑和沮丧。
-   **“反馈修复的滞后和回归”令人失望**: 一些已被标记为修复的问题（如缓存、模式切换）在后续版本中再次出现，社区成员对此表达了明显的失望情绪，希望开发者在修复bug时能进行更充分的回归测试。

</details>

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*