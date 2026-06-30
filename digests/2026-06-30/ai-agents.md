# OpenClaw 生态日报 2026-06-30

> Issues: 390 | PRs: 500 | 覆盖项目: 13 个 | 生成时间: 2026-06-30 03:36 UTC

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

好的，作为AI智能体与个人AI助手领域开源项目分析师，我将根据您提供的OpenClaw项目数据，生成一份结构清晰、数据驱动的项目动态日报。

---

# OpenClaw 项目动态日报 | 2026年06月30日

## 1. 今日速览

OpenClaw项目在2026年6月30日维持了极高的社区活跃度。过去24小时内，项目收到了390条Issue更新和500条PR更新，表明社区参与度和代码贡献量均处于峰值水平。目前项目有大量高优先级的Bug报告（主要集中在会话状态、消息丢失和安全领域）和待合并的PR（449条）等待处理。尽管今日无新版本发布，但开发管线非常繁忙，尤其是在修复回归问题（如DeepSeek缓存、Dashboard性能、Codex OAuth）和加固安全边界方面。项目健康度**良好，但需关注**：虽然贡献量巨大，但大量“待合并”的PR和“需要维护者评审”的Issue可能会成为进展瓶颈。

## 2. 版本发布

*无。* 在过去24小时内，没有新的版本（Release）发布。

## 3. 项目进展

今日项目进展主要体现在一批针对“agents”和“gateway”核心组件的防御性编程（guard）PR上，这些PR旨在提升系统稳定性和鲁棒性。虽然大部分PR仍处于开放状态，但它们的出现表明项目正在主动解决由插件或不可靠输入导致的崩溃问题。

- **核心稳定性加固**：维护者 `vincentkoc` 提交了一系列旨在防御“工具描述符”读取失败的PR（如 #89726, #89725, #89734, #89733, #89730, #89720, #89699, #89717）。这些PR在关键代码路径上增加了 `try/catch` 保护，防止单个插件或工具的异常导致整个智能体或工具系统崩溃，显著提升了系统的容错能力。
- **安全性与边界**：
    - 合并了 `#89635` 旨在修复 `writeTextAtomic` 函数创建目录权限过于宽松的问题，将状态目录权限上限改为 `0700`，提升了本地数据安全性。
    - `#89702` 修复了macOS应用在系统升级后陷入无限重配对循环的问题，提升了用户体验。
    - `#97952` 明确了代码执行（Codex）相关的敏感控制需要管理员权限，强化了授权模型。
- **性能与资源管理**：`#89696` PR引入了低内存保护机制，在系统内存不足时提前中止工具调用，避免了主机OOM。
- **渠道特定修复**：
    - `#97711` 通过限制JSON响应读取大小，防止了Microsoft Teams渠道的潜在OOM攻击。
    - `#89744` 修复了Discord多账户启动时的延迟排序问题。
    - `#97991` 修复了飞书渠道在非入站消息上下文中工具调用使用错误的绑定账户问题。

**项目整体向前迈进了一大步**，从单纯的功能开发转向了系统健壮性、安全性和可观察性的深度打磨。

## 4. 社区热点

今日社区讨论集中于几个核心问题，反映了用户对**会话状态一致性、消息传递可靠性和性能**的广泛关注。

1.  **`#86538` [Bug]: Session write-lock timeouts block subagent delivery lanes**
    - **热度**: 18条评论
    - **核心诉求**: 用户报告会话的JSONL写入锁超时会导致子智能体投递通道阻塞，且缺乏足够的诊断信息。这是影响多智能体协作稳定性的严重问题。
    - **分析**: 这是目前最活跃的Issue之一，反映了用户对于复杂工作流（如子代理）中并发写入锁竞争的普遍担忧。

2.  **`#80520` [Bug]: Telegram messages silently dropped, no sendMessage logged**
    - **热度**: 11条评论
    - **核心诉求**: Telegram消息被静默丢弃，没有任何日志记录，用户无法感知消息发送失败。这是一个典型的“静默失败”问题，对用户体验伤害极大。
    - **分析**: 该问题在11天内获得11条评论，说明对Telegram用户影响面广。用户期望系统提供更明确的错误反馈，而非无声无息地失败。

3.  **`#94518` [Bug]: DeepSeek cache hit rate <10% after 6.x upgrade**
    - **热度**: 6条评论，且获得8个👍（是展示列表中点赞数最高的之一）
    - **核心诉求**: 从5.28升级到6.x后，DeepSeek模型的缓存命中率骤降至10%以下，导致API成本飙升和响应变慢。
    - **分析**: 这是一个典型的“回归”问题，且直接影响用户的经济利益（API调用成本）。用户对边界感知缓存机制的变更非常敏感。

4.  **`#79077` [Feature]: Support for Telegram bot-to-bot and guest-bot modes**
    - **热度**: 8条评论，8个👍（并列最高赞）
    - **核心诉求**: 用户强烈希望OpenClaw支持Telegram平台5月7日发布的新功能，即“机器人间通信”和“访客机器人”模式。
    - **分析**: 这并非Bug，而是一个明确的功能请求。获得大量点赞表明社区对紧跟上游平台新特性的期待非常高。

## 5. Bug 与稳定性

过去24小时内报告的Bug主要集中在**会话状态**、**消息丢失**和**回归问题**上。以下按严重程度排列：

- **严重 (S级 - 功能阻塞或数据丢失风险)**:
    - **`#97970`** [P1]: `openclaw update` 补全`gateway.bind`字段为`lan`，与 `auth.mode:none` 冲突，导致Gateway以exit 78直接退出。这是关键的自动升级陷阱，影响所有依赖默认值行为的用户。 **无修复PR**。
    - **`#97877`** [P1]: `empty-error-retry`（空错误重试）逻辑被`hadPotentialSideEffects`标志阻塞，导致在同一个会话中，如果在某个工具调用后遭遇瞬时的5xx错误，系统会静默失败，不会重试。 **有Fix PR关联**。
    - **`#95121`** [P2]: Codex OAuth路径回归，即使是微小请求也需要花费约28秒的初始化时间，性能严重下降。 **无修复PR**。

- **中等 (A级 - 影响核心功能或体验)**:
    - **`#83736`** [P2]: Gateway在升级后无法容忍子节点存在微小的Node协议版本差异，导致节点无法连接。 **无修复PR**。
    - **`#87058`** [P1]: Android节点连接后，因命令协调过程问题，无法发现或展示其能力（advertises zero commands），导致节点不可用。 **无修复PR**。
    - **`#83532`** [P1]: Web UI响应延迟，用户必须手动刷新页面才能看到智能体的回复。 **无修复PR**。
    - **`#96857`** [P2]: 智能体工具的正常文本输出被退化为`(see attached image)`占位符，导致智能体对文本输出“失明”。 **无修复PR**。

- **回归 (R级 - 以前正常的功能现在失败)**:
    - **`#81934`** [P2]: 更新至2026.5.12后，macOS上的Gmail发送、Dropbox终端访问、PDF生成等多项功能同时失效。 **无修复PR**。
    - **`#82250`** [P1]: macOS的LaunchAgent在检测到已有Gateway运行时，退出不干净，导致 Launchd 无限重启。 **无修复PR**。

**今日没有与新Bug强关联的已合并修复PR**，表明社区虽然报告了问题，但修复仍需时间。

## 6. 功能请求与路线图信号

今日收集的功能请求显示用户希望扩展OpenClaw的平台边界和开发者体验。

- **`#79077` [Feature]: Telegram bot-to-bot / guest-bot modes** - 强烈的社区诉求，是跟上平台演进的关键P2特性。结合现有PR（如`#82002`讨论Telegram群组上下文丢失），该项目在Telegram渠道上的投入是可见的，此特性很可能在后续版本中考虑。
- **`#80213` [Feature]: Skill author-defined setup hook (run skill-supplied script on install/update)** - 开发者需求，希望能够在安装/更新技能时运行自定义脚本，以完成更复杂的后处理任务。这是对当前有限的`install`类型的重大扩展，信号级别较高。
- **`#81913` [Feature]: Expose stable plugin SDK surface for installed skill workflows** - 协同于上述Issue，社区希望为技能工作流提供一个稳定的、官方的插件SDK，避免第三方插件直接访问核心模块的内部API。这表明社区生态正在向更成熟、更标准化的方向发展。
- **`#82450` [Feature]: Linear Persistent Workspace Mode for Blind Users** - 来自无障碍社区的声音。用户（完全失明）希望有一个线性的、持久的工作区模式，以简化屏幕阅读器的使用。这是一个非常有价值的可用性改进请求。

**路线图信号**：`#81960` 要求允许在初始化（onboarding）时配置多个provider和模型，这可能暗示了项目希望简化用户的首次配置体验，并可能在未来版本中作为默认行为的一部分。

## 7. 用户反馈摘要

从今日的Issue评论中，可以提炼出以下用户痛点和使用场景：

- **痛点1: “静默失败”的不可接受性**
    > 用户对**消息被无声丢弃**（`#80520`）、**异常退出无提示**（`#80700`）、**重试逻辑静默绕过**（`#97877`）等问题表达了强烈不满。用户期望系统提供明确的反馈（错误日志、通知），而不是让他们去“猜”发生了什么。
- **痛点2: 升级带来的“惊喜”**
    > 多个问题（`#94518`, `#81934`, `#82250`, `#97970`）明确指向**升级版本导致现有工作流程被破坏**。这突显了项目的回归测试和升级迁移指南仍存在缺口，尤其是在配置兼容性和API行为变更上。
- **痛点3: 核心功能的可靠性焦虑**
    > 关于**会话锁**（`#86538`）、**子智能体上下文丢失**（`#81490`）、**Telegram群组上下文丢失**（`#82002`）的讨论，显示出用户正在将OpenClaw应用于**多智能体协作、复杂工作流**等更高阶场景。这些场景对系统状态一致性要求极高，任何不稳定因素都会被放大。
- **使用场景: 真实世界中的多工具整合**
    > 盲人用户（`#82450`）使用OpenClaw管理**视频推广、社交媒体、博客、市场研究**等复杂工作流，展示了OpenClaw作为“万能AI办公助手”的强大潜力。用户对无障碍需求的反馈，是产品成熟度的一个重要信号。
- **满意点**: 用户虽然抱怨问题，但在表达方式上往往是“这是一个非常强大的工具，但是……”的开场白，这表明用户对项目的整体愿景和潜力是认可的，但稳定性是当前的核心矛盾。

## 8. 待处理积压

以下是一些长期未得到明确进展或维护者响应的重要Issue/PR，建议维护者关注：

- **`#79077` [Feature]: Telegram bot-to-bot / guest-bot modes** - 创建于2026-05-07，获得8个👍和8条评论，是呼声最高的功能请求之一，但状态仍为“需要维护者评审”和“需要产品决策”。
- **`#77642` [Bug]: [5.3 regression] lossless-claw: duplicate answers + “missing tool result in session history"** - 创建于2026-05-05，是一个在上一个版本引入的回归问题，导致重复回答和合成错误。虽标注为P1，但仍需“产品决策”和“现场复现”。
- **`#81061` [Feature]: Hook: before_route_inbound_message** - 一个架构性的功能请求，提出需要“路由前”的消息钩子，以实现通道桥接/代理。该请求已满约一个月，但状态为“stale”和“P2”，可能需要更明确的产品层面的认可。
- **`#82070` [Bug]: CLI commands ~14s cold-start regression after 2026.5.12 update** - CLI性能退化是影响所有用户的普遍性问题，但Issue状态停留在“需要现场复现”，可能因为复现条件或环境不一致导致难以定位。

---

## 横向生态对比

好的，作为AI智能体与个人AI助手领域资深技术分析师，现根据您提供的2026年6月30日各项目动态数据，为您呈上横向对比分析报告。

---

### AI智能体开源生态横向分析报告 (2026-06-30)

**报告日期:** 2026-06-30
**分析师:** AI 智能体开源项目分析师

#### 1. 生态全景

当前，个人AI助手与自主智能体开源生态呈现出 **“核心平台成熟、功能分化加剧、稳定性成为瓶颈”** 的态势。以OpenClaw为首的核心项目正从功能快速扩张转向系统健壮性、安全性和可观测性的深度打磨，社区反馈中“静默失败”、“升级回归”和“配置冲突”成为普遍痛点。同时，大量新兴项目（如NanoBot、PicoClaw）正通过在 **“轻量级”**、**“协议扩展”** 或 **“特定平台深度优化”** （如AWS Bedrock）等方向寻求差异化。生态整体健康，但社区对基础稳定性、成本控制（Token/API缓存）和多智能体协作可靠性的要求已显著提高。

#### 2. 各项目活跃度对比

| 项目名称 | Issues 更新 | PR 更新 | 新版本发布 | 今日健康度评估 | 关键描述 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 390 | 500 | 无 | **良好，需关注** | 贡献量巨大，但大量`待合并`PR和`需评审`Issue可能成为瓶颈。 |
| **Hermes Agent** | 50 | 50 | 无 | **高活跃，承压大** | 社区反馈和PR提交量极高，但安全与稳定性Bug积压多，团队承压。 |
| **Zeroclaw** | 50 | 50 | 无 | **极高** | 高速迭代，社区讨论集中在工具/模型兼容性核心问题上。 |
| **IronClaw** | 14 | 50 | 无 | **高，版本冲刺前夜** | 密集合并大量Bug修复与WebUI v2测试，为Reborn版本发布做准备。 |
| **CoPaw** | 50 | 50 | 无 | **极高** | 单元测试覆盖率大幅提升，开发动能强劲，处于版本迭代前夜。 |
| **LobsterAI** | 少量 | 39 | **有 (v2026.6.29)** | **高** | 发布新版本，团队密集修复OpenClaw集成稳定性问题。 |
| **NanoBot** | 11 | 32 | 无 | **高** | 社区贡献活跃，核心方向偏向安全性、流式传输与WebUI优化。 |
| **NanoClaw** | 1 | 7 | 无 | **健康，势头良好** | PR活动频繁，安全性与功能修复并行，但核心Bug待解决。 |
| **NullClaw** | 1 | 2 | 无 | **中等偏上** | 开发节奏稳定，聚焦CLI体验优化与流式传输能力增强。 |
| **PicoClaw** | 3 | 3 | 无 | **平稳，功能迭代前期** | 社区有明确呼声，功能PR排队中，整体活跃度不如头部项目。 |

#### 3. OpenClaw 在生态中的定位

- **优势：** 作为核心参考项目，OpenClaw拥有**最庞大的社区规模和最完整的生态**。其Issue和PR更新量级远超其他项目（390/500 vs 50/50），显示出无可比拟的社区参与度。它在多智能体协作（子Agent）、深度安全加固（权限、路径）、渠道覆盖广度（Discord、飞书、Teams）等方面持续投入，是领域内的“基础设施”级项目。
- **技术路线差异：** OpenClaw倾向于构建一个**高度集成、功能全面**的“超级平台”，通过防御性编程和复杂的会话状态管理追求系统级稳定。这与NanoBot强调“超轻量、代码简洁”的极简主义路线形成鲜明对比。
- **社区规模对比：** 从数据看，OpenClaw的社区体量和问题广度是其他项目的**数倍甚至数十倍**。这既是其生态领导地位的体现，也意味着它在处理社区噪音、维护长期积压问题上需要投入更多资源。

#### 4. 共同关注的技术方向

多个项目不约而同地涌现出以下共同技术需求，表明这是行业级的痛点与趋势：

1.  **会话状态一致性与可靠性**
    - **涉及项目：** **OpenClaw** (#86538 会话锁)、**NanoBot** (#4595 会话数据中毒)、**Hermes Agent** (多个Session状态污染Issue)、**LobsterAI** (对话历史丢失)
    - **具体诉求：** 用户普遍要求系统保证会话数据的原子性、持久性和跨入口（如Web/Telegram）的一致性，避免因并发、崩溃或升级导致的数据丢失或污染。

2.  **成本优化与可观察性（Token/API缓存）**
    - **涉及项目：** **OpenClaw** (#94518 DeepSeek缓存回归)、**NanoBot** (#4222 前缀缓存失效)、**CoPaw** (#3891 DeepSeek缓存命中率)、**PicoClaw** (PR#3163 Bedrock缓存)、**Zeroclaw** (OTel集成深化)
    - **具体诉求：** 随着API调用成为主要成本，社区极度关注Prompt缓存效率和Token用量监控。用户希望有更智能的缓存策略、更精细的成本核算和可观测性工具。

3.  **安全性强化（边界、凭据、权限）**
    - **涉及项目：** **OpenClaw** (#89635 目录权限)、**NanoBot** (#4594 路径绕过)、**Hermes Agent** (symlink绕过、ACP权限漏洞)、**NanoClaw** (#2880 符号链接逃逸)
    - **具体诉求：** 社区对Agent可能导致的本地文件系统攻击、凭据泄露和未授权操作高度警惕。防御性编程和最小权限原则成为刚需。

4.  **渠道/协议中立性**
    - **涉及项目：** **PicoClaw** (#3093 请求SimpleX/Tox)、**NanoClaw** (PR#2884 Discord适配器)、**Zeroclaw** (Twilio SMS频道请求)、**CoPaw** (企业微信、钉钉优化)
    - **具体诉求：** 用户不希望被锁定在单一通信渠道。对去中心化、高度加密的协议（如DeltaChat, SimpleX）的支持需求开始浮现，表明社区用户对**数据主权和隐私**的关注度在提升。

#### 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
| :--- | :--- | :--- | :--- |
| **OpenClaw** | 全能型平台，强于多智能体与稳定性 | 寻求“一切集成”的进阶开发者、团队 | 复杂会话状态机、防御性编程、高度模块化 |
| **NanoBot** | 极轻量、代码简洁、快速上手 | 追求效率、偏好源码阅读的个人开发者 | 极简依赖、强调低心智负担、快速响应社区 |
| **Hermes Agent** | 安全性驱动、企业级认证与合规 | 对安全敏感的企业用户、安全研究员 | 深度安全审计（symlink、ACP）、OIDC企业认证 |
| **IronClaw** | Reborn新架构测试与WebUI v2 | 参与新版测试、关注架构演进的早期用户 | 新旧架构并行（Legacy & Reborn），聚焦测试覆盖 |
| **CoPaw** | AgentScope生态、多平台适配 | 依赖阿里通义千问或国产模型的用户 | 深度绑定`agentscope`框架、强于视觉/Fallback能力 |
| **Zeroclaw** | 插件生态（WASM+OCI）、深度可观测性 | 技术极客、构建私有Agent平台的开发者 | 前沿的插件分发机制（OCI）、开放遥测（OTel）深度集成 |
| **LobsterAI** | OpenClaw集成伴侣、任务编排 | OpenClaw用户，寻求任务管理增强 | 聚焦于OpenClaw的任务调度、定时任务与工作流 |

#### 6. 社区热度与成熟度

- **快速迭代阶段：** **Zeroclaw**, **CoPaw**, **NanoBot**。这些项目PR提交/合并频率极高，新功能和新Bug同时大量涌现，社区讨论辛辣，技术前沿探索味道浓厚。
- **质量巩固阶段：** **OpenClaw**, **Hermes Agent**。虽然也有大量PR，但社区热点和项目核心工作已从“加新功能”转向“查缺补漏”。大量Bug集中在“回归问题”、“性能退化”、“错误处理不透明”上，表明产品已进入从“能用”到“好用”的关键质变期。
- **版本冲刺阶段：** **IronClaw**。项目组正在为Reborn版本进行密集的QA和Bug修复，合并活动（20个）远高于新Issue提出量（14个），显示出典型的发布前集中打磨特征。
- **平稳演进阶段：** **PicoClaw**, **NullClaw**, **NanoClaw**。这些项目势头良好但规模尚小，发展节奏更稳健，社区互动更聚焦于特定功能或痛点的解决。

#### 7. 值得关注的趋势信号

1.  **“静默失败”不可接受：** 从**OpenClaw**（消息静默丢弃）到**IronClaw**（OAuth静默失败），所有项目都面临用户对“出错无反馈”的强烈不满。
    - **对开发者的启示：** **错误报告和诊断能力是下一阶段AI Agent应用可信度的基石。** 设计时必须考虑“失败大声”原则，确保系统在出错时能提供清晰的、可操作的反馈，这是取代用户“猜谜”体验的关键。

2.  **“轻量级”的再定义：** **NanoBot**的#660 Issue揭示了社区对“超轻量”的认知与项目实际技术栈（Python+Node.js）之间的鸿沟。
    - **对开发者的启示：** **“轻量”不仅是代码行数少，更是资源占用低、启动快、依赖解耦。** 纯Rust或纯Go的单二进制部署方案可能比“简洁的Python代码”更能满足高阶用户的“轻量”预期。

3.  **Long-loop Agent 的兴起：** **Hermes Agent**的#21172（持久化循环合约）和**CoPaw**的PR#5637（事件驱动子Agent）清楚地表明，社区已经不满足于“问答式”Agent，而是在构建能**自主运行、定时触发、后台协作**的长期任务。
    - **对开发者的启示：** **设计Agent框架时，必须考虑“持续性”和“状态管理”。** 理解并支持Agent的长时间运行、跨会话状态维护、以及事件驱动的唤醒机制，将是构建下一代自主AI员工的关键能力。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

好的，这是根据您提供的 NanoBot 项目数据生成的 2026-06-30 项目动态日报。

---

## NanoBot 项目动态日报 | 2026-06-30

### 1. 今日速览

今日项目活跃度极高。过去24小时内，社区提交了 **11个 Issue** 和 **32个 PR**，其中 PR 提交量尤为突出，显示了核心贡献者与社区的高度参与。项目修复已合并/关闭了 **3个 Issue** 和 **8个 PR**，但在执行环境安全、流式传输稳定性以及 WebUI 功能优化方面仍面临较大的开发压力与社区讨论。同时，一个涉及“臃肿依赖”的旧 Issue (#660) 被重新关注，反映了社区对项目核心理念的持续审视。

### 2. 版本发布

*无*

### 3. 项目进展

今日项目在功能完善和 Bug 修复上取得了多项实质性进展。以下为已合并或关闭的重要变更，展示了项目在安全性、用户体验和技术债务上的持续投入。

- **核心功能推进:**
    - **[CLOSED] PR #4502**: 新增网关 Webhook 触发器 (`feat: Add gateway webhook triggers`)，大幅提升了项目的集成能力和自动化工作流构建潜力。
    - **[CLOSED] PR #4600**: 优化了 WebUI 的提示词导轨缩略图 (`feat(webui): refine prompt rail minimap`)，将其移至左侧并重新设计为类似 Codex 的紧凑样式，改进了用户体验。

- **安全与稳定性修复:**
    - **[MERGED] PR #4594**: 修复了执行工具中的路径提取安全漏洞，阻止了通过 `=` 号（如 `--output=/etc/passwd`）绕过工作区边界检查的攻击向量。 (Fixes #4592)
    - **[MERGED] PR #4596**: 修复了 `StreamingFileEditTracker` 中一个严重 Bug，该 Bug 会错误地覆写非文件编辑工具（如 `read_file`）的 `tool_call.id`，导致会话数据永久污染。 (Fixes #4595)
    - **[MERGED] PR #4584**: 修复了 MCP (Model Context Protocol) 服务器 URL 在日志中泄露凭据的安全问题，增强了日志安全性。

- **开发者体验与项目健康度:**
    - **[MERGED] PR #4577**: 为 `bwrap` 沙箱执行环境添加了回归测试，确保 `/tmp` 临时空间的正确挂载，提升了代码健壮性。
    - **[MERGED] PR #4583**: 修复了配置加载过程中的一个潜在崩溃问题，即在工具键迁移时未正确处理 `null` 配置段。

### 4. 社区热点

今日最受关注的议题集中在对核心机制的反省与功能扩展的讨论上。

- **#660: [CLOSED] “超轻量”承诺与臃肿依赖的矛盾**
  - **链接**: [Issue #660](https://github.com/HKUDS/nanobot/issues/660)
  - **背景**: 这个始于半年前的 Issue 今日获得更新。用户指出项目自称“超轻量”，但 Dockerfile 同时依赖 Python 和 Node.js，与其宣传不符。该 Issue 获得了 **15条评论** 和 **5个赞**，是今日讨论度最高的议题。
  - **诉求分析**: 用户对项目核心理念“轻量级”的期待与实际技术栈构成之间存在认知差距。这不仅是技术问题，更是品牌和用户预期管理问题。

- **#4595: `apply_final_call_ids` 导致会话永久中毒**
  - **链接**: [Issue #4595](https://github.com/HKUDS/nanobot/issues/4595)
  - **背景**: 该 Bug 报告详细描述了流式传输中 `tool_call.id` 被错误覆写的问题，并立即有对应的修复 PR [#4596](https://github.com/HKUDS/nanobot/pull/4596) 被提交和合并。这种“报告即修复”的效率是社区健康的标志。
  - **诉求分析**: 社区对影响数据一致性和后续交互的“毒性”Bug 容忍度极低，能迅速引起共鸣并驱动快速修复。

### 5. Bug 与稳定性

今日报告的 Bug 涉及安全、数据损坏和用户体验，其中大部分已快速得到修复。

- **严重 (已修复)**:
  - **路径提取绕过安全限制**: PR [#4594](https://github.com/HKUDS/nanobot/pull/4594) 修复了 Issue [#4592](https://github.com/HKUDS/nanobot/issues/4592)，该漏洞允许恶意命令绕过工作区限制。*(严重度高)*
  - **会话数据永久中毒 (Session Poisoning)**: PR [#4596](https://github.com/HKUDS/nanobot/pull/4596) 修复了 Issue [#4595](https://github.com/HKUDS/nanobot/issues/4595)，该 Bug 错误地覆写了工具调用ID，导致后续所有交互都基于混乱的数据进行。*(严重度高)*
  - **凭据泄露风险**: PR [#4584](https://github.com/HKUDS/nanobot/pull/4584) 修复了 MCP 连接日志中可能包含明文凭据的安全问题。*(安全风险高)*

- **中等 (已修复/正在修复)**:
  - **安装脚本崩溃**: Issue [#4599](https://github.com/HKUDS/nanobot/issues/4599) 报告了 Linux 安装脚本在非交互式终端中崩溃。对应的修复 PR [#4602](https://github.com/HKUDS/nanobot/pull/4602) 已提交，通过检测终端类型并优雅处理来解决。
  - **配置加载崩溃**: PR [#4583](https://github.com/HKUDS/nanobot/pull/4583) 修复了 `null` 配置段导致迁移失败的问题。

### 6. 功能请求与路线图信号

今日社区提出了多项功能请求，其中一些已有相应的 PR 实现，预示着它们很可能被纳入下一个版本。

- **大概率纳入下个版本**:
  - **Provider 级别的代理配置 (Provider-Scoped Proxy)**: Issue [#4604](https://github.com/HKUDS/nanobot/issues/4604) 请求 Anthropic OAuth 支持，而 PR [#4578](https://github.com/HKUDS/nanobot/pull/4578) 提出的 `provider-scoped proxy config` 是一个更通用的解决方案，目前处于开放状态，热度较高。
  - **企业版 GitHub Copilot 端点覆盖**: PR [#4598](https://github.com/HKUDS/nanobot/pull/4598) 直接为 `GitHub Copilot for Business/Enterprise` 用户提供了支持，解决了 #4220 的请求。
  - **WebUI 功能增强**: 多个 PR (如 #4586, #4587, #4600) 正在为 WebUI 添加会话时间戳、Markdown 导出、界面优化等新功能，表明 WebUI 是当前开发的重点方向。

- **值得关注的长期信号**:
  - **外部脚本触发 Agent**: Issue [#4605](https://github.com/HKUDS/nanobot/issues/4605) 请求一种从外部脚本触发 Agent 任务的方式。用户已通过 `gws CLI` 和 Gmail skill 构建了邮件过滤系统，但希望能更深度集成。这体现了高级用户对平台可编程性和扩展性的需求。
  - **自动推理难度升级**: Issue [#4419](https://github.com/HKUDS/nanobot/issues/4419) 请求实现自动化的推理难度分级。这表明用户已在尝试利用模型的“深度思考”能力，并希望更智能地管理成本和响应时间。

### 7. 用户反馈摘要

从今日 Issues 和 PR 的评论中可以提炼以下用户反馈：

- **痛点**:
  - **“超轻量”期待与现实不符**: 用户 `besoeasy` 指出了 Dockerfile 依赖 Node.js，与“ultra-lightweight”宣传不符，质疑项目的技术选型。
  - **安装体验不佳**: 用户 `hamb1y-bot-hkuds-nanobot` 报告了安装脚本在标准环境下崩溃，说明新手引导流程的鲁棒性有待提升。
  - **数据损坏风险**: 用户 `MadSkittles` 报告了 `StreamingFileEditTracker` 导致的会话“毒性”问题，这对依赖会话连续性的用户是灾难性的体验。

- **满意/肯定**:
  - **赞赏代码轻量**: 用户 `chengyongru` (在 #4605 中) 表示：“Compared to OpenClaw, the lightweight codebase makes it easy to read and understand the source, which I really appreciate.” 这表明，尽管有 #660 的反对声音，但也有核心用户认可项目代码的简洁性。

### 8. 待处理积压

以下为长期未响应或维护者应关注的重要议题：

- **[OPEN] #4222: [`bug`] `max_messages` 截断与微压缩持续使前缀缓存失效**
  - **链接**: [Issue #4222](https://github.com/HKUDS/nanobot/issues/4222)
  - **原因**: 该 Bug 严重影响了与 LLM 交互的性能，因为每次对话都会破坏 prompt/prefix 缓存，导致成本增加和响应变慢。
  - **当前状态**: 创建于 2026-06-06，已有3条评论，但在进入 2026-06 下旬后无新进展。考虑到这是一个影响性能的核心问题，建议维护者重点关注。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，我将根据您提供的数据，生成一份Hermes Agent项目在2026年6月30日的项目动态日报。

---

# Hermes Agent 项目日报 | 2026-06-30

## 1. 今日速览

今日Hermes Agent项目处于**持续高活跃**状态，社区贡献和讨论热度极高。关键指标显示：
- **社区响应快**：过去24小时内，有 50 个新 Issue 和 50 个新 PR 被提出，表明社区参与度极高，同时也暴露出项目在快速迭代中遇到的各种问题。
- **待处理负担重**：存在大量待合并的PR（46个）和未解决的问题，形成了显著的“待办积压”。这主要是由于项目团队正在集中精力处理关键Bug和安全问题。
- **版本稳定**：今日无新版本发布，项目处于“大修”而非“大改”的阶段，重点在修复Bug和增强安全性。
- **安全与稳定是主线**：社区讨论和提交的PR高度集中在安全性加固（如symlink绕过、ACP权限漏洞）和稳定性修复（如session状态、内存污染、邮件解析崩溃）上，表明项目已进入质量强化期。

## 2. 版本发布

无

## 3. 项目进展

今日项目团队完成了数个关键PR的合并/关闭，在功能和安全性方面取得了显著进展：

- **核心安全修复**：PR #37336 被合并，这是一个对敏感凭据存储（如OAuth token和认证锁）进行写保护的关键安全补丁，有效防止了代理意外修改关键认证文件。这标志着项目在安全边界加固上迈出了重要一步。
- **平台兼容性增强**：PR #40019 被合并，通过将 `/var/run` 等系统路径加入媒体发送的黑名单，修复了一个通过路径解析绕过安全限制的漏洞，增强了网关在多种系统环境下的安全性。
- **网关/显示层优化**：PR #55166 被合并，为内置工具（如“搜索网页”、“浏览URL”）引入了更友好的人工可读标签，改善了终端和桌面版用户的交互体验，使其更接近ChatGPT的风格。
- **身份认证扩展**：PR #55344 被合并，为自托管OIDC（OpenID Connect）身份认证协议增加了对“机密客户端”（要求client_secret）的支持，提升了Dashbord的安全性和对企业级部署场景的支持。

整体来看，项目正在从快速功能开发阶段，转向对安全性、稳定性和用户体验的精修阶段。

## 4. 社区热点

今日社区讨论最为热烈、评论最多的Issues主要集中在以下方面：

- **macOS TUI模式崩溃 (Issue #27282, 10条评论)**
  [链接](https://github.com/NousResearch/hermes-agent/issues/27282)
  **分析**：用户`Ayanami-Shinji`报告在使用`--tui`模式时，网关在处理过程中意外退出，报错`stdin EOF`。问题核心在于它与内置内存（非byterover）的交互存在bug。这是继#14036后的又一例类似问题，暗示了`comp/tui`组件与`comp/gateway`之间可能存在设计缺陷或竞态条件。这是影响用户体验的核心痛点。

- **持久化长循环合约需求 (Issue #21172, 6条评论)**
  [链接](https://github.com/NousResearch/hermes-agent/issues/21172)
  **分析**：社区对“持久化长循环代理”功能有强烈需求。用户`zhengsx`引用Claude Code负责人的观点，提出了一个“一级合约”功能，允许用户为cron驱动的代理循环声明式地设置预算、停止条件和刷新策略。这反映了社区不再满足于单次会话，而是希望构建能持续运行、自主管理的代理系统。这是一个重要的路线图信号。

- **热调节参数不可配置 (Issue #17565, 5条评论，6个👍)**
  [链接](https://github.com/NousResearch/hermes-agent/issues/17565)
  **分析**：关于热参数（temperature）不可配置的Issue获得了6个赞，代表了广泛社区用户的强烈诉求。用户`cedricwyh`指出，当前硬编码的热参数导致模型过度随机化，产生严重幻觉，尤其是在代码生成等需要精度的任务中。这直接触及了代理核心能力的瓶颈，是不可接受的功能缺失。

- **桌面版鼠标滚轮问题 (Issue #37527, 5条评论)**
  [链接](https://github.com/NousResearch/hermes-agent/issues/37527)
  **分析**：桌面应用在长对话窗口中，鼠标滚轮向上滚动时会自动弹回底部。这个看似微小的UI Bug严重影响了用户的阅读和交互体验。用户反馈拖拽滚动条可以正常工作，说明问题出在滚轮事件处理逻辑上，可能涉及窗口滚动状态与焦点管理。

## 5. Bug 与稳定性

今日报告的Bug数量多、覆盖面广，按严重程度排列如下：

- **严重 (P1/P2) - 安全性相关**：
    - **ACP symlink绕过权限检查 (Issue #55367, P2)**: 攻击者可以创建一个指向凭据文件的symlink，从而绕过“敏感路径”自动批准检查。这是个严重的安全漏洞，**无修复PR**。
    - **凭据池读取陈旧环境变量 (Issue #20591, P1)**: 凭据读取逻辑未遵守设计，优先读取了过时的系统环境变量而非最新的 `.env` 文件配置，导致认证失败。**无修复PR**。
- **严重 (P1/P2) - 运行稳定性相关**：
    - **TUI模式异常退出 (Issue #27282, P1)**: 导致macOS用户无法正常使用TUI模式，如前述。
    - **session & 状态污染 (多个Issue)**: 包括WebUI/API session连续性失败 (Issue #55374)、跨配置文件内存污染 (Issue #54937)、终端工具无法获取当前session ID (Issue #55202) 等，这些问题导致用户操作上下文混乱，影响代理的可靠运行。**均有P2以上标签，相关PR #55386 正在修复cron session问题**。
    - **热参数被静默丢弃 (Issue #55276, P2)**: 用户配置的`reasoning_effort`/`thinking_budget`对特定provider无效且无任何提示，导致用户以为配置正确但模型行为不符合预期。
- **中等 (P2/P3) - 功能异常**：
    - **桌面版滚轮回弹 (Issue #37527, P2)**: 严重影响桌面端用户体验。
    - **Tool参数类型转换错误 (Issue #55369, P2)**: `Union[int, str]`类型的参数，`"007"`被错误转换为数字7，导致工具行为错误。
    - **邮件解析崩溃 (多个Issues)**: (Issue #55383, #55381) 恶意或格式错误的邮件会直接导致IMAP获取进程崩溃，影响整个邮件平台的可靠性。幸运的是，**有对应的修复PR (#55382, #55384)**，且均由报告者`MaxFreedomPollard`提交。

## 6. 功能请求与路线图信号

今日社区呼声较高的功能请求主要来自社区热点：

- **可配置热参数 (Issue #17565, 6个👍)**: 这是社区最基础的诉求之一。考虑到其高赞和重要性，**极有可能被纳入下一个版本**。
- **持久化长循环合约 (Issue #21172)**: 这是一个更具前瞻性的功能，代表了代理从“工具”向“员工”演进的路线。虽然当前开发资源紧张，但这项功能很可能会被列入**中期路线图**。
- **跨平台会话连续性 (Issue #54981)**: 用户希望能在Desktop和Telegram之间无缝切换对话。这需要引入更复杂的会话合并/同步机制，目前只是一个Feature请求，尚未有相关PR出现，短期内实现可能性较低。
- **“永久”/受保护技能 (Issue #25083)**: 用户希望保护核心技能文件免遭代理意外修改。这与当前的安全加固主题非常契合，**有很大可能在后续的某个安全版本中被实现**。

## 7. 用户反馈摘要

- **痛点**：
    - **配置不生效且无反馈**：用户对 `temperature` 和 `reasoning_effort` 等关键推理参数无法配置或配置被静默丢弃表示强烈不满 (Issues #17565, #55276)。
    - **安全问题令人担忧**：多个用户报告了安全边界问题，如symlink绕过、权限提升，显示出对代理安全性的高度不信任 (Issue #55367, #55147)。
    - **桌面UI体验不佳**：滚轮回弹、session丢失等Bug让桌面端用户感到沮丧(Issue #37527, #55374)。
    - **稳定性成为瓶颈**：邮件解析崩溃、session状态污染、TUI崩溃等问题表明，当前版本的可靠性远未达到生产级标准。

- **满意的地方**：
    - 相比之下，社区对PR的提交和修复速度表示正面。例如，报告邮件解析bug的用户 `MaxFreedomPollard` 同时提交了修复PR，展现了社区的自助精神。
    - 对`hermes-agent`技能过于冗长、成本高昂的反馈 (Issue #51387)，说明用户对代理的成本和效率很敏感，并希望其“帮助”功能本身能更加高效。

## 8. 待处理积压

以下为长期存在、尚未被有效回应的关键Issue或PR，建议项目维护者重点关注：

- **高龄Issue**：
    - **Issue #13489 (2026-04-21)**: ACP session的凭据解析错误，导致使用自定义provider时无法正常工作。此问题已存在超过2个月，属于核心功能缺陷，建议尽快评估和修复。
    - **Issue #17565 (2026-04-29)**: 热参数可配置化。虽然是一个Feature Request，但其高赞数和高用户呼声，长期不回应会损失社区信任。

- **待合并的PR**：
    - **PR #48436 (P1, 2026-06-18)**: 修复TUI在MCP关闭时自杀的关键bug。此PR影响到TUI功能和MCP工具稳定性，优先级极高，且标记了多个sweeper风险标签，**需要优先评审和合并**。
    - **PR #20239 (P2, 2026-05-05)**: 优化FTS存储架构以节省资源。这是一项性能优化，对长期运行的服务器部署至关重要，但已等待近2个月，建议安排评审。
    - **PR #36180 (P2, 2026-06-01)**: 修复API Server平台在没有配置`API_SERVER_KEY`时被错误加载的问题。这是一个潜在的安全/配置问题，建议尽快处理。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

好的，这是为您生成的 PicoClaw 项目动态日报。

***

## PicoClaw 项目动态日报 | 2026-06-30

### 1. 今日速览

过去24小时内，PicoClaw 项目活跃度中等，主要集中在社区反馈和功能开发的前期准备上。共有3个 Issue 和3个 PR 被更新，但均无新版本发布。其中，一个关于旧版 Safari 兼容性的 Bug 已被关闭，表明维护团队正在清理积压问题。社区对新网关（如 DeltaChat）和平台适配（AWS Bedrock 缓存优化）的呼声较高，相关 PR 正在等待合并，有望在下一版本中引入这些重要功能，提升项目的连接性和性能。整体来看，项目处于“平稳开发，功能迭代前期”的状态。

### 2. 版本发布

无新版本发布。

### 3. 项目进展

今日没有 PR 被合并或关闭，但在待合并队列中有几个值得关注的重要功能改进：

- **[PR #3063] feat: add deltachat gateway (新增 DeltaChat 网关)**：由社区开发者 `trufae` 提交，旨在为 PicoClaw 添加 DeltaChat 协议的网关支持。若合并，将极大扩展 PicoClaw 的通信协议覆盖范围，满足用户对去中心化通信的需求。状态：待合并。
  - 链接：`sipeed/picoclaw PR #3063`

- **[PR #3163] feat(bedrock): leverage Converse prompt caching via cache points (利用 Bedrock Converse API 提示缓存)**：由开发者 `loafoe` 提交，这是一个性能优化 PR。通过利用 AWS Bedrock 的提示缓存功能，可以显著降低使用该平台的 API 调用成本（缓存命中时输入部分仅计费约 0.1 倍），并可能减少响应延迟。这对于依赖 AWS Bedrock 的用户是重大利好。状态：待合并。
  - 链接：`sipeed/picoclaw PR #3163`

- **[PR #3156] feat(pico): emit per-turn LLM token usage on finalized message (在 Pico 通道上发送单轮 Token 用量)**：同样由 `loafoe` 提交，此 PR 旨在让下游消费者能够实时追踪每次对话的完整 Token 消耗（区分输入/输出），方便进行成本核算和用量监控。状态：待合并。
  - 链接：`sipeed/picoclaw PR #3156`

**项目进展小结**：虽然今日无合并操作，但这三个待合并的 PR 覆盖了“协议扩展”、“性能与成本优化”和“可观测性”三个关键方向，表明项目正在向更成熟、更企业级应用的方向迈进。

### 4. 社区热点

今日社区讨论最活跃的 Issue 是 **[#3093] [Feature] I need SimpleX or tox**。
- **链接**：`sipeed/picoclaw Issue #3093`
- **分析**：该 Issue 获得4条评论和1个赞。用户 `Damian-o2` 明确提出了对 `SimpleX`、`Wire` 或 `Tox` 等加密、去中心化通信协议网关的支持需求。结合已提交的 `DeltaChat` 网关 PR（#3063），可以清晰看出社区中存在一股强大的力量，希望 PicoClaw 能够支持更多样化、注重隐私的安全通信渠道。这不仅是功能请求，更是对项目未来发展路线的清晰信号。

### 5. Bug 与稳定性

今日报告并关闭了一个 Bug，另有一个未解决的 Bug 需要注意。

- **[已修复] Issue #3090 - [BUG] Panel does not work on Safari on iOS versions below 16.4 (低于16.4版本的iOS Safari无法使用面板)**
  - **严重程度**：高（影响了特定用户群体的核心功能访问）
  - **状态**：已关闭。该问题已被标记为 `[stale]` 后最终关闭，具体修复commit未在数据中显示，但问题已得到处理。
  - 链接：`sipeed/picoclaw Issue #3090`

- **[待修复] Issue #3153 - [BUG] Volcengine Doubao Seed tool calls occasionally leak as <seed:tool_call> text (豆包大模型工具调用偶尔泄漏为原始文本)**
  - **严重程度**：中（功能可用性受损，导致错误输出给用户）
  - **描述**：当使用 `doubao-seed-2.0-pro` 模型时，工具调用的结果偶尔会以原始 XML 标签的形式直接输出给用户，而非执行工具调用。这表明模型与 PicoClaw 的工具调用解析逻辑之间可能存在偶发性故障。
  - **是否已有修复 PR**：暂无。
  - 链接：`sipeed/picoclaw Issue #3153`

### 6. 功能请求与路线图信号

- **协议网关扩展**：除了已提交 PR 的 DeltaChat，用户还明确提出了对 SimpleX、Wire、Tox 等协议的支持。这些请求表明，“协议中立性”和“去中心化”是社区的核心期望。如果路线图允许，建立一个“网关扩展接口”或优先支持其中一两个热门协议，将能很好地满足用户诉求。
- **平台深度优化**：`PR #3163` (Bedrock 缓存) 和 `PR #3156` (Token 用量) 代表了社区对降本增效和精细化运营的追求。这暗示着 PicoClaw 的用户群体正从个人实验者向更专业的团队用户过渡，下一版本大概率会包含这些优化。

### 7. 用户反馈摘要

从 Issues 讨论中提炼的用户反馈如下：

- **痛点：豆包模型工具调用偶发故障。** 用户 `ms8great` 报告了使用 `doubao-seed-2.0-pro` 时工具调用失效的问题，这会影响所有依赖该模型进行自动化任务（如代码执行）的用户，降低了系统的可靠性。
- **诉求：支持更多加密/隐私优先的通讯协议。** 用户 `Damian-o2` 的诉求非常明确，代表了追求“反审查”、“去中心化”和“数据主权”的用户群体。这是一个细分但忠诚度很高的用户群。
- **满意点（推测）：旧版 Safari 问题得到解决。** 虽然报告Bug的Issue已被关闭，但未留下明确的满意度反馈。然而，关闭一个影响用户体验的兼容性Bug，通常对维护社区信心有积极作用。

### 8. 待处理积压

- **未合并的网关扩展 PR (#3063)**：该 PR 由社区贡献，已存在超过21天且未被合并。如果维护团队有计划或有疑虑（如维护成本、安全审查），建议尽快与贡献者沟通，给出明确反馈（合并、挂起或拒绝）。长期拖延可能打击社区贡献者的积极性。
  - 链接：`sipeed/picoclaw PR #3063`

- **未修复的豆包模型 Bug (#3153)**：该 Issue 在过去24小时内有更新，但尚未有修复 PR 关联。建议尽快复现并定位根因，以避免该问题进一步影响 Volcengine 用户群体。
  - 链接：`sipeed/picoclaw Issue #3153`

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

好的，这是根据您提供的 NanoClaw 项目数据生成的 2026-06-30 项目动态日报。

---

# NanoClaw 项目动态日报 | 2026-06-30

## 1. 今日速览
- **项目整体活跃度评估：高。** 过去24小时内PR活动频繁（7条），待合并PR数量（5条）表明社区贡献积极，项目正处于密集的功能迭代和关键Bug修复阶段。
- **核心进展：** 项目安全性和稳定性得到显著加强，两项关键修复（安全：符号链接逃逸攻击；功能：新渠道默认提供商继承）均已提交PR。此外，Discord渠道适配器、Slack Socket Mode等长期需求进入合并队列。
- **社区热点：** 一个关于Discord等渠道附件内容丢失的Bug（#2888）成为社区关注焦点，该问题直接影响用户核心交互体验，但尚未有对应的修复PR。
- **风险提示：** 今日无新版本发布，所有重要修复和功能仍处于“待合并”状态，需关注合并周期。
- **项目健康度：** 尽管存在一个影响核心体验的严重Bug，但开发团队和社区贡献者反应迅速，针对安全、功能缺陷和开发者体验的PR齐头并进，项目维护状态健康，势头良好。

## 2. 版本发布
无。

## 3. 项目进展 (今日合并/关闭的PR)
**已合并/关闭 (2条):**
- **#2883 [MERGED] feat: voice-notify v3 意图分流 + kill-switch** — 语音播报功能得到重大升级，从一刀切改为5类意图分流，并新增运行时kill-switch。`tier2tech-tian` 贡献，测试覆盖充分，表明项目在Agent交互体验上持续打磨。
- **#2882 [MERGED] fix(ncl): default messaging-groups create instance to channel_type** — 修复了 `ncl messaging-groups create` 命令因数据库约束导致崩溃的Bug (`omri-maya` 贡献)。提升了命令行工具的稳定性和开发者体验。

**分析：** 今日合并的两个PR分别聚焦于AI Agent的人机交互体验和底层工具稳定性，表明项目在“功能增强”与“基础维护”两条线路上并行推进。

## 4. 社区热点
- **#2888 [OPEN] Discord (and likely other url-only chat-sdk adapters) drop image/file attachments** — 获1条讨论，是今日唯一活跃的Issue。
    - **链接：** [Issue #2888](https://github.com/nanocoai/nanoclaw/issues/2888) (注：原文为 nanocoai/nanoclaw，此处沿用)
    - **诉求分析：** 用户 `eagansilverpathmarketing` 报告了一个严重Bug：通过Discord发送图片/文件时，Agent只接收到文件名，看不到内容。作者已定位到根因（`chat-sdk-bridge.ts` 中的 `messageToInbound` 方法），并指出Telegram工作正常。**这意味着核心的多模态交互能力在Discord渠道上完全失效，对依赖文件分析的用户影响巨大。**

## 5. Bug 与稳定性
按严重程度排列，从高到低：
1.  **P0 - 核心功能缺失:** **#2888** - Discord渠道附件内容丢失，Agent无法处理图片/文件。此为当前最严重的未修复Bug。
    - **链接：** [Issue #2888](https://github.com/nanocoai/nanoclaw/issues/2888)
    - **状态：** 无关联的修复PR。
2.  **P1 - 安全性问题:**
    - **#2880 [OPEN] fix(security): contain inbox symlink escapes** — 修复一个严重的安全漏洞：恶意Agent可通过符号链接逃逸攻击，在宿主机上写入任意文件。`johnmathews` 已提交修复PR，建议优先合入。
    - **链接：** [PR #2880](https://github.com/nanocoai/nanoclaw/pull/2880)
3.  **P2 - 功能缺陷:**
    - **#2886 [OPEN] fix: channel-registered new agents inherit the install's provider** — 修复新渠道注册时，Agent组默认使用Claude提供商，导致单提供商安装中出现401错误。`thisdotrob` 提交了直接修复。
    - **链接：** [PR #2886](https://github.com/nanocoai/nanoclaw/pull/2886)
4.  **P3 - 开发体验Bug:**
    - **#2882 [CLOSED] fix(ncl): default messaging-groups create instance to channel_type** — 已修复的命令行工具Bug。
    - **链接：** [PR #2882](https://github.com/nanocoai/nanoclaw/pull/2882) (已合并)

## 6. 功能请求与路线图信号
- **Discord渠道支持 (信号强烈):** PR #2884 ([PR #2884](https://github.com/nanocoai/nanoclaw/pull/2884)) 正在寻求合并，该PR不仅添加了Discord适配器，还修复了Gateway模式下的审批按钮路由问题。结合Issue #2888的反馈，完善Discord功能是社区和开发者的共同优先级。
- **Slack Socket Mode (路线图确认):** PR #2885 ([PR #2885](https://github.com/nanocoai/nanoclaw/pull/2885)) 将引导式设置中的Slack Socket Mode支持从 `channels` 分支合入主分支。这表明官方希望简化用户配置，提升Slack渠道的易用性。
- **Dashboard推送 (新功能):** PR #2871 ([PR #2871](https://github.com/nanocoai/nanoclaw/pull/2871)) 提出了一个新的Dashboard Pusher功能，用于向外部服务器推送状态快照。该功能可能为未来的监控、运维或可视化面板（如OpenCode）铺平道路。

## 7. 用户反馈摘要
- **痛点聚焦：** 用户名 `eagansilverpathmarketing` 的反馈最为具体。他不仅报告了Bug，还**直接指出了根因代码所在行 (src/channels/chat-sdk-bridge.ts)**，这为开发者快速定位和修复提供了巨大帮助。这体现了社区中存在相当专业的高阶用户。
- **使用场景：** 从Issue内容推断，用户正在实际生产环境中使用NanoClaw集成Discord，并依赖文件/图片的自动处理和解析功能。当前Bug已经完全阻塞了其核心工作流。
- **满意点：** 尽管遇到Bug，但用户能精准报告问题，侧面说明了他对项目有一定了解且愿意投入精力反馈。目前尚未看到其他明确表示满意或不满的评论。

## 8. 待处理积压
- **#2888 [OPEN] Discord 附件丢失** — 作为P0级、直接影响核心功能的Bug，虽为最新提交，但应被视为最高优先级积压。目前尚无修复PR，维护者需立即响应，可考虑在 #2884 (Discord适配器PR) 中一并修复，或指派专人跟进。
    - **链接：** [Issue #2888](https://github.com/nanocoai/nanoclaw/issues/2888)
- **#2880 [OPEN] 符号链接逃逸安全修复** — 此Bug (CWE-59) 严重性高，修复PR已存在3天，但仍在Pending。长期积压可能导致安全风险。
    - **链接：** [PR #2880](https://github.com/nanocoai/nanoclaw/pull/2880)

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，以下是根据您提供的NullClaw项目数据生成的2026年6月30日项目动态日报。

***

### **NullClaw 项目动态日报 | 2026年6月30日**

**项目名称:** NullClaw (github.com/nullclaw/nullclaw)
**报告日期:** 2026-06-30
**分析师:** AI 开源项目分析师

#### 1. 今日速览

今日项目活跃度中等偏上，核心聚焦于 **CLI交互体验的修复** 和 **流式传输能力的增强**。社区反馈了一个关于Telegram Channel在空闲后停止响应的Bug，但后端服务运行正常。合并/关闭活动较少，但有三个待合并的PR表明有重要的功能改进和依赖更新正在排队等待审查。整体项目健康度良好，开发节奏稳定。

#### 2. 版本发布

*   **无**

#### 3. 项目进展

今日项目成功合并了一个重要的PR，显著提升了终端用户的使用体验；同时，一个与流式传输相关的重磅新功能PR也已开放。

*   **已合并/关闭：**
    *   **[PR #960] [CLOSED] fix(cli): handle arrow keys in agent REPL**
        *   **作者:** vernonstinebaker
        *   **状态:** 已合并/关闭
        *   **变更摘要:** 为交互式 `nullclaw agent` REPL环境添加了一个轻量级、无分配的行编辑器。现在，在TTY会话中，用户可以使用方向键导航历史记录、移动光标、删除字符等，告别了之前显示控制字符（如 `^[[A`）的糟糕体验。
        *   **项目意义:** 这是一个重要的用户体验优化，使得NullClaw的Agent交互模式（REPL）更加友好和专业，降低了用户的使用门槛。
        *   **链接:** [PR #960](https://github.com/nullclaw/nullclaw/pull/960)

*   **待审查的重点PR：**
    *   **[PR #971] [OPEN] feat(streaming): native tool calls during SSE streaming**
        *   **作者:** vernonstinebaker
        *   **状态:** 待合并
        *   **变更摘要:** 解耦了对原生工具调用的支持与流式传输路径。此前，只要附加了流式回调，代理循环就会强制禁用原生工具，将其转为提示注入格式。此PR允许那些支持流式传输期间原生工具的模型供应商（如最新的GPT-4或Claude模型）正常发出原生工具调用。
        *   **项目意义:** 这是一个架构层面的改进，显著提升了流式传输场景下调用工具的效率和兼容性。这意味着用户在使用支持此特性的模型时，将获得更流畅、更实时的工具调用体验。
        *   **链接:** [PR #971](https://github.com/nullclaw/nullclaw/pull/971)

#### 4. 社区热点

*   **热点问题: [Issue #972] [Bug] Telegram channel 空闲后停止响应**
    *   虽然目前只有一个新Issue，但它代表了社区用户一个**具体且紧迫的痛点**。用户报告NullClaw集成的Telegram Channel在过夜空闲后“死亡”，不再响应新消息。有趣的是，`nullclaw`后端进程本身似乎仍在正常工作（可以响应命令行Ping）。
    *   **背后的诉求:** 用户希望NullClaw的Telegram集成具有**健壮的连接保持机制**（例如心跳、自动重连），确保长期空闲后仍能正常服务。这暴露出后端在管理长连接（如Telegram Bot的长轮询或Webhook）时可能存在状态管理问题。
    *   **链接:** [Issue #972](https://github.com/nullclaw/nullclaw/issues/972)

#### 5. Bug 与稳定性

*   **严重:**
    *   **[Issue #972]** Telegram channel 空闲后停止响应。
        *   **状态:** 新开，无评论，无修复PR。
        *   **严重性:** 高。该Bug直接导致NullClaw的一个主要功能入口（Telegram）不可用，影响了用户的日常使用和信任度。
        *   **分析:** 疑似长连接的空闲超时或状态丢失，需重点排查Telegram Bot客户端的连接池或长轮询机制。
        *   **链接:** [Issue #972](https://github.com/nullclaw/nullclaw/issues/972)

#### 6. 功能请求与路线图信号

*   **核心功能增强：**
    *   **PR #971 (feat(streaming): native tool calls)** 是当前最强烈的信号，表明项目正致力于支持**最新的AI模型特性**，并优化**实时交互体验**。这很可能被纳入下一个版本。
    *   **PR #956 (ci(deps): bump alpine from 3.23 to 3.24)** 是一个常规依赖更新，但保持基础镜像的最新状态是安全和稳定的基础。
*   **新需求信号：**
    *   Issue #972 间接提出了一个功能需求：**为Telegram集成增加自动重连或心跳机制**。虽然这是一个Bug修复，但本质上是对稳定性的功能需求。

#### 7. 用户反馈摘要

*   **正面反馈（隐含）:**
    *   PR #960 的修复表明用户对 `nullclaw agent` 命令行REPL的体验有抱怨（无法正常使用方向键），该修复解决了之前混乱的交互问题，预计会得到用户的积极反馈。
*   **负面/痛点反馈:**
    *   **连接稳定性差:** Issue #972 的作者明确反馈Telegram集成在空闲后失效，导致服务不可用。作者提到“后端似乎工作正常”，意味着问题出在Telegram channel前端与后端的持久连接上，这是一个明确的体验中断点。
    *   **使用场景示例:** 用户在夜间或周末不使用时，第二天早上发现Telegram bot无法响应，必须手动重启服务，这对追求“永远在线”的个人AI助手而言是致命缺陷。

#### 8. 待处理积压

*   **依赖更新待合并:**
    *   **[PR #956] ci(deps): bump alpine from 3.23 to 3.24 in the docker-images group**
        *   **作者:** dependabot[bot]
        *   **创建时间:** 2026-06-15
        *   **状态:** 待合并
        *   **风险:** 低。这是一个常规的依赖更新，但已悬而未决超过两周。建议尽快合并并检查Docker构建是否正常。
        *   **链接:** [PR #956](https://github.com/nullclaw/nullclaw/pull/956)

*   **悬而未决的热点问题:**
    *   **[Issue #972] Telegram channel 空闲后停止响应**
        *   **建议:** 维护者应优先响应该Issue，尝试复现并提供排查思路或临时解决方案（例如建议用户配置时间戳ping或使用crontab定期重启服务），以安抚社区情绪并收集更多信息。
        *   **链接:** [Issue #972](https://github.com/nullclaw/nullclaw/issues/972)

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，我将根据您提供的IronClaw项目数据，生成一份结构清晰、数据驱动的项目动态日报。

---

# IronClaw 项目动态日报 | 2026年6月30日

## 1. 今日速览

今日项目活跃度极高，社区与核心团队在Bug修复和功能迭代上均投入了大量精力。Issues 更新 14 条，其中新提交的高质量 Bug 报告多达 10 个；Pull Requests 更新 50 条，显示出密集的代码提交与审查活动。核心团队正集中力量推进 **Reborn** 版本的稳定性、WebUI v2 的体验优化以及多用户权限体系的融合设计。尽管无新版本发布，但大量 Bug 修复和功能 PR 的合并，标志着项目在迈向更高稳定性的道路上取得了坚实进展。

## 2. 版本发布

无。

## 3. 项目进展

今日共有 **20 个** PR 被合并/关闭，主要集中在以下关键领域：

-   **Reborn 测试框架与覆盖率提升**：核心贡献者合并了多组关于 Reborn 集成测试的 PR，包括模拟 MCP 脚手架重构（#5427）、共享持久化组测试（#5402）以及将 Legacy E2E 覆盖率迁移至 Reborn 流程（#5371, #5372, #5373）。这显著增强了 Reborn 版本的质量保障体系。
-   **WebUI v2 本地化与 QA**：大量关于 WebUI v2 的 PR 被合并，包括工具的本地化文案（#5401）、授权与审批流程的测试覆盖（#5372）以及将 QA 表单提示集成到自动化测试中（#5406）。这表明团队正密集打磨WebUI v2的用户体验。
-   **关键 Bug 修复**：关闭了 #5413（OAuth 刷新静默失败）和 #5196（“每次询问”工具权限失效）等高影响级别 Bug，提升了系统的可靠性。
-   **CI/CD 与工具链优化**：合并了修复 Canary PR 目标验证的 PR（#5422）和 Rust 依赖的常规更新（#5050），确保了开发流程的顺畅。

**项目头部推进总结**：项目主要沿着 **“Reborn 引擎稳定性 + WebUI v2 体验打磨 + 测试基础设施强化”** 三条主线加速推进，已经从功能验证阶段进入精细化调优与可靠性加固阶段。

## 4. 社区热点

今日讨论最多的议题集中在 Bug 报告，而非大型功能讨论。

- **`#5415` [Bug Bash P1]**：多工具 Google Sheets 工作流报“协议违反”错误。此 Issue 由社区 QA 成员 `joe-rlo` 报告，是今日最严重的 Bug 之一。核心问题在于涉及 18-25 次工具调用的复杂流程在 Google Sheets 集成时出现故障。此 Bug 凸显了复杂编排场景下的稳定性挑战，可能成为明天的优先修复项。
    - 链接： [Issue #5415](https://github.com/nearai/ironclaw/issues/5415)

- **`#5414` (未在列表，但 `#5417-5420` 系列讨论度高)**：`joe-rlo` 连续提交了多个关于 Web UI 和技能选型的 Bug（如技能选错 #5417，消息顺序错乱 #5418，无重命名自动化选项 #5419），表明社区 QA 人员正在对 Reborn 版本进行高强度、系统性的功能验收。这些 Bug 虽然单个影响有限，但集中反映了当前版本在边缘用例上的可用性问题。
    - 链接：
        - [Issue #5417](https://github.com/nearai/ironclaw/issues/5417)
        - [Issue #5418](https://github.com/nearai/ironclaw/issues/5418)
        - [Issue #5419](https://github.com/nearai/ironclaw/issues/5419)

**分析**：社区焦点已从新功能畅想转向了**实际使用中的精细化问题和可靠性**。用户期望的是“能用且好用”，今天的大量 Issue 正是对此期望的直接反馈。

## 5. Bug 与稳定性

今天 Bug 报告非常集中，大部分来自 QA 测试。按严重程度排列如下：

**P1 (Critical)：**
- **`#5415`**：多工具 Google Sheets 工作流因“协议违反”错误失败。[链接](https://github.com/nearai/ironclaw/issues/5415)
- **`#5426`**：[QA] 因系统盘不可用导致无法创建 Routine。[链接](https://github.com/nearai/ironclaw/issues/5426)

**P2 (High)：**
- **`#5416`**：错误的 Google 连接状态导致矛盾的身份认证流程。[链接](https://github.com/nearai/ironclaw/issues/5416)
- **`#5417`**：搜索 Hacker News 时，激活了错误的技能。[链接](https://github.com/nearai/ironclaw/issues/5417)
- **`#5421`**：Reborn 版本中 Web 搜索体验差且需要额外认证。[链接](https://github.com/nearai/ironclaw/issues/5421)

**P3 (Medium)：**
- **`#5418`**：工具调用后，对话消息顺序错乱。[链接](https://github.com/nearai/ironclaw/issues/5418)
- **`#5419`**：[QA] 无法重命名已有自动化作业。[链接](https://github.com/nearai/ironclaw/issues/5419)
- **`#5420`**：Routine 投递目标是全局设置，而非按 Routine 配置。[链接](https://github.com/nearai/ironclaw/issues/5420)

**已修复/已关闭的高影响 Bug：**
- **`#5413`** (CLOSED)：`Reborn inline OAuth` 在刷新失败时静默处理，做出了“大声失败”的修复。[链接](https://github.com/nearai/ironclaw/issues/5413)
- **`#5196`** (CLOSED)：`“Ask each time”` 工具权限失败并导致重复授权流程问题已修复。[链接](https://github.com/nearai/ironclaw/issues/5196)

**稳定性汇总**：项目今日暴露出在**复杂工具链编排、多步骤认证、以及对用户意图的准确理解**上存在较多稳定性与可用性回归。好消息是，核心团队对 Bug 响应迅速，已关闭了几个根因明显的核心 Bug。

## 6. 功能请求与路线图信号

今日没有全新的宏大功能请求，更多是针对现有功能的改进信号。

- **`#5420`**：Routine投递全局化问题。用户希望通过此 Bug 报告间接请求“**按 Routine 配置投递渠道**”的功能。
- **`#5419`**：无法重命名自动化。用户请求增加修改自动化名称的 UI 功能。
- **`#5421`**：Web 搜索配置体验差。用户请求在 Reborn 下实现**真正的零配置 Web 搜索**体验。
- **`#4776`** (OPEN)：为符合条件的工具添加**“始终允许”**的全局设置。此长期 Issue 今日无更新，但它是 Reborn 权限系统的关键 UX 改进。相关 PR `#5394` 正在推进功能策略的端到端实现，可能会影响此功能的落地。

**路线图信号**：以上功能请求均属于**用户体验微调和可用性增强**范畴，表明产品已具备核心功能，当前重点在于打磨细节。这些建议很可能在接下来的几个小版本（如 0.25.0 或 0.26.0）中被采纳。

## 7. 用户反馈摘要

从今日 Issues 的评论和描述中，可以提炼出以下用户痛点：

- **“困惑”**：用户 `joe-rlo` 在报告 `#5416` 时，描述了 “连接 Gmail 时智能体错误地报告已连接” 的场景，反映出当前系统在**状态反馈和意图解读**方面让用户感到困惑。
- **“不透明”**：`#5415` 中的 `“protocol violation”` 错误对于用户来说是一个黑盒错误，无法指导用户进行下一步操作。类似的，`#5413` 修复前的“静默失败”也是不透明的典型案例。
- **“缺少控制力”**：`#5419` 和 `#5420` 直接反映了用户对**基本配置能力的缺失感到沮丧**。无法重命名自动化、无法为不同 Routine 设置不同投递渠道，这些在预期中“理所应当”的功能确实会严重影响用户信任度。
- **积极的修复反馈**：虽然无直接正面评论，但两个高影响 Bug (`#5413`, `#5196`) 的迅速关闭，透露了核心团队对社区/QA 报告的重视，这有助于建立正向的社区反馈循环。

## 8. 待处理积压

以下 Issue/PR 长期未得到响应或存在较大争议，建议维护者关注：

- **`#4108`** (OPEN, 34天): `Nightly E2E failed`。这是一个由 CI 机器人自动报告的自动化测试持续失败 Issue。虽然可能属于偶发，但一个持续一个多月的 E2E 失败表明 CI 稳定性存在系统性问题，需排查根因。
    - 链接： [Issue #4108](https://github.com/nearai/ironclaw/issues/4108)

- **`#3706`** (OPEN, 45天): `dependabot` 提出的 JS 依赖 (`postcss`, `@remotion/cli`) 更新 PR。它已存在超过45天，且属于间接依赖更新。虽然风险低，但长期积压会导致后续合并时出现更多冲突，建议尽快处理。
    - 链接： [PR #3706](https://github.com/nearai/ironclaw/pull/3706)

- **`#4776`** (OPEN, 19天): `Add global Always Allow setting`。此 Feature Request 被标记为 `Reborn-Only Scope`，且是 `#5385` 多用户能力策略的一部分。虽然今天 PR `#5394` 在推进相关能力，但此 Issue 本身未获得管理层的明确评论或纳入时间线，应尽快给予更新。
    - 链接： [Issue #4776](https://github.com/nearai/ironclaw/issues/4776)

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

好的，作为 LobsterAI 项目的 AI 智能体与个人 AI 助手领域开源项目分析师，我为您呈上 2026 年 6 月 30 日的项目动态日报。

---

# LobsterAI 项目动态日报 | 2026-06-30

**项目名称:** LobsterAI
**数据来源:** github.com/netease-youdao/LobsterAI
**统计周期:** 2026-06-29 至 2026-06-30

## 1. 今日速览

今日 LobsterAI 项目活跃度极高。核心开发团队正全力推动 **v2026.6.29 版本发布** 的最终合并与稳定性修复工作，PR 合并/关闭数量高达 39 条，是近期最繁忙的时段之一。项目焦点集中在 **OpenClaw 集成** 的运行时稳定性、**Cowork 会话导航** 的 UI 体验优化，以及通过 **诊断日志** 提升生产环境可观测性。社区方面，用户对积分清零政策和重复输出导致 Token 浪费的问题反馈较为强烈，同时提出了任务编排和 UI 适配等建设性建议。

## 2. 版本发布

- **名称:** [LobsterAI 2026.6.29](https://github.com/netease-youdao/LobsterAI/releases/tag/v2026.6.29)
- **核心更新:**
    - **OpenClaw 集成稳定性增强:**
        - 修复了 Agent 工作区与任务工作目录混淆的问题，确保 Agent 的身份、记忆文件能被正确加载。
        - 修复了定时任务运行后，后续对话历史丢失的问题。
        - 修复了用户对话轮次缓存不一致的问题。
        - 优化了插件审批流程，使其正确路由到 Cowork 权限系统。
    - **Cowork 体验优化:**
        - 清理了对话轨道（conversation rail）的导航预览，使 UI 更清晰。
    - **其他:**
        - 多个 PR 合并以修复 OpenClaw 在 v2026.6.1 版本中的回归问题。
- **破坏性变更:** 无明确记录。
- **迁移注意事项:** 建议所有用户升级到此版本以获得 OpenClaw 集成的最佳稳定性和 bug 修复。

## 3. 项目进展

今日项目通过密集的 PR 合并，取得了显著进展，主要集中在对新版本的质量把关和对早期问题的回溯修复上。关键进展包括:

- **发布流程收尾:** PR [#2228](https://github.com/netease-youdao/LobsterAI/pull/2228) 成功将 `release/2026.6.29` 分支合并到 `main`，标志着新版本的正式推进。此过程涉及多次`revert`与`reapply`操作 (PR [#2225](https://github.com/netease-youdao/LobsterAI/pull/2225), [#2226](https://github.com/netease-youdao/LobsterAI/pull/2226))，体现了团队对代码库整洁度的严格把控。
- **OpenClaw 深度修复:** 针对 OpenClaw 集成，团队修复了多个深层次问题，包括：
    - Agent 引导工作区与任务当前工作目录的分离 (PR [#2227](https://github.com/netease-youdao/LobsterAI/pull/2227))。
    - 定时任务运行后的对话历史维护 (PR [#2220](https://github.com/netease-youdao/LobsterAI/pull/2220))。
    - 用户对话轮次缓存稳定性 (PR [#2219](https://github.com/netease-youdao/LobsterAI/pull/2219))。
    - 引入迁移脚本以兼容旧的定时任务存储格式 (PR [#2189](https://github.com/netease-youdao/LobsterAI/pull/2189))。
- **可观测性提升:** PR [#2229](https://github.com/netease-youdao/LobsterAI/pull/2229) 为 Cowork 和 OpenClaw 流程增加了诊断日志，为未来的线上问题排查提供了有力工具。
- **插件兼容性:** 团队修复了新版 OpenClaw 插件安装架构的兼容性问题 (PR [#2182](https://github.com/netease-youdao/LobsterAI/pull/2182))，并解决了 NIM 等插件的编译问题 (PR [#2186](https://github.com/netease-youdao/LobsterAI/pull/2186))。

## 4. 社区热点

今日话题主要集中在新版本发布带来的功能优化，以及用户长期反馈的痛点。

- **热点对话 & 功能请求:**
    - **[Issue #2120: 建议](https://github.com/netease-youdao/LobsterAI/issues/2120):** 用户提出了三项具体建议：1) 借鉴 Workbuddy 的任务存储机制，实现任务预输入以提高连续性；2) 延长单次任务运行时长；3) 调整 2560x1600 分辨率下的技能界面 UI 为三列。该 Issue 体现了用户对**任务编排能力**和**高分辨率适配**的期待。
    - **[Issue #2131: LobsterAI 支持 hermes agent 有计划吗？](https://github.com/netease-youdao/LobsterAI/issues/2131):** 社区对集成新的 Agent 框架（如 Hermes）表现出兴趣，表明用户希望 LobsterAI 能保持开放性和兼容性。
- **Bug 反馈:**
    - **[Issue #2121: 对一个现象的疑问（怀疑是bug）](https://github.com/netease-youdao/LobsterAI/issues/2121):** 用户报告了重复输出文字的问题，并猜测这会浪费 Token。这是关于 **Token 经济性** 和 **Agent 行为可控性** 的重要反馈，核心开发者需关注是否存在 prompt 优化或逻辑缺陷。
    - **[Issue #2081: 订阅](https://github.com/netease-youdao/LobsterAI/issues/2081):** 用户对订阅积分月底清零的政策表达了强烈不满。这虽然是商业模式问题，但会直接影响用户满意度和留存率，建议产品团队关注。

## 5. Bug 与稳定性

今日汇报了数个关键 Bug，部分已有对应的修复 PR。

| 严重程度 | Issue / PR 链接 | 问题描述 | 是否有 Fix PR |
| :--- | :--- | :--- | :--- |
| **高** | [Issue #2079](https://github.com/netease-youdao/LobsterAI/issues/2079) | **执行结果窗口滚动到顶端会假死**。这是一个能稳定复现的UI冻结问题，严重影响用户体验。 | 暂无 |
| **高** | [Issue #2121](https://github.com/netease-youdao/LobsterAI/issues/2121) | **Claw重复输出文字**，可能导致 Token 浪费。 | 暂无 |
| **中** | [Issue #1388](https://github.com/netease-youdao/LobsterAI/issues/1388) | **邮箱配置-测试连通性** 后一直无响应。 | 无 |
| **低** | [Issue #1386](https://github.com/netease-youdao/LobsterAI/issues/1386) | **长对话分享截图** 存在内容不全的问题。 | 无 |
| **低** | [Issue #1389](https://github.com/netease-youdao/LobsterAI/issues/1389) | **英文界面下，语言选择项仍显示中文**，国际化问题。 | 无 |
| **修复中** | [PR #2220](https://github.com/netease-youdao/LobsterAI/pull/2220) | 修复了**定时任务运行后，后续对话历史丢失**的问题。 | 已修复 |
| **修复中** | [PR #2227](https://github.com/netease-youdao/LobsterAI/pull/2227) | 修复了**OpenClaw Agent 引导文件加载错误**的问题，导致 Agent 个性丢失。 | 已修复 |

## 6. 功能请求与路线图信号

今日的 Issue 和 PR 暗示了以下可能的路线图方向：

- **任务编排与持久化 (高可能性):** Issue #2120 提出的“预输入任务”建议，与 PR [#2220](https://github.com/netease-youdao/LobsterAI/pull/2220) 中关于“定时任务运行后对话历史维护”的修复相呼应。这表明项目团队正在**强化任务的连续性和状态管理**，未来可能引入更高级的任务队列和编排功能。
- **Agent 生态扩展 (中等可能性):** Issue #2131 关于 Hermes Agent 的问询，以及近期对 OpenClaw 插件架构的大量修复，表明团队在**围绕 OpenClaw 构建更丰富的 Agent 生态**，未来可能会支持更多第三方 Agent 框架或协议。
- **UI 与用户体验优化 (高可能性):** 来自 Issue #2120 和 Issue #2121 的反馈（UI 布局、Token 浪费可视化），以及今日多个关于 Cowork 对话 UI (PR #2222, #2223) 的修复与回滚，都指向**用户体验**是当前和接下来的优化重点。

## 7. 用户反馈摘要

从今日的 Issue 评论中，可以提炼出以下核心用户痛点与场景：

- **痛点:**
    - **积分/订阅策略:** 用户对积分月度清零表示强烈不满，认为是“搞笑的”政策，直接影响了“价值感知”。
    - **Token 浪费与不确定性:** 用户怀疑 Claw 的重复输出消耗了不必要的 Token，对成本敏感且对 Agent 行为缺乏透明度感到困扰。
    - **稳定性:** 执行窗口假死问题严重影响核心工作流。
- **使用场景:**
    - **数据采集与监控:** 有用户使用 Claw 来运行数据获取脚本进行**长时间监控**，并遇到了任务被“terminated”的问题，这表明了 Claw 在**后台任务连续执行**方面的需求。
    - **多任务并行的开发流程:** 用户期望在运行时能预输入下一个任务，体现了**复杂工作流**和**开发效率**提升的需求。

## 8. 待处理积压

以下为长期未得到有效响应的关键 Issue，建议维护者关注，根据情况更新状态、分配负责人或给出评论。

- **[Issue #1390: 定时任务无法更新（偶现）](https://github.com/netease-youdao/LobsterAI/issues/1390)**
    - 创建于 **2026-04-03**，已过去近 3 个月。这是一个影响核心功能的严重 Bug，虽为偶现，但可能导致用户配置丢失或无法正常使用定时任务功能。

- **[Issue #1388: 邮箱配置-测试连通性一直没反应](https://github.com/netease-youdao/LobsterAI/issues/1388)**
    - 创建于 **2026-04-03**。该问题导致邮箱配置流程卡死，且需要强制重启应用，属于影响用户配置体验的中等严重 Bug。

---
**分析师总结:** 今日项目处于发布前的冲刺阶段，展示了高效的开发和修复能力。然而，一些长期存在的 Bug（如定时任务更新、邮箱配置无响应）以及与用户切身利益相关的订阅政策问题，若不能得到及时解决，可能影响社区长期健康度。建议在专注于新功能的同时，安排资源对积压的稳定性问题进行一次集中清理。

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

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，根据您提供的 CoPaw 项目数据，我已为您生成 2026-06-30 的项目动态日报。

---

# CoPaw 项目日报 | 2026-06-30

## 今日速览

项目今日活跃度**极高**。24小时内实现了50条PR的密集更新，其中33条已合并/关闭，显示出强劲的开发动能。社区讨论围绕 **v2.0.0-beta 发布准备**、**性能优化**与**多平台体验改进**展开。一个值得关注的健康信号是，即使在PR高并发期，仍有15条新Issue被创建，表明用户参与度并未因开发迭代而冷却。总体而言，项目正处于版本迭代前夜，状态活跃且稳定。

## 项目进展

今日共有 **33 个 PR 被合并/关闭**，标志着多个功能模块的显著推进。其中最值得关注的进展包括：

- **前端质量飞跃**：由开发者 `hanson-hex` 发起的一系列前端单元测试 PR (#5409, #5434, #5438) 相继被合并，覆盖了 `Stores`, `Hooks`, `Control pages`, `Agent hooks` 及 `Inbox + API` 模块，总计贡献了超过 426 个测试用例。这显著提升了前端代码的健壮性和可维护性。
- **核心稳定性修复**：
    - **AgentScope 版本升级**：PR #5576 已合并，将核心依赖 `agentscope` 升级至 `2.0.3` 版本。
    - **心跳任务优化**：针对 `Bug #5539`，PR #5557 已合并，将心跳任务执行超时时间从硬编码的120秒改为可配置 (`timeoutSeconds`)，解决了复杂心跳任务被意外中断的问题。
    - **通道消息处理**：PR #5567 (未列出, 从工单 #5554 推断) 和 PR #5548 修复了企业微信频道文件处理和通道请求中 `agent_id` 继承的问题，提升了多频道对接的可靠性。
    - **Windows 路径问题修复**：PR #5635 已合并，修复了Windows系统下图片/文件上传后路径转换失败的问题。
- **新功能推进**：
    - **子Agent事件驱动生命周期**：PR #5637 和 #5633 引入了事件驱动的后台子Agent生命周期，替代了轮询模式，允许子Agent在后台独立运行并主动唤醒父Agent，为复杂的多Agent协作场景提供了更高效的基础。

## 社区热点

1.  **优化空间巨大：DeepSeek 前缀缓存命中率（#3891）**
    - 链接：[Issue #3891](https://github.com/agentscope-ai/QwenPaw/issues/3891)
    - 热度：5条评论，获得1个👍赞。
    - 分析：该Issue虽创建于4月，但近期仍有讨论，反映了用户对成本的敏感。用户指出接入DeepSeek模型时，前缀缓存命中率仅95%，导致约5%的请求产生数倍的成本差异。这不仅仅是功能请求，更是一个强烈的**用户经济诉求**。讨论的持续表明，社区对模型API成本的优化有极高的期待，项目方应考虑将此纳入成本优化路线的优先级。

2.  **新版本的体验验证：QwenPaw v2.0.0-beta.1 安装验证（#5571）**
    - 链接：[Issue #5571](https://github.com/agentscope-ai/QwenPaw/issues/5571)
    - 热度：由 `github-actions[bot]` 创建，是正式发布流程的一部分。
    - 分析：这是一个自动化发布的检查项，标志着 v2.0.0-beta 版本已进入最后的**安装验证阶段**。虽然本身不是用户讨论，但它代表了项目最关键的最新动态。该Issue的完成状态将直接影响新版本的发布节奏，是整个社区的焦点。

3.  **UI/UX 优化讨论：工具调用结果卡片的计数错误（#5624, #5626）**
    - 链接：[Issue #5624](https://github.com/agentscope-ai/QwenPaw/issues/5624)
    - 分析：该Bug由用户 `Cederys` 详细报告并快速关闭。虽然已修复，但其评论区的高活跃度反映了用户对前端细节体验的重视。这个看似微小的显示错误，严重干扰了用户对工具执行结果（如 `glob_search` 搜索到241个文件）的直观理解，表明UI的准确性对用户信任至关重要。

## Bug 与稳定性

今日报告的 Bug 严重程度总体可控，但修复效率极高。

| 严重程度 | Bug 描述 | Issue 链接 | 修复状态 |
| :--- | :--- | :--- | :--- |
| **高** | MiniMax-M3 安全审核错误被缓存，导致后续所有视觉请求被错误剥离图片。 | [#5505](https://github.com/agentscope-ai/QwenPaw/issues/5505) | **已关闭** |
| **中** | 工具调用结果卡片标题计数始终显示为1（如 `glob_search`）。 | [#5624, #5626](https://github.com/agentscope-ai/QwenPaw/issues/5624) | **已关闭** |
| **中** | 企业微信发送文件后Bot无响应，因频道重启导致处理中断。 | [#5554](https://github.com/agentscope-ai/QwenPaw/issues/5554) | **已关闭** |
| **中** | 心跳任务因硬编码的120秒超时导致执行失败。 | [#5539](https://github.com/agentscope-ai/QwenPaw/issues/5539) | **已修复** (PR #5557 已合并) |
| **低** | Remote SSH 插件依赖安装存在循环及旧进程残留。 | [#5550](https://github.com/agentscope-ai/QwenPaw/issues/5550) | **已关闭** |
| **低** | 函数声明中 `type: null` 导致部分第三方模型处理失败。 | [#5543](https://github.com/agentscope-ai/QwenPaw/issues/5543) | **已关闭** |

今日社区报告的严重Bug数量较少，且6个Bug中5个已被关闭或修复，展现了开发团队对稳定性的快速响应能力。

## 功能请求与路线图信号

今日接收到多项关于功能增强的请求，结合已有PR，以下方向最可能被纳入下一版本规划：

*   **高优先级信号**：
    *   **纯文本模型的视觉Fallback**（#5615）：用户强烈期望当配置纯文本模型时，能自动调用备用视觉模型处理图片。这触及了模型配置的核心痛点，社区呼声很高。
    *   **自定义模型协议支持**（#5609）：用户希望支持非标准 `v1/chat/completions` 的API端点（如图片生成），以满足更多免费或非标准模型的需求。这拓宽了QwenPaw的模型生态。
    *   **对话记录断点保存**（#5579）：用户遭遇Agent执行重启命令或服务中断后对话丢失的问题，请求增加自动保存机制。这是一个对用户体验影响极大的功能，安全性要求较高。

*   **中优先级信号**：
    *   **Windows系统托盘图标**（#5622）：请求增加Windows系统托盘图标支持，让应用可后台运行。
    *   **钉钉通道流式输出优化**（#5603）：用户反馈钉钉频道卡片流式输出速度过慢，影响日常使用效率。
    *   **Telegram自定义BaseURL**（#5630）：支持Telegram频道的自定义BaseURL，以满足特定网络环境下的代理需求。

*   **已进入开发阶段**：
    *   **子Agent事件驱动生命周期**（PR #5637, #5633）：此功能已由社区贡献者 `splash-li` 提交PR，方向完全契合社区对更高效Agent协作的期待。
    *   **GUI自动化 - Computer Use**（PR #5187）：Windows桌面GUI自动化功能已有PR在跟进，进展顺利。

## 用户反馈摘要

从今日的Issue评论中可以提炼出以下真实的用户声音：

*   **对成本敏感**：用户 `LI-VIOLIENT` 对DeepSeek模型95%的缓存命中率表示担忧，明确指出未命中带来的额外计费成本是其核心痛点。
*   **对UI/UX细节高度关注**：用户 `Cederys` 报告了工具卡片计数显示错误，并对此类影响直观体验的问题非常敏感。用户 `gy23rm` 则报告了UI弹出层选中背景不明显。这表明用户期望项目不仅功能强大，更要“用起来舒服”。
*   **不同场景下的性能要求**：用户 `tecgic` 反馈了钉钉通道的流式输出过慢问题，而用户 `vipcys001-bot` 则抱怨新版“越来越卡顿”。这表明不同环境下的性能优化需要持续进行。
*   **对新功能的渴望**：用户 `KumaKorin` 和 `justsavo` 分别提出了对Telegram自定义BaseURL和Windows系统托盘的支持，显示了用户希望QwenPaw能更好地融入其个人工作流程。

## 待处理积压

以下为可能被社区或维护者忽略、但值得关注的议题：

*   **长期待响应的功能请求**：
    *   **#2495 - MCP工具列表展示**：该功能请求发布于3月底，至今已3个月未关闭，但社区讨论仍在继续。用户希望在配置MCP后，能直观看到其包含了哪些工具。虽然难度不高，但对插件生态的易用性至关重要。
    *   **#5609 - 自定义模型协议**：今日新的功能请求，但触及非标准API兼容性问题。这是QwenPaw能否成为“万能模型适配器”的关键能力，不应被忽视。
    *   **#5579 - 对话记录断点保存**：今日新提出的请求，但其关注的核心是数据安全与体验连续性，属于基础能力，建议纳入长期规划。

*   **未分配或状态不明确的高价值PR**：
    *   **#5221 - AgentScope中间件注册**：已开放两周，无新评论或更新。此PR决定了插件系统与核心循环的集成方式，对生态发展意义重大，建议维护者评估并推动进程。
    *   **#5187 - Windows GUI自动化**：同样已开放两周，但更新频繁。这是QwenPaw扩展能力边界的重要尝试，建议维护者持续关注，并在社区中发起讨论，明确其范围和规划。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，根据您提供的 ZeroClaw 项目 GitHub 数据，现呈上 2026-06-30 的项目动态日报。

---

# ZeroClaw 项目动态日报 | 2026-06-30

## 1. 今日速览

今日 ZeroClaw 项目活跃度极高，社区讨论与代码提交均十分密集。过去24小时内，项目有 **50 条 Issue 更新**（其中 43 条仍处于活跃状态）和 **50 条 PR 更新**（35 条待合并），显示出强劲的开发动力。社区讨论焦点集中在 **MCP/原生工具在推理模型中的可用性问题** 和 **运行时策略与安全性** 上。尽管无新版本发布，但多个关键修复和功能 PR 已合并，项目整体处于高速迭代状态，健康度良好。

## 2. 版本发布

今日无新版本发布。

## 3. 项目进展

今日有 15 个 PR 已合并/关闭，推进了多个关键领域的修复和功能增强：

- **Provider 兼容性修复**: PR #8512 / #8510 修复了 OpenAI 兼容 API 中 `tool_calls` 请求的 `content` 字段格式问题，避免了与严格模式后端的兼容性问题。这是一个重要的 bug 修复，提升了 ZeroClaw 与不同后端（如 OpenRouter, Azure OpenAI, Copilot）的互操作性。
- **MCP 工具稳定性**: PR #8403 (在 #8508 中被引用) 和 #8508 的提交，为 MCP 资源/提示功能奠定了基础。同时，PR #8514 修复了 `aardvark-sys` 库中 `LibraryNotFound` 错误的链式传递，提高了底层库的健壮性。
- **渠道与国际化**: PR #8511 解决了主分支因语义合并冲突导致的 CI 编译失败问题。PR #8513 为聊天工具栏按钮增加了七种语言的国际化支持，提升了多语言用户体验。
- **CI 与基础设施**: PR #8129 为 PR 门禁增加了 `cargo-audit` 步骤，用于自动扫描安全依赖项，增强了代码仓库的安全性。PR #8494 清除了主分支上的一个意外 gitlink，修复了 CI 流程。
- **工具行为优化**: PR #8497 修复了 Windows 上路径处理可能触发的 Clippy 警告，提升代码质量。
- **测试覆盖**: PR #8492 增强了 A2A 安全闸门的测试覆盖，确保安全机制的有效性。

**项目向前迈进的标志**：零散的兼容性修复和 CI 强化工作是项目稳定性的基石；而 MCP 资源/提示功能的铺垫工作，则为后续更强大的智能体能力打下了基础。

## 4. 社区热点

以下 Issue/PR 是今日讨论的焦点：

1.  **Issue #5600 - [Bug]: Use kimi-code provider in streaming chat call tools, provider API reports an error** (评论: 11)
    - **链接**: [Issue #5600](https://github.com/zeroclaw-labs/zeroclaw/issues/5600)
    - **分析**: 一个自4月10日就存在的、风险级别为 `high` 的 S1 级 Bug。用户在调用 `kimi-code` provider 进行流式聊天时遇到 API 错误。该问题已有 11 条评论，社区讨论热烈，是当前最受关注的稳定性问题。

2.  **Issue #8054 - [Bug]: System prompt tool-availability should match per-turn effective tools across all entry points** (评论: 9)
    - **链接**: [Issue #8054](https://github.com/zeroclaw-labs/zeroclaw/issues/8054)
    - **分析**: 讨论非常活跃的核心问题。它揭示了系统提示中工具可用性信息与各入口点（如通道、网关、WebSocket）实际可用工具不匹配的深层 Bug。这属于架构层面的问题，直接导致推理模型被告知“无工具可用”，阻塞了关键工作流。社区对此高度关注，并已有关联的 fix PR (#8053, #8496)。

**分析**: 社区热点清晰地指向了 **工具（Tools）** 与 **Provider/模型** 之间的交互问题，特别是对于支持推理/逻辑的模型。这表明用户正在大规模使用 ZeroClaw 的复杂功能，并对模型与工具的协同工作提出了更高要求。

## 5. Bug 与稳定性

今日报告和关注的 Bug 按严重程度排列如下：

| 严重级别 | Issue/PR | 摘要 | 修复状态 |
|---|---|---|---|
| S1 - 工作流阻塞 | #5600 | 使用 `kimi-code` provider 调用工具时 API 报错 | 待修复，社区正在讨论 |
| S1 - 工作流阻塞 | #6891 | 通过 Web 编辑定时任务时 API 报 422 错误 | 待修复 |
| S2 - 行为降级 | #8410 | 通道任务缺少首页的“无回复”意图，导致任务静默时仍发送无意义回复 | 待修复（新提出的问题） |
| S2 - 行为降级 | #7800 | ZeroCode (TUI) 的帮助提示和键绑定混乱（特别是 macOS） | 待修复 |
| P1 - 高优先级 | #7756 | 原生/MCP 工具在 OpenAI 和 Anthropic 推理模型上不可用 | 有相关的 Fix PR (#8053) |
| P2 - 中优先级 | #6157 | Nextcloud Talk 频道使用了错误的 API 路径调用机器人消息 | 待修复 |
| P2 - 中优先级 | #2128 | Cron 和心跳任务仍然会发送文字 `NO_REPLY` 文本 | 待修复（已有关闭的相同 issue #2128，但问题可能复发） |

## 6. 功能请求与路线图信号

今日的核心功能需求讨论，预示着项目未来的演进方向：

1.  **实时性与可观测性强化**:
    - **Issue #6642 / #6641**: 社区（由 @JordanTheJet 主导）在持续推动 OpenTelemetry (OTel) 集成的深化，包括在 LLM 调用 Span 中捕获完整的输入/输出，以及为每次 “Turn” 创建独立的 OTel Trace。这表明对监控、调试和成本核算的需求日益增长。
    - **Issue #8462**: 用户提出为 OTel 中的 LLM 和工具内容添加 **运行时策略**，这暗示了社区对数据隐私和内容安全有更高的要求。

2.  **插件生态与分发机制**:
    - **Issue #7497 (RFC)**: 提出用 **OCI 兼容的容器注册表** 作为 WASM 插件的存储和分发机制。这表明项目正在认真考虑构建一个安全、可扩展的插件生态系统，并可能引入供应链验证（如 Cosign）。

3.  **渠道与用户体验扩展**:
    - **Issue #8046**: 请求为 Telegram 频道增加 **Webhook 模式** 作为目前轮询模式的补充。这反映了用户在不同网络环境下部署的差异化需求。
    - **Issue #8170 (RFC)**: 提议在 Web 控制台内添加 **“应用内升级”** 功能，通过 `zeroclaw update` 命令实现。与之对应的 PR #8173 今日仍有更新，说明这个功能很可能在 v0.8.3 或后续版本中实现。
    - **Issue #6427**: 用户建议添加 **Twilio SMS 频道**，以实现纯粹的短信交互，这是对现有 WhatsApp 支持的有力补充，覆盖更广泛的用户触达场景。

**信号**: 项目正从基础的“能用”向“好用”和“生态化”发展。**插件系统（WASM + OCI）** 和 **深度可观测性** 是未来路线图中非常重要的投资方向。

## 7. 用户反馈摘要

从今日的 Issue 评论中，可以提炼出一些关键的用户声音：

- **痛点 1：配置与使用冲突**。Issue #8054 和 #7756 的讨论显示，用户对于某些模型“有工具却用不了”感到困惑。这不仅仅是 Bug，更是一种架构上的不一致，破坏了用户对 Agent 能力的预期。
- **痛点 2：文档与提示的误导性**。Issue #7800 明确指出 ZeroCode TUI 的键绑定提示“具有误导性”，尤其是在 macOS 上。这直接影响了新用户的入门体验。
- **满意点/期待**：Issue #6642 中，用户 @alexandme 提供了一个在个人 fork 中完成的开源实现，并愿意向上游贡献。这种正向的社区协作模式表明核心贡献者对项目方向和技术实现充满热情与信心。
- **真实使用场景**：Issue #8379 (已关闭) 提出了一个非常细致的 WhatsApp 群组交互场景：希望 Agent 在未被直接 @ 时，只“被动”收集上下文而不主动推理，以避免群聊中不必要的回复。

## 8. 待处理积压

以下是一些长期未响应或需要维护者关注的重要 Issue/PR：

1.  **Issue #6074 - audit: track 153 commits lost in bulk revert** (创建于 2026-04-24)
    - **链接**: [Issue #6074](https://github.com/zeroclaw-labs/zeroclaw/issues/6074)
    - **重要性**: **高**。这是一个审计跟踪任务，旨在追踪被批量回滚的 153 个提交中丢失的关键修复和功能。虽然标记为 `in-progress`，但涉及大量工作，需要持续的维护者关注，以确保没有重要的代码改动被永久丢失。

2.  **Issue #2467 - [Feature]: Webhook transforms** (创建于 2026-03-02)
    - **链接**: [Issue #2467](https://github.com/zeroclaw-labs/zeroclaw/issues/2467)
    - **重要性**: **中**。一个近四个月前的功能请求，用于增强 Webhook 系统的灵活性。虽然被标记为 `priority:p2`，但其 `Domain:Security` 和 `Domain:Architecture` 标签表明它对系统的可扩展性和安全性有一定影响，应纳入下次路线图讨论。

3.  **Issue #6754 - [Feature]: ACP bridge auto-pairing should not depend on a one-time-use code** (创建于 2026-05-18)
    - **链接**: [Issue #6754](https://github.com/zeroclaw-labs/zeroclaw/issues/6754)
    - **重要性**: **中**。该 issue 指出 ACP 桥接的自动配对依赖于一次性代码，操作上存在脆弱性。虽然目前只有一条评论，但对于有生产环境或需要稳定长期连接的运维人员来说是个痛点。

</details>

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*