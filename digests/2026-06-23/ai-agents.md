# OpenClaw 生态日报 2026-06-23

> Issues: 259 | PRs: 500 | 覆盖项目: 13 个 | 生成时间: 2026-06-23 03:31 UTC

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

好的，这是为您生成的 OpenClaw 项目动态日报。

# OpenClaw 项目动态日报 — 2026-06-23

## 1. 今日速览

今日 OpenClaw 项目继续保持超高活跃度，过去 24 小时内社区贡献了大量 Issues (259 条) 和 PRs (500 条)，显示出极强的开发与反馈动能。虽然待合并 PR 积压较多 (441 条)，但也涌现了多个关键修复和性能优化 PR，如修复 Codex 消息延迟、加速 CI 等。发布了一个新的 Beta 版本，重点改进了对话快速模式与模型路由可靠性。整体来看，项目处于高速迭代期，社区活跃，但稳定性和 Bug 修复仍是当前核心焦点。

## 2. 版本发布

- **[v2026.6.10-beta.2]**
  - **链接**: `openclaw/openclaw` Releases
  - **主要内容**:
    - **自动快速模式**: 现在 OpenClaw 可以在短对话轮次中自动启用快速模式，并在需要长时间运行的场景中返回正常模式，这是一种全新的交互优化。 (#85104)
    - **更可靠的模型路由**: 增强了模型路由的稳定性。
  - **破坏性变更**: 未提及。
  - **迁移注意事项**: 此版本为 Beta 版本，建议在测试环境进行验证。

## 3. 项目进展

今日项目在多个关键问题上取得了进展，一批重要的 PR 已被合并或接近完成，推动了稳定性和功能的完善。

- **修复 Codex 消息延迟与完成问题**:
  - PR [#95942](https://github.com/openclaw/openclaw/pull/95942) (OPEN, maintainer): 修复了 Codex 在 iMessage 上通过 `message_tool_only` 发送回复后，无法正确识别该回复为源回复，导致会话挂起的延迟问题。
  - PR [#95826](https://github.com/openclaw/openclaw/pull/95826) (CLOSED, maintainer): 解决了 `message_tool_only` 模式下 Codex 发送回复后的“尾部”延迟，优化了用户体验。

- **CI 与基础设施优化**:
  - PR [#95944](https://github.com/openclaw/openclaw/pull/95944) (OPEN, maintainer): 通过优化 QA 测试套件，大幅加速了 `smoke-ci` 流程，解决了 PR 因为测试过慢而被阻塞的问题。
  - PR [#95922](https://github.com/openclaw/openclaw/pull/95922) (CLOSED, maintainer): 修复了 CI 中测试箱在设置失败后未能正确最终化的问题，提升了 CI 的健壮性。

- **关键 Bug 修复**:
  - PR [#95417](https://github.com/openclaw/openclaw/pull/95417) (CLOSED): 修复了 Google 嵌入式智能体提示缓存响应读取无界的问题，防止外部端点调用导致性能问题。
  - PR [#95729](https://github.com/openclaw/openclaw/pull/95729) (OPEN): 扩展了模型故障转移原因分类器，以处理仅携带错误代码的提供商错误，确保模型故障转移机制能正确触发。

## 4. 社区热点

以下 Issues 和 PR 引发了社区最广泛的讨论和关注：

- **[Feature Request] 支持PostgreSQL替代SQLite作为内部存储** ([#90370](https://github.com/openclaw/openclaw/issues/90370))
  - **评论数**: 11, 👍: 2
  - **核心诉求**: 用户（尤其是有PostgreSQL基础设施的团队）希望将硬编码的SQLite存储替换为可配置的PostgreSQL，以减少资源浪费、打破数据孤岛并利用PostgreSQL的高级功能（如向量搜索）。这反映了企业级部署对存储灵活性的强烈需求。

- **Closed: Cron scheduled trigger contaminates global runtime state** ([#90991](https://github.com/openclaw/openclaw/issues/90991))
  - **评论数**: 14, 👍: 1, **状态**: CLOSED
  - **核心诉求**: 用户报告了一个严重的系统级问题：Cron定时触发器会污染全局运行时状态，导致整个系统过载失败。该问题已被成功解决，获得了社区的高度关注。

- **[Feature]: Add Antigravity CLI (agy) as CLI backend** ([#84527](https://github.com/openclaw/openclaw/issues/84527))
  - **评论数**: 3, 👍: 9
  - **核心诉求**: 因Google宣布弃用Gemini CLI，社区强力呼吁添加新的 `Antigravity CLI (agy)` 作为替代。此 Issue 获得了大量赞同，显示社区对上游服务变更的敏感性以及对OpenClaw兼容性的高要求。

- **Open: Critical: Gateway Memory Leak — RSS grows from 350MB to 15.5GB** ([#91588](https://github.com/openclaw/openclaw/issues/91588))
  - **评论数**: 13, 👍: 1
  - **核心诉求**: **P0 级问题**。报告了 Gateway 进程存在严重内存泄漏，在2-3天内从350MB增长到15.5GB，导致OOM崩溃和反复重启。这是对生产环境稳定性构成直接威胁的严重 Bug，社区高度聚焦。

## 5. Bug 与稳定性

今日报告的 Bug 中，**会话状态丢失、消息投递失败** 和 **安全问题** 是三大核心类别。

- **Critical (P0)**:
  - **[Gateway 内存泄漏]** [#91588](https://github.com/openclaw/openclaw/issues/91588): RSS从350MB增长到15.5GB，引发OOM崩溃。**暂无关联修复 PR**。

- **High (P1)**:
  - **[Cron 完成投递丢弃 `delivery.channel`]** [#92460](https://github.com/openclaw/openclaw/issues/92460): 即使显式配置了投递渠道，孤立 Cron 任务完成时仍可能因 Announcer 路径问题投递失败。**有关联修复 PR**。
  - **[非Anthropic模型工具调用失败]** [#90288](https://github.com/openclaw/openclaw/issues/90288): 非Anthropic模型将工具调用输出为纯文本而非结构化 `tool_use` 块。**暂无关联修复 PR**。
  - **[macOS location manager 导致TCC权限请求]** [#94147](https://github.com/openclaw/openclaw/issues/94147): macOS桌面端每秒重建 CLLocationManager，引发 TCC 权限请求风暴，影响用户体验。**暂无关联修复 PR**。
  - **[OOM killer 误导用户]** [#95612](https://github.com/openclaw/openclaw/issues/95612): CLI后端与Anthropic交互时返回 `401` 认证错误，而直接使用 `claude` 命令则正常。**暂无关联修复 PR**。

- **Medium (P2)**:
  - **`web_fetch` 忽略 `NO_PROXY`** [#93807](https://github.com/openclaw/openclaw/issues/93807): 所有请求（包括本地地址）都被强制通过代理。**暂无关联修复 PR**。
  - **`write` 工具和 `exec` heredocs 插入`\n`文本** [#93139](https://github.com/openclaw/openclaw/issues/93139): 工具将文本中的 `\n` 解释为字面字符而非换行。**暂无关联修复 PR**。

## 6. 功能请求与路线图信号

- **呼声最高的功能**:
  - **PostgreSQL 存储支持** ([#90370](https://github.com/openclaw/openclaw/issues/90370)): 此功能请求反映了高级用户对灵活后端存储的迫切需求，是进入企业市场的关键功能。
  - **Telegram Inline Query** ([#54794](https://github.com/openclaw/openclaw/issues/54794)): 用户希望能在任意聊天中通过 `@botname query` 调用机器人，此功能已存在数月，是 Telegram 社区长期以来的核心诉求。

- **可能纳入下一版本的功能**:
  - **Antigravity CLI (agy) 后端** ([#84527](https://github.com/openclaw/openclaw/issues/84527)): 鉴于 Google 将在 6月18日 停止 Gemini CLI 服务，更换后端的优先级极高。社区已提出明确的功能请求并有 9 个 👍，维护者很可能快速响应。
  - **按源目录索引内存，而非按智能体** ([#95724](https://github.com/openclaw/openclaw/issues/95724)): 这是一个优化提案，建议共享同一工作区的智能体共享向量索引，避免重复构建和存储。有助于减少资源消耗并提升性能。

## 7. 用户反馈摘要

- **满意点**:
  - 用户对项目的开发速度和活跃度普遍表示认可。尽管面临复杂问题，但快速迭代和修复的态度获得了社区的肯定。
  - Beta 版本的自动快速模式 (#85104) 受到了社区的感谢（@alexph-dev 和 @vincentkoc）。

- **痛点与不满**:
  - **稳定性问题频发**: 大量用户报告了会话状态丢失、消息投递失败、内存泄漏等回归问题和 Bug，严重影响了使用体验。
  - **升级体验差**: 升级到 v2026.6.9 后，内存存储被静默迁移，导致全面重新嵌入，且没有任何提示 ([#95495](https://github.com/openclaw/openclaw/issues/95495))，用户体验糟糕。
  - **调试困难**: 多个问题（如 [#88312](https://github.com/openclaw/openclaw/issues/88312), [#91588](https://github.com/openclaw/openclaw/issues/91588)）的诊断信息不足，用户难以自行排错，对 Gateway Crash Loop 等问题感到无奈。
  - **模型兼容性**: 非Anthropic模型（如 DeepSeek, MiniMax）的间歇性兼容问题和工具调用失败，让依赖这些低成本/多样化模型的用户感到困扰。

## 8. 待处理积压

以下为长时间未响应的开放 Issue 或 PR，提醒维护者关注：

- **[PR #67077] fix(auth-profiles): make post-success bookkeeping saves non-fatal** (2026-04-15 创建, 状态: ⏳ waiting on author)
  - 该 PR 修复 Windows 下因文件只读属性导致认证失败的顽固问题。已等待作者超过 2 个月，建议跟进。
  - [PR Link](https://github.com/openclaw/openclaw/pull/67077)

- **[Issue #54794] [Feature] Telegram Inline Query Support** (2026-03-26 创建, 开放中)
  - Telegram 社区的核心功能请求之一，已搁置近 3 个月。如果路线图中有重振 Telegram 生态的计划，请考虑评估。
  - [Issue Link](https://github.com/openclaw/openclaw/issues/54794)

- **[PR #76077] fix: add --timeout flag to openclaw message send with SIGTERM support** (2026-05-02 创建, 状态: 📣 needs proof)
  - 该 PR 解决了 `openclaw message send` 命令可能无限挂起的问题，对于命令行用户非常实用。需要维护者介入确认真实行为。
  - [PR Link](https://github.com/openclaw/openclaw/pull/76077)

---

## 横向生态对比

好的，作为您的资深技术分析师，现基于您提供的各项目2026年6月23日动态，为您呈上一份**个人AI助手/自主智能体开源生态横向对比分析报告**。

---

## 个人AI智能体开源生态横向对比分析报告 (2026-06-23)

### 1. 生态全景

当前，个人AI助手与自主智能体开源生态正经历**从“功能堆叠”向“系统化工程”的深刻转型**。整体态势呈现三个特征：**第一，社区共识高度聚焦于稳定性与安全性**，多项目不约而同地将资源投入到修复内存泄漏、加固认证、优化上下文管理及保障供应链安全上，标志着行业已跳出“能否实现”的初级阶段，进入“能否可靠运行”的质量攻坚期。**第二，企业级部署与深度定制的需求显著抬头**，对PostgreSQL等成熟存储后端、原生云服务提供商（如Vertex AI）的接入呼声日益高涨，反映了用户从个人尝鲜向生产级应用的场景迁移。**第三，核心架构进入重构窗口期**，以ZeroClaw和OpenClaw为代表，多个项目正在探索Wasm化、去核心依赖（如Node.js）、以及更精细的权限与流程控制（如Plan Mode），预示着下一代智能体平台将在可移植性、安全性和可控性上实现跃升。

### 2. 各项目活跃度对比

| 项目名称 | 24h Issues | 24h PRs | 新版本 | 待合并PR | 健康度与状态评估 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 259 | 500 | ✅ Beta | 441 | **高速迭代，性能与稳定是核心焦点**。极高的社区活跃度也带来了大量待处理积压，需要有效的优先级管理。 |
| **NanoBot** | 6 | 13 | ✅ v0.2.2 | 数量低 | **稳健迭代，质量巩固**。版本发布聚焦“耐久性”，Bug修复响应迅速，社区贡献质量高，项目成熟度稳步提升。 |
| **Hermes Agent** | 100+ | (与Issue合计) | ❌ | 数量多 | **平台适配攻坚期**。社区对Google Vertex AI等原生服务接入需求强烈，但桌面端构建等基础问题开始暴露并引发开发者挫败感。 |
| **PicoClaw** | ~19 | ~19 | ❌ | 少量 | **积极迭代，安全与渠道并重**。通过合并PR修复了WhatsApp稳定性核心Bug，同时社区贡献向Android ADB操控等细分领域延伸。 |
| **NanoClaw** | 0 | 5 | ❌ | 4 | **社区驱动，功能拓展期**。活跃度中等，但社区贡献者正在积极添加Telegram、邮件等新渠道，项目功能边界在社区推动下扩大。 |
| **NullClaw** | 0 | 2 | ❌ | 2 | **低活跃，维护模式**。核心开发节奏放缓，社区贡献集中在依赖更新和特定渠道（Matrix）的稳定性修复上。 |
| **IronClaw** | 15 | 24 | ❌ | 16 | **高强度重构，架构演进期**。围绕其“Reborn”架构进行密集开发，并发执行、精细化权限模型落地，但短期内引入了性能回归问题。 |
| **LobsterAI** | 0 | 6 | ❌ | 多个(Stale) | **核心功能与插件生态齐头并进**。合并了“计划模式”和OpenClaw插件修复，但同时存在大量积压数月的高优先级Bug，存在技术债务隐患。 |
| **TinyClaw** | 0 | 0 | ❌ | - | **休眠状态**。 |
| **Moltis** | 0 | 0 | ❌ | - | **休眠状态**。 |
| **CoPaw** | (高) | 50 | ❌ | 部分 | **高活跃度，稳定性问题突出**。社区围绕核心进程冻结等严重Bug展开热烈讨论，同时移动端适配和新集成在快速推进。 |
| **ZeptoClaw** | 0 | 0 | ❌ | - | **休眠状态**。 |
| **ZeroClaw** | 50+ | 50+ | ❌ | 48 | **架构重构驱动的高活跃度**。社区正在就“去Node.js化”和“Wasm-first”进行激烈辩论，多项S级Bug修复和根本性重构PR在流程中。 |

- **健康度分层**：
    - **快速迭代期（高风险高回报）**: OpenClaw, IronClaw, ZeroClaw。它们处于架构/功能密集开发期，创新性强但稳定性波动大。
    - **质量巩固期（稳定可靠）**: NanoBot。项目节奏平稳，以修复和优化为主，用户体验提升明显。
    - **功能拓展期（社区驱动）**: PicoClaw, NanoClaw, Hermes Agent。社区贡献活跃，积极拓展平台边界，但面临一些平台兼容性挑战。
    - **维护与休眠期**: NullClaw, TinyClaw, Moltis, ZeptoClaw。开发活动减缓或停滞。

### 3. OpenClaw 在生态中的定位

OpenClaw 作为本报告的核心参照，在生态中扮演着 **“超级大本营”与“风向标”** 的角色。
- **优势与差异**：
    1.  **压倒性的社区规模**：259条Issues和500条PR的日活量，数倍于其他项目。这种规模使其成为生态中最庞大的思想碰撞和Bug发现平台，任何微小的功能或性能改进都可能被放大数倍讨论。
    2.  **技术路线的先锋性**：它率先探索了 `自动快速模式`、`更可靠的模型路由` 等精细化交互控制，同时其庞大的插件生态（CoPaw等作为其插件之一）意味着它正在构建一个事实上的标准界面。
    3.  **随之而来的管理挑战**：441条待合并PR是OpenClaw双刃剑的体现。巨大的开发动能带来了严重的**积压风险**，这与其他项目（如NanoBot）精悍高效的PR处理形成鲜明对比。维护者面临严重的“认知过载”，可能导致部分社区贡献被忽视。

- **与同类对比**：与**NanoBot**（注重“耐久性”）和**NanoClaw**（社区驱动功能扩展）相比，OpenClaw更像一个庞大的“城市”，基础设施完善但交通拥堵；而NanoBot则像一个高效运转的“精工车间”。**IronClaw**虽然也是架构重构，但其范围限于“Reborn”内部，而OpenClaw的变动波及整个生态。**ZeroClaw**的“激进革命”路线（Wasm-first）与OpenClaw的“改良演进”路线形成了鲜明对比。

### 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求/表现 |
| :--- | :--- | :--- |
| **存储与基础设施** | OpenClaw, LobsterAI, IronClaw, Hermes Agent | 支持**PostgreSQL替代SQLite**作为内部存储；提供**云原生托管数据库**支持。 |
| **原生云服务提供商** | Hermes Agent, ZeroClaw | 要求直接接入**Google Vertex AI**、**OpenRouter**等大模型提供商，避免中间代理。 |
| **渠道与通信协议** | NanoBot, NanoClaw, IronClaw, PicoClaw, CoPaw | 新增或增强对 **Telegram (富文本/Webhook)、IMAP/SMTP 邮件、SimpleX/Tox、Slack** 等通信协议的原生支持。 |
| **模型路由与可靠性** | OpenClaw, ZeroClaw, CoPaw, Hermes Agent | 实现**模型故障转移**、**自动模型切换**、提升**非Anthropic模型的工具调用兼容性**。 |
| **上下文管理与内存** | ZeroClaw, IronClaw, CoPaw | 解决**上下文预算超限**问题；探索**智能体自我进化与技能提取**。 |
| **安全与权限** | PicoClaw, IronClaw, ZeroClaw | 强化**跨站点请求防御**、**精细化/分层审批权限**、**Wasm插件签名验证**。 |
| **桌面与移动端体验** | Hermes Agent, CoPaw | 修复**桌面端构建失败**、优化**移动端WebUI/小屏幕适配**。 |

### 5. 差异化定位分析

- **OpenClaw**: **全能型生态平台**。目标用户是开发者与高级用户，追求高度可定制化与广泛的插件/渠道生态。架构庞大，功能全面但复杂性高。
- **NanoBot**: **耐用型个人助手**。强调稳定、可靠、开箱即用。目标用户是追求长期稳定体验的个人用户，社区互动高效。
- **Hermes Agent**: **全渠道覆盖的Agent**。功能全面，但当前正应对平台适配的阵痛。从社区反馈看，用户群更偏向追求低成本、多样化模型的成本敏感型用户。
- **PicoClaw**: **轻量级嵌入/专精Agent**。聚焦于特定场景优化（如WhatsApp集成、设备ADB操控），追求轻量化与高集成度。
- **NanoClaw**: **社区驱动型扩展Agent**。核心开发团队人力可能有限，但社区贡献者活跃，填补了邮件、Telegram等实用功能空白。
- **IronClaw**: **下一代架构试验田**。通过“Reborn”架构激进探索新的交互模式（并发执行、自我进化）。适合追求前沿技术且能容忍不稳定的早期使用者。
- **LobsterAI**: **工作流与插件生态聚焦**。专注于“计划模式”等高级工作流控制，并作为OpenClaw的重要插件项目，在生态内部扮演特定角色。技术债务管理是其关键挑战。
- **CoPaw**: **社区活跃的全能型选手**。功能与生态齐头并进，但被稳定性问题所困扰。其社区讨论非常活跃，用户画像偏向于需要处理大量Agent协作与IoT集成的极客用户。
- **ZeroClaw**: **激进的架构革命者**。旨在通过“非Node.js化、Wasm化”实现极致的轻量、安全与可移植性。是生态中的“异类”，其发展进程值得所有开发者关注。

### 6. 社区热度与成熟度

| 层次 | 项目 | 特征 |
| :--- | :--- | :--- |
| **第一梯队 (生态级热度)** | **OpenClaw** | 无与伦比的Issue/PR数量，已形成围绕自身的庞大插件生态，其决策影响生态内其他项目。 |
| **第二梯队 (核心关注级)** | **IronClaw, ZeroClaw** | 虽绝对数量不及OpenClaw，但讨论质量极高（RFC、架构重构），社区聚焦于深层次技术问题，代表了行业的演进方向。 |
| **第三梯队 (局部热点级)** | **Hermes Agent, CoPaw, PicoClaw** | 社区活跃度较高，但讨论焦点相对分散，集中在特定平台（Telegram, Discord）、特定功能（移动端适配）或特定Bug上。 |
| **第四梯队 (小众稳定/边缘化)** | **NanoBot, NanoClaw, LobsterAI, NullClaw** | 活跃度中等或偏低，社区规模较小，但项目（NanoBot）成熟度高，或（NanoClaw）聚焦细分领域。 |
| **第五梯队 (休眠)** | **TinyClaw, Moltis, ZeptoClaw** | 完全无更新，项目似乎已停滞。 |

### 7. 值得关注的趋势信号

1.  **“反脆弱性”成为硬需求**：来自**OpenClaw**（内存泄漏）、**CoPaw**（进程冻结）、**ZeroClaw**（上下文超限）的S级Bug报告，以及**NanoBot**专门发布“耐久性”版本，共同指向一个核心趋势：**用户已无法容忍智能体“崩溃”、“挂起”、“静默失效”**。对于开发者而言，**恢复机制、优雅降级、健康监控** 将成为智能体框架的标准配置，而非加分项。

2.  **存储与API去中心化浪潮起**：**OpenClaw**和**Hermes Agent**社区对PostgreSQL和原生Vertex AI的强诉求，以及**ZeroClaw**彻底抛弃Node.js的激进计划，表明大模型应用正在经历从“便捷API绑定”向“**可持续、低成本、自托管基础设施**”的深刻转变。**开发者应准备好让应用适配多种存储后端，并支持用户选择自己的模型提供商。**

3.  **精细化人机协同模式受追捧**：从**LobsterAI**的“Plan Mode”到**IronClaw**的“每工具自动批准”机制，再到**NanoClaw**的“带理由的拒绝”，社区不再满足于“黑盒”全自动Agent，而是渴望获得 **“在关键节点可审核、可打断、可指导”** 的协作体验。这预示着未来智能体的设计范式将从“完全自主”转向“**可控自主（Controlled Autonomy）**”。

4.  **供应链安全成为零容忍项**：**ZeroClaw**的Wasm签名验证、**PicoClaw**的安全边界修复，都指向一个共识：**智能体生态的开放性（插件、技能）必须以底层可验证的安全性为前提**。Wasm技术因其良好的沙箱和签名机制，正成为构建安全插件体系的首选方案，这可能成为未来所有智能体框架的标配。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，现根据NanoBot (github.com/HKUDS/nanobot) 2026-06-23的GitHub数据，为您生成以下项目动态日报。

---

# NanoBot 项目动态日报 | 2026-06-23

## 1. 今日速览

今日项目活跃度极高，正式发布了 **v0.2.2** 版本，标志着在**耐久性 (Durability)** 方面取得重大进展。过去24小时内，项目共关闭了13个Pull Request（PR），主要聚焦于**稳定性修复** (特别是Gateway和WebUI) 和**版本发布的准备工作**。社区提交了13个新的PR与6个Issues，展现了强劲的社区贡献动力。值得注意的是，关于为Telegram Bot API 10.1提供富文本消息支持、以及PWA移动端支持的诉求开始浮现，预示着用户对平台集成和体验优化的需求仍在增长。

## 2. 版本发布

### v0.2.2 — 耐久性增强版
- **链接**: [v0.2.2 Release](https://github.com/HKUDS/nanobot/releases/tag/v0.2.2)
- **核心更新**: 本期版本主题是 **“耐久性 (Durability)”**，旨在让Agent在各种现实场景中表现得更稳健。关键改进包括：
    - **WebUI对话韧性**：WebUI的对话记录被分割存储，不再依赖单个脆弱文件，提升了数据安全性。
    - **分叉对话可靠性**：修复了在分叉（Fork）对话后，助手回复可能丢失的竞态条件问题 (PR #4455)。
    - **网关稳定性**：修复了前台网关在收到中断信号时可能无法正常退出的问题 (PR #4454)。同时，后台守护进程（Daemon）模式在状态管理、launchd集成方面也得到加强 (PR #4447)。
- **破坏性变更**: 从发布说明和无重大API变更的PR来看，`v0.2.2` 主要聚焦于内部架构优化和Bug修复，**预计没有破坏性变更**。
- **迁移注意事项**: 建议用户更新至该版本以获取更稳定的体验。由于涉及内部存储结构的变更，升级后首次启动可能需要一些时间进行数据迁移。

## 3. 项目进展

过去24小时，项目在**稳定性**和**可维护性**上取得了显著进展：

- **网关（Gateway）生命周期优化**：PR #4447、#4454、#4456 共同解决了网关启动、停止过程中的多个边界情况和并发问题，包括处理已取消的任务和后台进程状态记录。这使得NanoBot作为后台服务运行更加可靠。
- **WebUI 交互修复**：
    - **PR #4453**: 修复了发送消息后，WebUI滚动行为异常的问题，确保流式输出时能跟随最新内容。
    - **PR #4455**: 解决了分叉（Fork）对话在历史刷新后，助手回复会意外消失的Bug，这是提升用户交互体验的关键修复。
- **MCP 工具管理加固**：
    - **PR #4436** 和 **#4452**: 强制将`enabledTools`白名单逻辑应用于MCP服务器的所有可调用能力（资源、提示词），修复了资源泄露的安全隐患，并使得`enabledTools: []`能实现真正的“拒绝所有”。
- **流式响应健壮性**：PR #4443 修复了流式响应中可能出现的重复`tool_use` ID问题，避免了会话因“400”错误而永久性损坏。

## 4. 社区热点

- **PR #4412 `[CLOSED]`**: **[enhancement, webui] Suppress routine cron job notifications** - 此PR以较高关注度解决了用户痛点：升级后，即使LLM回复“无事可报”，所有绑定的Cron任务都会发送通知。该PR已合入`v0.2.2`版本，社区对此修复反响积极。
    - 链接: [PR #4412](https://github.com/HKUDS/nanobot/pull/4412)
- **Issue #4413 `[OPEN]`**: **Request for Telegram Bot API 10.1 rich messages** - 用户请求支持Telegram Bot新API的富文本消息格式。这表明社区希望NanoBot能跟上主流平台的最新特性，以提供更丰富的交互体验。
    - 链接: [Issue #4413](https://github.com/HKUDS/nanobot/issues/4413)

## 5. Bug 与稳定性

| 严重程度 | 问题描述 | 状态 | 相关链接 |
| :--- | :--- | :--- | :--- |
| **高** | **升级后，即使要求“不要发送”，Cron任务仍会发送所有LLM响应 (Regression)** | **已修复** (v0.2.2) | [Issue #4410](https://github.com/HKUDS/nanobot/issues/4410), [PR #4412](https://github.com/HKUDS/nanobot/pull/4412) |
| **中** | **MCP服务器重连时，网关会因`RuntimeError`崩溃** | 已有Fix PR (#4441) | [PR #4441](https://github.com/HKUDS/nanobot/pull/4441) |
| **中** | **流式响应中重复的`tool_use` ID会导致会话永久性损坏** | 已有Fix PR (#4443) | [PR #4443](https://github.com/HKUDS/nanobot/pull/4443) |
| **低** | **配对存储中，Sender ID类型转换不一致，可能静默拒绝已有活跃配对的用户** | 已有Fix PR (#4433) | [PR #4433](https://github.com/HKUDS/nanobot/pull/4433) |

## 6. 功能请求与路线图信号

- **高优先级信号**:
    - **Kimi编程版 (Kimi Coding Plan) 支持**: Issue #4463 和 PR #4464 非常新，表明用户对集成Kimi推出的付费“编程版”服务有强烈需求。考虑到NanoBot与Kimi的合作关系，此功能纳入下一版本的可能性**非常高**。
- **中优先级信号**:
    - **Telegram富文本消息**: Issue #4413 反映了用户对平台原生能力集成的期待。这通常被视作“锦上添花”特性，但鉴于用户呼声，很有可能被列入待办。
- **低优先级信号**:
    - **PWA移动端支持**: Issue #4457 和 PR #4458 提出增加PWA支持，让WebUI拥有类似原生App的体验。这有助于提升移动端用户的粘性，但可能不是当前开发团队的首要任务。

## 7. 用户反馈摘要

从Issue评论中可提炼出以下真实用户反馈：

- **升级痛点**: 用户 `KennethYCK` 报告了从v0.15升级后，Cron任务行为发生意料之外的改变 (Issue #4410)。这是一种典型的回归问题，社区及时跟进并迅速修复，体现了项目的积极反馈闭环。
- **新手入门门槛**: 用户在 Issue #4376 中提出，当前的`nanobot onboard --wizard`向导对非技术用户不友好，需要过多技术细节知识。用户期望一个更“傻瓜式”的配置体验。
- **平台集成诉求**: 用户 `madIlama` 在 Issue #4413 中分析并请求支持Telegram Bot API 10.1的富文本消息，表明用户不仅满足于基本的文本收发，而是追求更接近原生客户端的功能体验。

## 8. 待处理积压

- **PR #4397 `[OPEN]`**: [fix(runner): insert user-attention hint before mid-turn user messages](https://github.com/HKUDS/nanobot/pull/4397)
    - **状态**: 已开放5天，由社区贡献者 `DreamShepherd2006` 提交。该PR旨在解决用户打断LLM工具执行时，LLM可能忽略用户新消息的问题。
    - **分析**: 这是一个有价值的交互改进。目前没有评论或负面标签，可能需要维护者进行功能评估和Code Review。建议维护者尽快回应，避免打击社区贡献者的积极性。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

好的，这是根据您提供的 Hermes Agent GitHub 数据生成的 2026-06-23 项目动态日报。

---

# Hermes Agent 项目日报 — 2026-06-23

## 1. 今日速览

今日项目活跃度**极高**，24小时内产生了100条 Issue 和 PR 更新，社区参与度旺盛。核心动向是 **“稳定性修复与平台适配攻坚”**：一方面，大量 Pull Request 聚焦于修复因编码、配置、平台差异（Windows/macOS/Linux）导致的系统性 Bug，项目正在经历一轮精细化的代码质量提升；另一方面，社区对 **原生 Google Cloud Vertex AI 提供商** 和 **跨平台兼容性** 的呼声非常高，成为今日最热议题。尽管存在大量待合并 PR，但项目整体健康度良好，维护者响应积极。

## 2. 版本发布

*今日无新版本发布。*

## 3. 项目进展

今日无重大 PR 被合并，但有6个 PR 已被合并或关闭，显示部分问题已得到解决。以下是一些值得关注的进展（已关闭/合并）：

- **PR #50495 (已合并)**：[Support prompt summaries in skills index](https://github.com/nousresearch/hermes-agent/pull/50495)
  - **摘要**：为技能索引添加了 `prompt_summary` 元数据字段，允许更精确的提示路由文本，同时保持了向后兼容性。这是对智能体技能系统的一次精细优化。
- **PR #31923 (已关闭)**：[fix(gateway): detect scoped-lock PID reuse on macOS](https://github.com/nousresearch/hermes-agent/pull/31923)
  - **摘要**：修复了 macOS 上因 PID 重用导致网关适配器被锁文件永久阻塞的 bug。这是一个重要的稳定性修复，解决了 macOS 用户在长时间运行后可能遇到的网关假死问题。
- **Issue #27912 (已关闭)**：[Add Telegram passive history mode](https://github.com/nousresearch/hermes-agent/issues/27912)
  - **摘要**：Telegram 被动历史模式功能已在 `main` 分支实现并关闭，未来版本将支持机器人在群组中只响应唤醒词，而非所有消息。

## 4. 社区热点

今日社区讨论最热烈的议题主要集中在两个方向：

1. **呼声最高的需求：原生 Google Cloud Vertex AI 支持**
   - **Issue #12639**：[Support for Native Google / Vertex AI Provider](https://github.com/nousresearch/hermes-agent/issues/12639) (11条评论，10👍)
   - **Issue #13484**：[Feature: native Google Cloud Vertex AI provider support](https://github.com/nousresearch/hermes-agent/issues/13484) (8条评论，12👍)
   - **分析**：用户强烈希望摆脱对 OpenRouter 的依赖，直接接入 Google Cloud Vertex AI，以解决 402 计费错误和速率限制问题。这反映了社区对成本控制和直接接入主要云服务的强烈需求，是项目路线图中的重要信号。

2. **最具破坏性的 Bug：桌面构建反复失败**
   - **Issue #47917**：[Desktop build fails after update - electronDist does not exist](https://github.com/nousresearch/hermes-agent/issues/47917) (22条评论，2👍)
   - **分析**：这是今日评论最多的 Issue。问题在于更新后 Electron 二进制缓存被删除导致构建失败。用户尝试了修复方法但问题反复出现，引发了社区的广泛讨论和一定程度的挫败感。这已成为影响开发者和早期用户使用的关键障碍。

## 5. Bug 与稳定性

今日报告的 Bug 数量众多，按严重程度排列如下：

**P1 (严重) - 关键功能受阻或数据丢失风险：**
- **Issue #47917**：[Desktop build fails after update](https://github.com/nousresearch/hermes-agent/issues/47917) - 构建系统反复失败，影响桌面端开发与测试。
- **Issue #30636**：[state.db corruption from SIGTERM under high load](https://github.com/nousresearch/hermes-agent/issues/30636) - 高负载下进程终止导致 `state.db` 损坏，有数据丢失风险。
- **Issue #48648**：[Telegram streamed message duplication loop](https://github.com/nousresearch/hermes-agent/issues/48648) - Telegram 流式消息在超长时出现无限重复，严重影响用户体验。
- **Issue #24100**：[Discord command approval routes to wrong thread](https://github.com/nousresearch/hermes-agent/issues/24100) - 命令审批路由错误，存在潜在安全风险。
- **Issue #41289**：[Discord /model command blocks event loop](https://github.com/nousresearch/hermes-agent/issues/41289) - Discord 事件循环被阻塞，导致服务无响应。
- **Issue #51057**：[Discord single message dispatched twice](https://github.com/nousresearch/hermes-agent/issues/51057) - 消息被重复处理，导致用户收到双倍回复 (v0.17.0 回归)。

**P2 (中等) - 功能受影响或有更好的替代方案：**
- **Issue #30230**：[Gateway hits macOS fd limit (256)](https://github.com/nousresearch/hermes-agent/issues/30230) - macOS 文件描述符限制导致网关崩溃。
- **Issue #30594**：[`hermes update` fails with PEP 668](https://github.com/nousresearch/hermes-agent/issues/30594) - 系统 Python 环境更新失败，影响 Debian/Ubuntu 用户。
- **Issue #50765**：[ACP session/prompt hangs on Windows](https://github.com/nousresearch/hermes-agent/issues/50765) - Windows 上 ACP 服务挂起 (v0.17.0 回归)。
- **Issue #42727**：[Agent-led self-configuration corrupts redacted credentials](https://github.com/nousresearch/hermes-agent/issues/42727) - 智能体自我配置能持久化被修改的凭证，可能导致连接中断。
- **Issue #51155**：[Personalities don't change](https://github.com/nousresearch/hermes-agent/issues/51155) - 个性设置无法持久化或生效。
- **Issue #51089**：[Session resume can lose state](https://github.com/nousresearch/hermes-agent/issues/51089) - 会话恢复可能丢失中间状态。

**P3 (较低) - 小问题或非核心功能：**
- **Issue #37505**：[macOS DMG is arm64-only](https://github.com/nousresearch/hermes-agent/issues/37505) - 安装包不兼容 Intel Mac。
- **Issue #26083**：[Microsoft Teams plugin fails on Python 3.11](https://github.com/nousresearch/hermes-agent/issues/26083) - Teams 插件因 Python 版本依赖问题无法加载。
- **Issue #50547**：[Kanban plugin uses native browser dialogs](https://github.com/nousresearch/hermes-agent/issues/50547) - 看板插件使用了浏览器原生弹窗而非应用内组件。
- **Issue #51099**：[Honcho memory provider activates even when dependency missing](https://github.com/nousresearch/hermes-agent/issues/51099) - 依赖缺失时仍显示激活成功，造成混淆。

**已有修复 PR 的关键 Bug：**
- Issue #50618 (`/indicator` mac 不工作) -> PR #51178 ([已提交](https://github.com/nousresearch/hermes-agent/pull/51178))
- 多个 `read_text/write_text` 编码问题 -> PR #51179, #51172, #51177 ([已提交](https://github.com/nousresearch/hermes-agent/pull/51179))

## 6. 功能请求与路线图信号

除了上述热点 `Vertex AI` 支持外，今日还有以下值得关注的功能请求：

- **WhatsApp 消息模板支持** [#45935](https://github.com/nousresearch/hermes-agent/issues/45935)：用于在24小时窗口外重新触达用户，是生产环境中的真实需求。
- **字体选择器** [#37566](https://github.com/nousresearch/hermes-agent/issues/37566)：桌面端的个性化定制需求。
- **支持 `.mcp.json` 项目配置文件** [#51069](https://github.com/nousresearch/hermes-agent/issues/51069)：方便开发者使用已有的 MCP 服务器配置。
- **GLM-5 推理支持** [#50696](https://github.com/nousresearch/hermes-agent/issues/50696)：扩展对智谱 GLM-5 系列模型的支持。
- **Windows `computer_use` 工具支持** [#41044 (已关闭)](https://github.com/nousresearch/hermes-agent/issues/41044)：社区呼声高，但今日无明确 PR 进展，该功能需求仍处于提议阶段。
- **`IdentitiesOnly` 支持 (SSH)** [#51145 (已提交)](https://github.com/nousresearch/hermes-agent/pull/51145)：针对特定 SSH 主机认证问题的功能增强，已有 PR 提交，很可能被纳入下一个版本。

## 7. 用户反馈摘要

从今日的 Issue 评论中，可以提炼出以下真实用户痛点和使用场景：

- **“我被 OpenRouter 的计费和限速搞得很烦，只是想正常使用我自己的 Google 模型。”** — 这是多个用户的核心心声，他们希望 Hermes 能直接连接到 Vertex AI，而不是通过第三方代理来承担额外的风险和成本。
- **“每次更新桌面端都要重新构建，然后构建就失败，这太令人沮丧了。”** — 用户 `wordgao` (#47917) 的经历代表了一类开发者的挫折感，复杂的构建流程和缓存失效问题正在消耗他们的耐心。
- **“我在 Intel Mac 上装了应用，它直接崩溃了，只支持 arm64 让我很失望。”** — 用户 `JE4NVRG` (#37505) 指出了发布流程中的一个明显的兼容性盲区。
- **“我在一个 Telegram 大群组里使用机器人，它对我发的每一条消息都回复，这很烦人。我只需要它在听到特定词时才回应。”** — 用户 `fserg` (#27912) 清晰地描述了需要“被动监听”模式的真实场景。
- **“Honcho 内存提供商在缺少依赖时显示激活成功，这花了我们几个小时来调试。”** — 用户 `carstenflokstra` (#51099) 指出了错误反馈机制的重要性。一个误导性的成功消息比一个清晰的错误提示更具破坏性。

## 8. 待处理积压

以下是一些长期未响应或对项目影响重大，但今日未获得充分关注的 Issue/PR，提醒维护者关注：

- **PR #12769**：[feat(dingtalk): proactive messaging, media pipeline, card throttle](https://github.com/nousresearch/hermes-agent/pull/12769) (已存在超2个月，0评论)
  - **说明**：这是一个为钉钉平台适配器添加大量生产级功能的 PR，但从4月20日创建至今仍未合并，也无人评论。考虑到其代码量和工作量，可能需要维护者的评审和反馈。
- **PR #30179**：[feat(egress): iron-proxy credential-injection firewall for sandboxes](https://github.com/nousresearch/hermes-agent/pull/30179) (已存在1个月，0评论)
  - **说明**：这是一个重要的安全特性，为沙箱提供了凭证防火墙，防止凭证泄露。如此关键的 PR 无人评议，应引起重视。
- **Issue #12639 & #13484** (Vertex AI 支持)：虽然今天讨论热度高，但这两个 Issue 已存在2个多月。社区的需求信号已经非常强烈，**强烈建议项目团队明确表态并规划路线图**，以减少社区的不确定性。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，我将根据您提供的PicoClaw项目数据，生成一份结构化的项目动态日报。

---

### **PicoClaw 项目动态日报 | 2026年6月23日**

**项目名称:** PicoClaw (github.com/sipeed/picoclaw)
**报告生成时间:** 2026-06-23

---

#### **1. 今日速览**

今日项目活跃度较高，有**19条**新Pull Request（PR）的更新，尽管新发布的版本数为0。项目维护者处理了大量由自动化工具（如 dependabot）和社区贡献者提交的合并请求，并在WhatsApp集成、安全边界和跨站点请求防御等关键领域修复了错误。同时，社区在功能请求和Bug报告方面也保持了活跃。总体来看，项目处于**积极迭代和维护状态**，代码质量与安全性是今日关注重点。

#### **2. 版本发布**

*无新版本发布。*

#### **3. 项目进展**

今日项目向前迈进了坚实的一步，共**合并/关闭了7项**PR，其中包含多个重要修复。主要进展包括：

- **WhatsApp集成稳定性提升 (PR #3162)**: 已合并 `fix(whatsapp): add reconnection and async message processing`。该修复通过支持异步消息处理、添加心跳响应处理程序、读超时和带指数退避的自动重连，解决了WhatsApp WebSocket连接自动断开的问题。这显著提升了PicoClaw在WhatsApp渠道上的可靠性和用户体验。
- **Spawn异步回调优化 (PR #3155)**: 已合并 `feat(spawn): add direct_reply parameter with SkipInboundTurn support`。此功能解决了Spawn工具产生重复消息的问题，通过引入`direct_reply`参数和`SkipInboundTurn`机制，开发者可以更精细地控制回调行为，是架构层面的优化。
- **公开搜索功能增强 (PR #3152)**: 已合并 `add installation instructions to picoclaw skills search.`。现在在通过搜索功能查找技能时，输出结果会附带安装指引，提升了功能的实用性和新手友好度。
- **稳定性修复**: 解决了 `openai_compat` 提供者中关于 `native_search` 类型断言的潜在bug (PR #3091) 和 `evolution` 存储模块中的并发问题 (PR #3053)，消除了潜在的panic风险。
- **依赖更新**: 合并了几个dependabot提交的依赖更新，包括Vite (PR #3101) 和 ESLint (PR #3105)，确保了前端构建工具的稳定性。

#### **4. 社区热点**

- **`[Feature] I need SimpleX or tox` (Issue #3093)**
  - **链接**: [sipeed/picoclaw Issue #3093](https://github.com/sipeed/picoclaw/issues/3093)
  - **热度**: 获得了3条评论和1个👍。
  - **分析**: 用户强烈希望PicoClaw能够支持 **SimpleX** 或 **Tox** 等更注重隐私和去中心化的通信协议。这表明社区中存在对超越当前主流渠道（如WhatsApp、Web UI）的更安全和自定义通信方式的需求。这是一个明确的**功能请求信号**。

- **`[BUG] 经常重复任务` (Issue #3159)**
  - **链接**: [sipeed/picoclaw Issue #3159](https://github.com/sipeed/picoclaw/issues/3159)
  - **热度**: 今日新开，暂无评论。
  - **分析**: 用户报告了一个非常具体的复现步骤：在询问“今日美国新闻”后再询问“今日法国新闻”时，AI会再次执行美国新闻的任务。这表明可能存在**上下文管理或任务执行逻辑的Bug**，导致历史会话状态未能被正确清理或忽略。

#### **5. Bug 与稳定性**

今日报告的Bug按严重程度排列如下：

- **高:**
    - **`[BUG] 经常重复任务` (Issue #3159)**: 严重影响用户体验，可能导致Token浪费和响应延迟。**暂无修复PR**。
    - **`[BUG] Volcengine Doubao Seed tool calls occasionally leak as <seed:tool_call> text` (Issue #3153)**: 工具调用结果以原始XML形式泄露给用户，而非被正确执行。这是一个严重的功能性Bug。**已有修复PR #3154** 正在处理中。

- **中:**
    - **(PR #3160) 跨站脚本防御增强**: 虽然新提交的PR主要是修复，但它指出了原系统在处理launcher密码设置请求时缺乏跨站点请求验证，这是一个潜在的安全问题。修复已通过 **PR #3160** 提交。

- **低/稳定性:**
    - **`exec`命令安全边界修复 (PR #3161)**: 修复了自定义允许规则可能意外绕过全局拒绝模式的问题，属于安全强化。
    - **沙箱文件系统路径处理修复 (PR #3158)**: 为Windows环境下的沙箱文件系统路径处理增加了回归测试，防止了潜在的跨平台兼容问题。

#### **6. 功能请求与路线图信号**

- **新的通信渠道**: 用户要求支持 **SimpleX / Tox** 等隐私协议 (Issue #3093)。这是一个明确的、面向小众但有强需求用户群体的功能请求。
- **Android ADB远程操控 (PR #3157)**: 社区贡献者提交了名为 `feat: add Android ADB remote operations tool` 的**待合并PR**。该PR为PicoClaw添加了通过ADB操控安卓设备的能力，如屏幕截图、UI层级获取、点击滑动等。这说明项目正在向**设备自动化**和**移动端Agent**方向拓展，这是一个值得关注的路线图信号。
- **远程Pico WebSocket模式 (PR #3118)**: 另一项**待合并PR** 提出了为PicoClaw Agent添加远程WebSocket模式的功能，允许Agent连接到远程服务。这暗示了**分布式Agent**或**中心化Agent管理**的潜在方向。
- **Token用量跟踪 (PR #3156)**: **待合并PR** 提议在Pico通道上发送每轮对话的LLM Token用量。这是对**成本控制和监控**需求的响应，对于高级用户和企业级应用至关重要。

综合来看，**Android ADB集成 (PR #3157)** 和 **远程Agent模式 (PR #3118)** 是两个最有可能被纳入下一版本的重要功能，代表了项目的扩展方向。

#### **7. 用户反馈摘要**

- **重复任务问题 (Issue #3159)**: “给ai提问今天的美国新闻，然后再提问今天的法国新闻，在第二次回答中会再做一次美国新闻的任务才做法国新闻的。” 这反映了用户对**任务执行效率**和**上下文准确性**的深切不满，表明当前的对话逻辑存在缺陷。
- **工具调用泄漏 (Issue #3153)**: “tool calls are sometimes returned to the user as raw `<seed:tool_call>` text” 用户反馈工具调用以原始字符串形式泄露，而不是被系统执行。这暴露了与特定模型（豆包）的兼容性**或**模型响应解析逻辑的问题，影响功能的完整性和可靠性。
- **SimpleX/Tox支持请求 (Issue #3093)**: 用户简洁地表达了“I need gateway SimpleX or Wire or Tox”。这种风格的请求通常意味着用户有强烈的**特定场景需求**（如强隐私、抗审查），并且当前没有可替代的解决方案。

#### **8. 待处理积压**

- **依赖更新积压**: 以下由dependabot创建的PR已保持开放超过10天，建议维护者关注并合并，以避免潜在的安全风险或兼容性问题：
    - `build(deps): bump shadcn from 4.7.0 to 4.11.0` (PR #3104)
    - `build(deps-dev): bump @vitejs/plugin-react from 6.0.1 to 6.0.2` (PR #3100)
    - `build(deps-dev): bump typescript-eslint from 8.59.3 to 8.62.0` (PR #3103)

- **重要功能/修复待合并**:
    - `feat: add Android ADB remote operations tool` (PR #3157) - 有价值的扩展功能，等待评估与合并。
    - `Add remote Pico WebSocket mode to picoclaw agent` (PR #3118) - 具有潜力的新特性，但可能需要更深入的架构讨论。
    - `fix(openai_compat): recover Doubao Seed tool calls leaked as <seed:to…` (PR #3154) - 针对一个活跃Bug的修复，应优先处理。

- **长期未响应Issue**:
    - 关于支持 **SimpleX/Tox** 的 **Issue #3093**（已开放13天，3条评论）是社区呼声较高的功能请求，建议维护者给予正式回应，说明是否在路线图中或给出拒绝理由。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

好的，这是为您生成的 NanoClaw 项目动态日报。

---

# NanoClaw 项目动态日报 | 2026-06-23

## 1. 今日速览

今日项目整体活跃度**中等**，未见新的 Issue 提交或版本发布。核心动态集中在 Pull Request (PR) 的提交与合并上，共有5个 PR 处于活动状态。其中，一个重要的 **Telegram 集成功能已经被合并**，标志着项目在多渠道 Agent 交互能力上迈出了坚实一步。此外，社区贡献者持续发力，带来了**邮件集成、审批流程优化**等多项新特性提案，项目生态呈现积极发展态势。

## 2. 版本发布

*无*

## 3. 项目进展

今日项目有1个 PR 被合并，4个 PR 仍处于开放待审状态。

### 已合并/关闭
- **[PR #2831] feat: add Telegram integration (verified working on v2.1.1)**
  - **链接**: [nanocoai/nanoclaw PR #2831](https://github.com/nanocoai/nanoclaw/pull/2831)
  - **概要**: 由社区贡献者 `aarchh` 提交的 Telegram 集成功能。该 PR 通过了验证，能够在 v2.1.1 版本上正常工作，为 NanoClaw 增加了一个全新的通信渠道。
  - **影响**: 这意味着用户现在可以通过 Telegram Bot 与 NanoClaw Agent 进行交互，显著扩展了项目在即时通讯工具中的应用场景。这是社区对项目功能集的重要补充。

## 4. 社区热点

今日最受关注的 PR 均为社区贡献，显示了社区对“扩展 Agent 能力边界”的强烈兴趣。

1.  **IMAP/SMTP 邮件集成**
    - **PR**: #1235 [OPEN]
    - **作者**: `aronjanosch`
    - **链接**: [nanocoai/nanoclaw PR #1235](https://github.com/nanocoai/nanoclaw/pull/1235)
    - **分析**: 该项目试图将 NanoClaw 打造成一个可以自主处理电子邮件的 Agent。它不仅仅是简单地收发邮件，而是将其整合为 Agent 的“渠道”和“工具集”，允许 Agent 被动接收邮件作为输入，或主动阅读、撰写、管理邮件。这背后反映了用户希望 Agent 能深度融入工作流、处理复杂办公任务的诉求。尽管长期未更新，但其功能设计理念具有前瞻性。

2.  **CLI 仪表盘技能**
    - **PR**: #2795 [OPEN]
    - **作者**: `leetwito`
    - **链接**: [nanocoai/nanoclaw PR #2795](https://github.com/nanocoai/nanoclaw/pull/2795)
    - **分析**: 该项目旨在通过解析命令行界面（CLI）的输出，创建一个只读的仪表盘技能。这表明社区用户不仅满足于通过 API 集成，还希望 Agent 能够理解并利用传统的、非结构化的命令行工具输出，拓展 Agent 的信息感知能力。

## 5. Bug 与稳定性

今日无新的 Bug 报告。但有一个重要的稳定性修复 PR 正在审查中：

- **[PR #2830] fix(setup): reap dead peer service registrations whose binary is gone**
  - **严重程度**: **高** - 直接影响系统长期运行的稳定性和资源消耗。
  - **作者**: `amit-shafnir`
  - **链接**: [nanocoai/nanoclaw PR #2830](https://github.com/nanocoai/nanoclaw/pull/2830)
  - **说明**: 该修复解决了因未运行卸载程序就删除项目目录而导致的“僵尸”系统服务问题（如macOS的`launchd` plist）。这些残留服务会不断尝试启动不存在的二进制文件，导致资源浪费和系统污染。此 PR 旨在服务启动时自动清理这些无效注册。这是对项目安装/卸载机制健壮性的重要改进。

## 6. 功能请求与路线图信号

从今日的 PR 可以清晰地看到项目未来功能演进的几个方向：

1.  **多渠道集成**: 继 Telegram 被合并，IMAP/SMTP 邮件、CLI 等新的“渠道”和“技能”被提出，表明项目正在向一个全能的、多模态交互的 Agent 平台发展。
2.  **审批与协作流程优化**: [PR #2832](https://github.com/nanocoai/nanoclaw/pull/2832) “reject with reason” 是一个值得关注的信号。该功能允许人工审批者在拒绝 Agent 的操作请求时附带理由，Agent 再根据反馈进行调整。这反映了用户对 **Agent 与人类更精细、更智能的协作模式** 的需求，而不仅仅是简单的“通过/拒绝”。此功能很可能被纳入下一版本的审批框架改进中。

## 7. 用户反馈摘要

今日无新的 Issue 或评论产生。但从已提交的 PR 可以间接看出用户对项目的满意度较高，社区贡献者愿意投入精力进行功能开发和 Bug 修复，显示了良好的社区生态。

## 8. 待处理积压

- **[PR #1235] feat: add IMAP/SMTP email integration**
  - **状态**: 创建于 3 个多月前，最后一次更新距今超过1天。
  - **链接**: [nanocoai/nanoclaw PR #1235](https://github.com/nanocoai/nanoclaw/pull/1235)
  - **问题**: 这是一个功能量级较大、设计相对完善的 PR，但长期处于无人评论和审查的状态。考虑到其功能的价值，以及与近期合并的 Telegram 集成的高度互补性（邮件是异步通信，Telegram 是即时通信），建议项目维护者关注该 PR，评估其与当前代码库的兼容性并给予反馈。
  - **提醒**: 长期积压的高质量 PR 可能会打击贡献者的积极性，请维护团队予以重视。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，这是根据您提供的NullClaw (github.com/nullclaw/nullclaw) 数据生成的2026年6月23日项目动态日报。

---

# NullClaw 项目动态日报 | 2026-06-23

## 今日速览

项目今日处于低活跃度状态，社区贡献主要围绕依赖维护和一个关键功能修复展开。过去24小时内无新Issue或版本发布，但有2个待合并的Pull Request（PR），其中一项目前处于打开状态的PR针对Matrix协议的持久化状态同步问题提出了修复方案，另一项则是Docker基础镜像的自动化版本升级。整体上看，项目核心开发节奏有所放缓，但社区对稳定性和基础设施维护的关注度较高。

## 版本发布

无

## 项目进展

今日无已合并或关闭的PR。项目进展主要体现在以下两个待处理的PR上，它们代表了项目在稳定性与基础设施两个方向上的推进：
1.  **[#968] fix(matrix): persist next_batch across restart + test env isolation**：由社区贡献者 `addadi` 提交，旨在解决Matrix通道在服务重启后因RAM中同步光标丢失而触发全量初始同步的问题。该PR通过持久化`sync cursor`，可显著缩短重启后的同步时间并降低服务器负载。此修复体现了社区对运行时稳定性的关注。
2.  **[#956] ci(deps): bump alpine from 3.23 to 3.24 in the docker-images group**：由 `dependabot[bot]` 自动提交的依赖更新PR，将Docker基础镜像从Alpine 3.23升级至3.24。此举旨在引入最新的安全补丁和性能改进，是持续维护基础设施健壮性的体现。

## 社区热点

社区讨论热度最高的为 **PR #968**。该PR虽评论数为空，但作为过去24小时内唯一涉及功能修复的贡献，且由社区作者主动提交，其背后的核心诉求非常明确：**解决生产环境中Matrix同步状态的可靠性和效率问题**。用户在运行NullClaw时，因服务重启导致需要全量同步Matrix历史，这在高频使用场景下会消耗大量时间和资源。此PR正是直接响应了这一痛点。

-   **链接**: [nullclaw/nullclaw PR #968](https://github.com/nullclaw/nullclaw/pull/968)

## Bug 与稳定性

当前暂无新报告的Bug。待处理的稳定性相关PR为 **#968**，该PR直接修复了一个潜在的稳定性问题：由于`next_batch`未持久化导致的重启后发生不必要的全量同步，严重程度可归类为**中等**。该问题虽不导致服务崩溃，但会影响用户体验和资源效率。该修复目前已有PR，但尚未合并。

-   **链接**: [nullclaw/nullclaw PR #968](https://github.com/nullclaw/nullclaw/pull/968)

## 功能请求与路线图信号

今日无新增功能请求。从待处理的PR **#968**（持久化sync cursor）和 **#956**（升级基础镜像）可以判断，项目当前处于**稳定性优化和基础设施维护**阶段。下一版本的重点可能并非引入新功能，而是修复已知的可靠性问题并跟上依赖的最新安全标准。

## 用户反馈摘要

通过分析PR描述，可以提炼出一条关键的间接用户反馈：
-   **痛点场景**: 用户在运行Matrix通道服务时遭遇重启（可能是计划内计划外），随即发现服务花费了异常长的时间重新进行初始同步，影响了消息处理流程的连续性。
-   **诉求**: 用户（或贡献者）期望服务具备从上次中断点恢复的能力，避免重复处理全量历史数据。
-   **满意/不满意**: 不满意点在于当前“光标仅存在RAM中”的设计；满意点在于社区已有人（`addadi`）直接提交了修复方案。

## 待处理积压

以下两项待合并的PR需要维护者关注，其中PR #956已开放一周，需确认是否引入兼容性问题；PR #968作为关键功能修复，应优先评审与合并。

1.  **[#956] [dependencies, docker] ci(deps): bump alpine from 3.23 to 3.24**：依赖更新类，开放时长8天，无冲突但需确认版本兼容性。
    -   **链接**: [nullclaw/nullclaw PR #956](https://github.com/nullclaw/nullclaw/pull/956)
2.  **[#968] fix(matrix): persist next_batch across restart + test env isolation**：功能性Bug修复类，开放时长1天，直接提升服务稳定性，建议优先处理。
    -   **链接**: [nullclaw/nullclaw PR #968](https://github.com/nullclaw/nullclaw/pull/968)

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，现根据您提供的 IronClaw 项目数据，为您呈上 2026-06-23 的项目动态日报。

---

## IronClaw 项目动态日报 | 2026-06-23

### 1. 今日速览

项目当前处于 **高强度开发与迭代** 阶段，活跃度极高。过去24小时内，`Reborn` 架构的优化和功能补齐是核心主线，共产生了 15 条 Issue 和 24 个 PR，其中 **12 个新 Issue** 和 **16 个待合并 PR** 表明社区和核心团队正密集地发现并解决问题。性能回归、自动化功能完善、权限模型升级是今日的三大重点。尽管存在 `main` 分支的回归问题（#5139），但团队响应迅速，已有对应修复 PR 在队列中，整体项目健康度良好，处于快速演进期。

### 2. 版本发布

无

### 3. 项目进展

今日项目在多条关键线路上取得显著进展，以下是已合并/关闭的重要 PR：

- **并发与性能提升**: [#5085 feat(reborn): concurrent turn execution via TurnRunScheduler](https://github.com/nearai/ironclaw/pull/5085) 被合并。这是一项重要的性能改进，通过引入 `TurnRunScheduler` 将 `Reborn` 运行时从严格的串行执行改为并发执行，并支持用户/类型级别的并发上限。这将直接影响用户感知到的响应速度，是解决性能问题（#5125）的关键一步。
- **权限模型落地**: [#5063 feat(reborn): per-turn auto-approve resolution + never-auto-approve hard floor](https://github.com/nearai/ironclaw/pull/5063) 被合并。此 PR 解决了“全局自动批准”和“每次询问”的需求，引入了数据库支持的设置存储，并增加了“永不自动批准”的硬性底线。这直接对应并关闭了 #4959 和 #4958 两个重要 Issue，大幅增强了 Reborn 的安全性和灵活性。
- **基础设施与测试**: [#5081 Add hosted single-tenant Postgres profile](https://github.com/nearai/ironclaw/pull/5081) 被合并，为云托管版本做好了准备。同时，[#5136 Add Emulate-backed Gmail OAuth E2E coverage](https://github.com/nearai/ironclaw/pull/5136) 被提交，增强了关键外部服务集成的测试覆盖率，为项目质量提供保障。
- **触发器问题修复**: [#5140 fix(triggers): surface trigger input errors](https://github.com/nearai/ironclaw/pull/5140) 被合并，修复了触发器创建时错误信息不透明的问题，改进了开发者和用户的使用体验。

### 4. 社区热点

今日社区讨论最活跃的议题主要集中在 **“Reborn 回归性能问题”** 和 **“性能优化”** 两个方向。

- **核心回归问题**: **[#5139 reborn regression: web/research tasks hang at init](https://github.com/nearai/ironclaw/issues/5139)**
    - **热度**: 创建于昨日，已获 1 条评论，并在 PinchBench 测试中标记了 21/147 的任务失败。
    - **诉求**: 这是开发团队发现的严重回归问题。`main` 分支的最新提交导致 `web/research` 任务在初始化阶段死锁，造成了零 LLM 调用和零工具调用。用户和开发者迫切需要这个BUG被定位和修复。
- **性能优化专项**: **[#5125 [Reborn] IronClaw Performance Issues 06/22/2026 - 06/28/2026](https://github.com/nearai/ironclaw/issues/5125)**
    - **热度**: 这是一个系列性能问题的父 Issue，下属三个子 Issue（#5126, #5127, #5128）均已创建，但尚无评论。
    - **诉求**: 用户和开发者在本地 `dogfooding` 过程中普遍感受到了卡顿。此 Issue 旨在系统性地追踪并解决 Reborn 的性能问题，核心诉求是“让 IronClaw Reborn 感觉更快”，并提出了从延迟日志、推理调优到减少冗余步骤等多个子方向。

### 5. Bug 与稳定性

- **严重 - 回归性BUG**: **[#5139 reborn regression: web/research tasks hang at init](https://github.com/nearai/ironclaw/issues/5139)**
    - **描述**: 因 `main` 分支提交更新，导致 `reborn` 在初始化时卡死，无法进行任何 LLM 调用。直接影响每日 PinchBench 测试结果。
    - **状态**: 仍未关闭，正在活跃排查中。当前无直接修复 PR，但已作为高优先级被社区关注。

- **中等 - 功能异常**: **[#5129 [Reborn] Investigate Always approve not working for outbound_delivery_target_set](https://github.com/nearai/ironclaw/issues/5129)**
    - **描述**: 报告显示“总是允许”功能对特定能力 `outbound_delivery_target_set` 失效。此为 #5063 PR 合并后的潜在副作用。
    - **状态**: 仍为开启状态，需要复现和进一步调查。

- **低 - 持续失败**: **[#4108 Nightly E2E failed](https://github.com/nearai/ironclaw/issues/4108)**
    - **描述**: 夜间 E2E 测试持续失败，可能与 `main` 分支的回归有关。
    - **状态**: 已存在近一个月，需关注是否与 #5139 关联。

### 6. 功能请求与路线图信号

今日提出的新功能请求与路线图高度契合，反映出 Reborn 架构正快速覆盖 V1 版本的所有功能并加以改进。

- **渠道扩展**: **[#5124 Support Telegram channel for IronClaw Reborn](https://github.com/nearai/ironclaw/issues/5124)**
    - **信号**: 用户明确希望将 Telegram 作为 Reborn 的新渠道。这表明项目正在按计划向多平台 AI Agent 演进。
- **自动化管理**: **[#5122 Add Reborn automation delete support](https://github.com/nearai/ironclaw/issues/5122)** 和 **[#5121 Add Reborn automation pause/resume support](https://github.com/nearai/ironclaw/issues/5121)**
    - **信号**: 自动化系统的增删改查是基础功能。这两个功能的提出，并结合对应的PR（#5131, #5133），说明 Reborn 的自动化子系统正在快速成熟。
- **自我进化能力**: **[#5061 feat(reborn): skill extraction & self-evolution with activation controls](https://github.com/nearai/ironclaw/pull/5061)**
    - **信号**: 尽管此 PR 仍为开启状态，但其“技能提取与自我进化”的概念非常前沿，表明项目正在探索 AI Agent 的自主学习和适应性能力，这可能是未来版本的重要卖点。

### 7. 用户反馈摘要

从本日的数据来看，用户（主要是内部开发者和贡献者）的反馈集中在以下几点：

- **痛苦点**: **本地开发体验的卡顿感** 是当前最核心的痛点。虽然性能改进 PR（#5085）已合并，但其效果尚未体现到用户端。用户急切需要通过日志和归因来明确慢在哪里（#5126）。
- **使用场景**: 开发者正在通过 **本地 Dogfooding** 来发现 WebUI、配置、模型设置等首次使用时的不便（#4879）。同时，**自动化** 和 **权限控制** 是开发者日常测试和构建应用场景中的重点。
- **满意度**: 对于 **全局自动批准**（#4959）和 **每工具权限模型**（#4958）的最终落地，可以推测用户是满意的，因为这些功能直接解决了“每次确认繁琐”和“安全顾虑”之间的矛盾。另外，对 `Google WSM` 工具返回更友好错误信息（#4969）的修复，也改善了集成开发体验。

### 8. 待处理积压

- **长期未响应的重要PR**:
    - **[#4032 build(deps): bump the wasm group across 1 directory with 2 updates](https://github.com/nearai/ironclaw/pull/4032)**: 一个依赖更新 PR，已经开放 29 天，仍未被合并。持续积压的依赖更新可能会引入安全风险或导致与其他新代码不兼容，建议维护者尽快处理。
    - **[#5061 [NO MERGE] - Barcelona Hackathon](https://github.com/nearai/ironclaw/pull/4787)**: 由常规贡献者创建，用于支持特定活动的分支，但标记为“禁止合并”。随着时间推移，此分支与 `main` 的差异可能越来越大，建议团队评估其后续安排。

- **长期未响应的重要Issue**:
    - **[#4108 Nightly E2E failed](https://github.com/nearai/ironclaw/issues/4108)**: 每日运行的关键质量门禁持续失败，但 Issue 已存在近一个月。这可能意味着 CI/CD 流程存在瓶颈，或该故障已被团队视为非阻塞性问题。无论何种情况，都建议维护者进行明确回应，阐明状态或解决计划。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，以下是根据LobsterAI (netease-youdao/LobsterAI) 的GitHub数据生成的2026年6月23日项目动态日报。

---

## LobsterAI 项目日报 | 2026年6月23日 (数据截止: 2026-06-22)

### 1. 今日速览

今日项目整体活跃度较高，**核心功能迭代与Bug修复并行**。一方面，通过6个PR的合并，项目在核心工作流（Plan Mode）和OpenClaw插件生态系统上取得了重要进展；另一方面，仍有大量从4月初积累至今的Bug报告和性能/稳定性修复PR处于待处理状态，这构成了项目的技术债务。值得注意的积极信号是，过去24小时内**无新版本发布**，但社区的讨论和贡献热度未减，尤其是在OpenClaw架构和测试对齐方面。

### 2. 版本发布

-   无

### 3. 项目进展

过去24小时内共有6个PR被合并或关闭，显示了项目在核心功能和基础组件上的推进：

-   **核心工作流（Cowork）**：`PR #2183` 引入了 **“计划模式（Plan Mode）”**工作流。这是一个重要的功能推进，允许用户在Composer菜单中选择此模式，为复杂任务生成一个可交互的计划草稿，并支持复制、下载、展开折叠等操作。计划在未批准前会阻止工具调用，批准后则进入正常执行流程，这表明项目正在探索更可控、更可靠的AI工作流范式。[[链接]](https://github.com/netease-youdao/LobsterAI/pull/2183)
-   **OpenClaw插件生态**：`PR #2182`、`PR #2185`、`PR #2186` 集中对OpenClaw插件系统进行了修复和升级。
    -   修复了IM插件（钉钉、飞书、企微等）的安装兼容性问题，支持了OpenClaw 2026.6.1的新安装布局。[[链接]](https://github.com/netease-youdao/LobsterAI/pull/2182)
    -   修复了NIM通道运行时入口的编译问题。[[链接]](https://github.com/netease-youdao/LobsterAI/pull/2186)
    -   解决了`cwd`字段缺失的补丁问题，确保了插件SDK声明的正确生成。[[链接]](https://github.com/netease-youdao/LobsterAI/pull/2185)
-   **测试体系与文档**：`PR #2187` 和 `PR #2184` 分别对测试用例元数据和对齐文档（`AGENTS.md`）进行了更新和完善，为项目的长期稳定性和新贡献者提供了更好的基础。[[链接]](https://github.com/netease-youdao/LobsterAI/pull/2187) [[链接]](https://github.com/netease-youdao/LobsterAI/pull/2184)

**总结**：项目在“计划模式”这一高级功能和OpenClaw插件生态的稳定性上迈出了坚实一步。6个PR的快速关闭显示了维护者对这些领域的积极关注。

### 4. 社区热点

今日讨论最活跃的议题集中在**概览页（Profile Page）的系列Bug**上，尽管这些Issue已标记为“stale”（过时），但它们是近期唯一有讨论的Issues。

-   **标题**：【Bug】概览页"总会话数"始终显示为0
-   **链接**：[Issue #1414](https://github.com/netease-youdao/LobsterAI/issues/1414)
-   **分析**：此问题获得了最多的关注（评论数为1，与其他并列，但内容涉及用户核心数据统计）。用户报告称“总会话数”始终显示为0，而其他统计数据（如API调用数）正常，这直接破坏了用户对使用情况的追踪。背后反映了用户对**个人数据准确性**的强烈诉求。该问题已存在近3个月未解决，可能已影响部分重度用户的使用体验。

### 5. Bug 与稳定性

今日无任何新的Bug报告。但存在多个已报告数月的**高优先级核心Bug**，其中部分已有修复PR但仍未合并：

| 严重程度 | 标题 | 问题链接 | 状态 | 修复PR链接 | 备注 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **高** | 【Bug】概览页"总会话数"始终显示为0 | [Issue #1414](https://github.com/netease-youdao/LobsterAI/issues/1414) | OPEN (stale) | 无 | 核心数据统计错误，对用户信任度影响大 |
| **高** | 【Bug】概览页切换英文后 UI 布局错乱 | [Issue #1416](https://github.com/netease-youdao/LobsterAI/issues/1416) | OPEN (stale) | 无 | 国际化兼容性问题，影响非中文用户 |
| **中** | 【Bug】概览页"使用概览"时间维度筛选器点击无响应 | [Issue #1411](https://github.com/netease-youdao/LobsterAI/issues/1411) | OPEN (stale) | 无 | UI交互失效，功能性Bug |
| **中** | 定时任务已触发，未生成历史记录 | [Issue #1409](https://github.com/netease-youdao/LobsterAI/issues/1409) | OPEN (stale) | 无 | 数据持久化问题，影响自动化流程 |

**值得注意的是**，虽然这些是用户报告的Bug，但今日有数个涉及**性能**和**并发安全**的修复PR被提出并处于待合并状态，例如 `#1410` 优化SQLite写入性能、`#1420` 修复Cron服务并发问题。这些PR一旦合并，将显著提升项目稳定性和用户体验。

### 6. 功能请求与路线图信号

今日无新的功能请求。但从合并的PR `#2183`（Plan Mode）来看，**“计划模式”**被明确纳入并实现，这很可能是下一版本的重要特性。此功能指向用户对**更可控、更透明的AI任务执行流程**的需求，允许用户审查、修改和批准AI的计划，而不是直接执行。

此外，多个关于**OpenClaw插件系统**的修复和升级PR表明，**强化和扩展插件生态**是当前阶段的开发重点。

### 7. 用户反馈摘要

从已存在的Issues评论中，可以提炼出用户的真实痛点：

-   **数据准确性和一致性问题**：用户 `STUPIDDDD0` 在多个Issue中反馈概览页数据错误（总会话数为0、语言切换UI错乱），并十分详尽地描述了复现步骤（包括具体URL），这表明用户能清晰定位问题，但对于这些基础数据Bug的长期存在感到困扰。**痛点在于：使用数据是衡量服务价值的核心指标，不准确的信息会动摇用户信任。**
-   **UI/UX细节打磨不足**：`xuzx-code` 反馈的“skills添加较多时页面展示不友好” ([Issue #1413](https://github.com/netease-youdao/LobsterAI/issues/1413))，以及多个概览页UI Bug，都指向了产品在适配各种屏幕和内容量时的细节处理还有提升空间。用户期望的是流畅、整洁的交互体验。

### 8. 待处理积压

项目中存在大量标记为“stale”（过时）但至今未关闭的重要Issue和PR，形成了一定技术债务。以下是需重点关注的两类积压：

-   **高影响Bug（stale）**：如 `#1414`（总会话数显示为0）、`#1416`（英文UI错乱）等，均已积压近3个月，可能严重影响用户使用和口碑。建议维护者在下个迭代中优先排期处理。
-   **高质量修复PR（stale）**：开发者 `liulingfeng`、`choyuenga` 等人提的多个PR，如 `#1407`（OOM风险）、`#1410`（SQLite性能）、`#1420`（并发安全），都针对了非常核心的稳定性和性能问题，但至今未被合并。这些PR的搁置可能让外部贡献者感到挫败，且项目的稳定性隐患也持续存在。
    -   [PR #1407](https://github.com/netease-youdao/LobsterAI/pull/1407) (Token Proxy OOM风险 - 高)
    -   [PR #1410](https://github.com/netease-youdao/LobsterAI/pull/1410) (SQLite写入性能 - 中)
    -   [PR #1420](https://github.com/netease-youdao/LobsterAI/pull/1420) (Cron服务并发问题 - 高)

**对维护者的提醒**：建议对这些高质量的Stale PR进行Review，并给出明确反馈（合并或要求修改），以鼓励社区贡献和提升项目健康度。同时，积压的核心Bug应当被重新评估优先级，避免因“过时”标签而被忽略。

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

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，根据您提供的 CoPaw 项目数据，我已生成以下项目动态日报。

---

# CoPaw 项目动态日报 - 2026年06月23日

## 1. 今日速览

今日 CoPaw 项目社区活跃度极高。过去24小时内，Issue 和 PR 的讨论与提交均处于高位，其中 PR 数量高达50条，显示了开发团队的积极投入。尽管没有新版本发布，但社区围绕#5218 子Agent冻结等关键 Bug 的讨论极为热烈，同时涌现了多批次针对移动端适配和单元测试覆盖率提升的 PR。项目整体呈现出“高强度修复与渐进式优化并行”的态势，但核心稳定性问题仍需优先解决。

## 2. 版本发布

**无新版本发布。**

## 3. 项目进展

今日共有 12 个 PR 被合并或关闭，项目在以下方面取得了实质进展：

- **代码质量与测试**：社区贡献者 `hanson-hex` 提交了一系列单元测试 PR。
    - 后端：为 `qwenpaw.app.crons` 模块添加了 51 个测试用例，覆盖了定时任务的调度与模型验证逻辑。(#5405)
    - 前端：为 CoPaw 控制台（Console）的 Zustand stores、React hooks 等核心模块新增了约 120 个测试用例，建立了前端的回归安全网。(#5409)
    - **意义**：这是首次针对这两个模块系统性补全单元测试，标志着项目开始重视代码质量基建，为后续重构和新功能开发提供了保障。

- **核心功能修复**：
    - 修复了会话切换卡死问题：解决了嵌入式模式下点击侧边栏会话后，界面无法切换的 Bug。(#5357)
    - 修复了运行时提示文件加载逻辑：确保系统提示词（`AGENTS.md`, `SOUL.md` 等）从 Agent 配置的指定路径加载，而非默认路径。(#5396)

- **功能迭代**：
    - **移动端适配**：多位贡献者提交了针对设置页（安全、技能池、插件管理、模型管理）的移动端卡片布局优化 PR，显著改善了小屏设备上的可用性。(#5391, #5368, #5367, #5363, #5397, #5394)
    - **新集成**：新增了对小米米家智能家居生态的集成指南，拓展了 CoPaw 在 IoT 领域的连接能力。(#5375)
    - **Slack 频道支持**：支持通过 Socket Mode 连接 Slack 作为 AI 助手的交互频道，无需公网 URL，使用更便捷。(#5193)

## 4. 社区热点

- **[(Bug) 子Agent触发上下文压缩时QwenPaw进程冻结无响应 (#5218)](https://github.com/agentscope-ai/QwenPaw/issues/5218)**
    - **热度**：17条评论，成为24小时内讨论最激烈的 Issue。
    - **背后诉求**：用户在使用复杂的多 Agent 协作场景时，一旦子 Agent 触发上下文压缩功能，整个 QwenPaw 进程会完全冻结，只能通过手动重启恢复。这表明核心的上下文管理模块存在严重的线程或进程阻塞问题，直接影响了 CoPaw 作为 AI 助手的稳定性和可用性，是用户当前最痛点的问题之一。

- **[(问題) 每次升级之后，被禁用的内置技能又会重新变回启用2.0 (#5262)](https://github.com/agentscope-ai/QwenPaw/issues/5262)**
    - **热度**：9条评论，这是一个“回归”问题，用户对此感到沮丧。
    - **背后诉求**：用户希望拥有对技能的精细化控制权，每次升级后都需要手动禁用不需要的内置技能（如 `docx`, `xlsx`），操作繁琐。这个问题反映了项目在配置持久化方面存在缺陷，特别是在软件升级流程中，用户的个性化配置没有得到良好的保留，降低了用户体验。

## 5. Bug 与稳定性

以下为今日报告的 Bug，按严重程度排序：

- **严重**
    - **子Agent触发上下文压缩时进程冻结 (#5218)**: 进程无响应，需手动重启。无直接修复 PR。
    - **LLM 获取超时导致空闲后无限挂起 (#5411)**: 空闲10-15分钟后，发送消息会导致界面无限卡死，只能重启。这是一个严重的可用性问题。无直接修复 PR。

- **中等**
    - **Cron 调度器停止分发已启用的任务 (#5398)**: 应用进程存活，但定时任务不再触发。影响自动化工作流。无直接修复 PR。
    - **Dream Task 执行失败 (#5402)**: 用于总结记忆的“白日梦”任务全部报错。影响长期记忆机制。无直接修复 PR。

- **低/功能缺陷**
    - **自定义 OpenAI 兼容提供商不支持 Function Calling (#5345)**: 用户无法使用 OMLX 等第三方服务调用工具。
    - **Shell 命令执行无法解析特殊字符 (#5373)**: 如管道、重定向等标准 Shell 语法无法使用。
    - **前端白屏: 大量工具调用历史无法渲染 (#5401)**: 会话中工具调用过多时，前端直接崩溃。无直接修复 PR。
    - **浏览器自动填充劫持模型配置搜索框 (#5403)**: 搜索框被识别为密码框，弹出密码填充列表。无直接修复 PR。
    - **发送文件生成404链接 (#5370)**: `send_file_to_user` 工具生成的 URL 在前端解析错误。

**总览**：本期 Bug 报告集中在**核心进程稳定性**、**自动化任务**和**前端渲染**三大方面，多个 Bug 都触及了用户依赖的核心工作流，需要开发团队优先处理。

## 6. 功能请求与路线图信号

- **高潜力（有相关PR或社区讨论）**
    - **增加个人知识库 (#2969)**: 该项功能长期被用户期待（👍2票）。目前社区有 PR #5193 (Slack Channel) 和 #5375 (米家集成) 显示项目正在吸收社区集成，但知识库作为基础功能尚未有 PR。
    - **解耦智能体与工作空间 (#5392)**: 提出希望能在不同工作空间中复用同一个智能体。这与更深层次的多Agent管理和配置灵活性相关，可能是未来版本的重构方向。
    - **添加模型自动故障切换 (#5351)**: 社区指出 `RoutingChatModel` 存在但未实例化，用户希望实现主备模型或本地/云端模型的自动切换。这是一个增强可靠性的务实需求，可能与计划中的配置重构相关。

- **潜在信号**
    - **Stabilize the core app before adding new features (#5360)**: 有用户明确建议“先稳定核心应用，再添加新功能”。这个声音反映了社区对当前应用稳定性不足的普遍关切，应被项目维护者视为路线图的重要参考。

## 7. 用户反馈摘要

- **痛点**
    - **升级体验差**：用户对“每次升级后技能被重置”、“升级后启动报错”（#5379）感到困扰，期望一个更平滑的升级路径。
    - **消息队列混乱**：用户发现新增的消息队列在切换对话时容易“串台”，导致消息发送到错误的Agent（#5354）。
    - **移动端体验不佳**：用户反馈应用在手机浏览器上几乎无法使用，UI 元素错位、溢出（#5360, #5368等）。好消息是，今日有多条 PR 正在着手解决此问题。
    - **配置复杂**：新增自定义模型后，页面加载错误，无法使用（#5378）；新手用户在使用第三方 API 时遇到配置困难（#5345, #5330）。

- **使用场景与期望**：
    - 用户期望 CoPaw 成为一个“瑞士军刀”式的工具，希望它能处理从本地文件到智能家居的多种任务。
    - 有用户从其他项目（如 OpenClaw）迁移而来，希望 CoPaw 能支持配置文件的导入，以减少重复劳动（#5254）。

## 8. 待处理积压

- **[Feature] 增加个人知识库的功能 (#2969)**: 发起于2026年4月5日，是社区呼声最高的功能需求之一（👍2）。至今未分配任何标签或已知的开发排期。建议项目组重新评估该功能的优先级，因为它直接关系到 CoPaw 作为“个人 AI 助手”的核心价值。
- **[Bug] Cron scheduler stops dispatching enabled jobs while app remains alive (#5398)**: 虽然刚创建不久，但该 Bug 破坏了核心的自动化编排能力，且暂无修复 PR。如果持续无响应，会影响依赖定时任务的高阶用户。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

好的，这是根据您提供的 ZeroClaw GitHub 数据生成的 2026-06-23 项目动态日报。

***

# ZeroClaw 项目动态日报 – 2026-06-23

## 1. 今日速览

ZeroClaw 项目今日维持极高的活跃度，过去24小时内共计产生100条Issue和PR更新。项目目前处于**密集开发与架构重构期**，社区围绕“去Node.js化”、“Wasm化”和“供应链安全”三大主题展开了激烈讨论。尽管新版本发布数为0，但大量高风险的RFC（如Wasm-first运行时、硬件PGP签名）和修复性PR（如MCP工具不可见、历史记录压缩重写）表明项目正在为下一个重要里程碑（v0.8.3/v0.9.0）扫清障碍。当前需重点关注大量待合并的PR（48个），这可能导致进展延迟。

## 2. 版本发布

*(本日无新版本发布)*

## 3. 项目进展

本日合并/关闭了1个重要PR，同时多项关键工作处于待合并状态。

**已合并/关闭的进展：**
- **`fix(daemon): drain gateway before RPC reload` (PR #8104)**：修复了守护进程在RPC重载前未排空网关连接的缺陷，提升了系统在配置热加载时的稳定性和连接可靠性。

**待合并的重要进展（代表未来方向）：**
- **`refactor(history): rip out history pruning/compression...` (PR #8196, XL)**：这是一次大规模的历史上下文管理重构，旨在消除复杂的多层裁剪/压缩子系统，提供了一个更可预测、更透明的修剪机制，虽然风险高，但有望解决长期存在的上下文超限和工具结果静默丢失问题 (如 Issue #5808)。
- **`feat(turn): add ResolvedAgentExecution::resolve and route prod turn paths` (PR #8179, M)**：统一了所有生产路径上 “Agent执行” 的构造方式，这是实现“代理策略一致性”的关键步骤。
- **`feat(plugins): honor configured signature policy when loading plugin tools` (PR #8172, M)**：修复了插件加载器始终禁用签名验证的严重安全漏洞，现在是确保Wasm插件供应链安全可控的基石。

## 4. 社区热点

本日讨论最活跃的Issue和PR反映了社区对**基础架构变革**和**核心使用体验**的强烈关注。

- **`RFC: WebAssembly-first, eliminate Node.js from ZeroClaw's build and runtime` (Issue #7674)**
    - **评论**: 5 | **状态**: 已关闭
    - **链接**: [#7674](https://github.com/zeroclaw-labs/zeroclaw/issues/7674)
    - **分析**: 该RFC提出的“彻底消除Node.js依赖”计划引发了广泛关注。社区对减少供应链攻击面、统一构建栈的需求非常强烈。此RFC虽已关闭，但其衍生的两个子RFC (`#8132` 替换React UI, `#8135` Wasm插件运行时) 仍在活跃讨论中，表明社区支持这种激进的净化方案。

- **`[Bug]: Default 32k context budget is exceeded by system prompt + tool definitions...` (Issue #5808)**
    - **评论**: 4 | **状态**: 开放中
    - **链接**: [#5808](https://github.com/zeroclaw-labs/zeroclaw/issues/5808)
    - **分析**: 这是一个长期存在的P1级核心Bug，新对话的首轮迭代就会因系统提示词和工具定义过多而触发上下文预算超额。社区对此问题的抱怨和讨论热度持续不减，它直接影响了新用户的首次体验和复杂Agent的可用性。PR #8196的重构被视为根治此问题的希望。

## 5. Bug 与稳定性

今日报告了多个高优先级Bug，主要集中在渠道、工具可见性及跨平台兼容性上。已有多个fix PR在流程中。

| 严重程度 | Issue/PR | 描述 | Fix PR 状态 |
| :--- | :--- | :--- | :--- |
| **S0** | [#8013 (CLOSED)](https://github.com/zeroclaw-labs/zeroclaw/issues/8013) | **[Bug]: 禁用Agent不会停止其绑定的Discord频道** - 存在数据泄露/安全风险。 | 已关闭，推测已修复。 |
| **S1** | [#8193 (CLOSED)](https://github.com/zeroclaw-labs/zeroclaw/issues/8193) | **bug(zerocode): MCP工具在TUI会话中不可见** - 用户添加了MCP工具，但TUI界面看不到，导致工作流阻塞。 | 已关闭，推测已修复。 |
| **S1** | [#7756 (OPEN)](https://github.com/zeroclaw-labs/zeroclaw/issues/7756) | **原生/MCP工具在OpenAI Reasoning和Anthropic模型中不可用** - 模型无法接收到已注册的工具。 | 未提及，但相关联的 [#8054](https://github.com/zeroclaw-labs/zeroclaw/issues/8054) 正在跟踪系统性修复。 |
| **S1** | [#5808 (OPEN)](https://github.com/zeroclaw-labs/zeroclaw/issues/5808) | **默认32k上下文超限** - 导致模型持续进行无意义的预裁剪。 | 相关大重构PR [#8196](https://github.com/zeroclaw-labs/zeroclaw/pull/8196) 开放中。 |
| **S2** | [#7462 (OPEN)](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) | **Windows上74个测试失败** - CI未覆盖Windows环境，导致大量Unix-only命令和路径符号问题。 | 暂无明确修复PR，社区关注度上升。 |

## 6. 功能请求与路线图信号

新提出的功能请求指向了更完善的用户体验、安全增强和新渠道支持，部分已与现有PR形成关联。

- **[Feature]: Automatically set risk profile to yolo in quickstart (Issue #8125)**：提议在快速入门向导中自动启用宽松的风险配置，以改善新用户因限制过多而产生的糟糕体验。这反映了对用户上手流畅度的关注。
- **[Feature]: Optional Telegram webhook mode (Issue #8046)**：用户提议为Telegram渠道增加Webhook模式作为现有轮询模式的补充，以提升消息处理的实时性和减少API调用。这表明社区对成熟、低延迟通信渠道的需求。
- **Support OpenRouter model fallbacks array in provider config (Issue #8138)** + **关联PR #8207**：提议支持OpenRouter的模型自动故障转移功能。这是对API可靠性的直接增强，且已经有一个功能完成的PR在等待合并，极有可能纳入下一个版本。
- **RFC: Supply chain signing... (Issue #8177)** & **RFC: Wasm-first plugin runtime... (Issue #8135)**：这两个RFC共同描绘了ZeroClaw未来的安全蓝图：所有第三方扩展将是带签名的、能力声明的Wasm模块。这是项目长期安全架构的基石性信号。

## 7. 用户反馈摘要

从今天的讨论中可以提炼出用户的几个核心痛点：

- **“开箱即用”受限的痛苦**：用户抱怨默认的上下文预算（32k）太小（Issue #5808），而限制性的风险配置又让快速上手体验变差（Issue #8125）。这表明当前的默认配置偏保守，对探索型用户不够友好。
- **“看到了，但用不上”的沮丧**：MCP工具在TUI中（Issue #8193）或特定模型上（Issue #7756）不可见，让用户在完成MCP服务器连接后却无法使用工具，造成了非常糟糕的“功能断裂”体验。
- **对“系统复杂性”的隐忧**：多个社区成员参与了关于大规模架构重构的讨论（如历史重写PR #8196, Wasm-first RFC #7674）。虽然这体现了社区参与度，但也暗示用户对当前系统在某些核心场景（如上下文管理）下的复杂性和不可预测性感到不满，期待一次彻底的简化。

## 8. 待处理积压

以下为长期未响应或阻塞的重要Issue/PR，需要维护者特别关注，以避免社区贡献者流失或问题恶化。

1.  **[Bug]: 74 test failures on Windows (Issue #7462)**：创建于6月10日，至今未分配或收到明确修复计划。持续增长的Windows用户群体可能因此被毒害，影响项目跨平台生态声誉。
    - 链接: [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462)

2.  **`CI: required PR gate — cargo audit, lockfile check...` (PR #8056) & `CI: scheduled/manual security jobs...` (PR #8057)**：这两个PR拆分自一个大型安全加固计划，专注于CI/CD安全。它们已开放3天，虽然有讨论但进展不明。它们是提升项目供应链安全级别的关键步骤，不应被搁置。
    - 链接: [#8056](https://github.com/zeroclaw-labs/zeroclaw/issues/8056), [#8057](https://github.com/zeroclaw-labs/zeroclaw/issues/8057)

3.  **[Bug]: disabling an agent does not stop its bound Discord channel (Issue #8013)**：虽然在今天被关闭，但其严重性为S0（数据丢失/安全风险）。需要维护者确认其修复是否完整，并考虑是否需要发布一个紧急补丁版本。
    - 链接: [#8013](https://github.com/zeroclaw-labs/zeroclaw/issues/8013)

</details>

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*