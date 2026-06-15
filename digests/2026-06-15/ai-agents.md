# OpenClaw 生态日报 2026-06-15

> Issues: 500 | PRs: 500 | 覆盖项目: 13 个 | 生成时间: 2026-06-15 04:13 UTC

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

好的，作为AI智能体与个人AI助手领域开源项目分析师，根据您提供的OpenClaw项目数据，我为您生成了以下项目动态日报。

---

# OpenClaw 项目日报 (2026-06-15)

## 今日速览

项目今日维持高活跃度，24小时内处理了500条Issues和500条PR，显示出社区的高度参与。新版本`v2026.6.8-beta.1`已发布，重点改进了Telegram和WhatsApp的消息投递稳定性与丰富性。然而，活跃的Issues中有大量P1优先级的回归问题，主要集中在Matrix、Telegram、Discord等渠道的会话状态、消息丢失和投递异常上，提示近期更新引入了一些关键的稳定性和行为退化问题。维护团队正在积极通过PR修复，但积压的待合并PR数量庞大，可能成为瓶颈。

- **活跃度**: 🔥 极高
- **健康度**: 🟡 一般。功能迭代活跃，但存在多个严重的、影响核心通信渠道的回归问题，稳定性面临挑战。

## 版本发布

### [v2026.6.8-beta.1](https://github.com/OpenClaw/OpenClaw/releases/v2026.6.8-beta.1)

**主要更新内容**:
1.  **Telegram & WhatsApp 渠道增强**:
    -   **Telegram**: 现在可以发送包含表格、列表、可展开块引用的结构化富文本消息。CLI后端投递更稳定，并支持保留提示词的投递。废弃的原生草稿已迁移，富媒体边界处理更安全。
    -   **WhatsApp**: (摘要未显示详情，但标题提示其投递韧性也得到增强)。
2.  **其他**:
    -   涉及对该版本的多项内部修复和优化。

**破坏性变更 & 迁移注意事项**:
- 未明确提及破坏性变更。但用户升级后应密切关注Telegram和WhatsApp的消息格式、投递行为和草稿同步是否正常。
- `v2026.6.x` 系列版本发布较为频繁，建议用户在非生产环境先行测试。

## 项目进展

今日合并/关闭的PR相对较少，大量PR仍处于开放或等待作者/审核状态。重点推进如下：

- **[#93153](https://github.com/OpenClaw/OpenClaw/pull/93153) - Simplify QA evidence coverage shape**: 简化了QA证据的数据结构，有助于降低测试维护成本。
- **[#87298](https://github.com/OpenClaw/OpenClaw/pull/87298) - test: add temp directory helper guidance**: 已关闭。为测试框架增加了临时目录的帮助器，并配有迁移指南，提升了测试的健壮性和可维护性。

项目向前迈进的步伐稳健，但主要侧重于内部工程化（测试、QA流程）的优化，而非直接修复当前最紧迫的终端用户问题。

## 社区热点

今日最活跃的Issues反映了用户对核心渠道稳定性和AI交互可靠性的深切关注：

1.  **Matrix 线程回复回归 ([#87307](https://github.com/OpenClaw/OpenClaw/issues/87307))**:
    -   **热度**: 14条评论，1个👍。
    -   **核心诉求**: 用户升级到`2026.5.22`后，Matrix的线程回复功能退化，AI的回复变成了普通回复，且`/status`和`/model`命令失效。这是一个明确的回归问题，用户希望恢复原有行为。
2.  **MiniMax Cron任务在特定时段持续失败 ([#85888](https://github.com/OpenClaw/OpenClaw/issues/85888))**:
    -   **热度**: 12条评论，1个👍。
    -   **核心诉求**: 定时Cron任务在北京时间凌晨5-7点半持续报MiniMax API过载错误，而手动触发却能成功。这表明错误可能源于OpenClaw的调度或重试机制，而非API本身。用户要求排查调度逻辑。
3.  **Codex Agent回复被静默截断 ([#84516](https://github.com/OpenClaw/OpenClaw/issues/84516))**:
    -   **热度**: 11条评论，2个👍。
    -   **核心诉求**: 使用Codex/OAuth Agent时，回复被静默截断在1000-1100字符。这是一个严重的消息丢失问题，用户要求查明截断原因并恢复完整的回复功能。
4.  **Telegram Agent重复回复 ([#86519](https://github.com/OpenClaw/OpenClaw/issues/86519))**:
    -   **热度**: 9条评论，1个👍。
    -   **核心诉求**: 自`v2026.5.20`更新后，Agent在Telegram上对单一用户消息重复回复2-10次。`v2026.5.22`版本部分缓解但未完全修复。用户急需一个完整的修复。

**分析**: 社区焦点高度集中在近期更新（`v2026.5.20`, `v2026.5.22`）引入的回归问题上，这些问题直接影响了核心IM渠道的可用性和用户期望的AI交互行为。用户普遍反馈“本可正常工作，升级后反而出问题”，显示出对软件稳定性的担忧。

## Bug 与稳定性

今日报告的Bug数量众多，影响面广。以下为按严重程度排列的关键问题：

**P1 (严重/阻塞)**:

-   **会话状态 & 消息丢失类**:
    -   **Matrix 线程回复退化** - [#87307](https://github.com/OpenClaw/OpenClaw/issues/87307) (无Fix PR)
    -   **Codex Agent回复被静默截断** - [#84516](https://github.com/OpenClaw/OpenClaw/issues/84516) (无Fix PR)
    -   **Telegram 重复回复** - [#86519](https://github.com/OpenClaw/OpenClaw/issues/86519) (无Fix PR)
    -   **Codex App-Server在低延迟下中断** - [#86996](https://github.com/OpenClaw/OpenClaw/issues/86996) (无Fix PR)
    -   **Discord 会话被接管错误** - [#86508](https://github.com/OpenClaw/OpenClaw/issues/86508) (无Fix PR)
    -   **模型Fallback链失效** - [#85103](https://github.com/OpenClaw/OpenClaw/issues/85103) (无Fix PR)
    -   **会话写锁超时阻塞子Agent** - [#86538](https://github.com/OpenClaw/OpenClaw/issues/86538) (有[Fix PR链接](https://github.com/OpenClaw/OpenClaw/pull/88968))
    -   **Codex App-Server 木马执行超时** - [#86047](https://github.com/OpenClaw/OpenClaw/issues/86047) (无Fix PR)
    -   **单个Agent会话堵塞Gateway事件循环** - [#84903](https://github.com/OpenClaw/OpenClaw/issues/84903) (无Fix PR)
-   **认证/授权类**:
    -   **Control UI自动选择错误认证Profile** - [#85126](https://github.com/OpenClaw/OpenClaw/issues/85126) (无Fix PR)
    -   **MCP工具未注入subagent** - [#85030](https://github.com/OpenClaw/OpenClaw/issues/85030) (无Fix PR)
    -   **Codex OAuth刷新失败导致Agent死锁** - [#86215](https://github.com/OpenClaw/OpenClaw/issues/86215) (无Fix PR)

**P2 (中等)**:

-   **Amazon Bedrock Haiku 4.5推理Profile ARN不支持** - [#87318](https://github.com/OpenClaw/OpenClaw/issues/87318)
-   **过时工具调用活动阻塞会话** - [#87310](https://github.com/OpenClaw/OpenClaw/issues/87310)
-   **内存压缩的Token阈值对模型切换不友好** - [#87136](https://github.com/OpenClaw/OpenClaw/issues/87136)
-   **心跳驱动的Agent回复卡死** - [#83184](https://github.com/OpenClaw/OpenClaw/issues/83184) (有[Fix PR链接](https://github.com/OpenClaw/OpenClaw/pull/88992))

**有Fix PR的Bug**: 部分问题已有对应的修复PR，如#86538、#83184、以及标题中提到的`clawsweeper:linked-pr-open`标签的Issues。这表明维护团队正在积极处理，但PR的合并流程需要加速。

## 功能请求与路线图信号

-   **Gateway-lite模式 ([#86881](https://github.com/OpenClaw/OpenClaw/issues/86881))**：用户请求一个不依赖AI的轻量级Gateway模式，用于处理Webhook、Cron等确定性任务。这与项目的模块化愿景相符，可能会在未来版本中作为低优先级功能考虑。

-   **任务流生命周期Hook ([#87362](https://github.com/OpenClaw/OpenClaw/issues/87362))**：用户希望插件能够监听任务流的生命周期事件，以实现可观测性。对应的PR[#87377](https://github.com/OpenClaw/OpenClaw/pull/87377)已经提出，这是一个从功能请求到实施的积极信号，有望在后续版本中落地。

-   **Slash命令控制流模式 ([#74077](https://github.com/OpenClaw/OpenClaw/issues/74077))**：一个长期存在的功能请求，希望添加一个`/stream`命令来动态切换会话的预览流模式，方便用户在不重载配置的情况下调整体验。

-   **Model Failover和Terminal Failure Hooks ([#70990](https://github.com/OpenClaw/OpenClaw/pull/70990))**：一个XL规模的PR，为插件增加了模型故障转移和终端失败的钩子。这是一个成熟度较高的功能，如果合并，将极大增强系统的容错能力和可观测性。

-   **Compaction Fallback Model Chain ([#93125](https://github.com/OpenClaw/OpenClaw/pull/93125))**：一个M规模的PR，新增了内存压缩时的模型回退链配置，以应对模型限流或错误。这表明项目正在持续优化内存管理的健壮性。

## 用户反馈摘要

从今日的Issues评论中，可以提炼出以下用户反馈：

-   **最核心的痛点**：**升级后引入的回归问题**。多位用户强调“升级前能用，升级后不能用”，尤其是在`v2026.5.20`和`v2026.5.22`版本后，Telegram、Matrix等渠道出现了严重的消息重复、丢失和截断问题。这导致用户对更新产生信任危机，部分用户选择回滚。
-   **使用场景**：用户广泛应用OpenClaw连接多个IM渠道（Telegram, Discord, Matrix, WhatsApp等）作为个人AI代理。Cron任务和自动化调度是高频使用场景。
-   **不满意的点**：**静默失败**是最大的不满。Agent回复被截断、会话卡死后不通知用户、模型Fallback链未生效等，都导致用户不知道发生了什么，且难以排查。诊断信息和错误提示的缺乏是普遍问题。
-   **满意的点**：从功能请求可以看出，用户对OpenClaw的扩展性和模块化设计有期待，愿意提出像“Task Flow Hook”和“Gateway-lite”这样的高级功能。这表明核心用户对项目有信心，并希望它变得更强大。

## 待处理积压

以下是一些长期未响应或状态停滞的重要Issue/PR，需要维护者关注：

1.  **[#44395](https://github.com/OpenClaw/OpenClaw/issues/44395) - feat: heading-aware chunking + entity extraction for memory search (创建于 2026-03-12)**: 这是一个重要的内存搜索增强功能，为语义分割提供了更好的逻辑。3个月未解决，可能已被主分支的未来计划取代或需要重新评估。
2.  **[#45494](https://github.com/OpenClaw/OpenClaw/issues/45494) - [Bug]: Cron agent jobs silently time out (创建于 2026-03-13)**: 一个长期的P1回归Bug，Cron任务在API故障时不断超时而非快速失败。至今未有修复，可能影响了许多用户的自动化流程。
3.  **[#74077](https://github.com/OpenClaw/OpenClaw/issues/74077) - Feature: slash command to set preview streaming mode (创建于 2026-04-29)**: 一个已标记为“stale”的功能请求，但来自核心贡献者（ClawSean），设计良好。如果项目路线图计划探索动态用户体验，此功能值得重新激活。
4.  **[#79818](https://github.com/OpenClaw/OpenClaw/pull/79818) - feat(slack): expand message action parity (创建于 2026-05-09)**: 一个XL规模的PR，旨在扩展Slack消息操作的丰富性。状态长期为“🚀 automerge armed”，但始终未合并。可能因风险或冲突而被搁置，需要审核人给出明确反馈。
5.  **[#73399](https://github.com/OpenClaw/OpenClaw/pull/73399) - fix(feishu): carry forward DM fallback and topic labels (创建于 2026-04-28)**: 同#79818，状态为“🚀 automerge armed”但未合并。这些自动合并队列中的PR需要优先处理，以避免长期积压。

**总结**：OpenClaw项目今日展现了极强的社区活跃度，但也暴露了近期版本在稳定性方面的明显短板。维护者需要优先处理和修复当前最严重的P1回归问题，并审查自动合并队列中的积压。对于长期未决的用户诉求，应给予明确回应。

---

## 横向生态对比

好的，基于您提供的各项目2026-06-15动态数据，我为您生成了这份横向对比分析报告。

---

### 个人 AI 助手/自主智能体开源生态横向对比分析报告 (2026-06-15)

#### 1. 生态全景

当前个人AI助手开源生态正处于**功能深化与稳定性阵痛并存**的快速成长期。各项目均展现出极高的社区活跃度，核心功能（多渠道IM集成、多模态、Agent自动化）趋于完善。然而，这种高速迭代也带来了普遍的**稳定性挑战**，多个头部项目（如OpenClaw、Hermes Agent）均因近期更新引入了严重的回归问题，导致用户体验下降，显示出社区对新功能的渴望与对软件鲁棒性更高要求之间的矛盾。同时，**安全审计**与**企业级合规**开始成为不可忽视的议题，标志着生态正从个人极客工具向更广泛的生产力场景过渡。

#### 2. 各项目活跃度对比

| 项目名称 | 24h Issues | 24h PRs | 版本发布 | 健康度评估 |
| :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 500 | 500 | v2026.6.8-beta.1 | 🟡 一般 (高活跃，但存在大量严重的P1回归问题) |
| **NanoBot** | - | 27 (合并) | 无 | 🟢 健康 (高活跃，修复与重构并进) |
| **Hermes Agent** | 100+ (含PR) | 7 (合并) | 无 | 🟡 一般 (极高活跃，但安全问题与稳定性Bug集中披露) |
| **IronClaw** | 43 | 48 | 无 | 🟢 健康 (极高活跃，聚焦新架构打磨与安全加固) |
| **NullClaw** | 1 | 0 | 无 | 🟢 平稳 (低活跃，无Bug，社区需求明确) |
| **LobsterAI** | 2 | 0 (合并2) | 无 | 🟢 平稳 (中低活跃，核心功能增强，但存在积压) |
| **PicoClaw** | 5 | 9 (合并5) | Nightly | 🟢 健康 (活跃，代码质量改进和Bug修复为主) |
| **NanoClaw** | 7 | 10 (合并5) | 无 | 🟢 健康 (高活跃，功能推进与安全加固并行) |
| **ZeroClaw** | - | - | 无 | 🟡 一般 (高活跃，功能迭代快，但PR积压严重，存在技术债风险) |
| **CoPaw (QwenPaw)** | 41 | 6 (合并) | 无 | 🟡 一般 (极高活跃，大量Bug反馈，稳定性受挑战) |
| **Moltis** | 1 | 0 | 无 | 🟢 平稳 (低活跃，单一功能请求) |
| **TinyClaw** | 0 | 0 | 无 | - (无活动) |
| **ZeptoClaw** | 0 | 0 | 无 | - (无活动) |

#### 3. OpenClaw 在生态中的定位

OpenClaw 在生态中扮演着**社区规模最大、功能最全面的“旗舰级”参照项目**角色。其优势在于极其庞大的社区贡献量和快速的功能迭代，尤其是在Telegram/WhatsApp等核心IM渠道的消息丰富性上领先。然而，正因其体量大、迭代快，也使其成为生态中**稳定性风险最高的项目**之一。相比NanoBot和PicoClaw等更侧重于“小而美”、架构轻量的项目，OpenClaw的功能堆叠带来了更复杂的依赖和更高的回归概率。它代表了“功能优先”的路线，而IronClaw则代表了“架构与设计优先”的路线（通过“Reborn”架构进行深度重构）。

#### 4. 共同关注的技术方向

多个项目不约而同地涌现出相同或相似的需求，反映了行业的普遍痛点：

- **安全问题与认证授权加强**:
    - **Hermes Agent** (#46411, #46413): 文件读取越权、凭证泄露。
    - **NanoClaw** (#2760, #2761, #2762): `send_file` 路径泄露、Webhook认证绕过、MCP审批隐藏参数。
    - **IronClaw** (#4865, #4864): Shell批准边界绕过。
    - **ZeroClaw** (#5842): `extra_args` 安全影响追踪。
    - **NullClaw** (#955): 请求企业级身份认证支持。
- **自动化调度与任务可靠性**:
    - **OpenClaw** (#85888, #45494): Cron任务在特定时段失败、超时。
    - **Hermes Agent** (#32091): 非默认profile下的Cron任务丢失。
    - **CoPaw** (#5174): 定时/心跳Agent无法完成复杂任务。
    - **ZeroClaw** (#7384): 实现Cron任务的暂停/恢复管理。
- **Agent行为可观测性与调试信息**:
    - **OpenClaw**: 用户普遍抱怨“静默失败”，缺乏诊断信息。
    - **Hermes Agent** (#46090): 任务变得“极度缓慢”但原因不明。
    - **IronClaw** (#4852): Shell执行过程不透明。
    - **CoPaw** (#5009): 询问是否支持Langfuse等可观测性平台。
- **多模型/多渠道生态整合**:
    - **NullClaw** (#955): 请求Azure OpenAI身份认证。
    - **OpenClaw** (#70990): 模型故障转移和终端失败Hook。
    - **CoPaw** (#5182): 请求统一文本、向量、音视频模型配置。
    - **PicoClaw** (#2978): 希望添加 `omniroute` 等更多AI提供商。

#### 5. 差异化定位分析

| 项目 | 核心差异化 | 目标用户 | 技术架构特点 |
| :--- | :--- | :--- | :--- |
| **OpenClaw** | **功能广度与IM渠道深度** | 想要连接一切（Telegram, Matrix, Discord等）、追求功能全面的重度用户。 | 组件化、插件丰富，但架构耦合度高，回归风险大。 |
| **NanoBot** | **轻量高效、API兼容** | 注重性能、喜欢自定义、需要作为后端集成的开发者。 | 模块化、配置驱动，重构活跃（如解耦配置模型）。 |
| **Hermes Agent** | **多功能Agent与安全** | 对Agent自主性、安全问题敏感的高级用户和开发者。 | 功能集庞大，但安全漏洞和并发稳定性问题较为突出。 |
| **IronClaw** | **架构设计驱动** | 关注长期架构健壮性、对未来可扩展性要求高的开发者。 | 强调明确类型安全和信任链，通过“Reborn”架构进行根本性重构。 |
| **ZeroClaw** | **第三方集成速度** | 想要快速接入SMS、智能家居等特定生态的用户。 | 第三方集成响应快，但PR积压和技术债问题值得警惕。 |
| **CoPaw (QwenPaw)** | **企业级通讯与自动化** | 关注飞书、钉钉等国内企业通讯软件集成及自动化任务的组织用户。 | 对国内模型（Kimi）和企业应用集成度高，但在Windows端存在稳定性问题。 |
| **LobsterAI** | **文档与协同办公** | 需要在AI交互中深度集成文档（DOCX, PDF等）预览、分享的用户。 | 聚焦于办公场景的文档协作能力。 |
| **PicoClaw/NanoClaw** | **（推测）轻量、可扩展** | 喜欢动手、追求部署灵活性的开发者。 | PR数量显示代码质量改进和功能扩展并存。PicoClaw在探索远程Agent模式。 |

#### 6. 社区热度与成熟度

- **极高活跃与快速迭代阶段**: **OpenClaw**, **NanoBot**, **Hermes Agent**, **IronClaw**, **CoPaw**, **NanoClaw**。这些项目社区投入巨大（每日数十甚至上百PR/Issue），新功能和Bug修复同步涌现。但普遍伴随着稳定性挑战，处于“摸着石头过河”的快速扩张期。
- **活跃与质量巩固阶段**: **PicoClaw**, **ZeroClaw**。PicoClaw更侧重于代码质量（如显式处理边缘Error）和插件化扩展。ZeroClaw虽活跃，但PR积压和技术债问题可能正在拖慢其从“功能堆叠”向“质量优先”的转型。
- **平稳与功能性打磨阶段**: **LobsterAI**, **NullClaw**。项目活跃度较低，但社区反馈更聚焦于特定功能的缺失或增强，而非普遍性的稳定性问题，表明核心功能相对成熟。
- **停滞或低活跃**: **Moltis**, **TinyClaw**, **ZeptoClaw**。这些项目社区互动极少，可能处于维护期或探索性阶段。

#### 7. 值得关注的趋势信号

1.  **从“功能有无”转向“安全合规与工程效率”**: 社区反馈的重心正从“能不能做”转向“安不安全”、“稳不稳定”。要求企业级认证（NullClaw）、发现Shell绕过漏洞（IronClaw）、以及利用AI项目自身提升工程效率（IronClaw的“AI-native”提案），都标志着行业正在走向成熟。
2.  **“智能化”触发自动化的期望升级**: 用户不再满足于简单的Cron轮询（CoPaw #5174），而是期望Agent能“自主地”感知环境、管理状态、完成多步骤的复杂任务。定时任务和心跳Agent的“不自动”，暴露了当前Agent内核在实现真正自主性上的普遍瓶颈。
3.  **“付费墙”与多模型接入的矛盾激化**: 用户对已有付费订阅（如Kimi coding套餐、Claude Pro）无法在开源项目中使用感到沮丧（CoPaw #5156, Hermes #25267）。这催生了社区对**模型接入方式的灵活性**（如OAuth、身份认证）的强烈需求，是推动项目走向更广泛用户必须跨越的门槛。
4.  **项目运营的“次生问题”成为风险**: 积压的PR（ZeroClaw）、被标志为“陈旧”的功能请求（LobsterAI）、以及丢失的commit记录（ZeroClaw #6074），这些项目自身的工程管理和运营问题，正在成为社区信任的消耗点，其影响不亚于代码Bug。优秀的开源项目不仅需要代码，也需要健康的治理流程。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

好的，这是为您生成的 NanoBot 项目动态日报 (2026-06-15)。

---

# NanoBot 项目动态日报 — 2026-06-15

## 1. 今日速览

项目活跃度极高，24小时内合并/关闭了27个PR，并有19个新PR待审，显示出强劲的开发马力。社区修复热情高涨，特别是针对图像回退逻辑泄露路径和API兼容性的两个Bug已被迅速修复。同时，大型重构如配置模型解耦和Agent循环边界优化正在推进，表明项目正为更稳定的架构打下基础。WebUI的完善工作也在持续，移动端响应式设计和设置面板的补齐让用户体验更上一层楼。

## 2. 版本发布

无

## 3. 项目进展

过去24小时是项目快速整合功能与修复的密集期，共有**27个PR被合并/关闭**，以下是几项关键进展：

- **架构改良**：`#4314` 和 `#4344` 分别针对工具配置模型和Agent循环边界进行了深度重构。这解开了导入循环，并将运行时依赖与核心配置分离，为后续扩展提供了更清晰的模块边界。([#4314](https://github.com/HKUDS/nanobot/pull/4314), [#4344](https://github.com/HKUDS/nanobot/pull/4344))
- **Agent机制增强**：`#4269` 优化了Agent在达到最大工具迭代次数时的提示逻辑，即使没有工具调用也会给出最终状态；`#4274` 增加了按会话范围过滤历史记录的功能，提升了多会话场景下的上下文精确性。([#4269](https://github.com/HKUDS/nanobot/pull/4269), [#4274](https://github.com/HKUDS/nanobot/pull/4274))
- **文档与上手体验**：`#4177` 和 `#4245` 重构了文档入口，使其对初学者更友好，并移除了陈旧的“夜间版”分支指引，简化了贡献流程。([#4177](https://github.com/HKUDS/nanobot/pull/4177), [#4245](https://github.com/HKUDS/nanobot/pull/4245))
- **持续集成与质量**：`#4275` 增加了对无效配置文件“快速失败”的检查，防止因配置错误导致难以定位的问题。同时，`#4248` 修复了Token用量热力图的时区和标签裁剪问题。([#4275](https://github.com/HKUDS/nanobot/pull/4275), [#4248](https://github.com/HKUDS/nanobot/pull/4248))
- **WebUI 完善**：`#4339` 极大地改善了WebUI在移动设备上的显示效果，包括间距、安全区域和组件溢出处理。此外，桌面端的重启令牌和重放间隙问题 (`#4210`) 也得到了修复。([#4339](https://github.com/HKUDS/nanobot/pull/4339), [#4210](https://github.com/HKUDS/nanobot/pull/4210))

## 4. 社区热点

- **WebUI与配置全面对齐**：PR `#4313` (Feat(webui): config.json/webui parity) 在讨论和评论中获得了高度关注。该PR旨在弥合WebUI设置界面与`config.json`之间的功能差距，新增了温度、工具限制等多项写入端口。这反映了社区对“无需手动编辑配置文件，即可完成所有操作”的强烈期待，是提升产品成熟度和用户友好度的关键一步。([#4313](https://github.com/HKUDS/nanobot/pull/4313))

- **图像回退逻辑导致路径泄露**：Issue `#4345` 报告了一个严重的安全隐患，指出图像回退机制在失败时会将文件路径泄露给模型。该问题迅速获得了贡献者 `BearMett` 的关注，并立即提交了修复PR `#4346`，形成了“问题发现-修复-合并”的高效闭环，体现了社区的高响应能力。([#4345](https://github.com/HKUDS/nanobot/issues/4345), [#4346](https://github.com/HKUDS/nanobot/pull/4346))

## 5. Bug 与稳定性

- **严重：图片路径泄露** (`#4345`)：图像回退机制 (`_strip_image_content`) 在替换图像后，会向模型插入包含原始文件路径的文本，构成信息泄露风险。**已有修复PR (`#4346`) 跟进。**
- **中等：API 返回固定零 Token 使用量** (`#4309`)：`/v1/chat/completions` 端点始终返回0 Token消耗，破坏了计费和用量监控功能。**状态：待处理，尚无修复PR。**
- **中等：Anthropic 提供者温度参数兼容** (`#4333`)：向`claude-opus-4-8`等模型发送已废弃的`temperature`参数，导致请求被API拒绝。**已于6月14日关闭，推测已通过修复或模型配置调整解决。**
- **轻微：Telegram 代码块截断** (`#4250`)：长消息分割时，可能将围栏代码块 (` ``` `) 分割到不同消息中，导致显示混乱。**已于6月14日关闭，问题得到解决。**

## 6. 功能请求与路线图信号

- **自动化管理视图**：PR `#4330` (feat(webui): add automation management view) 增加了WebUI端的自动化任务列表、筛选、启停和删除功能。这表明项目正朝着提供更强大的“低代码”或“可视化”自动化管理能力迈进，是平台化的关键功能。([#4330](https://github.com/HKUDS/nanobot/pull/4330))
- **配置编辑器**：`#4313` 中关于WebUI/`config.json`功能对等的工作，暗示了未来可能内置一个更完整的配置编辑器，让用户无需手动编辑JSON即可进行高级设置。
- **Agent 模式 Bot 图标**：Issue `#4262` 请求在Agent模式启动时即显示用户自定义的`botIcon`，而非默认图标。该请求虽小，但提升了个人化体验，反映了用户对细节定制的需求。([#4262](https://github.com/HKUDS/nanobot/issues/4262))

## 7. 用户反馈摘要

- **图像处理的悖论**：用户 `BearMett` 发现了一个精巧的矛盾点：模型的图像回退逻辑本身是好的（防止模型因图像错误而崩溃），但它产生的替代文本却带来了新的（且更严重的）问题（路径泄露）。这反映了社区贡献者不仅在使用，更在深入分析功能实现逻辑，并提出建设性的改进方案。
- **API 兼容性痛点**：`alx1379` 报告的 `/v1/chat/completions` 零Token问题 (`#4309`) 直指与OpenAI生态工具的兼容性，这是影响集成体验的核心痛点，对于需要精确计费的场景（如企业用户）尤为致命。
- **新模型适配烦恼**：`Ulef1005` 在使用新发布的 Anthropic `opus-4-8` 模型时遇到了400错误，反映出项目对新模型的适配可能存在滞后，用户在尝试最新功能时容易受阻。

## 8. 待处理积压

- **`#4309`: `/v1/chat/completions` 返回零Token**：作为一个影响API生态兼容性的Bug，此问题已存在4天且暂无修复PR。建议维护者优先评估，这可能是一个小而关键的计算问题。([#4309](https://github.com/HKUDS/nanobot/issues/4309))
- **`#4344`: 重构配置和Agent循环边界**：该PR虽然影响力大，但重构涉及面广，代码审查和测试周期可能较长。从社区角度看，这是架构健康度提升的关键，值得静待其合并。([#4344](https://github.com/HKUDS/nanobot/pull/4344))

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

好的，这是为您生成的 Hermes Agent 项目动态日报。

---

# Hermes Agent 项目动态日报 | 2026年06月15日

## 1. 今日速览

今日项目活跃度极高，社区提交了大量 Issue 和 PR，显示出用户群体的积极参与度和项目自身的快速发展。

- **社区反馈爆发**：24小时内产生了 100 条 Issue 与 PR 更新，社区反馈异常活跃。关于 `response truncated` 的 Bug 讨论（#7237）在长达两个月后仍在发酵，说明输出长度限制问题对长文生成场景影响严重。
- **安全问题集中披露**：今日集中披露了数项中高危安全问题，涉及文件读取越权（#46411）、凭证泄露（#46413）等，项目组需优先关注。相关 PR (#46422) 已开始尝试解决部分 CI/CD 层面的 token 权限问题。
- **核心稳定性受关注**：多个关于长连接超时（#44560）、会话内存污染（#46303）、网关配置失效（#45963）等 P1/P2 级别的 Bug 被提出并讨论，反映出项目在并发、网络和持久化方面的稳定性有待加强。
- **社区呼声明确**：用户对特定功能需求明确，如支持 Claude 订阅 OAuth (#25267)、增加 Intel Mac 构建（#42199）等，这些诉求在社区中获得高赞，是未来功能开发的重要参考。

## 2. 版本发布

无新版本发布。

## 3. 项目进展

今日合并/关闭了 7 个 PR，项目在以下方面取得了显著进展：

- **基础设施与稳定性**：
    - **S6 容器管理**：`#46289` 修复了 S6 日志服务在 virtiofs 容器中因锁文件残留导致启动失败的问题。`#46292` 增强了 S6 服务管理器中 profile 网关状态持久化机制，确保容器重启后能恢复用户意图。
- **关键 Bug 修复**：
    - **内存工具注入**：`#46348` 修复了内存提供者工具注入时不遵守 `disabled_toolsets` 配置的问题，增强了用户对工具表面的控制力。
    - **配置文件路径**：`#46315` 修复了特定配置下系统服务单元文件中 PATH 设置不可靠的问题，提高了稳定性。
- **工具生态扩展**：
    - **Unsloth Studio 插件**：`#46451` 提交了一个全新的插件，用于在本地启动和监控 Unsloth Studio 微调实例，标志着项目向本地模型微调领域拓展。该插件关联 Issue `#46450`。

## 4. 社区热点

以下 Issue 和 PR 引发了社区最广泛的讨论：

1.  **[Bug] Error: Response truncated due to output length limit** (Issue #7237)
    - **链接**: [NousResearch/hermes-agent Issue #7237](https://github.com/NousResearch/hermes-agent/issues/7237)
    - **热度**: 46条评论，6个👍
    - **分析**: 这是今日讨论量最大的议题，尽管它在两个月前就已开启，但仍在引发持续讨论。用户在使用 CLI 聊天或各种网关消息时，频繁遇到输出被截断的错误。这反映了核心模型交互在长上下文场景下的一个关键痛点，对用户体验影响极大，社区期望一个根本性的解决方案。

2.  **[Feature] Claude Agent SDK model provider with subscription OAuth** (Issue #25267)
    - **链接**: [NousResearch/hermes-agent Issue #25267](https://github.com/NousResearch/hermes-agent/issues/25267)
    - **热度**: 7条评论，21个👍
    - **分析**: 该功能请求得到了极高的点赞数，反映出大量用户希望在 Hermes 中使用 Claude 的同时，能复用已有的 Claude Pro 订阅，避免支付双重费用。这是一种强烈的用户诉求，即对现有付费生态的整合和价值的最大化利用。

## 5. Bug 与稳定性

今日报告的 Bug 主要集中在安全问题、并发稳定性和配置相关问题上。

- **紧急 (P1)**:
    - **[Bug]: send_message Matrix (media) path reconnects + re-inits E2EE per message** (Issue #46310): 每次媒体消息都进行完整的矩阵加密重连，导致密钥耗尽和消息丢失。已有 Fix PR (#46407)。
    - **[Bug]: Cron jobs created from a profile-scoped agent session go to a jobs.json the gateway never reads** (Issue #32091): 在非默认 profile 中创建的定时任务成为“孤儿”任务，永远不会被执行。无 Fix PR。

- **高影响 (P2)**:
    - **[Security]: read_file can exfiltrate credential stores from sibling profiles** (Issue #46411): 文件读取功能可以越权访问同一用户的其它 profile 下的凭证，属于严重的安全泄露风险。
    - **[Security]: Desktop file preview can read Hermes credential stores** (Issue #46413): 桌面应用的文件预览功能未屏蔽 Hermes 自身的凭证文件，同样存在安全风险。
    - **[Bug]: Concurrent sessions cross-contaminate** (Issue #46303): 并发会话间存在内存和 git 工作树污染，影响隔离性。
    - **[Bug]: model.options handler blocks on synchronous per-provider HTTP calls** (Issue #44560): 同步HTTP调用导致WebSocket超时，影响前端体验。
    - **[Bug]: gateway per-profile log/run leaves logs/gateways/ parent root-owned** (Issue #45258): Docker 环境下的日志目录权限问题。
    - **[Bug]: profile create auto-starts a doomed resident gateway** (Issue #45963): Docker 环境下创建新 profile 会因 token 冲突导致网关僵尸进程。

## 6. 功能请求与路线图信号

- **高可行性信号**：
    - **[Feature]: Claude Agent SDK model provider with subscription OAuth (Codex-style)** (Issue #25267): 社区高赞。已有 `#16634` PR 增加了对 Codex 原生 Web 搜索的支持，该项目可能作为下一个类似扩展点。
    - **[Feature]: Add ability to remove provider accounts** (Issue #45865): 用户迫切需要在UI中管理已连接的账户。这是一个用户体验改进的常见需求，容易被采纳。
    - **[Feature]: x86_64 (Intel) macOS build for Desktop App** (Issue #42199): 用户对 Intel Mac 构建的呼声明确，这是一个扩大用户基础的可行方向。
- **规划中 / 讨论中**：
    - **[Feature]: GBrain as memory provider plugin** (Issue #46253): 社区提议集成一个更高级的语义记忆后端，这符合 Hermes 不断扩展插件生态的路线。
    - **[Feature]: Make fallback session-stickiness configurable** (Issue #23094): 用户希望可以配置模型回退的粘性策略，这是一个提升灵活性的合理请求，可能会被纳入后续小版本迭代。

## 7. 用户反馈摘要

从今日的 Issues 和评论中，可以提炼出以下用户痛点:

1.  **“付费双重”的困扰** (Issue #25267): “I want to run Hermes with Claude as the model backend while staying on my Claude subscription... effectively pay twice.” 用户希望在已有其他模型订阅的情况下，不必为 Hermes 场景再次购买 API。
2.  **“新功能上线，体验却下降了”** (Issue #45058): “...it silently routes all traffic to Parallel.ai... without user opt-in.” 用户发现在未被告知的情况下，其网络请求被路由至第三方服务，引发了关于隐私和默认行为的担忧。
3.  **“UI 设计缺乏可用性”** (Issue #45865, #46192): “...seems to be no way to disconnect the account in the UI.” 用户界面在账户管理和配置项设置方面不够直观，缺少基础操作入口（如“断开连接”）和便捷交互（如“保留”框）。
4.  **“明明能用，但就是这么卡”** (Issue #46090): “I'm noticing it's becoming extremely slower, even for tasks that should take seconds.” 用户报告性能退化问题，即使在简单任务中也变得极度缓慢，这可能与自动的上下文压缩机制或资源泄漏有关。

## 8. 待处理积压

以下为长期未响应或推进缓慢的重要议题，提请维护者关注：

- **Issues**:
    - **[Bug] Error: Response truncated due to output length limit** (Issue #7237): 持续近两个月的核心问题，热度极高，需要给出长期修复计划。
    - **[Bug] Cron jobs created from a profile-scoped agent session go to a jobs.json the gateway never reads** (Issue #32091): P1 优先级，严重影响定时任务功能在非默认 profile 下的可用性。
    - **[Bug] Agent becoming extremly slow for basic tasks** (Issue #46090): 性能退化对用户体验影响巨大，需要排查并给出解决方案或解释。
- **Pull Requests**:
    - **[fix(auth): resolve Codex usage credentials from auth fallbacks](https://github.com/NousResearch/hermes-agent/pull/17480)** (PR #17480): 一个已开启近两个月的认证修复，长期未合并，可能影响 `/usage` 命令在特定认证场景下的可用性。
    - **[fix: preserve context on compression failures](https://github.com/NousResearch/hermes-agent/pull/26051)** (PR #26051): 旨在增强上下文压缩失败的健壮性，一个十分重要的稳定性改进，应尽快审阅合并。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，以下是根据 PicoClaw (github.com/sipeed/picoclaw) 2026-06-15 的 GitHub 数据生成的每日项目动态日报。

---

## PicoClaw 项目动态日报 | 2026-06-15

### 1. 今日速览

PicoClaw 项目今日活跃度**较高**。核心开发团队持续进行代码质量改进和 bug 修复，同时社区贡献者提交了多项新的功能特性与改进。过去24小时内，有5个 Issue 和9个 PR 被更新，其中包括一个重要的新版本 `nightly` 发布。项目健康度良好，社区互动积极，尤其是新功能（如远程 WebSocket 代理模式、外挂通道支持）和稳定性修复（如 TTS、文件系统错误处理）方面取得了明显进展。

### 2. 版本发布

- **Nightly Build (v0.2.9-nightly.20260615.13a38bd1)**
  - **内容**：此版本为自动化构建的夜间构建版，基于最新的 `main` 分支。包含了截至发布时所有合并的代码变更。
  - **注意事项**：该版本可能不稳定，仅供测试和尝鲜。不建议在生产环境中使用。
  - **变更日志**：[查看完整变更日志](https://github.com/sipeed/picoclaw/compare/v0.2.9...main)

### 3. 项目进展

今日有5个 PR 被合并/关闭，标志着项目在稳定性和代码整洁度上迈出了稳健的一步。

- **稳定性修复集群**：开发者 `chengzhichao-xydt` 集中提交了三个针对边缘 case 的修复 PR，体现了对代码质量的严谨态度。
    - [#3124 - fix(tts): 处理错误响应路径中的 io.ReadAll 错误](https://github.com/sipeed/picoclaw/pull/3124)：当 TTS API 返回非200状态码时，现在会正确检查并处理 `io.ReadAll` 可能发生的错误，避免了诊断信息被静默丢弃。
    - [#3123 - fix(filesystem): 显式忽略目录文件描述符的 Close() 错误](https://github.com/sipeed/picoclaw/pull/3123)：修复一个 lint 问题，使代码意图更明确。
    - [#3122 - fix(evolution): 在 appendJSONLRecords 中捕获写入文件的 Close() 错误](https://github.com/sipeed/picoclaw/pull/3122)：修复了一个潜在的数据丢失风险，现在会捕获 `defer f.Close()` 在写文件时可能产生的延迟错误（如磁盘满、NFS 错误）。
- **代码质量与重构**：
    - [#3121 - refactor(openai_compat): 用结构化日志替换 log.Printf](https://github.com/sipeed/picoclaw/pull/3121)：完成了 OpenAI 兼容提供商模块的日志标准化，提升了对问题的追踪能力。
- **Agent 稳定性**：
    - [#2904 - Fix agent loop reload and panic cleanup stability](https://github.com/sipeed/picoclaw/pull/2904)：经过近一个月的审查，这个修复 Agent 循环重载和 panic 清理稳定性的重要 PR 已被合并，解决了 `pkg/agent` 中的三个相关问题，包括因弃用 goroutine 导致的重入问题。

### 4. 社区热点

今日社区讨论热度中等，多数 Issue 和 PR 评论数较少。值得关注的是：

- **`mcp add` 命令的 Bug 报告 ([#3041](https://github.com/sipeed/picoclaw/issues/3041))**：这是一个关于命令行参数解析的 Bug，影响用户通过 `mcp add` 添加 HTTP/SSE 类型的 MCP 服务器。该问题获得1条评论，说明它已被社区开发者注意到，虽然暂时未有 PR 跟进，但这是一个影响日常使用的配置问题。

### 5. Bug 与稳定性

今日报告的 Bug 主要集中在兼容性和功能回归上，按严重程度排列如下：

- **中等**：
    - [#3125 - web_search 工具与 Brave API Key 迁移冲突](https://github.com/sipeed/picoclaw/issues/3125)：这是一个**关键的功能回归**（严重性：高）。自架构升级将 API 密钥迁移到 `.security.yml` 后，`web_search` 工具完全失效。LLM 识别并调用了该工具，但后端立即返回“无结果”。这是一个影响用户核心体验的 Bug，**目前尚无已关联的修复 PR**，需要维护者优先处理。
    - [#3090 - Panel 在 iOS 16.4 以下版本 Safari 上不工作](https://github.com/sipeed/picoclaw/issues/3090)：一个 Web 兼容性问题，影响移动端用户访问管理面板。
- **较低**：
    - [#3044 - allow_from 对包含冒号的 Matrix 用户 ID 失效](https://github.com/sipeed/picoclaw/issues/3044)：一个特定于 Matrix 频道配置的 Bug，会导致用户被错误拒绝。
    - [#3041 - `mcp add` 命令参数解析错误](https://github.com/sipeed/picoclaw/issues/3041)：影响添加 MCP 服务器的配置流程，属于配置体验方面的 Bug。

### 6. 功能请求与路线图信号

社区和开发者对项目的可扩展性和远程连接能力表现出浓厚兴趣。

- **极高可能纳入下一版本**：
    - [#3118 - `picoclaw agent` 添加远程 WebSocket 模式](https://github.com/sipeed/picoclaw/pull/3118)：一个**积极的路线图信号**。此 PR 允许 Agent 通过 WebSocket 连接远程 PicoClaw 实例，极大增强了部署的灵活性。PR 已开启3天，正在等待审查和合并。
    - [#3120 - 为外挂通道(channel)添加 `RegisterChannelSettings` 钩子](https://github.com/sipeed/picoclaw/pull/3120)：此 PR 旨在使 PicoClaw 更容易通过第三方模块扩展通道，这表明项目正在朝着更强的插件化和可扩展性方向发展。
- **可能考虑纳入**：
    - [#2978 - [已关闭] 添加 omniroute 作为提供商](https://github.com/sipeed/picoclaw/issues/2978)：虽然是已关闭的旧 Issue，但其请求添加第三方提供商的需求反映了社区对**更多元化 AI 提供商**的渴望。
    - [#2975 - telegram 通道消息回复视为 @提及](https://github.com/sipeed/picoclaw/pull/2975)：这是一个社区提出的功能请求，旨在提升 Telegram 群组中的交互体验，虽已暂停一段时间，但仍值得关注。

### 7. 用户反馈摘要

- **痛点**：
    - **API Key 管理变更导致的困惑**：用户 `Giordano10` 在 [#3125](https://github.com/sipeed/picoclaw/issues/3125) 中报告的 `web_search` 工具因密钥迁移而失效，直接影响了重要的内置功能。这表明迁移过程可能缺乏必要的向后兼容或清晰的文档引导。
    - **命令行使用体验不佳**：用户 `carlosprados` 在 [#3041](https://github.com/sipeed/picoclaw/issues/3041) 中详细描述了 `mcp add` 命令的参数解析问题，指出相关的“DisableFlagParsing”行为导致了“静默的服务器命名错误”。这反映了对精确、稳定 CLI 工具的期望。
- **使用场景**：通过 Issue 和 PR，可以看用户的使用场景多样，涉及 Matrix 即时通讯、Telegram 群组机器人、Web 代理（`allow_from`）以及通过 MCP 集成外部服务等。用户对远程 Agent 模式 (`--remote` PR #3118) 的需求，暗示了对于分布式或云端部署 PicoClaw 的兴趣。
- **满意度**：多数 Bug 报告描述清晰，并提供了复现步骤，表明用户愿意为改善项目质量做出贡献。

### 8. 待处理积压

以下为长期未响应的重要 Issue 或 PR，建议维护者关注：

- **重要功能 PR**：
    - [#2975 - feat(telegram): 在群组聊天中将回复机器人消息视为提及](https://github.com/sipeed/picoclaw/pull/2975)：此 PR 已开启超过2周，处于“stale”状态。这是一个对 Telegram 用户很友好的功能，如果设计上没有问题，值得安排评审。
    - [#3118 - 为 picoclaw agent 添加远程 WebSocket 模式](https://github.com/sipeed/picoclaw/pull/3118)：如前所述，此 PR 价值很高，建议尽快安排评审。
- **重要 Bug**：
    - **无**。今日报告的 Bug (#3125, #3090 等) 均为新提交，尚在合理等待回应的时间范围内。但 #3125 的严重性高，建议尽早确认并分配。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw 项目动态日报 | 2026-06-15

---

## 1. 今日速览

过去24小时，NanoClaw 项目保持**高活跃度**：共处理7条 Issue（6条新开，1条已关闭），10条 PR（5条待合并，5条已合并/关闭）。值得注意的是，出现了 **3个安全相关 Issue**（#2760、#2761、#2762），均为 YLChen-007 提交，涉及文件泄露、认证绕过和审批流程缺陷，需优先关注。同时，Codex 集成进入关键阶段（PR #2757、#2770），预算耗尽静默丢消息的 Bug 已有修复 PR。整体上，项目正处于功能推进与安全加固并行的活跃期。

---

## 2. 版本发布

本日无新版本发布。

---

## 3. 项目进展

今日 **5个 PR 被合并/关闭**，标志着以下重要进展：

| PR | 状态 | 描述 | 影响 |
|---|---|---|---|
| [#2769](https://github.com/nanocoai/nanoclaw/pull/2769) | ✅ 已合并 | 文档：Codex 交互认证步骤提示 + 主机重启步骤 | 提升 Codex 安装的可用性 |
| [#2757](https://github.com/nanocoai/nanoclaw/pull/2757) | ✅ 已合并 | **Codex 代理提供者 v2** — 应用服务器能力集成，仅限 Vault 认证 | 重大功能里程碑，Codex 成为完整代理提供者 |
| [#2756](https://github.com/nanocoai/nanoclaw/pull/2756) | ✅ 已合并 | **操作员驱动的提供者选择/切换/内存迁移** | 架构级变更，引入提供者注册表、选择器、安装器 |
| [#2764](https://github.com/nanocoai/nanoclaw/pull/2764) | ✅ 已合并 | 文档修复：CLAUDE.md 中两个 Key Files 路径修正 | 提升 AI 辅助开发体验 |
| [#2758](https://github.com/nanocoai/nanoclaw/pull/2758) | ✅ 已合并 | CLI 工具安装数据驱动化（`cli-tools.json`） | Dockerfile 简化，技能安装更灵活 |

**关键信号**：PR #2756 和 #2757 的合并标志着 NanoClaw 的**提供者系统完成重构**，从单一 Claude 依赖转向可扩展的提供者架构。这为后续支持更多 LLM 提供者奠定了基础。

---

## 4. 社区热点

今日无高评论数的“热点”讨论（所有 Issue/PR 评论数为 0），但以下内容反映了社区的核心诉求：

### 安全审计成为焦点 🔥
- **YLChen-007** 连续提交 3 个安全 Issue（[#2760](https://github.com/nanocoai/nanoclaw/issues/2760)、[#2761](https://github.com/nanocoai/nanoclaw/issues/2761)、[#2762](https://github.com/nanocoai/nanoclaw/issues/2762)），涉及：
  - `send_file` 绝对路径文件泄露
  - 本地网关回环 Webhook 认证绕过
  - MCP 服务器审批流隐藏参数
- **分析**：这看起来是一次系统性安全审计的结果。虽然评论数为0，但提交者描述的细节完整度表明是经过深入研究的报告。

### Codex 集成持续推进
- PR [#2766](https://github.com/nanocoai/nanoclaw/pull/2766)、[#2765](https://github.com/nanocoai/nanoclaw/pull/2765) 均为 `[follows-guidelines]` 标记的 Codex 相关功能提交，表明社区正在按规范流程为 Codex 添加渠道和提供者技能。

### 用户反馈墙 — 预算耗尽静默丢消息
- Issue [#2751](https://github.com/nanocoai/nanoclaw/issues/2751) 提出：当 LLM 调用超出 token/费用预算时，用户得不到任何回复。已有 fix PR [#2759](https://github.com/nanocoai/nanoclaw/pull/2759) 关闭此 Issue。

---

## 5. Bug 与稳定性

### 安全漏洞（严重程度：高）

| Issue | 标题 | 严重性 | 状态 | 描述 |
|---|---|---|---|---|
| [#2760](https://github.com/nanocoai/nanoclaw/issues/2760) | `send_file` 绝对路径任意文件泄露 | 🔴 严重 | 待处理 | `send_file` 工具接受任意绝对路径，无读取范围限制，可导致敏感文件被外泄 |
| [#2761](https://github.com/nanocoai/nanoclaw/issues/2761) | 本地网关环回 Webhook 认证绕过 | 🔴 严重 | 待处理 | 本地 Webhook 未认证发送者即可执行操作 |
| [#2762](https://github.com/nanocoai/nanoclaw/issues/2762) | MCP 服务器审批流隐藏参数 | 🟠 高 | 待处理 | 批准者看不到 `args` 和 `env`，攻击者可隐藏恶意参数 |

### 功能性 Bug

| Issue | 标题 | 严重性 | 状态 | 修复 PR |
|---|---|---|---|---|
| [#2751](https://github.com/nanocoai/nanoclaw/issues/2751) | 预算耗尽 LLM 调用静默丢消息 | 🟡 中 | **已有修复** | [#2759](https://github.com/nanocoai/nanoclaw/pull/2759) |
| [#2767](https://github.com/nanocoai/nanoclaw/issues/2767) | Telegram 遗留 Markdown 清理器过时 | 🟢 低 | 待处理 | 适配器已支持 MarkdownV2 |

### 文档 Bug

| Issue | 标题 | 严重性 | 状态 |
|---|---|---|---|
| [#2763](https://github.com/nanocoai/nanoclaw/issues/2763) | CLAUDE.md Key Files 指向已移动文件路径 | 🟢 低 | **已关闭**（已修复） |

**风险提示**：3个安全漏洞均无修复 PR 关联，且攻击面清晰（文件系统、本地网络、审批流程），建议维护者优先评估并计划修复。

---

## 6. 功能请求与路线图信号

### 可能纳入下一版本的功能

| 功能 | 对应 Issue/PR | 证据 |
|---|---|---|
| **Claude 提示缓存默认启用** | [#2768](https://github.com/nanocoai/nanoclaw/issues/2768) | 简单配置变更，对复杂系统提示的 agent 有明显性能提升 |
| **Codex 图片生成交付** | [#2770](https://github.com/nanocoai/nanoclaw/pull/2770) | 已有 PR，修复构建和交付流程 |
| **提供者切换/选择 UI** | [#2756](https://github.com/nanocoai/nanoclaw/pull/2756) | 已合并，核心架构已就绪 |
| **CLI 工具数据驱动安装** | [#2758](https://github.com/nanocoai/nanoclaw/pull/2758) | 已合并，基础框架已落地 |

### 强烈社区信号

- **提供者生态**：PR #2756 的合并意味着下一版本很可能支持 **多个 LLM 提供者动态切换**（如 Claude、Codex、OpenAI等），这是用户长期以来的需求。
- **Codex 深度集成**：多个 PR 指向 Codex 将成为首选的“非默认”提供者。

---

## 7. 用户反馈摘要

由于今日所有 Issue/PR 评论数均为 0，反馈主要来自 Issue 正文：

| 用户痛点 | 来源 | 上下文 |
|---|---|---|
| **预算管理不透明** | [#2751](https://github.com/nanocoai/nanoclaw/issues/2751) | “用户收不到任何回复” — 预算耗尽时静默失败，破坏使用体验 |
| **安全担忧** | [#2760](https://github.com/nanocoai/nanoclaw/issues/2760) | 文件泄露风险 — 用户可能无意中被窃取本地文件 |
| **AI 辅助开发体验差** | [#2763](https://github.com/nanocoai/nanoclaw/issues/2763) | CLAUDE.md 路径过时，AI 助手因此卡住 |
| **配置遗漏** | [#2768](https://github.com/nanocoai/nanoclaw/issues/2768) | 提示缓存未默认开启导致性能浪费 |

**积极信号**：无用户抱怨 UI/UX 问题，更多关注在**安全性和功能完整性**上，说明核心功能已被社区接受。

---

## 8. 待处理积压

### 长期未响应的 Issue

| Issue | 标题 | 创建时间 | 最后更新 | 备注 |
|---|---|---|---|---|
| [#2751](https://github.com/nanocoai/nanoclaw/issues/2751) | 预算耗尽静默丢消息 | 2026-06-12 | 2026-06-14 | **已有修复 PR**，建议优先合并 |
| [#2732](https://github.com/nanocoai/nanoclaw/pull/2732) | 健康审计加固（PR） | 2026-06-11 | 2026-06-14 | 19 文件变更，多 Agent 安全审计结果，需 reviewer 审查 |

### 等待处理的安全 Issue（强烈建议本周内响应）

- [#2760](https://github.com/nanocoai/nanoclaw/issues/2760) — 文件泄露（严重）
- [#2761](https://github.com/nanocoai/nanoclaw/issues/2761) — 认证绕过（严重）
- [#2762](https://github.com/nanocoai/nanoclaw/issues/2762) — MCP 审批隐藏参数（高）

**建议**：对上述安全 Issue，维护团队应：
1. 在 24 小时内回复确认收到，并给出初步评估时间表
2. 考虑临时禁用受影响的功能（如 `send_file` 绝对路径支持）
3. 在修复前发布安全公告

---

## 项目健康度总结

| 维度 | 评级 | 说明 |
|---|---|---|
| **活跃度** | ⭐⭐⭐⭐⭐ | 10 PR + 7 Issue / 天，开发者持续贡献 |
| **代码质量** | ⭐⭐⭐⭐ | 多项修复和功能有测试覆盖；安全审计结果提示需加强安全 CI |
| **用户体验** | ⭐⭐⭐ | 预算处理问题已修复，但安全漏洞可能影响信任 |
| **文档** | ⭐⭐⭐⭐ | 有专门文档修复 PR，但 CLAUDE.md 仍有疏漏 |
| **社区参与** | ⭐⭐⭐⭐ | 安全研究者积极参与；贡献者遵循规范（`follows-guidelines` 标签） |

**今日关键词**：**安全审计**、**提供者生态**、**Codex 集成**

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，以下是根据您提供的NullClaw项目数据生成的日报。

---

## NullClaw 项目动态日报 | 2026-06-15

### 1. 今日速览

今日项目整体活跃度较低，无代码合并或版本发布。社区贡献主要集中于一项新功能请求的提出，该请求聚焦于增强Azure OpenAI的身份认证安全性。项目仓库未出现新的Bug报告或待解决问题，整体状态稳定，但缺乏核心功能推进的动态。维护团队可能需要关注即将到来的待办事项积压。

### 2. 版本发布

无

### 3. 项目进展

今日无任何Pull Requests被合并或关闭，项目核心代码库未发生变更。

### 4. 社区热点

今日唯一的社区动态是新增的 **Issue #955**：**“[enhancement] Identity based authentication support for Azure OpenAI LLM Provider”**。

- **链接**: [Issue #955](nullclaw/nullclaw Issue #955)
- **分析**: 这是今天社区唯一的声音。该请求建议利用`DefaultTokenCredential`从Azure CLI登录中获取开发者凭证，以替代当前可能存在的密钥或API Key认证方式。背后的核心诉求是**企业级安全合规**。用户（@kunalk16）明确指出，许多Azure订阅的安全策略禁止使用API Key，必须采用托管身份或用户身份进行登录。这表明NullClaw的用户群已深入到更严格的企业安全环境，项目若想在该场景下广泛采用，此功能将从“锦上添花”变为“必需品”。

### 5. Bug 与稳定性

今日无新的Bug报告。

### 6. 功能请求与路线图信号

- **功能请求**: `Identity based authentication support for Azure OpenAI` (Issue #955)
- **路线图信号**: 这是一个**强信号**。它指出了项目在云服务提供商（特别是Azure）集成方面的一个关键缺失。虽然目前没有对应的PR，但考虑到该请求的合理性（符合Azure最佳安全实践）和潜在的广泛需求，它很可能被纳入下一个版本（或次版本）的规划中。建议项目维护者优先评估此请求，并可能在其Github `Projects`或路线图中创建对应卡片。

### 7. 用户反馈摘要

由于今日仅有1个Issue且无评论，用户反馈非常明确且集中：

- **痛点**: 在当前Azure OpenAI集成中，无法使用身份认证（Identity-based Auth），这导致在某些安全策略严格的Azure订阅中无法使用NullClaw。
- **使用场景**: 企业用户或受严格监管的组织，他们要求所有服务间调用必须通过Azure AD身份进行验证，而非静态密钥。
- **期望**: 支持`DefaultAzureCredential`，无需手动配置密钥，自动使用当前环境（如Azure VM、CLI登录）中的身份凭证。

### 8. 待处理积压

项目当前无长期未响应的Issue或PR，社区队列清晰。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，这是根据您提供的IronClaw项目GitHub数据生成的2026-06-15项目动态日报。

---

# IronClaw 项目日报 | 2026-06-15

## 1. 今日速览

IronClaw 项目今日保持**极高活跃度**，过去24小时内产生了43个Issues和48个PR，核心团队与社区成员均在密集开发和修复中。**“Reborn”** 新架构是当前绝对焦点，大量Issues集中在其UX、安全、稳定性及Extension体验的打磨上。同时，团队启动了内部“**Dogfooding**（吃自己的狗粮）”活动，通过使用自身产品来发现可用性问题，并提出了利用IronClaw提升自身工程效率的 **“AI-native”** 提案，标志着项目进入自我进化阶段。项目暂无新版本发布。

## 2. 版本发布

无。

## 3. 项目进展

今日合并/关闭的重要PR主要聚焦于 **“Reborn”架构的基础设施、核心功能修复以及关键的依赖更新**。项目在稳固新架构基础的同时，也在修复已发现的设计缺陷。

- **核心架构与安全加固**:
    - **[#4836] (已关闭)** feat(runtime-context): surface connected channels, delivery state, and run origin。实现了运行时上下文，让模型能感知到连接通道、投递状态和运行来源，提升了模型对环境的感知能力。([链接](https://github.com/nearai/ironclaw/pull/4836))
    - **[#4848] (已关闭)** auth-resume: match pending resume by per-invocation identity (input_ref), not just capability_id。修复了一个授权恢复中的潜在安全问题，确保授权恢复能精确匹配到具体调用，而非仅凭能力ID，防止了身份盗用。([链接](https://github.com/nearai/ironclaw/issues/4848))
    - **[#4851] (已关闭)** Trusted-trigger origin is laundered through adapter_kind string。修复了一个深层次的安全设计缺陷：触发器的“信任”状态在被转换、扁平化后，下游重新推导时可能出现错误。此次修复强化了信任链的类型安全。([链接](https://github.com/nearai/ironclaw/issues/4851))

- **主要功能推进**:
    - **[#4871] (打开中)** feat(attachments): image attachment support for vision-capable models。这是一个里程碑式的PR，为支持视觉的模型（如GPT-4V）启用了真正的图片附件功能，附件将以多模态内容直接发送给模型，而不仅仅是文本指针，显著提升了Reborn的交互能力。([链接](https://github.com/nearai/ironclaw/pull/4871))

- **依赖更新**:
    - **[#4876] (打开中)** build(deps): bump the everything-else group across 1 directory with 43 updates。一次大规模的依赖更新，包含42个包的版本升级，有助于保持项目技术先进性和安全性。([链接](https://github.com/nearai/ironclaw/pull/4876))

**项目健康度分析**：项目正在从功能原型阶段快速转向成熟化和精细化阶段，边沿性强、核心模块不断重构、安全与稳定性问题被及时发现和修复，项目处于非常健康的发展期。

## 4. 社区热点

今日讨论热度集中在 **Reborn架构的Extension体验** 和 **Shell工具的安全绕过** 两个议题上，反映了社区对新功能的兴奋与对安全问题的警觉。

- **[#4890] Extension setup flow is fragmented:** 用户报告了GitHub和Google Calendar Extension安装后的设置流程碎片化，安装成功后用户不清楚下一步操作（如何授权、配置）。这揭示了Reborn Extensions的UX设计有待完善，是社区最迫切的优化需求之一。 ([链接](https://github.com/nearai/ironclaw/issues/4890))
- **[#4886] Installed extensions provide limited guidance:** 与#4890类似，用户反馈Extesion安装后，界面提示“AUTH NEEDED”，但没有清晰的指导告诉用户如何进行下一步，导致用户体验割裂。 ([链接](https://github.com/nearai/ironclaw/issues/4886))
- **[#4865] & [#4864] Shell approval boundary bypass via transparent wrapper:** 这两个安全报告是今日的焦点。贡献者 `YLChen-007` 发现了两条Shell批准边界绕过路径：一个是通过 `env /bin/sh -c` 透明包装器绕过授权；另一个是利用命令包装器继承前一个命令的自动授权。这直接威胁到用户通过Shell执行高风险命令的安全模型，已引起团队高度警惕。 ([#4865](https://github.com/nearai/ironclaw/issues/4865), [#4864](https://github.com/nearai/ironclaw/issues/4864))

## 5. Bug 与稳定性

今日报告的Bug多数集中在**Reborn新架构**的UX和功能缺陷上，同时也暴露了一个**高风险的安全漏洞**。

| 严重程度 | Issue | 摘要 | 是否有Fix PR |
| :--- | :--- | :--- | :--- |
| **严重 (Critical)** | [#4865](https://github.com/nearai/ironclaw/issues/4865) | [Security] Shell批准边界绕过（via `env /bin/sh -c` 包装器） | 暂无 |
| **严重 (Critical)** | [#4864](https://github.com/nearai/ironclaw/issues/4864) | [Security] Shell批准包装器绕过，高风险命令继承先前自动批准状态 | 暂无 |
| **高 (High)** | [#4887](https://github.com/nearai/ironclaw/issues/4887) | [Reborn] Provider-backed MCP工具批准恢复失败，因陈旧 capability input_ref | 暂无 |
| **高 (High)** | [#4892](https://github.com/nearai/ironclaw/issues/4892) | [Reborn] WebUI v2 日志链接对非操作员可见，并吞掉403错误返回空日志流 | 暂无 |
| **中 (Medium)** | [#4874](https://github.com/nearai/ironclaw/issues/4874) | Bug: WebChat v2 聊天在通过非localhost的HTTP访问时，发送失败并报“Illegal invocation” | 暂无 |
| **中 (Medium)** | [#4870](https://github.com/nearai/ironclaw/issues/4870) | [Reborn] WebUI WebSocket helper 与 v2 auth 合约冲突 | 暂无 |

## 6. 功能请求与路线图信号

今日的功能请求主要集中在 **“工程效率”** 和 **“开发者体验”** 上，这是一个强烈的路线图信号。

- **AI原生工程流程**: `think-in-universe` 提交了一系列Issues（#4878, #4882, #4881, #4880, #4883），旨在将IronClaw自身用于自动化代码审查、测试覆盖、预览部署，并构建coding agent cloud workflow。这标志着项目不仅是一个产品，更是一套开发方法论。([链接](https://github.com/nearai/ironclaw/issues/4878))
- **Extension体验优化**: 多个Issues (#4890, #4886) 都指向了Reborn Extension从安装到配置再到使用的流程割裂问题。这强烈暗示下一个版本将重点优化Extension的Onboarding和UX。
- **通用附件系统**: 虽然已有一个关键PR (#4871) 支持了图片附件，但对应的基础Issue (#4644) 仍为打开状态，要求将所有通道的附件系统统一并扩展。这表明附件功能的完整落地将是后续的重要目标。

## 7. 用户反馈摘要

- **痛点**: **“碎片化”** 是今日用户反馈的核心词。用户对Extension从市场安装到最终使用的流程感到困惑，不清楚如何进行授权或配置，需要手动“摸索”。
- **场景**: 用户开始尝试更复杂的多步骤任务，例如分析GitHub仓库（#4867）, 使用Google Calendar（#4884），以及通过Shell执行系统命令（#4852, #4865），反映出用户对IronClaw作为通用Agent的期待。
- **满意度**: 用户对Re-born新架构的功能是兴奋的，例如发现了图像附件支持（#4871），但当前的UX短板和安全隐患正在消耗这份热情。用户 `YLChen-007` 在活跃地报告安全漏洞，这表明社区中有一群深度技术用户，愿意花时间帮助项目变得更好。
- **不满意之处**: WebUI v2的日志功能对非管理员用户混淆（#4892）；Network模式下HTTP访问报“Illegal invocation”错误（#4874）；Shell命令的执行过程在审批对话框和活动历史中不透明（#4852）。

## 8. 待处理积压

以下为长期未关闭或值得重点关注的重要Issue/PR，提醒维护者关注：

- **[#4871] feat(reborn): image attachment support for vision-capable models:** 虽然此PR今日活跃，但它所解决的基础问题 [#4644 Universal attachments](https://github.com/nearai/ironclaw/issues/4644) 已存在一周，且评论不多。该问题对提升Reborn的交互质量至关重要，建议尽快推进。
- **[#4588] feat(reborn): observability seams — trajectory observer + LLM provider injection:** 这是一个由经验丰富的贡献者 `pranavraja99` 提交的大型PR，旨在为Reborn增加可观测性钩子。它对于Benchmark和未来进行深度性能分析非常关键，已存在6天，建议定期review以推动合并。
- **[#4575] Fix system ResourceScope JSON round-trip:** 一个由常规贡献者 `matiasbenary` 提交的修复性PR，解决了一个序列化/反序列化问题。虽然规模较小，但“系统范围”问题可能影响核心权限判断，建议优先审查。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，我已根据您提供的LobsterAI项目数据，生成2026年6月15日的项目动态日报。

---

## LobsterAI 项目动态日报 | 2026-06-15

### 1. 今日速览

今日项目活跃度**中等偏低**。过去24小时内，没有新的版本发布，表明项目可能处于稳定期或功能开发的中后期。社区提交了2个新的Issue和3个未合并的PR，但大部分为历史积累的“陈旧(stale)”项，真正的即时动态较少。值得注意的是，今日成功合并了1个重要的PR (#2159)，聚焦于文档Artifact的分享与预览优化，这标志着项目在核心文档协作能力上取得了实质性的功能提升。整体来看，项目维护节奏稳健，但对社区长期未处理事项的响应速度有待观察。

### 2. 版本发布

无新版本发布。

### 3. 项目进展

今日合并/关闭了2个重要PR，标志着以下功能和修复的推进：

- **[已合并] 文档 Artifact 分享与预览优化** (PR #2159): 这是一个重要的功能增强PR。它引入了对 DOCX, PPTX, XLSX, PDF, CSV, TSV 等多种文档格式的Artifact分享能力，并优化了预览体验。具体包括文件打包、类型校验、大小限制、PDF原生预览兜底以及表格自动列宽等细节。这显著提升了LobsterAI在办公协同场景下的实用性和用户体验。
  - 链接: [PR #2159](https://github.com/netease-youdao/LobsterAI/pull/2159)

- **[已合并] 修复已删除定时任务幽灵复活 Bug** (PR #1465): 这是一个关键的稳定性修复。解决了用户删除定时任务后，重启应用该任务以空会话形式“幽灵”重现的Bug。根本原因是删除操作未清理本地SQLite中的关联会话记录。此修复直接提升了定时任务功能的可靠性和用户信任度。
  - 链接: [PR #1465](https://github.com/netease-youdao/LobsterAI/pull/1465)

**项目进度总结**: 项目在增强核心功能（文档协作）和修复关键稳定性问题（定时任务）上均取得了可见进展，整体朝更成熟、更可靠的方向迈进。

### 4. 社区热点

今日社区讨论热度不高，暂无引起激烈讨论的Issue或PR。所有2个新开的Issue和3个待合并的PR均创建于4月初并已标记为“陈旧(stale)”，说明在过去两个多月内，这些议题没有得到足够的关注或跟进。这反映了项目维护者在处理积压议题上可能存在瓶颈。

**潜在诉求分析**: 标记为“陈旧(stale)”的PR (如 #1429, #1430, #1431) 涉及会话内消息搜索、阻止系统休眠和运行计时器等提升用户体验的功能，表明社区用户对更精细化的会话控制、搜索效率及长时间任务可靠性有明确需求。

### 5. Bug 与稳定性

今日报告的Bug有两个，均于4月初提出且标记为“陈旧”，严重程度为**低**，属于UI/UX层面的问题。

- **Issue #1434: 搜索无数据时提示语和按钮未中文化**
  - **严重程度**: 低（UI/本地化问题）
  - **描述**: 在Agent的技能Tab页搜索无结果时，提示语和按钮显示为英文，与用户设定的中文语言环境不符。
  - **已有关联PR**: 无
  - 链接: [Issue #1434](https://github.com/netease-youdao/LobsterAI/issues/1434)

- **Issue #1435: 新建Agent时名称过长导致UI溢出**
  - **严重程度**: 低（UI/交互问题）
  - **描述**: 创建自定义Agent时，输入超长名称会直接溢出弹出的对话框，展示不友好。
  - **已有关联PR**: 无
  - 链接: [Issue #1435](https://github.com/netease-youdao/LobsterAI/issues/1435)

### 6. 功能请求与路线图信号

今日没有新增的功能请求。但从待处理的3个PR中，可以识别出明确的路线图信号：

- **会话体验增强**: PR #1429（会话内消息搜索）、PR #1431（运行计时器）和PR #1430（阻止系统休眠）均旨在提升Cowork会话的用户体验和可靠性。如果这些PR最终被合并，将意味着下一版本会重点关注会话交互的精细度、用户对耗时的感知度以及长时间运行的稳定性。
  - 链接: [PR #1429](https://github.com/netease-youdao/LobsterAI/pull/1429), [PR #1430](https://github.com/netease-youdao/LobsterAI/pull/1430), [PR #1431](https://github.com/netease-youdao/LobsterAI/pull/1431)

### 7. 用户反馈摘要

今日无新的用户评论。根据两个存留的Issue，可以提炼出以下用户痛点：

- **本地化不彻底**: 用户对部分UI元素未随语言设置切换表示不满，这表明用户在追求完整、一致的中文交互体验。
- **输入限制缺乏友好提示**: 用户对名称无明确长度限制或限制后处理不当（直接溢出）表示困扰，这反映了用户期待更智能、更防呆的交互设计。

### 8. 待处理积压

以下这些长期处于“OPEN”状态且标记为“陈旧”的Issue和PR需要维护者关注，它们代表了社区已贡献但未被采纳或反馈的代码/想法：

1.  **会话内消息搜索功能** (PR #1429): 创建于2026-04-03，代码已就绪但未合并。这是社区开发者贡献的增强功能。
    - 链接: [PR #1429](https://github.com/netease-youdao/LobsterAI/pull/1429)
2.  **会话运行期间阻止系统休眠** (PR #1430): 创建于2026-04-03，对长时间任务的可靠性至关重要。
    - 链接: [PR #1430](https://github.com/netease-youdao/LobsterAI/pull/1430)
3.  **会话运行计时器** (PR #1431): 创建于2026-04-03，提升用户对任务耗时的感知。
    - 链接: [PR #1431](https://github.com/netease-youdao/LobsterAI/pull/1431)
4.  **中文本地化Bug** (Issue #1434, #1435): 创建于2026-04-03，问题简单明确，修复成本低，长期搁置影响用户体验。
    - 链接: [Issue #1434](https://github.com/netease-youdao/LobsterAI/issues/1434), [Issue #1435](https://github.com/netease-youdao/LobsterAI/issues/1435)

**建议**: 项目维护者可以优先评审并合并/关闭这些“陈旧”的PR和Issue，以保持社区贡献的积极性，并提升项目透明度。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis 项目动态日报 (2026-06-15)

## 1. 今日速览
项目今日整体活跃度较低，主要活动集中在1个新的功能请求Issue上，无新的PR提交或版本发布。社区讨论热度不高，但该Issue提出的功能（纯Rust内存后端）具有显著的性能优化潜力，可能引发后续开发关注。项目健康度平稳，但需关注新功能需求是否会被团队采纳并纳入路线图。

## 3. 项目进展
- 今日无合并或关闭的PR，项目核心代码无直接变更。

## 4. 社区热点
- **[#1123] [Feature]: Add pure-Rust turbovec as an alternative memory backend for extreme edge compression**  
  - 作者：joeblew999 | 评论：0 | 👍：0  
  - 链接：https://github.com/moltis-org/moltis/issues/1123  
  - **分析**：这是今日唯一活跃的Issue，尽管暂无评论或点赞，但提案本身具有明确的技术价值：通过纯Rust实现的内存后端（turbovec）来优化极端边缘场景下的压缩性能。这类需求通常来自对内存效率和跨平台兼容性有严格要求的用户，反映了社区对“自包含、无外部依赖”运行模式的强烈倾向。后续需关注是否有维护者或贡献者回应，以及是否会被纳入待办。

## 6. 功能请求与路线图信号
- **#1123** 提出的`turbovec`后端若被采纳，可能成为下一版本的核心亮点，尤其适合IoT或资源受限的边缘设备部署。该功能不涉及破坏性变更（纯新增后端），但需评估与现有内存管理模块的集成成本。目前无关联PR，建议维护者优先进行技术可行性评估。

## 7. 用户反馈摘要
- 在**#1123**中，用户明确表达了“pure-Rust”偏好，暗含对C/C++依赖（如valgrind、jemalloc等）的规避需求。这类反馈指向开发者在跨平台编译和分发中的实际痛点（如减少二进制体积、避免外部库版本冲突），是项目向“零外部依赖”演进的重要信号。

## 8. 待处理积压
- **长期未响应的关键Issue**：未发现。但建议维护者定期审视所有open状态Issue（特别是2026年之前提交的），以避免社区贡献流失。当前唯一open的Issue **#1123** 尚未被指派或添加标签，需尽快响应以保持社区参与积极性。

---

**项目健康度总结**：  
- 活跃度：低（仅1个新Issue，无PR/Release）  
- 稳定性：未发现新Bug或回归  
- 社区参与：需求明确但缺乏互动  
- 风险：功能请求若长期无人回应，可能影响贡献者信任度  

建议：明日可启动**#1123**的标签分类（如`enhancement`、`needs-discussion`）并邀请团队核心成员发表技术意见，以推动项目脉络向前发展。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，以下是根据 CoPaw (QwenPaw) 提供的 GitHub 数据生成的 2026-06-15 项目动态日报。

---

# CoPaw (QwenPaw) 项目动态日报 | 2026-06-15

## 今日速览

项目社区活跃度极高，24小时内共产生41次议题（Issues）与PR（Pull Requests）互动。Bug修复和功能请求数量均处于高位，表明项目正处于快速迭代与功能深化阶段。尤其值得关注的是，与 `v1.1.11.post2` 版本相关的回归问题（如Gemini工具调用、本地模型不显示）及Windows桌面端稳定性问题（进程泄露、Tauri启动慢、控制台崩溃）成为社区反馈焦点，同时有多项针对“定时任务”、“上下文压缩”等高级功能的深度探讨。项目维护者响应迅速，已合并/关闭了多项关键修复。

## 版本发布

**无新版本发布。**

## 项目进展

过去24小时内，项目团队在稳定性与功能完善方面取得了实质性进展，成功合并/关闭了6个PR，解决了社区痛点。

- **修复关键回归与稳定性问题：**
    - **[PR #5051]** 修复了Windows桌面版重启后智能体及对话历史重置的问题（关联Issue #4733）。
    - **[PR #5037]** 修复了Linux系统浏览器检测时，若 `.desktop` 配置项 `Exec=` 为空可能触发的 `IndexError` 崩溃问题。
    - **[PR #5035]** 修复了 `LlamaCppBackend` 解析版本号时因硬编码切片导致的潜在崩溃（当构建号超过9999时）。
    - **[PR #5038]** 修复了 `LightContextManager.pre_reply` 方法在收到空消息列表时可能触发的 `IndexError` 崩溃。
    - **[PR #5092]** 回滚了一项已知有问题的打包修复 (`#5084`)，解决了编译后Discord插件检查问题（关联Issue #5086）。

- **新增功能与插件：**
    - **[PR #5188]** 新增了请求负载转换（Request Payload Transforms）功能，允许插件在发送聊天请求前修改数据。这为高级用户和插件开发者提供了更灵活的定制能力。

**项目整体评估：** 项目团队正积极回应用户报告的回归问题和历史Bug，尤其是涉及核心稳定性和使用体验的缺陷。同时，也在持续推进功能的可扩展性开发。

## 社区热点

今日社区讨论的核心集中在**功能深度使用体验**和**关键回归问题排查**上，反映了社区从“能用”到“好用”的期望升级。

1.  **[Issue #5156] 建议支持 kimi-for-coding / 加入 uv 白名单** (评论: 5)
    - **链接：** [agentscope-ai/QwenPaw Issue #5156](https://github.com/agentscope-ai/QwenPaw/issues/5156)
    - **诉求：** 用户已付费订阅了Kimi的coding套餐，但QwenPaw仅支持Kimi的官方API，导致用户无法将已有订阅服务集成到QwenPaw中使用。
    - **分析：** 此需求代表了社区对**多模型支付/接入方式**整合的强烈呼声。用户希望软件能提供更高的灵活性，支持更多的模型提供者和接入方式，而不仅仅是官方API。

2.  **[Issue #5047] Windows Tauri 桌面端启动特别慢** (评论: 5)
    - **链接：** [agentscope-ai/QwenPaw Issue #5047](https://github.com/agentscope-ai/QwenPaw/issues/5047)
    - **诉求：** 从Python打包切换到Tauri后，Windows桌面端启动时间从1-2分钟变成了十几分钟，并伴随无响应状态。
    - **分析：** 这是一个严重的用户体验问题。Tauri架构虽提供了更好的前端体验，但启动效率的急剧下降违背了用户的预期。该Issue被标记为已关闭，需观察其关闭原因（是已修复还是转为内部工单），但社区的期待和焦虑感显而易见。

3.  **[Issue #5174] 定时任务和心跳机制的缺陷是吗？** (评论: 2)
    - **链接：** [agentscope-ai/QwenPaw Issue #5174](https://github.com/agentscope-ai/QwenPaw/issues/5174)
    - **诉求：** 用户发现Cron Agent虽然能执行简单的脚本，但无法完成生成知识文件等复杂操作。心跳Agent理论上能执行任务，但实际并不执行。
    - **分析：** 这表明项目的**定时与自动化任务系统**存在设计或实现上的限制。用户的深层诉求是希望“Agent”能够在特定时间或场景下真正自主地完成有状态、多步骤的任务，而不仅仅是执行简单的命令。这触及了Agent自主性的核心能力。关联的PR #5180正尝试解决此问题。

## Bug 与稳定性

此类别问题在过去24小时内量多且关键，涉及多个严重程度。已有关联fix PR的项已标注。

| 严重程度 | Issue/PR | 描述 | 状态 |
| :--- | :--- | :--- | :--- |
| **严重** | [#5047](https://github.com/agentscope-ai/QwenPaw/issues/5047) | **Windows Tauri桌面端启动极慢 (10+分钟)** | **已关闭** (需确认修复情况) |
| **严重** | [#5138](https://github.com/agentscope-ai/QwenPaw/issues/5138) | **Windows客户端进程持续增加，内存占用90%+** | **已关闭** (修复可能已合并) |
| **严重** | [#5163](https://github.com/agentscope-ai/QwenPaw/issues/5163) | **Gemini工具调用在v1.1.11.post2回归，`v1.1.10`正常** | 开放中 |
| **高** | [#5184](https://github.com/agentscope-ai/QwenPaw/issues/5184) | **v1.1.11.post2中本地模型提供商不显示** | 开放中 |
| **高** | [#5192](https://github.com/agentscope-ai/QwenPaw/pull/5192) | **修复Windows控制台崩溃（Rich库兼容性）和自杀死命令** | **PR开放，待合并** |
| **中** | [#5166](https://github.com/agentscope-ai/QwenPaw/issues/5166) | **Python 3.13环境安装TeamChat插件失败 (`imghdr` 模块移除)** | 开放中 |
| **中** | [#5181](https://github.com/agentscope-ai/QwenPaw/issues/5181) | **插件依赖安装失败时，cmd窗口持续弹窗** | 开放中 |
| **中** | [#5162](https://github.com/agentscope-ai/QwenPaw/issues/5162) | **对话思考逻辑进入死循环** | 开放中 |
| **中** | [#5171](https://github.com/agentscope-ai/QwenPaw/issues/5171) | **上下文压缩导致信息完全丢失，任务中断** | 开放中 |
| **低** | [#5165](https://github.com/agentscope-ai/QwenPaw/issues/5165) | **PyInstaller打包脚本引用不存在模块，启动白屏** | 开放中 |

## 功能请求与路线图信号

社区功能请求方向明确，主要集中在**可观测性、平台扩展性和交互体验**上。

- **可观测性支持 (被广泛讨论):** `[Issue #5009]` 询问是否有计划集成Langfuse、OpenTelemetry等可观测性平台。这看似一个简单问题，实则反映了**GenAI应用走向生产环境的必经之路**。虽然该Issue已被关闭，但它是社区对项目专业度的重要期待。
- **平台扩展 (明确方向):** `[Issue #5168]` 提议增加越南Zalo Bot官方支持，而 `[PR #5186]` 和 `[PR #5175]` 则为前端界面贡献了完整的越南语翻译。这表明项目正获得来自东南亚的早期贡献者关注，**国际化是明确的增长方向**。
- **自动化与Agent能力增强 (深度需求):** `[Issue #5174]` 与 `[Issue #5171]` 共同指向用户对Agent自主执行复杂任务、处理上下文压缩与保留的**高级功能需求**。关联的修复PR `#5180` 正在解决超时和自主性问题。
- **统一模型配置:** `[Issue #5182]` 提出的统一文本、向量、音视频模型配置，是降低用户使用门槛、提升平台可管理性的**重要架构优化信号**。

## 用户反馈摘要

提炼自社区Issue评论的真实用户声音：

- **正面反馈：** 有用户感谢团队维护项目，并对已打通的功能（如飞书流式卡片）表达了认可。
- **核心痛点：**
    - **“启动慢”、“卡死”、“内存泄露”**：Windows Tauri桌面端的稳定性和性能问题是最常被提及的痛点，严重影响日常使用体验。
    - **“不能用已有的付费订阅”**：无法将Kimi coding套餐等第三方订阅接入QwenPaw，让付费用户感到功能受限和资源浪费。
    - **“自动化不自动”**：对Cron/Heartbeat Agent的期待与实际能力（无法自主完成复杂任务、上下文丢失）之间的落差，使许多用户感到失望。
    - **“升级后出现问题”**：多名用户明确报告从v1.1.10升级到v1.1.11.post2后出现新Bug（如Gemini工具调用失效、本地模型不显示），对版本兼容性感到担忧。
    - **“界面细节体验不好”**：代码不高亮、长回复飞书卡片慢、审批流程找不到入口、控制台信息折叠缺陷等问题，虽非致命，但持续消耗用户耐心。

## 待处理积压

以下为长期未响应或可能被忽视，但仍需维护者关注的重要议题与PR：

1.  **[PR #4622] plugin(datapaw): add data-analysis plugin with 12 BI skills** (已开放24天)
    - **链接：** [agentscope-ai/QwenPaw PR #4622](https://github.com/agentscope-ai/QwenPaw/pull/4622)
    - **说明：** 一个包含12项商业智能技能的“数据分析和可视化”插件，功能丰富。长期未合并，可能因审核难度或优先级问题而停滞。建议维护者给出明确反馈（合并、要求修改或拒绝）。

2.  **[PR #4902] feat(manage_prd): add built-in PRD CRUD tool with frontend renderer** (已开放13天)
    - **链接：** [agentscope-ai/QwenPaw PR #4902](https://github.com/agentscope-ai/QwenPaw/pull/4902)
    - **说明：** 一个重要的功能PR，增加内置的PRD管理工具。长时间未得到实质性回复，可能因核心功能变更而需谨慎评估。建议加速review流程。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

好的，这是为您生成的 ZeroClaw 项目动态日报。

---

# ZeroClaw 项目动态日报 | 2026-06-15

## 1. 今日速览

ZeroClaw 项目在2026年6月15日整体保持**高度活跃**状态。24小时内，Issue 和 PR 的更新量巨大，显示出社区贡献者和维护团队的强劲动力。然而，我们也观察到一些重要的风险信号：**积压 PR 数量极高**（46个待合并），且**多个高优先级 Open PR 处于“需要作者行动”状态**，这可能会延缓关键修复和新功能的落地。尽管没有新版本发布，但 PR 的提交和合并集中在**渠道扩展、配置修复和运行时优化**上，项目正处于功能快速迭代期。

## 2. 版本发布

- **无新版本发布。** 上次发布节点为 v0.7.5-debian。

## 3. 项目进展

今日合并/关闭的 PR 虽然不多（4个），但质量很高，主要集中在回滚和长期累积问题的修复上：

- **渠道与配置修复：** **PR #7664** [已关闭] 修复了一个严重 Bug（#7542），即 `ask_user` 在网关 Web 界面中因通道提前关闭而失败的问题，这对降低用户使用门槛至关重要。**(链接: [PR #7664](https://github.com/zeroclaw-labs/zeroclaw/pull/7664))**
- **长期痛点解决：** **PR #7594** [已关闭] 实现了重要的配置系统重构，引入了类型驱动的别名选择器和自声明配置枚举。这解决了配置路径硬编码的问题，为未来更灵活的配置管理奠定了基础。**(链接: [PR #7594](https://github.com/zeroclaw-labs/zeroclaw/pull/7594))**
- **功能落地：** **PR #7384** [已关闭] 为定时任务（Cron Job）增加了**暂停/恢复**功能，使用户可以直接通过仪表盘管理任务，而无需删除重建。**(链接: [PR #7384](https://github.com/zeroclaw-labs/zeroclaw/pull/7384))**

这些合并表明，项目正在逐步解决一些影响用户体验的痛点和基础设施层面的历史债务。

## 4. 社区热点

今日最受关注的 Issue 反映了社区在**容器化部署和多智能体协作**上的强烈需求：

- **#3642 [已关闭]：“完整版” Docker 镜像需求。** 该 Issue 获得了13条评论，是过去24小时内讨论最活跃的。用户 `LaurensBosscher` 指出，由于部分功能（如 WhatsApp）默认被禁用，普通用户上手较难。社区期望提供一个开箱即用的，包含所有功能标志的“完整版” Docker 镜像。这说明 **ZeroClaw 的部署简便性被认为是阻碍新用户增长的关键因素**。**(链接: [Issue #3642](https://github.com/zeroclaw-labs/zeroclaw/issues/3642))**
- **#6808 [开放]：工作流程、看板自动化与标签清理的 RFC。** 该 RFC 获得了11条评论，专注于治理和项目流程的优化。这通常标志着项目在快速增长后，开始主动进行内部流程的规范化和效率提升。**(链接: [Issue #6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808))**

## 5. Bug 与稳定性

今日报告了多个 Bug，严重程度不一，部分已有修复 PR：

- **高风险（S1 - 工作流阻塞）：**
    - **#7470 [开放]**：`delegate` 工具在 `agentic` 模式下，当目标对象的 `allowed_tools` 为空时，会错误拒绝请求。此问题直接阻碍了多智能体审查/研究场景的实现。目前有3个维护者关注，暂无直接修复 PR。**(链接: [Issue #7470](https://github.com/zeroclaw-labs/zeroclaw/issues/7470))**
    - **#7664 [已关闭]**：`ask_user` 功能在网关 Web 界面中失败。**已通过 PR #7664 修复**。**(链接: [Issue #7542](https://github.com/zeroclaw-labs/zeroclaw/issues/7542), [PR #7664](https://github.com/zeroclaw-labs/zeroclaw/pull/7664))**

- **中等风险（S2 - 功能退化）：**
    - **#6856 [开放]**：`show_tool_calls` 选项在 `[channel]` 配置中缺失，导致通道响应中不显示工具调用详情。**(链接: [Issue #6856](https://github.com/zeroclaw-labs/zeroclaw/issues/6856))**

- **其他标注：**
    - **#5842 [开放]**：跟踪 `extra_args` 字段的安全影响，防止恶意 CLI 标志注入，这是一个需要长期关注的安全审计项。**(链接: [Issue #5842](https://github.com/zeroclaw-labs/zeroclaw/issues/5842))**

## 6. 功能请求与路线图信号

过去24小时内，用户提出了一系列功能请求，其中一些可能与未来的版本规划重合：

- **请求：** 提供包含所有功能标志的“完整版” Docker 镜像 (**#3642**)。
- **请求：** Nix flake 应正确暴露出 `zeroclaw` 包本身，而非仅工具链 (**#6906**)。
- **请求：** 添加 Vonage、Sinch、Plivo、Telnyx 等多个 SMS 通道集成。这些请求（#6494, #6452, #6453, #6451）均由 `theonlyhennygod` 提出，且全部**已关闭**，说明相关功能接入速度极快。
- **请求（已实现）：** 添加 Sonos、Shazam、Spotify、Philips Hue、8Sleep 等第三方工具集成。同样由 `theonlyhennygod` 提出，体现了项目在智能家居和媒体娱乐生态上的快速扩张意图。

从“已关闭”的 Issue 来看（如大量由 `theonlyhennygod` 提出的集成请求），**项目对第三方集成的响应速度极快**，这可能是其吸引用户的一个重要策略。

## 7. 用户反馈摘要

从 Issue 评论中，可以提炼出以下用户痛点和使用场景：

1.  **部署门槛高 (Issue #3642)**：新用户和非技术用户发现在安装和配置时，因部分功能默认禁用而感到困惑，需要“开箱即用”的完整体验。
2.  **配置复杂与易错 (Issue #6856, #7617)**：用户对配置参数感到困惑（如 `show_tool_calls` 缺失），且容易因错误的 TOML 缩进导致配置静默失效。这表明配置文档或配置验证机制有待加强。
3.  **渠道集成不稳定 (Issue #6847, #5662)**：WhatsApp 通道的 QR 码无法显示，QQ 通道的语音消息被多次处理导致数据库重复项。这些是**直接影响用户核心体验**的问题，需要优先修复。
4.  **Bug 响应积极 (Issue #5528)**：用户 `vvmar` 报告了邮件通道配置中的严重逻辑错误（S0级别），该 Issue 已被及时接受和处理，显示了维护团队对高危 Bug 的重视。

## 8. 待处理积压

以下是一些长期未响应或存在停滞风险的 Open Issue 和 PR，值得维护团队关注：

- **累积提交丢失 (Issue #6074)**：跟踪一次批量回滚中丢失的153个提交。该 Issue 已开放超过50天，至今无具体恢复方案，这可能是项目的一个 **“技术债炸弹”**。需要更高优先级介入。**(链接: [Issue #6074](https://github.com/zeroclaw-labs/zeroclaw/issues/6074))**
- **积压 PR 风险**：目前有**46个待合并的 PR**，这是一个显著的数字。其中许多标注了 `needs-author-action`（如 PR #5892, #6693, #7610, #7616 等），表明贡献者可能尚未回应 Review 意见。长期积压不仅会消耗维护者精力，也容易导致代码冲突和贡献者积极性下降。
- **高风险 Open PR (PR #5892)**：修复了两个生产环境阻塞 Bug（`empty tool_choice` 和 `orphaned tool_use`），影响范围包括OpenAI、Bedrock等多个关键Provider。该 PR 自4月19日开出，且需要作者行动，是当前急待解决的风险点。**(链接: [PR #5892](https://github.com/zeroclaw-labs/zeroclaw/pull/5892))**
- **需要关键决策的 RFC (Issue #6293)**：关于“气隙执行模式”的 RFC，通过将 ZeroClaw 拆分为离线和在线两个进程来增强安全性。该提案对架构影响深远，但从5月3日至今仍在讨论阶段，需要项目核心团队进行更明确的决策和规划。**(链接: [Issue #6293](https://github.com/zeroclaw-labs/zeroclaw/issues/6293))**

</details>

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*