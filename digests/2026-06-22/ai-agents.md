# OpenClaw 生态日报 2026-06-22

> Issues: 500 | PRs: 500 | 覆盖项目: 13 个 | 生成时间: 2026-06-22 04:10 UTC

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

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，我已根据您提供的 OpenClaw GitHub 数据，为您生成了 2026-06-22 的项目动态日报。

---

# OpenClaw 项目日报 | 2026-06-22

## 1. 今日速览

今日 OpenClaw 项目活动极其活跃，共产生 1000 条相关更新（Issues 和 PRs 各 500 条）。项目正处于高频迭代与问题密集爆发的阶段。**活跃度评估：极高**。虽然有一个新的 Beta 版本发布，但社区反馈显示 P0/P1 级别的严重 Bug（如内存泄漏、消息丢失、Session 状态损坏）仍大量存在，且修复 PR 积压严重（待合并 390 条）。项目在积极修复，但快速迭代也带来了一定的稳定性挑战，社区用户的忍耐度正在受到考验。

- **最新版本**: `v2026.6.10-beta.1`
- **新 Issue 趋势**: 问题主要集中在 Session 状态一致性、消息传递丢失、Gateway 稳定性及内存泄漏。
- **社区情绪**: 部分用户因稳定性问题表达不满（如放弃使用、被阻断工作流），但也有大量用户积极参与 Bug 复现和定位，社区活跃度高。

## 2. 版本发布

### `v2026.6.10-beta.1`

- **链接**: [Release v2026.6.10-beta.1](https://github.com/openclaw/openclaw/releases/tag/v2026.6.10-beta.1)
- **核心更新亮点**: 此版本重点改善了 Agent 运行时的可靠性和会话状态管理。具体修复包括：
    - 保留待处理的子代理完成通知。
    - 确保持久化聊天记录在紧凑后不为空。
    - 修复了媒体索引对齐问题。
    - 重启休眠的后续任务。
    - 一致性地解决压缩模型别名问题。
- **迁移注意事项**: 此次为 Beta 版本，未提及重大破坏性变更（Breaking Changes）。建议开发者和用户在测试环境充分验证后再用于生产。

## 3. 项目进展

今日无已合并的重要 PR。这表明项目的主要精力仍集中在处理大量积压的 Issues 和待审核的 PR 上。尽管有 110 个 PR 被合并或关闭，但由于数据提供的是“评论数最多”的 30 个 PR，其中大部分仍处于开放状态，显示出维护者团队正在持续审查代码，但审查流程可能面临瓶颈。

## 4. 社区热点

以下是今日讨论最热烈的几个议题，反映了社区最大的痛点：

1.  **Gateway 内存泄漏导致 OOM**
    - **Issue**: [#91588](https://github.com/openclaw/openclaw/issues/91588)
    - **核心诉求**: Gateway 进程内存从 350MB 持续增长至 15.5GB，2-3 天后触发 OOM 并进入重启循环。这是最严重的稳定性问题，社区用户迫切需要修复。

2.  **Anthropic Thinking 签名无效 & 错误文本泛化**
    - **Issue**: [#92201](https://github.com/openclaw/openclaw/issues/92201)
    - **核心诉求**: 嵌入式 Runner 在回放流式 Thinking 签名时偶发无效，但由于错误信息被泛化，导致恢复机制无法触发。用户希望有更精确的错误处理和恢复流程。

3.  **Agent 在 Telegram 上重复回复**
    - **Issue**: [#86519](https://github.com/openclaw/openclaw/issues/86519)
    - **核心诉求**: 自 5.20 版本更新后，Agent 在 Telegram 平台经常发送 2-10 次重复的回复。这严重影响了用户体验，是一个典型的、急需解决的回归问题。

4.  **会话模型切换后内部状态未刷新**
    - **Issue**: [#92415](https://github.com/openclaw/openclaw/issues/92415)
    - **核心诉求**: 使用 `/model` 命令切换模型后，`AgentSession` 内部的模型快照并未更新，导致上下文窗口、推理参数等 8 个后续操作使用了错误的旧模型配置。核心状态管理机制存在缺陷。

## 5. Bug 与稳定性

按严重程度排列今日最值得关注的 Bug：

| 严重等级 | Issue 编号 | 问题摘要 | 是否有 Fix PR |
| :--- | :--- | :--- | :--- |
| **P0** | [#91588](https://github.com/openclaw/openclaw/issues/91588) | Gateway 严重内存泄漏，导致 OOM 崩溃。 | 无 |
| **P0** | [#95623](https://github.com/openclaw/openclaw/issues/95623) | `tool_use.id` 清洗器未能处理 OpenAI 跨提供商故障转移后的复合 ID，导致 Anthropic 返回 400 错误，阻塞会话。 | 无 |
| **P1** | [#95495](https://github.com/openclaw/openclaw/issues/95495) | 版本升级时，存储迁移未被警告，导致 1499 个文件被重嵌入，造成数据丢失和性能问题。 | 无 |
| **P1** | [#92043](https://github.com/openclaw/openclaw/issues/92043) | 压缩超时（180s）是单个墙钟，无法在长的管道中复用部分进度，导致合法长压缩每次都失败。 | 无 |
| **P1** | [#86519](https://github.com/openclaw/openclaw/issues/86519) | Agent 在 Telegram 平台重复回复的回归问题。 | 无 |
| **P1** | [#90082](https://github.com/openclaw/openclaw/issues/90082) | `active-memory` 插件的断路器过于激进，熔断后向主 Session 注入无用提示，污染上下文。 | 无 |
| **P1** | [#93858](https://github.com/openclaw/openclaw/issues/93858) | 自动回复的 `foreground fence` 设计仍有缺陷，导致旧回复在途时新消息可以交错处理。 | 无 |

## 6. 功能请求与路线图信号

- **话题会话家族**：[#90916](https://github.com/openclaw/openclaw/issues/90916)
  - **信号**：一个 P2 功能请求，要求为单个助手/角色提供多个命名的“话题车道”，每个车道有独立的短期上下文，但共享长期记忆。这反映了用户对更精细会话管理的需求，可能被纳入未来大版本。
- **Kubernetes 部署文档更新**：[#91455](https://github.com/openclaw/openclaw/issues/91455)
  - **信号**：用户反馈 Kubernetes 部署文档不够直观，且缺少 Helm Chart。虽然项目当前认为单容器不适合 Helm，但社区需求表明这是企业级部署的障碍，值得项目组重新考虑。
- **子 Agent 编排能力**：[#92369](https://github.com/openclaw/openclaw/issues/92369)
  - **信号**：Cron 隔离会话中的子 Agent 编排（并行生成、等待、聚合结果）无法可靠工作。这是一个关键的功能缺口，影响了复杂自动化工作流的构建。

## 7. 用户反馈摘要

- **痛点**:
  - **稳定性堪忧**: "在 DigitalOcean 2vCPU/4GB droplet 上运行 OpenClaw，摩擦太大，正在拆除它。" ([#88087](https://github.com/openclaw/openclaw/issues/88087))
  - **破坏性更新无警告**: "2026.6.9 静默地迁移了内存存储位置，没有任何升级警告，导致 1499 个文件被迫重新嵌入。" ([#95495](https://github.com/openclaw/openclaw/issues/95495))
  - **调试困难**: "`launchd` plist 将 `StandardErrorPath` 硬编码为 `/dev/null`，所有 Gateway 的 stderr 日志都被丢弃了。" ([#90711](https://github.com/openclaw/openclaw/issues/90711))
  - **安全与隐私**: "2026.6.5 更新后，内部 Agent 的推理/思考过程被暴露给了用户，这是重大的隐私和 UX 回归。" ([#91804](https://github.com/openclaw/openclaw/issues/91804))
- **使用场景**:
  - 用户依赖 Cron 和子 Agent 构建自动化的周期任务和并行处理流水线。
  - Telegram, Slack, Discord, Feishu 等多渠道集成是核心使用场景。
  - `active-memory`、知识库、`web_fetch` 等插件被广泛使用。

## 8. 待处理积压

以下为长期未响应或状态停滞，但影响巨大的重要 Issue/PR，提醒维护者关注：

- **长时间未合并的 PR**:
    - [#85249](https://github.com/openclaw/openclaw/pull/85249): 修复 Cron 隔离执行器中 `undefined` `sourceDelivery` 的问题。已创建超过一个月（2026-05-22），状态仍为 `ready for maintainer look`，但评论数为 undefined，可能被遗漏。
    - [#58993](https://github.com/openclaw/openclaw/pull/58993): 修复 Google Chat 的 DM 检测问题。已创建超过两个月（2026-04-01），虽然状态为 `ready for maintainer look`，但存在 `stale` 标签，需要维护者评估其优先级。
- **长期存在的关键 Issue**:
    - [#86519](https://github.com/openclaw/openclaw/issues/86519): Telegram 重复回复的回归 Bug，已存在近一个月，社区影响大，需要优先解决。
    - [#43564](https://github.com/openclaw/openclaw/issues/43564): ACP Session 技能上下文注入的功能请求，已存在 3 个月，维护者在[#93884](https://github.com/openclaw/openclaw/issues/93884)中讨论了 Gateway 主机运行时边界，需要对此类长期路线图问题进行明确回应。

---

## 横向生态对比

好的，作为专注于 AI 智能体与个人 AI 助手开源生态的资深技术分析师，我将基于您提供的各项目日报摘要，为您生成一份横向对比分析报告。

---

### AI 智能体与个人 AI 助手开源生态横向对比分析报告 (2026-06-22)

#### 1. 生态全景

当前生态正处于 **“从功能堆砌到质量巩固”** 的阵痛与转型期。整体呈现出 **极高的社区活跃度**，但高频迭代也导致了 **稳定性问题和安全漏洞集中爆发**。多项目在核心稳定性（消息丢失、会话状态损坏、内存泄漏）和安全边界（MCP工具白名单绕过、SSRF防护、代理审批走私）上遭遇严重挑战，表明快速创新正在超越工程稳健性。同时，用户需求正从单一对话向 **可编排的工作流、精细的会话管理、移动端适配以及企业级部署** 演进，社区贡献者开始自发补位解决特定场景痛点（如移动端适配）。

#### 2. 各项目活跃度对比

| 项目名称 | Issues 数 (近24h) | PRs 数 (近24h) | 版本发布 | 健康度评估 | 活跃度评估 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 500 (新) / 500 (PR) | 500 (开放) | 1 (Beta) | **待修复** (P0/P1 Bug 堆积，修复积压) | **极高** |
| **NanoBot** | 7 (新/活跃) | 15 (合并/关闭) | 0 | **良好** (安全响应快，修复密集) | **极高** |
| **Hermes Agent** | 37 (新/活跃) | 46 (待合并) | 0 | **良好** (功能/修复 PR 活跃，但积压高) | **极高** |
| **PicoClaw** | 6 (新) | 29 (合并) | 1 (Nightly) | **优秀** (一次合并大量PR，版本迭代快) | **高** |
| **NanoClaw** | 2 (新, 均为高危安全) | 7 (新) | 0 | **风险** (待修复关键安全漏洞，无应对) | **中** |
| **NullClaw** | 1 (新) | 0 | 0 | **警告** (核心功能高频失败，维护静默) | **低** |
| **IronClaw** | 6 (新/关闭) | 29 (新/合并) | 0 | **良好** (CI稳健性提升，主线开发明确) | **中高** |
| **LobsterAI** | 1 (新, 安全) | 0 | 0 | **待观察** (历史Bug未修复，安全新隐患) | **中** |
| **CoPaw** | 15 (新) | 29 (新/合并) | 0 | **良好** (社区贡献活跃，移动端适配启动) | **高** |
| **ZeptoClaw** | 1 (关闭) | 1 (关闭) | 0 | **优秀** (专注CI工艺，小而美) | **低** |
| **ZeroClaw** | 50+ (新/活跃) | 45 (待合并) | 0 | **待观察** (高贡献但高积压，并行版本多) | **极高** |
| **TinyClaw** | 0 | 0 | 0 | **静默** | **无** |
| **Moltis** | 0 | 0 | 0 | **静默** | **无** |
| **CoPaw** | 15 | 29 | 0 | **良好** | **高** |

#### 3. OpenClaw 在生态中的定位

- **核心参照与生态底座**: OpenClaw 以极高的 Issue/PR 活跃度（1000条/天）稳居生态核心参照位。其庞大的社区规模和问题数量（P0/P1 Bug 堆积）表明它是功能最全面、集成最复杂的项目之一，但问题规模也反映了其快速迭代对稳定性的挑战。
- **技术路线优势**: 作为“核心参照”，OpenClaw 的架构（Gateways, Sessions, Cron, Sub-Agents）是最复杂的。其尝试解决的 Session 一致性、消息传递可靠性、子 Agent 编排等问题，是其他项目未来可能面临的。它像一面镜子，映射出生态的通用痛点（如内存泄漏、状态损坏）。
- **与同类相比**:
    - **vs. NanoBot / Hermes Agent**: OpenClaw 更侧重“一体化”完整解决方案（含所有频道、所有模式），生态系统较全面，但问题也最多。NanoBot/Hermes 则更聚焦于安全、特定提供商适配和核心引擎稳定性，其问题规模和处理效率（如快速修复安全漏洞）表明它们在稳定性上更胜一筹。
    - **vs. PicoClaw / IronClaw**: PicoClaw 在一个更小的代码库上实现了极高的 PR 合并效率，项目健康度极佳。IronClaw 则像是 OpenClaw 的“企业级/重构版”，专注于学习系统和并发执行等关键模块，体现了从“能做”到“做稳定”的演进方向。

#### 4. 共同关注的技术方向

多个项目不约而同地涌现出以下需求，标志着行业共识：

1.  **安全性是首要挑战**:
    - **MCP 工具/资源白名单绕过**: **NanoBot (#4434/5)**、**ZeroClaw (#7747/8120)**。核心诉求是严格限制 Agent/模型的 API 调用权限，防止恶意工具或资源泄露。
    - **审批/配置显示隐藏（审批走私）**: **NanoClaw (#2827)**。要求审批流程对用户完全透明，隐藏参数。
    - **SSRF 防护削弱**: **LobsterAI (#2181)**、**ZeroClaw (#5918)**。默认安全配置被攻击，要求加强。
2.  **核心稳定性与状态管理**:
    - **消息/工具调用丢失与重复**: **OpenClaw (#95623)**、**NanoBot (#4442)**、**CoPaw (#5344)**。流式场景下工具调用 ID 重复、消息丢失导致会话中断。
    - **内存泄漏/性能退化**: **OpenClaw (#91588 / Gateway OOM)**、**CoPaw (#5354 / 切换卡死)**。长时间运行后资源耗尽、OOM。
    - **插件系统/容错性**: **CoPaw (#4889 / 插件加载器)**、**ZeroClaw (#6361 / 上下文压缩丢失)**。跨平台、跨供应商的兼容性和错误恢复。
3.  **精细化管理与用户体验**:
    - **多渠道/多会话管理**: **OpenClaw (#90916 / 话题车道)**、**Hermes Agent (#10452 / 多Telegram机器人)**。用户需要按话题/工作区分隔会话，而非单一聊天。
    - **移动端/跨平台适配**: **CoPaw (大量PR)**、**PicoClaw (#3090 / iOS Safari)**。用户对移动浏览器和跨平台兼容性要求提高。
    - **只读/隔离模式**: **NanoBot (#4440 / 只读会话)**、**OpenClaw (#93858 / Foreground Fence)**。为降低成本或增强安全性，需要只读历史、隔离工作流。

#### 5. 差异化定位分析

| 维度 | OpenClaw | NanoBot | Hermes Agent | PicoClaw | IronClaw | ZeroClaw |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **功能侧重** | 全功能一体化（代理、网关、插件、任务） | 安全、轻量、MCP 生态 | 多提供商适配、DeskTop/TUI 体验 | 核心稳定性、跨平台、成本优化 | 企业级/重构、学习系统、可观测性 | 渠道扩展、WASM 外挂、企业级 |
| **目标用户** | 需要完整解决方案的开发者/团队 | 注重安全和稳定性的个人/团队 | 深度用户、多模型/平台使用者 | 资源敏感型设备、小团队 | 追求高可靠性、高自动化平台的企业 | 需要跨平台、多渠道的开发者/团队 |
| **技术架构** | 模块化重架构（Gateways/Sessions） | 轻量、插件式架构（MCP 优先） | 插件式架构，强 Provider 层 | 模块、配置驱动，强调健壮性 | CI 驱动、模块化、前瞻性设计 | 多版本 (v0.8.x) 并行，WASM 沙箱 |
| **健康度/策略** | 范围大、问题多、迭代快 | 代码审查严格，安全响应迅速 | 社区贡献活跃，但待合并 PR 多 | 合并效率高、版本迭代稳健 | 主干开发清晰、CI 稳健性投入大 | 社区高积压，并行开发风险高 |

#### 6. 社区热度与成熟度

- **快速迭代/功能堆砌阶段** (高热度，高 Bug 率):
    - **OpenClaw, ZeroClaw**: 功能全面但稳定性堪忧，社区更新频繁但维护压力大。
- **质量巩固/安全加固阶段** (高热度，修复密集):
    - **NanoBot, IronClaw, CoPaw**: 积极修复稳定性和安全问题，社区贡献转化率高，项目健康度在提升。
- **小众/专注/高质量阶段** (中低热度，高确定性):
    - **PicoClaw, ZeptoClaw**: 定位清晰，代码库小，合并效率极高，项目健康度好，适合对稳定性极为敏感的开发者。
- **处于风险/静默阶段** (低热度，问题待解决):
    - **NanoClaw, NullClaw, LobsterAI**: 存在待解决的关键安全或可用性问题，可能影响长期信誉。

#### 7. 值得关注的趋势信号

1.  **Agent 间的信任模型是下一个“雷区”**: NanoClaw 披露的目录穿越和审批走私漏洞，揭示了 Agent 互相通信（A2A）和自修改审批流程中的深层信任危机。未来安全研究将集中在 Agent 间的权限隔离和上下文验证上，而非仅关注模型 Prompt 注入。
2.  **“CI 即护城河”策略兴起**: ZeptoClaw 将 `binary-size` 设为合并门禁，IronClaw 投入大量精力优化 CI 缓存和重试。这表明头部项目开始将 **构建与发布工程** 视为核心竞争力的关键部分，以此来维护代码质量、控制二进制膨胀和提升部署确定性。
3.  **“个人 AI 助手”向“个人知识工作站”演进**: LobsterAI 用户提出的批量导出、消息书签、会话标签分类等需求，以及 NanoBot 提出的只读会话、搜索历史工具，共同描绘了未来个人 AI 助手不再是单一聊天框，而是一个 **知识管理、信息检索和自动化工作流的整合平台**。
4.  **渠道之争进入细分领域**: 基础渠道（Telegram, Slack等）基本成熟，但用户对 **国内平台（QQ via NapCat）、去中心化协议（SimpleX/Tox）、以及通用性更强的 Webhook** 的呼声更高。项目的渠道适配能力将成为决定其在全球特定市场触达率的关键。
5.  **对“静默失败”零容忍**: 无论NanoBot用户对`agent`静默停止的描述，还是OpenClaw、CoPaw用户对消息丢失的激烈反应，都表明用户最大的痛点不是Bug本身，而是**不可感知、不可恢复的失败状态**。这要求开发者必须提供精确的错误处理、超时重试以及优雅降级机制。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

好的，作为NanoBot项目的AI智能体与个人AI助手领域开源项目分析师，我已根据您提供的2026-06-22日GitHub数据，生成了以下项目动态日报。

---

### NanoBot 项目动态日报 | 2026-06-22

**数据快照日期：** 2026-06-22

---

#### 1. 今日速览

今日项目活跃度极高，社区贡献热情高涨。核心聚焦于**安全漏洞修复**与**稳定性增强**。两个关于MCP `enabledTools` 白名单绕过的高危安全问题被报告并迅速得到了修复PR。与此同时，针对流式响应中重复工具调用ID导致会话中断的严重Bug (#4442) 也收到两个修复方案。功能层面，对钉钉、Telegram等渠道的增强以及长期悬而未决的Mattermost集成请求 (#1011) 被重新激活。尽管无新版本发布，但项目正通过密集的PR合入快速迈向更稳定、更安全的 `v0.2.2`。

---

#### 3. 项目进展

过去24小时有 **15个PR被合并或关闭**，展示了高效的协作节奏。以下为关键进展：

- **安全加固 (优先级最高):** PR #4436 `fix(tools): gate MCP resource and prompt registration behind enabledTools` 被合并，修复了MCP插件资源（Resources）和提示（Prompts）可绕过 `enabledTools` 白名单限制的安全漏洞。这是对今日两个安全报告Issue (#4434, #4435) 的直接响应。
- **稳定性修复:**
    - PR #4206 `feat(dingtalk): add group_allow_from for group chat allowlist` 已合并，为钉钉渠道提供了群聊白名单支持。
    - 多个针对不同模块的修复PR（如 #4444, #4443针对重复工具ID、#4433修复配对存储中的类型强制转换问题）已进入开放状态，等待最终审核和合并。
- **功能推进:**
    - #4446 `feat(dingtalk): gate private chats and mention sender in group replies` 为钉钉渠道增加了 `disable_private_chat` 配置和@发送者的能力。
    - #4441 `fix(mcp): force-close streamable_http generator on reconnect failure` 解决了MCP服务器重连失败时集群崩溃的问题，提升了整体可用性。

项目整体正通过快速响应安全报告和社区Bug，从“功能堆砌”阶段进入到“精细化打磨”阶段，健康度显著提升。

**链接:**
- MCP安全修复PR: https://github.com/HKUDS/nanobot/pull/4436
- 钉钉群聊白名单PR(已合并): https://github.com/HKUDS/nanobot/pull/4206
- 钉钉功能增强PR: https://github.com/HKUDS/nanobot/pull/4446

---

#### 4. 社区热点

- **Mattermost集成请求 (#1011):** 这是一个持续了4个月的Issue，拥有 **4个👍**。用户表达了对Mattermost作为聊天渠道的支持需求，并对比了Discord、Telegram、Slack和WhatsApp的隐私、商业性或使用门槛问题。该Issue于今日更新，表明社区对去中心化、隐私友好的渠道支持仍有强烈诉求。

    **链接:** https://github.com/HKUDS/nanobot/issues/1011

- **安全和稳定性讨论 (多个Issues/PRs):**
    两项关于MCP安全问题的Issue(#4434, #4435) 和一例严重的会话污染Bug (#4442) 在短时间内获得了大量关注。这反映出随着NanoBot在MCP生态和高级流式推理中的使用加深，用户对**安全边界**和**运行时健壮性**的关注达到了新的高度。尤其是 #4442，它描述的用户场景（agent悄无声息地停止响应）对个人AI助手是致命的。
    **链接:**
    - 安全报告 #4434: https://github.com/HKUDS/nanobot/issues/4434
    - 安全报告 #4435: https://github.com/HKUDS/nanobot/issues/4435
    - 严重Bug #4442: https://github.com/HKUDS/nanobot/issues/4442

---

#### 5. Bug 与稳定性

- **[关键] MCP `enabledTools` 白名单绕过 (安全性):** Issue #4434 和 #4435 揭露了配置为 `[]`（禁止所有工具）时，资源（Resources）和提示（Prompts）仍能被暴露给模型，构成严重安全风险。
    - **状态:** 已修复。Fix PR #4436 已合并。
    - **影响:** 所有配置了MCP服务器并期望通过 `enabledTools` 进行严格访问控制的用户。

- **[关键] 流式响应中重复 `tool_use` ID导致会话中断 (稳定性):** Issue #4442 描述了Anthropic系列模型在流式响应中可能产生重复的 `tool_use` ID，导致整个会话永久性地被API拒绝（400错误），agent静默停止。
    - **状态:** 有2个修复PR (#4443, #4444) 在开放中。
    - **影响:** 使用Anthropic系列模型（如Claude）的所有用户。

- **[中] `Nanobot.run()` 钩子非并发安全:** Issue #4408 揭示了当用户使用`Nanobot.run()`并传入`hooks=`参数时，由于内部`_extra_hooks`被共享和修改，会导致多个并发运行调用发生竞态条件。
    - **状态:** 已关闭，但未关联PR，修复方法待确认。可能指出的问题已经修复或已被其他重构覆盖。

**链接:**
- 重复ID Bug: https://github.com/HKUDS/nanobot/issues/4442
- 并发安全Bug: https://github.com/HKUDS/nanobot/issues/4408

---

#### 6. 功能请求与路线图信号

- **[强信号] Telegram Bot API 10.1 富消息支持:** Issue #4413 提出了支持Telegram新富消息格式的请求。该请求已由PR #4422 实现并合并（CLOSED），表明项目对上游平台新特性的响应非常迅速。这极大概率会包含在下一个版本中。
- **[强信号] 只读会话和搜索历史工具:** Issue #4440 和 PR #4439 提出了一个只读的 `search_history` 工具，让Agent能检索历史记忆文件。这解决了大型项目中上下文窗口限制的痛点。同时，PR #4271 提出的 `read_only` 会话功能也能优化CPU/API消耗。这两个是提升“AI个人助手”实用性的关键信号。
- **[中信号] 钉钉和Cron功能增强:** PR #4225 为Cron任务增加静默模式，PR #4446 为钉钉增加私聊开关和提及功能。这些是针对特定部署场景的精细化控制，表明项目正朝着“企业级可用性”迈进。

**链接:**
- Telegram富消息PR(已合并): https://github.com/HKUDS/nanobot/issues/4422
- 搜索历史工具PR: https://github.com/HKUDS/nanobot/pull/4439
- 只读会话PR: https://github.com/HKUDS/nanobot/pull/4271

---

#### 7. 用户反馈摘要

- **核心痛点:**
    - **性能瓶颈:** 用户 `codeLong1024` 在#4420中指出，`estimate_prompt_tokens` 函数在每次迭代时都对静态的工具定义进行 `tiktoken` 编码，造成了显著的性能浪费，这在长期运行的“数字员工”场景中尤为突出。这是一个高质量的用户反馈，直接指向性能优化点。
    - **无法恢复的故障:** 用户 `tedyan` 在#4442中描述了因重复`tool_use` ID导致整个会话“中毒”，agent“静默停止”的严重问题。这表明用户最反感的不完全是Bug本身，而是“静默失败”这种无法感知、无法恢复的崩溃体验。
- **使用场景:**
    - 用户 `matthiasg` (#1011)明确表达了对Mattermost集成以替代其他平台的隐私性考虑。
    - 用户 `waelantar` (#4440， #4433)积极参与功能设计，其提出的 `search_history` 工具和修复的配对问题显示了深度用户对项目内部机制的熟悉和对长期记忆、系统键可靠性的重视。

**链接:**
- 性能优化诉求: https://github.com/HKUDS/nanobot/issues/4420
- 会话崩溃反馈: https://github.com/HKUDS/nanobot/issues/4442

---

#### 8. 待处理积压

1.  **PR #1854: 统一守护进程网关** (创建: 2026-03-11)
    - **状态:** 长期开放，至今无维护者回复。这是一个大型特性，意在统一不同平台的守护进程启动和管理。由于其复杂度高、风险大，可能被项目组搁置。
    - **提醒:** 建议维护者评估是否接受此方案，或给出指导方向，否则可能挫伤贡献者积极性。
    - **链接:** https://github.com/HKUDS/nanobot/pull/1854

2.  **Issue #1011：Mattermost Bot** (创建: 2026-02-22)
    - **状态:** 虽今日有更新，但仍无任何来自官方或社区的实质性进展（如WIP PR）。4个👍表明其社区需求明确。
    - **提醒:** 项目组应考虑将此需求标记为“help wanted”或“good first issue”，或将此作为一个“渠道适配器”的样板案例，指导贡献者开发。
    - **链接:** https://github.com/HKUDS/nanobot/issues/1011

3.  **PR #3869: DeepSeek消息处理兼容性** (创建: 2026-05-16)
    - **状态:** 开放超过一个月，旨在修复DeepSeek provider的多个消息格式问题。此类修复对于模型支持的稳定性至关重要。
    - **提醒:** 如果该PR的解决方案正确，应尽快推进合并，以稳定对DeepSeek模型的用户体验。
    - **链接:** https://github.com/HKUDS/nanobot/pull/3869

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

好的，这是为您生成的 Hermes Agent 项目动态日报。

---

## Hermes Agent 项目动态日报 | 2026-06-22

### 1. 今日速览

今日项目活跃度极高，社区贡献热情高涨。过去24小时内有大量 Issue 和 PR 被创建或更新，其中新开/活跃 Issue 达37个，待合并 PR 高达46个，表明项目正处于快速迭代期中。社区焦点主要集中在 **Google Gemini/Code Assist 服务下线后的紧急替代方案** 以及 **DeskTop/TUI 应用体验打磨** 上。多个关键的 Bug 修复和高优先级的特性 PR 于今日被提交，显示了项目维护者和社区贡献者对稳定性和新功能的高度关注。虽然无新版本发布，但积压的 PR 数量暗示下一次可能是一个包含众多破坏性变更的大版本。

### 2. 版本发布

无

### 3. 项目进展

尽管没有新的合并，但今日提交的 PR 展现了项目在两个关键方向上的重大推进：

- **服务商适配与身份验证**：面对 Google Gemini CLI 在6月18日的正式下线，社区积极响应。PR `#50033` 和 `#50064` 分别旨在让 Hermes 模拟 `@google/gemini-cli` 和 `@github/copilot` 的真实身份，以确保对各自后端 API 的正确调用。这直接回应了用户的紧急需求，是保证这些核心提供商能够继续工作的关键步骤。
- **核心引擎稳定性与性能**：PR `#50584`、`#50593` 和 `#50595` 系列工作通过将 `time.time()` 替换为 `time.monotonic()` 来修复因系统时钟调整（如NTP同步）导致的计时异常。这将显著提升会话时间追踪、工具执行测量和API调用耗时的准确性，是提升系统稳定性的重要基础优化。

### 4. 社区热点

- **`google-gemini-cli` 下线余波**：Issue `#29294` 和 `#44943` 虽然已关闭，但关于 Google Gemini CLI 停服的讨论持续高热。紧随其后的 Bug 报告 `#49701` 和 `#49705` 确认了该提供商已完全无法使用，激起了大量用户的不满和对替代方案 `antigravity` 的迫切需求。新的 Bug 报告 `#50530` 则深入揭露了 `antigravity` 提供商在实际使用中暴露的三个 P2 级别的严重问题，表明过渡并非一帆风shun。这成为了今日社区最关注的话题。
- **多 Telegram 机器人支持**：Issue `#10452` 虽创建较早，但今日仍有新评论，获得了7个评论和4个点赞。该需求意在让 Hermes 网关支持并路由多个 Telegram 机器人，反映了用户在生产环境中对更复杂、更灵活的消息管理架构的真实需求。

### 5. Bug 与稳定性

今日报告的 Bug 主要集中在桌面应用、CLI 和核心代理功能上。

| 严重级别 | Issue # | 标题 | 状态 | Fix PR |
| :--- | :--- | :--- | :--- | :--- |
| **P2** | `#50530` | google-antigravity 遗留 P2 集成问题汇总 | OPEN | 暂无 |
| **P2** | `#49983` | OpenRouter free models fail with HTTP 404 | OPEN | 暂无 |
| **P2** | `#50292` | Bedrock 非 Claude 模型路由到 Anthropic SDK 报错 | OPEN | 暂无 |
| **P2** | `#50404` | Discord 配置未按配置文件隔离 | OPEN | 暂无 |
| **P2** | `#50449` | Desktop “Thinking” 开关回弹，配置写错位置 | OPEN | `#50585` |
| **P2** | `#50553` | 切换配置不生效 | CLOSED | 已修复 |
| **P3** | `#37505` | macOS DMG 仅支持 arm64，Intel Mac 用户无法启动 | OPEN | 暂无 |
| **P3** | `#37917` | Windows桌面版 Ctrl+缩放快捷键无效 | OPEN | 暂无 |

**要点分析**：
- **`#50530` (google-antigravity)**：这是对 `google-gemini-cli` 替代服务的深度质量报告，指出了子代理崩溃、并发掉线和400错误，严重影响了核心功能体验。
- **`#49983` (OpenRouter Free Tier)**：OpenRouter 的免费模型因工具调用不受支持而返回404，对于使用免费服务的用户是严重的阻碍。
- **`#50449` (Thinking Toggle)**：“Thinking”开关的 UI 状态与应用配置不一致，是一个影响用户对 Reasoning 功能控制的体验问题，已有对应的 PR 修复。

### 6. 功能请求与路线图信号

- **核心集成**：多项高价值 PR 清晰指向了下一次大版本升级。
    - **AntiGravity / Copilot 身份伪装**：`#50033`, `#50064` 等 PR 暗示 Hermes 计划通过“伪装”成官方客户端身份，来确保对特定后端 API 的正常访问。这并非传统意义上的功能，而是一种重要的兼容性策略。
    - **Kanban Board 集成**：Issue `#41222` 呼声较高，提议将看板功能直接集成到桌面应用内，减少用户在 CLI 和 GUI 间的切换摩擦。这表明用户希望 Hermes 成为一个更整合的“一体化”工作平台。
    - **自我托管 Mem0 内存**：Issue `#31135` 请求为 Mem0 插件增加自托管选项，以满足对数据隐私和离线运行有更高要求的用户。
- **用户体验优化**：
    - **系统托盘**：`#50167` 请求桌面应用最小化到系统托盘，而非完全退出，这是桌面应用用户的常见需求。
    - **TUI 抓取与桌面应用同步**：PR `#50586` 修复了 TUI 创建的会话在工作区分组中显示为“无工作区”的问题，这是一个对桌面应用用户友好的改进。

### 7. 用户反馈摘要

- **对自动标题重复的不满**：用户 `jmelchiori` 在 Issue `#50537` 中反映，当两个会话生成相同的自动标题时，程序会抛出一个被静默吞掉的错误，导致标题设置失败。这是一个用户界面细节上的摩擦。
- **对 API 错误信息可读性的期望**：用户 `Jhdeval` 在 Issue `#50460` 中请求将难以理解的 API 错误（如 `HTTP 404`）转化为“已达到使用限制，将于2026-06-22 00:31:02 UTC重置”之类的人类可读信息。这反映了用户对于更友好、更人性化的错误提示的普遍诉求。
- **对图片上传体验的反馈**：用户 `linfeng961` 在 Issue `#50554` 中详细描述了桌面应用图片上传时的两个体验问题（纵向排列浪费空间、图片遮盖文字），并给出了清晰的期望行为（横向自动换行）。这表明用户对日常使用的 UI/UX 细节要求很高。

### 8. 待处理积压

- **#18034 [P2] fix(gateway): compact responses terminal tool outputs**: 一个来自 **2026年4月30日** 的 PR，旨在压缩终端工具输出，至今仍未合并。该项目已提交近两个月，对于改善网关性能和数据传输效率至关重要，提醒维护者关注。
- **#15151 [P3] [i18n] Thai Translation**: 持续近两个月的泰语翻译任务，虽然优先级不高，但长期未关闭可能会给社区翻译贡献者带来负面信号，建议维护者进行审查并合并或给出指导。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

好的，这是根据您提供的 PicoClaw 项目数据生成的 2026-06-22 项目动态日报。

---

## PicoClaw 项目日报 — 2026-06-22

### 1. 今日速览

项目今日活跃度极高，共处理了 38 项议题与合并请求，显示出强大的社区参与度和维护效率。核心亮点是发布了新的 Nightly 版本，并一次性合并了 29 个 PR，涵盖了从核心消息总线压力处理到 Web UI 流式体验和配置管理的多项重大功能与稳定性修复。社区讨论主要集中在新通讯协议集成需求、跨平台兼容性问题以及与特定大模型（如 Volcengine Doubao）的集成 bug 上。项目整体健康状况良好，处于快速迭代和功能增强阶段。

### 2. 版本发布

- **Nightly 构建发布：`v0.3.0-nightly.20260622.287853ab`**
    - **链接**: [https://github.com/sipeed/picoclaw/compare/v0.3.0...main](https://github.com/sipeed/picoclaw/compare/v0.3.0...main)
    - **说明**: 这是一个自动化的每日构建版本，可能不稳定，仅供测试使用。此版本包含了截止到当前 `main` 分支的所有最新提交。

### 3. 项目进展

今日合并/关闭了 29 个 PR，标志着多项重要功能的最终落地，项目在核心性能和用户体验方面迈出了坚实的一步。以下是关键进展：

- **核心稳定性与性能提升**:
    - `#2906` **修复消息总线背压处理**：引入了有界等待机制，当队列饱和时不再无限阻塞，并记录每流丢弃统计信息，大幅提升了系统在高负载下的稳定性和可见性。
    - `#2905` **修复过期上下文的回退链处理**：优化了提供者回退逻辑，当请求上下文过期时能立即停止尝试后续候选方案，避免了无效的资源消耗。

- **数据持久化可靠性增强**:
    - `#2907` **修复 JSONL 存储崩溃后的元数据漂移**：解决了在写入数据文件与元数据文件之间进程崩溃导致的数据不一致问题，提升了数据完整性。

- **用户体验与 Web UI 重构**:
    - `#2587` **支持端到端流式对话和滚动体验**：这是一个大型功能合并，为 Web 聊天添加了完整的流式传输支持，并重写了前端渲染和滚动行为，显著改善了交互的实时性和流畅度。
    - `#2891` **新增“恢复出厂设置”功能**：为配置升级不兼容等问题提供了安全的恢复路径，该功能会备份当前配置、创建默认配置并保留关键安全凭证。
    - `#2663` **改善配置保存与重启的反馈**：用户修改配置后的保存/重启反馈更加明确，修复了前端构建阻断问题。

- **新工具与功能集成**:
    - `#2673` **新增跨平台串口工具支持**：为 Linux、macOS、Windows 内置了 `serial` 硬件工具，并已集成到运行时注册表和仪表盘设置中。
    - `#2915 / #2831 / #2832 / #2833` **模型配置工作流大改**：这是一个分为三部分的重大改进系列。包括为 MiMo 等提供商添加通用模型列表、重构 Web UI 的模型选择与表单、支持从上游提供商拉取模型列表以及基础的模型连通性测试。

### 4. 社区热点

今日社区讨论焦点明确，主要围绕新的功能集成诉求。

- **`[Feature] I need SimpleX or tox` (#3093)**: 由用户 `Damian-o2` 提出，获得了 1 个赞和 2 条评论。用户明确提出了对 `SimpleX` 或 `Wire` 或 `Tox` 网关的支持需求。这反映了社区对去中心化、隐私优先通讯协议的兴趣正在增长。
    - **链接**: [sipeed/picoclaw Issue #3093](https://github.com/sipeed/picoclaw/issues/3093)

- **`[BUG] Continuous consumption of tokens every minutes when evolution is enabled` (#3012)**: 该 Issue 已有 5 条评论，是今日讨论最深入的问题。用户详细报告了在启用“进化”功能后，每分钟持续消耗 Token 的严重问题。这直接关系到项目运行成本，是开发者高度关注的核心 Bug。
    - **链接**: [sipeed/picoclaw Issue #3012](https://github.com/sipeed/picoclaw/issues/3012)

### 5. Bug 与稳定性

今日报告了 6 个 Issues，其中 2 个为新增 Bug，1 个为已关闭的 Bug。

- **[严重] Continuous consumption of tokens every minutes when evolution is enabled (#3012)**: 影响运行成本的严重问题，虽然已有一段时间，但今日仍有新评论，表明仍未解决。**严重程度: 高**。暂未见关联的修复 PR。
    - **链接**: [sipeed/picoclaw Issue #3012](https://github.com/sipeed/picoclaw/issues/3012)
- **[中等] Volcengine Doubao Seed tool calls occasionally leak as `<seed:tool_call>` text (#3153)**: 今日新报 Bug。当使用 `doubao-seed-2.0-pro` 模型时，工具调用会以原始文本形式泄漏给用户，而非执行。**严重程度: 高**，影响特定模型的核心可用性。暂未见关联的修复 PR。
    - **链接**: [sipeed/picoclaw Issue #3153](https://github.com/sipeed/picoclaw/issues/3153)
- **[中等] Panel does not work on Safari on iOS versions below 16.4 (#3090)**: 影响部分 iOS 用户的 Web 面板使用。**严重程度: 中**。暂未见关联的修复 PR。
    - **链接**: [sipeed/picoclaw Issue #3090](https://github.com/sipeed/picoclaw/issues/3090)
- **[已修复] Bug: allow_from fails for Matrix user IDs containing colon (#3044)**: 该问题已被关闭，表明已找到解决方案或已被处理。**严重程度: 低 (已解决)**。
    - **链接**: [sipeed/picoclaw Issue #3044](https://github.com/sipeed/picoclaw/issues/3044)
- **[已修复] `mcp add` mis-parses global flags into positionals (#3041)**: CLI 命令的解析错误问题已被关闭。**严重程度: 低 (已解决)**。
    - **链接**: [sipeed/picoclaw Issue #3041](https://github.com/sipeed/picoclaw/issues/3041)

### 6. 功能请求与路线图信号

- **新通讯协议集成信号 (#3093)**: 用户 `Damian-o2` 对 `SimpleX`、`Tox` 等隐私通讯协议的请求，是一个明确的信号，表明部分用户对主流通讯协议之外的去中心化替代方案有需求。目前尚无相关的 PR 或路线图声明。
- **“恢复出厂设置”功能已实现 (#2891)**: 此前社区对配置迁移和故障恢复可能存在的痛点，现已通过新增功能得到解决。这应被视为路线图上的一项重要补充。

### 7. 用户反馈摘要

- **正面反馈 (隐含)**：大量 PR 被成功合并，尤其体现在用户体验（Web 流式对话、配置反馈）和功能扩展（串口工具、恢复出厂设置）方面，表明维护者积极响应社区需求并快速交付。
- **痛点**:
    - **成本问题**: `#3012` 中用户 `xpader` 详细描述了因 Evolution 功能导致的 Token 持续消耗，这是一个非常现实的成本痛点。
    - **平台兼容性**: `#3090` 中用户 `3m377` 报告的 iOS Safari 兼容性问题，影响了移动端用户的访问。
    - **模型集成缺陷**: `#3153` 中用户 `ms8great` 反馈的 Volcengine Doubao 工具调用泄漏问题，直接破坏了特定模型的正常交互逻辑。
    - **功能缺失**: `#3093` 中用户 `Damian-o2` 直言“我需要 SimpleX 或 tox”，表达了对特定通讯方式的强烈需求。

### 8. 待处理积压

今日未发现长期未响应的紧急议题。但以下 Issue 虽然活跃，但尚未有明确的解决方案或开发进展，值得维护者关注：

- **`[OPEN] [BUG] Continuous consumption of tokens every minutes when evolution is enabled` (#3012)**: 自 6 月 5 日创建以来，已有 5 条评论，且问题严重（影响成本），至今未关闭，也无关联 PR。建议优先排查。
    - **链接**: [sipeed/picoclaw Issue #3012](https://github.com/sipeed/picoclaw/issues/3012)
- **`[OPEN] [BUG] Volcengine Doubao Seed tool calls occasionally leak as <seed:tool_call> text` (#3153)**: 这是今日报告的新 Bug，影响特定用户群体，维护者应尽早确认并响应。
    - **链接**: [sipeed/picoclaw Issue #3153](https://github.com/sipeed/picoclaw/issues/3153)

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，根据您提供的 GitHub 数据，我为您生成了 NanoClaw 项目的 2026-06-22 动态日报。

---

## NanoClaw 项目动态日报 (2026-06-22)

### 1. 今日速览

项目今日活跃度较高，主要受两个**高严重性安全漏洞报告**和一系列**稳定性修复 PR** 驱动。过去24小时内，社区贡献者提交了7个PR，其中3个已合并，显示出修复工作正在快速推进。然而，新发布的2个Issue均为[Security]类别，且尚未有关闭或合并的修复方案，这需要项目维护者给予最高优先级关注。总体来看，项目正处于一个密集的修复和加固阶段，社区贡献活跃但安全风险是当前首要挑战。

### 2. 版本发布
无。

### 3. 项目进展

今日共有 **2 个 PR 被合并**，1 个 PR 被关闭，主要聚焦于提升初始化和清理流程的健壮性。

- **[PR #2825] fix(setup): wait for the host socket before failing the first chat**
    - **状态**: 已合并
    - **贡献者**: `amit-shafnir`
    - **内容**: 修复了 `setup` 流程中的一个竞态条件。此前，`service`步骤在系统服务启动命令返回后立即检查主机socket，但此时主机进程可能尚未完全启动并绑定socket，导致“首次聊天”失败。此PR通过增加等待机制，确保socket就绪后才进行后续操作，提升了首次安装的用户体验。
    - **链接**: [PR #2825](nanocoai/nanoclaw PR #2825)

- **[PR #2168] fix(container): pin host.docker.internal to OneCLI's bridge IP in rootless Docker**
    - **状态**: 已合并
    - **贡献者**: `kpscheffel`
    - **内容**: 修复了在 rootless Docker 模式下，`host.docker.internal` 解析失败的问题。该PR通过将容器内的 `host.docker.internal` 直接映射到 OneCLI 的桥接 IP，而不是依赖 `host-gateway`，解决了网络连接问题。这是一个等待了近2个月的 PR，对使用 rootless Docker 的用户至关重要。
    - **链接**: [PR #2168](nanocoai/nanoclaw PR #2168)

这两个合并表明项目正在处理用户早期安装和特定环境配置下的痛点，整体向着更稳定、更易部署的方向迈进。

### 4. 社区热点

今日社区讨论的核心焦点完全集中在 **安全性**上，具体由以下两个新开的 Security Issue 驱动：

- **[Issue #2828]  [Security] A2A attachment forwarding 的目录穿越漏洞**
    - **热度**: 新开，0评论，但严重性极高
    - **内容**: 报告了A2A（Agent-to-Agent）附件转发功能存在安全风险。一个被攻陷或提示注入的目标Agent可以将其挂载的 `inbox/` 目录替换为符号链接（symlink），导致发送方Agent写入文件时，文件实际被写入到了预期会话根目录之外的位置，构成目录穿越攻击。
    - **链接**: [Issue #2828](nanocoai/nanoclaw Issue #2828)
    - **诉求分析**: 用户或安全研究员 YLChen-007 深入测试了 Agent 间通信的安全性，发现了一个关键的信任模型缺陷。背后的诉求是希望项目在Agent间文件交换的路径验证和权限控制上增加更强的检查机制，防止恶意Agent利用信任关系进行提权。

- **[Issue #2827] [Security] `add_mcp_server` 审批流程中的参数隐藏漏洞**
    - **热度**: 新开，0评论，但严重性极高
    - **内容**: 报告了 `add_mcp_server` 自修改流程中的审批绕过漏洞。当Agent申请添加一个MCP服务器时，给用户的审批卡片仅显示了服务器名称和基本信息，而**运行时参数 (`args`) 和环境变量 (`env`)** 被隐藏。这使得恶意Agent可以提交一个表面无害的MCP服务器请求，但实际上携带了恶意参数或环境变量，从而实现“审批走私”。
    - **链接**: [Issue #2827](nanocoai/nanoclaw Issue #2827)
    - **诉求分析**: 该问题触及了 NanoClaw 核心安全机制——代理自修改审核流程。用户诉求是审批过程必须是透明的，任何对系统环境或进程运行方式有影响的改动都必须完整地展示给用户，不能让Agent通过隐藏信息来绕过用户监督。

**总结**: 社区目前最关注的是 Agent 安全边界的完整性，尤其是防止恶意 Agent 利用系统功能进行权限提升或数据泄露。

### 5. Bug 与稳定性

今日报告的所有 Bug 均为安全相关，且严重性极高。

- **严重**:
    - **[Issue #2828] A2A 附件转发的目录穿越漏洞**: 允许攻击者将文件写入任意路径。**尚无修复 PR**。
    - **[Issue #2827] `add_mcp_server` 审批流程的参数走私漏洞**: 允许绕过用户审核执行恶意操作。**尚无修复 PR**。

- **较低影响/稳定性**:
    - **[PR #2830] fix(setup): reap dead peer service registrations whose binary is gone**: 这是一个**开放的修复 PR**。解决的是删除项目目录后，残留的启动服务（launchd/systemd）指向不存在的二进制文件，导致资源浪费和日志错误的问题。虽然不涉及安全，但保证了系统的干净整洁。
        - **链接**: [PR #2830](nanocoai/nanoclaw PR #2830)
        - 关联的 **[PR #2829] eee** 已关闭，该 PR 内容为空或测试性质。

### 6. 功能请求与路线图信号

暂无用户明确提出新功能请求，当前贡献者的精力主要集中在**修复和加固**上。

- **[PR #2826] fix(update-skills): nudge into skill updates, rebuild container on re-apply**: 这是一个**开放的修复 PR**，旨在改善技能更新机制，使其不再是可选操作，并在重新应用技能时重建容器。这可以视作对现有功能体验的增强，可能被纳入下一个补丁版本。
    - **链接**: [PR #2826](nanocoai/nanoclaw PR #2826)
- **[PR #2795] feat: add /add-clidash — read-only CLI-derived dashboard skill**: 这是一个**已开放数天的 PR**，贡献者 `leetwito` 创建了一个新的实用技能，用于从CLI派生一个只读仪表盘。这代表了社区对提升可观测性和控制台能力的兴趣，有可能被纳入后续小版本。
    - **链接**: [PR #2795](nanocoai/nanoclaw PR #2795)

### 7. 用户反馈摘要

今日无包含评论的Issue或PR，因此没有直接的文本反馈。但从提交的 PR 内容和 Issue 报告上，可以推断出用户画像与痛点：

1.  **高级用户/安全研究员**: 以 `YLChen-007` 为代表的用户正在进行深度的安全审计，他们关注的是代理系统内部复杂的信任关系和权限模型，而非简单的功能使用。
2.  **运维/部署者**: 以 `amit-shafnir` 为代表的贡献者正在解决安装和初始化过程中的各种边缘情况，比如竞态条件和服务残留，这反映了当下部署场景的复杂性和对一键安装、平滑卸载的硬性需求。
3.  **Docker 用户**: 长达2个月的 `PR #2168` 被合并，说明 rootless Docker 用户群体一直在等待这个关键修复，其痛点在于标准配置无法在特殊环境下工作。

### 8. 待处理积压

目前暂无长期未响应的问题。但存在一些 **开放的 PR** 和 **新开的严重 Issue** 需要维护者尽快回应和处理。

- **最高优先级**:
    - **[Issue #2828]**: 安全问题，无修复PR，需立即确认并分配任务。
    - **[Issue #2827]**: 安全问题，无修复PR，需立即确认并分配任务。
- **需要关注**:
    - **[PR #2531]** - **fix(poll-loop)**: 自5月18日起开放，解决轮询循环中消息重复的问题。这是一个核心通信机制的Bug，尽管评论数为0，但开放时间长，需要排查进度。
        - **链接**: [PR #2531](nanocoai/nanoclaw PR #2531)
    - **[PR #2830]**: 清理服务残留的PR，虽然影响不如安全问题，但也是提升系统健康度的良好改进。
        - **链接**: [PR #2830](nanocoai/nanoclaw PR #2830)

---
**分析师总结**：NanoClaw 今日的脉搏由“安全”和“稳定性”主导。社区正从功能开发阶段转向一个关注运行时安全和系统健壮性的新阶段。核心贡献者应尽快对 `#2828` 和 `#2827` 这两个安全漏洞做出回应，制定修复方案并发布补丁版本，以维护项目信誉。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，根据您提供的NullClaw项目数据，我为您生成了2026年6月22日的项目动态日报。

***

### NullClaw 项目日报 | 2026-06-22

**分析师：** AI 项目分析师
**数据来源：** GitHub `NullClaw/nullclaw` 公开仓库
**报告周期：** 2026-06-21 ~ 2026-06-22

---

#### 1. 今日速览

今日项目活跃度较低。过去24小时内，未产生新的Pull Request或版本发布，表明核心开发团队可能处于静默期或专注于其他内部开发任务。社区侧有一个关于“NoResponseContent”错误的Bug报告，该问题在特定模型（Agnes-2.0-Flash）下出现频率超过50%，且已被用户证实为高频复现问题，是当前社区关注的焦点。项目整体进入**维护与观察状态**，稳定性问题成为社区痛点。

#### 2. 版本发布

**无。** 过去24小时内未有新版本发布。上一个版本为 `v2026.5.29`，是本次Bug报告的直接关联版本。

#### 3. 项目进展

**无。** 过去24小时内未有Pull Request被合并或关闭。项目核心代码库在今日无明显向前推进。

#### 4. 社区热点

- **唯一焦点：** `Issue #967` - [bug] error: NoResponseContent
  - **链接：** [Issue #967](https://github.com/nullclaw/nullclaw/issues/967)
  - **分析：** 尽管只有1条评论，但该Issue是今日社区唯一的活动。背后的诉求非常明确：**用户无法稳定地使用核心 `agent` 功能**。报告者详细描述了环境（Win11）、模型版本（Agnes-2.0-Flash）及高频复现条件（>50%），并指出在“picocla...”的同类应用中可正常工作，这暗示问题可能源于NullClaw内部的请求处理或响应解析逻辑，而非模型API本身。这是对项目**核心可用性**的严重质疑。

#### 5. Bug 与稳定性

| 严重程度 | Bug 描述 | 关联 Issue | 是否已有 Fix PR |
| :--- | :--- | :--- | :--- |
| **严重 (Critical)** | 使用 `agent` 命令时出现 `error: NoResponseContent` 错误，触发概率 >50%，导致对话完全失败。 | [#967](https://github.com/nullclaw/nullclaw/issues/967) | 否 |

- **分析：** 此Bug严重影响了NullClaw作为个人AI助手的核心对话功能。报告者在21次对话中遇到12次，稳定性极差，属于“阻碍性”Bug。需优先排查NullClaw与Agnes-2.0-Flash模型的通信协议、超时处理及返回内容解析流程。

#### 6. 功能请求与路线图信号

**无。** 今日用户反馈集中于修复现有Bug，无新功能请求提出。开发团队需优先解决稳定性问题，这将是决定项目下一版本迭代方向的关键信号。

#### 7. 用户反馈摘要

- **痛点 (Pain Points):**
  - **核心功能不稳定：** 用户报告“同一个模型和API Key，在picocla...上能用”，但在NullClaw上超过一半的请求失败，直接质疑了项目的可靠性。
  - **体验不佳：** 平均响应时间27秒，加之大于50%的失败率，用户使用体验极差，可能严重挫伤社区信心。用户尝试使用基础问候语“你好”即触发错误。
- **使用场景：** 报告者为Windows环境下的终端用户，正尝试使用 `agent` 命令进行最基础的对话交互。

#### 8. 待处理积压

**无明确积压。** 当前唯一的Issue `#967` 尚处于开启状态，且无任何回复或标签（如 `bug`、`confirmed`）。维护者应尽快对该Issue进行复现、标注和回应，避免问题长期悬置而影响项目声誉。在无其他积压Issue的情况下，**`#967` 应立即成为最高优先级的工作项。**

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw 项目日报 — 2026-06-22

---

## 1. 今日速览

IronClaw 项目在 **2026-06-22** 保持中等偏活跃态势。过去 24 小时内共处理 **6 条 Issues**（新开 4 条，关闭 2 条）和 **29 条 Pull Requests**（待合并 15 条，已合并/关闭 14 条），核心团队密集推进 **Reborn 架构**的 CI 稳定性、学习系统、并发执行与 OAuth 刷新等关键模块。**待合并 PR 数量（15）略高于合并/关闭数量（14）**，表明代码审查和合并节奏稍有积压，但总体健康度良好；`dependabot` 贡献的依赖更新 PR 占据近半待处理量，建议优先合并低风险批次以减轻积压。

---

## 2. 版本发布

**无新版本发布。**

无正式 Tag / Release 产出。项目处于持续开发迭代期，核心功能以 `main` 分支上的 PR 合并为主。

---

## 3. 项目进展

过去 24 小时合并/关闭的关键 PR 如下，覆盖 CI 基础设施、MCP 状态修复及定时触发能力：

- **PR #5118** `ci(reborn): share one Rust cache across the closure`（已合并）  
  核心 CI 修复：将 crate-tests 矩阵中每个 crate 独立缓存改为共享缓存，解决 **60+ 缓存条目竞争 LRU 淘汰导致频繁重新下载依赖** 的根源问题，预计显著减少 CI 红率和运行时长。  
  [链接](https://github.com/nearai/ironclaw/pull/5118)

- **PR #5113** `ci: extract cross-cutting jobs into platform-and-compat.yml`（已合并）  
  CI 架构重构：将跨平台/兼容性检查从 `test.yml` 提取为独立 workflow，提升维护性和触发灵活性。  
  [链接](https://github.com/nearai/ironclaw/pull/5113)

- **PR #5115** `ci(reborn): retry crates.io network failures`（已合并）  
  为 **64-crate 并行解析** 的 CI 闭环增加 `CARGO_NET_RETRY`，缓解因 crates.io SSL/HTTP2 抖动引发的批量失败。  
  [链接](https://github.com/nearai/ironclaw/pull/5115)

- **PR #5065** `feat(triggers): one-shot scheduled triggers`（已合并）  
  新增 **一次性定时触发器**（`TriggerSchedule::Once { at, timezone }`），配合之前 PR #5065 的 Completed 筛选 Tab，为自动化的“单次执行”场景提供模块支持。  
  [链接](https://github.com/nearai/ironclaw/pull/5065)

- **PR #4990** `fix(reborn): NEAR AI MCP ready state projection`（已合并）  
  解决 **NEAR AI MCP 被 WebUI 错误显示“SETUP NEEDED”** 的问题，将运行时凭据与浏览器管理扩展配置解耦。对应 Issue #4925 已关闭。  
  [链接](https://github.com/nearai/ironclaw/pull/4990)

**项目整体前进：** CI 可靠性提升、一次性触发器功能上线、MCP 就绪状态修复。学习系统（WS-1/WS-2/WS-3）与并发执行（PR #5085）仍处于开放待合并状态，预计未来 1~2 天完成。

---

## 4. 社区热点

今日讨论最活跃的议题（按评论数/活动热度排序）：

| 议题 | 类型 | 作者 | 评论数 | 状态 | 热点分析 |
|------|------|------|--------|------|----------|
| #4925 NEAR AI MCP "SETUP NEEDED" 误报 | Issue | sunglow666 | 1 | **已关闭** | 用户反馈 MCP 自动安装后 UI 错误提示“需要额外配置”，核心团队已通过 PR #4990 修复并关闭。虽评论数不多，但此为 **直接影响用户首次使用体验** 的问题，代表了 Reborn WebUI 的 onboarding 容忍度问题。 |
| #5120 统一入口拒绝语义（Declined/Deny/Canceled） | Issue | hanakannzashi | 0（新开） | 开放 | 提出 **Auth、审批、活动投影三处使用不同拒绝术语** 的问题，意图统一为 `Declined`。反映 Reborn 在多个子系统间的命名规范化需求，属于设计一致性议题。 |
| #5119 本地 Dogfooding 发现跟踪（06/22—06/28） | Issue | think-in-universe | 0（新开） | 开放 | 开启为期一周的本地自测活动，目的为收集 “启动、配置、模型-提供商设置、首次运行可用性” 等问题。**社区参与机会**，鼓励用户复现和报告。 |

**背后诉求：** 用户更期待 **即装即用** 的体验和对 UI/UX 一致性的敏感度提升；核心团队通过主动 Dogfooding 活动来兜底边缘场景，展现对质量控制的投入。

---

## 5. Bug 与稳定性

| 严重性 | Issue/PR | 标题 | 状态 | 备注 |
|--------|----------|------|------|------|
| **高** | #4108 | Nightly E2E failed | **持续开放（自 05-27）** | 夜间 E2E 测试仍在失败，失败任务为 `Full E2E / E2E (extensions)`，至今已超过 **25 天** 未解决。此为 **项目健康度红线**，建议排查修复或标记为已知问题。 |
| 中 | #5071 | Google OAuth 令牌未主动刷新 → 用户需重新认证 | 已关闭（已修复） | PR #5081 等后续提交解决了 OAuth 刷新逻辑，但 PR #5081 本身仍为开放状态（单租户 Postgres 配置），实际修复是否能投入生产尚需确认。 |
| 中 | #5119 (Dogfooding) | 本地启动问题跟踪 | 新开 | 未来一周内可能上报多个本地启动、配置相关的 Bug，建议优先关注。 |
| 低 | #4925 | MCP 就绪状态投影错误 | 已关闭（PR #4990 合入） | 已修复。 |

**即时关注：** 请项目维护者重视 **#4108（Nightly E2E 持续失败）**，若未修复会对持续交付信心产生负面影响。

---

## 6. 功能请求与路线图信号

| Issue/PR | 功能描述 | 建议纳入版本 |
|----------|----------|--------------|
| #5117 | **自动化页面增加 “Completed” 汇总卡片**（展示已完成的一次性自动化数量） | ✅ 可能纳入下一版（已配合 #5065 筛选 Tab） |
| #5085 | **并发 Turn 执行调度器**（`TurnRunScheduler` + 用户级/类型级并发上限） | ✅ 下一个里程碑（XL 级别 PR，核心团队开发） |
| #4975 (WS-3) | **学习系统：轻量反射服务**（turn 完成后自动从失败/修正中学习） | ✅ 学习系统栈第三部分（待合并） |
| #5109 | **Workbench 只读 + 门控写入连接器路由（Composio）** | ⚠️ 草案阶段，可能下一个版本 |
| #5120 | **统一门控拒绝语义**（Declined/Deny/Canceled → Declined） | ✅ 设计可行，代码变更量可能小（取决于涉及范围） |
| #5081 | **托管单租户 Postgres 配置文件**（本地开发 + Postgres 持久化） | ✅ 平台预览路径的关键能力（XL 级别，DB 迁移） |

**路线图信号清晰：** **学习系统（WS-1/2/3）**、**并发 Turn 执行**、**Postgres 生产化配置** 是当前三大主线任务，预计 1~2 周内逐步合并。

---

## 7. 用户反馈摘要

基于 Issue #4925 评论与 Dogfooding 活动性质：

- **“Setup Needed 误报”**：用户指出 NEAR AI MCP 明明可正常使用，UI 却显示需要额外设置，点击“Configure”后体验困惑。**痛点核心**：WebUI 对内置扩展的 ready state 判断逻辑与真实运行时状态脱钩，导致新手产生“我还差什么东西没装”的错觉。
- **Dogfooding 活动意向**：`think-in-universe` 开启本地自测跟踪，表示“用本地 IronClaw Reborn 作为日常代理人，同时发现启动/配置问题”。**正面信号**：核心开发者主动吃自己的狗粮，提高早期问题发现率。
- **无强烈负面情绪**：整体社区反馈以功能请求和设计讨论为主，未出现严重投诉。

---

## 8. 待处理积压

以下议题长期未获得足够关注，建议维护者优先响应：

| 议题 | 类型 | 状态 | 创建时间 | 建议动作 |
|------|------|------|----------|----------|
| **#4108 Nightly E2E failed** | Bug | 开放 | 2026-05-27 | **高优先级**：检查 E2E (extensions) 失败原因，修复或添加已知失败标记 |
| **#2927 fix(channels): load_startup_active_channels for first-run fallback** | PR | 开放 | 2026-04-24 | 自 4 月以来未合并，内容涉及首次运行时频道激活回退，影响新用户启动体验 |
| **#4002 build(deps): bump actions group (16 updates)** | PR | 开放 | 2026-05-24 | 大版本批量更新（actions/checkout v4→v7 等），存在破坏性变更风险，需要 review |
| **#4032 build(deps): bump wasm group** | PR | 开放 | 2026-05-25 | wasm-tools 生态系统大版本更新（0.245→0.252），建议确认 API 兼容性 |
| **#4975 (WS-3) lightweight reflection service** | PR | 开放 | 2026-06-16 | 学习系统栈的第三 PR，依赖 #4938 (WS-2) 合并，建议在 WS-1/2 合并后加速 Review |

---

## 总结

IronClaw 项目在 **2026-06-22** 保持稳健但活跃的开发节奏。**CI 稳定性提升**（缓存共享、重试机制）是一大亮点，**一次性触发器、MCP 就绪状态修复** 实时落地。**学习系统与并发执行** 两大新功能处于开放待合并状态，是确定性向前推进的指针。**Nightly E2E 持续失败** 是唯一需要立即关注的风险点。总体项目健康度 **良好**，核心团队保持在快速迭代轨道上。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，根据您提供的LobsterAI项目数据，我为您生成了以下项目动态日报。

---

# LobsterAI 项目动态日报 | 2026-06-22

**项目名称:** LobsterAI (github.com/netease-youdao/LobsterAI)
**分析日期:** 2026-06-22
**数据区间:** 2026-06-21 至 2026-06-22

---

### 1. 今日速览

项目今日状态平稳，主要活动集中在对历史遗留问题的清理与归档上。过去24小时内，社区提交了1个新的安全相关Issue，但无新的Pull Request或版本发布。值得注意的是，有14个旧Issue被统一关闭（标记为`stale`），表明维护团队正在进行一次大规模的状态清理，以降低项目积压。整体来看，项目在功能迭代上进入短暂停滞期，但社区活跃度依然存在，特别是新提出的安全问题值得高度关注。

- **活跃度评估**: 中等。核心开发活动（PR、Release）暂停，但社区反馈（新Issue）和维护活动（关闭Stale Issue）仍在进行。

### 2. 版本发布

无新版本发布。

### 3. 项目进展

今日无新的Pull Request被合并或关闭。项目代码库和功能栈在过去24小时内无任何变更。主要进展体现在对历史Issues的清理上。

### 4. 社区热点

今日唯一的新Issue [#2181 “LobsterAI restores private-network browser access by default and weakens the bundled OpenClaw SSRF guard”](https://github.com/netease-youdao/LobsterAI/issues/2181) 成为社区焦点。

- **分析**: 该Issue由用户 YLChen-007 提出，其标题直言不讳地指出了项目的**安全架构缺陷**。它揭示了LobsterAI的浏览器设置层默认启用了`ProxyCompatible`模式，这种配置可能会绕过或削弱内嵌的OpenClaw组件对服务端请求伪造（SSRF）攻击的防御。
- **诉求分析**: 该反馈不仅仅是一个Bug报告，更是一个严重的**安全预警**。用户指出此举默认恢复了“内网浏览器访问”能力，这在企业环境中可能导致敏感内部资源泄露。这背后是用户对项目默认安全基线的高要求，以及对“开箱即用”的安全配置的强烈关注。
- **建议**: 项目维护者需立即响应此Issue，评估其影响范围，并在后续版本中调整默认策略，或提供明确的安全配置指南。

### 5. Bug 与稳定性

今日无新的Bug报告。然而，昨日（6月21日）被标记为`stale`并关闭的14个Issues中，包含大量与**UI/UX逻辑错误**和**配置管理缺陷**相关的严重Bug。虽已被关闭，但其暴露的问题具有代表性，按严重程度排列如下：

1.  **[严重] 安全与功能失效**
    -   [#1500](https://github.com/netease-youdao/LobsterAI/issues/1500): 禁用技能后仍在对话中被调用（状态同步Bug）。
    -   [#1502](https://github.com/netease-youdao/LobsterAI/issues/1502): 修改Agent技能列表后需切换Agent才能生效（状态同步Bug）。
    -   [#1506](https://github.com/netease-youdao/LobsterAI/issues/1506): 定时任务IM通知频道未选会话即可提交，导致通知静默失败（缺少表单校验）。

2.  **[中等] 功能不完整/错误**
    -   [#1504](https://github.com/netease-youdao/LobsterAI/issues/1504): IM机器人Popo的AES Key缺少必填校验（缺少表单校验）。
    -   [#1512](https://github.com/netease-youdao/LobsterAI/issues/1512): QQ Bot群组白名单缺少UI添加输入框（UI功能缺失）。
    -   [#1516](https://github.com/netease-youdao/LobsterAI/issues/1516): 关闭Settings面板后GitHub Copilot OAuth轮询未取消，Token可能丢失（资源管理/生命周期Bug）。

3.  **[轻微] 内容与展示问题**
    -   [#1513](https://github.com/netease-youdao/LobsterAI/issues/1513): 【声明条款】内容规范不统一（内容格式错误）。
    -   [#1509](https://github.com/netease-youdao/LobsterAI/issues/1509): Skills文件生成阻塞且无中间状态展示，用户感知差（用户体验问题）。

**重要提示**: 尽管上述Issues已被标记为`stale`关闭，但对应的代码问题并未修复，积压隐患仍然存在。

### 6. 功能请求与路线图信号

今日无新的功能请求。但在昨日被关闭的`stale` Issues中，用户 `MaoQianTu` 连续提出了多个非常有价值的功能改进建议，反映了用户对 LobsterAI 提高“生产力和信息管理能力”的强烈诉求。这些需求很可能被纳入项目未来的路线图。

-   [#1525](https://github.com/netease-youdao/LobsterAI/issues/1525): **会话颜色标注** - 通过视觉区分不同用途的会话。
-   [#1528](https://github.com/netease-youdao/LobsterAI/issues/1528): **批量导出会话** - 支持一次性导出多个会话记录进行备份或迁移。
-   [#1532](https://github.com/netease-youdao/LobsterAI/issues/1532): **本地使用统计** - 在设置页面增加本地会话/消息数量等使用统计面板。
-   [#1537](https://github.com/netease-youdao/LobsterAI/issues/1537): **消息书签/收藏** - 标记并快速定位长对话中的重要AI回复。
-   [#1541](https://github.com/netease-youdao/LobsterAI/issues/1541): **会话标签分类与筛选** - 为会话创建多维度标签，并支持按标签筛选。

**信号判断**: 用户 `MaoQianTu` 提出的这一组Issue，描绘了一个功能更强大的“个人知识管理”工具的雏形。这表明部分高端用户不仅将LobsterAI视为一个聊天工具，更希望它成为一个**可持久化、可检索、可管理**的个人信息中枢。这些需求与当前AI助手向知识管理工具演进的趋势高度吻合。

### 7. 用户反馈摘要

-   **用户痛点**: 从关闭的Issues看，用户反馈主要集中在**状态一致性**（禁用技能无效、配置修改不同步）和**操作流程不严谨**（无表单必填校验、无中间状态提示）方面。这表明用户在将LobsterAI用于自动化工作流（如定时任务、消息推送）时，遇到了较高的配置门槛和不确定性。
-   **使用场景**: 频现的场景包括**技能编排**（创建和禁用技能）、**自动化任务**（定时通知、IM机器人配置）以及**会话管理**（大量会话的组织与检索）。
-   **用户情绪**: 用户 `MaoQianTu` 提交的一系列Issue格式规范、描述清晰，且具有前瞻性，展现出**资深用户的参与热情和成熟的产品思维**。而新提交的Issue #2181 则表现出**安全意识较强的用户对项目安全基线的担忧**。

### 8. 待处理积压

-   **【高优先级】严重安全风险**: 新提交的Issue [#2181](https://github.com/netease-youdao/LobsterAI/issues/2181) 关于默认重置内网访问和削弱SSRF防御的问题，是当前最重要的积压项。此问题暂无回复，安全影子。
-   **【高优先级】历史遗留Bug**: 尽管已被标记关闭，但昨日关闭的大量由`MaoQianTu`和`jimmy-xz`提交的Bug（如#1500, #1502, #1506, #1509），**实际上并未修复**。维护者在清理归档后，应重新评估这些Bug的优先级，确认是标记错误还是计划在后续版本集中修复。特别是状态不同步问题，严重影响核心体验。
-   **【中优先级】CI/CD基础设施**: 昨日关闭的Issue [#1518](https://github.com/netease-youdao/LobsterAI/issues/1518) 关于Labeler权限修复，虽然已修复，但项目CI的稳定性仍需持续关注。

**分析师结语**: 今日LobsterAI项目表面平静，但暗流涌动。维护团队“关旧门”的同时，一扇新的“安全后门”被社区发现。建议项目组立即评估#2181的安全影响，并认真复盘昨日关闭的一批未修复Bug，避免“清理档案”等同于“掩盖问题”。用户的深度反馈揭示了项目从“AI聊天应用”向“AI知识管理平台”演进的强烈信号，这是值得长期投入的战略方向。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，以下是基于您提供的 CoPaw 项目数据生成的 2026-06-22 项目动态日报。

---

# CoPaw 项目日报 | 2026-06-22

## 1. 今日速览

项目今日活跃度极高，社区生态表现出强劲动力。过去24小时内产生了 **15 条 Issue** 和 **29 条 PR**，远超平均水平，显示出社区对功能完善和Bug修复的热情。**功能请求**和**Bug报告**平分秋色，其中移动端适配和核心稳定性成为两大焦点。值得注意的是，一位名为 `yaozy2020` 的贡献者连续提交了多个移动端适配的PR，表明社区正自发地推动项目向更广的使用场景（如手机浏览器）延伸。尽管没有新版本发布，但大量待合并的PR预示着一个功能密集的版本即将到来。

## 3. 项目进展

今日有 **5 个 PR 被合并/关闭**，为项目带来了实质性进展。主要集中在以下几个方面：

-   **核心插件系统修复**：
    -   **PR #4900 (已合并)**：[Decouple plugin loader initialization from agent startup](https://github.com/agentscope-ai/CoPaw/pull/4900) 解决了在Tauri桌面版等冻结环境中插件加载器无法启动的关键问题，这是Issue #4889的修复方案。
    -   **PR #5270 (已合并)**：[test(integration): Sprint 3.1-3.4](https://github.com/agentscope-ai/CoPaw/pull/5270) 完成了包含64个测试用例的集成测试套件，覆盖了插件系统、安全等核心模块，为项目稳定性提供了保障。
-   **移动端/UI适配**：
    -   **PR #5365 (已合并)**：[feat(console): mobile responsive layout for Agent Config page](https://github.com/agentscope-ai/CoPaw/pull/5365) 实现了Agent配置页面的移动端响应式布局，这是社区对移动端适配系列工作的开端。
-   **其他**：
    -   **PR #3831 (已合并)**：[Add vector model connection test feature](https://github.com/agentscope-ai/CoPaw/pull/3831) 新增了向量模型连接测试功能，完善了模型配置的管理体验。

**总结**：项目通过修复关键的插件系统和集成测试，筑牢了稳定性基础。同时，来自社区的移动端适配PR被合并，标志着项目开始关注并开始解决移动端体验问题。

## 4. 社区热点

今日最受关注的议题围绕 **用户体验 (UX)** 和 **稳定性** 展开，以下是讨论最活跃的议题：

-   **[Issue #5354] [Bug]: 消息发送队列容易串台；切换对话时切不回去** - 评论数：4
    -   **链接**: [https://github.com/agentscope-ai/CoPaw/issues/5354](https://github.com/agentscope-ai/CoPaw/issues/5354)
    -   **分析**: 用户报告了新引入的消息队列功能导致消息发送到错误的Agent，以及切换对话后UI卡死的严重问题。这直接影响了核心交互体验，引起了开发者的高度关注。**一个修复此问题的PR #5371 已在同日提交**，解决效率极高。

-   **[Issue #5262] [Bug]: 每次升级之后，被禁用的内置技能又会重新变回启用2.0** - 评论数：8
    -   **链接**: [https://github.com/agentscope-ai/CoPaw/issues/5262](https://github.com/agentscope-ai/CoPaw/issues/5262)
    -   **分析**: 这是一个**回归问题**（在 #4807 后再次出现），用户对升级后重置个人偏好的行为感到沮丧。评论数最多表明有 **复现/同感** 的社区成员较多。这体现了用户对软件稳定性和配置持久化的高要求。

-   **[Issue #5329] [Feature]: 在左边的侧边栏进入简介模式后，添加一个切换agent的按钮** - 评论数：5
    -   **链接**: [https://github.com/agentscope-ai/CoPaw/issues/5329](https://github.com/agentscope-ai/CoPaw/issues/5329)
    -   **分析**: 一个典型的**功能请求与Bug报告结合**的案例。用户创新地在手机浏览器上使用CoPaw，但发现UI不兼容，导致无法切换Agent。这强烈表达了社区对**移动端适配**的迫切需求。

## 5. Bug 与稳定性

今日报告的Bug数量较多，其中一些直接影响核心功能，需优先处理。

-   **严重级 - 功能性崩溃**：
    -   **[#5370] `send_file_to_user` ended up with http 404**: 文件预览功能彻底损坏，导致用户无法查看Agent发送的文件。
    -   **[#5354] 消息发送队列串台 & 切换对话卡死**: 导致多Agent交互和会话管理混乱。**有修复PR #5371**。
    -   **[#5344] `/api/console/chat` 静默丢消息**: API接口不可靠，当Agent忙时返回成功但实际无响应，严重影响自动化工作流。

-   **严重级 - 核心功能异常**：
    -   **[#5373] Shell command execution fails to parse shell special characters**: Agent执行 `shell` 命令时功能严重受限，无法使用管道、重定向等基础shell特性。
    -   **[#5345] Custom OpenAI-compatible providers don't support function calling**: 阻碍了用户接入其他兼容OpenAI的模型服务，限制了模型选择范围。
    -   **[#5353] v1.1.12 飞书群聊中必须 @ 智能体才会响应**: 即使配置不当，也强制要求@，违反了配置预期。
    -   **[#5262] 升级后内置技能再次启用**: 功能回归，用户体验差。

-   **中级 - 异常/回归**：
    -   **[#5320] 升级到 v1.1.12 后图片不显示**: 一个回归Bug，图片预览功能在最新版中被破坏了。**有修复PR #5324**。
    -   **[#5358] TypeError: Cannot read properties of null (reading 'object')**: 前端偶发错误，可能导致界面异常。
    -   **[#4889] Tauri桌面版插件加载器未启动**: 已通过PR #4900修复，但说明冻结环境部署仍存在问题。

## 6. 功能请求与路线图信号

-   **高可能性纳入下版本**:
    -   **[#5322] Feature Request: Real-time UI update and voice notification**：实时更新和语音通知，是提升API交互体验的关键，社区呼声高。
    -   **[#5351] Implement automatic model failover in model_factory.py**: 自动模型故障转移，是提升稳定性的重要特性。`RoutingChatModel` 代码存在但未启用，此功能请求是自然演进方向。
    -   **大量移动端适配请求 (#5329, #5369, #5362, #5364等)**: 结合已合并的PR #5365，可以断定**移动端适配**是下一版本的核心路线图，短期内会有一批相关PR被合并。

-   **中期/远期信号**:
    -   **[#5360] Stabilize the core app before adding new features**: 此Issue代表了部分用户的**保守派声音**，呼吁优先解决现有稳定性问题。维护者需要平衡新功能开发和Bug修复的节奏。
    -   **[#4622] plugin(datapaw): add data-analysis plugin**: 一个功能强大的数据分析插件，若被合并，将大幅扩展CoPaw的应用场景。目前仍在“Under Review”状态。
    -   **[#5321] feat(context): scroll context manager**: “滚动上下文管理器”是一个创新性功能，允许模型回顾历史对话，可能改变长对话的处理方式。处于`Under Review`状态，值得关注。

## 7. 用户反馈摘要

-   **痛点**:
    -   **偏好设置丢失**：“每次升级，禁用技能都会重置，很烦人。” (Issue #5262)
    -   **移动端体验差**：“在手机上用浏览器控制CoPaw，UI完全没法用，按钮都点不到。” (Issue #5329)
    -   **新功能反噬**：“消息队列是好功能，但串台了，给错Agent造成混乱。” (Issue #5354)
    -   **API稳定性**：“通过API发消息，服务器说成功了，但Agent根本没收到，也不知道失败了。” (Issue #5344)

-   **满意/期待**:
    -   **对消息队列功能的肯定**：尽管有Bug，但用户 `renzhong424` 在报告Bug时仍认可这是一个“非常不错的进展，极大地提高了效率”。(Issue #5354)
    -   **社区贡献的良性循环**：多名用户（如 `yaozy2020`）从报告问题者转变为解决方案的贡献者，提交了对应的修复/适配PR，表明社区生态健康，有强烈的“自己动手”精神。

## 8. 待处理积压

以下系长期未得到关注的Issue或PR，提醒维护者关注：

-   **[PR #5097] fix(security): fix Shield icon centering**：一个关于安全设置页面图标对齐的UI修复PR，自6月11日提交以来已超过10天未更新，属于优先级不高的样式问题，但长期搁置会堆积技术债。
    -   **链接**: [https://github.com/agentscope-ai/CoPaw/pull/5097](https://github.com/agentscope-ai/CoPaw/pull/5097)

-   **[PR #5040] fix(crons): tolerate invalid jobs in jobs.json**：这是一个对cron任务配置容错性的改进方案，与已合并的PR #5347是竞争关系。PR #5347采取了更激进的迁移修复方案，而此PR采用更温和的运行时容忍方案。这两个方案的取舍需要维护团队做出决定。
    -   **链接**: [https://github.com/agentscope-ai/CoPaw/pull/5040](https://github.com/agentscope-ai/CoPaw/pull/5040)

-   **[Issue #5360] Stabilize the core app before adding new features**：这个Issue本身不是一个Bug，而是一个方法论讨论。它代表了社区对项目方向的一种声音，维护者应予以回应，明确项目的迭代策略，以避免社区分裂。
    -   **链接**: [https://github.com/agentscope-ai/CoPaw/issues/5360](https://github.com/agentscope-ai/CoPaw/issues/5360)

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

好的，这是为您生成的 ZeptoClaw 项目 2026-06-22 动态日报。

---

### ZeptoClaw 项目动态日报 (2026-06-22)

**分析师:** AI 智能体与开源项目分析师

---

#### 1. 今日速览

今日项目活跃度较低，主要聚焦于 CI 流程的最终收尾工作。过去24小时内，项目关闭了一个关键的 CI 功能请求 Issue 及与之对应的 PR，标志着“二进制大小预算门禁”功能的完整落地。目前项目无新版本发布，也没有新的 Bug 或功能请求报告，整体状态趋于稳定。

#### 2. 版本发布

无

#### 3. 项目进展

今日合并/关闭了一个重要的 PR，完成了对二进制文件大小进行严格控制的核心 CI 功能。

- **PR #611 [CLOSED] chore(ci): promote binary-size to PR gate at 7.5MB**
  - **摘要:** 此 PR 将已有的 `binary-size` CI 检查升级为真正的 PR 合并门禁。主要改动包括：1) 移除了仅在 `push-to-main` 分支运行的限制，使其在每个 PR 上都会执行；2) 将门禁阈值设定为 7.5MB（`stripped` 后的 ZeptoClaw 二进制文件）。
  - **关联 Issue:** #537
  - **项目意义:** 项目维护者此前在 Issue #537 中定义“6MB 二进制文件”为项目的战略护城河，担心每次 PR 都可能导致体积膨胀。此 PR 的合并正式构建了一道自动化防线，从现在起，任何导致 ZeptoClaw 二进制大小超过 7.5MB 的 PR 都将被 CI 拒绝。这确保了项目在追求功能的同时，能够严格控制资源占用，维持其在资源受限设备（如机器人）上的部署优势。
  - **链接:** https://github.com/qhkm/zeptoclaw/pull/611

#### 4. 社区热点

今日唯一的 Issue 及对应 PR 构成了社区讨论的焦点，尽管评论数为0。

- **Issue #537 [CLOSED] [chore, P1-critical] chore(ci): binary size budget gate**
  - **热点分析:** 此 Issue 被标记为 **P1-critical**，尽管它不是 Bug，但其优先级反映了核心维护者对项目长期健康度的关键考量。诉求非常明确：通过自动化手段防止项目二进制文件无节制膨胀。这代表了维护者对“保持项目轻量”这一核心理念的坚持，社区虽然没有直接讨论，但通过 PR 的快速合并可以推断，这一方向得到了高度认同。
  - **链接:** https://github.com/qhkm/zeptoclaw/issues/537

#### 5. Bug 与稳定性

无新增 Bug 或稳定性问题报告。

#### 6. 功能请求与路线图信号

- **功能请求:** 今日无新增功能请求。历史 Issue #537 的“二进制大小预算门禁”功能已随着 PR #611 的合并而完成，将纳入下一版本中。

#### 7. 用户反馈摘要

今日无直接的用户反馈或评论。

#### 8. 待处理积压

当前没有超过30天未响应的关键 Issue 或 PR 积压。项目维护者对核心议题（如 #537）的响应和处理非常及时，项目健康状况良好。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，根据您提供的ZeroClaw项目GitHub数据，我为您生成了2026年6月22日的项目动态日报。

---

## ZeroClaw 项目动态日报 | 2026-06-22

### 1. 今日速览

ZeroClaw 项目在6月22日保持着极高的活跃度，日均更新量（50+）处于峰值水平。项目当前正处于多版本（v0.8.0, v0.8.1, v0.8.2, v0.8.3）并行推进的关键阶段，社区贡献密集。虽然今日无新版本发布，但开发进度主要由对 v0.8.x 系列稳定性和功能完善的需求驱动。值得注意的是，待合并的 PR 积压高达 45 条，显示出社区贡献热情高涨，但维护团队的审查和合并压力巨大。大量关于安全性（SSRF、环境变量泄露、配对码）、工具作用域（MCP、Pipeline）、以及渠道（Telegram、WhatsApp）问题的修复和功能请求，构成了今日社区讨论的核心。

### 2. 版本发布

*无*

### 3. 项目进展

本周项目在核心稳定性、安全性及渠道兼容性上取得了实质进展，多项重要修复已被合并或提交。

*   **渠道与交互修复**:
    *   **重要** `#7720` 的修复 PR `#8124`、`#8123` 已被关闭，其改动量巨大（触及43个文件），核心是实现了WhatsApp渠道的“允许群组”功能，提升了渠道管理的精细化程度。
    *   **安全性修复** `#7753` 的修复 PR `#7847` [fix(channels)](https://github.com/zeroclaw-labs/zeroclaw/pull/7847) 已提交，旨在解决并发会话持久化时的竞态条件（Race Condition），防止对话历史错乱，提升了多用户场景下的稳定性。
    *   **质量提升** `#7720` 修复 PR `#8124`, `#8123` 的关闭，标志着团队在渠道（Slack, WhatsApp）配置和集成上的持续投入。

*   **工具与运行时稳定性**:
    *   **关键修复** 针对 MCP 工具泄露的问题，PR `#7747`、`#8120` 正在推动将 MCP 工具作用域限定到具体 Agent，并实施禁止列表（denylist），解决了多代理环境下工具可见性控制的漏洞。这直接回应了社区对安全性的核心关切。
    *   **功能增强** 多个修复已提交：
        *   优化了浏览器工具在 WebDriver 下的快照功能 (`#7908`)。
        *   修复了管道（pipeline）子工具执行忽略Agent权限配置的问题 (PR `#7960`)。
        *   在非完全自主模式下，允许自动批准的工具执行 (PR `#7959`)，解决了用户工作流被阻塞的问题。
    *   **追踪器更新** v0.8.3 和 v0.8.2 的日程追踪器 (`#8070`, `#8071`, `#7320`, `#7314`, `#7852`) 保持了频繁更新，为项目路线的透明化管理提供了支持。

### 4. 社区热点

*   **`#6808`**: **RFC: 工作流、看板自动化与标签清理** (11条评论)
    *   **链接**: [Issue #6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808)
    *   **分析**: 这是今日最受关注的RFC。社区成员`Audacity88`提出了一套旨在优化项目治理和工作流程的改进方案，涉及引入“工作流”（Work Lanes）、自动化看板管理和标签清理。这反映出核心贡献者对协作效率和项目管理秩序有较高诉求，希望通过系统化手段减轻维护者的手动负担。

*   **`#2503`**: **询问 NapCat 渠道支持** (9条评论)
    *   **链接**: [Issue #2503](https://github.com/zeroclaw-labs/zeroclaw/issues/2503)
    *   **分析**: 这是一个长期未解且讨论活跃的功能需求。用户`irunmyway`急切希望 ZeroClaw 能支持 NapCat/OneBot 协议，以连接QQ。已有9条评论和大量用户共鸣，表明用户对连接国内主流即时通讯工具（如QQ）的需求非常强烈，相关功能的缺失已成为阻碍部分用户使用的关键痛点。

*   **`#2467`**: **Webhook 转换器功能请求** (6条评论)
    *   **链接**: [Issue #2467](https://github.com/zeroclaw-labs/zeroclaw/issues/2467)
    *   **分析**: 用户`MexHigh`点出了当前Webhook系统的局限性——无法处理任意payload。他提出了增加自定义Webhook路径和转换功能，以支持通用的Webhook发送者（如GitHub Webhook）。这代表了高级用户希望将ZeroClaw集成到自身工作流（特别是DevOps场景）中的强烈愿望，是提升项目可用性的关键需求。

### 5. Bug 与稳定性

按严重程度排列，重点关注 S1（工作流阻塞）级别的Bug。

*   **S0 - 数据丢失/安全风险**:
    *   **`#8094`**: [Antropic模型添加后无法在聊天中使用](https://github.com/zeroclaw-labs/zeroclaw/issues/8094)。用户报告在Quickstart中添加Anthropic模型后，无法立即在聊天窗口中使用，需要重置。可能为运行时/配置加载的Bug，暂无修复PR。

*   **S1 - 工作流阻塞**:
    *   **`#7756`**: [原生/MCP工具在OpenAI Responses和Anthropic轮次中不可用](https://github.com/zeroclaw-labs/zeroclaw/issues/7756)。核心工具依赖性问题，严重影响使用MCP的Agent工作流。暂无修复PR，但`#7747`等PR正试图解决MCP作用域问题，值得关注。
    *   **`#6361`**: [MiniMax等兼容供应商的上下文压缩丢失Tool Call结果，导致工具循环](https://github.com/zeroclaw-labs/zeroclaw/issues/6361)。严重影响与特定供应商（如MiniMax）的配合使用。暂未无直接修复PR，但状态为`in-progress`，表明开发团队已知晓。
    *   **`#4879`**: [Gemini CLI OAuth 认证失败](https://github.com/zeroclaw-labs/zeroclaw/issues/4879)。影响Gemini用户的使用入门。已有3条评论，状态为`status:accepted`，等待进一步处理。

*   **S2 - 行为降级**:
    *   **`#6360`**: [Telegram渠道提示缓存失效](https://github.com/zeroclaw-labs/zeroclaw/issues/6360)。在Telegram上无法复用LLM的缓存，导致响应变慢、成本增加。无直接修复PR。
    *   **`#8089`**: [Docker构建因缺少依赖文件而失败](https://github.com/zeroclaw-labs/zeroclaw/issues/8089)。Docker/Debian镜像构建失败。已有一个修复PR `#8093` 提交，旨在处理此问题。

### 6. 功能请求与路线图信号

*   **高优先级安全功能**:
    *   **`#5919`**: [WASM插件环境变量读取白名单](https://github.com/zeroclaw-labs/zeroclaw/issues/5919) 和 **`#5918`**: [WASM HTTP请求SSRF保护](https://github.com/zeroclaw-labs/zeroclaw/issues/5918) 是v0.8.2 WASM插件安全性的核心功能，体现了对插件安全隔离的重视。暂无具体修复PR，但它们是v0.8.2`wasm plugin program`追踪器 `#7314` 的一部分。
    *   **`#6613`**: [增强配对码强度](https://github.com/zeroclaw-labs/zeroclaw/issues/6613)。用户对6位数字配对码的薄弱性表示担忧，要求支持字母数字组合和更长设置。

*   **功能增强被纳入路线图的迹象**:
    *   **`#5287`**: [小模型的本地优先模式](https://github.com/zeroclaw-labs/zeroclaw/issues/5287)。状态为`status:in-progress`，表明开发团队正在积极推进这一功能，以满足用户对本地模型和高隐私诉求。
    *   **`#6289`**: [丢失技能/插件的智能安装建议](https://github.com/zeroclaw-labs/zeroclaw/issues/6289) 和 **`#4760`**: [使用工具调用的内存归并](https://github.com/zeroclaw-labs/zeroclaw/issues/4760) 等与核心运行时和智能体体验相关的功能均已标记为`status:accepted`，预计会在未来的v0.8.x版本中实现。

### 7. 用户反馈摘要

*   **对集成度的渴望**: 用户高度关注 ZeroClaw与外部服务（如NapCat/OneBot、更灵活的Webhook）的整合。`#2503`和`#2467`表明，用户希望将ZeroClaw无缝融入他们现有的、包括国内平台在内的数字生活中。
*   **对安全性的焦虑**: 多用户对安全权限模型提出了具体要求，如WASM插件的`zc_env_read`和`zc_http_request`函数 (通过 `#5919`、`#5918`) 以及对配对码强度的担忧 (`#6613`)。这反映了社区对开放生态中“能力越大，责任越大”的共识。
*   **对稳定性的不满**: 用户对Tool Call在不同模型/供应商间的不一致行为（`#7756`、`#6361`）以及特定渠道（如Telegram）的功能降级（`#6360`）表达了明显的挫败感。用户期望核心功能具有跨平台和供应商的同一性。
*   **对基础体验的抱怨**: 日志输出问题 (`#4721`) 虽然不致命，但影响了使用命令行工具的基础体验。用户`mikeyhew`指出错误输出应发往`stderr`以便于管道操作，这是一个经典的软件实践问题，显示了用户对专业性的要求。

### 8. 待处理积压

*   **重要** `#5919` & `#5918`: 这两项WASM安全性功能请求自4月19日起已存在超过2个月，且与即将发布的v0.8.2 WASM插件平台高度相关。它们目前仅有2条评论，但风险等级高，是重要的安全问题，提醒维护者尽快决策和排期。
*   **`#6361`**: 关于MiniMax等兼容性供应商的Tool Call丢失问题，自5月4日报告以来已逾一月，被认定为S1阻塞性问题但仍在`in-progress`状态，需关注其进展。
*   **长期未关闭的活跃Issue**: `#2503` (NapCat渠道支持) 和 `#2467` (Webhook转换器) 讨论度高，能反映用户强需求。虽然它们可能不在当前里程碑的精确射程内，但应该被标记并视为未来功能规划的重要输入。

</details>

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*