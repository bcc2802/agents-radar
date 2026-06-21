# OpenClaw 生态日报 2026-06-21

> Issues: 500 | PRs: 500 | 覆盖项目: 13 个 | 生成时间: 2026-06-21 04:10 UTC

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

好的，作为一名 AI 智能体与个人 AI 助手领域开源项目分析师，以下是根据您提供的 OpenClaw 项目 GitHub 数据生成的 2026-06-21 项目动态日报。

---

## OpenClaw 项目日报 | 2026-06-21

### 1. 今日速览

OpenClaw 项目今日保持极高的社区活跃度，24小时内产生近500条 Issue 和 PR 更新，但核心组件稳定性问题突出，大量严重 Bug 积压。新版本 v2026.6.9 已发布，主要增强了 Telegram 渠道的富文本交付能力。然而，来自社区的大量 P0/P1 级别的严重 Bug（包括内存泄漏、关键进程崩溃、会话状态丢失）仍处于待修复状态，部分 Bug 已影响用户超过两周，对项目健康度构成了严峻挑战。

### 2. 版本发布

*   **发布版本**: [v2026.6.9](https://github.com/openclaw/openclaw/releases/tag/v2026.6.9)
*   **主要更新**: 本次发布专注于改进 Telegram 消息投递的呈现质量。
    *   **增强的富文本支持**: Telegram 投递现在支持更丰富的 HTML、Markdown 格式、贴纸路径，并能更准确地渲染进度草稿和命令输出。
    *   **HTML 表格安全标准化**: 对 HTML 表格进行了安全处理，避免格式错误。
    *   **投递路径优化**: 确保了提及（mentions）和后台（spooled）处理器能在正确的投递路径上运行。
*   **破坏性变更 / 迁移注意事项**: 暂无。

### 3. 项目进展

虽然今日有 `v2026.6.9` 版本发布和一个针对 ClawSweeper 自动合并流程的 CI 优化 PR，但整体来看，今日并未合并任何修复核心 Bug 的高优先级 Pull Request。项目进展主要集中在自动化流程和新增功能（如添加 `description` 字段用于动态 Agent 发现、Feishu 卡片页脚配置）上。大量已存在的、带 fix PR 的严重 Bug 仍处于等待维护者审查或合并的状态，表明核心问题的解决效率有待提高。

### 4. 社区热点

*   **稳定性和性能回归问题引发广泛讨论**:
    *   **Issue #88312**: [[Bug]: [Regression] 2026.5.27: Codex app-server turn-completion stall returns](https://github.com/openclaw/openclaw/issues/88312) (16条评论，4个👍) - 一个关键的回归问题导致 Codex 应用服务器在完成回合时停滞，用户被迫回滚版本。
    *   **Issue #91588**: [Critical: Gateway Memory Leak — RSS grows from 350MB to 15.5GB over days](https://github.com/openclaw/openclaw/issues/91588) (13条评论) - 严重的网关内存泄漏问题，导致进程因 OOM 被杀死并触发重启循环。此 Issue 反应极多，说明该问题影响范围广。
    *   **Issue #85333**: [[Bug]: openclaw doctor --fix 4-5x slower on 2026.5.20 vs 2026.5.19](https://github.com/openclaw/openclaw/issues/85333) (13条评论) - 性能回归问题导致 `doctor --fix` 命令变慢4-5倍。

    **分析**: 用户及项目核心贡献者 (`petercheng`, `yair`) 报告的问题均指向近期版本（2026.5.20-2026.6.9）引入了重大的稳定性和性能倒退。社区对这些问题表现出高度关注，并提供了详细的复现步骤和根因分析，体现出用户对项目稳定性的强烈诉求。

*   **特定场景下的会话逻辑缺陷**:
    *   **Issue #84583**: [cron announce delivery triggers EmbeddedAttemptSessionTakeoverError](https://github.com/openclaw/openclaw/issues/84583) (9条评论, 3个👍) - Cron 任务投递和用户主动聊天之间的会话锁冲突，导致“会话被接管”错误，影响了 Telegram 等渠道的混合使用体验。

### 5. Bug 与稳定性

以下按严重程度排列，主要关注今日报告的严重问题：

*   **P0 (Critical)**:
    *   **Issue #91588**: [Critical: Gateway Memory Leak](https://github.com/openclaw/openclaw/issues/91588) - **已有修复 PR?** 未提及。该问题导致 RSS 增长至15.5GB，进程被 OOM 杀死，是当前最需要优先处理的稳定性问题。

*   **P1 (High)**:
    *   **Issue #88838**: [Track core session/transcript SQLite migration](https://github.com/openclaw/openclaw/issues/88838) - 核心会话/日志迁移的高风险任务，希望能通过小步提交（branch-by-abstraction）来回避大重构的风险。
    *   **Issue #88312**: [Codex app-server turn-completion stall](https://github.com/openclaw/openclaw/issues/88312) - 回归 Bug，导致 Codex 回合完成一直卡住。
    *   **Issue #85333**: `openclaw doctor --fix` 性能回归。
    *   **Issue #92201**: [Embedded runner: thinking signatures invalid on replay (Anthropic)](https://github.com/openclaw/openclaw/issues/92201) - 内嵌运行器在处理 Anthropic 的“思考”块签名时存在间歇性无效问题。
    *   **Issue #86047**: [Regression: plugin approval stalls interrupt turns](https://github.com/openclaw/openclaw/issues/86047) - 回归问题，插件审批过程导致会话中断和时间超时。
    *   **Issue #92043**: [Compaction timeout is a single wall clock with no partial-progress](https://github.com/openclaw/openclaw/issues/92043) - 压缩超时机制设计缺陷，导致合法但时间长的压缩任务永远失败。
    *   **Issue #92460**: [Isolated cron drops explicit delivery.channel](https://github.com/openclaw/openclaw/issues/92460) - 独立 Cron 任务完成通知时会丢弃显式指定的投递渠道。
    *   **Issue #92415**: [AgentSession.this.model snapshot never refreshed after /model switch](https://github.com/openclaw/openclaw/issues/92415) - 切换模型后，会话内部的模型快照未刷新，可能导致使用错误的模型信息。

*   **P2 (Medium)**:
    *   **Issue #84583**: Cron 通知导致会话接管错误。
    *   **Issue #90354**: 需要为预压缩内存刷新添加有界/已验证的追加语义。
    *   **Issue #90916**: 请求为聊天原生助手增加主题会话家族（topic-session families）功能。

*   **有修复 PR 的 Bug**:
    *   **PR #95476**: 修复模型幻觉生成的文档扩展名（如 `.docodex`）。
    *   **PR #95084**: 修复 Google Chat 泄露内部工具追踪行的问题。
    *   **PR #95278**: 避免复制 `process.env` 的开销（性能修复）。
    *   **PR #95091**: 修复 `doctor` 命令在不加 `--deep` 时发出虚假警告。
    *   **PR #95182**: 修复会话命名从 `label` 迁移到 `title` 过程中的运行时契约不完整问题。

### 6. 功能请求与路线图信号

*   **高频需求**: **会话状态持久化与隔离**。多个 Issue (#90916, #92369, #90354) 表达了用户对于更精细会话控制的渴望，包括：
    *   **主题会话家族**: 同一个 AI 助手能够拥有多个独立对话上下文（lane），并在不同上下文之间隔离“近期的对话记录”，同时共享“永久记忆”。（Issue #90916）
    *   **子代理编排**: 希望在 Cron 隔离会话中可以有可靠的方式来生成、等待并聚合子代理的结果。（Issue #92369）
    *   **有界的追加语义**: 需要为“预压缩内存刷新”操作增加硬性护栏，防止模型写入过大或嘈杂的数据。（Issue #90354）
*   **Kubernetes 部署文档优化**: Issue #91455 提出了改进 Kubernetes 部署指南的建议，说明有用户正在尝试将 OpenClaw 用于更标准化的生产环境部署。

### 7. 用户反馈摘要

*   **核心痛点是稳定性和性能回归**: 用户（如 `yair`, `petercheng`, `samson1357924`）清晰地反馈了近期版本引入的严重回归问题，并提供了详细的复现步骤和实验数据（如具体的耗时对比、内存增长曲线）。这表明项目的 CI/CD 流程在防止性能回退方面存在短板。
*   **对复杂交互场景的支持不足**:
    *   **Cron + 聊天混合使用**: 用户 `jonah791` 反馈 Cron 任务投递与用户主动聊天之间存在锁竞争问题（#84583），导致“会话被接管”错误。这揭示了在单实例、多渠道/多任务模式下，会话管理和锁机制设计存在缺陷。
    *   **子代理的可靠性**: 用户 `eightHundreds` 反馈在 Cron 隔离会话中编排子代理会失败（#92369），因为编排器会话在子代理完成前就结束了。这表明对于异步工作流的支持不够健壮。
*   **特定 AI 提供商的兼容性问题**: 随着更多用户使用 Anthropic (#92201)、Ollama (#94251) 等提供商，出现了与特定模型交互时的兼容性问题（如思考签名无效、流式响应未被消费）。这表明项目在支持多模型时的适配测试可能不足。

### 8. 待处理积压

*   **Issue #57713**: [[Bug]: Default sandbox image lacked python3, breaking edit/write](https://github.com/openclaw/openclaw/issues/57713) - 自2026-03-30起，一个基础的沙箱镜像缺失 `python3` 的问题，已被标记为“stale”。这影响了使用文件编辑/写入工具的默认体验，长期未处理可能会让新用户产生挫败感。
*   **Issue #14785**: [Reduce tool schema token overhead (~3,500 tok/session)](https://github.com/openclaw/openclaw/issues/14785) - 自2026-02-12起，一个关于减少工具 Schema  Token 开销的优化建议。虽然优先级为 P2，但 Token 成本直接关系到用户体验。该项目至今仍在讨论中，其长期存在表明项目在优化基础性能方面的进展缓慢。
*   **Issue #78493**: [sudo openclaw update can create mixed ownership](https://github.com/openclaw/openclaw/issues/78493) - 自2026-05-06起，`sudo openclaw update` 命令可能导致文件所有权混乱的问题。这是一个可能影响用户安全配置和升级流程的关键问题。

---

---

## 横向生态对比

好的，作为资深技术分析师，现根据您提供的各项目动态日报，为您呈上关于 AI 智能体与个人 AI 助手开源生态的横向对比分析报告。

---

### AI 智能体与个人 AI 助手开源生态横向对比分析报告 (2026-06-21)

#### 1. 生态全景

当前，个人 AI 助手与自主智能体开源生态呈现出 **“冰火两重天”** 的态势。一方面，**头部项目（OpenClaw, IronClaw, ZeroClaw）** 社区活跃度极高，开发者正围绕**稳定性、性能、并发安全与平台扩展性**展开激烈攻坚，并已开始从“功能堆叠”向“质量打磨”与“架构优优雅性”过渡。另一方面，大量**中尾部项目（NanoBot, CoPaw, Hermes Agent）** 仍在快速迭代功能，而**更小的项目（PicoClaw, NanoClaw, TinyClaw等）** 则明显进入维护沉寂期，呈现出清晰的 **“马太效应”**。此外，**Token 成本控制**、**会话状态一致性**以及**跨平台体验**已成为所有活跃项目共同面临的“三角难题”。

#### 2. 各项目活跃度对比

| 项目名称 | 今日 Issues | 今日 PRs | 新版本发布 | 健康度评估 |
| :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | ~500 条更新 | ~500 条更新 | v2026.6.9 | **危急** - 严重 Bug 积压，社区对稳定性强烈不满 |
| **NanoBot** | 中等 | 极高 | 无 | **良好** - 并发安全修复与性能优化是焦点 |
| **Hermes Agent** | 50 条 | 50 条 | 无 | **良好** - 活跃的 Bug 修复与功能迭代 |
| **PicoClaw** | 2 (stale) | 1 (stale) | Nightly Build | **待激活** - 活跃度低，用户反馈长期未响应 |
| **NanoClaw** | 1 | 6 | 无 | **中等** - 维护者需尽快处理待合并 PR 与安全 CVE |
| **NullClaw** | 1 | 0 | 无 | **平稳** - 社区活跃度极低，但未报告严重问题 |
| **IronClaw** | 极少量 | 21 (堆叠) | 无 | **极佳** - 核心团队主导的密集开发期，架构进化中 |
| **LobsterAI** | 0 (新) | 0 | 无 | **待激活** - 自动清理 stale 问题，无新开发动作 |
| **TinyClaw** | 0 | 0 | 无 | **基本停滞** - 0 活动 |
| **Moltis** | 0 | 2 (Dependabot) | 无 | **维护期** - 仅依赖更新，社区无互动 |
| **CoPaw** | 13 | 15 | 无 | **良好** - 从功能添加转向质量打磨，Bug 修复为主 |
| **ZeptoClaw** | 0 | 0 | 无 | **基本停滞** - 0 活动 |
| **ZeroClaw** | 50 | 50 | 无 | **极佳** - 极高活跃度，功能与稳定性并进 |

#### 3. OpenClaw 在生态中的定位

*   **优势与差异化**： OpenClaw 作为“核心参照”项目，拥有该生态中**最庞大的社区基础**和**最广泛的渠道（如丰富的富文本支持）与模型集成**。其设计理念强调**高度的可配置性与模块化**，允许用户深度定制 Agent 行为。
*   **技术路线**： 倾向于通过复杂的配置和插件系统来处理多样性，这导致了当前**严重的稳定性与性能回归**问题，暴露出其架构复杂性带来的维护成本。
*   **社区规模与当前危机**： OpenClaw 的社区规模无疑是最大的，但 **“社区越大，期望越高”** 。今日 V2026.6.9 版本的发布并未带来核心 Bug 修复，反而加剧了因稳定性问题（内存泄漏、进程卡死）引发的用户不满。与其说它是“功能领导者”，不如说它已成为**检验生态稳定性的压力测试场**。相比之下，IronClaw 和 ZeroClaw 因更聚焦的核心团队和更审慎的迭代节奏，社区健康度明显更优。

#### 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求 |
| :--- | :--- | :--- |
| **Token 成本与性能优化** | **Hermes Agent (#4379, #13983)**, **NanoBot (#4420)**, **NanoClaw (#2768)**, **ZeroClaw (#5808)** | 社区普遍要求优化固定开销（如工具 schema 编码）、默认启用缓存、缩短 Token 使用量。 |
| **并发安全与状态隔离** | **NanoBot (#4408)**, **OpenClaw (#84583)**, **CoPaw (#5344)**, **ZeroClaw (#6037)** | 核心运行时在多会话/多任务下的竞态条件、会话锁冲突、Cron 任务并发执行等问题。 |
| **会话状态持久化与上下文管理** | **OpenClaw (#90916, #90354)**, **Hermes Agent (#33618, #45059)**, **ZeroClaw (#5849, #6517)** | 用户渴望“永久记忆”与“短期上下文”的精细隔离、可靠的上下文压缩机制，以及更智能的记忆管理。 |
| **跨平台体验一致性** | **NanoBot (#4407, #4422)**, **OpenClaw (#84583)**, **Hermes Agent (#4335)**, **ZeroClaw (#7531)** | 用户希望在不同渠道（Telegram, WhatsApp, CLI, Web）获得一致的无缝体验，尤其是消息状态和富文本渲染。 |
| **第三方模型与提供商兼容性** | **CoPaw (#5345, #5328)**, **Hermes Agent (#92201)**, **NanoBot (#4429)**, **OpenClaw (#88838)** | 自定义 OpenAI 兼容 API、DeepSeek 等高性价比模型的特有 Bug 和思考模式适配。 |

#### 5. 差异化定位分析

| 项目 | 核心定位 | 目标用户 | 技术架构关键差异 |
| :--- | :--- | :--- | :--- |
| **OpenClaw** | “全能性”个人 AI 助手平台 | 高级用户、深度定制者、多模型/渠道重度用户 | 模块化插件架构，功能全面但复杂度高；当前稳定性问题严重。 |
| **IronClaw** | “企业级” Agent 运行时 | 开发者、需要高可靠性和可扩展性的团队 | Rust 为核心，强调**架构优雅性**（如 Manifest 驱动通道）和**性能**，但社区是核心团队主导。 |
| **ZeroClaw** | “创新性” Agent 平台 | 探索者、社区贡献者、重视 AI 自主学习的用户 | 拥有独特的 **Dream Mode (记忆整合)** 和丰富的 **v0.9.0 (安全/认证) 路线图**，功能迭代与稳定性并进。 |
| **CoPaw** | “易用性” Agent 平台 | 中文用户、关注 UI/UX 的开发者 | 对中文模型（DeepSeek, Zhipu）和社区（QQ, WeChat）支持更好，近期重点从功能转向 **Bug 修复与 UI 打磨**。 |
| **NanoBot** | “高性能” Agent 轻量级框架 | 集成商、对性能和并发要求高的开发者 | 追求 **轻量、高性能和异步并发**；当前正积极修复并发安全问题，项目健康度快速提升。 |
| **PicoClaw/** **NanoClaw** | 特定场景或子项目 | 特定需求（如 WebSocket、CVE），容易因维护者精力分散而失活 | 功能单一，活跃度严重依赖上游或核心维护者，属于生态的 **“边缘”** 部分。 |

#### 6. 社区热度与成熟度
- **快速迭代/开发冲刺阶段**: **IronClaw, ZeroClaw**。核心团队主导，大量 PR 堆叠，架构发生显著变化。
- **功能丰富化与质量巩固阶段**: **NanoBot, Hermes Agent, CoPaw**。社区反馈开始涌现，Bug 修复与优化成为主旋律，逐步从“能用”走向“好用”。
- **成熟但面临挑战阶段**: **OpenClaw**。拥有最大的社区，但正经历因快速增长带来的“成长的烦恼”，稳定性成为最大短板。
- **长期维护/沉寂阶段**: **PicoClaw, NanoClaw, NullClaw, LobsterAI, TinyClaw, Moltis, ZeptoClaw**。无新功能或修复，或仅有依赖更新，社区活力严重不足。

#### 7. 值得关注的趋势信号
1.  **“开箱即用”的性能需求压倒一切**：用户不再满足于“能工作”，而是要求“高效工作”。**Token 成本优化**是最高频的社区诉求，直接影响用户留存和项目口碑。开发者应优先排查默认配置下的冗余开销（如工具 schema、缓存策略）。
2.  **智能体的“自我认知”是下一个突破口**：用户正期待 Agent 具备超越“执行命令”的元认知能力，包括识别自身能力边界、理解“记忆”与“上下文”的区别，甚至具备“做梦”式的反思学习能力。这将是开启下一代产品差异化的关键。
3.  **生态的马太效应初现**：项目的活跃度与迭代速度呈现两极分化。**开发者应慎重评估依托**。加入 OpenClaw 可能获得最大资源，但需面对其稳定性风险；选择 IronClaw 或 ZeroClaw 则能享受更聚焦、更健壮的开发体验，但社区规模较小。
4.  **“安全”与“治理”不再是锦上添花**：ZeroClaw 独立的 v0.9.0 安全路线图和 IronClaw 的 Manifest 驱动通道，表明社区正从后端架构层面严肃对待认证、授权与CVE漏洞。这预示着 AI Agent 正从“个人玩具”走向“商业级应用”的关键一步。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

好的，作为 NanoBot 开源项目分析师，我已根据您提供的 GitHub 数据，为您生成 2026-06-21 的项目动态日报。

---

### 每日项目动态日报：NanoBot (github.com/HKUDS/nanobot)

**报告日期:** 2026-06-21
**数据覆盖:** 过去24小时 (截至 2026-06-21)

---

### 1. 今日速览

项目今日活跃度 **极高**。核心开发者和社区成员围绕并发安全、性能优化和平台扩展三大方向提交了大量代码。`Bug`修复和`性能优化`是今日绝对焦点，特别是 `run()` 方法的竞态条件和工具令牌估算效率问题，均有高质量的 `fix/PR` 跟进处理。此外，Telegram、WhatsApp、iMessage 等通道功能的增强也显示了社区对多平台支持的持续热情。项目正从功能丰富化转向深层稳定性与性能打磨，整体健康状况 **良好**。

### 2. 版本发布

- **无新版本发布。** 项目正处于密集开发阶段，多个 PR 仍在审查中，尚未形成新的稳定版或预发布版。

### 3. 项目进展

今日有 **4 个 PR 被合并或关闭**，项目在代码质量和稳定性上取得重要进展：

- **修复 MCP 服务器关闭时的崩溃问题** [PR #4303](https://github.com/HKUDS/nanobot/pull/4303)
  - **状态**: 已合并/关闭
  - **内容**: 修复了当 `streamableHttp` MCP 服务器会话结束时，`_close_server` 在不同 asyncio 任务中尝试退出作用域导致的 `RuntimeError` 崩溃。这是一个影响 MCP 工具调用稳定性的关键修复。
- **修复 Dream 功能禁用时提示膨胀问题** [PR #4321](https://github.com/HKUDS/nanobot/pull/4321)
  - **状态**: 已合并/关闭
  - **内容**: 修复了当 `dream.enabled` 设为 `false` 时，Dream 光标未正常推进，导致历史记录处理函数错误地认为有未处理内容，从而引发提示词无限制增长的问题。
- **修复 iOS Safari 输入框自动缩放问题** [PR #4427](https://github.com/HKUDS/nanobot/pull/4427)
  - **状态**: 已合并/关闭
  - **内容**: 修复了 WebUI 在 iOS Safari 上聚焦输入框时导致页面自动缩放的小众但影响用户体验的 Bug。通过为移动端输入框设置最小字体大小解决。
- **新增 iMessage 通道** [PR #4426](https://github.com/HKUDS/nanobot/pull/4426)
  - **状态**: 已合并/关闭
  - **内容**: 成功地通过 `Photon Spectrum` 服务为 NanoBot 新增了 iMessage 通道。这极大地扩展了项目的用户触达范围，尤其受苹果用户欢迎。

### 4. 社区热点

今日讨论最活跃、最受关注的问题是 **并发安全性**，直接引发了两条相关的 PR：

- **议题 #4408** ([链接](https://github.com/HKUDS/nanobot/issues/4408)): **`Nanobot.run()` 并发竞态条件**
  - **热度**: 2条评论，1个早期Bug报告，并直接导致了今日的PR #4425 和 #4409 的诞生。
  - **核心诉求**: 用户明确指出核心API `Nanobot.run()` 存在严重并发问题。当多个请求并行执行时，共享的 `_extra_hooks` 状态会被互相覆盖，导致钩子执行混乱。这暴露了项目初期设计对异步并发考虑不足的问题，是社区测试中发现的重大隐患。
- **PR #4425** ([链接](https://github.com/HKUDS/nanobot/pull/4425)): **使用 `contextvars` 修复并发竞争**
  - **来源**: 针对 Issue #4408 的直接修复方案，作者尝试利用 Python 的 `contextvars` 特性来隔离每次调用的状态。
- **PR #4409** ([链接](https://github.com/HKUDS/nanobot/pull/4409)): **通过传递参数而非修改共享状态修复**
  - **来源**: 针对 Issue #4408 的另一种修复思路，通过修改方法签名在调用链间传递钩子列表。
  - **社区动态**: 两个并行的修复方案表明社区对此问题极度重视，并且维护者正从不同角度评估最佳解决方案。这将是近期核心代码审查的重点。

### 5. Bug 与稳定性

今日报告的 Bug 和稳定性问题主要集中在以下方面，按严重程度排列：

- **严重 - 并发安全性**:
  - **[Bug] `Nanobot.run()` per-run hooks 并非并发安全** (Issue [#4408](https://github.com/HKUDS/nanobot/issues/4408))
    - **状态**: 有 2 个功能互补的修复 PR ([#4425](https://github.com/HKUDS/nanobot/pull/4425), [#4409](https://github.com/HKUDS/nanobot/pull/4409)) 正在审查中。这是最核心的运行时Bug，影响多用户/多会话场景下的一切行为。
- **中等 - 性能回归/冗余计算**:
  - **[Enhancement] `estimate_prompt_tokens` 函数对工具定义进行冗余 tiktoken 编码** (Issue [#4420](https://github.com/HKUDS/nanobot/issues/4420))
    - **状态**: 有 2 个性能优化 PR ([#4421](https://github.com/HKUDS/nanobot/pull/4421), [#4428](https://github.com/HKUDS/nanobot/pull/4428)) 被提出，均旨在缓存序列化后的工具定义，有望显著降低每次迭代的延迟。
- **低 - 日志与错误检测**:
  - **[Fix] Telegram 通道的富文本能力错误检测过于宽泛** (PR [#4423](https://github.com/HKUDS/nanobot/pull/4423))
    - **状态**: 待合并。修复了错误地将常见临时性错误视为“不支持富文本”的问题，并改善误导性日志。

### 6. 功能请求与路线图信号

用户提出的新功能需求，结合已有的 PR，显示出项目下一阶段的演进方向：

- **自定义提供商思考模式** (Issue [#4429](https://github.com/HKUDS/nanobot/issues/4429))
  - **诉求**: 允许用户通过 `custom` 提供商为模型配置非标准的思考/推理模式参数（如 VolcEngine/Doubao）。
  - **路线图信号**: 此请求表明用户对支持更多差异化的 LLM 服务商的需求强烈，尤其是国内大模型。实现此功能将提升项目的灵活性和本地化适配能力。
- **Telegram `sendRichMessage` API 支持** (Issue [#4422](https://github.com/HKUDS/nanobot/issues/4422))
  - **诉求**: 在 Telegram 通道中原生支持新 `sendRichMessage` API，以渲染表格、任务列表等复杂内容。
  - **路线图信号**: 紧跟上游平台 API 更新，提升特定通道的用户体验，符合社区长期期望。已有相关修复 PR ([#4423](https://github.com/HKUDS/nanobot/pull/4423))，说明开发者在积极响应。
- **子代理聚合结果模式** (PR [#4414](https://github.com/HKUDS/nanobot/pull/4414))
  - **诉求**: 为 Subagent 提供“聚合”模式，将并发子任务的结果合并为一条消息发送，而非实时逐条发送。
  - **路线图信号**: 这是对复杂工作流和代码执行场景的深度优化，旨在减少用户信息轰炸，提升可读性。

### 7. 用户反馈摘要

从今日的 Issues 评论中，可以提炼出以下用户痛点和场景：

- **“数字员工”性能瓶颈** (Issue [#4420](https://github.com/HKUDS/nanobot/issues/4420))
  - **用户**: `codeLong1024` (个人项目 `nanobee` 开发者)。
  - **痛点**: 项目响应慢。用户通过自身项目定位到是 `estimate_prompt_tokens` 函数在每次调用时都重新对工具定义做 JSON 序列化和 tiktoken 编码，导致冗余计算。
  - **诉求**: 用户希望上游项目能将工具定义的序列化缓存下沉到 tiktoken 编码层，以显著提升性能。这反映了用户对 NanoBot 性能极致优化的期待。
- **WhatsApp 首个消息无法识别** (PR [#4407](https://github.com/HKUDS/nanobot/pull/4407))
  - **痛点**: 在WhatsApp通道中，如果一个新联系人的首条消息使用LID（而非手机号）发送，该消息无法被解析和授权，导致用户无法与机器人正常对话。
  - **诉求**: 用户希望在启动时预加载LID到手机号的映射，确保首条消息也能被正确处理。

### 8. 待处理积压

以下为近期未获响应或进展缓慢的重要 Issue/PR，建议维护团队关注：

- **内存历史光标单调性修复** (PR [#4256](https://github.com/HKUDS/nanobot/pull/4256))
  - **创建时间**: 2026-06-08
  - **状态**: 待合并（已更新）
  - **重要性**: **高**。此 PR 目标是修复 `MemoryStore` 中历史记录光标分配可能不单调的问题，尤其在光标过期、被压缩或为负值时。这直接影响对话记忆的完整性和可靠性，是比较核心的稳定性修复。已近两周未获得最终审查，建议尽快安排。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

好的，这是为您生成的 Hermes Agent 项目动态日报。

---

# Hermes Agent 项目动态日报 | 2026-06-21

## 1. 今日速览

本项目在2026年6月21日表现出极高的活跃度。过去24小时内，共有50条Issue和50条PR被更新，表明社区参与度和项目维护力度均处于高位。主要焦点集中在**上下文压缩**和**会话状态持久性**的多个Bug修复上，同时社区也表达了对**Token开销**和**跨平台会话共享**等性能与功能方面的高度关注。虽然今日无新版本发布，但大量针对P1/P2级别关键Bug的修复PR已提交或合并，项目健康度正在快速修复中。

## 2. 版本发布

无

## 3. 项目进展

今日共有34个PR被合并或关闭，项目在多个关键领域取得了显著进展：

-   **关键Bug修复（上下文压缩与数据丢失）**：
    -   **PR #49925** (P1) 已合并：修复了网关会话卫生系统自动压缩时，若无法轮换session_id，会直接破坏原始对话记录的数据丢失Bug (`#21301`)。
    -   **PR #48956, #45059, #33618** 均已关闭（标记为重复或已修复）：针对因上下文压缩轮换`session_id`导致的`/goal`状态丢失问题，核心修复方案已被识别并实施。
    -   **PR #49930** (P1) 已提交：修复了Telegram适配器中因缺乏`keepalive`限制导致的文件描述符泄漏和`CLOSE_WAIT`问题 (`#31599`)，解决了该平台长期运行的稳定性隐患。

-   **功能与基础设施**：
    -   **PR #47425** 已合并：模型目录新增了MiniMax M2.7模型支持。
    -   **PR #48617** 已关闭（设计提案）：提出了基于规则的任务模型路由策略，旨在优化不同任务（如工具调用、写作）的模型选择，提升效率。
    -   **多个文档PR** (#47628, #48881, #49382, #47631, #47396, #48545) 已合并：涉及社区知识库链接、文档修订、安装依赖说明及配置参考更新，项目文档得以持续完善。
    -   **依赖项更新**：多个由 `dependabot` 发起的`/website`目录下的JavaScript依赖项更新PR已合并，提升了网站安全性。

## 4. 社区热点

今日最受关注的议题反映了用户对**性能成本**和**用户体验一致性**的强烈需求：

1.  **Issue #4379: Token开销分析** (15条评论, P3)
    -   **内容**：用户 `Bichev` 创建了一个监控仪表盘，分析了Hermes v0.6.0的Token消耗。结论是**每个API调用的73%是固定开销（约13.9K Token）**，并附上了详细的监控仪表盘链接和数据建议。
    -   **链接**：[NousResearch/hermes-agent Issue #4379](https://github.com/WeOpenLang/hermes-agent/issues/4379)
    -   **分析**：此问题引发了对Hermes基础架构效率的深入讨论。社区希望优化Token利用率以降低成本，而不仅仅是关注单次交互的Token总量。

2.  **Issue #13983: 默认Token消耗过高** (5条评论, P2)
    -   **内容**：用户 `mikelemo` 反馈，即使是一个简单的“who u”提示，默认安装也会消耗超过16K Token，质疑其合理性。
    -   **链接**：[NousResearch/hermes-agent Issue #13983](https://github.com/WeOpenLang/hermes-agent/issues/13983)
    -   **分析**：这直接关系到新用户的入门成本。与 `#4379` 相关联，社区强烈希望核心团队能优化默认配置下的Token开销，降低使用门槛。

3.  **Issue #41190: 统一插件路由选择器** (5条评论, P3)
    -   **内容**：用户 `MarkoPaasila` 提出需要一个统一的、可由插件访问的路由钩子，以覆盖每个LLM调用的`provider`和`model`，解决当前路由逻辑分散的问题。
    -   **链接**：[NousResearch/hermes-agent Issue #41190](https://github.com/WeOpenLang/hermes-agent/issues/41190)
    -   **分析**：这表明社区对复杂工作流（主模型、辅助模型、备用模型）的配置灵活性和可编程性提出了更高要求。

## 5. Bug 与稳定性

今日报告的Bug按严重程度排列如下：

-   **P1 (最高)**
    -   `#49903`: Desktop v0.17.0 升级后抛出 `Uncaught Error: Composer is not available`，导致输入无响应。**尚无修复PR**。
    -   `#49768`: 上下文压缩运行时导致 Dashboard 进程CPU 100%，桌面客户端超时。**已标记为已关闭（可能被修复/合并）**。
    -   `#49824`: v0.17.0网关启动失败，报错 `ModuleNotFoundError: cron.scheduler_provider`。**已标记为重复/已关闭**。

-   **P2 (重要)**
    -   `#49937`: Windows上`openai-codex` provider初始化失败，影响CLI、API_server等。已有修复**PR #49945**提交。
    -   `#49920`: Windows桌面应用更新后卡死在CONNECTING界面，原因是仪表盘构建时`NODE_ENV=production`导致`npm install`跳过开发依赖。**尚无修复PR**。
    -   `#49014`: Windows上`ssl_guard.py`因`truststore`库导致`NotImplementedError`。已有修复**PR #49945**提交。
    -   `#49747`: Docker中TTS edge插件懒安装失败，原因是环境变量被错误锁定为`1`。**尚无修复PR**。

-   **P3 (一般)**
    -   `#49911`: NVIDIA NIM provider模型列表被截断，只显示前50个模型。**尚无修复PR**。

**稳定性总结**：今日Bug主要集中在会话持久化、平台兼容性（特别是Windows和Docker）以及资源泄漏上。其中，`/goal`状态丢失和Telegram fd泄漏已被定位并修复，这显著增强了核心功能的稳定性。但Desktop v0.17.0的`Composer`错误和Windows安装问题仍是需要立即解决的P1级障碍。

## 6. 功能请求与路线图信号

-   **高优先级信号**：
    -   **Token优化**（`#4379`, `#13983`）和**路由灵活性**（`#41190`, `#48617`）是社区呼声最高的领域。`PR #32513`（减少attach操作Token费用）和`PR #48617`（基于规则的路由策略）的提出，表明核心开发团队已开始响应这些需求，它们极有可能被纳入下一版本的路线图。
    -   **跨平台会话共享** (`#4335`) 被标记为P3，但其3条评论和1个👍显示需求是存在的，可能作为长期功能点进行规划。

-   **中等优先级信号**：
    -   **国际化/本地化支持** (`#37543`) 和 **Python 3.14支持** (`#48723`) 代表了项目在受众和兼容性上的扩展方向。这些通常不会在紧急修复版本中优先处理，但会作为重要的社区信号被维护者收集。

## 7. 用户反馈摘要

-   **核心痛点**：
    -   **高Token消耗是用户的“心头大患”**。用户`mikelemo`和`Bichev`的反馈都直指“默认配置下Token消耗过高”的问题，这不仅是成本问题，也影响了用户对项目效率的第一印象。
    -   **状态丢失引发不信任感**。`/goal`在上下文压缩后丢失的问题（`#33618`, `#45059`等）被多名用户报告，这类数据持久性问题严重影响了用户对Agent记忆能力的信任。
    -   **平台间体验割裂**。用户`Logi4k`提出的跨平台会话共享需求，揭示了多平台使用时“信息孤岛”的痛点，即在一个平台（如CLI）上的上下文无法在另一个平台（如Telegram）延续。

-   **使用场景**：从Issue内容可以看出，Hermes Agent被广泛应用于**Telegram/WhatsApp/Cron网关**（`#4379`）、**桌面应用**（`#49903`）、**CLI接口**（`#13983`）以及通过**WebUI**进行长时间会话（`#33907`）等场景。

## 8. 待处理积压

以下是长期未解决、但今日再次被提及的重要Issue，提醒维护者关注：

-   **`#4379` Token开销分析**：这是一个P3级别但评论火爆的Issue，其作者不仅报告了问题，还提供了监控仪表盘和详细数据。该Issue的持续活跃表明社区对性能优化的强烈意愿。维护者可考虑将此纳入性能优化专项讨论。
-   **`#4335` 跨平台会话共享**：自2026年3月31日提出以来，该Issue一直未获得官方解决。随着多平台使用场景的普及，此需求可能逐渐从P3升级。维护者可在社区对该Issue给予更多关注。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw 项目动态日报 (2026-06-21)

## 1. 今日速览
- **整体活跃度：中等偏低**。过去24小时仅有2个Issue和1个PR更新，且均为长期未更新的“stale”条目，无新提交或合并活动，社区活跃度较低。
- **版本发布**：今日发布了一个 **nightly 构建**（v0.3.0-nightly.20260621），属于自动化不稳定版本，无明确破坏性变更说明。
- **社区讨论**：两个open Issue均为用户持续关注点，特别是关于“进化”功能下Token持续消耗的bug和WebSocket协议层面的客户端信号缺失，反映用户对稳定性和协议完整性的需求。
- **维护进展**：项目维护者在这一天没有响应或合并任何PR/Issue，所有条目均为用户自行更新评论，显示维护响应速度放缓。

## 2. 版本发布
- **新版本**：Nightly Build (v0.3.0-nightly.20260621.287853ab)
  - **类型**：自动化构建，不稳定
  - **变更内容**：对比 v0.3.0 与 main 分支的完整变更日志（[查看详情](https://github.com/sipeed/picoclaw/compare/v0.3.0...main)）
  - **破坏性变更**：未注明
  - **迁移注意**：建议仅供测试，生产环境勿用。如需回退，请使用稳定版 v0.3.0 或 v0.2.9。

## 3. 项目进展
- **今日无已合并/关闭的PR**。所有PR均为open状态，项目未向前推进任何明确的新功能或修复。

## 4. 社区热点
- **#3012 BUG**： [Continuous consumption of tokens every minutes when evolution is enabled](https://github.com/sipeed/picoclaw/issues/3012)
  - **热度**：评论 4 条，用户 @xpader 持续报告在启用了“进化”功能后，即使没有用户输入，token也会每分钟持续消耗。该问题已存在约16天，未获官方回复。
  - **诉求分析**：用户表达了强烈的**财务成本焦虑**，担心后台自动轮询或状态同步导致的浪费。同时，问题与 FreeBSD 环境、MiniMax 模型组合高度相关，需要运维侧排查。
- **#2984 Feature**： [Add explicit turn completion signal for Pico WebSocket clients](https://github.com/sipeed/picoclaw/issues/2984)
  - **热度**：评论 3 条，获得 2 次 👍。外部 WebSocket 客户端开发者希望获得明确的“本轮对话结束”信号，以便可靠地控制UI状态（如停止显示“typing”并等待用户新输入）。
  - **诉求分析**：这是一个**协议层面**的缺失，影响所有基于Pico协议构建第三方客户端的开发者，用户渴望获得与官方客户端相同级别的事件驱动确定性。

## 5. Bug 与稳定性
- **严重**：
  - **#3012**: Token持续消耗（即使无对话） -> 高昂成本风险。**无 fix PR**，问题已停留16天，建议立即定位。
- **中等**：
  - （今日无新崩溃或回归问题被报告）

## 6. 功能请求与路线图信号
- **#2984**: 明确请求添加`turn_complete`信号。虽然无关联PR，但结合 PR #2964（仍在open，过期）以及社区对协议一致性的关注，该功能**很有可能被纳入下一版本**的开发计划，尤其是对于想构建多模态或复杂交互服务的开发者而言。
- **#2964 (PR)**： **Feat/image input compression**（stale）—— 如果该PR能在近期被合并，将正式引入入站图像压缩策略，补全视觉管线配置能力。

## 7. 用户反馈摘要
- **痛点**：
  - 成本浪费：@xpader 在 #3012 中描述“i see token count go up even when i'm not at the computer”，反应后台无意义轮询导致超额计费。
  - 协议可靠性：@Brook-sys 在 #2984 中表示“当前通过`typing.stop`推断结束是不可靠的”，希望获得HTTP/WS标准的“完成”信号。
- **满意度**：无明显正面评价。用户积极贡献问题描述但长期未获维护者反馈，表明**用户对维护及时性感到不满或失望**。
- **使用场景**：多为高级用户（开发者、集成方），使用环境多样（FreeBSD、Web、Go语言客户端），验证了PicoClaw的可移植性，但也暴露了特定环境下的兼容性风险。

## 8. 待处理积压
- **#3012**：严重Cost Bug，已16天无响应。**建议维护者优先确认并给出临时规避方案**。
- **#2984**：协议功能需求，已有2个👍，影响面广。**建议纳入下次Sprint讨论**。
- **#2964 (PR)**：图像压缩功能PR过期21天，无review。**建议维护者评估是否合并，否则关闭以免误导社区**。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw 项目动态日报 (2026-06-20)

---

## 1. 今日速览

项目今日保持中等活跃度，**无新版本发布**。过去24小时关闭了0个Issue/PR，但新提交了1个Issue和6个待合并PR，主要集中在小幅清理重构、文档补充和安全修复领域。社区讨论焦点围绕 **Claude provider 默认启用 prompt caching** 的性能优化建议，以及多个清理死代码/文档的PR。整体健康度良好，维护者需关注6个待合并PR的审核与合并进展。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

今日无已合并/关闭的PR，但以下 **6个OPEN PR** 显示了项目向前推进的方向：

| PR # | 标题 | 作者 | 类型 | 关键点 |
|------|------|------|------|--------|
| #2824 | fix: drop stale "Global Memory" instruction from main seed prompt | CutSnake01 | 修复 | 移除主种子提示中的过时全局内存指令 |
| #2823 | fix: remove groups/global/CLAUDE.md (host deletes it on every startup) | CutSnake01 | 修复 | 移除每次启动被主机删除的无效全局配置文件 |
| #2822 | refactor(container-runner): drop dead /workspace/global mount | CutSnake01 | 重构 | 清理容器运行器中无用的 /workspace/global 挂载 |
| #2821 | docs: document assistant-name environment variables | chandrameenamohan | 文档 | 补充 assistant-name 环境变量的文档 |
| #2799 | fix(security): confine send_file reads to /workspace (CVE-2026-29611) | sturdy4days | **安全修复** | 修复路径遍历漏洞 CVE-2026-29611 |
| #2801 | fix(router): guard safeParseContent against non-object JSON | sturdy4days | 修复 | 修复 JSON 原始类型解析导致的 undefined 回退 |

**项目向前迈进的量化评估：**
- 4项清理和文档优化 → 提升代码质量和可维护性
- 1项高危安全漏洞修复（CVE）→ 重要的安全加固
- 1项解析稳定性修复 → 改善异常输入处理

---

## 4. 社区热点

### 最活跃 Issue：#2768
- **标题**：Enable prompt caching by default in Claude provider  
- **作者**：galmorduku  
- **链接**：[Issue #2768](https://github.com/qwibitai/nanoclaw/issues/2768)  
- **热度**：1条评论，讨论持续6天  
- **诉求分析**：  
  用户指出 Claude provider 在调用 `sdkQuery()` 时未设置 `enablePromptCaching`，导致每次交互都重新发送完整系统提示（system prompt），对包含丰富上下文的 Agent 造成显著的性能和成本浪费。  
  **核心诉求**：默认启用 prompt caching 功能，在不破坏现有行为的前提下优化性能。这反映出社区对 **运行效率与成本控制** 的高度关注。

### 最活跃 PR 集群：由 **CutSnake01** 提交的3个清理修复PR（#2824, #2823, #2822）
- **共同特征**：均针对项目中的 **遗留/死代码** 和 **无效配置**  
- **信号**：社区成员在主动清理技术债务，维护代码整洁度

### 安全热点 PR：#2799
- **标题**：fix(security): confine send_file reads to /workspace (CVE-2026-29611)  
- **作者**：sturdy4days  
- **链接**：[PR #2799](https://github.com/qwibitai/nanoclaw/pull/2799)  
- **重要性**：报告了一个已被分配 CVE 编号的路径遍历漏洞，允许注入 agent 读取容器内任意文件（包括凭证状态和外部挂载路径）。这是今日最严重的风险点。

---

## 5. Bug 与稳定性

| 编号 | 严重程度 | 摘要 | 状态 | 备注 |
|------|----------|------|------|------|
| PR #2799 | **严重 (CVE-2026-29611)** | `send_file` 未限制读取根目录，允许任意文件读取 | 待合并 | 已有修复PR，需优先审核 |
| PR #2801 | 中等 | `safeParseContent` 对 `"5"`、`"true"` 等原始JSON返回非对象，导致 `.text`/`.sender` 为 `undefined` | 待合并 | 影响部分路由消息处理 |
| Issue #2768 | 低 | Claude provider 未启用 prompt caching，导致性能/成本次优 | 待讨论 | 非功能性缺陷，算优化建议 |

**稳定性总结**：安全漏洞 CVE-2026-29611 是今日最严峻的稳定性威胁，需尽快合并 #2799。其余问题均属于功能完善层面。

---

## 6. 功能请求与路线图信号

| 来源 | 功能请求 | 未来可能性 | 判断依据 |
|------|----------|------------|----------|
| Issue #2768 | 默认启用 Claude provider 的 prompt caching | **高** | 零成本性能收益，且 Anthropic SDK 已有选项，只需改默认值 |
| PR #2821 | 文档化 assistant-name 环境变量 | **确认纳入** | 已是待合并的文档PR |

**路线图信号**：  
由 community-member 发起的4项清理和文档PR（CutSnake01），表明社区正在 **自发减轻项目技术债务**，这类清洁工作可能是下一版本发布前的预准备。

---

## 7. 用户反馈摘要

从目前仅有1条评论的 Issue #2768 中提炼：

> **用户痛点**（galmorduku）：  
> “The Anthropic Agent SDK defaults this to `false` for agent sessions, so every turn re-sends the full system prompt uncached. For agents with rich context, this is especially impactful.”  
> **翻译**：Anthropic SDK 默认关闭缓存，导致每轮对话都重新发送完整系统提示，对包含丰富上下文的 Agent 影响尤其严重。  
> **使用场景**：复杂上下文 Agent 应用  
> **不满意点**：默认行为导致不必要的性能开销和成本

**其他 PR 评论**：6个待合并PR均无社区评论，可能因 PR 提交集中且尚未引发大规模讨论。

---

## 8. 待处理积压

| 类型 | 编号 | 说明 | 年龄 | 提醒 |
|------|------|------|------|------|
| **安全PR** | [#2799](https://github.com/qwibitai/nanoclaw/pull/2799) | CVE-2026-29611 路径遍历漏洞修复 | 3天（6月17日） | **优先审核**，有安全影响 |
| 修复PR | [#2801](https://github.com/qwibitai/nanoclaw/pull/2801) | JSON原始类型解析修复 | 3天（6月17日） | 建议合并 #2799 后处理 |
| 清理PR | [#2822](https://github.com/qwibitai/nanoclaw/pull/2822) | 容器运行器死代码清理 | <1天 | 低优先级，可批量合并 |
| 清理PR | [#2823](https://github.com/qwibitai/nanoclaw/pull/2823) | 全局配置文件清理 | <1天 | 同上，建议与 #2822/#2824 合并 |
| 清理PR | [#2824](https://github.com/qwibitai/nanoclaw/pull/2824) | 种子提示清理 | <1天 | 同上 |
| 文档PR | [#2821](https://github.com/qwibitai/nanoclaw/pull/2821) | assistant-name 环境变量文档 | <1天 | 可合并 |
| 功能Issue | [#2768](https://github.com/qwibitai/nanoclaw/issues/2768) | Claude prompt caching 优化 | 6天（6月14日） | 未分配，等待维护者回应 |

**需要关注的长期待办**：  
除 #2799 和 #2801 外，其他待合并PR均可在一次 review 中批量处理。Issue #2768 虽不紧急，但可标记为“enhancement”并规划到下一迭代。

---

*报告生成时间：2026-06-21 00:00 UTC | 数据来源：NanoClaw GitHub*

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

好的，这是为您生成的 NullClaw 项目 2026-06-21 动态日报。

---

## NullClaw 项目动态日报 | 2026-06-21

### 1. 今日速览

过去24小时，NullClaw 项目整体活跃度较低。社区层面仅新增一个关于“NoResponseContent”错误的 Bug 报告，尚未有 PR 或新版本发布。当前项目健康度平稳，但核心开发动作放缓，维护者需重点关注近期出现的较高频次、高复现率的稳定性问题。

### 2. 版本发布
- 无新版本发布。

### 3. 项目进展
- 今日无 PR 被合并或关闭，项目无明显功能或修复推进。

### 4. 社区热点
- **#967 [Bug] error: NoResponseContent** ([链接](https://github.com/nullclaw/nullclaw/issues/967))
    - **热度分析**: 这是今日唯一的社区动态，虽无评论，但用户描述了很高的复现频率（>50%）。该问题直接关联到 Agent 功能的核心响应能力，可能影响大量用户的正常使用，是潜在的紧急问题。
    - **背后诉求**: 用户报告了在使用 `nullclaw agent` 命令时，程序在等待 27 秒后返回“NoResponseContent”错误，且发生频率极高。用户明确指出了相同的模型和 API Key 在“picocla”产品中工作正常，暗示问题可能出在 NullClaw 客户端与服务端的通信或响应处理逻辑上。

### 5. Bug 与稳定性
- **[严重] #967 error: NoResponseContent** ([链接](https://github.com/nullclaw/nullclaw/issues/967))
    - **严重程度**: 极高。该 Bug 导致核心 AI Agent 功能在超过半数的情况下完全无法使用，严重影响用户体验。
    - **复现环境**: Windows 11, NullClaw v2026.5.29, 模型 Agnes-2.0-Flash。
    - **状态**: 已报告，未确认，无修复 PR。

### 6. 功能请求与路线图信号
- 今日无明确的功能请求提交。`#967` 反映出用户对**Agent 响应稳定性**和**错误处理提示**有强烈的隐性需求。

### 7. 用户反馈摘要
- **用户痛点**: `#967` 报告者描述了Agent功能高概率失败的情况。用户等待27秒后只得到一个无意义的错误提示，体验极差。用户特别指出“同样的模型同样的apikey，我在picocla...”，这透露出**对竞品或替代方案稳定性更高的比较**，以及**对 NullClaw 该项目功能的明显不满和失望**。

### 8. 待处理积压
- **无**: 今日无长期未响应的 Issue 或 PR。但建议维护者优先关注并回应 `#967`，因该问题可能影响大量用户且复现率极高，若不及时处理，负面反馈可能积压。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，现根据您提供的IronClaw项目GitHub数据，为您呈上2026年6月21日的项目动态日报。

---

## IronClaw 项目日报 | 2026年6月21日

### 1. 今日速览

今日IronClaw项目**活动量极高**，核心贡献者推动了一系列关键功能的代码合并与迭代。虽然未发布新版本，但社区和团队通过21个Pull Request展现了强大的开发动力，特别是围绕“Reborn”运行时的重构和新的“清单驱动通道”架构取得了重大进展。与此同时，一个自动报告的Nightly E2E测试失败仍在待解决，但已有相关修复PR在并行推进。项目整体处于快速迭代、功能并发的活跃状态。

### 2. 版本发布

无

### 3. 项目进展

今日共有**9个PR被合并或关闭**，主要集中在以下方面，标志着项目在架构清晰度和功能完整性上迈出了坚实一步：

- **“Manifest-Driven Channels”核心架构落地**：核心成员`serrrfirat`合并了关于“清单驱动通道”的一系列PR，这是对项目扩展性的一次重大改造。
    - **PR #5103** 和 **PR #5104**：实现了将通道的入站策略（ingress policy）和认证（auth）从硬编码的Rust代码定义，转变为基于Manifest文件的声明式配置。这极大地简化了未来添加新通信渠道的流程。
    - **PR #5106**：作为该系列的“集大成者”，将之前针对Slack、Telegram等不同渠道的重复挂载逻辑，统一成一个通用的`serve`计划，大幅减少了代码冗余。
    - **PR #5102**：引入了跨合约的凭证一致性校验，确保不同部分对凭据的引用是安全且协调的。
    - **PR #5105**：修复了三个由于上述架构变更而导致的过时安全/认证测试，确保了代码库的健壮性。

- **清理和优化CI/CD流水线**：
    - **PR #4829**：删除了一个已停用的`reborn-integration`工作流，并将Reborn测试套件整合进Nightly深度CI中，简化了持续集成配置。
    - **PR #5086**（实验性）：关闭了一个探索性工作流，该工作流用于评估使用nextest、mold、sccache等工具加速全量测试套件的可行性。

- **Workspace实体与跨工作区共享功能**：**PR #2548**（由`standardtoaster`提交）在经过长期迭代后终于被合并。这是一个大型特性，实现了基于数据库的Workspace实体、成员管理和跨工作区资源共享，为多租户和企业级应用奠定了基础。

**项目向前迈进的程度**：核心团队迅速将“manifest-driven channels”从设计概念转化为落地代码，显著提升了项目的模块化和可扩展性。同时，长期积压的workspace功能合并，预示着产品在组织级协作能力上的重要升级。

### 4. 社区热点

今日社区讨论和关注焦点集中在每日CI自动化报告的稳定性问题上，以及核心贡献者提出的一系列架构性PR。

- **稳定性焦点**：
    - **[Issue #4108] Nightly E2E failed**: 由自动化机器人报告的最新Nightly端到端测试失败。虽然0评论，但它是当前直接影响项目质量信号的痛点。该问题由CI自动报告，未获得人工干预。

- **架构与开发焦点**：一系列由`serrrfirat`和`henrypark133`提交的大型PR（如#5107, #5085, #5087）评论数为undefined（可能为0或未公开），但它们代表了当前项目开发的核心方向。特别是 `serrrfirat` 的 PR #5107，它合并了之前几个堆叠的PR，提出了一个更大、更集成的“manifest-driven channel ingress contract”，显示出团队对架构重构的激进态度和决心。

**诉求分析**：社区的核心诉求（主要由核心贡献者驱动）是**构建一个更强大、可扩展且稳定的AI Agent运行时**。这体现在对性能（并发执行）、可靠性（OAuth令牌刷新）、功能完整性（一次性触发调度）以及架构优雅性（清单驱动）的追求上。

### 5. Bug 与稳定性

- **严重 - Nightly E2E测试失败**
    - **描述**：[Issue #4108](https://github.com/nearai/ironclaw/issues/4108) 报告Nightly E2E测试运行失败，影响项目核心功能的持续验证。
    - **严重程度**：高。E2E测试是软件质量的最后一道防线，持续失败会影响开发者信心和代码合并决策。
    - **状态**：未分配，0评论。目前尚无直接的修复PR链接于此Issue，但可以注意到PR #5086、#4829等都在优化CI流程，可能与解决此类问题间接相关。

- **低 - 修复过时的单元测试**
    - **描述**：PR #5105 修复了`main`分支上三个因重构而过时的安全/权限测试。这算是一种代码库回归（stale test），但已得到及时修复。

- **低 - 依赖更新**
    - **描述**：[PR #4002](https://github.com/nearai/ironclaw/pull/4002) 由dependabot发起，对GitHub Actions进行批量更新。由于是依赖更新，且已存在较长时间（5月24日），待合并，可能存在兼容性风险。

### 6. 功能请求与路线图信号

以下PR明确指向了未来版本的核心功能：

- **新功能：一次性调度触发器**：**PR #5065** (feat(triggers): one-shot scheduled triggers) 引入了`TriggerSchedule::Once {at}`，允许Agent在指定时间点执行一次任务。这弥补了仅支持Cron表达式的不足，极大拓展了定时任务的实用场景。
- **新功能：Manifest驱动通道**：**PR #5107** (manifest-driven channel ingress contract) 作为“Manifest-Driven Channels”的集大成者，将通道的入站策略、认证、传输和凭证集中管理。这可能会成为下一个版本的“杀手锏”特性，让第三方开发者通过manifest文件就能快速集成新平台。
- **新功能：Reborn学习系统**：**PR #4937** (reborn(learning): WS-1 memory learning semantics) 为Reborn运行时引入了“记忆学习”概念，允许Agent从错误中学习。这是迈向更智能、更自适应的Agent的关键一步。
- **新功能：并发Turn执行**：**PR #5085** (feat(reborn): concurrent turn execution) 打破了之前串行执行Turn的瓶颈，通过`TurnRunScheduler`实现并发执行并施加限制。这将显著提升Reborn运行时的吞吐量。
- **新功能：Google OAuth令牌自动刷新**：**PR #5087** (fix(reborn): proactively refresh Google OAuth tokens) 修复了令牌过期需要用户手动重连的问题，通过条件刷新机制提升了用户体验。

**路线图信号**：这些PR清晰地表明，项目团队正沿着大幅提升Reborn运行时**性能、智能性和集成能力**的路线图前进。下个版本很可能聚焦于“一次性触发器”和“Manifest驱动通道”。

### 7. 用户反馈摘要

今日数据中**没有来自真实用户的反馈或讨论**。所有提交的Issues和PR均来自核心团队成员或自动化机器人（如`github-actions[bot]`和`dependabot[bot]`）。这表明目前项目仍处于由核心开发团队主导的密集开发阶段，社区用户的参与度相对较低。

### 8. 待处理积压

以下是一些值得维护者关注的长期未响应Issue或PR：

- **Dependabot批量更新 [PR #4002]**：此PR已存在近一个月，涉及16个GitHub Actions包的更新。虽然影响范围广，但长期悬而未决可能导致项目CI环境与社区最佳实践脱节，也可能错失安全补丁。建议尽快进行审查和合并。
    - 链接：[PR #4002](https://github.com/nearai/ironclaw/pull/4002)

- **Nightly E2E测试持续失败 [Issue #4108]**：该Issue虽然是自动化报告，但E2E失败是项目健康度的红灯。它已被打开超过三周，至今无人分配或评论。建议安排专人跟进，确认这是由于随机Infra故障还是代码回归，并尽快修复。
    - 链接：[Issue #4108](https://github.com/nearai/ironclaw/issues/4108)

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

好的，这是为您生成的 LobsterAI 项目动态日报，日期为 2026-06-21。

---

# LobsterAI 项目动态日报 | 2026-06-21

## 1. 今日速览

过去24小时内，LobsterAI 项目活跃度较低。项目未发布新版本，也无新的 Issue 或 Pull Request 提交。项目团队主要在处理历史积压问题，关闭了5个因长期未活动而被标记为“stale”（过期）的 Issue。这表明项目当前处于维护和清理阶段，而非快速迭代期。核心开发工作或社区贡献活动暂时放缓。

## 2. 版本发布

无

## 3. 项目进展

今日无任何 Pull Request 被合并或关闭。项目整体状态保持稳定，未有新功能或修复被合入主分支。

## 4. 社区热点

今日无活跃讨论。以下为我们关注到的历史热点问题（已关闭）：

- **#1495 [CLOSED] [stale] 无缘无故中断进程**
  - **概述**：用户反馈在使用过程中频繁出现进程中断提示，询问是客户端还是大模型的问题。
  - **链接**: `netease-youdao/LobsterAI Issue #1495`
  - **分析**：该问题获得了1个“👍”，说明至少有一名其他用户也遇到了类似困扰。此问题涉及核心功能的稳定性，即使被关闭，仍值得开发团队关注是否有潜在的底层错误传播或客户端容错机制不足的问题。

## 5. Bug 与稳定性

今日无新增 Bug 报告。被关闭的5个Issue均为历史Bug，因长期无响应而被自动标记为“stale”并关闭。这些Bug 主要集中在**用户界面交互体验**和**任务执行稳定性**上：

- **严重（稳定性问题）**:
    - **#1495 [stale] 无缘无故中断进程**: 进程无故中断，严重影响用户体验。无关联修复PR。
- **中等（交互逻辑问题）**:
    - **#1468 [stale] 创建Agent弹窗关闭时无未保存确认**: 用户在重要表单填写内容后，关闭弹窗会导致数据丢失。
    - **#1469 [stale] Agent设置面板关闭时无未保存确认**: 修改Agent配置后，未保存直接关闭会导致修改丢失。
    - **#1470 [stale] MCP服务器配置弹窗关闭或按Escape时无未保存确认**: 填写敏感的API Key等环境变量后，未保存关闭会导致数据丢失。
    - **#1496 [stale] 任务显示完成，但是没有返回**: 任务状态显示完成，但实际结果未返回，属于任务生命周期管理的逻辑错误。

## 6. 功能请求与路线图信号

今日无新的功能请求提出。近期被关闭的Issue主要集中在修复现有Bug上，未反映出新的功能需求或路线图方向的调整。

## 7. 用户反馈摘要

从被关闭的Issue中，可以提炼出用户的核心痛点：

- **数据安全性担忧**：用户对于在关键操作（如创建Agent、配置服务器、修改设置）中因误操作导致数据丢失的体验非常不满。`MaoQianTu` 连续提交了 #1468、#1469、#1470 三个关于“未保存确认”的Issue，强烈反映了用户对“防误操作”机制的迫切需求。这是提升产品易用性和用户信心的关键改进点。
- **任务流程透明度不足**：`netease-george` 和 `xuzhiwu123` 反馈的任务“显示完成但无返回”或“无故中断”问题，表明用户对任务的执行状态和最终结果的预期出现了偏差。用户需要更清晰、准确的任务状态反馈机制，以及在任务失败时明确的错误原因提示。

## 8. 待处理积压

今日所有被关闭的Issue均为 `[stale]` 状态，意味着这些是对维护者长期未回应的问题进行的自动清理。随着这些积压问题被关闭，当前项目仓库处于“无长期未处理的重要公开Issue”状态。但建议项目维护者：

- **重新评估被关闭的Bug**：尤其是 #1495（进程中断）和 #1496（任务无返回），这些是影响核心功能的严重问题。建议规划在后续版本中修复，或至少给出用户明确的说明或临时解决方案。
- **考虑“未保存确认”功能**：尽管 #1468, #1469, #1470 已被关闭，但这代表了明确且合理的用户需求。建议将其作为提升 UI/UX 质量的任务单重新开启或纳入产品 backlog。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

好的，这是根据您提供的 Moltis 项目 GitHub 数据生成的 2026-06-21 项目动态日报。

---

## Moltis 项目日报 (2026-06-21)

### 1. 今日速览

今日项目状态**稳定**，社区活跃度较低。过去24小时内无新 Issue 提出，也无新版本发布。项目动态集中在依赖维护上，由机器人（Dependabot）提交并合并了两个关于 JavaScript 依赖更新的 PR，涉及 `astro` 和 `undici` 包。这表明项目正在进行例行的安全与兼容性维护，但未见核心功能开发或社区深度讨论。

### 2. 版本发布

无

### 3. 项目进展

今日项目主要完成了依赖层面的维护工作，具体进展如下：

- **PR #1133 (已合并/关闭)**：成功将 `/docs` 目录下的 `astro` 依赖从 `6.3.3` 更新至 `6.4.8`。该更新通常包含性能优化、小功能改进和 bug 修复，有助于提升项目文档构建的稳定性和速度。
- **PR #1134 (待合并)**：提出了一个更全面的依赖更新请求，计划在 `/docs` 和 `/website` 两个目录下分别更新 `astro` (至 `6.4.8`) 和 `undici`。该 PR 目前处于待合并状态，合并后将进一步确保项目在多个环境下的依赖安全性。

### 4. 社区热点

今日无引发社区讨论的热点 Issue 或 PR。所有活动均来自自动化机器人，无人参与评论或互动，表明社区当前处于平静观察期。

### 5. Bug 与稳定性

今日无新报告的 Bug。依赖更新类维护工作（PR #1133, #1134）本身就是预防性措施，旨在降低因依赖漏洞或版本过旧导致的潜在稳定性与安全性风险。

### 6. 功能请求与路线图信号

今日无新功能请求。无信号表明新功能将被纳入下一版本。

### 7. 用户反馈摘要

今日无用户反馈。

### 8. 待处理积压

- **[待合并] PR #1134**：一个由 Dependabot 提出的关于更新 `astro` 与 `undici` 依赖的合并请求。虽然风险较低，但长期搁置可能会使项目面临安全漏洞窗口。建议项目维护者尽快审核并合并。 [查看PR](https://github.com/moltis-org/moltis/pull/1134)

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，以下是基于您提供的 CoPaw 项目 GitHub 数据生成的 2026-06-21 项目动态日报。

---

## CoPaw 项目动态日报 | 2026-06-21

### 1. 今日速览

项目当日活跃度非常高，标志着从“功能密集添加期”过渡到“稳定性和质量打磨期”。**过去24小时内，社区提交了13个Issue和15个PR**，显示开发者与用户均积极参与。**重点关注领域集中在三个方向：** 一是 **稳定性与Bug修复**，占比最高，尤其围绕 DeepSeek 模型兼容性、连接错误和消息丢失问题；二是 **UI/UX 优化**，特别是移动端适配和侧边栏交互；三是 **核心功能增强**，如内存系统的时效性排名、KV缓存优化以及新的“滚动”上下文管理策略。尽管没有新版本发布，但 PR 合并节奏符合预期，为下一个版本的稳定迭代奠定了基础。

### 2. 版本发布

无

### 3. 项目进展

今日最重要的项目进展是 **“Langfuse 可观测性”改进项**被合并，以及多个影响用户核心体验的 PR 已提交，等待审核和合并。

- **已合并/关闭的 PR**:
    - [#5128 [CLOSED] group langfuse observations by agent loop](https://github.com/agentscope-ai/CoPaw/pull/5128)：**项目首次贡献者** totoyang 合并了该 PR。此改进将整个 Agent ReAct 循环的观测数据归入一个 Trace，极大提升了 Langfuse 可观测性的清晰度，解决了先前一次对话被拆分为多个孤立 Trace 的问题。
    - 同时，3个老旧的 Bug 或问题 Issue (#5208, #5250, #5343) 在今天被关闭，表明团队在同步清理积压问题。

- **等待合并的 14 个 PR** 中，已有多项功能修复接近完成，如下文所述。整体来看，项目在**修复兼容性、增强核心功能和优化用户界面**三个维度上均取得了实质性进展。

### 4. 社区热点

今日社区讨论的焦点集中在 **第三方模型兼容性** 和 **Agent 卡死/无响应** 两个核心痛点上。

- **最高热度 Issue**:
    - **#5345 [Bug]: Custom OpenAI-compatible providers (e.g. OMLX) don’t support function calling**：该 Issue 获得较多关注，因为它暴露了自定义 OpenAI 兼容提供商在 Function Calling 上的一个缺口。用户 `qiyuanlicn` 根据自身经验提出，项目原生支持的与自定义提供商的体验不一致，诉求非常具体，是潜在新用户和依赖第三方API的用户的重大障碍。
    - **#5328 [Bug]: 使用deepseek的过程中，agent经常在thinking的过程中卡死**：用户 `bob-geek11` 连续提交了多个与 DeepSeek 相关的卡死 Issue，这一系列问题获得了社区大量共鸣，表明 DeepSeek 模型的兼容性是目前影响用户体验的**首要问题**。
    - **#5329 [Enhancement]: 在左边的侧边栏进入简介模式后，添加一个切换agent的按钮**：用户 `bob-geek11` 的另一个高互动 Issue，反映了移动端 UI 的急切需求。评论中用户不仅提出了问题，还提供了详细的截图和初步解决方案，推动了前端优化方向。

### 5. Bug 与稳定性

今日报告的 Bug 集中爆发，但好消息是大部分已有关联的修复 PR。按严重程度排列如下：

- **严重：Agent 操作卡死/无响应**
    - **#5328**：使用 DeepSeek 时 Agent 在 `thinking` 过程中卡死。**已有修复 PR #5335**，该 PR 旨在确保后端错误不会导致前端 UI 永远卡在“等待”状态。
    - **#5333**：提交指令后 Agent 卡住，且文本框恢复可输入状态而非“停止”按钮（与 #5328 高度相关）。**已有修复 PR #5335**。
- **严重：消息静默丢失**
    - **#5344**：当 Agent 忙碌时，通过 API 发送的消息返回200成功但被静默丢弃。**已被标记为 Bug**，但暂无对应PR，这对自动化工作流是致命缺陷。
- **中高：集成兼容性问题**
    - **#5345**：自定义 OpenAI 兼容提供商（如 OMLX）不支持 Function Calling。**暂无对应PR**，但被标记为 Bug。
    - **#5330**：Zhipu 供应商 API 连接测试成功，但模型级连接测试全部失败。**已有修复 PR #5339**，该 PR 修正了 `check_model_connection` 方法发送的内容格式。
- **中：特定场景下的崩溃/性能问题**
    - **#5342**：当 LLM 调用失败（如502错误）时，`post_acting` 的截断机制失效，导致工具结果上下文爆炸。**暂无对应PR**，但已被标记为 Feature Request，其防御性设计值得关注。

### 6. 功能请求与路线图信号

用户在新 Issue 中提出了多个有价值的功能请求，结合已有 PR 来看，**内存系统重构**和**实时推送**将是下一版本的核心亮点。

- **“接近确定”进入下一版本的功能**:
    - **实时推送 & 语音通知**：用户 `xyxy` 在 **#5322** 中提出 API 消息无法实时更新 UI 的痛点。**已有 PR #5331** 为其实现了 SSE 推送和语音提示功能，很可能在下一个版本中上线。
    - **Sidebar 移动端优化**：用户 `bob-geek11` 提出的 **#5329** 已有 **PR #5334** 实现。该 PR 使侧边栏在收起状态下也能切换 Agent，解决了移动端核心痛点。
    - **内存检索时效性优化**：用户 `hellozhouuu` 提出的 **#5316** 已有 **PR #5325** 实现，增加了对每日记忆的可选时效性排序。
- **“可能纳入”的功能信号**:
    - **智能体办公室交互增强**：用户 `q1264703873` 在 **#5327** 中提出在智能体办公室页面直接发起对话和切换 session。这符合项目为用户提供更丰富交互形态的路线图，可能与即将推出的多智能体功能协同。
    - **KV Cache 优化**：**PR #5348** 提出冻结会话内的环境上下文日期，以保持 KV Cache 前缀一致，这是性能优化的一个关键方向，如果合并，将显著降低跨日对话的计算开销。

### 7. 用户反馈摘要

从 Issue 评论和描述中，我们可以提炼出当前用户的真实声音：

- **核心痛点：“卡死”与“失联”**
    - **用户 `bob-geek11` (多次提交)**：作为重度用户，他极为沮丧地描述了 DeepSeek 模型在不同客户端（Web、Console、Tauri）上反复出现的卡死问题。他的描述“agent就卡着不动”、“文本框又是可提交新指令的状态”精准地指向了 UI 状态管理的 Bug，这严重影响了他的工作流和对产品的信任。
- **对“隐藏”功能丢失的困扰**
    - **用户 `xyxy`**：作为 API 使用者，他遇到了消息被静默丢弃的问题（#5344）。他使用了“silently discarded”一词，这比一个清晰的错误更让人不安，因为用户无法得知问题所在。这反映出对 API 健壮性和透明性的高要求。
- **对“不公平”体验的质疑**
    - **用户 `qiyuanlicn`**：在 #5345 中，他对比了 Ollama（原生支持）与自定义提供商（OMLX）在 Function Calling 上的差异。他期望“自定义 OpenAI 兼容提供商也能完整支持 function calling”，这反映了社区对**开放、平等、无差别对待第三方服务**的普遍期望。
- **积极的参与与求助**
    - **用户 `hyper0x`**：在 #5330 中，他详细描述了 Zhipu 供应商的配置故障，并主动指出“供应商级别的 API 连接测试通过，但模型级别的连接测试全部失败”，这表明用户不仅是在报告问题，更是在帮助团队进行技术排查，体现了社区的高质量和参与度。

### 8. 待处理积压

- **开放性高、需维护者回应的 Bug**:
    - **#5344 [Bug]: /api/console/chat returns 200 but silently drops messages when agent is busy**：这是影响 API 集成可靠性的严重 Bug，已有完整的复现步骤，但尚未有任何 PR 或维护者的分配标记。建议 **优先处理**。
    - **#5345 [Bug]: Custom OpenAI-compatible providers... don’t support function calling**：直接阻碍了部分用户使用自有模型服务的能力，潜在影响面广。
- **长期未解决的核心问题**:
    - **DeepSeek 相关问题簇 (#5328, #5333)**：虽然 PR #5335 尝试修复 UI 卡死，但根本原因可能仍在后端模型调用的互操作性上。建议维护者在合并 #5335 后，追踪这些 Issue，确认卡死问题是否完全解决。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，我将根据您提供的 ZeroClaw 项目数据，生成一份结构清晰的 2026-06-21 项目动态日报。

---

# ZeroClaw 项目动态日报 | 2026-06-21

## 1. 今日速览

ZeroClaw 项目今日保持**极高活跃度**。过去 24 小时内，共产生 50 条 Issue 和 50 条 PR 更新，表明开发与社区互动均非常密集。尽管无新版本发布，但项目在 **v0.9.0 里程碑**（安全、认证、网关重构）和 **v0.8.2 技能平台** 上均有显著推进，多项关键的 Bug 修复和功能 PR 正在审查或等待合并（待合并 PR 达 47 个）。社区反馈主要集中在系统提示、上下文窗口管理、渠道功能性及技能查找等实际使用痛点，反映出用户正在深度使用并积极向更稳定、更智能的方向反馈。

## 2. 版本发布

今日无新版本发布。

## 3. 项目进展

今日虽无 PR 被合并，但活跃的 PR 池展示了项目在重要领域的进展。关键的 PR 包括：

-   **核心机制修复**：
    - `#8053` [fix(runtime): present native/MCP tools to reasoning models] - 修复了系统提示中未向推理模型呈递原生工具的问题，这对使用支持工具调用的高级模型至关重要。
    - `#8081` [fix(tools): ReadSkillTool uses agent workspace] - 针对 `#8047` Bug（技能文件查找路径错误）的修复 PR，确保技能读取路径正确。
    - `#8048` [fix(runtime): keep tool-result content under context pressure] - 修复在上下文压力下错误地截断工具结果的问题，并开始尊重 `history_pruning` 用户配置。

-   **功能与体验增强**：
    - `#8033` [feat(onboard): chat-based conversational setup assistant] - 一个大体量 PR，旨在复活并重新设计 `zeroclaw onboard` 命令，为用户提供对话式引导设置体验，对降低新用户门槛意义重大。
    - `#8006` [feat(zerocode): add Aliases/Costs tabs] - 将 Web 网关的别名/费用标签页功能同步到 TUI 界面，提升了用户对 Provider 的直观管理能力。
    - `#7945` [feat(auth): add xAI OAuth login support] - 一个 XL 尺寸的 PR，目标是增加 xAI/Grok 的 OAuth 登录，简化用户认证流程。

**项目向前迈进程度**：项目正处于功能迭代和稳定性加固并行的关键时期。多个“高风险”和“高严重性” Bug 被标记并有相应的修复 PR 提出，同时新功能（如 OAuth 支持、对话式引导）的落地也标志着项目正在向更成熟、更用户友好的方向演进。

## 4. 社区热点

今日最受关注的问题主要集中在“系统智能”与“基础功能缺陷”的矛盾上：

1.  **#5849 [Feature]: Dream Mode — Periodic Memory Consolidation & Reflective Learning** (评论: 18)
    -   **链接**: [Issue #5849](https://github.com/zeroclaw-labs/zeroclaw/issues/5849)
    -   **分析**: 该 Feature 请求热度极高，社区希望 ZeroClaw 能在空闲时像人类一样“做梦”，对记忆进行整合和反思，以提升长期学习能力。这反映了用户对 AI Agent 超越简单检索、具备自主学习和持续进化能力的强烈期待。

2.  **#5862 [Bug]: zeroclaw does not know it can add cron.** (评论: 13)
    -   **链接**: [Issue #5862](https://github.com/zeroclaw-labs/zeroclaw/issues/5862)
    -   **分析**: 这是一个非常基础但令人困惑的 Bug：Agent 本身不知道自己拥有 `zeroclaw cron` 功能。这表明系统提示或工具注册机制存在缺陷，限制了 Agent 的自我意识与利用自身核心功能的能力。这引发了社区对 Agent 自我认知和工具编排机制的讨论。

3.  **#6808 [RFC]: Work Lanes, Board Automation, and Label Cleanup** (评论: 11)
    -   **链接**: [Issue #6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808)
    -   **分析**: 这是一个关于项目治理的 RFC（技术提案）。社区非常积极地参与讨论如何优化工作流、自动化看板以及清理标签。这表明项目社区的参与者不仅仅是用户，还有很多深度参与项目治理的贡献者，展现了极高的社区成熟度。

## 5. Bug 与稳定性

今日报告的 Bug 主要集中在运行时稳定性、工具使用和配置正确性上。按严重程度排列如下：

-   **S0 - 数据丢失/安全风险**:
    -   `#6672` [Bug]: reasoning_content not passed back in agentic tool-call loops with Xiaomi thinking mode models (已关闭但曾为S0)。**状态**: 已标记为 blocked，待作者回应。
    -   `#6558` [Bug]: providers erro。**状态**: blocked，待作者回应。

-   **S1 - 工作流阻塞**:
    -   **`#8047` [Bug]: ReadSkillTool looks in `data_dir` but skills live in agent workspace** (S2，但影响核心功能). 有对应修复 PR `#8081`。**状态**: 新Issue，已有PR。
    -   `#5808` [Bug]: Default 32k context budget is exceeded by system prompt... (S1) **状态**: in-progress。
    -   `#6037` [Bug] Cron jobs can be launched repeatedly while still running (S1) **状态**: accepted。

-   **S2 - 行为降级**:
    -   `#5844` [Bug]: Too much emphasis on memory (S2) **状态**: accepted。
    -   `#6517` [Bug]: Context Overflow Causes Hallucination / Topic Drift (S2) **状态**: blocked，待作者回应。

-   **其他**:
    -   `#8051` [Bug]: suppressing bound channels when their owning agent is disabled (新Bug) **状态**: 已有修复PR `#8051`。
    -   `#8075` [Bug]: Keybinds vs. OS globals (zerocode) （新Bug）**状态**: 开放讨论。

**总结**: 上下文窗口管理、Cron 任务并发控制以及技能/工具路径查找是目前影响稳定性的主要问题，幸运的是核心问题均有对应的修复或解决方案在推进。

## 6. 功能请求与路线图信号

以下功能请求信号强烈，很可能被纳入后续版本：

-   **认证与安全 (v0.9.0 路线图核心)**:
    -   `#7141` [Feature]: OIDC Authentication Provider support. **信号**: 非常强烈。项目已设立专门的 tracker issue (`#7432`)，且有子任务 issue (`#8076`) 被创建，表明该功能正在稳步推进。
    -   `#8076` [Feature]: local username/password AuthProvider. **信号**: 强烈。作为 OIDC 的补充，满足无 IdP 场景的需求，属于 `#7141` 的子集。

-   **用户体验与交互**: `#7531` [Feature]: Support streaming card messages for QQ/DingTalk/WeChat/Feishu. **信号**: 较强。响应了多平台用户的等待焦虑问题，表明项目正在努力提升交互体验。

-   **开发协作**: `#8078` [RFC]: zerocode local pre-submission gate. **信号**: 极强，刚创建的新 RFC。这是一个开发规范类功能，旨在通过本地预检查来保证代码质量，反映了项目对贡献质量的重视，可能成为 Zerocode 的一个差异化特性。

-   **已接受的长期功能**: `#5849` [Feature]: Dream Mode. **信号**: 强。尽管是 4 月提出的，但已被标记为 `status:accepted` 且今日仍有讨论，是社区最期待的高级功能之一。预计会在主要稳定性和认证目标完成后再重点推进。

## 7. 用户反馈摘要

从今日的 Issues 和 PR 评论中，提炼出以下真实用户痛点与场景：

-   **“Agent 不够智能”**:
    -   **痛点**: Agent 过度依赖记忆而忽略当前对话上下文 (`#5844`)，导致在 Cron 任务等场景下表现不佳。
    -   **场景**: 用户希望 Agent 能更灵活地调度自身功能，而不是只会机械执行。例如，用户认为“添加定时任务”是常识，但 Agent 却不知道如何做 (`#5862`)。

-   **“稳定性和可靠性差”**:
    -   **痛点**: 上下文窗口溢出导致幻觉/话题漂移 (`#6517`)；Cron 任务会重复执行 (`#6037`)；服务因未知配置问题启动失败 (`#5883`, `#6558`)。
    -   **场景**: 用户在长时间对话中体验到 AI 性能下降，在自动化任务中遇到意外重复，在初始设置阶段就遭遇困难。

-   **“文档和功能不匹配”**:
    -   **痛点**: Agent 无法回答关于自身功能和配置的问题，用户认为应该将文档集成到 Docker 镜像中 (`#7950`)。
    -   **场景**: 用户在配置和使用过程中遇到问题，曾尝试向 Agent 本身询问，但未能得到有效回答。

-   **“特定渠道/模型问题”**:
    -   **痛点**: 小米思考模型在 Agent 循环中不传递推理内容 (`#6672`)；QQ 频道的特定命令在文档中没有提及 (`#5686`)。
    -   **场景**: 用户依赖特定模型或渠道进行生产工作，但这些场景下的 Bug 严重影响了他们使用 ZeroClaw 的信心。

## 8. 待处理积压

以下问题已长时间处于“等待作者回应”或“无法复现”状态，建议维护者关注并推动解决：

-   **`#6672`** [Bug]: reasoning_content not passed back... (S0) - **状态**: `needs-author-action`, `stale-candidate`。 *严重风险，若作者无回应应考虑接管。*
-   **`#6517`** [Bug]: Context Overflow Causes Hallucination... (S2) - **状态**: `needs-author-action`, `stale-candidate`。 *影响用户核心体验。*
-   **`#6558`** [Bug]: providers erro - **状态**: `needs-author-action`, `stale-candidate`。 *S0 风险的 Bug。*
-   **`#5883`** [Bug]: zeroclaw service start fails (已关闭) - **建议**: 尽管已关闭，但该问题影响 macOS 用户，应确认修复是否有效或是否有更好的文档指导。
-   **`#6243`** [Bug]: Streaming error: error decoding response body provider (已关闭) - **建议**: 同样建议确认修复。流式解码错误是常见的棘手问题，值得持续关注。

**维护者行动建议**:
1.  对 `#6672`, `#6517`, `#6558` 等标记为 `stale-candidate` 且影响严重的问题进行最后确认，如仍无法获得作者回应，应主动介入处理或关闭。
2.  全力推动 `v0.9.0` 和 `v0.8.2` 里程碑相关的 PR 合并，特别是 `#8053`, `#8048`, `#8033` 等关键修复和功能，以稳定社区信心。

</details>

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*