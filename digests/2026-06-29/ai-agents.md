# OpenClaw 生态日报 2026-06-29

> Issues: 500 | PRs: 500 | 覆盖项目: 13 个 | 生成时间: 2026-06-29 03:52 UTC

- [OpenClaw](https://github.com/openclaw/openclaw)
- [NanoBot](https://github.com/HKUDS/nanobot)
- [Hermes Agent](https://github.com/nousresearch/hermes-agent)
- [PicoClaw](https://github.com/sipeed/picoclaw)
- [NanoClaw](https://github.com/qwibitai/nanoclaw)
- [NullClaw](https://github.com/nullclaw/nullclaw)
- [IronClaw](https://github.com/nearai/ironclaw)
- [LobsterAI](https://github.com/netease-youdao/LobsterAI)
- [TinyClaw](https://github.com/TinyAGI/tinyagi)
- [Moltis](https://github.com/moltis-org/moltis)
- [CoPaw](https://github.com/agentscope-ai/CoPaw)
- [ZeptoClaw](https://github.com/qhkm/zeptoclaw)
- [ZeroClaw](https://github.com/zeroclaw-labs/zeroclaw)

---

## OpenClaw 项目深度报告

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，以下是根据您提供的 OpenClaw 项目 GitHub 数据生成的 2026-06-29 项目动态日报。

---

# OpenClaw 项目动态日报 | 2026-06-29

## 1. 今日速览

今日 OpenClaw 项目社区活动极其活跃，单日 Issue 与 PR 更新总量破千，显示出开发者社区极高的参与度和项目快速的迭代节奏。**项目健康度评估：极佳**。核心焦点集中在 **SQLite 会话存储迁移** 这一架构级重构之上（由 #96625 PR 主导）。同时，针对 Discord 等渠道的会话数据一致性问题、内存与 I/O 边界安全、以及核心工具如 `memory_search` 的稳定性 Bug 修复工作也在密集进行。新版 beta 发布也带来了对 Slack、Mattermost 等渠道的精细化控制能力。

## 2. 版本发布

**新版本：v2026.6.11-beta.2**

- **发布链接**: [openclaw v2026.6.11-beta.2](https://github.com/openclaw/openclaw/releases/tag/v2026.6.11-beta.2)
- **更新亮点**:
    - **更强大的渠道控制**: Slack 中继模式、原生 Mattermost `/oc_queue` 支持，以及按 DM 单独覆盖模型设置，使得渠道操作更易自动化和调优。(PRs #94707, #95546, #95120)
    - **更丰富的操作能力**: (发行说明中 Highlight 部分未完整显示，但通常包含其他关键改进)
- **破坏性变更**: 未明确提及。建议用户在升级前查阅完整的 Release Notes 以确认是否有配置或行为变更。
- **迁移注意事项**: 建议所有用户升级到此最新版本。对于使用了 Slack 或 Mattermost 渠道的用户尤其值得关注。

## 3. 项目进展

今日合并/关闭的 PR 展现了项目在多条战线上的稳健推进：

- **架构核心推进**:
    - **[核心] SQLite 会话存储重构进行中**: 由 #96625 PR (`refactor: flip sessions and transcripts to sqlite storage`) 主导的“路径 3”已合并为唯一的活跃实施路径。这是一个巨大的架构迁移，旨在解决长期存在的 `sessions.json` 无限膨胀、数据一致性问题。该 PR 已完成大部分工作，正在等待作者回应 (status: ⏳ waiting on author)。(#88838 追踪 Issue)
- **Bug 修复与稳定性提升**:
    - **Tlon 渠道修复**: 修复了因 UTF-16 边界截断导致 emoji 显示异常的 Bug，改善用户体验。(#97599)
    - **Bedrock 模型兼容性**: 修复了生成的 Bedrock 模型目录因元数据快照解析失败而被丢弃的问题，确保 AWS 用户能正常使用。(#97644)
    - **文档附件处理**: 修复了通过 Telegram 发送的非图片文件（如 PDF）无法被 Agent 读取的问题，提升了实用性。(#97647)
    - **OpenRouter 兼容性**: 修复了 DeepSeek V4 模型请求体因嵌套的 `reasoning` 字段导致被 OpenRouter 拒绝的问题。(#97309)
- **内存安全专项治理**: 项目似乎正在进行一轮针对“无界读取”导致 OOM 风险的专项治理。今日合并或活跃的 PR 包括了对 **Matrix** 响应 (#97547)、**xAI** 视频生成 (#96903)、**Mistral** 流式响应 (#97648) 以及 **CLI** 视频下载 (#97549) 的内存边界保护。这表明项目正在积极加固自身以防范资源耗尽攻击和意外崩溃。
- **新的功能/修复 PR**: 如 `flushPendingToolResults` 延后执行 (#97646) 和 Discord 回复中的快照冲突修复 (#97642) 等，均在今日被提出，标志着项目对新出现问题的快速响应。

## 4. 社区热点

今日社区讨论的核心围绕数据一致性与 Session 管理的稳定性，以下几个 Issue 引发了广泛讨论：

1.  **Issue #75: [Linux/Windows Clawdbot Apps](https://github.com/openclaw/openclaw/issues/75)**
    - **热度**: 评论 110，👍 81
    - **分析**: 这是一个从今年年初持续至今的长期热点，要求为 Linux 和 Windows 平台提供原生桌面应用。该项目已有一个 GTK 原生 Linux 应用的 PR (#59859) 在等待审核。该 Issue 拥有极高的社区关注度，是用户最迫切需求之一。

2.  **Issue #88838: [Track core session/transcript SQLite migration via accessor seam](https://github.com/openclaw/openclaw/issues/88838)**
    - **热度**: 评论 36
    - **分析**: 作为今日核心重构工作（#96625）的追踪 Issue，它本身就是社区开发者和核心贡献者关注的焦点。最新评论确认了“路径 3”整合及 #96625 为唯一活跃 PR，标志着项目在解决“session bloat”这个老大难问题上取得了决定性进展。

3.  **Issue #77598: [Track live dev agent behavior and trajectory](https://github.com/openclaw/openclaw/issues/77598)**
    - **热度**: 评论 22
    - **分析**: 该项目持续追踪内部开发人员 Agent 的行为轨迹，反映了项目对自身 AI Agent 行为的自省与监控能力，虽然评论数不多，但体现了项目高标准的质量文化。

4.  **Issue #88312: [Bug: Codex app-server turn-completion stall returns](https://github.com/openclaw/openclaw/issues/88312)**
    - **热度**: 评论 18，👍 4
    - **分析**: 一个关键的回归 Bug，导致 Codex 应用服务器在回合完成时卡死。社区对该问题非常关注，因为它直接影响 Core Agent 的可靠性。该问题的修复进展将直接影响用户对 Agent 稳定性的信心。

## 5. Bug 与稳定性

按严重程度排列，今日报告的亟待解决的关键 Bug：

- **P1 级别**:
    - **Session 写锁超时**: [#86538](https://github.com/openclaw/openclaw/issues/86538) - `Session write-lock timeouts block subagent delivery lanes`。此问题影响子Agent消息投递，是会话状态的严重Bug。
    - **Codex 回合完成卡死二次回归**: [#88312](https://github.com/openclaw/openclaw/issues/88312) - 修复过的问题再次出现，严重影响Codex服务稳定性。已有相关PR方案，但未关闭。
    - **Isolated cron 持续失败**: [#91363](https://github.com/openclaw/openclaw/issues/91363) - 独立的cron任务在 `model-call-started` 阶段持续报错，影响自动化流程。
    - **代理失效导致级联失败**: [#80040](https://github.com/openclaw/openclaw/issues/80040) - OAuth失效、模型切换导致的多重故障，用户体验极差。
    - **Node v26兼容性问题**: [#79752](https://github.com/openclaw/openclaw/issues/79752) - Discord等HTTP接口因gzip解压失败（macOS + Node v26）而报错。这是一个影响广泛的环境兼容性Bug。
    - **`memory_search` 索引重建失败**: [#91592](https://github.com/openclaw/openclaw/issues/91592) - 强制重建内存索引后，scopeHash不匹配，导致搜索功能完全失效。

- **P2/P3 级别**:
    - **会话/Transcript文件无限增长**: [#55334](https://github.com/openclaw/openclaw/issues/55334), [#45718](https://github.com/openclaw/openclaw/issues/45718) - 此类资源泄漏问题被归类为P1/P2，是SQLite迁移的核心目标之一。
    - **插件静默失败**: [#78301](https://github.com/openclaw/openclaw/issues/78301) - 插件加载器对无效合约的静默处理导致大量调试时间浪费。
    - **WebChat 消息渲染丢失**: [#77136](https://github.com/openclaw/openclaw/issues/77136) - WebChat客户端部分消息不显示，极大影响使用体验。

## 6. 功能请求与路线图信号

- **原生桌面应用**: 对 **Linux/Windows Clawdbot Apps** (#75) 的呼声依然最高，且已有相关的 GTK PR (#59859)。这很可能被纳入下一阶段的路线图。
- **网关无AI模式**: [#86881](https://github.com/openclaw/openclaw/issues/86881) - 请求提供一个不包含AI引擎的“轻量级网关模式”，用于无模型的确定性部署场景。这反映了用户对网关组件模块化、灵活性的需求。
- **i18n 支持**: [#79458](https://github.com/openclaw/openclaw/issues/79458), [#79034](https://github.com/openclaw/openclaw/issues/79034) - 对命令描述和UI元数据的本地化需求持续存在，表明项目非英语用户群体的增长和对国际化体验提升的期望。
- **渠道功能扩展**: 对 Telegram bot-to-bot/guest-bot 模式的支持 (#79077) 和对 Discord 频道不加载的Bug修复 (#77930)，显示社区对即时通讯渠道深度集成的迫切需求。

## 7. 用户反馈摘要

- **核心痛点**: `sessions.json` 无限制增长导致 OOM 和性能问题（#55334），是用户反馈最多、也最痛苦的长期Bug。SQLite迁移 (PR #96625) 是对此诉求的直接回应。
- **稳定性担忧**: Codex 回合完成卡死的回归问题 (#88312) 引发了部分用户对核心 AI Agent 稳定性的担忧。
- **多平台支持**: 对 Linux/Windows 原生应用的呼声（#75）反映了用户希望在不同操作系统上获得一致和深度集成的使用体验，而非仅仅依赖 Web 或 TUI。
- **环境兼容性**: macOS + Node v26 组合下的 gzip 解压问题（#79752）提醒项目需要加强对新兴运行时的测试覆盖。

## 8. 待处理积压

以下为长期存在、评论数高但尚未有确定解决路径的关键 Issue，提醒维护者关注：

1.  **[长期热点] Issue #75 | [enhancement] Linux/Windows Clawdbot Apps**: 已存在 6 个月，社区呼声极高，相关性 PR #59859 也在积压等待。亟需维护者就产品方向给出明确回应。
    - 链接: [openclaw/openclaw Issue #75](https://github.com/openclaw/openclaw/issues/75)

2.  **[高优先级] Issue #55334 | [perf] sessions.json unbounded growth**: 虽然今日有重大进展（#96625 PR），但此 Issue 的关闭应被视为里程碑事件。建议在 SQLite 迁移完成后立即关闭。
    - 链接: [openclaw/openclaw Issue #55334](https://github.com/openclaw/openclaw/issues/55334)

3.  **[安全/P1] Issue #74484 | [Gateway pairing scope deadlock](https://github.com/openclaw/openclaw/issues/74484)**: 一个影响 CLI 核心权限管理的权限死锁问题，自 4 月 29 日起未有突破性进展，存在安全隐患。

4.  **[重要] Issue #49104 | [telegram] HTML parse_mode silently truncates responses**: 影响 Telegram 频道消息渲染的 Bug，从 3 月就已存在。虽然不是 Crash，但对用户体验有直接影响。
    - 链接: [openclaw/openclaw Issue #49104](https://github.com/openclaw/openclaw/issues/49104)

---

---

## 横向生态对比

好的，作为资深技术分析师，以下是根据您提供的2026年6月29日各项目动态数据，生成的横向对比分析报告。

---

## AI智能体与个人AI助手开源生态横向对比分析报告 (2026-06-29)

---

### 1. 生态全景

今日，个人AI助手/自主智能体开源生态呈现出 **“核心项目极度活跃，生态分化加剧”** 的态势。以 **OpenClaw** 和 **ZeroClaw** 为代表的旗舰项目正进行大规模架构重构（如SQLite会话存储、WASM插件系统），社区参与度和代码迭代速度达到顶峰。与此同时，**NanoBot**、**Hermes Agent** 等项目则在稳定性、安全性及特定平台（如Windows、CJK输入法）体验上深耕，体现了各自的差异化竞争策略。然而，部分小型或专注硬件的项目（如 **NullClaw**、**ZeptoClaw**）活动停滞，生态的马太效应愈发明显。**安全加固**和**上下文窗口（Context Window）优化**成为多个项目的共同攻关焦点。

### 2. 各项目活跃度对比

| 项目名称 | 今日活跃度 | Issues 更新数* | PR 更新数* | 版本发布 | 健康度评估 | 核心关键词 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | **极高** | ~100 | ~100 | 是 (v2026.6.11-beta.2) | 极佳 | 架构重构、安全性、性能 |
| **NanoBot** | **极高** | 6 (5活跃) | 25 (11已合并) | 否 | 优秀 | 上下文缓存、稳定性、WebUI |
| **Hermes Agent** | **极高** | 43 (新/活跃) | 39 (新/待合并) | 否 | 良好 | 安全加固、UI Bug、CJK输入法 |
| **IronClaw** | **高** | 3 | 41 (17已合并) | 否 | 良好 | Reborn架构、测试框架、Slack集成 |
| **CoPaw** | **高** | 35 | 35 (含合并) | 否 | 良好 | 插件兼容性、Agent循环、模型兼容 |
| **PicoClaw** | **低** | 0 (1已关闭) | 0 (1待合并) | 否 | 稳定 | 图像压缩、Simplex通道 |
| **NanoClaw** | **中上** | 0 | 6 (1已合并) | 否 | 良好 | 安全修复、平台适配器 |
| **LobsterAI** | **中** | 1 (新) + 4 (已关闭) | 4 (已关闭) | 否 | 良好 | 兼容性、技能管理、Memory Search |
| **Moltis** | **温和** | 1 | 2 (待合并) | 否 | 稳定 | 性能优化、构建体积、Apple兼容 |
| **ZeroClaw** | **极高** | 50 | 50 | 否 | 良好 | 供应商兼容、WASM插件、ACP协议 |
| **NullClaw** | **低** | 1 (已关闭) | 0 | 否 | 待关注 | 硬件适配、维护静默 |
| **TinyClaw** | 无活动 | 0 | 0 | 否 | 停滞 | - |
| **ZeptoClaw** | 无活动 | 0 | 0 | 否 | 停滞 | - |

*注：Issues/PR更新数指过去24小时内被创建、评论、或变更状态的议题/拉取请求总计。*

### 3. OpenClaw 在生态中的定位

- **优势与社区规模**: **OpenClaw** 今日的单日PR/Issue更新量破千，是其他任何项目无法比拟的，其社区规模与活跃度在整个生态中处于**压倒性领先地位**。其版本发布频率（v2026.6.11-beta.2）和庞大的功能集（Slack/Mattermost深度集成、渠道级模型覆盖）标志着它是一个功能全面、迭代极快的“航母级”项目。
- **技术路线差异**: OpenClaw 正在进行**SQLite会话存储**的架构级重构，旨在解决 `sessions.json` 无限膨胀这个P1级长期痛点，这是生态内极具前瞻性的工程决策。相比之下，**ZeroClaw** 则通过**WASM插件系统**和**ACP协议**来扩展能力边界，强调了可扩展性和标准互操作性。
- **定位**: **OpenClaw** 是生态的“锚点”和“风向标”，其动态直接反映了主流个人AI智能体平台的发展方向。它的成功重构将极大影响其他项目在数据一致性、长会话管理方面的设计。但这也意味着其复杂度高，对新用户和特定平台的深度优化（如Hermes在CJK输入法的打磨）可能不如专门化项目。

### 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求/体现 |
| :--- | :--- | :--- |
| **上下文窗口优化** | **OpenClaw**, **ZeroClaw**, **NanoBot** | ZeroClaw (default 32k budget exceeded)，NanoBot (context prefix caching失效)，OpenClaw (memory_search索引失效)。这是所有项目的核心性能痛点。 |
| **安全与资源隔离** | **Hermes Agent**, **NanoClaw**, **OpenClaw** | Hermes (符号链接、子进程泄露风险)，NanoClaw (CWE-59容器逃逸)，OpenClaw (无界读取OOM)。容器化、沙箱化和路径检查成为安全标配。 |
| **平台/UI体验** | **Hermes Agent**, **NanoBot**, **CoPaw** | Hermes (Windows闪烁、CJK输入法)，NanoBot (WebUI重启卡死)，CoPaw (日志过多)。桌面端和Web前端的精细化打磨是提升用户留存的关键。 |
| **标准协议支持** | **ZeroClaw**, **IronClaw**, **PicoClaw** | ZeroClaw (ACP多选提讯)，IronClaw (Slack配对协议)，PicoClaw (Simplex通道)。行业正积极拥抱标准化协议以促进互操作性。 |
| **降级/可替代性** | **LobsterAI**, **CoPaw** | LobsterAI (Memory Search provider锁定)，CoPaw (模型自动降级)。用户对服务单点故障（如OpenAI API 429）的容忍度在降低，对多供应商、本地化备选方案的需求强烈。 |

### 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
| :--- | :--- | :--- | :--- |
| **OpenClaw** | 全功能、高可扩展性 | 高级开发者、企业级用户 | 强中心化路由、外挂式插件、SQLite持久化迁移 |
| **ZeroClaw** | 模块化、开放性、标准互操作 | 开发者、平台集成方 | 解耦的网关、WASM运行时、ACP协议 |
| **NanoBot** | 轻量、易用性、社交集成 | 个人用户、社交媒体工作者 | 强调子代理（Subagent）和多模型弹性 |
| **Hermes Agent** | 开发者桌面体验、代码生成 | 专业开发者 | 高度绑定桌面IDE体验、强调终端任务执行 |
| **CoPaw** | 开放平台、合作伙伴集成 | 企业级用户、第三方开发者 | 突出插件生态、组织级管道、复杂的权限模型 |

### 6. 社区热度与成熟度

- **快速迭代阶段**: **OpenClaw** 和 **ZeroClaw** 处于最激烈的功能开发和架构重构期，代码变动频繁，社区参与度最高，但也伴随着大量的回归Bug（如Codex卡死、供应商兼容性）。
- **质量巩固阶段**: **Hermes Agent** 和 **NanoBot** 今日的重点在于修复长期存在的Bug（IME、上下文缓存）和进行安全加固，而非引入全新架构，表明它们正在从“做加法”转向“做减法”和“做精细”。
- **稳定成熟阶段**: **PicoClaw**、**Moltis**、**NanoClaw** 等项目的活跃度较低，仅处理个别Issue和PR，核心功能稳定，处于微创新和维护状态。
- **停滞风险阶段**: **NullClaw**、**TinyClaw**、**ZeptoClaw** 几乎无任何活动，社区健康度堪忧，需要关注其长期存活性。

### 7. 值得关注的趋势信号

1.  **“确定性”与“持久性”的呼声高涨**: 从 **Hermes Agent** 的“确定性工作流引擎”请求，到 **OpenClaw** 的SQLite迁移，再到 **IronClaw** 的测试框架强化，社区对AI智能体**行为的可预测性**和**状态的持久性**提出了极高要求。开发者不再满足于“黑盒”智能，而是要求AI Agent像传统软件一样可测试、可审计、可恢复。
2.  **从“聊天”到“工作”的范式转变**: 用户不再仅仅将AI当做聊天机器人。无论是 **LobsterAI** 的定时任务UI升级，还是 **NanoBot** 的A2A对等委托，都表明用户希望智能体能**融入现有工作流**，成为可管理、可编排的生产力工具。这意味着“出错后的干预”和“非打断式交互”能力将变得至关重要。
3.  **开源生态的“强基工程”**: 今天大量项目涌入的**安全修复**（路径穿越、容器逃逸、子进程泄露）和**性能优化**（上下文窗口、批处理）表明，AI智能体开源社区正在经历一个从“功能堆砌”到“工程科学”的理性回归。对于AI智能体开发者而言，这意味着**部署、运维、信任**的成本将成为衡量项目价值的关键差异化因素，而非单纯的功能数量。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，我已根据您提供的 NanoBot GitHub 数据，生成了以下项目动态日报。

---

## NanoBot 项目动态日报 | 2026-06-29

### 1. 今日速览

NanoBot 项目今日活跃度**极高**，社区协作与代码贡献均达到近期高峰。过去24小时内，有 **25 个 Pull Request** 被提交或更新，其中 **11 个已成功合并/关闭**，显示了核心团队对关键 Bug 和社区 PR 的快速响应。同时，**6 个 Issues** 被更新，其中 **5 个为活跃讨论**，社区围绕上下文缓存失效、语音输出等核心体验提出了高质量反馈。尽管今日无新版本发布，但项目在**上下文管理、安全性、子代理能力**等方面取得了显著的技术进展，主分支的健康度良好。

### 2. 版本发布

*   **无新版本发布。** 但大量已合并的 PR 表明下一个版本将包含一系列重要改进。

### 3. 项目进展 (重要合并/关闭的 PR)

以下 PR 通过合并/关闭，显著推进了项目的功能性和稳定性：

*   **修复核心 Bug：上下文缓存失效 (#4222)**
    *   **[已合并] PR #4568** ([链接](https://github.com/HKUDS/nanobot/pull/4568)): 由 `findshan` 贡献，解决了 `max_messages` 截断机制导致的前缀/提示缓存持续失效的问题。通过“块对齐”的重放窗口驱逐策略，保持了缓存热度，对于长对话和多轮交互的性能提升至关重要。*（这是对 Issue #4222 的核心修复）*

*   **强化稳定性：工具调用健壮性**
    *   **[已合并] PR #4510** ([链接](https://github.com/HKUDS/nanobot/pull/4510)): 由 `m11y` 贡献，修复了 LLM 返回格式错误的工具调用（如缺失名称）时可能导致崩溃的问题。
    *   **[已合并] PR #4569** ([链接](https://github.com/HKUDS/nanobot/pull/4569)): 由 `m11y` 贡献，进一步强化了对上游中继服务返回的畸形工具调用响应的处理，提升了与第三方服务的兼容性。

*   **提升用户体验：WebUI**
    *   **[已合并] PR #4565** ([链接](https://github.com/HKUDS/nanobot/pull/4565)): 由 `axelray-dev` 贡献，修复了 Issue #4500 中 WebUI 在重启后界面卡在“处理中”状态以及停止按钮失灵的问题，显著改善了用户交互体验。

*   **扩展功能：MCP 工具 & 技能管理**
    *   **[已合并] PR #4542** ([链接](https://github.com/HKUDS/nanobot/pull/4542)): 由 `codedragoncom` 贡献，MCP 工具现在可以返回图像内容作为工件（Artifact），而非无意义的 Base64 字符串，使得图像生成/处理类 MCP 工具真正可用。
    *   **[已合并] PR #4504** ([链接](https://github.com/HKUDS/nanobot/pull/4504)): 由 `goodtiding5` 贡献，支持将技能（Skill）文件放在子目录中组织，解决了技能过多时的目录管理混乱问题。

**项目里程碑评价：** 今日的修复和功能合并，标志着项目在**底层稳定性（上下文管理、工具调用）** 和**表层用户体验（WebUI修复、技能管理）** 上均迈出了坚实的一步，项目正从功能完善期向体验打磨期过渡。

### 4. 社区热点

*   **【热点 Bug】 #4222 - [Bug] 上下文前缀/提示缓存持续失效** ([链接](https://github.com/HKUDS/nanobot/issues/4222))
    *   **热度：** 评论 3，并有专门的修复 PR (#4568) 合入。
    *   **分析：** 这是社区开发者反复遇到的性能痛点。用户 `imkuang` 精准地指出了 `max_messages` 截断和微压缩（microcompact）两个机制如何导致每次对话都使缓存失效，大大增加了延迟和成本。该问题引起开发者强烈共鸣，并迅速推动了修复，体现了社区对项目性能优化的高关注度。

*   **【热点功能】 #4010 - [Feature] 文本转语音 / 语音输出支持** ([链接](https://github.com/HKUDS/nanobot/issues/4010))
    *   **热度：** 评论 2，获得 2 个 👍。
    *   **分析：** 用户 `olgagaga` 提出，NanoBot 目前已支持语音输入，但无法“说话”。这个请求旨在闭环语音交互体验，尤其对于本地语音类渠道（如 Telegram 语音消息）意义重大。该诉求清晰且推动力强，是项目从“全能文本助手”走向“多模态交互助手”的关键一步。

### 5. Bug 与稳定性

| 严重程度 | 问题描述 | Issue 链接 | Fix PR 状态 |
| :--- | :--- | :--- | :--- |
| **高** | **上下文缓存持续失效 (#4222)**：`max_messages` 截断机制破坏前缀缓存，导致性能和成本问题。 | [Issue #4222](https://github.com/HKUDS/nanobot/issues/4222) | **已合并** ([#4568](https://github.com/HKUDS/nanobot/pull/4568)) |
| **中** | **WebUI 重启后卡住 (#4500)**：自重启导致 WebUI 界面停留“处理”状态，停止按钮失效。 | [Issue #4500](https://github.com/HKUDS/nanobot/issues/4500) | **已合并** ([#4565](https://github.com/HKUDS/nanobot/pull/4565)) |
| **中** | **安全绕过风险 (#4521)**：`exec.allowPatterns` 的 `re.search()` 方法可以被链式命令绕过。 | 由 PR [#4562](https://github.com/HKUDS/nanobot/pull/4562) 提及 | **待合并** ([#4562](https://github.com/HKUDS/nanobot/pull/4562)) |
| **低** | **微信渠道流式输出问题**：`WeixinConfig` 缺少 `streaming` 字段导致非流式API被强制使用，无法复现问题。 | 由 PR [#4567](https://github.com/HKUDS/nanobot/pull/4567) 提及 | **待合并** ([#4567](https://github.com/HKUDS/nanobot/pull/4567)) |

**总结：** 今日报告的高优先级 Bug (#4222, #4500) 均已得到修复并合并，项目稳定性提升显著。安全相关的修复（#4562）正在进行中。

### 6. 功能请求与路线图信号

以下功能请求得到了社区积极响应，并已有初步的 PR 实现，很可能被纳入下一个版本：

*   **子代理模型预设覆盖 (Subagent Model Preset)**
    *   **请求：** Issue #4231 (由 PR #4570 关联)。允许 `spawn` 命令为子代理指定不同的模型预设，而非始终继承父代理的模型。
    *   **PR 进展：** [PR #4570](https://github.com/HKUDS/nanobot/pull/4570) (待合并) 和 [PR #4291](https://github.com/HKUDS/nanobot/pull/4291) (待合并) 均实现了此功能，可能会竞争合并。

*   **原生 A2A (Agent-to-Agent) 对等委托**
    *   **请求：** Issue #4179 (由 PR #4571 部分实现)。让 NanoBot 支持复杂的工作流，如 Supervisor -> Researcher -> Writer。
    *   **PR 进展：** [PR #4571](https://github.com/HKUDS/nanobot/pull/4571) (待合并) 实现了原生 A2A 机制，是架构上的重要扩展。

*   **减少上下文使用，降低成本**
    *   **请求：** 多个 Issue 提及成本优化。
    *   **PR 进展：** [PR #4581](https://github.com/HKUDS/nanobot/pull/4581) (待合并) 直接针对此需求，通过压缩子代理消息等方式减少输入令牌，目前仍在讨论中。

### 7. 用户反馈摘要

*   **负面/痛点：**
    *   **性能问题：** 用户 `imkuang` 明确反馈了由`max_messages`机制引起的性能问题，称其“continuously invalidate prefix/prompt caching”，导致每次对话都产生额外开销。
    *   **WebUI 体验：** 用户 `zpljd258` 报告了自重启后 WebUI 界面卡死、停止按钮无效的问题，严重影响了单次使用体验。
    *   **安全性担忧：** 用户 `michaelxer` 通过 PR #4562 暴露了 `exec.allowPatterns` 的安全绕过漏洞，这是一个潜在的严重安全隐患。

*   **正面/驱动：**
    *   **功能请求强烈：** 用户 `olgagaga` 对“语音输出”功能的诉求清晰且获得了社区共鸣（👍: 2），用户 `3L1AS` 明确提出了 WebUI 的体验优化请求（时间戳显示、导出Markdown）。
    *   **开发者友好：** 用户 `HaoyangSunMartin` 请求对 conda 等虚拟环境的更好支持，表明该项目正在被期望用于更复杂的开发环境下。
    *   **组群聊天痛点：** 用户 `morandot` 指出了在群聊场景下消息触发的痛点，并提供了详细的使用场景描述，表明项目正被实际应用于真实的多用户协作环境。

### 8. 待处理积压

以下 Issue 或 PR 处于“开放”状态，且更新较早或缺少维护者反馈，建议项目维护者给予关注：

*   **Issue #3938** ([链接](https://github.com/HKUDS/nanobot/issues/3938)): **[增强] 为群聊频道添加消息缓冲/去抖功能**。
    *   **状态：** 开放，上次更新时间 2026-06-28，仅1条评论。
    *   **风险：** 这是一个针对组群聊天场景的核心优化请求，被长期搁置。随着项目在其他社交渠道（如微信）的支持增强，此需求会变得更加迫切。缺少维护者回复可能导致用户失望。

*   **PR #4192** ([链接](https://github.com/HKUDS/nanobot/pull/4192)): **[功能] 允许子代理继承 MCP 工具**。
    *   **状态：** 开放，上次更新时间 2026-06-29，创建于 2026-06-04。
    *   **风险：** 这是一个非常有价值的增强，能够极大地扩展子代理的能力边界。然而它已经待合并超过三周，可能因为与 #4291 / #4570 的重叠或冲突而被搁置。维护者应明确其优先级别和合并计划，避免开发者白费功夫。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，我将根据您提供的Hermes Agent (NousResearch/hermes-agent) GitHub数据，为您生成2026年6月29日的项目动态日报。

---

# Hermes Agent 项目动态日报 | 2026年6月29日

## 1. 今日速览

今日项目社区活跃度“极高”，共收到 `100` 条议题（Issues）和拉取请求（PRs）更新。其中新开/活跃议题 `43` 条，新开/待合并 PRs `39` 条，显示社区贡献热情高涨。核心动态集中在 **Windows桌面应用的UI闪屏** 和 **中文输入法兼容性** 等长期顽疾上，同时安全相关的 PR 合并显著提升了项目边界安全。值得注意的是，今天没有新版本发布，但针对LM Studio集成和桌面端终端持久化等用户体验改进正在积极推进中。

## 2. 版本发布

今日无新版本发布。

## 3. 项目进展

今日共有 `11` 个 PR 被合并或关闭，主要集中在安全加固和核心Bug修复，项目整体健壮性得到显著提升。

- **安全防线加固 (P1/P2)**: 今日合并了多个由社区贡献者（@teknium1 等）从历史PR中抢救并提交至 `main` 分支的安全修复，包括：
    - `#54563 fix(agent): limit .hermes.md parent walk to git repos only`: 修复了 `.hermes.md` 文件在共享系统上的跨用户提示注入风险。
    - `#54569 fix(matrix,mattermost): invite auth check + API path traversal guard`: 修复了Matrix和Mattermost平台的两个认证和路径遍历漏洞。
    - `#10347 fix(security): block _EXTRA_ENV_KEYS from subprocess env`: 防止子进程泄露微信、飞书等平台密钥。
    - `#6704 fix(matrix,mattermost): configurable E2EE passphrase, invite auth check, path traversal guard`: 允许用户配置Matrix端到端加密密码，取代硬编码。
    - `#7136 fix(security): patch 5 open vulnerabilities`: 修复了5类安全漏洞，包括PYTHONPATH沙箱注入、代码执行逃逸等。
- **LM Studio 集成修复 (P2/P3)**: 针对用户连接LM Studio（本地模型服务）时出现的路径构建和模型发现错误，今日合并了两个关键修复：
    - `#50187` & `#53295`: 修复了LM Studio基URL规范化问题，确保当用户粘贴不同格式的URL时，Hermes能正确调用API接口。
    - `#54567 fix(lmstudio)`: 进一步统一了LM Studio的基URL处理逻辑，确保模型探测和聊天功能正常工作。
- **基础设施清理**: `#54564` 移除了仓库中误提交的 `54MB` 的PR信息图，并将 `infographic/` 目录加入 `.gitignore`，维护了仓库的清洁。

**总结**: 今天项目在安全性上迈出了坚实一步，修复了大量积压的P1级漏洞，同时对LM Studio这类用户广泛使用的本地部署方案做了关键的兼容性修复，为下一阶段的稳定发展奠定了基础。

## 4. 社区热点

今日的社区讨论焦点高度集中，主要围绕两个长期存在的用户体验问题：

1.  **Windows桌面GUI控制台窗口闪烁 (`#54220`， 9条评论)**: 这是社区公认的“最受报告”的活跃Bug。问题描述为在Windows桌面应用上，每次启动子进程（如CMD, Git, PowerShell）时，都会有一个黑色控制台窗口一闪而过，严重影响使用体验。该议题已被标记为 `tracking` 议题，显示了维护者对此问题的重视。

2.  **中文/日文/韩文 (CJK) 输入法 (IME) 兼容性问题**: 这是一个由多个Issue组成的“问题簇”，共4个相关议题在本日报中被提及，合计获得近20条评论，是当前社区情绪最集中的痛点。
    - `#38826` (8条评论): macOS桌面应用中文输入法异常，按回车键会提交空/不完整的文本，需使用Shift+Enter。
    - `#39025` (4条评论): Windows桌面应用中，中文输入法文字输入后，按回车键无法发送。
    - `#39538` (3条评论): 桌面Composer组件丢失或无法提交CJK输入法文本。
    - `#39651` (3条评论): CJK输入法导致发送按钮显示为语音按钮，并伴随文本截断。
    - **分析**: 这些议题揭示了桌面应用在处理非英语输入法时存在核心的文本状态同步（Draft State）与Composer组件交互的bug，且横跨macOS和Windows平台，是当前最迫切需要解决的UI/UX问题。

## 5. Bug 与稳定性

今日报告的Bug数量较多（`50`条更新中，包含大量新问题和复现报告），按严重程度排列如下：

| 严重程度 | Issue # | 标题 | 状态 | 备注 |
| :--- | :--- | :--- | :--- | :--- |
| **P1 (严重)** | `#54220` | Windows Desktop GUI: console windows flash on subprocess spawns | **OPEN** | 社区最普遍反馈的Bug，已建立追踪议题。尚无修复PR。 |
| **P2 (高)** | `#54527` | Gateway message routing misdirects user input between TUI sessions | **OPEN** | 多TUI会话间消息路由错乱，导致输入永久丢失，是重大的功能故障。 |
| **P2 (高)** | `#54572` | patch tool (replace mode) can edit the wrong region | **OPEN** | 核心工具 `patch` 的区域匹配逻辑存在缺陷，可能错误地修改文件内容，影响可靠性。 |
| **P2 (高)** | `#54589` | OpenAI-compatible TTS backends without opus support fail | **OPEN** | 语音合成（TTS）功能对非标准后端兼容性差。**已有修复PR `#54597`**。 |
| **P2 (高)** | `#54593` | Ollama vision models silently strip image attachments | **OPEN** | **刚刚报告**，本地视觉模型（Ollama）的功能完全失效，是一个严重的回归/缺陷。 |
| **P2 (高)** | `#54579` | Long code blocks lose their indentation when split | **OPEN** | 长回复被拆分成多条消息时，代码块的缩进格式丢失，影响开发协作场景。 |
| **P2 (高)** | `#54049` | DeepSeek: OpenResty drops chunked streaming | **OPEN** | 特定网络环境下，DeepSeek API的流式响应中断。 |
| **P2 (高)** | `#3002` | [Bug]: Fails to install NeuTTS during setup | **OPEN** | **长期未解决**，核心语音功能“文字转语音”（NeuTTS）安装失败。 |
| **P2 (高)** | `#13834` | Hermes openai-codex fails on same machine where official Codex CLI works | **OPEN** | Hermes的Codex兼容性存在问题，需要复现。 |

**小结**: 稳定性方面存在多项P1/P2级问题，覆盖桌面体验、核心工具、外部集成等多个维度。特别是 `#54527` (消息路由错乱) 和 `#54220` (控制台闪烁) 严重损害了核心使用体验。

## 6. 功能请求与路线图信号

今日的功能请求和PR展现了社区对项目智能化和易用性的深入探索：

- **确定性工作流引擎 (`#5354`， 8 👏 8 👍)**: 一个非常受欢迎的功能请求，建议为Hermes Agent引入类似“Lobster”的确定性工作流引擎，用于处理需要精确复现或低延迟的任务（如API密钥轮换），避免LLM每次都要重新规划，从而节省Token和降低延迟。这表明社区希望Hermes在“高度自主”和“确定性执行”之间取得平衡。
- **用户工作区与知识库 (`#531`， 4条评论)**: 请求为Hermes增加持久化的用户知识库（RAG集成），允许用户上传文档并让Agent搜索和引用。这是个人AI助手从“聊天”走向“深度工作”的必备功能。
- **PR #54585 (桌面终端持久化)**: 一个备受期待的UI改进，允许重启桌面应用后恢复终端标签页和历史记录（进程不重启），增强开发工作流的连续性，类似于VS Code的终端行为。
- **PR #54599 (Telegram消息反应)**: 尝试将Telegram的消息反应（Emoji）映射为Agent可以理解的“动作”，拓展了人机交互的维度。
- **PR #54591 (批量修复P3议题)**: 一个“打包式”PR，解决了5个低优先级的P3问题，涵盖Agent归属、工具修复、桌面应用等。这种模式值得鼓励，能有效清理技术债务。

**路线图信号**: 社区对 **“确定性”** 和 **“持久化知识”** 的呼声很高，这两个方向很可能成为下一个版本的重要特性。同时，桌面应用体验的精细化打磨（如终端持久化、IME修复）是当前的重中之重。

## 7. 用户反馈摘要

从今日的Issues评论中，可以提炼出以下真实的用户痛点：

- **“新用户受挫”**: 用户 `haarts` 在 `#3002` 中报告安装核心组件 `NeuTTS` 时失败，这体现了新手在配置过程中的常见障碍。
- **“生产环境部署困扰”**: 用户 `vtbjbb-alt` 在 `#19201` 中报告，`load_dotenv(override=True)` 的默认行为会覆盖由系统d/Docker注入的环境变量，这与“12-Factor App”的配置惯例冲突，给进行容器化部署的用户带来困扰。
- **“期望稳定的核心工具”**: 用户 `MaxFreedomPollard` 在 `#54572` 中对 `patch` 工具表达担忧，认为其模糊匹配策略可能导致错误的编辑，动摇了用户对核心代码编辑功能的信心。
- **“对桌面应用的强烈不满”**: 关于控制台闪烁 (`#54220`) 和输入法 (`#38826`等) 的反馈量巨大，虽未直接显露出用户情绪，但其高票数和被标记为跟踪议题，表明这是用户满意度最低、最迫切需要修复的功能。
- **“对开源协议/品牌的好奇”**: 用户 `shashank-sn` 在 `#54591` 中修复了硬编码的“Nous Research”品牌信息，使其可配置，这反映了社区对Agent定制化和白标签能力的需求。

## 8. 待处理积压

以下是需要维护者重点关注的长期未解决或即将变得重要的问题：

| Issue # | 标题 | 优先级 | 已开启天数 | 提醒原因 |
| :--- | :--- | :--- | :--- | :--- |
| `#531` | Feature: User Workspace & Knowledge Base | P3 | **115天** | 呼声很高的功能请求，如果迟迟无法推进，可能会影响用户体验升级。 |
| `#3002` | [Bug]: Fails to install NeuTTS during setup | P2 | **96天** | 影响新用户入门的拦路虎，长时间未解决。 |
| `#5354` | [Feature]: Deterministic Workflow Engine | P2 | **85天** | 社区呼声高涨（8个👍），代表了重要的演进方向，应给予路线图层面的回应。 |
| `#13834` | Hermes openai-codex fails... | P2 | **68天** | 兼容性Bug，可能存在被社区放弃的风险，需维护者主动复现或确认。 |
| `#28004` | Telegram typing indicator stuck | P2 | **42天** | 竞态条件导致的UI bug，影响基础消息平台的用户体验。 |

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

好的，这是根据您提供的 PicoClaw 项目数据生成的 2026-06-29 项目动态日报。

---

# PicoClaw 项目动态日报 | 2026-06-29

## 1. 今日速览

项目今日活跃度较低。过去24小时内，**无新Issues或PR被创建**，整体贡献节奏平缓。一个关于WebSocket通信的老旧功能请求（#2984）已被关闭，标志着该需求的讨论告一段落。同时，一个关于图像输入压缩的功能性PR（#2964）被合并，为项目视觉管道增加了关键的可配置性。当前有一个关于新增“简单通道（simplex）”类型的新功能PR（#3193）处于待合并状态，预计将在近期为项目扩展新的集成能力。

## 2. 版本发布

无新版本发布。

## 3. 项目进展

- **图像输入压缩功能合并 (#2964)**: PR #2964 已被关闭并合并。该PR为PicoClaw的视觉处理管道增加了可配置的入站图像压缩策略。此前，系统仅通过 `max_media_size` 限制图像大小，无法在构建模型负载前进行多级压缩，可能导致模型处理开销过大。此项改进允许开发者设定更细粒度的压缩策略，优化了性能并降低了带宽消耗。
- **新增“simplex”通道类型 (#3193)**: 一个新的PR #3193 正处于待合并状态。该PR扩展了PicoClaw的通道类型，新增了“simplex”（单工/简单通道）支持。该功能可能用于连接一些仅支持单向消息传输的第三方平台或协议，增强了项目的互联互通性。

## 4. 社区热点

- **#2984 [已关闭] 为Pico WebSocket客户端添加显式完成信号**
  - **链接**: [Issue #2984](https://github.com/sipeed/picoclaw/issues/2984)
  - **分析**: 该Issue是过去24小内唯一有活跃的条目（虽被关闭）。自6月2日提出以来，共获得4条评论和2个👍。用户的核心诉求是：当前WebSocket客户端只能通过 `typing.stop` 等间接事件推断AI代理已完成响应，缺乏一个明确、确定性的“完成（turn completion）”信号，导致客户端状态的同步存在不确定性。该Issue因长期无后续活动被自动标记为“stale”后关闭，其底层需求（协议清晰度）可能仍是开发者和用户的关注点。

## 5. Bug 与稳定性

今日无新报告的Bug或稳定性问题。

## 6. 功能请求与路线图信号

- **已合并 / 路线图中**:
  - **可配置的图像压缩** (PR #2964): 响应了用户对视觉输入性能优化的需求，已合并至主分支，预计会包含在下一个版本中。
  - **Simplex 通道支持** (PR #3193): 体现了项目持续扩展第三方平台连接性的路线图。此功能是新增集成点，非破坏性变更，预计将被快速合并。

- **未解决的需求 (展望)**:
  - **WebSocket 显式完成信号** (Issue #2984): 虽然被关闭，但该需求代表了开发者对协议成熟度、客户端可编程性的更高要求。如果PicoClaw未来计划强化WebSocket协议的规范性，此问题可能会被重新讨论并在后续版本中实现。

## 7. 用户反馈摘要

从Issue #2984的摘要和背景来看，用户（尤其是进行外部集成的开发者）反馈了一个关键痛点：
- **痛点**: 在通过Pico协议进行WebSocket集成时，客户端缺乏明确的“代理响应结束”信号。开发者不得不依赖 `typing.stop` 这种非确定性的间接信号，这会增加客户端状态机设计的复杂度，并可能导致用户体验上的延迟或状态错乱（例如，用户看到“正在输入”状态提前消失，但实际消息还在处理中）。
- **使用场景**: 任何需要通过WebSocket API与PicoClaw智能体进行实时对话的第三方应用，如自定义聊天界面、机器人应用等。

## 8. 待处理积压

- **PR #3193 [待合并] 新增simplex通道类型**
  - **链接**: [PR #3193](https://github.com/sipeed/picoclaw/pull/3193)
  - **状态**: 自6月27日提交以来，已等待超过24小时未合并。建议维护者尽快审查，确认该实现是否会影响现有通道，若无问题则可合并以解锁新的集成场景。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

好的，这是根据您提供的 NanoClaw 项目 GitHub 数据生成的 2026-06-29 项目动态日报。

---

# NanoClaw 项目动态日报 | 2026-06-29

## 1. 今日速览
项目今日活跃度中等偏上，主要集中于安全加固与适配器修复。过去24小时内，社区贡献了6个Pull Request，其中1个已合并，5个待审，体现了积极的开发态势。值得注意的是，今天没有新Issue被提出，也没有新版本发布，项目焦点集中在解决已知的安全漏洞（CWE-59）和平台适配器（Discord、Telegram、Codex）的稳定性问题上。核心贡献者`johnmathews`提交的两个PR直接回应了一个严重的安全问题（#2828），显示出项目方对安全性的高度重视。

## 2. 版本发布
无

## 3. 项目进展
今日最重要的进展是成功合并了一个安全修复PR，并新增了多个针对特定模块的修复与功能。

-   **已合并/关闭**
    -   **`#2879` [closed] fix(agent-to-agent): containment-check target inbox in forwardAttachedFiles**：这是一个重要的**安全修复**。该PR修复了代理间（A2A）附件转发功能中的一个路径穿越漏洞（关联 #2828）。通过镜像现有防御模式：拒绝预置符号链接、使用`realpath`和`isPathInside`进行路径检查，确保附件不会写入会话根目录之外，有效防止了恶意代理通过符号链接劫持主机文件系统。
        -   [PR #2879 链接](https://github.com/nanocoai/nanoclaw/pull/2879)

-   **待审中（关键条目）**
    -   **`#2881` fix(discord): decode custom_id delimiter**：修复了Discord适配器中按钮交互解析失败的问题。该问题会导致按钮值被错误解析为“0\n0”，而非正确的“0”，从而中断用户交互流程。
        -   [PR #2881 链接](https://github.com/nanocoai/nanoclaw/pull/2881)
    -   **`#2880` fix(security): contain inbox symlink escapes**：另一个关键安全修复，针对 `#2828` 问题提供了更全面的解决方案。它在主机写入附件的两个路径（代理人站目录和A2A转发路径）上都进行了符号链接检查，以防止被攻破的Agent容器通过建立符号链接在主机上任意写入文件。
        -   [PR #2880 链接](https://github.com/nanocoai/nanoclaw/pull/2880)
    -   **`#2877` feat(telegram): native rich rendering**：为Telegram Bot适配器增加了原生富文本渲染支持，利用Bot API 10.1的新功能。这将显著提升用户通过Telegram与NanoClaw交互时的消息展示效果。
        -   [PR #2877 链接](https://github.com/nanocoai/nanoclaw/pull/2877)

**总结**：项目在**安全性**和**平台适配**两个维度上都有实质性的推进。安全方面，针对已报告的漏洞（#2828）进行了彻底的修复，并合并了其中一个解决方案；平台方面，Telegram和Discord的交互体验和稳定性都将得到提升。

## 4. 社区热点
今日社区讨论热度不高，所有PR均无评论。但从提交的PR性质来看，有两个热点议题：

1.  **安全漏洞（#2828）**：该问题由`johnmathews`贡献了两个PR（#2879, #2880）进行修复。虽然未直接看到用户讨论，但该问题被标记为CWE-59（符号链接跟随），是一个严重的、可能导致主机文件被恶意写入的安全隐患。社区（尤其是维护者）对此问题的关注度极高，迅速响应并提出了解决方案。
2.  **平台适配性**：针对Discord（#2881）和Telegram（#2877）的PR体现了社区对多平台支持的热情。Telegram的富文本功能是一个增强用户体验的需求，而Discord的修复则是一个影响正常使用的Bug。

## 5. Bug 与稳定性
今日无新Bug报告，但PR中的修复揭示了两个影响稳定性的问题：

-   **严重**：
    -   **CWE-59 符号链接跟随（#2828）**：攻击者可通过在会话目录中放置符号链接，引导主机程序将文件写入到系统任意位置。这是一个严重的安全漏洞，可能影响整个系统。**已有关联的fix PR：`#2879` (已合并) 和 `#2880` (待审)**。
-   **高**：
    -   **Discord 按钮交互失效**：当按钮`custom_id`中包含换行符分隔符时，解析逻辑出错，导致按钮值无法被正确解析。这将直接导致用户无法通过点击按钮与机器人进行交互。**已有fix PR：`#2881`**。

## 6. 功能请求与路线图信号
今日没有新的功能请求Issue，但两个PR暗示了未来的发展方向：

-   **可能的下一版本功能**：
    -   **增强的Telegram原生交互**：`#2877` PR引入的`sendRichMessage` API支持，表明项目正在积极采用最新的Bot API来提升用户体验，这很可能被纳入下一个版本。
    -   **Codex 认证健壮性**：`#2878` PR修复了OneCLI令牌过期后Codex连接失败的问题。这说明项目团队正在优化与外部AI服务的连接稳定性和错误处理，这是一个重要的质量改进点。

## 7. 用户反馈摘要
由于所有PR和Issue均无评论，无法直接从今日数据中提炼用户反馈。但从PR内容可以推断出一些潜在的用户痛点：

-   **Discord用户**：可能遇到了按钮交互偶尔失败的情况，原因是底层解析逻辑的Bug。`#2881`的修复即为解决此问题。
-   **Codex/OneCLI用户**：可能遇到了突然的“访问令牌无法刷新”错误，需要反复重新登录。`#2878`的修复直接回应了这一痛点。
-   **高级用户/自部署者**：对于安全性有较高要求的用户，`#2828`相关修复（#2879, #2880）解决了他们可能担心的恶意Agent逃逸问题，增强了自部署环境的安全信心。

## 8. 待处理积压
今日没有明显的“长期未响应”的Issue或PR。所有开放中的PR创建时间都在1-2天内，维护者响应积极。重点关注以下几个待合并的、与安全和稳定性相关的PR：

-   **`#2881` fix(discord)**: 修复用户交互Bug，建议优先合并。
-   **`#2880` fix(security)**: 进一步加固安全防线，建议与已合并的 `#2879` 一同审查，确保没有遗漏。
-   **`#2878` fix(codex)**: 提升Codex Agent的可用性，避免用户频繁掉线。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw 项目动态日报 | 2026-06-29

---

## 1. 今日速览

- 过去24小时内，项目仅处理了1条已关闭的Issue（#50），无新Issue或PR产生，社区活跃度处于低位。
- 无新版本发布或PR合并，项目代码与功能层面未出现可见推进。
- 唯一被关闭的Issue#50（关于ESP32兼容性）于2026-06-28最终由作者关闭，但未附带任何技术结论或迁移方案。
- 整体来看，项目当前处于“维护静默期”，开发者协作与用户互动显著放缓，需关注长期健康度。

## 2. 版本发布

（无新版本发布，省略此部分。）

## 3. 项目进展

- **PR合并/关闭**：过去24小时内无PR更新。
- **功能推进**：无合并的代码变更，项目主干无向前演进痕迹。

## 4. 社区热点

- **Issue #50 [已关闭]**: *Can this run on an Esp32?*  
  - 作者：ngantrandev | 创建：2026-02-21 | 关闭：2026-06-28 | 评论：4 | 👍：0  
  - 链接：[#50](https://github.com/nullclaw/nullclaw/issues/50)  
  - **分析**：这是过去24小时内唯一被更新的Issue，且已关闭。讨论围绕在ESP32上运行NullClaw的可行性，属于硬件兼容性诉求。虽然关闭，但未给出明确的技术可行性结论或使用指导，反映出缺乏官方回应或文档支持。

## 5. Bug 与稳定性

- 过去24小时内未报告新的Bug、崩溃或回归问题。
- 未发现任何已被标记为严重或急迫的稳定性问题。

## 6. 功能请求与路线图信号

- **潜在需求**：Issue#50所暗示的**ESP32硬件适配**功能是用户提出的核心需求。尽管已关闭，但该需求在社区中尚未得到满足。
- **路线图信号**：无官方路线图更新。目前无任何PR或分支指向硬件适配（如ESP-IDF、Arduino框架支持）的开发。

## 7. 用户反馈摘要

- **用户痛点（源自Issue#50评论）**：  
  - 对在嵌入式硬件（ESP32）上运行NullClaw表现出强烈兴趣，但缺乏可行的安装指引或移植指南。
  - 从关闭状态推测，用户可能因长期无官方反馈而自行放弃或转向替代方案。
- **满意/不满意**：无正面或负面满意度数据。关闭Issue时未附带解决方案，可能使用户体验不佳。

## 8. 待处理积压

- **长期未响应的重要Issue**：  
  - Issue#50 *Can this run on an Esp32?* 虽有社区互动（4条评论），但无维护者回应，最终由作者自行关闭。这反映了维护者对特定硬件需求的忽视，建议项目维护者考虑补充硬件兼容性文档或关闭原因说明。
- **PR积压**：当前无待合并PR，但长期无维护活动本身即为风险。

---

## 项目健康度评估

| 指标               | 状态       | 风险信号                     |
|--------------------|------------|------------------------------|
| 社区活跃度         | 低         | 0新Issue，0新PR           |
| 代码维护频率       | 停滞       | 无合并、无版本发布           |
| Bug/稳定性处理     | 无         | 无新报告，但无反馈闭环       |
| 用户反馈响应       | 缺失       | Issue#50无官方回应         |
| 路线图可见性       | 极低       | 无版本发布、无路线图文档     |

**建议**：项目维护者宜尽快回复或关闭积压的Issue（如#50），发布更新计划或至少提供官方说明，以避免用户流失与信任下降。

---

*本日报基于NullClaw (github.com/nullclaw/nullclaw) 2026-06-29 公开数据生成。*

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

好的，这是根据您提供的 IronClaw 项目数据生成的 2026-06-29 项目动态日报。

---

## IronClaw 项目动态日报 - 2026-06-29

### 1. 今日速览

项目今日活跃度**极高**，尤其集中在 Pull Request 的提交与合并上。过去24小时内共有41条PR更新，其中17条已被合并或关闭，显示核心开发团队正在进行高效率的功能开发与集成。Issues 方面有3条更新，其中一条关于「能力策略」的 Issue 已拥有对应的实现 PR。虽然项目暂无新版本发布，但存在一个相关的发布 PR（#5311）正在审查中，可能预示着版本更新的临近。整体而言，项目正处于密集的功能开发与迭代阶段，健康状况良好。

### 2. 版本发布

无新版本发布。

### 3. 项目进展

今日项目进展迅速，核心团队在测试框架、集成、Bug修复和文档方面取得了显著成果。以下为今日合并/关闭的重要 PR：

- **`[codex] Harden Slack pairing activation flows` (PR #5362 [OPEN])**: 虽未合并，但作为今日更新且由经验丰富的贡献者提交的重点PR，它强化了Slack账户配对流程的鲁棒性，包括处理过期码、隔离配对线程等，提升了用户体验的稳定性。
- **`fix(reborn): surface real failure detail instead of generic "invalid_input"` (PR #5338 [OPEN])**: 另一项重要的修复工作，旨在将隐藏的、真实的错误信息暴露给终端用户，而非显示通用的“无效输入”，这对于调试和提升用户反馈质量至关重要。
- **`feat(reborn): add /pair Slack slash command...` (PR #5377 [CLOSED])**: 该PR已合并，为Slack V2引入了一个新的 `/pair` 斜杠命令，用于个人绑定配对恢复，并优化了无效码的错误提示，直接改善了Slack集成用户的体验。
- **`test: validate /benchmark build against current ironclaw main (throwaway)` (PR #5393 [CLOSED])**: 一个验证性PR已合并，用于修复因依赖锁定文件更新导致的 `/benchmark` 构建失败问题，保证了CI管道的健康。
- **`docs(reborn-itest): Slice 9 — descope embeddings fake...` (PR #5386 [CLOSED])**: 文档型PR已合并，在开发集成测试框架时发现“嵌入层”的接缝不可达，因此决定移除该部分测试范围的计划，展示了开发过程的透明度和务实态度。
- **`test(reborn): slice 4 — URL-keyed HTTP matcher + egress assertion API` (PR #5387 [CLOSED])**: 测试框架PR已合并，为 Reborn 集成测试框架添加了关键的URL匹配和出口断言API，增强了测试能力。
- **`[codex] fix reborn google oauth decode and preview host login` (PR #5388 [CLOSED])**: 修复了Google OAuth令牌解码和预览域名登录问题的PR已合并，确保了登录流程的兼容性和安全性。

这些合并表明项目在 **Reborn架构**、**Slack集成**、**测试框架**和**CI健全性**方面取得了扎实的进展。

### 4. 社区热点

今日无特定的 Issues/PRs 获得大量评论或反应。社区讨论的热点主要通过核心贡献者提交的复杂PR来体现，尤其是在 **Reborn 测试框架**（如 #5392）和 **Slack 集成**（如 #5362）这两个方向上。

这些PR涉及面广，改动量大（标签多为XL），包含架构决策（测试框架）和对用户行为的精细调整（Slack配对），反映了当前开发工作的重心。

### 5. Bug 与稳定性

- **严重/优先级高**:
    - **[#4108] Nightly E2E failed**: 这是一个持续存在的、已打开一个月有余的每日构建失败问题。该问题未被解决，可能会阻碍自动化回归测试，是影响项目稳定性的一个已知风险点。当前无关联的 fix PR。
    - **PR #5393 [CLOSED]**: 该PR的修复内容揭示了在2026-06-25 12:14 UTC之前基于主分支的PR会触发 `/benchmark` 构建失败，该问题已由这个验证PR修复并合并。

- **中等/低优先级 (已有修复PR)**:
    - **PR #5338 [OPEN]**: 修复了在工具执行出错时，用户界面只显示通用“无效输入”错误的问题，致力于提供更准确的错误详情。
    - **PR #5388 [CLOSED]**: 修复了Google OAuth登录失败的问题，该问题影响了使用预览/自定义域名的用户。

### 6. 功能请求与路线图信号

- **核心功能请求**:
    - **[#5385] Add Capability Policy**: 这是一个由用户提出的新功能请求，旨在引入细粒度的用户权限管理（区分所有者、管理员和成员）。**该请求已有对应的实现PR (#5394 `capability policy e2e`)**，表明这个功能很可能被纳入下一个里程碑或版本中。这可能是项目转向更复杂、可配置权限模型的重要信号。

- **潜在进入下一版本的特征**:
    - **`feat(reborn): Context management — progressive tool disclosure` (PR #5149 [OPEN])**: 该PR旨在解决工具上下文过大导致的API超时问题，通过渐进式工具披露来优化性能。这是一个关键的优化，很可能成为未来版本的核心特性。
    - **`Add Reborn WebUI v2 live QA canary` (PR #5354 [OPEN])**: 为 WebUI v2 添加生产环境的金丝雀测试，是提升发布质量和稳定性的重要基础设施。

### 7. 用户反馈摘要

从现有的 Issue 和 PR 中提炼的用户反馈有限，但可以观察到以下趋势：
- **对更好错误提示的隐性需求**: PR #5338 的修复直接回应了用户在遭遇故障时无法获得有效信息的痛点。
- **对更复杂权限管理的需求**: Issue #5385 明确提出了对“能力策略”（即用户权限管理）的需求，表明项目在发展过程中，社区用户开始需要更精细的控制能力。
- **对第三方集成的稳定性需求**: 多个围绕 Slack 集成（如 PR #5362, #5377）的修复和改进，表明用户对 Slack 等合作伙伴集成的稳定性、可靠性和易用性有较高期望。

### 8. 待处理积压

以下长期未响应或未解决的问题/PR需要维护者关注：

- **[#4108] Nightly E2E failed**:
    - **状态**: 已打开超过一个月，每日构建持续失败。
    - **链接**: nearai/ironclaw Issue #4108
    - **建议行动**: 这是一个影响项目质量保障的**关键**阻塞性问题。需优先调查根本原因并修复，否则所有CI结果的可信度都将受到质疑。
- **[#4002] build(deps): bump the actions group...**:
    - **状态**: 已打开超过一个月，等待合并的 Dependabot PR。
    - **链接**: nearai/ironclaw PR #4002
    - **建议行动**: 大量CI Actions的版本积压可能导致未来CI行为的突然变动或兼容性问题。建议安排审查并合并。

- **[#4032] & [#4498] & [#5114]**: 这是另外三个已经打开超过一周的 Dependabot 依赖更新 PR，涉及 Wasm、序列化和 Tokio 生态系统。虽然风险通常较低，但长时间积压会增加未来合并时的冲突风险。需要维护者分配时间进行批量审查。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

好的，这是为您生成的 LobsterAI 项目动态日报。

---

# LobsterAI 项目动态日报 (2026-06-29)

**数据统计周期：** 2026-06-28 00:00 UTC - 2026-06-29 00:00 UTC

### 1. 今日速览

今日项目活跃度中等偏上，主要体现在代码合并和议题处理上。**24小时内关闭了4个历史 Issue 和4个 PR**，显示出项目维护者对积压问题进行了有效的清理。同时，**新提交的1个 Issue(#2216) 报告了一个严重的功能阻塞问题**，即 Memory Search 的 embedding provider 被锁定且无法切换，这可能影响部分用户的核心功能使用。**最重要的进展是 PR #2217 被合并**，该 PR 修复了新版 OpenClaw 插件的审批流程，将其路由到现有权限系统，解决了用户关切的兼容性问题。整体来看，项目正处于解决兼容性问题和优化核心功能的阶段。

### 2. 版本发布

无新版本发布。

### 3. 项目进展

今日项目通过合并/关闭重要 PR，在 **OpenClaw 兼容性**和 **技能管理** 方面取得了关键进展：

- **OpenClaw 插件审批修复 (PR #2217 [CLOSED])**：此 PR 被合并，解决了用户在新版 OpenClaw 中遇到的插件审批流程问题。通过将审批事件路由到现有的权限系统，确保了功能的一致性和安全性。这直接回应了 Issue #1443 中对新版本 OpenClaw 适配的担忧。
- **技能管理功能合并 (PR #1440 和 #1445 [CLOSED])**：这两个较早的 PR 今日被关闭，标志着两项重要功能被整合进主分支：
    - **技能UI优化 (PR #1440)**：将已选技能标签从拥挤的输入框工具栏移至 textarea 上方，显著改善了多技能选择时的用户体验。
    - **技能重复导入修复 (PR #1445)**：修复了 zip 导入时目录名异常和三种导入渠道均无法有效防止技能重复的问题。该修复通过读取 `SKILL.md` 中的 `name` 字段进行校验，避免了重复技能注入 system prompt 导致大模型路由混乱的稳定性隐患。

### 4. 社区热点

今日表现最突出的 Issue 是：

- **#2216 [Memory Search 无法切换为 local embedding provider]**: 尽管创建时间较短，但这是一个**严重且紧急**的功能阻塞问题。用户 `AL-Mint` 报告在 OpenAI API 配额耗尽后，Memory Search 功能完全不可用，因为 UI 锁定仅支持 OpenAI，无法切换到本地或其他 provider。该问题触及了**用户对服务本地化和可控性的核心诉求**，即“当外部服务不可用时，系统应提供可靠的本地替代方案”。预计会引发更多社区成员的共鸣和讨论。

### 5. Bug 与稳定性

今日报告了一个严重等级较高的 Bug：

1. **严重：Memory Search Embedding Provider 被锁定 (Issue #2216 [OPEN])**
    - **描述**：在 LobsterAI 2026.6.1 版本中，Memory Search 的 Embedding Provider 被固化为 openai，用户无法在设置界面中切换为 local 或其他 provider。当 OpenAI API 返回 429 错误（配额耗尽）时，用户无法使用 Memory Search 功能。
    - **状态**：新建，未分配，未关联修复 PR。
    - **紧急度**：高。此问题会直接导致依赖 Memory Search 功能的用户在外围服务故障时完全无法使用。

此外，今日关闭了 4 个标记为 `[stale]` 的旧 Issue，它们多为报障类问题，如“创建定时任务无反应 (#1437)”、“上传技能停用后仍可通过对话调用 (#1439)”。这些问题虽已关闭，但其暴露的**技能使用状态与对话状态不同步**、**UI交互阻塞无反馈**等问题仍需关注，确保在后续版本中得到彻底解决。

### 6. 功能请求与路线图信号

- **OpenClaw 新版本适配 (Issue #1443 [CLOSED])**：虽然此 Issue 今天被标记为 `stale` 并关闭，但其核心诉求 —— **适配新版 OpenClaw** —— 已经通过 **PR #2217** 得到了部分解决。这表明项目团队正在有计划地跟进上游依赖的更新。
- **定时任务模块 UI 全面升级 (PR #1488 [OPEN])**：这是一个已存在近3个月的 PR，展示了从功能到UI的完整升级方案（卡片网格、搜索、历史任务）。其长期处于 `[OPEN]` 状态，**可能暗示维护者正在审阅或等待代码质量达到合并标准**。这应被解读为路线图上确定会到来的一个较大改进。
- **技能选择与会话解耦 (PR #1494 [OPEN])**：另一个长期未合并的 PR，旨在将技能选择状态从全局改为按会话独立管理。这解决了用户跨会话体验不一致的痛点。其持续开放状态**可能表明该改动涉及较大的状态管理重构，需要更谨慎的测试**。

### 7. 用户反馈摘要

- **痛点**：
    - **服务依赖风险**：“当 OpenAI API 配额耗尽时（429），记忆搜索完全不可用。”(Issue #2216) —— 用户对云服务单点故障的担忧明显。
    - **技能管理混乱**：“关闭技能，在对话中使用技能关键字”技能仍能被调用 (Issue #1439)；“添加技能对话后引用的技能不展示，重新切换agent会重新展示”(Issue #1442) —— 用户对技能生效的逻辑感到困惑，认为其行为不符合直觉。
- **使用场景**：用户 `devilszy` 在 Issue #1442 中详细描述了 Agent 与技能交互的场景，提出了核心疑问：“agent选择技能的作用是什么？只触发选择的技能？”，这表明用户希望系统有更清晰的**技能路由和触发逻辑**。

### 8. 待处理积压

以下为长期未响应或可能被忽略的重要工作项，建议维护者关注：

1. **PR #1488 [OPEN] - 定时任务模块 UI 全面升级** (创建: 2026-04-05)
    - **理由**：这是一个功能完整、涉及面广的重大UI改进，已积压近3个月。其内容（搜索、历史查询、卡片布局）是用户明确需求的体验提升。建议尽快进入复审或合并流程。
    - [链接](https://github.com/netease-youdao/LobsterAI/pull/1488)

2. **PR #1494 [OPEN] - 技能选择状态改为按会话独立管理** (创建: 2026-04-06)
    - **理由**：此PR直接修复了 Issue #1442 中报告的 “技能跨会话同步”的反直觉行为，对于提升用户体验至关重要。长期搁置可能导致类似 Issue 反复出现。
    - [链接](https://github.com/netease-youdao/LobsterAI/pull/1494)

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

好的，这是根据您提供的 Moltis 项目 GitHub 数据生成的 2026-06-29 项目动态日报。

---

## Moltis 项目日报 | 2026-06-29

### 1. 今日速览

过去24小时内，Moltis 项目整体活跃度处于“温和”水平，无新版本发布。社区贡献者主要聚焦于**性能优化**和**构建配置**两个方向，提交了2个待合并的 Pull Request (PR)。Bug 方面，报告了1个关于 Apple 容器 ID 长度限制的问题，但尚未有对应的修复提交。项目没有紧急的阻塞性问题，开发节奏稳健，社区贡献质量较高。

### 2. 版本发布

无新版本发布。

### 3. 项目进展

今日无 PR 被合并，但有两个重要的 PR 处于待合并状态，它们代表了项目向更稳定、更高效的方向迈进的关键步骤：

- **优化图像上下文占用 (PR #1138):** 该 PR 解决了高分辨率图片作为 Base64 URI 嵌入时，会消耗超出模型上下文窗口预算的问题（一张照片可达 ~350K token）。修复方案是在图片进入模型上下文之前对其进行**降采样**。这对多模态场景下的用户体验是重要的性能修复，能有效防止因图片过大导致的对话中断。
- **修复构建依赖泄漏 (PR #1139):** 该 PR 修复了一个构建配置问题：`gateway` 模块的 `metrics` 特性会“强制”启用 `moltis-matrix` 模块（及其底层的 `matrix-sdk`），即使 Matrix 通道并未被启用。修复方法是使用弱依赖声明 (`?` 限定符)，**显著减少了非 Matrix 用户的构建体积和编译时间**。

**项目向前迈进：** 这两个 PR 一旦合并，将直接提升用户体验（处理图片更流畅）和开发者体验（编译更轻量）。

### 4. 社区热点

今日社区讨论热点主要集中在 **Issue #1137**，且唯一活跃的讨论也围绕于此。

- **热点 Issue: [Bug]: Apple Container ID exceeds name limit ( #1137 )**
    - 链接: [Issue #1137](https://github.com/moltis-org/moltis/issues/1137)
    - **分析：** 该问题报告了在 Apple 平台（可能是 macOS 或 iOS）上，与容器/沙箱相关的 ID 超出了命名长度限制。这通常是一个 **平台兼容性 root 级 Bug**，会影响所有在 Apple 生态下使用容器功能（如应用沙箱、数据隔离）的用户。用户（作者 holgzn）已确认使用最新版本并搜索过现有 issues，说明这是一个新发现的问题。有1条评论，表明至少有一位维护者或社区成员已关注并可能正在复现或分析。

### 5. Bug 与稳定性

今日仅报告了一个 Bug，属于 **中等严重程度**：

- **Bug: Apple Container ID 超出名称限制 (#1137)**
    - **严重程度:** 中等。直接影响 Apple 设备上的功能可用性，但不影响其他平台。
    - **影响范围:** 所有使用 macOS/iOS 的 Moltis 用户。
    - **修复状态:** 尚无关联的修复 PR。可能需要底层代码容器管理逻辑的调整。

### 6. 功能请求与路线图信号

今日无直接的功能请求 issue。但**待合并的 PR #1138 (图片降采样)** 可以被视为社区对高性能多模态能力的强烈需求的反映。该 PR 直接解决了用户在与 AI 交互时频繁遇到的“图片太大，无法处理”的痛点，这是一个明确的信号，表明**增强图像处理能力**是当前用户最迫切的需求之一，极有可能被纳入下一个版本的关键特性。

### 7. 用户反馈摘要

从唯一活跃的 Issue #1137 的评论中，可以提炼出以下用户反馈：

- **用户场景：** 用户在 Apple 设备上部署或使用 Moltis，可能涉及容器化运行环境或应用沙箱。
- **核心痛点：** 发现 Apple 平台内部的容器标识符（ID）长度超过了系统允许的限制，导致相关功能（可能是应用隔离或数据存储）无法正常工作。
- **负面反馈：** 这是一个阻止用户正常使用的平台兼容性 Bug。用户期望 Moltis 能在所有主流操作系统上无缝运行，对 Apple 平台的适配尚未达到预期。

### 8. 待处理积压

今日新增的 **Issue #1137** 是当前最重要的待处理事项。虽然它创建于两天前，但更新于昨日，意味着问题已被维护者关注。但由于尚无修复 PR，它需要被列为优先处理的积压工作：

- **积压项: [Bug]: Apple Container ID exceeds name limit (#1137)**
    - **优先度:** 高
    - **原因:** 阻止特定平台用户正常使用，影响用户留存和项目跨平台声誉。
    - **状态:** 已打开，待分析原因和给出修复方案。建议社区维护者尽快确认根本原因并分配修复任务。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，我已经根据您提供的 CoPaw (QwenPaw) 项目 GitHub 数据，为您生成了 2026-06-29 日的项目动态日报。

---

# CoPaw (QwenPaw) 项目动态日报 | 2026-06-29

## 1. 今日速览

今日项目活跃度**极高**，24小时内共有 35 条 Issue 和 PR 更新，社区参与和代码贡献均非常踊跃。Bug 修复与功能开发并进，尤其在 **插件兼容性 (AgentScope 2.0 迁移)** 和**通信渠道增强 (钉钉、Matrix)** 方面取得了显著进展。一个值得关注的挑战是用户报告的 **DeepSeek V4 模型兼容性 Bug** 和 **Agent 无限循环** 问题，社区正在积极提供 `fix PR`。总体来看，项目正处在一个健康、高强度的迭代期。

## 2. 版本发布

- **今日无新版本发布。**

## 3. 项目进展

今日完成了多项重要 PR 的合并，标志着项目在稳定性、CI 流程和基础设施上迈出了坚实一步：

- **基础设施与CI优化**：
    - **[PR #5578] (已关闭)**：修复了 Windows/macOS 桌面端 (Tauri) 的首次启动验证流程，通过移除初始化后的标记文件解决了环境准备问题。
    - **[PR #5531] (已关闭)**：通过 `pytest-xdist` 将集成测试运行时间从 24 分钟骤降至 3.5 分钟，并修复了 5 个在并行测试下不稳定的文件，极大提升了 CI 效率。
    - **[PR #5542] (已关闭)**：适应 AgentScope 2.0 的重大变更，全面修复了端到端测试套件，确保新框架下的质量门禁。

- **关键功能落地**：
    - **[PR #5210] (已关闭)**：新增 `qwenpaw cron update` CLI 命令，用户可以**直接修改现有定时任务**的配置，无需先删除后重建，回应了用户长期以来的痛点 (Issue #4939)。
    - **[PR #5321] (已关闭)**：引入全新的 **scroll 上下文管理策略**。它将完整对话持久化到 SQLite 数据库中，并提供 Python REPL 按需召回，是 Agent 长对话记忆管理的一次重要创新。

- **插件生态修复**：多个插件相关的修复被合并，例如修复 QwenPaw 宠物插件 (PR #5565) 和更新检测器缓存键 (PR #5500)。

## 4. 社区热点

今日最受关注的议题集中在 AI 模型兼容性和 Agent 行为逻辑上，反映了用户在实际使用中面临的核心挑战。

1.  **[Issue #5573] DeepSeek V4 模型兼容性 (Bug)** - **评论数最多 (3条)**：
    - **链接**：[Issue #5573](agentscope-ai/QwenPaw Issue #5573)
    - **分析**：用户报告通过 OpenAI 兼容端点使用 DeepSeek V4 模型时，遇到两种 400 Bad Request 错误。社区已提供详细的根因分析和代码修改建议，作者 (非专业 Python 开发者) 请求官方评估。该 Issue 直接关联到一个正在处理的 **[PR #5582] (修复流式 reasoning_content 错误)**，表明团队正在积极介入。

2.  **[Issue #4873] SubAgent 无限轮询 (Bug)** - **评论数较多 (3条)，且持续时间长**：
    - **链接**：[Issue #4873](agentscope-ai/QwenPaw Issue #4873)
    - **分析**：这是一个持续近一个月的严重 Bug。同时启动两个 SubAgent 会导致主 Agent 陷入高频工具调用循环，且无法从飞书端打断。此问题与已关闭的跨 Agent 无限循环 (Issue #5204) 类似，凸显了 Agent 间并发和死锁检测机制的薄弱。

## 5. Bug 与稳定性

按严重程度排列：

1.  **严重：Agent 行为异常 / 通信中断**
    - **[Issue #4873] 同时开两个subagent导致主agent无限快速轮询** （**严重**，共存近一个月）
    - **[Issue #5204] 两个Agent通过Matrix互聊时陷入无限循环** （**严重**，已关闭，表明官方已处理同类问题）
    - **[Issue #5584] 无法连接自定义ascend-vllm模型** （**高**，1.1.7 之后版本回归，影响特定用户群）
    - **[Issue #5573] DeepSeek V4 模型推理错误** （**高**，影响使用非官方或中转站的 DeepSeek V4 用户。**已有 fix PR (#5582)**）

2.  **中低：功能异常 / 体验问题**
    - **[Issue #5587] Qwen-Image Tool 安装错误** （**中**，影响插件安装体验）
    - **[Issue #5591] 日志信息过多（GET /api/console/inbox/events）** （**低**，影响终端使用体验，属噪音问题）
    - **[Issue #5579] 异常中断场景下对话记录丢失** （**中**，已识别为设计缺陷）

## 6. 功能请求与路线图信号

基于用户提出的需求与现有PR判断，以下功能很可能进入下一版本：

- **高可能性**：
    - **[Issue #5564] 钉钉 @Mention 支持**：直接关联的 PR [#5590] 已提交，正在合并中，预计很快上线。
    - **[Issue #5572] 模型自动降级（Fallback）**：用户呼声高，且是提升服务可用性的关键能力，可能成为下一个优先开发项。
    - **[Issue #5588] 记忆搜索支持专用 Reranker**：用户提出改进记忆检索的精确度，属于 Agent 长期性能优化方向。

- **中可能性**：
    - **[Issue #5579] 对话记录断点保存**：重要性高但实现复杂，预计会进入长期讨论和设计阶段。
    - **[Issue #5583] 聊天界面UI/UX改进**：多个关于 UI 的 Issue（如#5583，#5589）表明社区对前端体验有较高期待，可能在某次迭代中集中优化。

## 7. 用户反馈摘要

- **痛点**：
    - **模型兼容性是最大痛点**：用户在使用非主流模型（如 DeepSeek V4 通过中转站、华为昇腾 vLLM）时频繁遇到兼容性问题，且在高版本中回归 (Issue #5573, #5584)，影响用户体验和项目推广。
    - **Agent 不稳定行为**：“无限轮询”、“无限对话”等问题让用户感到失控，尤其是无法通过日常使用的客户端（如飞书）打断，体验割裂 (Issue #4873)。
    - **常用工具不够便捷**：`cron` 任务不支持直接更新、钉钉群内无法 @ 其他 Agent、技能选择无法连续添加，这些细节影响了用户操作效率 (Issue #4939, #5564, #5589)。

- **满意度**：
    - **对功能 PR 的积极响应**：对于已关闭的 `cron update` PR，原 Issue (#4939) 作者给出了积极反馈。
    - **社区互助积极**：用户会详细分享问题发现和修改思路（如 Issue #5573），即使是非专业开发者也愿意贡献，体现了社区凝聚力。

## 8. 待处理积压

- **[Issue #4873] “同时开两个subagent会导致主agent无限快速轮询直至任务结束”**：
    - **优先级**：**高**。这是一个严重且持续近一个月的 Bug，直接影响核心 Agent 并发功能。虽然已有 #5204 这类同类问题被关闭，但具体修复机制需要确认是否已覆盖此 Issue。
    - **建议**：项目维护者应明确回应此 Issue，说明 #5204 的修复是否解决了此问题，或者是否需要新的修复。

- **[Issue #5584] “无法连接自定义的ascend-vllm模型”**：
    - **优先级**：**中**。虽然是特定场景，但属于回归问题，且会影响使用国产硬件的用户群体。建议标记为 Bug 并安排排查。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

好的，这是根据您提供的 ZeroClaw GitHub 数据生成的 2026-06-29 项目动态日报。

---

# ZeroClaw 项目日报 (2026-06-29)

## 1. 今日速览

ZeroClaw 项目今日维持高活跃度。过去 24 小时内，社区共提交了 50 条 Issues 和 50 条 PRs，显示出强大的社区贡献动力。当前工作重点集中在 **稳定性修复**、**平台兼容性**（特别是针对 OpenAI 兼容提供方的工具调用问题）以及 **功能增强**（如离线定价、WASM 插件和 ACP 协议的完善）。大量 P1 优先级的 Bug 修复和 RFC 处于讨论或待合并状态，表明项目正处于紧张的迭代期，为即将到来的 v0.8.x 系列版本做冲刺。

## 2. 版本发布

**(无)**

## 3. 项目进展

今日无重大 PR 被合并，但开放了大量用于修复和增强的 PR，显示项目正积极处理社区反馈。以下为今日提交的关键 PR：

- **供应商兼容性修复**：
    - 【PR #8474】`fix(providers/copilot): gate tool_choice on non-empty tools`
    - 【PR #8473】`fix(providers/azure-openai): gate tool_choice on non-empty tools`
    - 【PR #8471】`fix(providers/compatible): gate tool_choice on non-empty tools`
    - **摘要**：一个高优先级 Bug 的系列修复，该问题导致 OpenAI 兼容的 API（如 vLLM）在无工具可用时发送空 `tools` 列表和 `tool_choice: "auto"`，引发 HTTP 400 错误。这三个 PR 分别针对 Copilot、Azure OpenAI 和通用兼容提供方进行了修复，是解决 Issue #7862 的关键步骤。

- **WASM 插件架构推进**：
    - 【PR #8368】 `feat(plugins): wasmtime component-model host for tool/channel/memory`
    - **摘要**：这是一项重量级（size: XL）的增强，为 ZeroClaw 的插件系统引入了基于 `wasmtime` 和组件模型 (Component Model) 的主机支持。它将允许工具、通道和内存等核心能力通过 WASM 插件进行扩展，是 v0.8.x 路线图中的关键里程碑。

- **提讯（Elicitation）/ 协议（ACP）增强**：
    - 【PR #8338】 `feat(elicitation): ACP multiple-choice for the ACP channel and Zerocode Code tab`
    - **摘要**：实现了 ACP (Agent Communication Protocol) 草案中的 **多选题提讯模式**。这可以让代理在不确定时以选择题形式向用户提问，改善了用户交互体验，尤其适用于 Zed 等支持此特性的编辑器。

## 4. 社区热点

今日最受社区关注的话题集中在 **运行时核心稳定性** 和 **标准协议支持** 上。

1.  **#5808 [Bug]: Default 32k context budget is exceeded...** (7 条评论)
    - **链接**: [Issue #5808](zeroclaw-labs/zeroclaw Issue #5808)
    - **分析**: 这是一个高严重性 (S1) 的 Bug，讨论核心在于：**默认的上下文预算设置不合理**。默认的 32k token 限制在新会话首次迭代时就被系统提示词和工具定义超出 3.3 倍，导致代理在“第一轮对话”就被迫“预压缩”，严重影响用户体验。用户质疑默认值的设置依据。

2.  **#6969 [RFC]: unified output routing model…** (7 条评论)
    - **链接**: [Issue #6969](zeroclaw-labs/zeroclaw Issue #6969)
    - **分析**: 这是一个高风险的 RFC，由用户从 Letta 迁移后提出的 **核心需求**：用户希望可以精细控制代理回复的**方式和位置**（例如，早晨简报通过邮件发送，技术问题通过 Slack 发送）。当前 ZeroClaw 缺乏这种统一的输出路由模型。此 RFC 代表了社区对代理能力更高级、更细粒度控制的主流期望。

## 5. Bug 与稳定性

今日报告了多个高风险 (risk:high) 和影响工作流 (S1/S2) 的 Bug：

- **S1 - 工作流受阻**:
    - **#5808**: 默认上下文预算过小，导致第一轮即被预压缩。无直接修复 PR。
    - **#6361**: `context_compression` 会丢失 `tool_calls` 和 `tool` 结果消息，导致工具循环和角色错误。无直接修复 PR。
    - **#6891**: Web 网关中编辑定时任务导致 API 422 错误。无直接修复 PR。

- **S2 - 功能降级**:
    - **#8386**: SQLite 作为默认内存后端，但快速入门没有引导用户配置嵌入模型，导致混合搜索静默降级为仅关键词搜索。无直接修复 PR。
    - **#7862**: OpenAI 兼容提供方发送空工具列表时触发 HTTP 400 错误。**已有修复 PR (#8474, #8473, #8471) 待合并**。
    - **#8410**: 通道任务（如条件性回复）缺乏“无回复”的意图状态，导致代理在不该回复时依旧发送空消息。无直接修复 PR。

## 6. 功能请求与路线图信号

- **Delegation 模式增强**: 【Issue #8238】提议增加**独立委托模式 (independent delegate mode)**，允许专门化的 Agent 完全按照自己的策略和工具集运行，而不仅仅遵循主 Agent 的委托限制。此功能在 #7514 和 #7590 中已有铺垫，很可能被加入 v0.9.0 或更高版本。
- **网关 WebSocket 生命周期解耦**: 【Issue #7759】提议将 WebSocket 连接视为**传输通道**而非任务生命周期管理者，支持断线重连后恢复进行中的 Agent 推理。这是一个对 Web UI 体验影响重大的 P1 请求，可能在 v0.8.x 系列中看到进展。
- **离线定价目录**: 【PR #8380】除了网关实时定价，增加了**离线、静态的价格目录**，适用于自托管或私有化部署场景。这表明项目正积极考虑企业和本地化部署的完整需求。

## 7. 用户反馈摘要

- **迁移用户的痛苦**：来自 Issue #6969 的用户反馈揭示了从 Letta 等平台迁移过来的用户面临的 “**定制化输出路由**” 功能缺失问题，认为当前的回复方式过于单一，无法满足真实世界的多样化需求。
- **开箱即用体验**：Issue #8386 的反馈核心是 **Quickstart 引导不够完善**，导致新用户极易进入“配置不一致”的陷阱（混合搜索降级却不自知），这对新用户留存是一个潜在风险。
- **macOS 键盘快捷键问题**：Issue #7800 报告了 ZeroCode TUI 中 **快捷键与 macOS 不兼容**、且难以发现的问题，体现了跨平台体验优化的必要性。

## 8. 待处理积压

- **高优先级 Bug 等待修复 PR**:
    - **#6361** [Bug]: context_compression drops assistant(tool_calls) and tool(result) entirely for OpenAI-compatible providers (e.g. MiniMax), causing tool loops... 风险: **high**。
    - **#6891** [Bug]: Scheduled Jobs edit error API 422 风险: **medium**。
    - **#5808** [Bug]: Default 32k context budget is exceeded by system prompt + tool definitions on iteration 1... 风险: **high**。
    - **#7800** [Bug]: Code help/keybindings are misleading or unreachable, especially on macOS 风险: **medium**。

    *以上 Issue 均长期开放，严重程度高，且截至今日没有明确的修复 PR，建议维护者重点关注。*

</details>

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*