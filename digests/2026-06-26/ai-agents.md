# OpenClaw 生态日报 2026-06-26

> Issues: 500 | PRs: 500 | 覆盖项目: 13 个 | 生成时间: 2026-06-26 03:37 UTC

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

好的，作为 AI 智能体与个人 AI 助手领域的开源项目分析师，我将根据您提供的 OpenClaw 项目 GitHub 数据，为您生成一份结构清晰、数据驱动的项目动态日报。

---

# OpenClaw 项目动态日报 | 2026-06-26

## 📊 今日速览

过去24小时内，OpenClaw 项目保持**极高**的活跃度。项目同时有 **500 条 Issue** 和 **500 条 PR** 产生动态，显示出庞大的社区参与度和激烈的开发进程。尽管没有新的版本发布，但大量待处理的 PR (411 条待合并) 表明核心开发团队有大量的工作正在审查和排队中。当前项目的核心关注点集中在 **会话状态管理**、**消息投递可靠性** 以及 **安全性** 上。多起高优先级的 Bug 报告围绕会话上下文膨胀、子代理交付丢失及网关内存泄露等稳定性问题，表明项目正处于一个关键的稳定性和可靠性打磨阶段。

## 🚀 最新版本发布
*（无更新）*

---

## ✅ 项目进展（已合并/关闭的重要 PR）

过去24小时内，共 **89 条 PR** 被合并或关闭。其中，以下几条 PR 对项目推进具有显著意义：

- **[#68936] Autofix: add PR review autofix pipeline + Windows daemon** (已关闭)
    - **摘要**：合并了一个自动化 PR 审查修复流水线，能够根据审查意见自动生成修复代码。同时，增加了一个 Windows 后台守护进程，用于管理该流水线和 OpenClaw 网关。
    - **重要性**：显著提升了开发和代码审查的效率，并为 Windows 平台的用户提供了更好的后台运行体验。这是一个重要的基础设施改进。

- **[#96913] fix(ollama): preserve tool_calls.arguments as JSON string** (已关闭)
    - **摘要**：修复了 Ollama 模型在多轮工具调用时因参数序列化方式不符合 OpenAI API 规范而失败的问题。
    - **重要性**：保证了对 Ollama 生态系统的兼容性，这是 OpenClaw 支持的关键本地或云模型之一。

- **[#96914] fix(secrets): avoid exec target gateway failures** (已关闭)
    - **摘要**：修复了在解析 Secret 时因目标集包含未实例化的 SecretRef 而导致网关生成大量噪音错误的问题。
    - **重要性**：提升了网关的稳定性和日志的可用性，避免了不必要的运行痛苦。

**总结**：项目在本日主要推进了**自动化工具链**、**模型（Ollama）兼容性**和**核心稳定性（密钥管理）** 三大方面。

---

## 🔥 社区热点

1. **[Issue #63918] Cron agentTurn sends thinking=none to OpenAI** (评论: 17)
    - **标签**: `P2`, `impact:auth-provider`
    - **链接**: `openclaw/openclaw Issue #63918`
    - **分析**: 这是过去24小时内讨论最激烈的 Issue。问题在于由 Cron 作业触发的 `agentTurn` 会发送不被 OpenAI 模型（如 `gpt-5-nano`）支持的 `thinking` 参数值。用户对Cron任务与特定模型的不兼容问题表现出高度关注，期待快速修复。

2. **[Issue #68596] Feature Request: Configurable streaming watchdog timeout** (评论: 15, 👍: 8)
    - **标签**: `P2`, `impact:session-state`
    - **链接**: `openclaw/openclaw Issue #68596`
    - **分析**: 社区呼声最高的功能请求。用户在使用长推理模型（如 DeepSeek-R1）时，频繁触发默认30秒的流式看门狗超时警告。这表明用户对**长上下文/长思考模型**的支持有迫切需求，希望提供一个可配置的阈值以避免误报。

3. **[Issue #58450] Agent can promise a later follow-up without starting any action** (评论: 15)
    - **标签**: `P2`, `impact:message-loss`
    - **链接**: `openclaw/openclaw Issue #58450`
    - **分析**: 这是一个关于**会话完整性和用户信任**的痛点问题。Agent 在任务结束时会空口承诺会跟进，但实际上并未启动任何后台任务或工具调用。用户因此会对 Agent 产生不切实际的期望，最终导致失望。这被认为是消息丢失的一种表现形式。

---

## 🐛 Bug 与稳定性问题（按严重程度排列）

以下为过去24小时内值得关注的高优先级 Bug，多数可能由 `clawsweeper` 自动化工具标记或总结：

1.  **P1 | 会话/消息丢失**
    - **[Issue #69208] Umbrella: duplicate transcript ... across channels**
        - **标签**: `impact:session-state`, `impact:message-loss`
        - **链接**: `openclaw/openclaw Issue #69208`
        - **描述**: 这是一个跨渠道（MSTeams, webchat, Telegram等）的伞状问题，涉及重复转录、回放和上下文组装。表明会话管理问题可能是系统性的。

    - **[Issue #67777] Subagent completion delivery can be lost**
        - **标签**: `impact:session-state`, `impact:message-loss`
        - **链接**: `openclaw/openclaw Issue #67777`
        - **描述**: 子Agent的完成交付可能因直接通知超时、排空或孤儿删除而丢失，导致任务结果无法传回主Agent。**已有 Fix PR 等待合并**。

    - **[Issue #63216] Repeated hard resets ... retry loop re-injects bootstrap context**
        - **标签**: `impact:session-state`, `impact:message-loss`
        - **链接**: `openclaw/openclaw Issue #63216`
        - **描述**: 即使配置了高保留代币阈值，特定会话仍会反复触发硬上下文溢出重置，导致启动上下文被重复注入，形成恶性循环。

    - **[Issue #54531] Force reply to originating channel** (`P1`)
        - **标签**: `impact:message-loss`, `impact:security`
        - **链接**: `openclaw/openclaw Issue #54531`
        - **描述**: Agent 生成回复后无法将消息发回原始渠道（Telegram/Discord等），用户只能在网关UI中看到回复，移动端收不到。这严重影响了多端体验。

    - **[Issue #53540] "Network connection lost" when LLM generates a tool call with large parameters**
        - **标签**: `impact:message-loss`
        - **链接**: `openclaw/openclaw Issue #53540`
        - **描述**: 当LLM生成带有大参数的Tool Call时，参数生成延迟超过底层请求超时，导致嵌入式运行器报“网络连接丢失”错误。

2.  **P1 | 安全漏洞**
    - **[Issue #57326] CLI-backed helper paths still bypass CLI dispatch**
        - **标签**: `impact:security`
        - **链接**: `openclaw/openclaw Issue #57326`
        - **描述**: 部分助手路径仍然绕过 CLI 调度，直接使用嵌入/API路径来处理本应由 CLI 后端处理的任务，这可能导致安全策略绕过。

3.  **P1 | 性能/稳定性**
    - **[Issue #54155] Gateway memory leak: 389MB → 14.7GB over 4 days**
        - **标签**: `impact:crash-loop`
        - **链接**: `openclaw/openclaw Issue #54155`
        - **描述**: 网关进程存在严重内存泄漏，持续运行4天后内存占用可从389MB膨胀至14.7GB，最终导致OOM。这是一个严重影响服务器稳定性的问题。

    - **[Issue #55334] sessions.json unbounded growth causes gateway OOM**
        - **标签**: `impact:crash-loop`
        - **链接**: `openclaw/openclaw Issue #55334`
        - **描述**: `sessions.json` 文件因包含重复的 `skillsSnapshot` 且未清理临时会话而无限增长，最终导致网关 OOM。与 `#54155` 同属内存管理问题。

4.  **P1 | 回归**
    - **[Issue #53599] Chrome extension browser relay removed**
        - **标签**: `impact:security`
        - **链接**: `openclaw/openclaw Issue #53599`
        - **描述**: 此前的版本移除了Chrome扩展中继和WebSocket服务器，而替代方案仅支持本地主机，导致依赖跨机器浏览器控制的托管供应商受到影响。

---

## 💡 功能请求与路线图信号

过去24小时内用户提出的新功能需求中，以下信号反映了社区对项目的普遍期待：

1.  **更强的安全性与隐私性**
    - **[Issue #64046] 支持敏感数据脱敏**：用户强烈要求对配置文件、日志和UI中的API Key、Token等敏感信息进行脱敏处理，当前明文存储风险较高。
    - **[Issue #56349] Unbypassable outbound policy enforcement**：需要一个**强制执行**的出站消息策略门禁，以确保所有对外发送的消息都经过合规性检查，避免通过不同路径绕过。

2.  **Agent 能力与生态扩展**
    - **[Issue #63930] Support Anthropic advisor tool**：支持 Anotropic 的 Beta 版 `advisor tool`（服务端工具），允许 Claude 在推理过程中咨询另一个模型。
    - **[Issue #66252] Per-Agent TTS/STT Configuration Overrides**：支持为不同 Agent 设置独立的语音（TTS）和语音识别（STT）配置，实现多语言/多角色支持。
    - **[Issue #63990] Multi-index embedding memory**：支持多个向量索引，允许在多个嵌入模型之间进行故障切换，避免因单一模型问题导致记忆搜索失效。

3.  **稳定性与诊断能力**
    - **[Issue #58818] guarantee last N raw messages in agent context**：保证在上下文压缩或会话重置后，Agent 仍能看到最近的 N 条原始消息，解决长对话中历史信息丢失的问题。
    - **[Issue #54373] Context Provenance**：为用户注入的上下文添加来源和易变性元数据，使 Agent 能区分“会话启动时的固定知识”和“当前轮次读取的新信息”。

---

## 💬 用户反馈摘要

从过去24小时的高互动 Issue 中，可提炼出以下核心用户反馈：

- **对长推理模型支持不满**：用户 `Yaemikoreal` 明确指出，默认的30秒流式超时对于 `kimi-k2.5` 和 `DeepSeek-R1` 等模型来说太短，导致频繁误报，影响使用体验。
- **对消息投递可靠性焦虑**：多位用户（`al-osokin`， `jackiedepp`， `downwind7clawd-ctrl`）报告了 Agent “说一套做一套”或消息凭空消失的问题，特别是在 Telegram 等渠道。这表明消息投递管道（尤其是异步场景下）存在严重的可靠性瓶颈。
- **对会话状态管理感到困惑**：会话的硬重置、上下文丢失、重复注入等问题让用户感到沮丧，尤其是在长对话中。有用户表示即使调高了 `reserveTokensFloor`（如 `sisutuulenisa`），也未能避免频繁重置，说明问题的根因可能不仅仅是代币预算。
- **对 Plugin/Skill 生态体验不佳**：`ocdlmv1` 在 Issue #50090 中详细阐述了社区技能开发（ClawHub）的现状，指出“承诺与现实之间存在巨大鸿沟”，开发者发现工具（Driftnet）已过时，文档不清晰，导致难以验证和构建高质量技能。

---

## 📋 待处理积压

以下为长期未响应的、可能被维护者忽略的重要 Issue 或 PR：

1.  **[Issue #50090] Community Skill Development & ClawHub**
    - **标签**: `P2`, `impact:security`
    - **链接**: `openclaw/openclaw Issue #50090`
    - **状态**: 创建于3月19日，仍在讨论，无具体进展。这是一个关于生态系统的核心问题，如果不解决，将严重影响社区贡献者的积极性。

2.  **[Issue #51429] 工作路径hardcode问题**
    - **标签**: `P2`, `impact:session-state`
    - **链接**: `openclaw/openclaw Issue #51429`
    - **状态**: 创建于3月21日。报告称代码中存在硬编码的 `/Users/wangtao` 路径并被合并发布，导致所有用户的工作目录被错误设置。3个月未解决，有核心代码质量问题嫌疑。

3.  **[PR #72510] fix(group-chat): wire multi-agent bot-targeting signals end-to-end**
    - **标签**: `P2`, `status: needs proof`
    - **链接**: `openclaw/openclaw PR #72510`
    - **状态**: 创建于4月27日。该 PR 旨在解决多 Agent 群聊场景下 Agent 无法识别消息是针对自己还是其他机器人的问题。这是一个重要的社交场景功能，但已积压两个月。

---

## 横向生态对比

好的，作为AI智能体与个人AI助手领域开源项目分析师，我将基于您提供的各项目动态，为您生成一份横向对比分析报告。

---

## 开源AI智能体生态横向对比分析报告 | 2026-06-26

### 1. 生态全景总览

当前，个人AI助手与自主智能体开源生态呈现出**高度活跃、分化加剧、聚焦稳定与安全**的总体态势。一方面，以OpenClaw为核心巨擘的社区，其讨论热度与代码量均达到峰值，项目正从功能扩张期艰难地向稳定期过渡，重度用户开始抱怨会话管理、消息投递等核心架构的可靠性问题。另一方面，NanoBot与ZeroClaw等后起之秀通过快速响应安全漏洞和探讨下一代架构（如Wasm），在各自细分领域构建了差异化的社区信任。整体来看，生态从拼功能、拼集成转向了**拼稳定性、拼安全、拼开发者体验**的深水区竞争。

### 2. 各项目活跃度对比

| 项目 | Issues 总数 | PR 总数 | 发布/版本 | 健康度评估 |
| :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 500+ | 500+ | 无 | **高活跃，但承压**：社区讨论爆炸，但大量积压（411 PR待合并）和高P Bug（内存泄漏、消息丢失）表明处于痛苦的转型期。 |
| **NanoBot** | 12 | 15 | 无 | **高活跃，聚焦安全**：因安全研究员集中报告漏洞，处理效率极高（同日修复），表明项目安全响应机制成熟。同时功能开发并行。 |
| **Hermes Agent** | 50 | 50 | 无 | **高活跃，Bug修复井喷**：报告了多个P0/P1级严重Bug（会话状态、内存泄漏），但社区有对口修复PR，展示出强大的自救能力。 |
| **PicoClaw** | 2 | 19 | 无 | **中等活跃，稳健迭代**：虽数据量小，但Bug修复与合并效率高（6/19个PR被合并），项目维护节奏健康，无积压严重问题。 |
| **NanoClaw** | 1 | 16 | 无 | **高活跃，功能交付期**：PR合并率高（11/16），大量新功能（容器资源、认证容灾）集中落地，进入重要的功能释放阶段。 |
| **IronClaw** | 50+ | 50+ | 无 | **极高活跃，基建夯实期**：大量Issues和PR专注于Reborn WebUI修复和底层能力（CAS锁、Trace Commons）构建，是生态中企业级能力最强的项目之一。 |
| **LobsterAI** | 1 | 8 | 无 | **中等活跃，深度协作优化**：团队集中合并8个PR，聚焦于Cowork模式和OpenClaw插件系统，显示出专注打磨核心协作体验的决心。 |
| **CoPaw** | 25 | 50+ | 无 | **高活跃，模型兼容性攻坚**：大量PR围绕修复特定模型（GLM、MiniMax）的兼容性问题与遗留Bug，模型适配是其核心竞争力。 |
| **ZeroClaw** | 38 | 50+ | `v0.8.2` **准备中** | **极高活跃，治理与架构变革期**：社区讨论集中在供应链安全、Wasm插件、看板治理等RFC，预示即将迎来重大架构更新。 |
| **其他** | *NullClaw, TinyClaw, Moltis, ZeptoClaw 无活动* | *-* | *-* | **低活跃**：表明部分项目可能处于停滞或维护阶段，生态资源有向头部集中的趋势。 |

### 3. OpenClaw 在生态中的定位

- **核心地位与规模优势**：OpenClaw拥有**绝对领先**的社区规模（500+ Issues/PRs），是市场的“参照物”和“基础设施”。其他项目（如LobsterAI、CoPaw）的部分功能明确围绕OpenClaw兼容性进行修复，证明了其生态中心地位。
- **技术路线差异**：与其他项目相比，OpenClaw采用**高度组件化、功能模块化**的架构，允许用户深度定制。但这带来了更复杂的配置与状态管理难题（会话丢失、消息投递可靠性）。相比之下，Hermes更专注于平台化体验（Dashboard），NanoBot则强调服务器插件生态（MCP）。
- **活跃度对比**：OpenClaw的活跃度无人能及，但这既是优势也是劣势。其焦点分散在数百个不同的Bug和功能请求上（如Cron任务、长模型支持），而NanoBot能在一天内集中处理同类安全漏洞，表明其社区焦点更集中，决策链条更短。
- **社区健康度**：OpenClaw面临着社区贡献者参与度（如积压的多项影响体验的P2级别Issue长期未解决）与项目维护成本（411条待合并PR）之间的平衡问题，这也是大型明星项目普遍面临的挑战。

### 4. 共同关注的技术方向

以下为多个项目中涌现出的共性需求，构成了当前生态的技术发展主线：

- **会话状态管理与消息可靠性**：
    - **涉及项目**: **OpenClaw**, **Hermes Agent**, **ZeroClaw**, **LobsterAI**。
    - **具体诉求**: 解决会话上下文膨胀、子Agent交付丢失、消息重复或丢失、会话状态同步错误、跨渠道消息路由等问题。这是所有面向重度用户的智能体平台面临的**首要共性瓶颈**。

- **工具/工具链安全与权限管理**：
    - **涉及项目**: **NanoBot**, **OpenClaw**, **Hermes Agent**, **ZeroClaw**。
    - **具体诉求**: 1) **白名单绕过防护**（如NanoBot的exec、MCP白名单绕过）；2) **权限持久化存储**（如IronClaw的“Always allow”不生效）；3) **精细化策略控制**（如ZeroClaw的“delegate绕过白名单”问题）。安全从“功能”变成了“默认组件”。

- **模型兼容性与长推理支持**：
    - **涉及项目**: **OpenClaw**, **CoPaw**, **ZeroClaw**。
    - **具体诉求**: 支持更丰富的模型提供商（Gemini、Groq、月之暗面），特别是解决 **长推理链/长上下文的兼容性问题**（如OpenClaw的流式超时配置，CoPaw的ToolCall参数序列化）。这是满足用户对“更强大模型”期望的技术前提。

- **开发者体验（API/文档/插件系统）与生态扩展**：
    - **涉及项目**: **OpenClaw**, **PicoClaw**, **CoPaw**, **ZeroClaw**。
    - **具体诉求**: 更清晰的贡献指南（ZeroClaw的RFC）、更易用的插件开发工具（OpenClaw的ClawHub困难、CoPaw的DataPaw插件）、更好的接口稳定性（Hermes Dashboard的回归Bug）。**从“能扩展”向“好扩展”转变**。

### 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
| :--- | :--- | :--- | :--- |
| **OpenClaw** | 通用AI智能体底座，高度可定制 | **高级开发者/系统集成商** | 微服务化、组件化、功能丰富，但复杂度高 |
| **NanoBot** | 安全第一，轻量级服务器插件 | **安全敏感型开发者** | 基于MCP插件体系，安全审计严格，Bug修复快 |
| **Hermes Agent** | 企业级平台，集成体验 | **团队/企业用户** | 强平台（Dashboard），多渠道接入，状态管理比OpenClaw更统一 |
| **PicoClaw** | 极致轻量级，嵌入式/边缘部署 | **硬件玩家/物联网** | 代码体积极小，资源占用低，维护者响应速度较快 |
| **NanoClaw** | 功能丰富，快速迭代 | **追求前沿功能的开发者** | 架构简洁，功能落地快（/learn, 认证容灾），但稳定性偶有波动 |
| **IronClaw** | 企业级治理，能力策略 | **大型组织** | 侧重权限控制、审批流，基础设施（Trace Commons、CAS锁）强大 |
| **LobsterAI** | 协作AI（Cowork模式） | **需要多智能体协作的团队** | 深度打磨plan模式、子代理协作，聚焦“人+AI”协同 |
| **CoPaw** | 模型兼容性之王 | **使用非主流模型的用户** | 测试覆盖度高，修复大量边缘模型（GLM, MiniMax）的问题 |
| **ZeroClaw** | 下一代架构实验场 | **架构创新者/贡献者** | Wasm-first、供应链安全、Rust重构，走在技术探索前沿 |

### 6. 社区热度与成熟度分层

- **第一梯队（快速迭代/质量问题并存）**:
    - **OpenClaw**, **IronClaw**, **ZeroClaw**。
    - **特征**: 社区规模最大，话题最多，但同时暴露出最多的稳定性（Bug报告）和治理（长积压）问题。

- **第二梯队（功能落地/质量巩固过渡）**:
    - **NanoBot**, **Hermes Agent**, **NanoClaw**, **CoPaw**。
    - **特征**: 快速修复严重Bug，积极合并新功能PR，维护者与贡献者互动紧密，项目正从“可用”向“好用”过渡。

- **第三梯队（稳健维护/专注细分领域）**:
    - **PicoClaw**, **LobsterAI**。
    - **特征**: 社区规模较小，但指标健康，Bug修复快，功能有深度，维护者精力集中，属于潜在的“小而美”黑马。

- **第四梯队（沉寂/停滞）**:
    - **NullClaw**, **TinyClaw**, **Moltis**, **ZeptoClaw**。
    - **特征**: 连续24小时无活动，表明项目缺乏活力，贡献者可能已经转移。

### 7. 值得关注的趋势信号

1.  **安全正从“加分项”变为“生存必备项”**：NanoBot一日修复多个严重漏洞、ZeroClaw的供应链安全RFC、OpenClaw的Secret解析崩溃和权限绕过，共同敲响了警钟。对于任何希望进入企业市场的AI助手项目，**零信任架构、细粒度权限控制、可验证的构建过程**不再是可选项，而是必需品。

2.  **“长推理/Agent Loop”的可靠性是下一个战场**：OpenClaw的流式超时、CoPaw的Agent死循环、Hermes的会话状态损坏，都指向了一个核心问题：**当AI Agent需要长时间思考或执行复杂工具链时，如何保证其状态不丢失、执行不卡死、结果不重复？** 这将是下一阶段智能体产品差异化的关键。

3.  **端侧与云原生架构开始分化**：PicoClaw的轻量级、ZeroClaw的Wasm-first代表着向**边缘/去中心化**方向的技术路线，而OpenClaw、IronClaw的微服务化则代表了**中心化/平台化**路线。开发者需要根据自身场景（隐私、延迟、部署成本）做出选择。

4.  **协作（多Agent/人机协同）模型成为必争之地**：LobsterAI将全部精力押注在Cowork模式，IronClaw的审批流程、ZeroClaw的delegate模式均涉及多实体交互。这表明，“单Agent”的会话模式已不能满足需求，**如何让多个智能体或人与智能体顺畅协作**，成为定义下一代AI平台的核心入口。

5.  **开发者体验（DX）成为竞争力护城河**：OpenClaw的ClawHub投入大但体验差、Hermes的Dashboard更新后崩溃，这些反面教材与ZeroClaw积极主动的贡献文档更新形成对比。在功能趋同的背景下，**能让开发者快速上手、轻松贡献、稳定预期的项目，将最终赢得社区心智。**

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

好的，这是根据您提供的 NanoBot 项目 GitHub 数据生成的 2026-06-26 项目动态日报。

---

## NanoBot 项目动态日报 - 2026-06-26

### 1. 今日速览

今日项目核心动态是集中处理多个严重的安全漏洞，这些漏洞在昨日被集中报告。**过去24小时关闭了12个安全问题相关的 Issue**，并提交了对应的修复 PR (如 #4525, #4526)，表明项目组对安全性问题响应迅速且处理高效。同时，社区提交的新 PR 主要集中在增强 WebUI 体验 (PWA支持)、优化 MCP 连接稳定性及扩展技能管理功能。尽管版本发布停滞，但项目在安全加固和功能迭代上均取得显著进展。

**活跃度评估：** 高。安全事件处理拉动 Issue/PR 更新数量激增，同时功能开发和 Bug 修复并行推进。

### 2. 版本发布

无新版本发布。

### 3. 项目进展

今日项目关键进展体现在安全修复与功能增强并重，共有 15 个 PR 被合并或关闭，重点包括：

- **核心安全加固 (已完成):**
    - `#4524`: 修复了 MCP `enabledTools` 白名单绕过漏洞，确保资源 (Resource) 和提示 (Prompt) 能力也受白名单控制。
    - `#4099`: 修复了文件系统工具中的 `extra_allowed_dirs` 权限越界问题，确保这些目录对 `write_file` 工具保持只读。

- **稳定性修复 (已合并/关闭):**
    - `#4532`, `#4530`, `#4531`: 一系列的修复改善了 Anthropic API 兼容性、流式与非流式响应对工具调用 ID 去重的处理以及流媒体增量合并的正确性。
    - `#4522`: 为所有工具添加了通用重复调用保护，防止 Agent 因工具反复失败而陷入死循环，提升系统鲁棒性。
    - `#4523`: 修复了一个因文件系统创建时间戳精度不足导致的测试用例不稳定问题。

- **功能增强 (待合并或已关闭):**
    - `#4502`: 提出了为 Gateway 添加 Webhook 触发器的功能，扩展了 NnaoBot 与其他系统集成的能力。
    - `#4504`: 提议支持在 `skills` 目录下使用子目录进行分组，以改善大量技能的导航和管理。

**项目总结：** 项目通过快速安全修复巩固了基础安全防线，并通过多个小修补提升了潜在的系统稳定性。同时，新的功能提议表明项目正在向更复杂、更企业级的集成场景演进。

### 4. 社区热点

今天社区最受关注的话题集中在**安全漏洞的披露与修复**上。用户 **@YLChen-007** 在今天集中提交了多个安全问题的详细报告，包括：

- `#4514`, `#4515`, `#4516`, `#4520`, `#4521`: 一系列关于 `exec` 工具通过链式命令、注释、包装器前缀等方式绕过白名单的漏洞。
- `#4519`, `#4517`: MCP 服务器 `enabledTools` 白名单绕过，导致资源和提示能力暴露。
- `#4518`: exec 工具默认使用登录 shell 可能会重新引入用户环境变量中的密钥，带来安全风险。

**分析：** 这表明一位有经验的社区安全研究员正在对 NanoBot 进行深入的安全审计。其报告非常详尽，指出了许多清晰且高危的漏洞，这促使项目维护团队立即做出反应，并在同一天提交了对应的修复 PR (如 `#4525`, `#4526`)。这种高效的协作模式是开源项目的积极信号，极大地提升了项目安全健康度。

### 5. Bug 与稳定性

今日报告的 Bugs 主要集中在安全性与跨平台兼容性，严重程程度高。

| 严重程度 | Issue 编号 | 问题描述 | 状态 | 相关修复 PR |
| :--- | :--- | :--- | :--- | :--- |
| **严重** | `#4514`, `#4515`, `#4516`, `#4520`, `#4521` | `exec` 工具允许列表多种绕过方式，可执行未授权的 Shell 命令。 | 已关闭 | `#4525`, `#4526` |
| **严重** | `#4519`, `#4517`, `#4434`, `#4435` | MCP `enabledTools` 白名单不生效，可暴露资源/提示功能。 | 已关闭 | `#4524` |
| **严重** | `#4518` | `exec` 默认登录 shell 可能泄露用户密钥。 | 开放 | `#4525` |
| **中等** | `#4511` | Windows 系统下，`nanobot gateway --background` 在 `/restart` 后状态不符。 | 开放 | 暂无 |
| **中等** | `#4513` | 将 NanoBot 注册为 Windows 系统服务 (nssm) 后，执行 `/restart` 异常。 | 开放 | 暂无 |
| **低** | `#4488` | Telegram Web 版本消息显示“此消息不支持”，疑似由富文本功能引入的回归问题。 | 关闭 | 已通过其他方式修复？ (未在 PR 列表中体现) |

### 6. 功能请求与路线图信号

- **WebUI 增强 (移动端):** `#4479` 提出的 PWA 支持和侧边栏滑动手势，已有对应的 PR (`#4494`) 被提交。该功能有望显著改善移动端用户的体验，很可能被纳入下一个版本。
- **MCP 服务器空闲自动关闭:** `#4506` 提出了自动关闭空闲 MCP 服务器以防止资源泄露的功能。这反映了在大规模使用中，资源管理已成为社区用户关注的实际问题。
- **技能目录分层:** `#4504` 提议允许 `skills` 目录使用子目录，以解决技能数量增多后的组织管理难题。这是一个直击用户痛点的功能，纳入下个版本的可能性很高。
- **子 Agent `fail_on_tool_error` 可配置:** `#4198` 请求将子 Agent 在工具调用失败时的行为配置化，以提供更灵活的错误处理能力。这是一个提升复杂任务自动化稳定性的方向性请求。

### 7. 用户反馈摘要

从今日关闭的 Issue 评论中，可以提炼出以下用户反馈：

- **安全是首要关切：** 用户 **@YLChen-007** 通过详尽报告表达了对 NanoBot 安全性的高度关注和严谨态度。其报告揭示了 `exec` 和 MCP 权限控制机制中存在的深层问题，表明高级用户对 Agent 安全边界有较高要求，并希望项目能提供更细粒度和难以绕过的安全控制。
- **用户体验的“小痛点”：**
    - 用户 `@Quincy-Zh` 报告了 Windows 系统下作为服务运行和后台重启的问题，这可能影响部分 Windows 用户在自动化部署场景下的使用。
    - 用户 `@chengyongru` 遇到的 Telegram Web 消息不支持问题，虽然是客户端的限制，但反映出跨平台体验一致性的重要性。
    - 用户 `@0ndrec` 反馈模型有时会回复“已完成但无响应”，这可能涉及模型输出解析逻辑或上下文处理问题。

### 8. 待处理积压

以下为一些开放且应获得更多关注的 Issue 和 PR，提醒维护者留意：

| 类型 | 编号 | 标题 | 创建时间 | 最后更新时间 | 备注 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Issue | `#4518` | [Security] Default login-shell execution in `exec` reintroduces secrets from shell startup files | 2026-06-25 | 2026-06-25 | 一个高优先级的安全风险，虽然有修复 PR (`#4525`)，但 Issue 本身尚未更新状态。 |
| Issue | `#4511` | [bug] Windows 系统下，gateway 命令行选项 --background 的问题 | 2026-06-25 | 2026-06-26 | 影响 Windows 用户体验的实际 Bug，目前无关联修复 PR。 |
| Issue | `#4513` | [bug] 使用 nssm 把 nanobot 设置为系统服务，执行 /restart 重启程序的异常问题 | 2026-06-25 | 2026-06-25 | 与 `#4511` 类似，是关于 Windows 服务部署的另一个稳定性问题。 |
| PR | `#4441` | [fix] fix(mcp): force-close streamable_http generator on reconnect failure | 2026-06-21 | 2026-06-25 | 修复 MCP 服务器重连失败导致 Gateway 崩溃的问题，已开放多日，宜尽快审查合并。 |

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，这是为您生成的 Hermes Agent 项目动态日报。

---

# Hermes Agent 项目动态日报 | 2026-06-26

## 1. 今日速览

项目今日活跃度极高，尤其是 **Bug 修复** 与 **平台适配** 工作迎来了井喷。过去24小时内，社区提交了50条Issue和50条PR，主要集中在核心稳定性修复和多个平台的适配问题上。值得注意的是，今日报告了多个 **P0/P1 级别的严重Bug**，包括会话状态损坏、内存泄漏、安全漏洞等，但社区响应迅速，多个问题已存在对应的修复PR。总体来看，项目在经历快速迭代，当前重点在于修补回归缺陷和增强系统整体健壮性。

## 2. 版本发布

- **无**

## 3. 项目进展

今日虽无重大版本发布，但多个重要PR的更新标志着项目在关键领域的推进：

- **安全性增强**: PR #52801 `fix(email): reject spoofed From: header for authorization` 针对邮件网关的假冒攻击(GHSA-rxqh-5572-8m77)提供了修复，通过强制SPF/DKIM/DMARC验证来加固身份认证边界。
- **会话状态修复**: PR #52808 `fix(gateway): prune stale sessions.json entries on startup` 修复了因非正常关闭导致会话路由失忆的问题。PR #52818 `fix(gateway): clear stale resume_pending markers in scheduler` 解决了僵尸标记累积问题。这两者共同提升了网关与会话管理的健壮性。
- **Webhook 防循环**: PR #52824 `fix(webhook): add sender_blocklist to prevent self-triggered loops` 解决了Webhook路由中可能引发的自我触发死循环问题，增强了自动化的安全性。
- **桌面端修复**: PR #52819 `fix(desktop): WSL2 clipboard image paste + Linux titlebar overlay` 修复了WSL2环境下粘贴图像和标题栏的兼容性问题，提升了跨平台体验。
- **工具链适配**: PR #52812 `fix: detect Python toolchain via HERMES_PYTHON env var in Nix-packaged environments` 和 PR #52645 `feat: add Volcengine Ark provider` 分别增强了在Nix环境下的兼容性和新增了火山引擎作为内置大模型提供商。

**总结**: 项目在**坚固内核** (会话、网关、安全性) 和**扩展外延** (WSL2、Nix、新平台) 两方面均有实质进展，正从功能扩张期向稳定性与生态完善期过渡。

## 4. 社区热点

今日讨论最活跃的议题反映了社区对**功能完善**与**遗留Bug**的普遍关注：

1.  **[Feature]: support Telegram Bot API 10.1 Rich Messages** (Issue #44428, 7条评论)
    - **链接**: https://github.com/nousresearch/hermes-agent/issues/44428
    - **分析**: 社区用户对 Telegram 新功能适配有强烈需求。该Issue讨论了如何利用Telegram最新的富消息API (RichMessage)，以实现标题、列表、表格、LaTeX等在Telegram上的原生渲染。这反映了用户对更丰富、更现代的交互体验的追求。

2.  **[Bug]: Dashboard chat feature is broken after hermes update** (Issue #36658, 8条评论)
    - **链接**: https://github.com/nousresearch/hermes-agent/issues/36658
    - **分析**: 这是一个已持续近一个月的Bug。用户在更新后Dashboard聊天功能出现React错误，导致无法使用。社区用户持续关注此问题并补充log，希望得到快速解决。这暴露出项目在重大更新时对前端功能的回归测试可能不足。

3.  **[Feature]: integrate headroom-ai for tool output compression** (Issue #39691, 8条评论)
    - **链接**: https://github.com/nousresearch/hermes-agent/issues/39691
    - **分析**: 关于上下文压缩的讨论非常深入。社区提出了一个具体的第三方方案 `headroom-ai`，旨在为工具输出提供更细粒度的压缩，而非现有的全话总结。这表明高级用户对优化token消耗、提升长会话性能有明确且专业的需求。

## 5. Bug 与稳定性

今日报告的Bug数量多且严重，是当前项目面临的主要挑战。以下是按严重程度排列的关键问题：

- **P0 (严重)**:
    - `fix: resume/cron messages send stale DB fields, breaking provider prompt cache` (PR #52813) - **已有修复PR**。会话恢复时发送过期数据，导致100%的提示缓存失效，严重影响性能和成本。
    - `Gateway Memory Loss — INSERT omits active column in hermes_state.py` (Issue #51646) - 网关写入数据库时遗漏关键字段，导致新会话永远加载不到历史消息，功能严重受损。

- **P1 (高)**:
    - `fix(gateway): prune stale sessions.json entries on startup (FM9)` (PR #52808) - **已有修复PR**。网关崩溃后的会话失忆问题。
    - `fix(email): reject spoofed From: header for authorization` (PR #52801) - **已有修复PR**。邮件网关安全漏洞。
    - `Web/WeChat sessions leak history` (Issue #49106) - **已关闭**。跨会话的历史泄漏问题已被修复。
    - `installer fails at "desktop" stage on Windows 10` (Issue #46260) - Windows桌面端安装失败，影响新用户和平台采用率。

- **P2 (中)**:
    - `Telegram typing indicator stuck indefinitely` (Issue #28004) - 一个已持续一个多月的UX问题，虽不致命但严重影响观感。
    - `Feishu adapter incorrectly downgrades markdown tables to plain text` (Issue #52786) - **已有修复PR**（PR #27922）。飞书表格渲染问题复发。
    - `hermes update produces broken Desktop asar when git pull adds npm deps` (Issue #52764) - 自动更新流程在特定情况下会产生产品文件损坏的桌面端版本。

- **P3 (低)**:
    - `write_file tool: non-local terminal backend path resolved on macOS host` (Issue #52823) - Docker后端路径解析错误，影响macOS用户。

**总体评估**: 今日的Bug报告显示出系统在会话状态管理、平台适配和自动更新流程方面存在一些“有问题的边缘情况”。但好消息是，大部分严重问题已有或同时有修复PR，显示了项目维护者与社区的快速响应。

## 6. 功能请求与路线图信号

用户提出的新功能请求多样，部分与现有PR高度契合，信号清晰：

- **强烈路线图信号**:
    - **飞书富文本渲染 (Unified Fix)** (Issue #46470): 提出使用飞书Card 2.0统一修复所有Markdown渲染问题。这与PR #27922 (Fix feishu markdown tables)、PR #51269 (Bot-to-bot for Feishu) 等形成了合力，表明飞书适配是当前的重点方向。
    - **桌面端系统托盘** (Issue #52787) 和 **Linux .desktop 快捷方式** (Issue #52769): 用户对桌面端体验提出了更符合操作系统习惯的要求，如最小化到托盘、自动创建桌面图标。这标志着Hermes Desktop正从“能用”向“好用”进化。

- **前瞻性需求**:
    - **中文界面支持** (Issue #52825): 有中国用户明确提出桌面端需要中文支持。这是项目国际化的重要信号，可能在未来版本中纳入i18n规划。
    - **AGENTS.md 过大问题** (Issue #52821): 指出系统提示词文件过大浪费Token。这是一个非常专业的技术建议，表明社区用户已经开始关注底层架构的性能优化。
    - **Bulk Archive Sessions** (Issue #48843): 用户请求批量归档会话功能。这是一个典型的“由小型项目管理工具向大型平台进化”过程中的用户痛点。

## 7. 用户反馈摘要

从Issue评论中提炼的用户声音：

- **痛点:**
    - “会话历史在会话之间泄漏，唯一的修复办法是重启，太麻烦。”（Issue #49106）
    - “更新后Dashboard直接挂了，报React错误，回滚也无法解决，非常影响工作。”（Issue #36658）
    - “在Windows上安装失败，卡在桌面端构建，对新手太不友好了。”（Issue #46260）
    - “Telegram打字的‘正在输入…’状态永远不消失，用户很困惑。”（Issue #28004）

- **满意/认可:**
    - (针对PR) “很高兴看到对这个安全问题的修复，特别是之前OAuth的漏洞让我很担心。”（对PR #47705 和 PR #52801 的认可）
    - (针对新功能) “希望 `/goal` 命令在桌面端也能支持多行，现在只有CLI和Telegram能用，体验不完整。”（Issue #41323，表达了对CLI和Telegram体验的认可）

## 8. 待处理积压

- **长期未解决的安全/关键功能请求**:
    - `[Feature]: credential proxy daemon` (Issue #4656, **84天未关闭**)
    - **链接**: https://github.com/nousresearch/hermes-agent/issues/4656
    - **状态**: 这是一个关于凭证代理守护进程的高级安全功能请求。虽然PR #30179 (`iron-proxy`) 是其中的一部分，但该Issue仍在开放，等待最终整合和更广泛的讨论。**分析**: 此Issue代表了社区对零信任架构的长期追求，虽然进展缓慢但方向正确，维护者仍需关注。

- **长期未解决的P2 Bug**:
    - `Telegram typing indicator stuck indefinitely` (Issue #28004, **39天未关闭**)
    - **链接**: https://github.com/nousresearch/hermes-agent/issues/28004
    - **状态**: 一个明显的竞态条件Bug，描述了修复思路但PR尚未合并。**分析**: 该Bug持续时间长，影响Telegram用户体验。建议维护者重新评估优先级，或鼓励社区提交更完善的修复方案。

- **合并受阻的早期功能PR**:
    - `feat(vertex): add Vertex AI provider for Gemini` (PR #8427, **75天未合并**)
    - **链接**: https://github.com/nousresearch/hermes-agent/pull/8427
    - **状态**: PR已提交两个多月，功能对大型企业用户极有价值。**分析**: 此PR的长期停滞可能会让贡献者感到沮丧，并对社区的贡献机制产生疑虑。如果存在冲突或选择其他方案的问题，维护者应主动沟通并说明原因。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，以下是根据您提供的 PicoClaw 项目数据生成的 2026-06-26 项目动态日报。

---

## PicoClaw 项目动态日报 (2026-06-26)

**项目名称:** PicoClaw (github.com/sipeed/picoclaw)
**报告周期:** 2026-06-25 至 2026-06-26

### 1. 今日速览

今日项目活跃度显著提升，共处理了 **19 条 PR**，其中 **6 条** 被合并或关闭，代码合并速率较高。核心贡献者和 Dependabot 均有产出，修复了多项 Bug 并进行了依赖升级。Issues 方面，社区反馈的问题得到快速响应，有 **2 个 Bug 被关闭**，表明问题处理流程高效。虽然无新版本发布，但大量 PR 的合并和活跃的 Issue 处理，表明项目正处于密集的迭代维护期，整体健康度良好。

### 2. 版本发布

- **无新版本发布。**

### 3. 项目进展

今日项目在稳定性和代码质量上取得了实质性进展，多项关键 Bug 已被修复并合并。

- **修复 Evolution 功能 Token 消耗问题 (PR #3169, #3166, #3168):** `Alix-007` 贡献者今日合并了 3 个重要的修复 PR。
  - **PR #3169**: [修复 Evolution 模式下的心跳检测导致的不必要 Token 消耗](https://github.com/sipeed/picoclaw/pull/3169)。该修复跳过了“冷路径”调度，防止在草稿模式下定期执行心跳检查时浪费 Token。
  - **PR #3166**: [修复了 `openai_compat` 中导致编译失败的构建错误 `undefined: log`](https://github.com/sipeed/picoclaw/pull/3166)，改用结构化日志记录器。
  - **PR #3168**: [改进了模型错误响应的处理](https://github.com/sipeed/picoclaw/pull/3168)，当服务器返回非 200 状态码且响应体读取失败时，会正确报告底层读取错误，而非空或误导性的 HTTP 错误。

- **提高代码健壮性 (PR #3170, #3171, #3172):** `chengzhichao-xydt` 今日提交并合并了针对代码健壮性的多个修复：
  - **PR #3170**: [修复了 Base64 编码器在 `io.Copy` 失败时资源泄漏的问题](https://github.com/sipeed/picoclaw/pull/3170)，确保无论复制成功与否都正确关闭编码器。
  - **PR #3171**: [为 LINE 频道的 `Send` 方法添加了类型断言检查](https://github.com/sipeed/picoclaw/pull/3171)，防止因意外的 map 值类型导致程序 panic。
  - **PR #3172**: [在多个错误路径和重试循环中显式忽略 `Close()` 错误](https://github.com/sipeed/picoclaw/pull/3172)，避免次要错误掩盖主要错误。

### 4. 社区热点

- **Feature Discussion: 用 Vodozemac 替代 libolm (Issue #3088)**
  - **状态:** [OPEN]
  - **链接:** [#3088](https://github.com/sipeed/picoclaw/issues/3088)
  - **分析:** 该 Issue 提议替换不安全和未维护的 `libolm` 库，转而使用官方替代品 `vodozemac`，获得了 2 个 👍 和 3 条评论。这表明社区对底层安全依赖库的演进高度关注，并积极推动项目采用更先进、更安全的替代方案。这是影响项目长期安全性和标准合规性的关键议题。

### 5. Bug 与稳定性

今日无新的重大 Bug 报告。昨日活跃的两个 Bug 已得到解决：

- **严重程度: 中** - **[CLOSED] Evolution 模式下持续消耗 Token (Issue #3012)**
  - **链接:** [#3012](https://github.com/sipeed/picoclaw/issues/3012)
  - **状态:** 该问题已由 PR #3169 修复并关闭。
- **严重程度: 中** - **[CLOSED] Agent 执行每小时任务时出现频道错误 (Issue #1757)**
  - **链接:** [#1757](https://github.com/sipeed/picoclaw/issues/1757)
  - **状态:** 已关闭。虽然未提及具体关联的修复 PR，但问题已得到解决。

### 6. 功能请求与路线图信号

- **新增远程 Pico WebSocket 模式 (PR #3118)**
  - **链接:** [#3118](https://github.com/sipeed/picoclaw/pull/3118)
  - **状态:** [OPEN]
  - **分析:** 该 PR 为 `picoclaw agent` 命令添加了可选的远程模式，允许通过 WebSocket 连接到远程 Pico 实例。这显著扩展了 PicoClaw 的使用场景，使其可以部署在非本地环境，是通往分布式或服务化架构的重要信号，可能被纳入下一版本。

- **新增 Delta Chat 网关 (PR #3063)**
  - **链接:** [#3063](https://github.com/sipeed/picoclaw/pull/3063)
  - **状态:** [OPEN]
  - **分析:** 该 PR 为 PicoClaw 增加了 Delta Chat 作为新的消息网关。Delta Chat 是一个基于邮件的加密聊天应用，此举将拓宽 PicoClaw 的生态连接能力，接纳更多的去中心化通信渠道。

### 7. 用户反馈摘要

- **Bug 反馈闭环高效：** 从 Issue #3012 和 #1757 来看，用户报告的 Bug 能够得到快速确认和修复。特别是 #3012 (Evolution Token 消耗问题)，从 6月5日报告到6月25日修复关闭，处理周期在一个月内，反映出项目团队对影响用户体验的 Bug 给予足够重视。
- **积极贡献安全方向：** Issue #3088 (用 Vodozemac 替代 libolm) 的提出和获得关注，表明用户群体中有对项目底层安全架构有深入了解的开发者，并乐于贡献高质量的改进方案。

### 8. 待处理积压

- **修复 Sub-turn 消息重复 (PR #3142)**
  - **链接:** [#3142](https://github.com/sipeed/picoclaw/pull/3142)
  - **状态:** [OPEN] (stale)
  - **提醒:** 该 PR 从 6月17日开启，旨在修复异步子 Agent 完成时可能导致消息重复交付的 Bug。此问题影响聊天体验，建议维护者关注其状态并推动评审与合并。

- **技能安装的类型断言问题 (PR #3092)**
  - **链接:** [#3092](https://github.com/sipeed/picoclaw/pull/3092)
  - **状态:** [CLOSED] (stale)
  - **注意:** 该 PR 虽已显示为关闭，但在 PR 列表中仍被标记为 `stale`，请确认其最终处理结果（是已合并还是被拒绝）并更新状态标签，避免造成混淆。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

好的，这是根据您提供的 NanoClaw 项目 GitHub 数据生成的 2026-06-26 项目动态日报。

---

# NanoClaw 项目动态日报 | 2026-06-26

## 1. 今日速览

今日项目活跃度**极高**。过去24小时内，共有 **16 个 Pull Request (PR)** 被更新，其中 **11 个已合并/关闭**，显示出维护者正在进行密集的代码合并与清理工作。核心动态集中在**安全加固**、**平台兼容性修复**、**新功能交付**（如容器资源限制、认证容灾、技能学习）以及**长期积压特性的最终落地**。虽然仅有1个新 Issue 提交，但 PR 的合并节奏表明项目正处于一个重要的功能交付和稳定性提升阶段。

## 2. 版本发布

**无。**

当前没有新的版本发布。但大量的 PR 合并在未来几天内可能会触发一个包含多项改进的新版本。

## 3. 项目进展

今日合并/关闭的 PR 涵盖了多个重要领域，显著提升了项目的成熟度和安全性：

- **安全性与稳定性**：
    - [`#2817`](https://github.com/nanocoai/nanoclaw/pull/2817) **[已合并]** `fix(security): confine send_file reads to workspace`：通过严格的文件路径验证，修复了一个可能导致文件读取越权的安全漏洞。
    - [`#2815`](https://github.com/nanocoai/nanoclaw/pull/2815) **[已合并]** `fix(router): guard safeParseContent against primitive JSON`：修复了路由器在处理原始JSON时可能存在的解析问题，增强了鲁棒性。
    - [`#2830`](https://github.com/nanocoai/nanoclaw/pull/2830) **[已合并]** `fix(setup): reap dead peer service registrations`: 解决了用户删除项目代码后，系统残留失效服务注册的问题，提升了系统清理的彻底性。
- **新功能交付**：
    - [`#2856`](https://github.com/nanocoai/nanoclaw/pull/2856) **[已合并]** `feat(container): per-container CPU/memory limits (opt-in)`：为Agent容器提供了可选的CPU和内存限制功能，防止单个Agent占用过多主机资源。
    - [`#2855`](https://github.com/nanocoai/nanoclaw/pull/2855) **[已合并]** `feat(auth): subscription-primary credential posture with API-key failover`：引入了订阅优先、API密钥作为热备的认证策略，当主要认证方式失败时能自动切换，提升了服务的可靠性。
    - [`#2832`](https://github.com/nanocoai/nanoclaw/pull/2832) **[已合并]** `feat(approvals): reject with reason`：在审批流程中增加了“拒绝并附带理由”的功能，使Agent能根据反馈进行更智能的响应。
    - [`#2843`](https://github.com/nanocoai/nanoclaw/pull/2843) **[已合并]** `feat: add /learn skill`：新增了一个强大的 `/learn` 技能，允许用户通过目录、URL或粘贴内容，提炼并创建可复用的技能，极大地扩展了平台的可扩展性。
- **长期特性落地**：
    - [`#2472`](https://github.com/nanocoai/nanoclaw/pull/2472) **[已关闭]** `feat(slack): per-message thread for top-level posts in per-thread sessions`：经过一个多月的开发与测试，该PR最终被合并。它解决了Slack集成中“每话题会话”模式的行为问题，现在每个新对话能正确创建独立会话，并回复为线程消息，而非堆积在同一个会话中。

## 4. 社区热点

今日最值得关注的动态是 **#2472** 和 **#2471** 两个关于 Slack 集成的 PR 最终被关闭。尽管它们并非于今日新开，但在经过一个多月的等待后被合并，显示了社区对此功能的强烈需求。

- **链接**: [#2472 feat(slack): per-message thread for top-level posts in per-thread sessions](https://github.com/nanocoai/nanoclaw/pull/2472), [#2471 feat(router): per-channel threadId rewrite for per-thread sessions](https://github.com/nanocoai/nanoclaw/pull/2471)
- **诉求分析**: 这两个 PR 共同解决了一个Slack用户的痛点：在高频使用场景下，“per-thread”模式无法正常工作，所有消息都堆积在一个会话中，导致混乱。社区用户通过创建并耐心等待这两个PR，成功推动了平台核心集成体验的重大改进。

## 5. Bug 与稳定性

今日报告的 Bug 较少，但已完成的修复PR体现了对稳定性的持续投入。

- [High] **v1到v2数据库迁移崩溃**：
    - **影响**: 旧版本v1数据库（如1.1.0）在迁移到v2时会因缺少`is_main`列而崩溃。
    - **严重程度**: 高，会阻止用户升级。
    - **状态**: 已有修复PR [`#2859`](https://github.com/nanocoai/nanoclaw/pull/2859) [待合并]。
- [Medium] **macOS容器内证书问题**：
    - **影响**: 在macOS使用Rancher Desktop时，Agent API调用因无法找到网关CA证书而失败。
    - **严重程度**: 中，影响特定平台用户。
    - **状态**: 已通过PR [`#2854`](https://github.com/nanocoai/nanoclaw/pull/2854) [已合并] 修复。

## 6. 功能请求与路线图信号

- **多管理员审批与CLI审批 (Issue #2857)**：
    - 用户 `sirpy` 提出的Issue [`#2857`](https://github.com/nanocoai/nanoclaw/issues/2857) 建议支持多管理员审批，并允许拥有机器访问权限的所有者通过CLI进行审批。这是一个非常有价值的请求，直接扩展了审批流程的可用性和健壮性。
    - **信号**: 考虑到最近刚合并了“拒绝并附带理由”的PR (`#2832`)，项目显然正在完善审批模块。此Issue很可能在未来版本中被采纳。

## 7. 用户反馈摘要

- **用户痛点/场景**:
    - **审批流程限制**: 单点审批模式限制了团队协作，当负责审批的管理员不在线时，流程会阻塞 (`#2857`)。
    - **Slack集成混乱**: 在使用“per-thread”模式时，用户抱怨所有消息都混在一起，无法有效跟踪对话 (`#2472`, `#2471`)。
    - **升级障碍**: 部分用户因历史数据库结构不同，无法顺利完成版本升级 (`#2859`)。
- **满意点**:
    - **审批交互优化**: 社区对新增的“拒绝并附带理由”功能持积极态度，认为这能让人机交互更智能 (`#2832`)。
    - **新技能期待**: `/learn` 技能的合并引发了社区的关注，用户期待它能为平台带来新的自定义能力 (`#2843`)。

## 8. 待处理积压

- **重要待合并PR**: **[`#2795`](https://github.com/nanocoai/nanoclaw/pull/2795)** `feat: add /add-clidash — read-only CLI-derived dashboard skill`。此PR于6月17日提交，旨在添加一个CLI仪表盘技能，并且已有后续修复PR (`#2858`) 来补充它。该技能请求有一定关注度，建议维护团队尽快审阅并决定是否合并。
- **待定问题**: 暂无长期无人响应的严重问题。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

好的，作为一名 AI 智能体与个人 AI 助手领域开源项目分析师，我将根据您提供的 IronClaw 项目数据，为您生成 2026-06-26 的项目动态日报。

---

## IronClaw 项目动态日报 | 2026-06-26

### 1. 今日速览

项目今日活跃度极高，过去24小时内有**50个**新/活跃的Issue和**50个**PR更新，显示出密集的开发和社区互动。开发节奏稳健，社区发现并报告了大量关于 **Reborn WebUI** 的交互与持久化问题，项目核心团队也迅速响应，提交了一系列高优先级的修复与功能 PR。尽管今日无新版本发布，但多个大型 PR（如 Trace Commons、CAS 锁优化和能力策略基础设施）的持续推进，表明项目正处于为下一代功能集合夯实底层基础的关键阶段。

### 3. 项目进展

今日项目推进主要集中在修复 Reborn WebUI 的用户体验问题和夯实底层基础设施两个方向。

- **UI/UX 修复与优化**:
    - **WebUI v2 日志页面修复**: 修复了日志页面无法滚动的问题，提升了调试体验。[PR #5278](https://github.com/nearai/ironclaw/pull/5278) 已被合并。
    - **“日志”入口位置调整**: 修复了“日志”入口出现在消息输入框内部的问题，将其移至专属工具栏，优化了聊天界面。[PR #5284](https://github.com/nearai/ironclaw/pull/5284) 已提交。
    - **“审批”卡与全局设置关联**: 为审批卡上的“总是允许”选项增加了通往全局设置的链接，提升了工具权限管理的易用性。[PR #5247](https://github.com/nearai/ironclaw/pull/5247) 处于待合并状态。
    - **消息时间戳一致性**: 为对话中的消息增加了稳定的时间戳显示。[Issue #5212](https://github.com/nearai/ironclaw/issues/5212) 已关闭，相关修复已完成。

- **后端稳定性与性能**:
    - **消除死锁风险**: 通过引入共享的 `cas_update` 辅助函数，替换了每记录锁，消除了 `per-record lock convoys` 问题，提升了并发场景下的稳定性。[PR #5234](https://github.com/nearai/ironclaw/pull/5234) 已提交。
    - **减少数据库往返**: 将 Postgres CAS `put` 操作的三次数据库往返合并为一次，显著优化了写入路径的性能。[PR #5255](https://github.com/nearai/ironclaw/pull/5255) 已合并。
    - **修复循环挂起问题**: 修复了因状态判断遗漏而导致的 `forever-hangs` 问题，并阻止了因门控导致的运行时错误杀死。[PR #5250](https://github.com/nearai/ironclaw/pull/5250) 已提交。

- **面向未来的基础设施**:
    - **能力策略（Capability Policy）基础**: 实现了 **多用户本地认证** 机制，为后续精细化的权限控制策略铺平了道路。[Issue #5272](https://github.com/nearai/ironclaw/issues/5272) 对应的 [PR #5286](https://github.com/nearai/ironclaw/pull/5286) 已提交。
    - **内存扩展（Memory Extension）**: 实现了 #3537 的核心内容，将模型内存作为一个用户态扩展，并提供了原生文档存储提供者。这是增强记忆与自我学习能力的关键一步。[PR #5205](https://github.com/nearai/ironclaw/pull/5205) 处于待合并状态。
    - **Trace Commons 集成**: 提交了一个大型 PR，为整个集群的 Trace Commons 实例级注册、用户追踪和检查功能奠定了基础。[PR #5280](https://github.com/nearai/ironclaw/pull/5280) 是一个里程碑式的进展。

### 4. 社区热点

今日社区的热点集中在 **Reborn WebUI 的交互细节和工具权限持久化** 问题上。多个 Issue 引起了成员的深入探讨。

- **工具权限无法持久化**: `#5243` [Approve & always allow] 和 `#5283` [web_search]  均报告 "Approve & always allow" 功能失效。用户反复遇到每次对话都需要手动批准工具调用的问题，严重影响了使用体验和工作流效率。这表明工具的权限持久化逻辑存在根本性缺陷，是目前社区反馈最集中的痛点。

- **审批流程与消息丢失**: `#5196` ["Ask each time" 授权失败] 和 `#5210` [审批门控时发送新消息导致状态丢失] 揭示了当前审批流程的脆弱性。用户在执行“每次询问”操作时，若步骤不当会导致验证失败或消息状态错乱，反映出状态机的健壮性不足。

- **内部细节暴露**: `#5191` [内部技能调试消息暴露] 引发了社区对系统透明度的讨论。用户注意到原本属于系统内部的编排消息被直接展示在聊天UI中，虽然提供了额外信息，但也可能造成困惑。这一现象体现了社区用户正在深度使用并探索系统的内部机制。

### 5. Bug 与稳定性

今日报告的Bug主要集中在 WebUI 交互和后台自动化任务，按严重程度排列如下：

| 严重程度 | Issue / PR | 问题描述 | 是否有 Fix PR |
| :--- | :--- | :--- | :--- |
| **严重** | [#5276](https://github.com/nearai/ironclaw/issues/5276) | 定时自动化任务因 “No thread attached” 错误全部失败，成功率为0%。 | 待定 |
| **严重** | [#5289](https://github.com/nearai/ironclaw/issues/5289) | 工作流因 `invalid_input` 失败后，抛出的错误信息过于笼统（“driver protocol error”），掩盖了真正原因。 | 待定 |
| **高** | [#5192](https://github.com/nearai/ironclaw/issues/5192) | 拒绝某个工具的审批后，模型仍可能发起新的工具审批请求，导致循环。 | 待定 |
| **高** | [#5196](https://github.com/nearai/ironclaw/issues/5196) | “Ask each time” 权限配置下，批准后仍可能因授权错误失败，并触发重复的审批流。 | 待定 |
| **中** | [#5282](https://github.com/nearai/ironclaw/issues/5282) | “Logs” 入口不应出现在消息输入框内部，干扰用户输入。 | [是 - #5284](https://github.com/nearai/ironclaw/pull/5284) |
| **中** | [#5210](https://github.com/nearai/ironclaw/issues/5210) | 在审批门控开启时发送新消息，会导致重复警告和消息状态丢失。 | 待定 |
| **低** | [#5289](https://github.com/nearai/ironclaw/issues/5289) | 新消息输入框在等待 AI 响应时会卡死，无法输入。 | 待定 |

### 6. 功能请求与路线图信号

今日不仅报告了bug，还涌现了大量面向未来的功能请求，主要围绕**企业级权限管理和记忆系统**。

- **企业级权限管理 (能力策略)**: `#5261` [Admin-shared tools & skills] 及其一系列子 Issue (`#5266`, `#5267`, `#5268`, `#5272`, `#5273`) 构成了一个宏大的EPIC。这些请求来源于有管理企业级 AI 代理集群需求的用户，希望实现管理员共享工具、细粒度权限控制、多用户等高级功能。对应的多个修复 PR（如 `#5286`, `#5288`, `#5277`）已快速跟进，说明项目方高度重视此功能，极有可能被纳入下一版本的重点规划。

- **高级记忆与自我学习**: `#5260` [Reborn personal memory & self-learning] 是一个长期跟踪的北向目标，而 `#5264` [Memory #3537 follow-ups] 则列出了第一阶段的后续工作。这表明社区对让 AI 更加“了解”用户寄予厚望。配套的 `#5205` PR 已经实现了其主要代码，标志此功能即将落地。

- **自动化发现与易用性**: `#4980` [Automations empty state] 指出，当无自动化时，页面未提供任何创建指引。此需求虽小，但直接关系到新用户的留存率。考虑到开发团队正在重构UI，此提议很有可能被采纳。

### 7. 用户反馈摘要

从今日的 Issue 评论中，可以总结出以下几点真实用户反馈：

- **痛点一：工具权限管理失效**
  - **用户`@sunglow666`**: 反复报告 “Approve & always allow” 不生效的问题，声称 “*...does not persist the tool permission to Settings > Tools*”，表明此功能严重阻碍了用户的正常使用流程，信任度下降。
  - **用户`@think-in-universe`**: 在 `#5129` 中报告 `Always approve` 功能对 `outbound_delivery_target_set` 不工作，说明此问题可能是一个全局性缺陷，而非个别现象。

- **痛点二：自动化任务不可靠**
  - **用户`@loopstring`**: 报告每日PR摘要自动化每次都失败，错误为 “No thread attached”，导致了0%的成功率。这表明关键的自动化基础设施不够稳健，影响了依赖它的用户。

- **痛点三：UI/UX 不友好**
  - **用户`@sunglow666`**: 在 `#5191` 中抱怨 “*...internal skill orchestration/debug messages*” 被直接暴露在聊天界面中。这表明对于非技术用户来说，内部细节是噪音，破坏了简洁的体验。

- **满意点：新功能进展被看到**
  - **用户`@zetyquickly`**: 积极地创建了关于企业级权限管理的 EPIC `#5261` 及其子任务，并贡献了对应的代码。这说明核心贡献者对项目方向有投入，且有资源推动复杂功能落地，展现了项目内部活跃的协作生态。

### 8. 待处理积压

以下为长期存在或今日报告但尚未有明确解决路径的重要 Issue，建议维护团队关注：

- `#5119` - **IronClaw Reborn Local Dogfooding Findings**: 这是一个自 06/22 开始、为期一周的“自用测试”追踪 Issue。尽管已关闭大量子 Issue，但今天仍有新问题（如 `#5289`）归于其下。维护者应持续关注此 Issue，直到所有关键性问题解决，并总结出全面的“Reborn 体验”报告。

- `#5173` - **Daily ironclaw failure taxonomy — 2026-06-23**: 这是一份关于测试套件失败的详细分析报告。虽然不是Bug，但对于理解模型行为和测试缺陷模式至关重要。建议相关负责人（如 `@pranavraja99`）推动讨论，将分类结果转化为可执行的优化任务。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，以下是根据LobsterAI项目2026年6月26日数据生成的日报。

---

### LobsterAI 项目动态日报 | 2026-06-26

#### 1. 今日速览

过去24小时，LobsterAI项目异常活跃，核心开发团队（`liuzhq1986`, `btc69m979y-dotcom`）集中合并了8个Pull Request，显示出项目正处于高强度迭代期。修复工作主要集中在 **OpenClaw 插件系统** 的稳定性、**协作（Cowork）** 模式的子代理与计划模式逻辑优化，以及设置同步等基础设施的健壮性提升。尽管无新版本发布，但今日的修复和优化质量很高，显著提升了项目的稳定性和用户体验。

#### 3. 项目进展

今日项目进展迅速，8个PR全部被合并或关闭，体现了优秀的交付节奏。这些PR主要围绕三个核心领域：

- **OpenClaw 插件系统加固（3个PR）：** 
    - [#2203](https://github.com/netease-youdao/LobsterAI/pull/2203) 修复了本地扩展在预编译后加载失败的问题，确保了自定义扩展的可用性。
    - [#2202](https://github.com/netease-youdao/LobsterAI/pull/2202) 修复了在严格允许列表中，浏览器插件（Browser Plugin）被意外屏蔽的问题，保证了功能的完整性。
    - [#2201](https://github.com/netease-youdao/LobsterAI/pull/2201) 解决了子会话同步时可能产生的重复助手回复问题，避免了对话历史的混乱。
- **协作（Cowork）模式优化（3个PR）：** 
    - [#2199](https://github.com/netease-youdao/LobsterAI/pull/2199) 修复了父会话完成后，子代理状态轮询停止的问题，确保了多代理协作场景的完整执行。
    - [#2200](https://github.com/netease-youdao/LobsterAI/pull/2200) 通过智能处理流抖动，避免了Qwen等模型在计划（Plan）模式下生成重复消息的问题。
    - [#2204](https://github.com/netease-youdao/LobsterAI/pull/2204) 优化了计划标签的解析逻辑，现在能正确显示块级标签中的计划内容，而不是泄露标签符号到聊天消息中。
- **核心功能与UI修复（2个PR）：** 
    - [#2206](https://github.com/netease-youdao/LobsterAI/pull/2206) 修复了“开机自启”设置项的状态显示问题，确保其与操作系统真实状态同步，并增强了日志和错误提示。
    - [#2205](https://github.com/netease-youdao/LobsterAI/pull/2205) 更新了协作模式下的计划模式图标，换用了更美观的主题感知SVG组件。

#### 4. 社区热点

今日社区热点集中在 **Issue #1392** ([链接](https://github.com/netease-youdao/LobsterAI/issues/1392))：
- **讨论焦点：** 该Issue报告了一个影响部分定时任务的开关无法点击关闭的bug，持续已有近三个月。虽然只有一条评论，但作为当日唯一活跃的Issue，它代表了用户在使用自动化任务（定时任务）核心功能时遇到的严重障碍。
- **用户诉求：** 深层诉求是 **功能配置的可靠性**。用户发现“大部分任务开关正常，只有部分任务开关无法点击”，这表明问题并非全局性，可能与特定任务配置或状态有关。用户期望开关功能在任何场景下都应100%可用。

#### 5. Bug 与稳定性

| 严重程度 | Bug 描述 | Issue/PR 链接 | 状态 |
| :--- | :--- | :--- | :--- |
| **高** | 部分定时任务的开关点击无反应，无法关闭任务 | [Issue #1392](https://github.com/netease-youdao/LobsterAI/issues/1392) | 待处理 |
| **中** | 子代理会话同步时可能产生重复的助手回复，影响阅读体验 | [PR #2201](https://github.com/netease-youdao/LobsterAI/pull/2201) | 今日已修复 |
| **中** | 在父会话结束后，子代理的状态轮询停止，导致结果无法刷新 | [PR #2199](https://github.com/netease-youdao/LobsterAI/pull/2199) | 今日已修复 |
| **中** | 协作模式下的计划（Plan）标签泄露到消息中 | [PR #2204](https://github.com/netease-youdao/LobsterAI/pull/2204) | 今日已修复 |
| **中** | 流抖动导致计划模式下生成重复的计划消息 | [PR #2200](https://github.com/netease-youdao/LobsterAI/pull/2200) | 今日已修复 |
| **低** | 开机自启设置状态与操作系统真实状态不同步 | [PR #2206](https://github.com/netease-youdao/LobsterAI/pull/2206) | 今日已修复 |

#### 6. 功能请求与路线图信号

今日无明确的新功能请求。但从今日合并的PR中，可以观察到以下路线图信号：

- **协作（Cowork）模式持续成熟：** 针对子代理、计划（Plan）模式、流抖动等一系列修复，表明项目团队正在全力打磨这个核心的AI协作功能，目标是使其在各种模型和网络环境下都能稳定、优雅地运行。
- **系统健壮性与可观测性增强：** PR #2206 增加了诊断性日志和失败信息展示，PR #2201和#2199也加入了调试日志。这表明团队开始从“功能实现”迈向“系统运维”，这是项目进入成熟期的重要标志。

#### 7. 用户反馈摘要

- **痛点（来自 Issue #1392）：** 用户在使用“定时任务”这一自动化功能时，遇到了部分开关失效的bug。这个问题存在已近三个月，可能对依赖该功能实现工作流程自动化的用户造成了持续的困扰。

#### 8. 待处理积压

- **[Issue #1392] 定时任务开关点击无反应：**
    - **优先级：高**
    - **原因：** 该问题已存在 **85天**，影响核心功能，且无任何维护者回复或标记。作为社区当日唯一活跃的Issue，它成为了社区关注的焦点。
    - **建议：** 维护团队应尽快安排复现并排查此问题，并在Issue中与用户沟通，说明原因或提供临时解决方案。这是提升项目健康度和用户信任度的关键一步。

---
*数据截止：2026-06-26 12:00 (UTC)*

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

好的，作为AI智能体与个人AI助手领域开源项目分析师，以下是基于您提供的CoPaw (GitHub仓库: agentscope-ai/CoPaw) 数据生成的2026年6月26日项目动态日报。

---

## CoPaw 项目动态日报 | 2026年6月26日

### 1. 今日速览

过去24小时内，CoPaw项目保持高度活跃，社区贡献与开发者响应均十分积极。共有25条Issue更新和50条PR更新，反映出强大的社区参与度和密集的开发活动。尽管无新版本发布，但大量Bug修复和功能PR的合并表明项目正处于一个敏捷迭代、修复遗留问题并为新特性铺路的关键阶段。项目整体健康度良好，但需关注多个回归性Bug（如浏览器进程管理）和前端性能问题。

### 2. 版本发布

- **版本发布:** 无

### 3. 项目进展

今日合并或关闭的PR主要聚焦于**Bug修复、模型兼容性优化和文档建设**，提升了项目稳定性和可用性。

- **Bug修复:**
    - `PR #5496` [已合并] - 修复了 GLM-5.x 模型通过 OpenCode Go 使用时，因 tool schemas 中包含 `$ref/$defs` 导致的 `json_schema_converter.cc` 错误。([查看PR](https://github.com/agentscope-ai/QwenPaw/pull/5496))
    - `PR #5538` [已合并] - 修复了 `#5480` 报告中提到的控制台长消息排版错乱问题（Markdown换行符不生效）。([查看PR](https://github.com/agentscope-ai/QwenPaw/pull/5538))
    - `PR #5457` [已合并] - 对 `send_file_to_user` 功能增加了文件大小上限，防止因文件过大导致的潜在问题。([查看PR](https://github.com/agentscope-ai/QwenPaw/pull/5457))
    - `PR #5443` [已合并] - 修复了在 AgentScope 2.0 迁移后，TUI（终端用户界面）中 ACP（Agent Communication Protocol）命令和内联审批功能失效的问题。([查看PR](https://github.com/agentscope-ai/QwenPaw/pull/5443))

- **新功能与改进:**
    - `PR #5540` [待合并] - 对自动记忆（auto memory）系统进行重构，从基于回复ID追踪转向基于用户轮次标记（turn marker），提升了记忆机制的准确性和鲁棒性。([查看PR](https://github.com/agentscope-ai/QwenPaw/pull/5540))
    - `PR #5448` [待合并] - 为TUI引入了项目级代码会话支持，允许将ACP会话绑定到特定项目目录。([查看PR](https://github.com/agentscope-ai/QwenPaw/pull/5448))

- **文档与基建:**
    - `PR #5380` [已合并] - 增加了Langfuse（LLM可观测性工具）的Docker部署文档，方便用户进行生产级追踪。([查看PR](https://github.com/agentscope-ai/QwenPaw/pull/5380))

### 4. 社区热点

- **热点Issue: `#5345`: 自定义OpenAI兼容提供商无法进行函数调用**：该问题获得8条评论，讨论了OMLX等提供商无法使用function calling的兼容性问题。这反映出用户对连接第三方模型多样性的强烈需求，而不仅仅是标准OpenAI API。
    - [查看Issue](https://github.com/agentscope-ai/QwenPaw/issues/5345)
- **热点Issue: `#5379`: Python安装后启动报 Internal Server Error**：6条评论，该问题直接阻碍了新用户的上手体验，影响了项目的首次使用印象。
    - [查看Issue](https://github.com/agentscope-ai/QwenPaw/issues/5379)
- **热点Issue: `#5505`: MiniMax-M3图片安全审核误判导致视觉请求被剥离**：3条评论，这是一个比较棘手的状态缓存Bug，会导致模型错误地认为不支持图片输入，影响多模态用户体验。
    - [查看Issue](https://github.com/agentscope-ai/QwenPaw/issues/5505)
- **热点PR: `#4622`: 新增DataPaw数据分析插件**：带有 `[first-time-contributor, Under Review]` 标签，社区成员贡献的包含12个BI技能的插件，展现了生态扩展的活跃度。
    - [查看PR](https://github.com/agentscope-ai/QwenPaw/pull/4622)

### 5. Bug 与稳定性

今日报告的Bug按严重程度排列如下：

- **严重 - 核心功能崩溃/资源泄漏:**
    - `#5379`: Python安装后启动即报 `Internal Server Error`，疑似与网络相关，影响首次使用。 ([详情](https://github.com/agentscope-ai/QwenPaw/issues/5379))
    - `#5520` (高热度): `browser_use stop()` 方法无法完全清理Chrome子进程，导致内存泄漏。此问题为 `#2733` 的回归。**[无fix PR]** ([详情](https://github.com/agentscope-ai/QwenPaw/issues/5520))
    - `#5479`: >500KB的大会话文件前端的打开直接崩溃，无法渲染，影响重度用户的历史会话管理。**[无fix PR]** ([详情](https://github.com/agentscope-ai/QwenPaw/issues/5479))
    - `#5162`: 对话思考逻辑进入死循环，核心AI交互Bug。**[无fix PR]** ([详情](https://github.com/agentscope-ai/QwenPaw/issues/5162))

- **中等 - 功能异常：**
    - `#5505`: MiniMax-M3模型因安全审核误判导致后续视觉请求被错误剥离。**[无fix PR]** ([详情](https://github.com/agentscope-ai/QwenPaw/issues/5505))
    - `#5543` & `#5472`: Tool schemas中的 `"type":"null"` 或 `$ref` 导致特定模型（如GLM、第三方代理）调用失败。**[对应PR #5545 #5496]** ([详情#5543](https://github.com/agentscope-ai/QwenPaw/issues/5543), [#5472](https://github.com/agentscope-ai/QwenPaw/issues/5472))
    - `#5539`: 内置心跳任务因硬编码的120秒超时而失败。**[无fix PR]** ([详情](https://github.com/agentscope-ai/QwenPaw/issues/5539))
    - `#5528`: 在带有IME包装器的Linux桌面环境中，`browser_use` 启动失败。**[无fix PR]** ([详情](https://github.com/agentscope-ai/QwenPaw/issues/5528))

- **低 - UI/UX问题：**
    - `#5508`: `send_file_to_user` 在Windows本地App的文件预览链接返回404。**[无fix PR]** ([详情](https://github.com/agentscope-ai/QwenPaw/issues/5508))
    - `#5529`: 内置 `/new` 命令与自定义技能`/news` 自动补全冲突。**[无fix PR]** ([详情](https://github.com/agentscope-ai/QwenPaw/issues/5529))
    - `#5501`: 宽屏模式下聊天窗口发送按钮对齐问题。**[无fix PR]** ([详情](https://github.com/agentscope-ai/QwenPaw/issues/5501))

### 6. 功能请求与路线图信号

- **高优先级信号 - 模型/提供商管理增强：**
    - `#5527`、`#5342`、`#2188`: 多个Issue均反映了对模型管理更高级功能的需求，包括 **模型动态切换**（负载均衡/故障转移）、**工具结果大小硬限制** 以防止上下文爆炸，以及支持**新式的Responses API格式**。这表明用户正在生产环境中使用CoPaw，并遇到了可靠性和扩展性问题。
- **新功能信号 - 插件与集成：**
    - `PR #4622`: DataPaw数据分析插件的提交，表明社区正在积极扩展CoPaw的专业应用场景。这是一个被标记为 `Under Review` 的较大贡献，有可能被纳入下一版本。
    - `Issue #5547`: 用户询问如何在插件工具中获取 `sessionId` 以满足权限控制需求，反映出将CoPaw作为后端服务进行企业级集成的趋势。

### 7. 用户反馈摘要

- **痛点（来自Issue评论）：**
    - **上手体验受阻:** 用户 `luo201227` (Issue #5379) 遭遇直接安装后启动失败，反馈称“直接报错Internal Server Error”，这是体验的致命伤。
    - **可靠性问题：** 用户 `feng183043996` (Issue #5520) 报告浏览器进程泄漏是“regression from #2733”，表示该问题曾被修复但再次出现，对项目维护的持续性和测试覆盖度提出质疑。
    - **惊喜与不便：** 用户 `MiXiaoxiong` (Issue #5508) 在尝试使用 `send_file_to_user` 功能时发现无法预览文件，该功能本身对用户有用，但实现的缺陷影响了整体体验。
    - **配置复杂度：** 用户 `yeyun1999` (Issue #5541) 无法成功配置 Ollama 的 cloud 模型，显示文档或UI引导可能存在不足。

### 8. 待处理积压

以下为长期未关闭或被标记但未获得足够关注的Issue/PR，提醒维护者关注：

- **重要Bug (需优先处理)：**
    - `#5162` [对话死循环] - 自2026-06-12创建，影响核心对话逻辑，无回应。([链接](https://github.com/agentscope-ai/QwenPaw/issues/5162))
    - `#5342` [工具结果硬限制] - 自2026-06-20创建，提出了一个重要的防御性编码特性，提防上下文爆炸导致的级联故障，无合并PR。([链接](https://github.com/agentscope-ai/QwenPaw/issues/5342))
- **长期PR (需Review或决策)：**
    - `#4041` [feat(desktop): Tauri托盘行为] - 自2026-05-05创建，`[Under Review]` 状态已逾一个月，需要一个明确的合并或关闭决定。([链接](https://github.com/agentscope-ai/QwenPaw/pull/4041))
    - `#4622` [feat(datapaw): 数据分析插件] - 同上，是一个较大的社区贡献，需要更深入的设计review。([链接](https://github.com/agentscope-ai/QwenPaw/pull/4622))

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

好的，作为 ZeroClaw 项目的 AI 智能体与个人 AI 助手领域开源项目分析师，以下是基于 2026-06-26 数据生成的 ZeroClaw 项目动态日报。

---

## ZeroClaw 项目动态日报 (2026-06-26)

### 1. 今日速览

今日项目活跃度**极高**，社区贡献和核心维护工作均十分密集。过去24小时内，项目形成了 **38 条 Issue** 和 **50 条 PR** 的大量讨论与处理，显示出强大的社区活力。尽管没有新版本发布，但大量高风险的 RFC（如供应链安全、Wasm 插件运行时）和用户反馈的严重 Bug 正得到积极讨论和修复，表明项目正从功能快速迭代期转向架构优化与稳定性增强的关键阶段。**项目健康度良好，但处理大量高风险议题和堵点 Issue 的能力将是近期关键考验。**

### 3. 项目进展

今日项目在 Bug 修复、功能迭代和发布准备上均有显著推进。以下为已合并/关闭的**重要 PR**：

- **修复与稳定性提升：**
    - **`#8218` [CLOSED]** `fix(agent/history): saturate tool-result trim accounting to avoid underflow panic`：修复了工具结果修剪计算中可能因数据溢出导致的 panic 问题，提升了代理循环的稳定性。
    - **`#8202` [CLOSED]** `[Bug]: refreshed_new_session_system_prompt missing bundled_skill loading...`：修复了用户在开启新会话时，系统提示缺失捆绑的（bundle）技能的问题，修复了“拉取并使用技能”的核心工作流。
    - **`#8219` [CLOSED]** `[Bug]: gpt-oss-120b on Groq fails native multi-turn tool loops...`：修复了在使用 Groq 提供商进行多轮工具调用时，因序列化和参数校验问题导致流程中断的 Bug，增强了兼容性。
    - **`#8265` [CLOSED]** `fix(i18n): translate 22 tool-channel-room-* keys for matrix room tool`：完成了 Matrix 聊天室工具的国际化翻译，提升了非英语用户的体验。
- **发布准备：**
    - **`#8234` [CLOSED]** `chore(release): bump version to v0.8.2 and add changelog`：**重要里程碑**。项目正式将版本号推进至 `v0.8.2` 并更新了变更日志，预示着新版本发布在即。该项目吸纳了此前多个修复和功能。
- **文档与维护：**
    - **`#8341` [OPEN]** `docs(AGENTS.md): sync paths and crate list with current workspace layout`：更新了关于代理开发的官方文档，使其与当前的工作区结构保持一致，降低了新贡献者的入门门槛。
    - **`#8154` [CLOSED]** `[Bug]: Kimi Code ... regression`：快速修复了因 API 端点变更导致的月之暗面（Kimi）模型提供商集成故障。

**项目整体迈向 v0.8.2 版本发布，同时在代理稳定性、提供商兼容性及用户工作流修复方面取得了扎实进展。**

### 4. 社区热点

今日最受关注的议题主要集中在项目治理和未来架构大方向的选择上，反映了社区核心成员对项目长期健康发展的深度思考。

- **`#8177` [OPEN]** `RFC: Supply chain signing - hardware PGP, hermetic builds, and SLSA provenance` (评论: 8)
    - **链接:** [Issue #8177](https://github.com/zeroclaw-labs/zeroclaw/issues/8177)
    - **诉求分析:** 该 RFC 提议为项目引入供**应链安全**机制，包括硬件 PGP 密钥、SLSA 溯源证明等。这是当前云原生和区块链领域高度重视的安全实践，社区的广泛参与表明用户和贡献者对 ZeroClaw 的**生产环境可信度**有很高期待。项目若采纳此 RFC，将极大提升其作为严肃企业级基础设施的信誉。

- **`#6808` [OPEN]** `RFC: Work Lanes, Board Automation, and Label Cleanup` (评论: 11)
    - **链接:** [Issue #6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808)
    - **诉求分析:** 这是今日评论数最多的 Issue。该 RFC 提出优化项目管理流程，包括引入工作泳道、自动化看板管理和标签清理。这表明核心贡献者（特别是 `Audacity88`）在主动倡导**更高效、更透明的项目治理模式**，旨在降低维护负担，引导社区贡献更有序地进行。这是项目从快速成长走向成熟管理的必要信号。

### 5. Bug 与稳定性

今日报告的 Bug 覆盖了运行时、配置、安全等多个方面，其中**严重性为 S1（工作流受阻）的 Bug 被快速关闭**，显示了良好的修复响应速度。

- **严重风险 (S0 - 数据丢失/安全风险):**
    - **`#8279` [CLOSED]** `[Bug]: delegate bypasses parent's tool allowlist`: 报告称“delegate”工具会绕过父级的安全策略，允许子代理调用父级策略中排除的工具。这是一个严重的安全漏洞，已于另一 Issue `#7743` 中跟踪处理，并已关闭。
- **阻断/阻塞风险 (S1 - 工作流受阻):**
    - **`#8202` [CLOSED]**：新会话技能加载失败。已修复。
    - **`#8219` [CLOSED]**：Groq 提供商多轮工具调用失败。已修复。
    - **`#8154` [CLOSED]**：月之暗面（Kimi）提供商 API 端点回归。已修复。
- **主要功能退化 (S2 - 行为退化):**
    - **`#8312` [OPEN]** `[Bug]: fill-translations leak-repair leaves stale translations-map entries...`：报告了一个新的文本数据泄露路径，涉及翻译修复工具。
    - **`#8334` [OPEN]** `[Bug]: skills install/list/remove target data_dir, which no multi-agent runtime loads`：报告称多代理环境下，技能安装、列表和删除等 CLI 命令指向了错误的配置目录，导致“拉取并安装技能”的核心体验在多代理场景下失效。

**总结:** 安全问题是今日的重中之重。供应商回归问题得到了快速处理，但一些底层的配置和翻译工具 Bug 仍需关注。

### 6. 功能请求与路线图信号

今日最引人注目的功能请求集中于**架构重构与安全基建**，这预示着未来版本将发生根本性变化：

- **Wasm 优先与插件安全：**
    - **`#8135` [OPEN]** `RFC: Wasm-first plugin runtime`: 提议将 WebAssembly (Wasm) 作为默认插件运行时，强调能力强制和安全分发。这很可能成为 `v0.9.0` 的核心特性，旨在彻底解决原生插件带来的安全性和依赖性问题。
    - **`#8132` [OPEN]** `RFC: Replace React/Vite web UI build with Rust→Wasm framework`: 提议用 Rust 编译为 Wasm 的框架（如 Dioxus/Leptos 等）替换当前的 React/Vite Web UI，以求消除对 Node.js 构建环境的依赖。
- **代理执行与配置增强：**
    - **`#8238` [OPEN]** `[Feature]: Add independent delegate mode`：在 `#7743` 和 `#7514` 的基础上，进一步要求添加独立的“代理委托”模式，允许专门 Agent 使用自己的策略和工具集，而不是被父级策略完全限制。这与当前的安全策略讨论紧密相关。
    - **`#8138` [OPEN]** `Support OpenRouter model fallbacks array`: 提议为 OpenRouter 提供商增加模型故障转移支持，这点通常会被社区高优先级处理。
    - **`#8173` [OPEN]** `feat(gateway): in-app upgrade with auto-restart from the web dashboard`: 一个支持性的大型 PR，实现了从 Web 仪表盘进行应用内升级和自动重启的功能，极大提升了运维便利性。

**路线图信号：** 项目正在酝酿一次重大的**基础设施升级**，重心转向**安全、模块化（Wasm）和消除复杂构建依赖**。用户对于代理的灵活性和自我管理能力（如独立委托模式、模型故障转移）的需求也显著增加。

### 7. 用户反馈摘要

从 Issues 评论中提炼的关键信息：

- **配置困惑:** 用户 `#8334` 报告，`skills install` 等 CLI 命令在多代理环境中失效，对文档与实现不一致感到困惑：“`skills install` 目标 `data_dir`，而多代理运行时并不加载该目录”。
- **寻求更好的集成:** 用户 `#6165` 提议通过轻量化核心和外部技能集（Skills）的交互，简化项目对 Jira、Github 等服务的原生集成代码，这反映了对项目架构简洁性（“不要”过多的内建服务）的长期诉求。
- **对安全交付的紧迫感:** 在 `#8177`（供应链签名）的评论中，部分核心贡献者讨论了**离线签名、多仲裁方**等复杂流程，显示出社区对提供一个**可信、防篡改**的产品非常认真，这可能是商业或安全敏感用户的强烈需求。

### 8. 待处理积压

以下为长期未解决或关键路径上需要维持者关注的 Issue 和 PR：

- **`#5903` [OPEN 超过 2 个月]** `[Bug]: MCP stdio child processes accumulate on daemon`: 长期的 MCP 子进程泄露问题。虽已被标记为接受（accepted），但至今无 fix PR 被合并。
    - **链接:** [Issue #5903](https://github.com/zeroclaw-labs/zeroclaw/issues/5903)
- **`#6165` [OPEN 约 2 个月]** `RFC: Prefer a lighter ZeroClaw core through external integrations`: 关于核心瘦身和外部集成重构的 RFC，尽管讨论活跃，但陷入停滞，可能影响未来代码清理。
    - **链接:** [Issue #6165](https://github.com/zeroclaw-labs/zeroclaw/issues/6165)
- **`#8132` / `#8135` / `#8177` [OPEN 约 4 天]**：**这几条近期的高风险 RFC（替换 UI、Wasm 插件运行时、供应链签名）被标记为 `blocked` 或 `needs-maintainer-review`。它们涉及项目的根本性架构变革，需要维护者的明确方向性决策，以避免社区贡献者的重复劳动。
    - **链接 1:** [Issue #8132](https://github.com/zeroclaw-labs/zeroclaw/issues/8132)
    - **链接 2:** [Issue #8135](https://github.com/zeroclaw-labs/zeroclaw/issues/8135)
    - **链接 3:** [Issue #8177](https://github.com/zeroclaw-labs/zeroclaw/issues/8177)
- **`#7846` [OPEN 约 9 天]** `feat(runtime): wire before_llm_call hook into LLM call paths`：这是一个风险高但影响深远的功能，旨在允许在代理 LLM 调用前插入自定义钩子。该 PR 处于潜在的久置风险中。
    - **链接:** [PR #7846](https://github.com/zeroclaw-labs/zeroclaw/pull/7846)

</details>

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*