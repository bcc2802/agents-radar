# OpenClaw 生态日报 2026-06-25

> Issues: 448 | PRs: 500 | 覆盖项目: 13 个 | 生成时间: 2026-06-25 03:30 UTC

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

好的，作为 AI 智能体与个人 AI 助手领域的开源项目分析师，根据您提供的 OpenClaw 项目 GitHub 数据，我将为您生成 2026 年 6 月 25 日的项目动态日报。

---

# OpenClaw 项目动态日报 | 2026-06-25

## 📊 今日速览

今日 OpenClaw 项目社区活跃度极高。过去 24 小时内，共有 **448 条 Issue 更新** 和 **500 条 PR 更新**，显示出强大的社区贡献力与维护团队的响应速度。虽然大部分 PR (87%) 仍处于待合并状态，但 Issue 解决率 (13.7%) 保持健康。新的 **v2026.6.11-beta.1** 版本发布，主要集中在频道控制能力升级。然而，项目也面临着大量关于会话状态、数据安全与消息丢失的 P1 级 Bug 挑战，稳定性是需要持续关注的核心议题。

## 🚀 版本发布

### v2026.6.11-beta.1 发布
- **核心亮点：** 本期更新显著增强了频道控制能力。
    - **Slack:** 新增 `relay mode`，优化消息路由。
    - **Mattermost:** 支持原生 `/oc_queue` 命令。
    - **DM 模型覆盖:** 实现了**每个 DM 会话的独立模型覆盖**，允许对不同频道或私聊进行精细化模型配置，提升自动化灵活性。
- **致谢:** 感谢 @sjf-oa, @amknight, @xydigit-zt, @thomaszta, @gandalf-at-lerian 的贡献。

*(本次发布摘要未提及破坏性变更或迁移注意事项。若有，建议维护者在发布说明中明确标注。)*

## 🛠️ 项目进展 (今日合并/关闭的重要 PR)

今日共有 **66 个 PR 被合并或关闭**，推动了项目在多方面的进步：

- **核心稳定性与恢复：** 针对会话恢复的难题，`#95899` 通过在被中断的助手回复后重新呈现最后一条用户消息，实现了**网关重启后的自动恢复**，避免了用户重新输入。
- **文件操作安全：** `#96636` 修复了 `edit` 工具在进行模糊文本匹配时可能**重写无关行**的 Bug，提升了编辑准确性。
- **安全加固：** 多个 PR（如 `#96571`、`#96580`、`#96581`、`#96572`、`#96573`、`#96574`、`#96575`）针对不同频道（Teams、WhatsApp、Telegram、IRC、Google Chat、Synology Chat、QQBot）进行了**UTF-16 边界截断**修复，防止因表情符号等字符导致的乱码或 API 错误。`#96336` 则将托管状态目录权限强制设为 `0o700`，防护多用户环境下的数据泄露。
- **媒体与视觉：** `#93848` 修复了 Telegram 中**图片无法作为原生视觉块**传入给模型的问题，之前模型只能收到 `<media:image>` 占位符。

## 🔥 社区热点 (今日讨论焦点)

今日社区讨论的热点集中在以下几方面：

1.  **跨平台应用需求呼声持续高涨：**
    - **[Issue #75]** Linux/Windows 版 Clawdbot 应用需求：尽管发布于今年 1 月，但以 **109 条评论**和 **80 个 👍** 高居榜首。社区对覆盖桌面主流操作系统有强烈且持续的诉求，这已成为项目的顶级功能需求。
    - **链接:** [openclaw/openclaw Issue #75](https://github.com/openclaw/openclaw/issues/75)

2.  **会话状态与消息丢失问题引发广泛讨论：**
    - **[Issue #88838]** 核心会话/转录 SQLite 迁移问题：作为一个近期创建的 P1 级 Issue，获得了 **36 条评论**，表明社区对核心数据层的稳定性高度关注。该 Issue 跟踪通过访问器模式迁移直接会话存储调用，是重构关键路径，但对用户可见影响较小。
    - **链接:** [openclaw/openclaw Issue #88838](https://github.com/openclaw/openclaw/issues/88838)
    - **[Issue #22676]** Signal 守护进程重启竞争条件：该问题涉及进程管理和消息发送失败，评论数达到了 17 条，反映出部分用户在特定消息通道（Signal）上遇到了较为严重的稳定性问题。
    - **链接:** [openclaw/openclaw Issue #22676](https://github.com/openclaw/openclaw/issues/22676)

## 🐛 Bug 与稳定性

今日报告的 Bug 数量大且严重，多为 P1 级别，影响面广。

| 严重程度 | 问题摘要 | 关联 Issue | 是否有 Fix PR? |
| :--- | :--- | :--- | :--- |
| **P0** | **网关内存泄漏至 1073MB+**，导致 cron 任务静默失败、所有网络请求超时。这是一个严重的性能退化问题。 | [#87109](https://github.com/openclaw/openclaw/issues/87109) | 无 |
| **P1** | **会话状态/消息丢失类** - 包括 group chat 陷入 `failed` 状态后静默丢弃消息 ([#86827](https://github.com/openclaw/openclaw/issues/86827))、子代理 `jsonl.lock` 文件无法释放导致会话永久损坏 ([#95833](https://github.com/openclaw/openclaw/issues/95833))、`steer` 模式未正确注入消息 ([#48003](https://github.com/openclaw/openclaw/issues/48003)) 等。 | 多个 | 部分有 |
| **P1** | **安全与权限** - `exec` 工具不继承技能环境变量 ([#31583](https://github.com/openclaw/openclaw/issues/31583))、MCP 工具无法注入子代理 ([#85030](https://github.com/openclaw/openclaw/issues/85030))、`workspaceAccess: none` 沙箱为只读 ([#37634](https://github.com/openclaw/openclaw/issues/37634))。 | 多个 | 部分有 |
| **P1** | **回归与崩溃** - `2026.6.9` 版本静默迁移 Memory 存储导致全量重嵌入 ([#95495](https://github.com/openclaw/openclaw/issues/95495))、`Cannot convert undefined or null to object` 错误 ([#38327](https://github.com/openclaw/openclaw/issues/38327))。 | [#95495](https://github.com/openclaw/openclaw/issues/95495), [#38327](https://github.com/openclaw/openclaw/issues/38327) | [#95495 已关闭](https://github.com/openclaw/openclaw/issues/95495) `[CLOSED]` |
| **P2** | **行为异常** - `write` 工具无追加模式导致数据丢失 ([#40001](https://github.com/openclaw/openclaw/issues/40001))、Safeguard 模式忽略自定义 compaction 模型 ([#57901](https://github.com/openclaw/openclaw/issues/57901))。 | 多个 | 部分有 |

**分析:** 大量 **P1 级 Bug** 集中在 `session-state` 和 `message-loss` 上，这是 AI 助手的核心可靠性问题。内存泄漏问题更是直接威胁到服务的长期稳定运行。项目需要优先解决这些稳定性与数据一致性问题。

## 💡 功能请求与路线图信号

社区功能请求体现了对**控制能力、安全性和可观测性**的深度需求：

- **热门趋势：** **精细化权限控制**成为最强烈的信号。`[Feature]: Path-scoped RWX permissions` (##39979)、`[Feature]: Capability-based permissions` (#12678) 和 `Feature: Add denylist support` (#6615) 三个提案同时高亮，表明社区对超越简单黑白名单的、类似 Unix DAC 的细粒度权限模型有共识。
- **平台拓展：** **Telegram Business Bot** 支持 (#20786) 和 **Slack Block Kit** (#12602) 的支持需求强烈，显示用户希望在特定商业沟通平台上获得更深入的集成体验。
- **运维与可观测性：** **`Subagent lifecycle observability`** (#38626) 和 **`Gateway-lite mode`** (#86881) 等提案，反映了从个人使用向团队和企业级部署场景演进的信号，对运维管理和资源效率提出了更高要求。
- **下版本可能纳入的功能：** 结合已有的 PR，`feat(sessions): add local timezone prefix to archive filenames` (#96652) 和 `feat(embedded-runner): expose prep stage timings` (#78381) 等 PR 正在推进，表明会话归档的可读性优化和嵌入式运行时的性能观测功能可能率先落地。

## 🗣️ 用户反馈摘要

从今日的 Issues 中，我们可以提炼出以下几类用户反馈：

- **痛点 - 升级之痛：** 用户 `@fenglanhua` 在 #95495 中抱怨从 `2026.6.8` 升级到 `2026.6.9` 时，Memory 存储被静默迁移，导致 1499 个文件需要重新嵌入，缺乏事先警告。这暴露了版本升级中数据迁移策略的不足。
- **痛点 - 配置生效困惑：** 用户反映 `OPENCLAW_HOME` 设置为 `~/.openclaw` 时产生嵌套目录 `~/.openclaw/.openclaw` (#45765)，`compaction.model` 配置被忽略 (#57901)。这些反馈表明配置层的逻辑**应该更加直观和一致**。
- **使用场景 - 追求精细化控制：** 用户 `@good-warning` 提出的 `announceTarget` 选项 (#27445) 和 `@882soft` 提出的分层引导文件加载 (#22438) 代表了高级用户在利用 OpenClaw 编排复杂工作流时，对消息路由和 Token 消耗控制的极致追求。
- **满意之处：** 虽然今日反馈以问题为主，但 `v2026.6.11-beta.1` 中对 Slack Relay Mode 等频道控制能力的增强，收到了来自多位贡献者的致谢，表明社区对这些针对性的改进是认可的。

## 📋 待处理积压

以下 Issue/PR 长期未得到维护者回应或推进，需要重点关注：

- **高优先级 Bug:** **`Signal daemon stop() race condition`** (#22676) 创建于 2 月，是 P1 级 Bug，影响特定通道的稳定性，至今没有明确的解决方案。
- **高热度功能需求:** **`Linux/Windows Clawdbot Apps`** (#75) 作为评论最多、赞数最高的话题，社区期盼已久，但进展不明，需要维护者给出路线图或回应。
- **长期未合并的 PR:** **`feat(embedded-runner): expose prep stage timings`** (#78381) 和 **`fix(auth): cooldown inline api key billing failures`** (#88709) 均为 P2 级别，但已经准备好等待维护者审查数周甚至更长。长时间搁置可能会打击贡献者的积极性。

---

## 横向生态对比

好的，作为您的资深技术分析师，现根据2026年6月25日的各项目动态日报，为您呈现一份关于AI智能体与个人AI助手开源生态的横向对比分析报告。

---

### **个人AI助手开源生态横向对比分析报告 (2026-06-25)**

#### **1. 生态全景**

今日，AI智能体与个人AI助手开源生态呈现 **“整体繁荣、局部攻坚、安全与平台化成为主旋律”** 的态势。所有活跃项目均处于高强度迭代期，社区贡献活跃度极高（多个项目日PR数超50）。生态核心焦点正从单一功能创新转向 **系统级的稳定性、安全加固和平台化能力建设**，如跨平台兼容、多租户权限隔离、供应链安全等。与此同时，Token成本和用户体验优化的呼声日益高涨，标志着生态正从“能用”向“好用、省用”的成熟阶段过渡。

#### **2. 各项目活跃度对比**

| 项目名称 | 今日Issues数 | 今日PR数 | Release情况 | 健康度评估 | 备注 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 448 | 500 | 发布 v2026.6.11-beta.1 | 🟢 非常活跃 | 社区贡献量巨大，但部分P1级Bug积压，需重点解决稳定性。 |
| **NanoBot** | 4 | 18 | 无 | 🟢 活跃 | 聚焦渠道兼容性修复与WebUI体验优化，社区驱动的快速迭代。 |
| **Hermes Agent** | 50 | 50 | 无 | 🟢 非常活跃 | Token优化、A2A协议、稳定性修复成为三大焦点，核心功能演进中。 |
| **PicoClaw** | 0 | 8 | 无 | 🟡 稳定但沉寂 | 社区讨论热度低，但一次性清理12个安全漏洞，处于内部清理与安全过渡期。 |
| **NanoClaw** | 1 | 18 | 无 | 🟢 活跃 | 多方向功能扩展（多Bot、E2EE、远程MCP），社区贡献者覆盖面广。 |
| **NullClaw** | - | - | - | ⚪ 无活动 | 24小时内无任何动态。 |
| **IronClaw** | 10+ | 44 | 无 | 🟢 非常活跃 | 聚焦运行时稳定性与架构重构（记忆层），社区“狗粮测试”驱动大量修复。 |
| **LobsterAI** | 1 | 42 (合并) | 无 | 🟢 非常活跃 | 核心贡献者清空积压PR，主要修复OpenClaw网关和IM集成稳定性。 |
| **TinyClaw** | 0 | 1 (合并) | 无 | 🟡 稳定 | 平台支持短板修复（Windows CLI），小幅迭代中。 |
| **Moltis** | - | - | - | ⚪ 无活动 | 24小时内无任何动态。 |
| **CoPaw** | 24 | 50 | 无 | 🟢 非常活跃 | 主要精力在修复AgentScope 2.0迁移后的回归Bug，同时社区对自定义模型兼容性呼声高。 |
| **ZeptoClaw** | - | - | - | ⚪ 无活动 | 24小时内无任何动态。 |
| **ZeroClaw** | 43 | 50 | 无 | 🟢 非常活跃 | 聚焦安全与多租户架构，正在进行架构升级的关键讨论，社区驱动力强。 |

#### **3. OpenClaw 在生态中的定位**

*   **优势与社区规模**：OpenClaw 是目前生态中**社区贡献量最大、版本迭代最激进**的项目，其日PR/Issue处理量远超同类。它与 LobsterAI 形成了紧密的上下游关系（LobsterAI 的核心功能高度依赖OpenClaw网关），并成为其他项目（如PicoClaw、NanoClaw）命名的“参照系”，体现了其作为**底层基础设施领域的核心参照项目**地位。

*   **技术路线差异**：OpenClaw 的架构设计强调**高度模块化和插件化**，特别是通过其网关系统与各种即时通讯（IM）平台深度集成。相比之下，其他项目在架构上各有侧重：Hermes Agent 专注于 Agent间通信协议（A2A/ACP）和Token优化；ZeroClaw 则更关注企业级安全与多租户隔离。OpenClaw 的路线更偏向于**通用型、极易扩展的个人AI助手基座**。

#### **4. 共同关注的技术方向**

多个项目不约而同地涌现出以下技术需求，反映了生态的共同演进方向：

1.  **稳定性与数据一致性问题**：
    *   **涉及项目**：**OpenClaw**、**Hermes Agent**、**IronClaw**、**CoPaw**。
    *   **具体诉求**：会话状态丢失/损坏、消息静默丢弃、运行时熔断/冻结、内存泄漏。这表明，随着智能体承担更复杂的任务，**核心数据路径的可靠性**成为所有项目面临的首要挑战。

2.  **安全与权限隔离**：
    *   **涉及项目**：**OpenClaw**、**Hermes Agent**、**PicoClaw**、**NanoClaw**、**ZeroClaw**、**CoPaw**。
    *   **具体诉求**：路径穿越漏洞、认证绕过、工具权限逃逸、MCP工具隔离失效、供应链安全（SLSA）。这表明，AI智能体从玩具走向生产力工具时，**安全模型和权限控制**是必须跨越的门槛。

3.  **跨平台与多平台兼容性**：
    *   **涉及项目**：**OpenClaw**、**NanoBot**、**TinyClaw**、**NanoClaw**。
    *   **具体诉求**：对Linux/Windows桌面原生应用的支持、Windows CLI环境修复、Telegram Web与钉钉等特定IM平台的消息格式兼容。用户期望个人助手能够在所有主流设备上无缝、一致地运行。

4.  **Token与性能优化**：
    *   **涉及项目**：**Hermes Agent**、**OpenClaw**、**CoPaw**。
    *   **具体诉求**：工具Schema懒加载、会话内容压缩、上下文预算管理、前端渲染性能优化。随着模型API成本愈发敏感，**降低Token消耗、提升运行效率**已成为开发者社区的核心焦虑点。

#### **5. 差异化定位分析**

| 项目 | 功能侧重 | 目标用户 | 技术架构差异 |
| :--- | :--- | :--- | :--- |
| **OpenClaw** | 通用型个人助手底座 | 开发者、个人用户 | 强调插件化与IM网关集成，架构最成熟，社区最大。 |
| **NanoBot** | 即时通讯机器人 | 开发者、办公用户 | 专注于Telegram、钉钉等渠道的适配与修复，轻量级。 |
| **Hermes Agent** | 智能体网络与优化 | 高级开发者、企业开发者 | 前瞻性探索A2A/ACP Agent间通信，极致追求Token效率。 |
| **PicoClaw** | 安全与嵌入式系统 | 安全研究员、硬件开发者 | 聚焦安全审计，关注嵌入式设备适配，社区规模较小但专业。 |
| **NanoClaw** | 多协议扩展 | 开发者 | 积极集成新协议（Matrix E2EE、远程MCP），功能扩展能力强。 |
| **IronClaw** | 稳定性与架构演进 | 核心贡献者、测试用户 | 通过“狗粮测试”驱动稳定性修复，注重内部架构重构（记忆层解耦）。 |
| **LobsterAI** | OpenClaw优化与套件 | OpenClaw用户 | 核心贡献者主导，与OpenClaw捆绑，专注于其稳定性和功能收尾。 |
| **TinyClaw** | 轻量级跨平台 | 个人开发者 | 极简功能集，专注于解决“跑起来”的跨平台问题。 |
| **CoPaw** | 综合AI应用平台 | 广大开发者和用户 | 在AgentScope平台之上，强调前端体验、自定义模型集成和插件生态。 |
| **ZeroClaw** | 企业级安全与多租户 | 企业架构师、运维 | 架构创新最前沿，关注身份认证（OIDC）、RBAC、供应链安全和WASM插件系统。 |

#### **6. 社区热度与成熟度**

*   **快速迭代阶段**：**OpenClaw**、**Hermes Agent**、**IronClaw**、**CoPaw**、**ZeroClaw**。这些项目日均PR/Issue量高，社区讨论激烈，正处于功能和架构的快速演进期，但也伴随着较多的Bug和稳定性挑战。
*   **质量巩固阶段**：**LobsterAI**。核心贡献者通过大量合并PR进行Bug修复和代码清理，项目整体处于向稳定版本冲刺的巩固期。
*   **稳定维护阶段**：**TinyClaw**。功能迭代放缓，专注于基础兼容性修复，项目成熟度较高，增长平稳。
*   **沉寂/低活跃阶段**：**PicoClaw**、**NanoBot**。虽有贡献，但社区讨论热度相对较低，可能正处于内部重构或焦点转移期。
*   **无活跃**：**NullClaw**、**Moltis**、**ZeptoClaw**。

#### **7. 值得关注的趋势信号**

1.  **从“功能”到“治理”：企业级安全成为下一波竞争焦点**。ZeroClaw对OIDC、RBAC、供应链安全的深度讨论，与OpenClaw、CoPaw等项目中爆发的权限逃逸、路径穿越等问题，共同指向了一个趋势：**AI智能体的安全治理从加分项变为准入门槛**，尤其是在多租户、企业级部署场景下。对于开发者而言，早期关注并采用安全最佳实践的项目将具备长期优势。

2.  **“省Token”战役全面打响**：Hermes Agent通过数据驱动的“Token开销分析”发起讨论，并带来了“工具Schema懒加载”的热门建议。这不是孤例，OpenClaw的“压缩模型”相关Issue和CoPaw的“时间戳放置”讨论也从侧面印证了这一点。这表明，**随着大模型API成本的压力，优化Token消耗已从开发者锦上添花的技巧，变成了产品竞争的核心指标**。支持懒加载、智能压缩、结构化输出成本控制的项目，将更容易赢得开发者青睐。

3.  **Agent互操作性成为新赛道**：Hermes Agent对A2A/ACP协议的积极探索，以及OpenClaw、NanoClaw对远程MCP服务器支持，表明生态正从构建“单个强大Agent”转向**构建“Agent网络”**。未来的个人AI助手可能不再是孤立的个体，而是能与其他Agent协商、协作的网络节点。这对于想要构建复杂自动化工作流的开发者来说，是一个极具价值的战略方向。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

好的，作为 NanoBot 项目的 AI 智能体与个人 AI 助手领域开源项目分析师，以下是为您生成的 2026 年 6 月 25 日项目动态日报。

---

# NanoBot 项目动态日报 | 2026-06-25

**项目名称:** NanoBot (github.com/HKUDS/nanobot)
**报告日期:** 2026-06-25
**分析师:** AI 分析师

---

### 1. 今日速览

今日项目活跃度极高，社区贡献热情不减。主要动态集中在 Telegram 和钉钉 (DingTalk) 等即时通讯渠道的兼容性修复与功能增强，特别是针对新 API 消息格式（Rich Message）在 Telegram Web 客户端引发的渲染问题，已有多位贡献者提出了解决方案。同时，WebUI 的交互体验和 AI 模型的上下文中继（Thinking Tags）显示问题也得到了快速响应。尽管今日无新版本发布，但大量处于开放状态的 PR 和 Issue 表明项目正处于密集的迭代期，社区贡献的价值链路清晰。

### 2. 版本发布

今日无新版本发布。

### 3. 项目进展

今日合并或关闭了12个PR，标志着项目在多个维度上取得了推进：

- **渠道兼容性修复:** 针对 Telegram Web 的 Rich Message 不兼容问题，PR #4505 (已关闭) 通过 `raw-parse` 模式绕过了高级渲染。针对钉钉渠道，PR #4501 (已合并) 正待处理，旨在解决富文本和超时问题。
- **WebUI 体验优化:** PR #4465 (已关闭) 修复了 `<thinking/>` 标签被明文渲染的问题，提升了模型推理过程的展示体验。
- **安全与配置修正:** 对 OpenAI 兼容 API 鉴权的讨论 (Issue #4490) 和对 WebUI 新首页交互 Bug (Issue #4500) 的识别，为后续的修复 PR 提供了明确目标。
- **项目基础设施建设:** 多项 PR (如 #4416, #4415, #4424) 仍在持续的开放性迭代中，显示出项目在 cron 任务、子智能体调度和记忆管理等核心功能上正进行深度工业化改进。

### 4. 社区热点

今日社区讨论的热点集中于 **Telegram 新 API (Bot API 10.1)** 带来的兼容性问题及其解决方案。

- **[Issue #4488] telegram web: "This message is not supported on the web version of Telegram"**
    - **链接:** [Issue #4488](https://github.com/HKUDS/nanobot/issues/4488)
    - **热度:** 该 Issue 直接触发了一系列修复 PR，是今日社区讨论的始发点。用户 `chengyongru` 报告了在使用新富文本消息功能后，Telegram Web 客户端无法渲染的问题。这直接反映了从新功能上线到用户实际体验之间的差距。

- **[PR #4489] fix: add rich_messages config to disable sendRichMessage for Telegram Web (#4488)**
    - **链接:** [PR #4489](https://github.com/HKUDS/nanobot/pull/4489)
    - **热度:** 该 PR 由 `axelray-dev` 提交，提出通过添加配置项来禁用富文本消息，从而解决兼容性问题。这是社区针对特定 Bug 推动配置灵活性的典型例子，体现了对产品稳定性的考量。

- **[PR #4505] fix(telegram): add raw_message config option for Telegram Web compat (#4488)**
    - **链接:** [PR #4505](https://github.com/HKUDS/nanobot/pull/4505)
    - **热度:** 由 `michaelxer` 提交，提出了另一种解决方案，提供 `raw_message` 配置项。与 PR #4489 思路类似但实现不同，显示出社区对同一个问题有多种解决路径的探讨。

**分析:** 用户对 Telegram Web 的兼容性体验非常敏感。社区对“如何优雅地处理新 API 破坏性变更”的讨论，表明用户不仅希望功能先进，更期望平台稳定。贡献者之间“竞标”式的解决方案提交，体现了该项目的社区治理活力。

### 5. Bug 与稳定性

今日报告的 Bug 主要集中在渠道适配和前端交互两个层面，按严重程度排列如下：

- **严重: Telegram Web 消息渲染失败 (Bug #4488)**
    - **描述:** 使用 Rich Message 格式发送的消息在 Telegram Web 端显示为“不支持的消息”，但在移动端正常。
    - **状态:** 已有两个对应的 fix PR (#4489, #4505)，目前一个已合并。问题正在修复中。
    - **链接:** [Issue #4488](https://github.com/HKUDS/nanobot/issues/4488)

- **中等: 钉钉渠道富文本丢失和超时 (Bug #4497)**
    - **描述:** 钉钉渠道1) 因未正确处理 `richText` 消息类型而导致内容丢失；2) 发送文件或图片时会出现 `httpx.ConnectTimeout`。
    - **状态:** 对应的 fix PR #4501 存在，等待合并。
    - **链接:** [Issue #4497](https://github.com/HKUDS/nanobot/issues/4497)

- **中等: WebUI 首页导航 Bug 及 Stream 停止异常 (Bug #4500)**
    - **描述:** 1) 在 WebUI 欢迎页发送消息后不会自动跳转到对话；2) 自我重启后流式输出可能卡住；3) 点击停止按钮会报“No active task to stop”的错误。
    - **状态:** 待确认和修复。
    - **链接:** [Issue #4500](https://github.com/HKUDS/nanobot/issues/4500)

- **低危: WebUI 中 Thinking 标签明文显示 (Bug #4465)**
    - **描述:** WebUI 将模型的 `<thinking>` 标签当作普通文本显示，泄露了模型的控制模板内容。
    - **状态:** **已关闭**，由 PR #4465 修复。
    - **链接:** [Issue #4465](https://github.com/HKUDS/nanobot/issues/4465)

### 6. 功能请求与路线图信号

- **强信号: 钉钉渠道的富文本支持 (Issue #4497 & PR #4501)**
    - **需求:** 用户希望钉钉能够支持文件、图片及富文本格式的消息。
    - **路线图指示:** 这表明团队正在拓展对国内主流通讯平台的支持，钉钉渠道的功能完备性很可能在下一版本中得到显著提升。

- **强信号: 自定义 Provider 的思考模式支持 (PR #4482)**
    - **需求:** 允许用户在使用自定义大模型提供商（如 VolcEngine/Doubao）时，也能配置并启用模型的“思考/推理”模式。
    - **路线图指示:** 这表明项目在强化其“通用 AI 代理”的定位，对非标准模型的兼容性是保持竞争力的关键。

- **中信号: MCP 服务器空闲自动关闭 (PR #4506)**
    - **需求:** 贡献者 `primit1v0` 引入了 `idle_timeout` 参数，自动杀死空闲的 MCP 服务器进程，以释放资源。
    - **路线图指示:** 这是一个典型的运维友好型功能，说明项目正从“能用”向“好用”和“省资源”演进，对生产环境部署非常重要。

### 7. 用户反馈摘要

- **核心痛点:** 用户对 **“纯客户端”稳定性** 和 **“平台兼容性”** 极为关注。Telegram Web 的兼容性问题 (Issue #4488) 虽然看似简单，但严重影响了特定用户群体的基础体验。用户希望新功能上线前进行更充分的客户端兼容性测试。

- **使用场景:** 从多个 Issue 和 PR 可以看出，用户在不同场景下使用 NanoBot：
    - **个人助手:** 通过 Telegram 和钉钉进行消息收发，获取快速响应。
    - **开发调试:** 深度使用 MCP 协议集成外部工具和知识库 (PR #4436, #4452)。
    - **内容创作:** 使用 WebUI 进行对话和管理，对 PWA 支持 (Issue #4479) 表现出兴趣。

- **满意之处:** 从社区贡献者对《轻量级》(Issue #660) 质疑的讨论来看，用户对项目“全栈”易用性（Python + Node.js）带来的功能完整性有认可，但对“轻量”的定义有不同看法。从 Issue #3437 (Heartbeat) 的长期追踪来看，社区对长期规划的、系统级的功能（如心跳触发）有持续耐心。

### 8. 待处理积压

- **[严重] Issue #660: 轻量级声明与 Node.js 依赖的矛盾**
    - **链接:** [Issue #660](https://github.com/HKUDS/nanobot/issues/660)
    - **积压时间:** 超过 4 个月
    - **摘要:** 用户质疑项目“超轻量级”的自我描述，因为其依赖在 Dockerfile 中包含了 Node.js。该 Issue 获赞 5 个且有 11 条评论，表明这是一项持续引发社区讨论的**核心设计哲学争议**。至今没有官方回应或明确的“去 Node.js”计划，这会持续磨损部分潜在用户的信任。

- **[中等] Issue #3437: Heartbeat Trigger 功能**
    - **链接:** [Issue #3437](https://github.com/HKUDS/nanobot/issues/3437)
    - **积压时间:** 约 2 个月 (从关联 PR #4437 创建时间推断)
    - **摘要:** 该功能请求最终在 PR #4437 中得到实现，目前 PR 仍在开放中。虽然已有进展，但该 Issue 本身在提出后长期处于无响应状态，直到最近才被跟进。类似的长期未响应 Issue 可能需要维护者注意更新状态，给用户一个交代。

**分析师总结:** 项目正处于健康的、由社区驱动的快速迭代期。核心挑战在于如何在快速集成新功能（如 Telegram Bot API 10.1）和维护现有渠道的稳定及兼容性之间取得平衡。对于积压较久的核心架构争议，建议项目维护团队给予明确回应，设定清晰的长期路线图，以维护社区共识。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，这是根据您提供的Hermes Agent GitHub数据生成的2026年6月25日项目动态日报。

---

# Hermes Agent 项目动态日报 | 2026年6月25日

## 1. 今日速览

今日Hermes Agent项目保持**极高活跃度**，过去24小时内迎来了50条Issue更新与50条PR更新，核心议题聚焦于**Token优化**、**Agent间通信协议（A2A/ACP）** 以及**稳定性修复**。社区对降低API调用开销、增强跨Agent协作能力表现出强烈兴趣。在稳定性方面，针对OpenAI-Codex凭证管理、桌面端编码和网关事件循环阻塞等问题的修复持续进行。项目整体处于快速迭代和功能扩张的高压期。

## 2. 版本发布

无新版本发布。

## 3. 项目进展 (重要合并/关闭的 PR)

今日项目在功能扩展和代码清理上均有推进，关键进展如下：

- **Cron任务可延续性**: PR #51077 和 #52250 (由 `victor-kyriazakos` 贡献，`teknium1` 重新基于 `main` 分支提交) 被成功合并。这一特性允许用户对Cron投递的消息进行回复，代理将能识别并延续上下文，而非询问“什么是任务#2？”，**显著提升了定时任务的交互体验**。
- **桌面端性能优化**: PR #52273 (由 `OutThisLife` 提交) 被合并。该PR修复了在大型文件/目录上执行 `/learn` 命令时，桌面应用可能发生的**界面卡死或崩溃**问题，提升了用户体验。
- **QQ机器人Bug修复**: PR #38182 (由 `GangJust` 提交) 被合并。该PR解决了QQ机器人网关中，在“中断模式”下系统注记错误地要求继续任务的问题，并修复了聊天类型识别错误。
- **持续代码清理**: 贡献者 `AlexFucuson9` 提交了多个“移除无用f-string前缀”的PR (批次6,8,9: #52274, #52280, #52281)，涉及 `hermes_state`, `cli`, `tools`, `agent`, `plugins` 等核心模块，**总计清理超过170处静态字符串**，体现了项目对代码质量的持续关注。

## 4. 社区热点

本周社区讨论的热点集中在**降低长期运行成本和提升Agent间互操作性**两大主题上。

- **🥇 Token开销分析与优化 (Issue #4379)**: 获得了16条评论。贡献者 `Bichev` 通过自建的监控仪表盘数据分析得出，73%的API调用是固定开销（约13.9K tokens），其中工具Schema是主要来源。这一发现与排名靠前的 **Feature #6839 (Lazy Tool Schema Loading)** (28条评论, 14👍) 互相呼应，**社区对优化Token消耗、降低运营成本的需求极为迫切**。
- **🥈 Agent间通信协议 (A2A) 与 (ACP) 扩展 (Issue #514, #5257)**: 分别获得22/11条评论，18/16个赞。社区正积极推动Hermes支持 Google 的 A2A 协议（实现“谁可以帮助我？”的发现机制）和通用化 ACP 客户端（实现多Agent编排）。这表明**社区已经不满足于单个Agent的能力，而是希望构建Agent网络和编排能力**。
- **🔥 内存/上下文压缩新思路 (Issue #39691)**: 获得7条评论，10个赞。用户 `Songraf` 提出集成 `headroom-ai` 进行细粒度的工具输出压缩，以取代当前粗粒度的全量会话压缩。这是对 #4379 提出的优化问题的其中一种具体解决方案，引发了积极讨论。

## 5. Bug 与稳定性

项目今日报告的Bug中，以下问题值得高度关注：

| 严重程度 | Issue | 问题描述 | 状态 |
| :--- | :--- | :--- | :--- |
| **P1** | #52197 | Discord网关跨进程缓存失效时，在持有锁的情况下执行清理操作，导致事件循环阻塞，**可能引起心跳超时和连接断开**。 | 新报告，待修复 |
| **P1** | #19566 | OpenAI-Codex凭证池在轮转时，可能丢弃新添加的凭证，**导致认证失败**。 | 待修复 |
| **P2** | #52212 | QQ、微信等不支持 `edit_message` 的平台，**静默丢弃所有工具调用进度消息**，即使用户配置了 `tool_progress_grouping` 也无效。 | 新报告，待修复 |
| **P2** | #52160 | 经过两次上下文压缩后，Anthropic适配器发送的请求中第一条消息角色为 `assistant`，**导致API回400错误**。 | 新报告，待修复 |
| **P2** | #52244 | 升级后的Hermes Desktop (Hermes One) 在 Windows 上**截断并乱码化Agent输出信息**，疑似UTF-8编码问题。 | 新报告，待修复 |
| **P2** | #42627 | 仪表盘在闲置状态下持续占用**20-50% CPU**。 | 待修复 |

**已有修复PR的Bug**: 针对 #41445 (`hermes prompt-size` 工具计数不准确)，PR #52032 已提交，但状态为“已关闭/重复”，可能已被其他方案替代。针对 #51069 (支持项目本地 `.mcp.json` 配置)，该Issue已被关闭为重复。

## 6. 功能请求与路线图信号

除了社区热点中提到的 Token优化、A2A/ACP协议，以下功能请求具有较强的路线图信号：

- **企业及平台集成**: **Rocket.Chat支持 (#3725)** (11条评论, 10👍) 呼声很高，表明社区对更多企业级通信平台的需求。
- **内存系统重构**: **可配置的内存后端 (#47349)** (7条评论) 和 **MCP暴露内存 (#10835)** (已关闭，但有社区成员开发了独立插件 (#42864))，表明用户希望**解耦、灵活管理记忆系统**，并能与其他Agent共享。
- **Google Vertex AI集成**: 来自 PR #8427 的提交，增加了对Google Vertex AI上Gemini模型的支持，并已持续Open状态，这是一个重要的企业级LMM集成。
- **飞书平台功能增强**: PR #47863 (跨平台审批委派) 和 #42038 (机器人间@协作) 的持续活跃，表明飞书平台是企业用户非常关注的阵地，相关功能正在快速完善。

## 7. 用户反馈摘要

- **核心痛点**: **Token消耗过高**是最普遍的痛点。用户 `Bichev` 通过数据揭示了73%开销为固定成本；用户 `jarviszomine` 主张引入懒加载Tool schema。这反映了用户对**控制成本、提高本地模型运行效率**的强烈渴望。
- **使用场景**: 用户 `meron1122` 期望增加Rocket.Chat支持，`easyvibecoding` 提出通过MCP与Claude Code/Cursor共享记忆，表明Hermes正在被尝试用于**企业协作环境和多Agent生态系统**。
- **不满与抱怨**:
    - `dlukt` 报告称z.ai平台在峰值时段对Hermes进行速率限制，而官方工具却无问题，暗示**第三方提供商可能存在不兼容或限制**。
    - `koishi70` 报告称秘密信息（API Key）的脱敏机制会**破坏代码语法**，导致工具调用失败，这是一个影响核心安全与功能完整性的严重设计问题。
    - `FikFikk` 反馈仪表盘空闲时CPU占用过高，`SrDee00` 反馈Windows端输出乱码，表明**桌面客户端的性能和稳定性仍有明显短板**。

## 8. 待处理积压

- **高价值长期议题**:
    - **Issue #514: A2A协议支持** (创建于3月6日，评论:+22, 👍:18) | [链接](NousResearch/hermes-agent Issue #514): 尽管讨论热度极高，但项目尚未正式采纳。如果此功能被纳入路线图，将是项目在Agent网络生态中迈出的重要一步。
    - **Issue #6839: Lazy Tool Schema Loading** (创建于4月9日，评论:+28, 👍:14) | [链接](NousResearch/hermes-agent Issue #6839): 解决核心Token开销问题，是#4379的热门解决方案之一，但状态仍为 `needs-decision`，需要维护者尽快做出决策。
- **高风险Bug (P1)**:
    - **Issue #19566: OpenAI-Codex 凭证池丢失凭证** (创建于5月4日) | [链接](NousResearch/hermes-agent Issue #19566): 此问题阻塞了使用OpenAI-Codex的用户，影响面广且严重，悬而未决时间较长。
    - **Issue #52197: Discord网关心跳阻塞** (创建于6月24日) | [链接](NousResearch/hermes-agent Issue #52197): 新报告的P1级问题，可能造成Discord机器人大面积掉线，需立即排查。
- **长时间未更新的重要PR**:
    - **PR #8427: 添加Vertex AI Provider** (创建于4月12日) | [链接](NousResearch/hermes-agent PR #8427): 该PR实现了企业迫切需要的Gemini模型支持，但已开放超过2个月，可能遇到了合并冲突或设计分歧，建议维护者跟进。
    - **PR #47863: 跨平台审批委派** (创建于6月17日) | [链接](NousResearch/hermes-agent PR #47863): 该PR旨在解决企业环境中的权限控制问题，已开放一周，与现存的安全边界议题相关，值得关注。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，以下是根据 PicoClaw (github.com/sipeed/picoclaw) 的 GitHub 数据生成的 2026-06-25 项目动态日报。

---

# PicoClaw 项目动态日报 | 2026-06-25

## 1. 今日速览

今日项目状态 **活跃**，但核心集中于安全修复与内部清理。过去24小时内，项目**无新Issue开启、无新PR合并、无新版本发布**，表面看似平静。然而，闭源安全研究员集中提交的 **12个安全相关的Issues** 被一次性关闭（标记为`stale`），表明项目团队正在集中处理之前报告的安全漏洞。同时，有 **8个Pull Requests** 处于待合并状态，其中包含一个重要的新DeltaChat网关功能和多个针对OpenAI兼容层的bug修复，显示出项目功能开发和代码质量维护仍在并行推进。总体而言，社区讨论热度较低，但开发活动并未停滞，正处于一个“清理积压、准备合并”的阶段。

## 2. 版本发布

无新版本发布。

## 3. 项目进展

今日无Pull Requests被合并，项目在代码层面未产生新变更。然而，**13个已关闭的Issues** 显示出项目在安全和稳定性方面取得了重要进展。考虑到上周集中报告的多个安全漏洞（如SSRF绕过、命令注入等）今日被关闭，可以推断项目团队已对这些漏洞进行了审查并可能在内部进行了修复。这标志着项目在安全性方面向前迈进了一大步，为正式版本的发布清除了关键障碍。

## 4. 社区热点

今日社区最活跃的议题是此前关于 **PageAgent 对 Vue 等 MVVM 架构适配的咨询（Issue #3167）**。该Issue聚焦于一个具体的、高价值的用户场景：如何在复杂的Vue后台系统中应用PicoClaw的GUI Agent能力。虽然评论不多，但提出的问题（DOM与Virtual DOM的映射、`v-model`状态捕获、动态组件识别）非常专业，代表了企业级用户的核心诉求。这反映出社区用户不再满足于简单的网页操作，而是开始探索在复杂前端框架下的深度集成能力。

*   **[Issue #3167]** 咨询：PageAgent 是否有针对 Vue 等 MVVM 架构的适配方案或规划？ https://github.com/sipeed/picoclaw/issues/3167

## 5. Bug 与稳定性

过去24小时内报告了**1个新Bug**（Issue #3167 实为咨询），但**13个被关闭的Issues**中绝大多数是此前报告的严重安全漏洞。这些漏洞的关闭是今日稳定性的最大亮点，涉及权限绕过、SSRF防护、命令执行等多个维度。

| 严重程度 | 复现 | Issue / PR | 描述 | 状态 |
| :--- | :--- | :--- | :--- | :--- |
| **严重** | 是 | [#3082](https://github.com/sipeed/picoclaw/issues/3082) | 飞书回复上下文扩展绕过 `allow_from` 权限检查 | 已关闭 |
| **严重** | 是 | [#3078](https://github.com/sipeed/picoclaw/issues/3078) | `web_fetch` SSRF保护可被HTTP代理绕过 | 已关闭 |
| **严重** | 是 | [#3074](https://github.com/sipeed/picoclaw/issues/3074) | `web_fetch` SSRF防护可被ISATAP IPv6绕过 | 已关闭 |
| **严重** | 是 | [#3072](https://github.com/sipeed/picoclaw/issues/3072) | Launcher首次密码设置存在CSRF漏洞 | 已关闭 |
| **严重** | 是 | [#3071](https://github.com/sipeed/picoclaw/issues/3071) | 经过认证的WebSocket客户端可触发未授权配置重载 | 已关闭 |
| **中等** | 是 | [#3115](https://github.com/sipeed/picoclaw/pull/3115) | 内联Data URL媒体提取导致会话历史损坏 | **待合并** (PR已提交) |

## 6. 功能请求与路线图信号

今日无新的功能请求开启。信号主要集中在**待合并的PR**中，它们很可能被纳入下一个版本：

*   **信号1: 新网关支持** - **[PR #3063]** 添加了DeltaChat网关的Feature，这表明项目的多平台/去中心化通信能力将得到扩展。这是一个明确的路线图信号。
*   **信号2: 原生流式请求** - 已关闭的 **[Issue #2404]** （请求在配置中添加streaming支持）虽被关闭，但未提及具体实现方式。考虑到AI模型交互普遍需要流式输出，此功能很可能是项目内建的、或通过其他方式（如WebSocket）已经实现，但配置化的需求可能已在内部完成或在未来版本中以更优雅的方式支持。
*   **信号3: 远程Pico模式** - **[PR #3118]** 为`picoclaw agent`命令添加了远程WebSocket模式，这将成为开发者和高级用户连接PicoClaw实例的新途径，增强了其作为远程控制端点的灵活性。

*   **[PR #3063]** feat: add deltachat gateway https://github.com/sipeed/picoclaw/pull/3063
*   **[PR #3118]** Add remote Pico WebSocket mode to picoclaw agent https://github.com/sipeed/picoclaw/pull/3118

## 7. 用户反馈摘要

从今日动态中提炼的用户声音如下：

*   **专业用户痛点（PageAgent与Vue框架）：** 社区用户指出了在Vue/Element UI等MVVM框架下使用PageAgent的挑战。用户的核心痛点是GUI Agent无法有效识别和操作组件内部状态（如`v-model`、`watcher`），导致自动化任务（如填写表单、切换标签页）难以实现。这表明项目若想在复杂业务系统（特别是内部后台）中落地，必须解决与前端框架的兼容性问题。用户的期待是能看到对`data-v-xxx`属性、虚拟DOM Tree的映射策略等深度适配方案。

## 8. 待处理积压

以下是需提请维护者关注的、持续时间较长且尚未合并的重要PR，它们的功能增量显著，但处于“停滞”状态（标记为`stale`）：

*   **[PR #3063]** feat: add deltachat gateway (创建: 2026-06-08)
    *   **重要性：** 高，引入了新的通信渠道。
    *   **当前状态：** 已标记为`stale`，自6月8日以来无显著进度。
    *   **链接：** https://github.com/sipeed/picoclaw/pull/3063

*   **[PR #3116]** fix(pico): complete turn.done lifecycle signaling (创建: 2026-06-12)
    *   **重要性：** 高，修复了内部消息生命周期的一个核心缺陷。
    *   **当前状态：** 已标记为`stale`，等待review和合并。
    *   **链接：** https://github.com/sipeed/picoclaw/pull/3116

*   **[PR #3115]** Fix inline data URL media extraction for generic tool output (创建: 2026-06-12)
    *   **重要性：** 高，修复了一个会导致会话历史损坏的Bug。
    *   **当前状态：** 已标记为`stale`，等待review和合并。
    *   **链接：** https://github.com/sipeed/picoclaw/pull/3115

**分析师点评：** 这三个PR的功能和修复对于项目的可用性和扩展性至关重要。考虑到今日已清理了大量安全Issues，建议维护团队可以优先从这些积压的、且重要的PR开始进行Review和合并，以尽快为社区交付新功能和稳定性改进。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw 项目动态日报 | 2026-06-25

## 1. 今日速览

过去24小时，NanoClaw 项目保持**高活跃度**，共产生1个新 Issue 和18个 Pull Request，其中2个已合并/关闭。社区贡献者集中发力，提交了多项功能扩展与安全修复，特别是在 **Telegram 多Bot实例支持**、**Matrix 原生E2EE适配器**、**MCP服务器远程连接**等方向有显著进展。虽然无新版本发布，但大量待合并的 PR 表明项目正向功能丰富度和底层安全性双线推进。

---

## 2. 版本发布

**无** 新版本发布。

---

## 3. 项目进展

### 已合并/关闭的 PR（2条）

- **#2849 [已关闭] feat(telegram): support multiple bot instances**  
  作者: grantland  
  支持通过 `TELEGRAM_BOT_TOKEN_<SUFFIX>` 环境变量在单个实例中运行多个 Telegram Bot。**注意：该PR虽被关闭，但相同功能另有一个开放PR #2853 存在，推测关闭原因为重复提交或状态标记问题。**

- **#2799 [已关闭] fix(security): confine send_file reads to /workspace (CVE-2026-29611)**  
  作者: sturdy4days  
  修复了安全漏洞 `CVE-2026-29611`：`send_file` 未对文件路径做根目录约束和规范化，导致被注入的 agent 可读取容器内任意文件（如凭据状态、挂载区的敏感数据）。现在读取范围被限制在 `/workspace` 内。

### 关键待合并 PR 速览

| PR # | 标题 | 方向 | 重要性 |
|------|------|------|--------|
| #2844 | feat(matrix): native persistent E2EE adapter | 功能 | ⭐ 核心基础设施 |
| #2854 | fix(onecli): redirect TMPDIR for gateway CA on macOS | 修复 | 🔴 macOS用户阻塞 |
| #2853 | feat(telegram): support multiple bot instances | 功能 | 社区高频需求 |
| #2842 | Generic inert extension-point seams + reserve MCP names | 架构 | 扩展性提升 |
| #2847 | feat: support URL-based (remote) MCP servers | 功能 | 新能力扩展 |

项目在**安全性加固**（CVE修复）、**多平台兼容性**（macOS CA问题）、**通信协议扩展**（Matrix E2EE、远程MCP）三个维度取得了实质性进展。

---

## 4. 社区热点

### 🔥 Issue #2852：Telegram 多Bot功能为何被移除？

- 链接：[nanocoai/nanoclaw Issue #2852](https://github.com/nanocoai/nanoclaw/issues/2852)
- 作者: Kwisss | 评论: 0 | 👍: 0 | 创建: 2026-06-24

**诉求分析：**
用户反映 Telegram 多Bot功能曾经存在但后来被移除，虽项目声称有“instance”支持，但 Claude（推测指官方AI助手）无法使其正常工作。用户询问该功能是否会被重新实现，还是需要寻找替代方案。

**联动分析：**
此 Issue 与 PR #2849 和 #2853（均为 Telegram 多Bot实例支持）高度相关。说明该功能并非被抛弃，而是正在重构中。用户可能遇到的是**过渡期的断档**，而非功能彻底取消。

---

## 5. Bug 与稳定性

### 严重 Bug / 阻塞问题

1. **#2854 [OPEN] macOS + Rancher Desktop 下所有 agent API 调用失败**  
   - 作者: rodrigocuriel | 创建: 2026-06-25  
   - **严重程度：🔴 高**（影响 macOS 用户全功能使用）  
   - **根因**：OneCLI SDK 将网关 CA 包写入 `TMPDIR`，但容器内无法挂载该路径，导致自签名证书验证失败。  
   - **是否有fix PR**：✅ 本PR即修复，新增环境变量重定向。  
   - 链接：[PR #2854](https://github.com/nanocoai/nanoclaw/pull/2854)

2. **#2850 [OPEN] Signal 群组消息缺少 isMention / isGroup 标记**  
   - 作者: grantland | 创建: 2026-06-24  
   - **严重程度：🟡 中**（导致路由无法区分Bot被提及与群组全体消息）  
   - **是否有fix PR**：✅ 本PR即修复。  
   - 链接：[PR #2850](https://github.com/nanocoai/nanoclaw/pull/2850)

3. **#2802 [OPEN] ncl socket 通信缺少超时和缓冲区上限**  
   - 作者: sturdy4days | 创建: 2026-06-17 | 已更新  
   - **严重程度：🟡 中**（资源泄漏/无限等待风险）  
   - **是否有fix PR**：✅ 本PR即修复。  
   - 链接：[PR #2802](https://github.com/nanocoai/nanoclaw/pull/2802)

4. **#2800 [OPEN] `--folder` 路径穿越漏洞 + `--image-tag` 未限制**  
   - 作者: sturdy4days | 创建: 2026-06-17  
   - **严重程度：🟠 中高**（CWE-22 路径穿越，可逃逸 `GROUPS_DIR`）  
   - **是否有fix PR**：✅ 本PR即修复（加固路径校验、强制image pinning）。  
   - 链接：[PR #2800](https://github.com/nanocoai/nanoclaw/pull/2800)

5. **#2801 [OPEN] `safeParseContent` 对原始JSON原语返回非对象**  
   - 作者: sturdy4days | 创建: 2026-06-17  
   - **严重程度：🟢 低**（但对依赖 `.text`/`.sender` 的路径造成静默失败）  
   - 链接：[PR #2801](https://github.com/nanocoai/nanoclaw/pull/2801)

### 稳定性改进

- **#2851 [OPEN] 测试轮询循环遗弃导致后续测试消息被窃取**  
  - 修复测试基础设施中的资源泄漏，确保测试隔离性。  
  - 链接：[PR #2851](https://github.com/nanocoai/nanoclaw/pull/2851)

- **#2750 [OPEN] 修复容器被KILL后 outbound.db 日志过期问题**  
  - 长期存在的日志竞争条件修复，关联 Issue #2516、#2640。  
  - 链接：[PR #2750](https://github.com/nanocoai/nanoclaw/pull/2750)

---

## 6. 功能请求与路线图信号

### 高可能性纳入下版本的功能

| 功能 | 来源 | 状态 | 判断依据 |
|------|------|------|----------|
| **Telegram 多Bot实例** | Issue #2852 + PR #2853 | 已有实现PR | 社区强烈需求，已有完整实现提议 |
| **Matrix 原生E2EE** | PR #2844 | 技术验证中 | 替换WASM加密为Rust绑定，性能/可靠性提升明显 |
| **远程MCP服务器支持** | PR #2847 | 功能提案 | 扩展MCP生态至HTTP/SSE连接 |
| **Docker-in-Docker 支持** | PR #2846 | 功能修复 | 满足agent组内部使用Docker的场景 |
| **/learn 技能：从任何来源蒸馏可复用技能** | PR #2843 | 新技能提议 | 降低技能创建门槛，提升社区UGC能力 |

### 路线图信号

- **通用扩展点架构**（PR #2842）：作者 foxsky 提交了一组“无注入惰性扩展点”，允许在不改变当前行为的前提下注册自定义逻辑。这可能是未来插件系统的前奏。
- **安全性持续增强**：sturdy4days 连续提交了 #2799/#2800/#2801/#2802 等一系列安全加固PR，涉及文件读取、路径穿越、socket通信等，表明项目进入**安全审计与加固阶段**。

---

## 7. 用户反馈摘要

### 来自 Issue #2852 的痛点

> “we had it, and then it got removed. its said that there is ‘instance’ support, but Claude cannot get it to work, Is it ever going to be implemented? or do we need to look elsewhere?”

**用户画像**：有经验的NanoClaw使用者，曾依赖于Telegram多Bot功能。  
**痛点**：功能被移除后无明确迁移路径。官方文档中的“instance”支持无法实际工作。  
**情绪**：略显沮丧，已在考虑是否切换到其他平台。  
**建议回应**：明确告知#2853已在修复中，并提供临时工作绕过（如使用多个独立实例）。

---

## 8. 待处理积压

### 长期未响应的重要 PR/Issue

| 项目 | 状态 | 创建日期 | 最后更新 | 天数 | 重要性 |
|------|------|----------|----------|------|--------|
| #2802 fix(security): ncl socket hardening | OPEN | 2026-06-17 | 2026-06-24 | 8天 | 高（安全相关） |
| #2800 fix(security): folder + image-tag validation | OPEN | 2026-06-17 | 2026-06-24 | 8天 | 高（安全相关） |
| #2801 fix(router): harden safeParseContent | OPEN | 2026-06-17 | 2026-06-24 | 8天 | 中 |
| #2815 fix(router): guard safeParseContent against primitive JSON | OPEN | 2026-06-18 | 2026-06-24 | 7天 | 中（#2801的替代方案） |
| #2750 fix: recover stale outbound.db journals | OPEN | 2026-06-12 | 2026-06-24 | 13天 | 高（稳定性，关联两个Issue） |

**重点关注**：
- **#2750** 已存在13天，且关联两个已发Issue（#2516、#2640），涉及容器被Kill后的数据恢复，对生产环境稳定性影响大。
- **#2802 / #2800** 均为安全修复，等待合并窗口。建议尽快审查合并，避免安全风险积累。

---

## 总结

NanoClaw 项目今日呈现**高强度社区贡献 + 多方向功能扩展**的健康态势。18个PR的一天量级表明项目处于活跃开发期，且贡献者覆盖面广（至少6位独立贡献者在活动）。安全方面，CVE修复已合入，但仍有数个安全PR待合并。社区热点集中在Telegram多Bot功能回退与重构，建议维护者尽快明确沟通该功能的时间表。整体项目健康度评级：**🟢 良好**，但需加快安全PR合并及积压响应速度。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目的分析师，以下是根据您提供的 IronClaw 项目数据生成的 2026-06-25 项目动态日报。

---

## IronClaw 项目动态日报 — 2026-06-25

### 1. 今日速览

IronClaw 项目今日处于 **高强度迭代与稳定性攻坚** 阶段，活跃度极高。过去24小时内，项目涌现了大量 PR（44条），尤其是针对 Reborn 运行时多次出现的“熔断”和“冻结”问题，核心团队提交了数个根因修复 PR，显示出对系统稳定性的高度关注。同时，围绕 WebUI、工具权限和多租户体验的用户反馈问题集中爆发，社区测试（dogfooding）正在驱动大量体验优化和 bug 修复。整体来看，项目正处于从功能开发向稳定性与用户体验打磨过渡的关键时期。

### 2. 版本发布

**无新版本发布。**

### 3. 项目进展 (今日关键合并/关闭 PR)

今日项目合并/关闭的 17 个 PR 主要集中在 **紧急稳定性修复**、**架构解耦** 和 **功能收尾** 上，重要进展包括：

- **记忆层（Memory）架构重构落地**： 里程碑级的 **PR #5163** (`feat(memory): model memory as a userland extension (#3537)`) 已被合并。该 PR 将 Reborn 的记忆模块从内核中解耦，提取为独立的、与供应商无关的 Crate (`ironclaw_memory` 和 `ironclaw_memory_native`)，为未来支持多种记忆后端（如数据库、向量存储）奠定了基础。这是一个关键的 M2 里程碑。
- **关键 Bug 修复上线**：
    - **PR #5193** (`fix(ci): restore green main ...`) 被合并，修复了因 CI 配置错误导致的 `main` 分支红牌问题，确保了开发流程的畅通。
    - **PR #5190** (`[bug, reborn] ... [Reborn WebUI] Invalid UI bearer token...`) 被关闭，修复了无效令牌允许进入 WebUI 界面但后续操作无响应的误导性问题。
- **核心架构优化推进中**： **PR #5137** (`refactor(reborn): extract ironclaw_reborn_http_kit`) 作为分解巨型 Crate (`ironclaw_reborn_composition`) 的第一步，正在积极开发中。这表明项目在应对代码膨胀，追求更清晰、可维护的架构。

**总结**：项目今日通过合并记忆层的重大重构和关键的 bug 修复，在架构发展和稳定性保障上迈出了坚实一步。

### 4. 社区热点

今日最受关注的议题围绕 **Reborn 运行时** 的稳定性与 **WebUI 交互体验**。

- **根源性分析**： **Issue #5173** (`Daily ironclaw failure taxonomy — 2026-06-23 (deepseek-v4-flash)`) 提供了每日失败分类，揭示了大量测试失败源于基准测试缺陷，而非模型质量。这为社区和开发者指明了当前需要优先解决的痛点。
- **核心修复集**：多项由核心成员 ( `henrypark133`, `serrrfirat` ) 提交的 PR，如 **PR #5204** (`fix(reborn): bound NEAR AI provider calls...`)、**#5206** (`fix(reborn): stop WASM execution from starving...`) 和 **#5203** (`fix(llm): fast-fail a dead/degraded provider...`)，针对 6月24日的运行时熔断事故提出了根本性解决方案。这些 PR 获得了大量关注，因为它们直接关系到用户能否正常使用。
- **WebUI 体验优化**： **PR #5084** (`Redesign the automations page`) 和 **PR #5068** (`tool permissions + global auto-approve settings`) 分别针对自动化页面和工具权限设置进行了重新设计，反映社区对更友好、更可控的用户界面的强烈需求。

**分析**：当前社区的核心诉求非常明确：**稳定性和可用性**。用户通过“狗粮测试”（dogfooding）暴露了大量使用中的痛点，社区和核心开发者正在紧密协作，从根因分析和代码层面进行系统性修复。

### 5. Bug 与稳定性

今日报告的 bug 数量较多，且集中在 Reborn 运行时和 WebUI 上，按严重程度排列如下：

- **严重**：
    - **运行时“冻结”/“熔断”**： **PR #5204** 和 **#5206** 的标题表明，6月24日发生了一起大规模运行时故障，表现为长达4分钟的总线冻结和`lease_expired`错误。根因定位为 `NEAR AI provider` 调用挂起和 `WASM` 执行耗尽 Tokio 工作池。**已有 fix PR (#5204, #5206)**。
    - **认证/授权绕过后台挂起**： **Issue #5190** (已关闭) 和 **#5196**, **#5192** 指出，无效/被拒绝的令牌或工具权限可能导致应用进入“静默挂起”或无响应状态，严重损害用户体验。**已有部分修复 (#5190)**。
- **中等问题**：
    - **捆绑技能误触发安全检查**： **Issue #5169** 指出`Bundled skills`中的普通API词汇（如“Authorization”）会错误地触发提示词安全过滤，导致合法请求失败返回误导性的“临时系统问题”。**暂无 fix PR**。
    - **工具调用状态显示不一致**： **Issue #5189** 反映，成功的工具调用在运行时不会显示活动详情，而失败的工具会显示，导致用户困惑。**暂无 fix PR**。
    - **WebUI 日志不可用**： **Issue #5179** 报告多租户用户无法从 WebUI 访问日志。**已有 fix PR (#5199)**。
- **小问题**：
    - **内部编排消息泄露**： **Issue #5191** 指出，某些内部技能激活或上下文预算信息会直接显示在聊天 UI 中，影响观感。**暂无 fix PR**。

### 6. 功能请求与路线图信号

今日新提出的功能请求主要围绕提升 **可观测性** 和 **内存能力**。

- **可观测性增强**： **Issue #5182** (`Reborn hosted observability: meaningful logs + failure diagnostics`) 由 `serrrfirat` 提出，要求为 Reborn CLI 和托管部署提供有意义的日志和故障诊断能力。结合已有 **PR #5199** (`allow web ui logs for multi-tenancy users`)，这表明 **“日志与诊断”** 是项目下一阶段的核心优化方向。
- **内存系统扩展**： **Issue #5201** (`Reborn memory: remaining #3537 milestones after the M2 lift`) 明确列出了 `#3537` 路线图中的后续步骤，包括上下文清理、边界白名单、用户配置文件读取等功能。紧随其后的是 **PR #5205** (`feat(memory): host-owned context sanitization ...`)，这是一个直接的后续 PR。这表明记忆层功能将在近期得到快速扩展和加固。
- **“按需询问”工具权限体验**： **Issue #5197** 和 **#5196** 反映了用户在设置工具为“Disable”或“Ask each time”时，系统行为不符合预期（如调用无关工具或重复弹出授权）。这些反馈可能会被快速纳入到 **PR #5068** (工具权限设置) 的后续迭代中。

### 7. 用户反馈摘要

从今日的 Issues 评论中可以提炼出以下几点用户痛点：

- **“假死”误导性强**：用户 `zetyquickly` 在 **#5169** 中描述了因安全检查导致的看似“临时系统问题”的报错，体验非常差。这表明系统错误提示需要更精确、更有指导性。
- **操作反馈缺失**：用户 `sunglow666` 在 **#5189** (`Successful tool runs do not show activity details`) 中反映，成功的操作没有进度反馈，而失败的操作却有，这种**不一致的反馈**让用户感到困惑和焦虑。
- **权限控制与预期不符**：用户 `sunglow666` 在 **#5192** 和 **#5196** 中详细描述了工具权限控制的失败场景，核心是 **“用户拒绝/设置后，系统仍试图按原计划执行”**，导致授权流程被破坏，这是自动化流程中一个严重的信任危机。
- **调试困难**：用户 `think-in-universe` 在 **#5179** 中强调了多租户环境下无法查看日志的问题，直接点出 **“调试困难”** 是阻碍用户采用的一个关键障碍。

### 8. 待处理积压

- **长期 E2E 测试失败**： **Issue #4108** (`Nightly E2E failed`) 自 2026-05-27 起持续更新，显示夜间端到端测试长期处于失败状态。这暗示 CI 流程或核心功能可能存在一个持久性的根本问题，需要项目维护者重点关注和根因分析。
- **依赖批量更新 PR 待合并**： **PR #5138** (`build(deps): bump the everything-else group ...`) 已堆积多日，更新了 44 个依赖。此类 PR 通常风险较低但容易因与新代码冲突而被忽略。长期搁置可能导致安全隐患或阻碍后续开发（`dependabot` 通常会自动解决冲突，但需要人工审核）。
- **PR #4002** (`build(deps): bump the actions group`) 情况类似，已堆积超过一个月（自 2026-05-24）。建议项目维护者评估并处理这些依赖更新 PR，以保持供应链健康。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

好的，这是根据您提供的 GitHub 数据生成的 LobsterAI 项目动态日报。

---

# LobsterAI 项目动态日报 | 2026-06-25

## 今日速览

今日项目整体活跃度**极高**，核心贡献者（特别是 `fisherdaddy`）合并了大量从5月25日至6月1日积压的 Pull Requests，数量达到42个。这些合并集中在 **OpenClaw 网关稳定性、IM（即时通讯）插件集成、CoWork 对话状态**等关键模块的修复与优化。同时，一个关于定时任务不可重复执行后自动删除的Issue引发了讨论。尽管没有新版本发布，但代码库在稳定性和功能完整性上取得了显著进步。

## 版本发布

无新版本发布。大量PR的合并可能预示着一次重大版本更新的临近。

## 项目进展

今日合并/关闭了 42 个 PR，主要来自贡献者 `fisherdaddy` 和 `liuzhq1986`，覆盖了几大核心领域：

- **OpenClaw 网关稳定性与修复**：多个PR致力解决OpenClaw网关的启动、重启和资源消耗问题。
    - [#2198](https://github.com/netease-youdao/LobsterAI/pull/2198) 预装了OpenClaw的QQ和Discord官方插件，并同步了相关配置。
    - [#2195](https://github.com/netease-youdao/LobsterAI/pull/2195) 和 [#2196](https://github.com/netease-youdao/LobsterAI/pull/2196) 统一了OpenClaw网关在 macOS/Linux/Windows 下的启动路径，修复了可能被误判为应用路径的问题。
    - [#2043](https://github.com/netease-youdao/LobsterAI/pull/2043) 修复了由GitHub Copilot Token刷新导致的网关重启问题。
    - [#2049](https://github.com/netease-youdao/LobsterAI/pull/2049) 修复了工具调用循环中止后仍在消耗Token的严重问题。
    - [#2050](https://github.com/netease-youdao/LobsterAI/pull/2050) 处理了网关会话更新超时导致聊天界面阻塞的问题。
- **CoWork 协作**：
    - [#2197](https://github.com/netease-youdao/LobsterAI/pull/2197) 修复了在历史记录回退后，最终回答中可能出现重复前缀的问题。
    - [#2058](https://github.com/netease-youdao/LobsterAI/pull/2058) 优化了最终回答与工具结果之间的时间窗口逻辑。
    - [#2078](https://github.com/netease-youdao/LobsterAI/pull/2078) 新增了技能路由元数据的功能，而非简单内联提示。
- **IM (即时通讯)**：
    - [#2063](https://github.com/netease-youdao/LobsterAI/pull/2063) 限定了回复组装在当前轮次，并过滤了推理过程中的“思考”块。
    - [#2086](https://github.com/netease-youdao/LobsterAI/pull/2086) 修复了更新/重装时的一个微信Bug。
- **代码质量与维护**：
    - [#2047](https://github.com/netease-youdao/LobsterAI/pull/2047) 解决了会话冻结的问题。
    - [#2048](https://github.com/netease-youdao/LobsterAI/pull/2048) 过滤了LLM流式输出中的空数据。
    - [#2057](https://github.com/netease-youdao/LobsterAI/pull/2057) 替换了已弃用的VBScript启动器为PowerShell。
    - [#2089](https://github.com/netease-youdao/LobsterAI/pull/2089) 新增了 `minimax m3` 模型支持，并更新了BYOK模型的默认上下文窗口。

## 社区热点

**#1394** [OPEN] [stale] **[定时任务选择不重复执行时，执行一次后会自动被永久删除（预期不自动删除）](https://github.com/netease-youdao/LobsterAI/issues/1394)**
- **作者**: `zqgittest`
- **分析**: 该Issue虽然创建于4月初，但在昨日（6月24日）有更新，是过去24小时内唯一活跃的讨论。用户的核心诉求是**对“不重复”定时任务行为的误解与优化**。用户认为，即使是不重复的任务，在执行完毕后也应保留以供编辑或未来复用，而非直接删除。这反映了用户对任务模板或草稿功能的潜在需求。尽管目前仅有一条评论，但此问题触及了工作流设计的核心逻辑，值得开发者关注。

## Bug 与稳定性

- **严重（已修复）**:
    - **Token持续消耗**: [#2049](https://github.com/netease-youdao/LobsterAI/pull/2049) 修复了OpenClaw工具循环中止后仍在无意义消耗Token的问题，这直接关系到用户的经济成本。
    - **会话冻结**: [#2047](https://github.com/netease-youdao/LobsterAI/pull/2047) 解决了会话界面无法响应的严重问题。
    - **聊天阻塞**: [#2050](https://github.com/netease-youdao/LobsterAI/pull/2050) 修复了网关更新超时导致聊天消息发送被阻塞的问题。
- **中等（已修复）**:
    - **最终回答重复**: [#2197](https://github.com/netease-youdao/LobsterAI/pull/2197) 修复了历史回退后回答中可能出现重复前缀的显示问题。
    - **微信更新Bug**: [#2086](https://github.com/netease-youdao/LobsterAI/pull/2086) 修复了更新或重装时的一个特定于微信的Bug。
- **已有Issue，无PR关联**:
    - **定时任务自动删除**: [#1394](https://github.com/netease-youdao/LobsterAI/issues/1394) 记录了关于“不重复”定时任务逻辑的Bug/功能请求，当前状态为开放，尚无关联的修复PR。

## 功能请求与路线图信号

- **模型与功能扩展（信号：强烈）**:
    - `fisherdaddy` 合并的PR [#2089](https://github.com/netease-youdao/LobsterAI/pull/2089) 增加了对 `minimax m3` 模型的支持并更新了BYOK模型参数，表明项目正持续扩展模型兼容性。
    - 合并的PR [#2198](https://github.com/netease-youdao/LobsterAI/pull/2198) 预装了QQ和Discord官方插件，显示项目在IM/渠道集成方面的努力。

- **工作流/定时任务优化（信号：中等）**:
    - Issue [#1394](https://github.com/netease-youdao/LobsterAI/issues/1394) 要求保留已执行的非重复定时任务。这有可能被纳入下一版本的任务管理优化中。

## 用户反馈摘要

- **痛点**：从Issue [#1394](https://github.com/netease-youdao/LobsterAI/issues/1394) 可以看出，用户对“不重复”任务的期望是**事后可编辑和复用**，而当前“执行后自动删除”的行为与预期相悖，导致了困惑和不满。用户在工作流设计上期待更高的灵活性和容错性。

## 待处理积压

- **Issue #1394** [OPEN] [stale] [**定时任务选择不重复执行时，执行一次后会自动被永久删除（预期不自动删除）**](https://github.com/netease-youdao/LobsterAI/issues/1394)
    - **状态**: 自4月3日创建，6月24日有更新，但仍是`Open`状态。标签为`stale`，可能意味着长期未被处理。
    - **建议**: 建议维护者关注此需求，它涉及到工作流设计的基本逻辑。可以讨论是维持现有行为但增加提示，还是修改行为以保留任务记录。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，根据您提供的 TinyClaw (github.com/TinyAGI/tinyagi) 项目数据，现为您呈上 2026-06-25 的项目动态日报。

---

# TinyClaw 项目日报 | 2026-06-25

## 1. 今日速览

今日项目整体活跃度较低，24小时内无新 Issue 提交或版本发布，社区讨论趋于平静。核心亮点在于一项重要的 **Windows 跨平台兼容性修复** 已成功合并关闭，解决了长期阻碍 Windows 原生用户使用 CLI 的关键障碍。这表明项目团队正在积极弥补平台支持短板，提升项目健康度。目前项目处于小幅迭代与稳定性巩固阶段。

## 2. 版本发布

无。过去24小时无新版本发布。

## 3. 项目进展

今日项目核心进展是合并并关闭了 PR #281，该 PR 聚焦于 **Windows 原生环境（非 WSL）下的 CLI 兼容性修复**。

- **PR #281: [CLOSED] fix: Windows cross-platform support in CLI**
    - **作者**: mperkins0155
    - **简介**: 该 PR 修复了三个导致 `tinyagi` CLI 在原生 Windows 上无法运行的 Bug：
        1.  **驱动器号重复问题**: 解决了 `new URL('.', import.meta.url).pathname` 在 Windows 下返回 `/C:/Users/...` 路径（包含前导斜杠），导致 `path.resolve` 将其解析为 `C:\C:\Users\...` 双驱动器号错误，进而引发 `MODULE_NOT_FOUND` 的问题。
    - **影响**: 此修复是 TinyClaw 向“真正跨平台”迈出的关键一步，解决了 Windows 用户长期无法原生使用的痛点，极大地提升了该项目在 Windows 开发者/用户群体中的可用性。

## 4. 社区热点

今日社区讨论相对平静，无高热度讨论的 Issues 或 PRs。PR #281 是过去24小时内唯一的动态，其核心诉求明确指向**平台的普适性**。随着个人 AI 助手工具的发展，社区对跨平台（特别是 Windows）原生体验的呼声日益增高。此次修复表明项目团队对此予以了迅速响应。

## 5. Bug 与稳定性

今日报告并修复了 **1 个严重 Bug**：

- **Bug**: Windows 原生 CLI 环境下的 `MODULE_NOT_FOUND` 错误。
- **严重程度**: **严重**。该问题直接导致 Windows 用户无法安装并运行 CLI，属于环境阻塞性 Bug。
- **状态**: **已修复**。PR #281 已合并关闭，该 Bug 已通过代码修复解决。

## 6. 功能请求与路线图信号

今日社区无新的功能请求 Issue 提出。

**路线图信号分析**:
PR #281 的快速合并和关闭，释放了强烈的路线图信号：
- **平台兼容性优先级提升**: 项目团队有意将跨平台支持（特别是对 Windows 的原生支持）作为近期发展的重点，以确保不同操作系统的用户都能获得一致体验。
- **开发者体验优化**: 解决 CLI 核心启动问题，表明团队正从基础工具链层面出发，优化开发者和用户的初始体验，降低上手门槛。

这预示着下一个小版本（或后续版本）可能会包含更多关于 Windows 平台（如文件路径、环境变量、进程管理）的全面兼容性测试与修复。

## 7. 用户反馈摘要

由于过去24小时无新 Issue 或 PR 评论产生，主要用户反馈可归纳为来自 PR #281 作者及维护者的行为：

- **痛点明确**: 用户 `mperkins0155` 发现了安装后无法运行 CLI 的直接体验问题，并定位到具体的 Node.js 路径处理机制与 Windows 系统兼容性的深度技术问题。
- **贡献积极**: 用户不仅报告了问题，还主动提交了高质量的修复代码，侧面反映出社区中有一定数量的 Deep C/C++/Node.js 开发者和“行动派”用户，他们愿意主动修复自己遇到的问题，回馈社区。

## 8. 待处理积压

当前无长期未响应的重要 Issue 或 PR。项目维护状态良好，需继续保持。建议项目维护者在下一个小版本发布前，统一回顾并关闭更早之前的、可能已被修复或过时的 Issue，以保持项目看板的清爽。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

好的，作为AI智能体与个人AI助手领域的开源项目分析师，我将根据您提供的CoPaw (github.com/agentscope-ai/CoPaw) GitHub数据，生成一份结构清晰、数据驱动的项目动态日报。

---

# CoPaw 项目动态日报 | 2026-06-25

## 1. 今日速览

项目今日活跃度**极高**，近24小时社区提交了24条Issue和50个PR，显示出社区参与度和开发者投入均处于高位。当前，项目正处于关键的 **AgentScope 2.0 迁移后稳定期**，大量工作集中在修复版本迁移带来的兼容性问题（如消息流、流式传输、工具调用渲染等）。此外，社区对**自定义提供商兼容性**、**前端性能体验**以及**插件系统扩展性**表现出了强烈诉求。虽然有多个严重Bug被报告，但对应的修复PR也已快速跟进，展现了项目良好的响应能力。

## 2. 版本发布

**无**

## 3. 项目进展

今日合并/关闭了多个重要PR，主要聚焦于修复2.0迁移导致的回归问题：

- **[已关闭] #5493 - fix(token_usage): restore chat token/context usage ring & popover under agentscope 2.0**：修复了AgentScope 2.0迁移后，聊天界面中Token/上下文用量显示组件（环形图与弹出框）无法渲染的问题。这是对核心用户体验的重要修复。
- **[已关闭] #5491 - fix(dashscope): honour extra_body generate_kwargs and avoid sending default enable_thinking**：修复了DashScope（阿里云模型）提供商的兼容性问题，使其能正确处理旧版兼容代码路径中的`generate_kwargs`，并避免了发送默认的`enable_thinking`参数带来的潜在问题。
- **PR #5487 - fix(channel): restore streaming path and split multi-segment reply into separate streaming boxes**：核心修复，恢复了所有IM渠道（如飞书、钉钉等）在2.0迁移后完全断裂的流式传输路径。同时优化了多段回复的显示逻辑。
- **PR #5495 - fix(runtime): align envelope event translation with v1 streaming protocol**：对齐2.0 SSE事件翻译逻辑与1.0版本的流式协议，修复了前端工具调用渲染错误的问题。此问题曾导致工具调用显示为堆叠块而非分组显示。

**总结**：今日项目进展集中在“修旧”而非“建新”，通过解决2.0迁移后的一系列关键性回归Bug，项目正向一个更稳定、更兼容的2.0版本稳步迈进。

## 4. 社区热点

今日讨论最活跃、关注度最高的Issue反映了用户对“兼容性”和“易用性”的强烈需求。

1.  **[OPEN] #5345 - [Bug]: Custom OpenAI-compatible providers (e.g. OMLX) don't support function calling**
    - **链接**: [Issue #5345](https://github.com/agentscope-ai/QwenPaw/issues/5345)
    - **分析**: 该问题获得了8条评论，是今日讨论最激烈的主题。用户报告称，像OMLX这样实现完整OpenAI兼容API的自定义提供商，在CoPaw中无法使用Function Calling功能，而原生支持的Ollama则工作正常。这揭示了用户对**集成非主流/区域性模型提供商**的强烈需求，以及当前自定义提供商实现不完善的问题，是社区功能诉求的**头号热点**。

2.  **[OPEN] #5403 - [BUG] Browser autofill hijacks search input in Model Configuration page**
    - **链接**: [Issue #5403](https://github.com/agentscope-ai/QwenPaw/issues/5403)
    - **分析**: 该问题涉及前端UI交互细节，浏览器自动填充功能错误地将“搜索提供商”输入框识别为密码框，导致弹出保存的用户名/密码建议。这虽然是一个小Bug，但直接影响了模型配置的日常操作流程，获得了4条评论，说明用户对**产品细节和体验**非常敏感。

## 5. Bug 与稳定性

今日报告的Bug数量较多，按严重程度排列如下：

- **严重（影响核心功能）**:
    - **[OPEN] #5505 - MiniMax-M3 图片安全审核错误被缓存为 `rejects_media=True`**：该问题非常严重。因图片被内容安全审核拒绝，系统错误地认为模型“不支持图片”，并缓存该错误状态，导致后续所有包含图片的请求在发送前被错误剥离。这直接破坏了视觉类Agent的核心能力。**暂无明确Fix PR**。
    - **[OPEN] #5379 - [Bug]: 通过Python命令安装后启动，直接报错Internal Server Error**：用户刚安装就遭遇500错误，日志指向`get_remote_addr(transport)`，严重影响新用户上手体验。**暂无明确Fix PR**。
    - **[OPEN] #5401 - [Bug]: Console: session with large tool-use history fails to render**：包含大量工具调用的对话历史导致前端白屏/崩溃。这是前端性能和容错性问题，限制了Agent处理复杂任务的能力。**暂无明确Fix PR**。
    - **[CLOSED] #5373 - [Bug]: Shell command execution fails to parse shell special characters**：核心工具功能缺陷，无法处理Shell管道、重定向等操作符。**已关闭**，说明已修复或确认非Bug。
    - **[CLOSED] #5264 - [Bug] 群聊消息回复被发送到私聊**：一个令人困扰的渠道消息路由Bug，严重影响多会话场景下的使用体验。**已关闭**，表明已修复。

- **中等（影响特定功能或体验）**:
    - **[OPEN] #5479 - 【前端性能】大会话文件（>500KB）打开报错**：涉及前端加载大型会话的性能问题，直接导致页面崩溃，无法查看历史记录。
    - **[OPEN] #5480 - Console 长消息排版错乱**：长Markdown消息排版不渲染，需切换Tab才能恢复。影响信息可读性。
    - **[OPEN] #5501 - [Bug]: 宽屏模式下聊天窗口发送按钮对不齐**：UI细节问题，已有**PR #5502** 尝试修复。
    - **[CLOSED] #5476 - [Bug]: 移动端无法切换智能体**：移动端关键功能缺失。**已关闭**。

## 6. 功能请求与路线图信号

今日收到的功能请求显示出社区对插件化和生态扩展的期望：

- **[OPEN] #5484 - [Feature]: Support installing plugins via pip from PyPI**: 用户建议支持通过PyPI安装插件，从而统一Python生态的安装体验。这是一个重要的生态建设信号。**已有对应的PR #5492** 正在开发中，很可能会被纳入下一个小版本。
- **[OPEN] #5489 - [Feature]: Support OpenAI response format**: 要求支持OpenAI格式的响应信息，可能旨在与更广泛的工具链或应用（如OpenAI的Structured Outputs）进行互操作。这体现了社区对**标准化**和**互操作性**的追求。
- **[OPEN] #5427 - [Feature]: Kimi Coding Plan Models configuration**: 用户希望支持Kimi K2 Code模型的Anthropic兼容API端点。这与#5345号Issue的自定义提供商Function Calling问题相关，说明社区对非标准API格式的模型支持有需求。
- **[OPEN] #5455 - [Question]: Why not make the current time a per-user-message prefix instead of putting it in environment/system context?**: 该问题讨论了时间戳在上下文中的放置位置，旨在优化Prompt缓存稳定性。提出者**已有本地实现**，并且社区贡献者**已提交PR #5499**来推动此改动，显示出社区驱动的技术探讨正在转化为实际贡献。
- **[OPEN] #5231 - [Feature]: MCP 工具名称在聊天界面显示原始名称，以及文件卡片默认展开优化**: 用户希望MCP工具的显示名称更人性化，这涉及到模型调用数据与前端展示的分离，是一个不错的可用性优化点。

## 7. 用户反馈摘要

- **痛点**:
    - **自定义模型集成困难**：用户（qiyuanlicn）在#5345中详细描述了使用自定义OpenAI兼容提供商遇到Function Calling失败的场景，并提供了与Ollama的对比，代表了一批希望“白嫖”或使用特殊模型用户的心声。
    - **安装与上手门槛**：用户（luo201227）在#5379中反映，安装后直接报500错误，使得新用户的“第一次体验”极差，这可能流失潜在用户。
    - **前端性能瓶颈**：多名用户（如rescodexx, Nasak2, samluoabc）抱怨前端在会话数据量大时出现卡顿或直接崩溃，这表明前端渲染性能是当前一个突出的短板。
    - **渠道消息路由异常**：用户（feng183043996）在#5264中记录了一个逻辑严谨的群聊/私聊消息串扰Bug，并提供了日志证据，展示了高价值用户在使用复杂IM场景时的困扰。

- **满意度**:
    - **Bug修复响应快**：从#5373、#5264、#5503等多个Issues被快速关闭来看，用户反馈的问题得到了及时处理。
    - **社区贡献积极性高**：从#5455的提问到**PR #5499**的快速跟进，以及**PR #5492**、**PR #5506**等多个贡献者提交的PR可以看出，社区成员愿意投入精力来改进项目，整体社区生态健康向上。

## 8. 待处理积压

- **重要 Issue 待维护者回应或跟进**:
    - **[OPEN] #5345 - Custom OpenAI-compatible providers don’t support function calling**: 社区呼声最高的问题，已进入技术讨论，但缺乏官方维护者的明确技术路线图或解决方案承诺。
    - **[OPEN] #5379 - Internal Server Error on first startup**: 严重影响新用户体验的核心Bug，需尽快定位根因并给出临时解决方案或修订。
    - **[OPEN] #5401 - Console crash with large tool-use history**: 长期存在的前端性能瓶颈，会影响高级用户的使用，需要从前端虚拟滚动或后端分页传输两方面考虑解决方案。

- **长期未动的 PR 待 Code Review**:
    - **[OPEN] #4041 - feat(cli-desktop): System tray startup item function**: 提出于5月5日，已超过50天未合并。功能（系统托盘启动）完整且已实现Windows支持，但状态仍为`Under Review`，可能因优先级或技术细节被搁置。
    - **[OPEN] #4669 - feat(desktop): add tauri auto updater**: 提出于5月25日，是桌面版用户长期等待的功能。同样处于`OPEN`状态，需要维护者评估和推动。

**建议**：维护者团队应优先关注 #5345 和 #5379 两个极具代表性的问题，并着手审查积压的PR，特别是 #4041 和 #4669，以进一步提升产品稳定性和桌面用户体验。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，我将根据您提供的ZeroClaw项目数据，为您生成2026年6月25日的项目动态日报。

---

## ZeroClaw 项目动态日报 | 2026-06-25

### 1. 今日速览

ZeroClaw 项目今日处于 **高活跃度** 状态。社区讨论激烈，核心聚焦在 **安全、多租户架构和运行时稳定性** 三个方向。Issue 和 PR 数量均维持高位（43条 Issue，50条 PR），显示出项目正在经历一个密集的功能设计与问题修复周期。尽管今日无新版本发布，但大量针对权限隔离（RBAC、OIDC）、插件系统（WASM）和严重Bug（如委托代理逃逸工具白名单）的深度讨论，表明项目正处于架构升级的关键阶段，社区驱动力强劲。

### 2. 版本发布

**无**

### 3. 项目进展

今日项目在几个关键方向上取得了实质性进展，主要体现在**已关闭的PR**和**部分重要功能合并**上：

- **核心故障修复与架构修复合并**:
    - **PR #7771** (已关闭): 修复了观察者事件的遥测链路传播问题，现在 `channel`, `agent_alias` 和 `turn_id` 能正确传递给所有Agent生命周期事件，改善了可观测性和调试能力。
    - **PR #8100 / #8164** (均已关闭): 两个PR均修复了NVIDIA NIM模型提供商的视觉能力支持问题，通过添加缺失的 `vision` 能力标志，使得多模态模型（如LLaVA）可以正常工作。
    - **PR #8101** (已关闭): 修复了 `fill-translations` 工具在修复文本泄露时，未清除遗留的续行符，导致重新解析后泄露数据仍存在的Bug。

- **重要功能推进与发布准备**:
    - **PR #8234** (开放中): 启动了v0.8.2版本的发布流程，包括版本号提升和变更日志更新。这表明团队正在准备一次维护性发布。
    - **PR #8313** (开放中): 一项重要的技能系统改进，默认采用紧凑注入模式。这改进了Agent的性能，将冗长的技能描述移至按需加载，是朝着更高效Agent交互迈出的关键一步。

**小结**: 项目今日修复了数个关键bug，并推进了下一次发布的准备工作，整体处于稳健的“修复-改进-发布”循环中。

### 4. 社区热点

今日讨论最激烈的议题集中在**安全与权限隔离**，这是社区的核心关切：

1. **[#7141] OIDC Authentication Provider support** (评论: 6): 关于引入标准身份认证提供者的讨论持续升温。这背后反映出社区对**摆脱单一、不安全认证方式**的强烈诉求，特别是对于生产环境下的多用户部署场景。

2. **[#8177] RFC: Supply chain signing - hardware PGP, hermetic builds, and SLSA provenance** (评论: 6): 对供应链安全（Supply Chain Security）的关注度极高。社区希望项目能采用硬件PGP、SLSA溯源等业界标准来保证发布物（容器镜像、二进制文件）的完整性，这表明用户对ZeroClaw的**企业级可信度**提出了更高要求。

3. **[#5982] Per-sender RBAC for multi-tenant agent deployments** (评论: 9): 作为讨论最火爆的议题，该Feature Request直指多租户环境下的核心痛点——**精细化权限控制**。社区需要一个能区分客户、运营、开发者角色的访问控制系统，以实现工作空间、工具集和速率限制的隔离。它已成为当前安全讨论的基石。

### 5. Bug 与稳定性

今日报告的Bug数量多且严重，主要集中在**安全隔离失效**和**数据丢失**风险上。按严重程度排列如下：

- **[S0 - 数据丢失/安全风险] #8279** (开放中): **严重安全漏洞**。`delegate` 工具会绕过父Agent的工具白名单，子Agent可以调用父Agent策略明确排除的工具。**已有 PR #7960 提交修复**（`fix(tools): gate execute_pipeline sub-tool execution with per-agent ToolAccessPolicy`），但尚未合并。
- **[S1 - 工作流阻塞] #8151** (已关闭): 在Matrix频道中，延迟处理的图片附件在重新加载历史时丢失引用，导致Agent后续否认看到过该图片。会严重影响基于图片的交互流程。
- **[S2 - 降级行为] #8312** (开放中): 一个新的数据泄露Bug。某些修复操作会留下“残余”的翻译条目，这些条目会在后续操作中重新“泄露”用户的翻译文本。
- **[S2 - 降级行为] #5903** (开放中): MCP子进程内存泄漏。当心跳检测启用时，每个心跳周期都会产生一个未被清理的MCP子进程，长时间运行会耗尽系统资源。
- **[S2 - 降级行为] #7733** (开放中): **配置无效果**。`mcp_bundles` 字段虽能解析并显示在配置中，但运行时并未实际强制执行，导致按Agent隔离MCP工具的功能是一个“静默的无效操作”，这是一个严重的安全感知差距。

### 6. 功能请求与路线图信号

今日的新功能请求与路线图信号明确指向**企业级多租户、插件系统标准化和更灵活的Agent执行模式**。

- **多租户与安全（高优先级）**:
    - **#8290** (新, 追踪Issue): 正式启动“多用户里程碑”，核心目标是实现`per-principal isolation + per-sender authz`。这将整合 #5982 (RBAC)、#7141 (OIDC) 等工作，是下一阶段的核心路线图。
    - **#8226** (新): 支持按Agent自定义环境变量，解决多租户下的凭证和令牌隔离问题，是 #8290 的具体实现之一。
    - **#8309** (新): 针对“SkillForge”功能进行技术决策，决定是“用安全默认值恢复并连接”还是“移除该功能”，凸显了团队对功能实用性和安全风险的权衡。

- **插件系统进化**:
    - **#7497** (RFC): 提出使用OCI规范容器镜像仓库作为WASM插件的存储、分发和发现机制，这将彻底改变插件的分发和验证模型，提升插件生态的可扩展性和安全性。
    - **#8187** (RFC): 提案为WASM插件添加硬件访问能力（GPIO, SPI, I2C等），表明ZeroClaw正在探索IoT和边缘计算场景。

- **Agent能力深化**:
    - **#8303** (RFC): 提出“Goal mode”（目标模式），允许Agent在一个用户目标的引导下持续工作，直到完成、暂停或失败。这超越了现有的回合制交互，使ZeroClaw能处理更复杂的、长周期的任务。

### 7. 用户反馈摘要

从今日的Issue和PR评论中，可以提炼出以下用户痛点和场景：

- **“我的配置没生效”**: 用户`metalmon`在 #7733 中报告了 `mcp_bundles` 字段是“静默的无效操作”，这是一个典型的安全感知问题：**用户以为配置了隔离，但实际上并没有，导致安全幻觉**。
- **“它用了我的权限，但我没授权”**: 用户`wangmiao0668000666`在 #8279 中发现的委托Agent权限逃逸问题，反映了**用户对Agent代理行为的细粒度控制有极高要求**，尤其是当涉及敏感工具（如Shell）时。
- **“图片处理令人困惑”**: 用户`aq-uua`在 #5514 中反馈Telegram发送多张图片时，Agent会产生多个重复回复。用户`singlerider`报告了 #8151 中图片在Matrix上丢失引用。这显示了**不同频道在多媒体消息处理上的不一致性和行为异常**是用户常见的痛点。
- **“开发者需要更强的安全保障”**: 关于 #7141 (OIDC) 和 #8177 (供应链安全) 的持续讨论表明，社区开发者群体关心的是**项目的生产就绪性和企业采用门槛**，他们需要标准化的认证和安全发布流程。

### 8. 待处理积压

以下为长期未响应或进展缓慢，但影响重大的Issue/PR，提醒维护者关注：

- **[#5514] Agent request appends each subsequent image** (2026-04-08): 一个持续超过两个月的Telegram多图片处理Bug，虽不严重但影响用户体验。
- **[#5903] MCP stdio child processes accumulate** (2026-04-19): 同样存在两个月的MCP子进程泄漏问题，对于长时间运行的Daemon服务是潜在的系统稳定性炸弹。
- **[#6943] RFC: Deconflict Plugin System Goals** (2026-05-26): 这是关于插件系统架构方向的关键性澄清RFC。它指出了当前设计文档（FND-001）中存在互相矛盾的目标，急需维护者介入决策，以消除贡献者的困惑。

**建议**: 建议项目维护者优先审视 #6943 的架构冲突问题，同时将 #8279 (委托权限逃逸) 和 #5903 (MCP泄漏) 列为最优先级的待修复Bug。

</details>

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*