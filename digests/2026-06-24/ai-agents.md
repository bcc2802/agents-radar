# OpenClaw 生态日报 2026-06-24

> Issues: 192 | PRs: 500 | 覆盖项目: 13 个 | 生成时间: 2026-06-24 03:32 UTC

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

好的，作为AI智能体与个人AI助手领域开源项目分析师，根据您提供的OpenClaw项目数据，我已为您生成了2026年6月24日的项目动态日报。

---

# OpenClaw 项目日报 | 2026-06-24

## 1. 今日速览

项目今日维持高活跃度，24小时内总计处理了近700条Issue和PR动态。尽管仍有大量新Issue和PR涌入（新开+活跃Issue 141条，待合并PR 457条），但社区和核心维护者也在积极进行问题分类和修复工作（关闭51个Issue，合并/关闭43个PR）。项目发布了一个小版本更新，主要优化了对话模式和模型路由。值得注意的是，与**会话状态管理**、**数据损坏/丢失**和**多代理/插件兼容性**相关的高优先级Bug（P1/P2）依然频繁出现，是当前稳定性的主要挑战。总体来看，项目迭代速度很快，社区贡献活跃，但稳定性和遗留系统迁移问题仍是当前关注焦点。

## 2. 版本发布

-   **新版本**: **v2026.6.10**
    -   **更新内容**:
        -   **对话自动快速模式**: 在简短对话轮次中自动启用快速模式，并在长对话中回退到正常模式，以平衡响应速度和交付可靠性。(#85104) 感谢 @alexph-dev 和 @vincentkoc。
        -   **更可靠的模型路由**: 对Zai模型进行了合成优化，提升了路由稳定性。
    -   **破坏性变更 & 迁移注意事项**: 本次为小版本更新，未提及破坏性变更。建议用户关注快速模式的默认启用行为，确认其是否符合预期使用场景。

## 3. 项目进展

今日关闭/合并的PR主要集中在解决关键的Bug和提升系统鲁棒性：

-   **关键Bug修复**:
    -   **修复ACP核心错误**: PR #96270 修复了 `stringifyNonErrorCause` 函数可能返回 `undefined` 导致的潜在崩溃问题。
    -   **修复外部频道插件审批流程**: PR #96259 和 PR #96140 解决了在执行审批后，对外部频道插件的反馈路由错误问题，确保回复能正确发送到聊天频道。
    -   **修复自动频道简介措辞**: PR #96244 修正了 Mattermost 频道提示语中的措辞不准确问题。
-   **功能与体验改进**:
    -   **OpenShell插件增强**: PR #96073 为OpenShell沙箱创建添加了非敏感环境变量配置支持，提升了灵活性和易用性。
    -   **Web抓取增强**: PR #96268 修复了HTML实体解码时对Unicode星号字符的截断和双重解码问题，提升了内容抓取质量。
-   **性能与稳定性**:
    -   **防止无限重启恢复**: PR #96230 引入了重试预算机制，阻止了在会话卡死后无休止地自动恢复，避免资源耗尽。
    -   **改进Cron任务状态分类**: PR #96266 将可从短暂工具错误中恢复的Cron任务正确分类为 `ok`，避免误报错误。

## 4. 社区热点

-   **#92445 - [PR] 飞书的审计敏感信息脱敏**: 该PR引起了社区的广泛关注，旨在修改飞书频道的消息发送逻辑，对外部联系人（如手机号、邮箱等）进行脱敏处理。这反映了用户端对于**数据合规和隐私保护**的强烈诉求，尤其是在企业级IM（如飞书）集成中。
    -   *链接*: [openclaw/openclaw PR #92445](https://github.com/openclaw/openclaw/pull/92445)
-   **#88838 - 追踪核心会话/聊天记录的SQLite迁移**: 作为一个涉及“钻石龙虾”级别（高优、影响大）的Issue，它持续吸引着大量讨论。该Issue的评论数最高（35条），社区成员、维护者正在激烈讨论通过“accessor seam”模式来迁移底层存储的方案。这说明**核心数据架构的更替**是当前社区最关心的技术债务之一。
    -   *链接*: [openclaw/openclaw Issue #88838](https://github.com/openclaw/openclaw/issues/88838)
-   **#96236 - 请求iOS节点TestFlight邀请**: 一个简单但获得3条回复的功能请求，显示了社区对**移动端原生体验**的渴望。用户不仅希望将OpenClaw作为个人助手，更希望将其集成到日常设备中，如通过iPhone接收推送通知和利用位置感知功能。
    -   *链接*: [openclaw/openclaw Issue #96236](https://github.com/openclaw/openclaw/issues/96236)

## 5. Bug 与稳定性

今日报告的Bug修复工作进展良好，但新报告的及持续存在的P1/P2级问题仍然较多，以下按严重程度排列：

-   **P0/关键 (Critical)**:
    -   **无**。
-   **P1/高 (High)**:
    -   **会话锁死/崩溃**:
        -   *[修复中]* “Subagent abort-settle fails to release .jsonl.lock” (#95833) - 子代理强制终止后锁文件未释放，永久阻塞会话。
        -   *[待审查]* “Stuck-session recovery aborts long-but-active agent runs” (#88870) - 长任务被错误地作为“卡死”会话中止，且提示信息具有误导性。
        -   *[已修复]* “fix(session): stop repeated restart recovery after retry budget” (#96230) - 已通过引入重试预算解决无限恢复问题。
    -   **消息丢失/交付失败**:
        -   *[待修复]* “Subagent completion delivery can fail...” (#92076) - 请求者会话被清除时，子代理结果无法交付。
        -   *[待修复]* “Media generation succeeds but completion delivery fails” (#86034) - 媒体生成成功但交付失败，导致用户误以为生成失败。
-   **P2/中 (Medium)**:
    -   **回归问题 (Regressions)**:
        -   *[已修复]* “Dreaming runs but memory never promotes” (#96118) - v6.9版本的回归问题，已关闭。
        -   *[待修复]* “Telegram richMessages breaks paragraph breaks” (#95554) - v6.9中Telegram富文本格式渲染错误。
        -   *[待分析]* “v2026.6.8: state migration leaves channel conversation-store SQLite empty” (#94939) - 升级后频道对话存储库损坏（0字节），导致Proactive消息（如MS Teams）失效。
    -   **API/模型兼容性**:
        -   *[待修复]* “Native Anthropic path: replaying historical thinking blocks bricks long tool-use threads” (#94228) - 使用Anthropic原生路径时，历史thinking块会导致后续工具调用失败。
        -   *[待分析]* “DeepSeek cache hit rate <10% after 6.x upgrade” (#94518) - 升级后DeepSeek模型缓存命中率骤降，增加成本和延迟。
-   **P3/低 (Low)**:
    -   **UI/UX问题**: “Control UI: auto-derive session title” (#94529), “WebChat render order bug” (#95566) 等。

## 6. 功能请求与路线图信号

-   **核心架构演进**:
    -   **MCP作为压缩提供者**: Issue #96156 提出允许将MCP服务器作为上下文压缩引擎，这为插件化压缩提供了全新的思路，可能成为未来提高大型会话性能的关键路径。
    -   **非伪造的面板调度API**: Issue #71712 提出了为“代理”提供创建和管理自身定时任务的API，同时保证操作来源不可伪造。这表明项目正在向更高级的**自主代理**方向演进。
-   **用户体验提升**:
    -   **命名会话**: Issue #93422 要求支持 `/label` 和 `/new <name>` 命令来命名会话。结合 #94529 的会话标题自动派生请求，可以预见**会话管理**（侧边栏、标签化）将是下一阶段UI优化的重点。
    -   **全局SSRF策略**: Issue #93068 请求提供一个统一的、网关级别的SSRF安全策略配置，而不是让每个子系统单独配置。这反映了用户对**安全易用性**的更高要求。
-   **生态与集成**:
    -   **Cloudflare AI Gateway升级**: Issue #91945 建议将内置的Cloudflare提供商升级到新的REST API，以替代已弃用的Unified API。这表明用户积极跟进上游服务变化，推动项目保持兼容性。
    -   **Exec Shell可配置性**: Issue #49931 要求为Windows上的exec工具提供Shell配置选项。这是典型的**跨平台体验**一致性问题，对非类Unix系统用户至关重要。

## 7. 用户反馈摘要

-   **真实痛点**:
    -   **升级风险**: 多位用户（如 #94939）报告在版本升级后出现数据丢失或服务中断，这导致用户对升级感到犹豫和焦虑。
    -   **错误信息不透明**: Issue #46548 指出当工具调用失败时，只显示“失败”，不提供具体原因，让用户和开发者都难以定位问题。同样，#88870中的误导性提示也让用户感到困惑。
    -   **跨平台体验差距**: Windows用户在issue #93465和#49931中反复遭受ACPX运行失败和Shell硬编码的困扰，表明项目在非macOS系统上的支持仍需加强。
-   **使用场景**:
    -   **企业级应用**: 许多反馈（如 #92445 飞书脱敏、#94939 MS Teams集成）强烈指向企业用户。他们需要合规、稳定、能与现有企业SaaS（如飞书、Teams、飞书等）深度集成的方案。
    -   **个人高级助手**: 用户（如 #96236）渴望一个能在移动设备上运行的、具备主动通知能力的个人助手，将云助手与个人设备深度绑定。
-   **满意/不满意**:
    -   **满意**: 用户对快速迭代和积极修复Bug的社区氛围表示认可。Pull Request和Issue的详尽描述（如#88838）表明开发者和用户都在认真协作。
    -   **不满意**: 尽管修复快，但新出现的P1/P2级稳定性问题（特别是会话状态丢失）仍是用户最大的不满。有用户反馈“session enters zombie state”（#95760），“permanently breaking the session”（#95833），这些“永久性”的破坏性体验严重影响用户信心。

## 8. 待处理积压

以下Issue和PR已长时间未更新或待审查，可能对项目健康度构成风险，提醒维护者关注：

-   **关键Issue**:
    -   **#42840** `<diamond>`: “Feature Request: Add MathJax/LaTeX Support to Control UI” 。自2026-03-11开启，获得7个👍，但近期无实质性进展。作为基础性功能需求，长期搁置可能影响项目在学术和科学领域的吸引力。
        -   *链接*: [Issue #42840] (https://github.com/openclaw/openclaw/issues/42840)
    -   **#73910** `<diamond>`: “BUG: OpenClaw-managed Codex ACP uses isolated CODEX_HOME without auth bridge”。自2026-04-29报告，影响Codex ACP的集成体验，目前仍在等待维护者审查（`needs-maintainer-review`）。
        -   *链接*: [Issue #73910] (https://github.com/openclaw/openclaw/issues/73910)
-   **长期待合并PR**:
    -   **#46303** (P1): “fix: drain inbound debounce buffer and followup queues before SIGUSR1 reload”。一个非常重要的修复，防止热重启时丢失消息。自2026-03-14开启，尽管标记了P1，但状态长期处于“waiting on author”，且存在多处`merge-risk`标记，整合风险较高。
        -   *链接*: [PR #46303] (https://github.com/openclaw/openclaw/pull/46303)
    -   **#59959** (P2): “feat: cute GTK-native Linux App”。面向Linux用户的原生桌面应用。自2026-04-02开启，状态为“waiting on author”。对于扩大用户基础，特别是开发者社区，具有重要意义。
        -   *链接*: [PR #59859] (https://github.com/openclaw/openclaw/pull/59859)

---

## 横向生态对比

好的，作为一名专注于 AI 智能体与个人 AI 助手开源生态的资深技术分析师，我已根据您提供的 2026 年 6 月 24 日各项目的社区动态，为您生成以下横向对比分析报告。

---

# 个人 AI 助手/自主智能体开源生态横向分析报告 (2026-06-24)

## 1. 生态全景

2026年6月24日，个人AI助手开源生态呈现出**“核心颠覆、平台扩展、外部涌现”的三层格局**。以 **OpenClaw** 为首的核心项目正经历从“实验性助手”向“高可靠性生产力平台”的艰难蜕变，其工作重心已从功能堆叠转向解决“会话状态管理”、“数据迁移”和“系统鲁棒性”等核心架构问题。与此同时，**NanoBot、Hermes Agent、CoPaw** 等二级生态项目正积极进行平台化扩展，深耕 Slack、Telegram、飞书等特定集成场景，并围绕模型路由、安全控制等方向进行差异化竞争。此外，以 **PicoClaw、ZeroClaw** 和 **NullClaw** 为代表的新锐力量则通过极致的性能优化、安全架构重铸等“杀手锏”，试图在细分市场建立优势。整个生态呈现出“头部求稳、腰部求全、尾部求新”的健康发展态势。

## 2. 各项目活跃度对比

| 项目 | 今日新/活跃 Issues | 今日新/活跃 PRs | 版本发布 | 核心发现 / 健康度评估 |
| :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 141 | 457 (待合并) | v2026.6.10 | **高活跃，瓶颈期**。社区贡献爆炸，但核心稳定问题（会话状态丢失、数据损坏）突出，迭代速度与质量保障的平衡是主要挑战。 |
| **NanoBot** | 14 | 40 | 无 | **高活跃，快速修复**。模型工具调用 ID 重复、安全绕过等关键 Bug 修复迅速，社区对安全性和模型稳定性诉求强烈。 |
| **Hermes Agent** | 50 | 50 (待合并) | 无 | **高活跃，功能拥堵**。待合并 PR 积压严重（47个），核心痛点聚焦 Token 消耗和平台兼容性（Windows, macOS）。 |
| **PicoClaw** | 1 | 15 | 无 | **中等活跃，安全加固**。修复了 `exec` 漏洞并引入 CSRF 防护，重点在于安全性、跨平台支持（Windows, Android）和远程代理模式。 |
| **NanoClaw** | 1 | 12 | 无 | **中等活跃，依赖升级**。完成了 Chat SDK 升级，新增 Slack Socket Mode、带理由的审批拒绝等功能，项目处于快速迭代期。 |
| **NullClaw** | 1 | 1 | 无 | **低活跃，功能待整合**。主要动态是修复一个 Bug，并等待一个“Cron 子代理”核心功能 PR 合并，项目处于冲刺前平静期。 |
| **IronClaw** | 约 10+ (新) | 20 (合并) | 无 | **高活跃，质量风险**。专注于 Reborn 生态系统修复，交付了自动化管理闭环，但自动化死锁、安全黑名单误报等新问题涌现。 |
| **Lobster AI** | 1 | 11 | 无 | **中等活跃，隐患突出**。5个PR被合并修复了核心工作流，但一个已存在3个月的严重用户故障（升级崩溃）未解决，安全隐患（请求ID可预测）也长期被积压。 |
| **Tiny AGI** | 0 | 0 | 无 | **无活动**。 |
| **Moltis** | 0 | 1 | 无 | **低活跃，积累交付**。`send_image` 工具能力并入，处于功能合并后的稳定期，社区处于观望状态。 |
| **CoPaw (QwenPaw)** | 35 | 50 (待合并) | v1.1.12.post2 | **高活跃，移动为先**。移动端适配是核心主题，但定时任务（Cron）的严重缺陷和高内存占用是当前主要隐患。 |
| **ZeptoClaw** | 0 | 0 | 无 | **无活动**。 |
| **ZeroClaw** | 约 6+ (新) | 50+ (待合并) | 无 | **高活跃，架构重构**。围绕供应链安全、插件权限、内应用升级等架构议题进行深度讨论和贡献，测试覆盖率大幅提升。 |

## 3. OpenClaw 在生态中的定位

- **核心参照与生态基座**：OpenClaw 无疑是该生态的**“锚点项目”**和**“数据参照点”**。其庞大的 Issue/PR 库（近700条动态）、复杂的架构（会话管理、模型路由、MCP 集成）和活跃的开发者社区，使其成为其他项目（如 LobsterAI, CoPaw 等）学习借鉴和集成适配的核心对象。它的迁移问题和稳定缺陷，往往是整个生态共同面临挑战的先声。
- **优势：生态与规模**：OpenClaw 最大的优势在于其**无与伦比的规模和生态号召力**。它拥有最丰富的模型提供商支持、最复杂的插件系统和最广泛的路由特性（如飞书、Mattermost）。技术路线上，它更倾向于**渐进式的、面向企业的复杂集成**。
- **技术路线差异**：与追求极致的 **ZeroClaw（供应链安全）** 或轻量化的 **PicoClaw** 不同，OpenClaw 的技术路线更偏向**“全功能、高复杂度、渐进式稳定”**。它愿意为功能的完整性接受短期内稳定性不足的代价。相比之下，**NanoBot** 和 **Hermes Agent** 则更专注于特定平台和性能优化，技术栈更轻，迭代更快。
- **社区规模对比**：在观测的12个项目中，OpenClaw 的社区活跃度（Issue/PR 讨论、贡献者数量）**遥遥领先**，是唯一一个处于“社区爆炸”阶段的项目。其社区规模可能是位列第二的 Hermes Agent 或 ZeroClaw 的 5-10 倍。

## 4. 共同关注的技术方向

| 技术方向 | 具体诉求 | 涉及项目 | 信号强度 |
| :--- | :--- | :--- | :--- |
| **会话/状态管理的稳定性** | 会话丢失、锁死、数据损坏、内存泄漏。这是所有活跃项目的**头号公敌**。 | **OpenClaw**, **Hermes Agent**, **CoPaw**, **PicoClaw**, **ZeroClaw** | **极高** |
| **模型路由/多提供商支持** | 扩展对更多模型（如 DeepSeek, Kimi, OpenCode）的支持，并提升路由的可靠性、缓存和故障转移能力。 | **OpenClaw**, **NanoBot**, **CoPaw**, **ZeroClaw**, **PicoClaw** | **高** |
| **安全与合规** | SSRF 防护、MCP 工具权限控制、凭证管理、供应链签名、数据脱敏/隐私保护（如飞书）。 | **OpenClaw, NanoBot, PicoClaw, ZeroClaw** | **高** |
| **跨平台适配与集成** | 针对 Telegram, Discord, Slack, 飞书，Mattermost, 移动端（iOS/Android）的深度优化。 | **OpenClaw, NanoBot, Hermes Agent, PicoClaw, NanoClaw, LobsterAI, CoPaw** | **高** |
| **Token 优化与性能** | 减少固定开销、降低 Token 消耗、提升响应速度。 | **Hermes Agent, CoPaw** | **中** |
| **定时任务/自动化（Cron）** | 提升定时任务的可靠性和管理能力。 | **OpenClaw, NullClaw, LobsterAI, CoPaw** | **中** |
| **容器化部署稳定性** | 解决 Docker 配置丢失、共享内存不足等问题。 | **Hermes Agent, NanoClaw, CoPaw** | **中** |

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
| :--- | :--- | :--- | :--- |
| **OpenClaw** | 企业级、全功能、集成枢纽 | 企业团队、高级开发者、需要深度定制的用户 | 复杂的会话管理、MCP 深度集成、模块化网关 |
| **NanoBot** | 社区友好、广泛集成（平台多） | 个人开发者、快速原型验证者、跨平台用户 | 轻量级架构、活跃的模型提供商社区、快速修复 |
| **Hermes Agent** | 研发效能、编码辅助 | 软件工程师、开源贡献者 | 强调 Token 优化、多 Agent 编排（未来）、与 VSCode 等 IDE 集成 |
| **PicoClaw** | 轻量、安全、边缘部署 | 嵌入式/物网开发者、安全敏感用户 | Go 语言实现、极小的二进制体积、强化的安全机制、远程代理模式 |
| **NanoClaw** | **协作与审批** | 团队协作、需要复杂审批工作流的用户 | 创新的“带理由拒绝”审批流程、Slack Socket Mode、扩展点设计 |
| **NullClaw** | **Cron 自动化** | DevOps 工程师、自动化流程构建者 | 核心功能围绕“Cron 子代理”引擎、追求 API 可编程性（JSON输出） |
| **IronClaw** | **Reborn 生态系统** | NEAR 协议生态用户、去中心化应用开发者 | 与 Reborn 平台深度耦合、治理机制、ACL 系统 |
| **LobsterAI** | **Cowork 协作模式** | 需要人机协作进行复杂任务规划的用户 | 独特的“计划确认与持久化”工作流、OpenClaw 集成 |
| **CoPaw** | **移动体验 & 记忆管理** | 移动办公用户、个人知识管理爱好者 | 系统化的移动端适配、持续重构的记忆系统 |
| **ZeroClaw** | **安全与架构韧性** | 企业级架构师、安全运维工程师 | 强调供应链签名（RFC）、内应用升级、插件权限白名单、SSRF 防护 |
| **Moltis** | **多模态交互** | AI 应用开发者、Skill 创建者 | 核心围绕 `send_image` 工具，将多模态能力封装为 Skill |

## 6. 社区热度与成熟度

- **快速迭代与功能创新阶段**：
    - **NanoClaw, CoPaw, PicoClaw**：这些项目社区活跃度高，功能迭代快（PRs 多，合并快），并且能快速响应用户反馈（如 CoPaw 的移动端适配、PicoClaw 的安全漏洞修复）。它们正通过引入新功能和优化体验来快速抢占细分市场。
- **质量巩固与稳定化阶段**：
    - **OpenClaw, Hermes Agent, ZeroClaw**：这些项目已拥有庞大用户基础或面临架构转型压力，其社区讨论和开发重心已从“功能有无”转向“功能好用”。它们通过大量修复 Bug（OpenClaw）、深度讨论架构（ZeroClaw）、以及优化性能（Hermes Agent）来巩固产品质量，为下一代功能迭代奠定基础。
- **低活跃或积累交付阶段**：
    - **NullClaw, LobsterAI, Moltis**：这些项目社区活跃度较低，可能处于功能集成后的静默期、等待关键 PR 合并（如 NullClaw），或者是在积累技术债务后等待爆发（如 LobsterAI 内长期积压的严重问题）。它们需要维护者主动激活社区或引导方向。

## 7. 值得关注的趋势信号

1.  **“体验为王”取代“功能为王”**：社区反馈中（OpenClaw、CoPaw、LobsterAI），对“升级后数据丢失”、“定时任务不可靠”等基础体验问题的投诉，远多于对新功能的渴望。**用户不再满足于“能做什么”，而是要求“稳定地做到”**。这要求所有 AI 智能体项目必须将稳定性视为产品生命线。

2.  **安全与隐私从“锦上添花”变为“入场券”**：无论是企业级用户（飞书脱敏）、还是个人开发者（SSRF 防护、MCP 权限、凭证管理），安全都已从可选项变为必选项。**安全机制的设计不能以牺牲用户体验为代价**（如 IronClaw 的词汇黑名单误杀），项目需在便捷性与安全性之间找到智能平衡点。

3.  **平台化与垂直集成的双轮驱动**：
    - **横向平台化**：NanoBot、Hermes Agent、PicoClaw 都在积极扩展支持的平台和模型提供商，试图成为“万能连接器”。
    - **纵向垂直集成**：CoPaw 深耕“移动 Agent”，NullClaw 聚焦“定时任务”，Moltis 定义“多模态 Skill”。**全栈的深度体验优化，比宽泛的平台覆盖更具竞争力**。

4.  **从“被动响应”到“主动代理”**：
    - 社区对 **Cron 子代理**（OpenClaw, NullClaw）、**自主技能创建**（ZeroClaw）、以及**多 Agent 编排**（Hermes Agent）的探索，预示着**AI 智能体正从“用户叫，我才动”的被动工具，向“自主发现任务、自主规划并执行”的主动代理演进**。这是行业最激动人心的未来方向，也是当前质量挑战的根本来源。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，根据您提供的NanoBot项目数据，我为您生成了2026年6月24日的项目动态日报。

---

# NanoBot 项目动态日报 | 2026-06-24

## 1. 今日速览

今日NanoBot项目社区活跃度较高，24小时内产生了40个PR和14个Issue，项目维护和功能推进节奏良好。**核心聚焦于安全修复、平台扩展和稳定性提升**：两项关键安全漏洞（MCP `enabledTools` 策略绕过）被报告，并已有相应的修复思路；同时，项目成功合并了对**OpenCode**、**Kimi Coding Plan**等新模型提供商的支持，并修复了多个影响用户体验的Bug（如Telegram显示错乱、iOS Safari输入框放大）。此外，WebUI的PWA支持和新侧边栏手势功能正在积极开发中。

## 2. 版本发布

- **无新版本发布。**

## 3. 项目进展

今日共有 **15个 PR 被合并或关闭**，标志着项目在多个维度取得了实质性进展：

- **新提供商支持：**
    - **Kimi Coding Plan**：合并了 PR [#4464](https://github.com/HKUDS/nanobot/pull/4464)，为订阅用户增加了专门的 `kimi_coding` 提供商，扩展了对Kimi平台商业服务的支持。
    - **OpenCode Zen & Go**：合并了 PR [#4476](https://github.com/HKUDS/nanobot/pull/4476)，新增了两个来自OpenCode的系列模型，丰富了用户可选择的模型生态。
- **关键Bug修复：**
    - **工具调用ID重复**：合并了多个PR（[#4443](https://github.com/HKUDS/nanobot/pull/4443)、[#4444](https://github.com/HKUDS/nanobot/pull/4444)），修复了流式响应中因工具调用ID重复导致会话“中毒”（HTTP 400错误）的严重问题，显著提升了Anthropic系列提供商（如Claude）的稳定性。
    - **Telegram消息错乱**：合并了 PR [#4472](https://github.com/HKUDS/nanobot/pull/4472)，修复了依赖 `sendRichMessage` 特性后出现的换行失效和消息闪烁问题。
    - **iOS Safari输入框缩放**：合并了 PR [#4471](https://github.com/HKUDS/nanobot/pull/4471)，通过设置输入框字体大小解决了移动端WebUI的关键UI问题。
- **其他维护与改进：**
    - **Gateway生命周期**：修复了Gateway在停止失败时状态处理不当的问题，提高了后台服务的健壮性。
    - **文档更新**：更新了运行时环境变量的文档，提升了项目的可配置性和透明度。
    - **Node版本升级**：项目依赖已升级至Node 24。

## 4. 社区热点

今日社区讨论的焦点集中在两个方向：**安全性** 和 **模型稳定性**。

- **🔒 最受关注的安全问题：** **Issues [#4434](https://github.com/HKUDS/nanobot/issues/4434)** 和 **[#4435](https://github.com/HKUDS/nanobot/issues/4435)** 报告了MCP `enabledTools` 允许/拒绝列表存在绕过漏洞，可能将未授权的资源和提示暴露给模型。这两条Issue产生了社区讨论，反映出用户对MCP安全机制的高度关注，尤其是在企业或敏感数据场景下。
- **⚙️ 最受关注的稳定性问题：** **Issue [#4442](https://github.com/HKUDS/nanobot/issues/4442)** 报告的“流式响应中重复tool_use ID导致会话阻塞”问题，是今日社区讨论的另一焦点。虽然该Issue本身没有太多评论，但其背后对应了多个PR（[#4443](https://github.com/HKUDS/nanobot/pull/4443)、[#4444](https://github.com/HKUDS/nanobot/pull/4444)）的快速修复，说明这是一个影响广泛的Bug。

## 5. Bug 与稳定性

今日报告的Bug主要集中在前端显示、模型交互和配置持久化方面，按严重程度排列如下：

- **严重：**
    - **MCP安全策略绕过** (`#4434`, `#4435`)：核心安全漏洞，可导致信息泄露。**目前尚无Fix PR**，需要维护者高度关注。
    - **工具调用ID重复导致会话“中毒”** (`#4442`)：已被合并的PR [#4443](https://github.com/HKUDS/nanobot/pull/4443) 和 [#4444](https://github.com/HKUDS/nanobot/pull/4444) **已修复**。
- **中等：**
    - **WebUI渲染 `<thinking/>` 标签** (`#4465`)：将模型内部标签泄露给用户，影响体验。对应的Fix PR [#4466](https://github.com/HKUDS/nanobot/pull/4466) **正在待合并**。
    - **Dream技能重复创建** (`#4467`)：每次运行Dream都会新建技能文件，而不是更新已有技能，影响用户工作流管理。**尚无Fix PR**。
- **低严重性：**
    - **WebUI iOS缩放** (`#4388`)：对应PR [#4471](https://github.com/HKUDS/nanobot/pull/4471) **已合并修复**。
    - **Telegram显示错乱** (`#4470`)：对应PR [#4472](https://github.com/HKUDS/nanobot/pull/4472) **已合并修复**。

## 6. 功能请求与路线图信号

社区对功能扩展的需求集中在**集成更多平台**和**增强用户体验**上。

- **新平台集成**：**PR [#4459](https://github.com/HKUDS/nanobot/pull/4459)** 提出的**Mattermost**频道支持，是继已验证的Telegram和Discord之后，对团队协作工具的重要扩展。此PR目前为**开放状态**，**很可能被纳入下一版本**。
- **PWA与移动端体验**：**PRs [#4480](https://github.com/HKUDS/nanobot/pull/4480) 和[#4479](https://github.com/HKUDS/nanobot/issues/4479)** 提出的PWA支持和新侧边栏滑动手势，表明社区对“类原生”移动WebApp体验的需求强烈。这些功能正在开发中，**接近合并**。
- **Agent能力增强**：**PR [#4485](https://github.com/HKUDS/nanobot/pull/4485)** 提议使子代理（sub-agent）的 `fail_on_tool_error` 可配置，这能提升Agent在处理错误时的鲁棒性。**开放状态，有潜力被接受**。
- **Dream功能优化**：**Issue [#4467](https://github.com/HKUDS/nanobot/issues/4467)** 提出了Dream更新现有技能而非创建副本的需求，反映了用户对自动化工作流精细控制的诉求。此功能**可能在未来版本中被考虑**。

## 7. 用户反馈摘要

从今日的Issues和PR评论中，我们可以提炼出以下真实的用户反馈：

- **痛点：**
    - **模型稳定性**：用户 `tedyan` 和 `zpljd258` 在 `#4442` 和 `#4473` 中报告了因工具调用ID重复导致的整轮对话失败问题，这是一个严重影响使用连续性的致命Bug。
    - **前端体验**：用户 `zpljd258` 在 `#4388` 中报告了iOS Safari上的输入框放大问题，影响移动端日常使用。用户 `ZhouJ-sh` 在 `#4465` 中报告了 `<thinking/>` 标签泄露，破坏了对话的沉浸感。
    - **自动化工作流**：用户 `songsong-hui` 在 `#4467` 中表达了对Dream功能“每次都创建新文件”而非“更新已有文件”的沮丧，希望有更智能的技能管理方式。
- **使用场景**：
    - **编码/开发**：对 `kimi_coding`、`OpenCode` 等编程专用模型的支持，说明用户将NanoBot深度集成于开发工作流中。
    - **团队协作**：PR `#4459` 中的Mattermost支持，暗示用户希望在私有或企业内部的团队通讯工具中使用NanoBot。

## 8. 待处理积压

以下为长期未响应或目前仍未解决的重要事项，建议维护者重点关注：

- **安全漏洞 (高优先级)**
    - **Issues [#4434](https://github.com/HKUDS/nanobot/issues/4434)** 和 **[#4435](https://github.com/HKUDS/nanobot/issues/4435)**：关于MCP `enabledTools` 安全策略绕过。至今无Fix PR或维护者回复，这是潜在的安全风险。
- **长期未合并的PR (中优先级)**
    - **PR [#3732](https://github.com/HKUDS/nanobot/pull/3732)**：`fix(providers): require api_base before local provider wins on keyword match`。该PR存在已超过一个月，旨在修复一个可能被本地提供商“劫持”云端模型的逻辑错误。若持续无人关注，可能为用户配置带来困扰。
- **新功能/增强 (中优先级)**
    - **PR [#4459](https://github.com/HKUDS/nanobot/pull/4459)**：`feat: add Mattermost channel support`。此PR功能完整，是社区热门需求，但尚未获得合并或详细审查。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，以下是根据 Hermes Agent 项目 2026-06-24 的 GitHub 数据生成的每日项目动态。

---

## Hermes Agent 项目动态日报 (2026-06-24)

### 1. 今日速览

今日项目活跃度极高，社区讨论和代码贡献均处于高潮期。**过去24小时内共产生了50个新Issue和50个新PR**，表明项目正经历密集的社区反馈和功能迭代。当前积压了 **47个待合并PR**，远超合并速度（仅3个），存在一定程度的功能开发“拥堵”。**核心贡献集中在性能优化（Token消耗）、网关稳定性（Telegram、Windows、Docker）以及多平台集成（Excel、Feishu、Zulip）**。同时，大量关于安全边界（如Tirith审批、凭证泄露）和配置兼容性的长期Bug依然活跃，项目在扩展功能的同时，亟需关注技术债务的清理。

### 2. 版本发布

无

### 3. 项目进展

今日 PR 合并/关闭数量仅为 3 个，整体推进速度相对缓慢。主要进展体现在对长期遗留问题的修复提议上，但尚未被维护者合并。

- **Telegram 消息无限循环 Bug 已修复**：PR [#48648](https://github.com/NousResearch/hermes-agent/pull/48648) 修复了当流式消息超过 4096 字符限制时，Telegram 网关陷入无限嵌套回复循环的严重Bug。该 PR 已关闭，将对 Telegram 用户体验产生显著改善。
- **MCP 服务器工具不可见问题已关闭**：Issue [#51587](https://github.com/NousResearch/hermes-agent/issues/51587) 报告了用户配置的 MCP 工具无法在 Agent 会话中显示的问题。该 Issue 被关闭，但未给出具体解决方案（标记为`needs-repro`），问题可能需要进一步复现和验证。

### 4. 社区热点

今日社区讨论集中在对项目核心架构的**性能焦虑**和**未来演进的期待**上。

- **🔥 Token 开销：社区最核心的痛点**：Issue [#6839](https://github.com/NousResearch/hermes-agent/issues/6839)（评论 26，👍 14）和 [#4379](https://github.com/NousResearch/hermes-agent/issues/4379)（评论 15）共同揭示了社区对 **Token 过度消耗**的强烈不满。前者提出了“延迟工具加载”的改进方案，后者则通过数据证明每次 API 调用的 73% 都是固定开销。这是社区推动性能优化的核心诉求，直接影响用户的使用成本和模型响应速度。
- **多 Agent 编排：社区的远大理想**：Issue [#5257](https://github.com/NousResearch/hermes-agent/issues/5257)（评论 11，👍 16）提出了通用化 ACP 客户端，使 Hermes 能编排 Claude Code、Copilot 等其他编码 Agent。这反映了社区希望 Hermes 成为**全能 AI 编排中心**的强烈愿望，是项目未来差异化竞争的重要方向。

### 5. Bug 与稳定性

今日报告的 Bug 众多，部分严重问题已影响用户体验。

- **严重**
    - **凭证丢失**：[#19566](https://github.com/NousResearch/hermes-agent/issues/19566) (P1) OpenAI-Codex 的凭证池在刷新时可能丢弃新添加的凭证。这是一个安全与可用性并存的严重问题。
    - **密码泄露**：[#43083](https://github.com/NousResearch/hermes-agent/issues/43083) (P1) 密码被 `***` 替代后，模型读取自身对话历史时再次失败。这表明存在关键的凭证清理逻辑漏洞。
    - **Docker 配置损坏**：[#51579](https://github.com/NousResearch/hermes-agent/issues/51579) (P1) 每次 Docker 容器启动时，自动迁移会清空 `.env` 文件，导致电报等服务的配置丢失。这是对 Docker 部署用户的严重回归。

- **中/高**
    - **Windows 进程残留**：[#38387](https://github.com/NousResearch/hermes-agent/issues/38387) (P2) Windows 上的计划任务会留下无法关闭的空白控制台窗口，严重影响后台服务体验。
    - **Telegram 打字状态卡死**：[#28004](https://github.com/NousResearch/hermes-agent/issues/28004) (P2) Telegram 上的“正在输入…”指示器在响应结束后无限期卡住，影响用户交互体验。
    - **MCP 连接不生效**：[#51587](https://github.com/NousResearch/hermes-agent/issues/51587) (P1) 已关闭，但问题本身严重，显示了 MCP 功能集成的潜在不稳定。
    - **数据库记录错误**：[#51646](https://github.com/NousResearch/hermes-agent/issues/51646) (P2) 网关写入数据库时遗漏了关键字段，导致会话历史丢失，Agent 出现“失忆”。

### 6. 功能请求与路线图信号

今日新提出的功能请求显示了用户对 **“开箱即用”集成**和**精细控制**的强烈需求。

- **Excel 集成**：PR [#44356](https://github.com/NousResearch/hermes-agent/pull/44356) 提出了一个 Excel 侧边栏任务窗格，将 Hermes 直接带入办公场景。这是一个显著的生态扩展信号，若被合并，将极大提升产品在商业领域的价值。
- **飞书 & Zulip 适配**：PR [#49631](https://github.com/NousResearch/hermes-agent/pull/49631) 和 [#3335](https://github.com/NousResearch/hermes-agent/pull/3335) 分别针对飞书和 Zulip 用户。这表明社区正在推动 Hermes 成为**跨平台、跨语言**的通用消息助手。
- **订阅与计费管理**：PR [#51639](https://github.com/NousResearch/hermes-agent/pull/51639) 提议在 TUI 中增加订阅查看和计费命令。这预示着项目可能正在考虑或用户强烈希望有更高级的会员/计费系统。

### 7. 用户反馈摘要

- **高频痛点**：Token 消耗过高是压倒性的呼声。用户在使用本地模型时尤其强烈，每次调用注入数千 Token 的固定开销成为主要瓶颈。
- **平台依赖性问题**：用户对特定平台的 Bug 非常敏感。例如，macOS 桌面应用无法启动（[#49787](https://github.com/NousResearch/hermes-agent/issues/49787)）、macOS 上 `openai-codex` 失败（[#13834](https://github.com/NousResearch/hermes-agent/issues/13834)）、以及 Windows 上安装和运行的种种问题（[#38387](https://github.com/NousResearch/hermes-agent/issues/38387), [#26044](https://github.com/NousResearch/hermes-agent/issues/26044)），表明跨平台兼容性是明显短板。
- **安全期望**：用户对安全控制有明确期望。如[#35357](https://github.com/NousResearch/hermes-agent/issues/35357)所述，仅对 Shell 命令进行审批，而对 `write_file` 等非 Shell 工具无审批，用户认为这是一个安全漏洞。
- **配置困惑**：用户对某些配置项失效感到困惑，如 `auxiliary.compression.provider` 在切换模型后失效（[#27538](https://github.com/NousResearch/hermes-agent/issues/27538)）和 `terminal.working_dir` 不生效（[#51636](https://github.com/NousResearch/hermes-agent/issues/51636)），反映配置系统逻辑存在不一致。

### 8. 待处理积压

- **长期遗留功能请求**：
    - [PR #22648](https://github.com/NousResearch/hermes-agent/pull/22648) **(P3)**：为 Ollama 添加云搜索/提取功能。自 2026-05-09 以来无更新，但作为本地部署用户的扩展，值得关注。
    - [PR #8427](https://github.com/NousResearch/hermes-agent/pull/8427) **(P3)**：添加 Vertex AI 作为 Gemini 模型的提供商。这是一个企业级功能，已开放2个月未合并，可能错过企业用户窗口。
- **需要维护者关注的决策**：
    - [Issue #51646](https://github.com/NousResearch/hermes-agent/issues/51646) **(P2)**：网关“失忆”Bug，涉及到核心的会话管理逻辑，需要尽快确认并讨论解决方案，而非仅标记为 `needs-repro`。
    - [PR #51305](https://github.com/NousResearch/hermes-agent/pull/51305) **(P2)**：修复多个 CVE 的依赖更新 PR，是持续的安全维护，应优先合并。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，以下是基于您提供的数据生成的PicoClaw项目动态日报。

---

# PicoClaw 项目动态日报 | 2026-06-24

## 1. 今日速览

今日项目活跃度**中等偏高**。社区贡献稳健，共有15个PR处于活跃状态，其中5个被合并/关闭。值得关注的是，核心安全与稳定性方面取得了重要进展，包括修复了`exec`命令中自定义允许规则绕过deny模式的安全漏洞、引入了跨站请求防护，并解决了Windows和Android/Termux平台上的特定Bug。此外，功能开发持续推进，AWS Bedrock提示缓存和远程WebSocket代理模式等新特性正在集成中。整体来看，项目在保持功能迭代的同时，对安全性和跨平台兼容性的投入显著增加。

## 2. 版本发布

**无**。过去24小时内无新版本发布。

## 3. 项目进展

今日项目主要围绕**安全加固**、**Bug修复**和**代码质量**进行推进，共有5个重要PR被合并/关闭，标志着项目稳定性的提升：

- **[安全] 修复 `exec` 命令自定义允许规则漏洞 (`#3161`)**: 解决了当命令匹配 `custom_allow_patterns` 时，deny模式完全失效的严重问题。此修复确保即使命令被允许，deny模式依然生效，防止了潜在的安全绕行，例如允许jq命令但可执行读取环境变量等危险操作。**（已关闭/合并）**
- **[安全] 新增跨站请求防护 (`#3160`)**: 通过对 `/api/auth/setup` 端点添加 `Sec-Fetch-Site` 等浏览器来源校验，拒绝跨站点的首次设置请求，防止了CSRF攻击，保护了Dashboard的初始密码设置流程。**（待合并）**
- **[Bug修复] 修复OpenAI兼容API中的 `seed` 泄露问题 (`#3154`)**: 针对火山引擎豆包Seed模型在工具调用时，有时会将`<seed:tool_call>` XML原始内容泄露到`message.content`字段的问题提供了修复。此补丁清理了非标准输出，确保了与标准API的兼容性。**（已关闭/合并）**
- **[Bug修复] 修复了多个lint警告和潜在类型断言错误**:
    - `PR #3059`: 显式忽略错误路径和重试循环中的 `Close()` 错误，解决lint警告，提升代码健壮性。**（已关闭/合并）**
    - `PR #3054`: 修复了 `LINEChannel.Send` 对 `sync.Map` 值进行类型断言时缺少`ok`检查的问题，防止类型不匹配时发生panic。**（已关闭/合并）**
- **[Bug修复] 恢复Web会话详情历史记录 (`#3047`)**: 修复了会话详情API (`GET /api/sessions/{id}`) 无法展示已归档历史消息的问题，同时保持了列表接口的高效分页。**（已关闭/合并）**

## 4. 社区热点

今日社区讨论集中在两个核心问题上：

1.  **Windows平台QQ频道连接失败 (`#3015`)**:
    - **状态**: 已关闭 (stale).
    - **链接**: [Issue #3015](https://github.com/sipeed/picoclaw/issues/3015)
    - **分析**: 这是一个持续近三周的问题。用户报告在Windows的Release版本上，运行 `picoclaw gateway` 时，QQ频道因从 `bots.qq.com` 获取App Access Token超时而失败，而Pico频道功能正常。该问题虽是Windows特有，但关联到QQ频道模块的核心连接机制。虽然目前标记为stale关闭，但连接稳定性的反馈值得维护者在下一版本中关注。

2.  **Android/Termux上进程钩子导致Gateway崩溃 (`#3164`)**:
    - **状态**: 已开启（活跃）.
    - **链接**: [Issue #3164](https://github.com/sipeed/picoclaw/issues/3164)
    - **分析**: 这是今日新报告的问题。用户在Android/Termux环境下降级到v0.2.9版本后，任何JSON-RPC over stdio的进程钩子都会在启动2秒内导致gateway崩溃。即使是极简的 "hello world" 钩子也无法工作。该问题影响移动端部署和自动化工作流，对希望在手机上运行PicoClaw的用户构成显著障碍。

## 5. Bug 与稳定性

今日报告的Bug按严重程度排列如下：

- **严重 (Critical)**:
    - **[新] Android/Termux进程钩子崩溃 (`#3164`)**: 在Termux环境下，任何进程钩子都会导致gateway启动后立即崩溃，为移动端部署带来重大障碍。**（暂无Fix PR）**
- **中 (Medium)**:
    - **[新] 跨站点请求设置风险 (`#3160`)**: 报告了一个对 `/api/auth/setup` 端点的CSRF风险，虽然已有修复PR，但在合并前仍构成潜在安全威胁。**（已有Fix PR #3160）**
    - **[新] `exec`命令安全绕过 (`#3161`)**: 自定义允许规则会禁用deny模式，允许恶意行为绕过安全检查。**（已有Fix PR #3161）**
- **低 (Low)**:
    - **[旧] Windows QQ频道连接失败 (`#3015`)**: 已标记为stale并关闭。影响特定平台用户的功能体验。**（无Fix PR，已关闭）**

## 6. 功能请求与路线图信号

今日有两个值得关注的新功能PR，可能被纳入下一版本：

- **[新功能] AWS Bedrock 提示缓存 (`#3163`)**: 这是一个重要的性能优化PR，为AWS Bedrock Converse API集成了显式的提示缓存点。通过在`system`、`tools`和`messages`中插入缓存点，可以显著降低重复请求的成本（读取时按约0.1倍输入算费）。这对于使用AWS Bedrock和较长上下文的用户是重大利好，信号强烈。
- **[新功能] 远程Pico WebSocket代理模式 (`#3118`)**: 为`picoclaw agent`命令增加了一个`--remote`参数，使其能够通过WebSocket连接到远程的Pico实例。这扩展了PicoClaw作为Agent的部署模式，使其能够与不在同一台机器上的Pico网关通信，为分布式架构提供了可能性。

## 7. 用户反馈摘要

从本日活跃的Issues评论中，可以提炼出以下用户真实反馈：

- **痛点明确**: Windows用户对QQ频道连接的稳定性非常敏感。连接失败问题虽已关闭，但其持续时间长、影响核心功能，反映了跨平台兼容性仍是项目的软肋。用户反馈显示：“Pico channel works normally”，说明问题高度特定于QQ协议的实现。
- **使用场景**: Android/Termux用户正在探索在移动设备上自主运行AI Agent，进程钩子是实现自定义逻辑和自动化的关键。当前的崩溃问题阻碍了这一场景的落地，用户期望地是一个稳定、可扩展的移动端部署方案。
- **满意点**: 从对**Telegram**功能的PR (`#2975`) 反馈看，社区对提升群聊交互体验（如将回复Bot消息视为@提及）表现出兴趣，表明用户正在积极将PicoClaw集成到更复杂的社交互动场景中。

## 8. 待处理积压

以下为长期未响应或有待关注的重要Issue/PR：

- **[PR #2975] feat(telegram): 回复Bot消息视为群聊提及**: 该PR已提交超过三周，且添加了有用的用户体验改进。目前仍为“Open”状态，建议维护者尽快合并或提供反馈。
    - 作者: Jlan45 | 更新: 2026-06-23 | 链接: [PR #2975](https://github.com/sipeed/picoclaw/pull/2975)
- **[PR #3118] 添加远程Pico WebSocket代理模式**: 这是一个重要的架构性功能，自6月12日提交以来尚未合并，状态存疑。如果路线图支持，应尽快评估并推进。
    - 作者: jp39 | 更新: 2026-06-23 | 链接: [PR #3118](https://github.com/sipeed/picoclaw/pull/3118)

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

好的，以下是基于您提供的 GitHub 数据生成的 NanoClaw 项目动态日报。

---

# NanoClaw 项目动态日报 | 2026-06-24

## 今日速览

今日项目活跃度极高，24小时内处理了12个Pull Requests，展现出强大的协作与集成能力。核心围绕 **依赖升级**（Chat SDK 4.29.0）、**功能增强**（Slack Socket Mode、扩展点缝、带理由拒绝审批）及 **基础设施改进**（容器性能）展开，显示出项目已进入快速迭代阶段。尽管新 Issue 数量较少，但高质量的 PR 流表明核心开发团队和社区贡献者的工作重心在代码交付而非问题报告上。项目整体健康状况良好。

## 项目进展

过去24小时是“大丰收”的一天，共有 **8 个 PR 被合并或关闭**，推动了多项关键特性与修复落地：

- **依赖体系升级 (Chat SDK 4.29.0)**：贡献者 `gabi-simons` 完成了一系列重要合并，包括 `#2834` (核心 `main` 分支) 、`#2835` (频道适配器 `channels` 分支) 和 `#2836` (提供者注册表 `providers` 分支)。此次升级锁定了 `@chat-adapter/*` 与 `chat` 软件包的版本，确保整个安装表面的类型一致性。此系列合并为后续功能奠定了坚实基础。
- **Slack Socket Mode 支持**：`gabi-simons` 提交的 `#2837` 已合并，新增的 Socket Mode 允许 Slack 集成通过 WebSocket 连接，无需公开 HTTP 端点，对本地开发和 NAT 环境下的用户体验提升巨大。
- **带理由的审批拒绝**：`moshe-nanoco` 的 `#2832`（待合并）引入了一项重要的审批交互优化。模块审批卡上新增“带理由拒绝”按钮，使拒绝方可以附加一行理由，该理由会回传给请求的 Agent，使 AI 能够理解拒绝原因并进行适应性调整。
- **技能更新体验优化**：`Koshkoshinsk` 的 `#2826` 已合并，修复了 `更新-nanoclaw` 流程中将技能更新视为可选步骤的问题。现在，系统会主动提示用户更新技能，并且当用户重新应用配置时会重建容器，确保技能更新被正确加载。
- **引导技巧 (Hook Surface Guard)**：`javexed` 的 `#2833` 已合并。此 PR 旨在添加代码引导与规范检查，确保新的 PR 遵循项目贡献指南，提升整体代码质量与协作效率。

**项目推进程度**：此次更新标志着 NanoClaw 在 **依赖管理、开发者/用户交互流程、AI Agent 协作深度** 三个关键维度上迈出了坚实一步。尤其是 Slack 的 Socket 支持和带理由的拒绝功能，直接提升了产品的可用性和智能性。

## 社区热点

尽管今日的 Issues 和 PRs 评论数普遍不高，但有两个主题引发了显著的关注：

- **[#2840] Nanoclaw v2 binds port 3000 of external host ip for slack**：
    - **讨论热度**：作为今日唯一的活跃 Issue，其提出的“端口占用导致隧道失效”问题直击 Slack 集成的安全与配置核心。
    - **背后诉求**：用户希望遵循“正确且安全”的隧道配置方式，但发现系统自动占用了关键端口（3000），导致隧道功能无效。这实际上是一个 **可用性与安全性设计冲突** 的反馈。用户担心这种“不走隧道”的默认行为可能带来安全隐患。这可能需要项目方调整端口绑定逻辑，或在文档中提供更明确的端口冲突解决指南。

- **[#2771] perf(container): --shm-size=1g + --init for agent containers** (待处理)：
    - **内容分析**：虽然创建于8天前，但今日仍有更新。这个 PR 旨在解决 `agent-browser` (Chromium) 在容器中因默认共享内存不足而崩溃的问题。这背后反映了 **高级功能（如Browser Agent）对底层基础设施的依赖**，以及社区对项目“开箱即用”稳定性的期待。

## Bug 与稳定性

今日报告了一个 Bug，但暂无活跃的修复 PR。

- **中等严重性：[#2840] Slack集成端口绑定冲突** - 用户报告在安装并配置 Slack 集成时，NanoClaw v2 自动将 `localhost:3000` 绑定到了外部 IP，导致用户建议的安全隧道方案失效。这是一个正确的行为应该是一个配置问题或设计缺陷，直接影响了 Slack 集成的安全配置路径。

## 功能请求与路线图信号

今日未收到新的显式功能请求 Issue，但从活跃的 PR 中，我们可以看出未来的路线图方向：

- **高级 Agent 行为控制**：
    - **[#2832] 带理由的拒绝**：此功能是 AI-Agent 协作中的一次重要交互升级。它从简单的“是/否”决策，迈向了“解释性拒绝”。这表明项目正在探索让 Agent 不仅仅是执行任务，更能理解否决背后的业务逻辑，从而提高任务成功率。此特性很可能被纳入下一个重要版本。
- **基础设施稳定性改进**：
    - **[#2771] 容器性能优化**：添加 `--shm-size=1g` 和 `--init` 参数的建议，反映出项目对运行复杂、资源密集型 Agent（如Browser Agent）场景的重视。这个 PR 大概率会被合并，以解决用户在新手阶段遇到的 Chromium 崩溃问题，属于“性价比”极高的小改动。

## 用户反馈摘要

从今日的 Issues/PRs 评论中，可以提炼出以下用户反馈趋势：

- **对安全性和正确性的高要求**：用户 `sirpy` 明确指出了 `#2840` 中的安全问题，并表达了对“正确且安全”的配置路径的追求。这表明项目的早期用户群具备一定的技术实力和安全意识，对产品的配置模式有较高期待。
- **对配置繁琐度的抱怨（潜在）**：`#2840` 中用户需要手动创建隧道，但发现系统自动绑定端口导致其努力白费，这暴露出项目在“自动化”和“用户意图理解”方面可能存在脱节。用户希望工具能自动适配或清晰地解释其默认行为。

## 待处理积压

- **[#2771] perf(container): --shm-size=1g + --init for agent containers** (8天前创建，开放性高)
    - **重要性**：高。直接影响所有使用 `agent-browser`（浏览器自动化）功能的用户，是常见的“屏幕截图不显示”或“浏览器崩溃”问题的根本原因之一。
    - **状态**：已停滞8天，建议维护者尽快审核合并。这属于一种“低风险、高收益”的稳定性修复。 ([链接](https://github.com/nanocoai/nanoclaw/pull/2771))

- **[#2842] Generic inert extension-point seams** (开放性高)
    - **重要性**：中。这是一个架构层面的演进，旨在为下游 fork 提供清晰的扩展点，而不会对上游主项目造成侵入性。虽然对普通用户影响不大，但对下游维护者和组织具有战略意义。需要更多讨论和审查。 ([链接](https://github.com/nanocoai/nanoclaw/pull/2842))

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

好的，这是为您生成的 NullClaw 项目动态日报。

---

# NullClaw 项目动态日报 | 2026-06-24

**数据来源:** github.com/nullclaw/nullclaw

### 1. 今日速览

今日项目活跃度较低，未见新版本发布或新功能合并。主要动态为旧有问题的修复与长期PR的持续跟进。**#967 号 Bug 已被关闭**，解决了部分用户遇到的“NoResponseContent”报错问题。同时，**#783 号关于 Cron 子代理的重磅功能 PR** 仍在等待合并，显示出项目在任务调度自动化方面的进展但尚未落地。整体来看，项目处于迭代后的稳定期或功能开发冲刺前的平静期。

### 2. 版本发布

无

### 3. 项目进展

- **Bug 修复推进**：持续困扰部分用户的 `NoResponseContent` 错误（Issue #967）已被关闭。这表明开发团队已定位并解决了该问题，提升了特定场景下的稳定性。
  - 链接: [Issue #967](https://github.com/nullclaw/nullclaw/issues/967)

- **核心功能待合并**：**#783 号 PR** 在近24小时内获得了更新，表明贡献者仍在积极维护。该 PR 引入“Cron 子代理引擎”是一个重大功能升级，包含数据库调度、历史记录、安全加固以及 JSON 输出格式支持。其合并将极大增强项目的自动化能力和可观测性。
  - 链接: [PR #783](https://github.com/nullclaw/nullclaw/pull/783)

### 4. 社区热点

- **#967 [Closed] `error: NoResponseContent`**：该 Issue 是过去24小时内唯一有动态的议题。虽然已经被关闭，但其讨论周期较长（从6月20日到6月23日），且社区用户提供了详细的复现步骤和环境信息（Win11, Agnes-2.0-Flash 模型，>50%复现率）。这表明用户对AI Agent基础功能的稳定性（尤其是模型交互层面）有较高且直接的要求。
  - 链接: [Issue #967](https://github.com/nullclaw/nullclaw/issues/967)

### 5. Bug 与稳定性

| 严重程度 | Bug/问题 | 描述 | 状态 | Fix PR/备注 |
| :--- | :--- | :--- | :--- | :--- |
| **高** | #967 `NoResponseContent` | 在Windows 11上，与Agnes-2.0-Flash模型交互时，程序返回 `NoResponseContent` 错误，复现率高（>50%）。已由用户提交详细的环境和日志。 | **已关闭** | 该问题已被修复并关闭。 |

### 6. 功能请求与路线图信号

- **Cron 子代理 (Cron subagent)**：来自 PR #783 的功能。这是一个强烈信号，表明项目正在向**定时任务自动化**方向拓展，使用户能构建更复杂的 Agent 工作流（如定时抓取、定时报告）。
  - 链接: [PR #783](https://github.com/nullclaw/nullclaw/pull/783)

- **JSON CLI 输出**： #783 PR 同样引入了 `cron list --json` 格式输出。这反映了**开发者对可编程性和集成能力**的需求，使得其他脚本或工具可以更容易地解析 NullClaw 的输出。

### 7. 用户反馈摘要

从 #967 Issue 的评论中可以提取出以下用户反馈：

- **痛点**：用户指出了在高频使用特定模型（Agnes-2.0-Flash）时，Agent 体验极差（27秒等待后无响应）。明确指出“apikey”配置生效，但 NullClaw 自身的调用层存在兼容性或稳定性问题。
- **使用场景**：日常的`agent -m "你好！"`基本对话场景。
- **建议**：用户通过对比其他客户端（“picocla...”）表现正常，暗示了 NullClaw 的 API 调用层可能存在问题，而不仅仅是模型或账号问题。

### 8. 待处理积压

- **PR #783 `feat(cron): cron subagent, run history, JSON output, security hardening`**：该PR从2026年4月7日创建至今仍未合并，已累计2个多月。虽然贡献者仍在更新，但长期等待合并可能影响社区贡献者的积极性，并导致功能分支与主分支产生较大差异。建议项目维护者尽快安排 review 与合并，或给出明确的决策反馈。
  - 链接: [PR #783](https://github.com/nullclaw/nullclaw/pull/783)

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，以下是根据您提供的 IronClaw 项目数据生成的 2026-06-24 项目动态日报。

---

# IronClaw 项目日报 | 2026年06月24日

## 1. 今日速览

今日项目**活跃度极高**，Issues 和 PR 数量均处于近期高位。核心团队正在集中精力解决 Reborn 生态系统的多个关键问题，包括**认证、内存管理、自动化支持以及工具权限系统**。尽管修复了数十个 Bug，但新发现的 **自动化死锁** 和 **模型安全词汇检查误报** 等问题暗示系统复杂性正在增加。当前项目健康度 **良好但需关注质量风险**，重点正在从功能开发转向稳定性与用户体验打磨。

## 2. 版本发布

**无**。过去24小时内无新版本发布。

## 3. 项目进展

今日共 **合并/关闭 20 个 PR**，完成了多项关键功能交付和修复，项目在 Reborn 平台的技术债清理和功能完备性上迈出了坚实一步。

### 核心功能交付与修复
- **[#5133] feat(reborn): add Reborn automation delete support**：实现了 Reborn 自动化规则的删除功能，包括 WebUI v2 的 API 路由和前端确认弹窗。
- **[#4969] fix(google-wasm): auth required errors**：修复了 Google WASM 工具（Drive, Docs等）在凭证失效时返回模糊错误的问题，现在会正确触发 `auth_required` 流程，这是用户长期抱怨的痛点。
- **[#5172] Fix Reborn credential delete and reauth**：修复了 Reborn 环境下的凭证删除和重新认证流程，解决了凭据失效后无法顺畅恢复使用的问题。
- **[#5152] feat(slack): move setup into WebUI**：将 Slack 的配置流程从复杂的 TOML 文件迁移到 WebUI 界面，降低了用户的使用门槛。
- **[#5166] Wire dynamic Slack routine delivery** 和 **[#5164] Restore Slack routine outbound targets**：完成了 Slack 作为自动化任务输出目标的功能，使得自动化结果可以直接推送到 Slack。

### 基础设施与代码质量改进
- **[#5168] fix: correct Reborn GitHub API requests**：修正了 Reborn 集成中 GitHub API 请求的格式问题，提升了与 GitHub 交互的兼容性。
- **[#5122] 和 [#5121] Add Reborn automation delete/pause-resume support**：补全了自动化管理的基础增删改查（CRUD）能力，核心功能闭环基本达成。

## 4. 社区热点

今日社区讨论聚焦于 **Reborn 生态系统的复杂性和用户控制权**。

- **[#5173] Daily ironclaw failure taxonomy — 2026-06-23**：由维护者 `pranavraja99` 创建的自动化故障分类报告，虽评论为0，但其分析了115个失败的基准测试，指出多数失败源于基准测试本身的缺陷，这可能导致社区对项目稳定性的误判。**这揭示了项目缺乏清晰的“质量信号”来区分模型问题与基准测试问题。**
- **[#5169] Bundled skills trip the prompt-safety vocabulary denylist**：用户 `zetyquickly` 报告了一个 “clean-setup” 复现的严重问题：一个善意的请求因为捆绑技能中包含了 “Authorization” 等常规API词汇而触发安全黑名单，导致任务静默失败并显示为 “临时系统问题”。**这反映了安全策略过于激进，对开发者和高级用户造成困扰，社区诉求是希望得到更透明的错误提示或更智能的词汇过滤机制。**
- **[#5129] [Reborn] Investigate Always approve not working for outbound_delivery_target_set**：用户 `think-in-universe` 报告了 “始终允许” 功能在特定场景下失效。**这触及自动化信任模型的核心，社区希望自动化能够真正做到“无人值守”，任何自动化过程中的意外中断都会严重破坏用户体验。**

## 5. Bug 与稳定性

今日报告的 Bug 涉及数据安全、死锁和 UI/UX 问题，严重程度较高。

| 严重程度 | Issues / PR | 描述 | 状态 |
| :--- | :--- | :--- | :--- |
| **高** | **[#5169] Bundled skills trip the prompt-safety vocabulary denylist** | 安全词汇过滤器误杀，导致正常功能静默失败，并给出误导性错误提示。 | 开放，无修复 PR |
| **高** | **[#5148] Turn scheduler heartbeat can self-deadlock** | 调度器心跳与状态更新冲突，导致用户进程被“永久”阻塞，需要重启才能恢复。 | 开放，无修复 PR |
| **中** | **[#5147] Flaky test: trigger_poller_does_not_submit_turn_for_unpaired_actor** | 不稳定的测试用例，间歇性导致合并队列被阻塞，影响团队开发效率。 | 开放，无修复 PR |
| **中** | **[#4986] [Reborn] Recurring automation can become permanently blocked waiting for tool approval** | 自动化的工具审批等待可能导致永久阻塞，与 `#5129` 问题呼应。 | 开放，无修复 PR |
| **中** | **[#4640] [bug] Reborn gsuite google-calendar list_events returns oldest/unordered events** | Google Calendar 工具工作不正常，返回的是最老的事件而非未来的事件，数据价值极低。 | 开放，无修复 PR |
| **低** | **[#5157] Inference section sometimes missing from Settings** | 在 Railway 部署环境下，设置页面缺少“推理”配置项。 | 开放，无修复 PR |
| **低** | **[#5146] No button to deactivate an extension on Extensions page** | 扩展管理页面缺少“停用”按钮，用户无法在不卸载的情况下关闭扩展。 | 开放，无修复 PR |

**注意：** 此次无 PR 被标记为修复上述 Bug，意味着这些问题正在成为新的待办积压。

## 6. 功能请求与路线图信号

- **自动化管理闭环**：`[#5122, #5121]` 的关闭标志着自动化管理的增、删、暂停、恢复能力已就绪。加上今日合并的删除功能，自动化全生命周期管理已基本完成。`[#5129]` 中 “Always approve” 的问题是下一个需要攻克的关键障碍。
- **用户数据主权与透明性**：
    - **[#5167] Stop tracking `dist` in git**：有核心成员提出将 `dist` 目录从 git 中移除，这能减少 PR 噪音，并确保构建产物与当前代码一致。这是项目成熟化的信号。
    - **[#5144] Show NEAR AI default base URL in provider card**：用户希望在供应商卡片上显示默认的 API 地址，而不是显示 `None`，以减少困惑。
    - **[#5163] feat(memory): model memory as a userland extension**：一个大型 PR，将核心的记忆层解耦为用户空间的扩展。这暗示了项目的架构演进方向：**通过扩展机制提供更强的模块化和可定制性**。

## 7. 用户反馈摘要

- **痛点一：认证与权限体验不佳**
    - **[#3733] Invalid Gmail token shows success/activated toast**：用户 `sunglow666` 反馈，即使输入了错误的 Gmail 令牌，系统也会显示“激活成功”的 Toast 通知。这种虚假的成功反馈极其误导，是典型的负面体验。
    - **[#3732] Gmail auth gate shows inconsistent UI**：同样来自 `sunglow666`，抱怨 Gmail 的认证界面在不同对话中呈现出不一致的交互方式（OAuth链接 vs 手动输入令牌），令用户感到困惑。

- **痛点二：错误处理和反馈机制不完善**
    - **[#4991] WASM google-drive auth failures dead-end**：用户 `zetyquickly` 抱怨当 Drive 凭证过期时，工具返回的是泛化的 `operation_failed` 错误，而不是提示用户重新认证，导致流程硬阻断 (`dead-end`)。这与 `#4969` 的修复直接相关，说明该修复非常及时。
    - **[#4640] google-calendar list_events returns oldest events**：用户 `BenKurrek` 发现日历工具的行为完全不符合预期，反映了工具“开箱即用”的体验不佳。

## 8. 待处理积压

- **[#4108] Nightly E2E failed**：一个持续了近一个月的每日 E2E 测试失败报告。虽然可能由环境波动引起，但持续未解决会影响团队对稳定性的信心。[[链接](https://github.com/nearai/ironclaw/issues/4108)]
- **[#3733] Invalid Gmail token shows success/activated toast**：已开放超过一个月，是优化用户体验和认证流程的核心 Bug。尽管已有关联的修复 PR（如 #4969），但该 Issue 本身尚未关闭，表明 Toast 提示层面的问题仍未彻底解决。[[链接](https://github.com/nearai/ironclaw/issues/3733)]
- **[#4640] Reborn gsuite google-calendar list_events returns oldest/unordered events**：已开放两周，是一个非常直观的功能缺陷，会严重影响依赖日历功能的用户的初次使用印象。[[链接](https://github.com/nearai/ironclaw/issues/4640)]

---

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，我将根据您提供的LobsterAI GitHub数据，为您生成2026年6月24日的项目动态日报。

---

# LobsterAI 项目动态日报 | 2026-06-24

## 1. 今日速览

今日项目活跃度中等偏上。**Issue 池保持稳定**，仅有一条用户报告的严重Bug持续未解决。**Pull Request 活动频繁**，过去24小时内共有11条PR更新，其中5条已合并/关闭，6条待处理。项目团队在**核心协作功能**（cowork）、**定时任务**（scheduled-task）和**OpenClaw网关**方面进行了重要的缺陷修复和功能增强。特别值得注意的是，一个重大的新功能——集成**LiteLLM作为AI网关提供商**的PR已被提出，表明项目正在积极拓展其AI模型接入的生态。

## 2. 版本发布

无新版本发布。

## 3. 项目进展

今日合并/关闭的5条PR（#2192, #2191, #2190, #2189, #2188）主要由社区贡献者完成，代表了项目在稳定性和功能完善上的重要进展：

- **核心工作流优化**：PR #2192 为 “Cowork” 协作模式增加了**持久化计划确认流程**。这意味着AI生成的计划在被用户确认或修改前会保持活跃，提升了计划的可靠性和用户控制力。这是一个重要的用户体验改进。
- **定时任务稳定性提升**：系列PR（#2191, #2190, #2189）专注于修复OpenClaw网关下的定时任务问题。包括**完善启动状态显示**、**同步Cron运行会话**（避免重复创建会话）、以及**启动时自动迁移旧的Cron数据存储格式**。这些修复表明项目正在积极解决其核心调度功能的稳定性问题。
- **项目推进整体评估**：项目团队成功修复了与OpenClaw集成的关键遗留问题，并优化了核心的协作工作流，为下一阶段的功能迭代奠定了更稳定的基础。

## 4. 社区热点

- **#1400 [OPEN] 严重Bug：4.1版本升级后反复重启**
  - **链接**: [Issue #1400](https://github.com/netease-youdao/LobsterAI/issue/1400)
  - **热度分析**: 该Issue是今日唯一活跃的Issue，已有6条评论。用户 `danielmonlite` 报告了一个严重影响使用的崩溃问题，并从4月3日创建至今仍未关闭，表明用户等待时间较长，耐心可能已达极限。
  - **背后诉求**: 用户的核心诉求不仅是解决当前的崩溃问题，还包含了**升级的平滑性**和**配置的兼容性**。用户提到了自定义LLM（qwen3.5-plus）无法调用，可能与LobsterAI默认配置冲突，这暴露出项目在配置管理和版本升级指导方面存在短板。

## 5. Bug 与稳定性

根据严重程度排列如下：

1.  **严重: 4.1版本升级崩溃** (Issue #1400)
    - **状态**: 开放，未解决
    - **描述**: 用户在升级到4.1版本后，网关反复启动失败并陷入无限循环。同时，升级前存在自定义LLM（qwen3.5-plus）无法调用的Bug。项目处于“彻底瘫痪”状态。
    - **链接**: [Issue #1400](https://github.com/netease-youdao/LobsterAI/issue/1400)
    - **是否已有Fix PR**: 否

2.  **已修复: OpenClaw定时任务数据迁移** (PR #2189)
    - **状态**: 已合并/关闭
    - **描述**: 修复了旧版OpenClaw定时任务数据在启动时未被正确处理的问题。
    - **链接**: [PR #2189](https://github.com/netease-youdao/LobsterAI/pull/2189)

3.  **已修复: OpenClaw定时任务会话同步** (PR #2190)
    - **状态**: 已合并/关闭
    - **描述**: 修复了OpenClaw Cron任务运行时，会话键名不规范导致的会话重复创建问题。
    - **链接**: [PR #2190](https://github.com/netease-youdao/LobsterAI/pull/2190)

4.  **存在安全风险: 请求ID可预测** (PR #1401)
    - **状态**: 开放，已标记 `stale`（陈旧）
    - **描述**: 报告了 `Math.random()` 生成的请求ID可能被预测，存在SSE数据流被劫持的安全风险。
    - **链接**: [PR #1401](https://github.com/netease-youdao/LobsterAI/pull/1401)
    - **备注**: 该PR已存在近3个月，尽管重要，但被标记为陈旧，需项目维护者关注。

## 6. 功能请求与路线图信号

- **LiteLLM AI网关集成 (PR #2193)**
  - **链接**: [PR #2193](https://github.com/netease-youdao/LobsterAI/pull/2193)
  - **路线图信号**: 这是一个**强力信号**。LiteLLM作为流行的AI代理网关，能无缝对接上百种大语言模型API。此PR的提出意味着项目有意向将自身打造成更通用的AI应用平台，摆脱对单一或有限模型提供商的依赖。如果被合并，将是项目重要里程碑，很可能被纳入下一个主要版本。

- **长期未处理的积压特性请求**
  - **PR #1404**: 优化定时任务创建界面的时间控件和下拉选择器，以提升UI/UX一致性和操作便利性。（已存在近3个月）
  - **PR #1402 & #1406**: 修复多选附件和IM通知渠道列表的Bug，属于体验修复，并非全新功能，但长时间未被合并。（已存在近3个月）

## 7. 用户反馈摘要

- **核心痛点 - 升级灾难**：从Issue #1400可以清晰看到，用户 `danielmonlite` 从3.30版本升级至4.1版本后遭遇了**完全不可用**的状态。其语气（“彻底瘫痪”、“严重bug”、“反复启动失败”）反映了极度的挫败感和对项目质量的失望。
- **对比落差**：另外几个标记为 `stale` 的PR（#1401, #1402, #1403, #1404, #1406）在3个多月前提出的改进（如UI优化、安全风险修复）至今未被处理。这与近日高频率合并的PR形成了鲜明对比，**社区贡献者的等待时间过长**，可能影响其后续贡献热情。

## 8. 待处理积压

以下为长期未响应或响应不足的Issue和PR，可能影响项目健康度和社区声誉，建议维护团队优先关注：

1.  **紧急-未解决用户故障**:
    - **Issue #1400**: 严重Bug，用户项目瘫痪，已存在近3个月，无任何官方回复或进展。
    - **链接**: [Issue #1400](https://github.com/netease-youdao/LobsterAI/issue/1400)

2.  **重要-安全风险**:
    - **PR #1401**: 修复SSE请求ID可预测的安全问题。已存在近3个月，被标记为`stale`，需尽快评估和合并。
    - **链接**: [PR #1401](https://github.com/netease-youdao/LobsterAI/pull/1401)

3.  **体验改进-社区贡献积压**:
    - **PR #1404, #1402, #1406, #1403**: 这些PR都是明确的Bug修复或UI优化，提交已有近3个月。如果功能有效，建议尽快合并或给予明确反馈（如需要修改的地方），避免挫伤社区贡献者的积极性。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis 项目动态日报 — 2026-06-24

## 1. 今日速览
- **活跃度评估**：低。过去24小时内没有新 Issue 提交或关闭，仅有一项 PR 从合并状态转为关闭，表明社区讨论和问题报告处于冰点。
- **功能整合**：PR #215（`send_image` 工具）已被关闭，意味着图像发送能力已正式合并入主分支，这是项目在**多模态交互**与**渠道扩展**方向上的关键一步。
- **版本冻结**：无新版本发布，项目处于功能合并后的稳定期。
- **健康度小结**：虽然近期活跃度低，但核心基础设施（截图管道复用、Telegram 渠道支持）已完成建设，项目处于“积累交付”阶段，社区响应可能存在等待新版本发布的观望情绪。

## 2. 版本发布
无新版本发布。

## 3. 项目进展
- **PR #215** [CLOSED] `feat(tools): add send_image tool for channel image delivery`  
  **摘要**：新增 `send_image` 工具，允许 skill 向 Telegram 等渠道发送本地图片文件（PNG、JPEG、GIF、WebP）。该工具复用现有的截图管道，通过 `data:` URI 在 `screenshot` key 中返回图像数据，聊天运行器会自动拾取并推送。支持 `caption` 参数为图片添加文本说明。  
  **影响**：  
  - 强化了 Moltis skill 的**多模态输出能力**，从只能生成截图扩展到可主动发送任意图像。  
  - 降低与 Telegram 等渠道的集成复杂度，开发者无需自行处理图像编码或上传逻辑。  
  - 该 PR 从合并到关闭，标志功能已完全入库，后续开发者可直接在 skill 中调用 `send_image`。  
  **链接**：https://github.com/moltis-org/moltis/pull/215

## 4. 社区热点
今日无活跃讨论或高关注度 Issue/PR。PR #215 虽产生1条未显示的评论（数据标注 `undefined`），但无实质讨论。整体社区沉寂，可能是由于：
- 项目现阶段功能稳定，用户无紧迫问题。
- 缺少版本发布，社区焦点转向其他计划（如下一阶段路线图讨论）。

## 5. Bug 与稳定性
**无 Bug 报告**。过去24小时内无新 Issue 提及崩溃、异常或回归问题，代码库状态稳定。

## 6. 功能请求与路线图信号
**无新功能请求**。但结合今日关闭的 PR #215，可提出以下前瞻判断：
- **趋势**：图像发送工具完成后，下一阶段可能聚焦于**接收图像**（如用户通过 Telegram 发图给 skill 分析）或**其他渠道适配**（如 Discord、Slack 的图片推送）。
- **潜在需求**：用户可能期望 `send_image` 支持 URL 输入（不仅限于本地文件），或加入对动态生成图表（如 Matplotlib 输出）的直接封装。

## 7. 用户反馈摘要
由于今日无 Issue 更新和无评论数据（`undefined`），无法提炼用户反馈。项目公共交流渠道暂缺活跃信号，建议维护者通过以下方式触达社区：
- 在 README 或新版本公告中引导用户试用 `send_image` 并提交反馈。
- 开放一个“使用体验” Issue 模板，鼓励用户分享集成案例。

## 8. 待处理积压
**无待处理积压**。当前 Issue 和 PR 列表均为空（0条开放 Issue，0条待合并 PR），维护者负担轻，适合：
- 启动下一版本功能规划（如“技能市场”或“渠道模板库”）。
- 清理历史遗留标签或过时的讨论（如有）。

## 总结
Moltis 项目今日处于**稳定低活跃**状态，**核心进展**是图像发送能力并入主分支，为 skill 的多模态交互奠定基础。无 Bug、无积压、无新需求，适合维护者推进文档更新或内部测试。建议下一次版本发布时，结合 `send_image` 写一个案例教程，以激发社区二次开发热情。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，我已根据您提供的 CoPaw 项目 GitHub 数据，生成 2026-06-24 的项目动态日报。

---

# CoPaw 项目动态日报 | 2026-06-24

**项目名称**：CoPaw (QwenPaw)
**数据统计时段**：2026-06-23 至 2026-06-24
**分析师**：AI 开源项目分析师

### 1. 今日速览

CoPaw 项目今日保持**高活跃度**。社区提交数量（35个Issues，50个PR）处于高位，但合并/关闭率（23/50）略低，表明维护者审核工作繁忙。核心亮点是**v1.1.12.post2 补丁发布**，主要修复了会话删除后的导航问题。社区焦点集中在 **Cron 定时任务故障、自定义 API 兼容性**以及**移动端适配**两大方向。多个关于**内存占用和启动性能**的反馈值得关注，预示着用户对资源管理优化的强烈需求。

### 2. 版本发布
-   **发布版本**：[v1.1.12.post2](https://github.com/agentscope-ai/QwenPaw/releases/tag/v1.1.12.post2)
-   **更新内容**：
    -   **修复**：修复了删除当前会话后导航到新聊天的问题（PR [#5376]）。
    -   **功能**：增强了控制台和聊天的文件预览功能，支持相对路径（PR [#5377]）。
-   **破坏性变更**：无。
-   **迁移注意事项**：这是一个小版本补丁，主要修复 Bug，可平滑升级。

### 3. 项目进展

今日合并/关闭了多个重要 PR，项目在以下方面取得进展：

-   **性能优化**：`#5469 [CLOSED]` **并行化关闭流程**。通过`asyncio.gather`并行停止多个管理器（Workspace、Browser等），显著缩短了应用关闭时间。这是一个社区呼声较高的底层优化。
-   **内存管理重构**：`#5450 [CLOSED]` **重构记忆生命周期**。对`/compact`命令和`/system_prompt`指令进行了大幅重构，优化了记忆管理子系统的职责划分和健壮性，有望缓解部分记忆相关的性能问题。
-   **移动端适配**：`#5452 [CLOSED]` **Skill Pool 页面**、`#5473 [CLOSED]` **Coding 聊天面板** 完成移动端适配。`#5444 [OPEN]` **侧边栏与页眉**的移动端适配也在进行中，表明团队正系统性地推进移动体验。
-   **功能改进**：`#5436 [OPEN]` **拖拽文件上传**功能已提交PR，将增强聊天区的易用性。

### 4. 社区热点

今日讨论最热烈的话题集中在**定时任务可靠性**和**自定义模型兼容性**：

1.  **Cron 定时任务故障**：
    -   [Issue #5235](https://github.com/agentscope-ai/QwenPaw/issues/5235)：Cron 任务到了预定时间不执行，任务状态卡在 `pending`。
    -   [Issue #5398](https://github.com/agentscope-ai/QwenPaw/issues/5398)：Cron 调度器在应用存活状态下停止分发已启用的任务。
    -   **分析**：这两个问题（共17条评论）揭示了定时任务模块存在严重的调度逻辑缺陷，可能影响依赖定时任务（如每日总结、记忆更新）的用户体验。这是当前最紧急的**关键缺陷**之一。

2.  **自定义 OpenAI 兼容 API 的 Function Calling 支持**：
    -   [Issue #5345](https://github.com/agentscope-ai/QwenPaw/issues/5345)（6条评论）：用户 `@qiyuanlicn` 报告称，在通过自定义提供商添加 OMLX 等 API 后，模型无法使用工具（function calling），仅返回文本。
    -   **分析**：这表明当前的 OpenAI 兼容适配不够完善，无法适配所有实现细节略有差异的第三方API。这限制了 CoPaw 的模型扩展性。

3.  **高内存占用**：
    -   [Issue #5441](https://github.com/agentscope-ai/QwenPaw/issues/5441)（3条评论）：用户反映应用刚启动，还未做任何操作，内存占用已达1.4GB。
    -   **分析**：内存占用是今天多个报告（#5441, #5439, #5421）的共性痛点，直接影响了用户在低配设备上的使用体验。

### 5. Bug 与稳定性

今日报告的 Bug 按严重程度排列如下：

| 严重程度 | Bug 描述 | Issue 链接 | Fix PR 状态 |
| :--- | :--- | :--- | :--- |
| **严重** | Cron 定时任务无法正常触发或停止调度 | [#5064](https://github.com/agentscope-ai/QwenPaw/issues/5064), [#5235](https://github.com/agentscope-ai/QwenPaw/issues/5235), [#5398](https://github.com/agentscope-ai/QwenPaw/issues/5398) | 无 |
| **高** | 升级后禁用的内置技能会重新启用 | [#5262](https://github.com/agentscope-ai/QwenPaw/issues/5262)（12条评论） | 无 |
| **高** | DeepSeek 等模型在 `thinking` 过程中卡死 | [#5328](https://github.com/agentscope-ai/QwenPaw/issues/5328) | 无 |
| **高** | 自定义 OpenAI 兼容提供商不支持 `function calling` | [#5345](https://github.com/agentscope-ai/QwenPaw/issues/5345) | 无 |
| **中** | 包含大量工具调用的会话导致前端崩溃/白屏 | [#5401](https://github.com/agentscope-ai/QwenPaw/issues/5401) | 无 |
| **中** | Tauri 环境下找不到 Python，无法运行自定义脚本 | [#5317](https://github.com/agentscope-ai/QwenPaw/issues/5317) | 无 |
| **中** | 安装后启动报错 `Internal Server Error` | [#5379](https://github.com/agentscope-ai/QwenPaw/issues/5379) | 无 |

### 6. 功能请求与路线图信号

-   **高优先级信号：移动端适配**：由 `#4635` 触发，今日一系列以 `mobile adaptation` 为主题的 PR 被提出（#5470, #5452, #5458, #5459, #5444），这些 PR 已进入审核或待合并状态，大概率会随下一版本发布。
-   **中等优先级信号：记忆系统增强**：`#5316` 提出的为 `memory_search` 添加“时效性”排名算法，与今日已合并的 `#5450` (记忆生命周期重构) 相辅相成，方向一致，很可能被纳入路线图。
-   **低优先级/新功能请求**：`#5427` 提出支持 Kimi 的 Anthropic 兼容端点，`#5453` 请求支持 KaTeX 数学公式渲染。这些代表了特定用户群体的需求，反馈人数尚少，短期内可能不会成为开发重点。

### 7. 用户反馈摘要

-   **负面/痛点**：
    -   **升级体验差**：用户 @daigoopautoy 对“每次升级都要重新禁用内置技能”感到困扰（#5262）。
    -   **定时任务不可靠**：用户 `@tina0501853` 和 `@howyoungchen` 报告了 Cron 任务无法触发的问题，这削弱了 Agent 自动化的可靠性（#5064, #5398）。
    -   **资源占用过高**：用户 `@w409401768` 对1.4GB的启动内存占用表示不满（#5441）。
    -   **`thinking` 过程卡死**：用户 `@bob-geek11` 反馈在使用 DeepSeek 时，Agent 常在思考过程中卡死，需要手动干预（#5328），交互体验不佳。

-   **正面/期望**：
    -   多个移动端适配 PR 的提出，反映了社区对跨设备访问 CoPaw 的强烈需求。
    -   LaTex支持请求（#5453）表明，CoPaw 正在被用于更多需要处理数学/科学内容的场景。

### 8. 待处理积压

以下为长期未响应或悬而未决的重要 Issue/PR，需要维护者关注：

1.  **[Feature #3995](https://github.com/agentscope-ai/QwenPaw/issues/3995) | 增强记忆管理与召回机制**：创建于5月1日，已有3条评论，是社区长期呼声极高的功能改进。虽然今日有相关重构 PR 合并，但 Issue 讨论的自动归档、冲突检测等细节尚未完全落地。
2.  **[Bug #1296](https://github.com/agentscope-ai/QwenPaw/issues/1296) | Discord Channel 流式响应支持**：创建于3月11日，近期仍有讨论。作为核心聊天渠道之一，流式传输的缺失影响了 Discord 用户的体验。
3.  **[PR #5059](https://github.com/agentscope-ai/QwenPaw/pull/5059) | Matrix 加密媒体修复**：已创建超过两周，仍为 Open 状态。该修复对使用 Matrix 端到端加密的用户至关重要。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，根据您提供的 ZeroClaw 项目数据，我为您生成了 2026-06-24 的项目动态日报。

---

## ZeroClaw 项目动态日报 | 2026-06-24

### 1. 今日速览

ZeroClaw 项目今日呈现出高强度的**安全与架构加固**态势。社区围绕供应链安全、插件权限模型和网关可升级性展开了深度（RFC）讨论，并提交了多项关键增强PR。同时，项目正系统性地补齐测试覆盖率，今日有大量来自新贡献者的单元测试PR涌入，涉及运行时、工具、API认证等多个核心模块，显示出项目健康度良好，社区贡献活跃。然而，50个待合并PR积压，且无版本发布，表明维护团队正集中精力进行内部质量提升，而非外发新版本。

### 3. 项目进展

今日项目无新版本发布，工作重点在于**内部质量提升**和**架构讨论**。虽然没有 PR 被合并，但社区提交了大量高质量的 PR，预示着未来几天的重大进展。

- **安全与架构演进 (PR #8173)**: `NiuBlibing` 提交了大型PR `feat(gateway): in-app upgrade with auto-restart from the web dashboard`。该PR实现了RFC #8170，将网页仪表盘中的版本标签转变为完整的升级交互入口，支持检测、展示发布日志、应用更新并自动重启，是通往0.9.0版本的重要一步。
- **测试覆盖率显著提升 (PR #8273, #8272, #8271, #8270 等)**: 大量新贡献者（`Alix-007`, `yuxuan-7814`）提交了针对特定模块的单元测试PR。这些PR覆盖了插件访问器、API认证、认证速率限制、报告模板安全、内存去重冲突处理等关键路径。这表明项目正在系统性地清理技术债务并巩固现有功能的稳定性。
- **OpenRouter 集成增强 (PR #8207, #8141)**: `yuxuan-7814` 和 `vinitasher` 分别独立提交了PR，旨在将 `fallback_models` 配置项真正传递给 OpenRouter 的原生 API，以启用自动模型故障转移。这两个PR都处于待审核状态，预计合并后将显著提升ZeroClaw使用OpenRouter时的可靠性。
- **技能与动态更新 (PR #8261)**: `IftekharUddin` 提交了一个L级增强PR，为自主技能创建增加了可选的 `SKILL.md` 反思路径，使得代理可以在执行过程中自动生成技能规范文档，这有助于推动ZeroClaw的自主性和技能生态发展。

### 4. 社区热点

今日社区讨论的核心在于**“防御性加固”**，最活跃的议题均围绕安全和架构可靠性展开。

- **RFC: 供应链签名 (Issue #8177 - 4条评论)**: `ConYel` 提出的RFC是今日讨论的焦点。社区正在深入探讨如何通过硬件PGP、封闭构建和SLSA溯源来保护ZeroClaw的供应链。这直接回应了此前对CI管道（#7675）进行硬化的需求，显示出社区对项目长期安全性的高度关注。
    - [Issue #8177](https://github.com/zeroclaw-labs/zeroclaw/issues/8177)
- **MCP工具在TUI中缺失 (Issue #8193)**: `Audacity88` 报告了一个严重的稳定性问题 (S1 - 工作流受阻)，即MCP服务器暴露的工具在ZeroCode TUI会话中不可见，即使网关侧能看到它们。该Issue在24小时内被关闭，表明修复速度极快。
    - [Issue #8193](https://github.com/zeroclaw-labs/zeroclaw/issues/8193)
- **内应用升级 (Issue #8170 & PR #8173 - 3条评论)**: `NiuBlibing` 的RFC和对应的PR形成联动，引起了社区对用户体验提升的讨论。在Web仪表盘中一键升级并重启，被看作是改善运维体验的关键功能，解决了用户必须离开控制台手动操作的问题。
    - [Issue #8170](https://github.com/zeroclaw-labs/zeroclaw/issues/8170)
    - [PR #8173](https://github.com/zeroclaw-labs/zeroclaw/pull/8173)

### 5. Bug 与稳定性

今日报告的Bug集中在系统提示词不一致和特定通道（Matrix）的媒体处理问题上，严重性均为S1。

- **S1 - 工作流受阻: 系统提示词工具可用性不一致 (Issue #8054)**: `perlowja` 报告了一个跨多个入口点的系统提示词Bug：系统提示告知推理模型“没有可用工具”，而实际上原生/MCP工具已在请求中。这是个架构级问题，虽然 `#8053` 修复了运行时代理路径，但其他入口点（通道、WebSocket等）仍存在同样的问题，`status:blocked` 表明解决起来有挑战。
    - [Issue #8054](https://github.com/zeroclaw-labs/zeroclaw/issues/8054)
- **S1 - 工作流受阻: Matrix通道图片参考丢失 (Issue #8151)**: `singlerider` 报告了一个与通道历史缓存相关的问题。当用户发送图片并要求机器人“稍后处理”时，机器人在后续轮次中会声称看不到该图片，因为图片的缓存引用丢失了。这是一个影响体验的数据一致性问题，目前尚无修复PR关联。
    - [Issue #8151](https://github.com/zeroclaw-labs/zeroclaw/issues/8151)

### 6. 功能请求与路线图信号

综合近期Issues和已有PR，可以勾勒出下一版本的轮廓：

- **供应商兼容性增强 (Issue #8138, PR #8207, #8141)**: 社区对OpenRouter的自动故障转移功能呼声很高，已有两个PR实现该功能，预计将很快被纳入`v0.8.3`或`v0.9.0`版本。
- **安全性、合规性与用户体验 (PR #8171, #8136)**: 旨在为浏览器工具增加`allowed_private_hosts`白名单，允许用户在明确授权下访问内网资源。这平衡了SSRF防护（#5918）与用户的实际内网访问需求。
- **自动化与零配置 (PR #8033)**: 一个大型PR `feat(onboard)` 旨在将`zeroclaw onboard`命令重做为基于聊天的对话式设置助手，显著降低新用户的入门门槛。这将是路线图上重要的用户体验改进。
- **平台特性支持 (Issue #8046)**: 为Telegram通道增加webhook模式，以支持无公网IP环境的快速响应，这是来自社区的实际运维需求。

### 7. 用户反馈摘要

- **痛点: 安全配置门槛高**: 多个Issue（#5919, #8125, #8134）反映了用户对安全与易用性之间平衡的困惑。例如，插件权限模型过于严格导致意外受限（用户希望YOLO模式），而通道会话过期策略缺失导致Token消耗过高。用户期望ZeroClaw提供更智能、更自动化的默认配置，同时保留手动微调的入口。
- **场景: 多云供应商与可靠性**: 用户在讨论中（#8138）明确提出了对OpenRouter多模型故障转移的需求，表明有大量用户在使用ZeroClaw作为代理访问多个第三方LLM供应商，他们非常关注服务的高可用性和可靠性。
- **满意点: 积极修复问题**: #8193（MCP工具缺失）Isssue从报告到关闭仅用了不到24小时，这种快速的Bug修复获得了社区的正面评价，用户普遍对ZeroClaw维护团队的响应速度表示满意。

### 8. 待处理积压

- **安全积压: `zc_env_read` 插件权限白名单 (Issue #5919)**: 这个已关闭的Issue指向了插件系统的一个根本性安全设计：一个拥有`env_read`权限的插件可以读取任何环境变量。虽然Issue已关闭，但并未看到对`fc_env_read`实现白名单机制的PR，这可能是未来一个需要引入的安全加固点。
    - [Issue #5919](https://github.com/zeroclaw-labs/zeroclaw/issues/5919)
- **测试基础设施: 追踪153个丢失提交 (Issue #6074)**: 该Issue追踪3月28日一次批量回滚中丢失的153个提交。这个审计工作长期处于 `in-progress` 状态，尽管近期没有新评论，但它依然是社区和核心维护者的一块“心病”，预计需要在未来某个版本（如v0.9.0）中进行系统性恢复或重写。
    - [Issue #6074](https://github.com/zeroclaw-labs/zeroclaw/issues/6074)
- **架构统一: 斜杠命令注册表合并 (RFC #7929)**: 该RFC提出将Web UI、TUI和通道运行时中三个独立的、硬编码的斜杠命令注册表统一为一个由网关提供的数据源。这个提案能够解决功能碎片化和维护成本问题，但尚未进入实施阶段，需要维护者推动。
    - [Issue #7929](https://github.com/zeroclaw-labs/zeroclaw/issues/7929)

</details>

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*