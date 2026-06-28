# OpenClaw 生态日报 2026-06-28

> Issues: 500 | PRs: 500 | 覆盖项目: 13 个 | 生成时间: 2026-06-28 03:43 UTC

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

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，我将根据您提供的 OpenClaw 项目 GitHub 数据，生成一份结构化的项目动态日报。

---

## OpenClaw 项目动态日报 — 2026-06-28

### 1. 今日速览

项目今日活跃度极高，展现了社区大量的使用与反馈。过去24小时内，**Issues 和 PR 的更新数量均达到500条**，但绝大多数为新提交或活跃的 Issue（487条/97.4%）和待合并的 PR（459条/91.8%），合并率（~8%）较低，这表明项目处于一个 **“高输入、低输出”** 的瓶颈期。维护者面临巨大的审阅压力。**无新版本发布**，大量的 P0/P1 级内存泄漏、会话状态损坏等严重 Bug 和历史遗留的功能请求（如 #91588、#65161）仍在等待处理，项目整体处于 **“用得多，修得慢”** 的健康度预警状态。

---

### 3. 项目进展

今日有 41 条 PR 被合并或关闭，以下是其中较为关键的贡献：

- **任务系统健壮性提升**：PR [#97352](https://github.com/openclaw/openclaw/issues/97352) `fix(tasks): harden ACP task cancellation` 修复了 ACP 任务取消可能导致重复任务行和 CLI 取消失败的问题，提升了任务管理的可靠性。
- **群聊管理功能增强**：PR [#69297](https://github.com/openclaw/openclaw/issues/69297) `fix(whatsapp): Add group admin privacy controls` 为 WhatsApp 频道增加了群组管理员覆盖权限，允许配置特定管理员绕过 @提及限制。
- **会话存储重构推进**：PR [#96625](https://github.com/openclaw/openclaw/issues/96625) `refactor: flip sessions and transcripts to sqlite storage` 是一个重量级重构，旨在将核心会话存储从 JSON 文件迁移到 SQLite，以解决性能瓶颈和数据丢失问题。此 PR 仍在等待作者更新，是项目架构演进的关键一步。
- **AI 模型兼容性修复**：PR [#97355](https://github.com/openclaw/openclaw/issues/97355) `fix(ollama): keep OpenAI-compatible tool_call arguments as strings` 修复了使用 Ollama Cloud 模型（通过 OpenAI 兼容接口）时，由于 `tool_call` 参数类型问题导致的 Agent 调用失败。

---

### 4. 社区热点

今日讨论最热烈的 Issue 反映了用户在 **会话上下文管理** 和 **模型幻觉** 方面的核心痛点：

1.  **[#58450] Agent 承诺后续跟进却无实际行动**：评论数 15，获得了社区广泛共鸣。用户抱怨 Agent 经常回复“我会检查并回来跟进”，但实际上并未启动任何后台任务或子代理。这揭示了 Agent 的 **“假承诺”** 行为，严重损害了用户信任。
    - 链接：https://github.com/openclaw/openclaw/issues/58450

2.  **[#92201] 流式推理签名在重放时间歇性无效**：评论数 15。这是一个严重且难缠的 Bug，用户在代理重放时，Anthropic 的 `thinking` 签名会失效，且由于错误信息被泛化，恢复机制无法生效。这直接导致 **会话回复丢失**。
    - 链接：https://github.com/openclaw/openclaw/issues/92201

3.  **[#91588] 关键网关内存泄漏 (P0)**：评论数 14，标记为 P0。用户报告网关进程内存从 350MB 持续增长到 15.5GB，最终导致 OOM 崩溃和重启循环。这是当前最严重的稳定性问题之一，影响了所有长期运行 Gateway 的用户。
    - 链接：https://github.com/openclaw/openclaw/issues/91588

---

### 5. Bug 与稳定性

今日报告的 Bug 中，**内存泄漏** 和 **会话状态损坏** 是两大核心主题，严重性极高。

**P0 级 (紧急)**:
- **Gateway 内存泄漏**：[#91588](https://github.com/openclaw/openclaw/issues/91588) - RSS 从 350MB 增长至 15.5GB，导致 OOM 崩溃。**（尚未修复）**

**P1 级 (高严重性)**:
- **心跳隔离模式回归**：[#65161](https://github.com/openclaw/openclaw/issues/65161) - 心跳节奏卡顿，`exec-event` 误报为心跳，上下文无法释放。
- **编码 Agent 无法完成任务**：[#62505](https://github.com/openclaw/openclaw/issues/62505) - 用户反馈原本工作的编码 Agent 突然停滞，仅输出模糊状态更新。
- **子代理中止锁释放失败**：[#95833](https://github.com/openclaw/openclaw/issues/95833) - 超时中止后未释放 `jsonl.lock` 文件，导致会话永久不可用。**(今日已关闭)**。
- **容器化运行的堆不释放**：[#95915](https://github.com/openclaw/openclaw/issues/95915) - 嵌入运行中止后，分配的内存不释放，导致内存逐渐耗尽。**(今日已关闭)**。
- **溢出恢复导致消息重复**：[#66443](https://github.com/openclaw/openclaw/issues/66443) - 上下文溢出恢复机制会复制用户消息，加速 Token 消耗和日志膨胀。
- **OpenClaw 状态显示异常**：[#57256](https://github.com/openclaw/openclaw/issues/57256) - `openclaw status --deep` 报告记忆模块不可用，但实际网关插件运行正常，导致诊断困扰。
- **CLI 后端绕过问题**：[#57326](https://github.com/openclaw/openclaw/issues/57326) - 部分辅助路径仍然绕过正确的 CLI 分发逻辑，影响 CLI 后端模型的正确调用。

**P2 级 (中等严重性)**:
- **会话上下文膨胀**：[#67419](https://github.com/openclaw/openclaw/issues/67419) - 每个新会话都会注入大量重复的引导文件，浪费 20-30% 的 Token。
- **备份命令竞态条件**：[#67417](https://github.com/openclaw/openclaw/issues/67417) - `openclaw backup create` 在备份过程中若会话文件被清理，会导致 ENOENT 错误。

---

### 6. 功能请求与路线图信号

今日的功能请求呈现出对 **细粒度权限控制**、**多层记忆架构** 和 **工具可观测性** 的强烈需求。

- **可执行的 Agent 生命周期钩子**：[#43454](https://github.com/openclaw/openclaw/issues/43454) 请求在子代理完成、工具调用等节点触发钩子。这是一个对自动化工作流至关重要的功能，如果实现，将极大提升 OpenClaw 的扩展性。
- **Outbound 策略强制执行**：[#56349](https://github.com/openclaw/openclaw/issues/56349) 要求对 Agent 的所有出站消息进行统一的预发送校验。这反映了用户对 Agent “胡言乱语”或“越权操作”的担忧，是安全性的核心需求。
- **多槽位记忆架构**：[#60572](https://github.com/openclaw/openclaw/issues/60572) 建议将单一记忆槽拆分为多个专用记忆槽，以便同时使用不同记忆提供者（如对话记忆+知识图谱）。这是对更复杂、更智能记忆能力的探索。
- **多索引嵌入模型**：[#63990](https://github.com/openclaw/openclaw/issues/63990) 支持多个嵌入模型并提供故障转移，避免混合向量空间导致语义错误，是构建生产级检索系统的关键。
- **远程 Reranker 端点**：[#64438](https://github.com/openclaw/openclaw/issues/64438) 需求与前述记忆功能一脉相承，旨在引入外部 Reranker 服务提升检索精度。
- **敏感数据脱敏**：[#64046](https://github.com/openclaw/openclaw/issues/64046) 特别指出 `openclaw.json` 等配置文件中的 API Key 以明文存储，这在安全性要求较高的场景下是重大隐患。

**与已有 PR 关联的信号**：多篇关于记忆架构的 PR（如 #63990 #60572）和相关讨论暗示，**记忆系统的改造** 是下一版本可能聚焦的路线图方向。

---

### 7. 用户反馈摘要

- **核心痛点：Agent“失联”与“假承诺”**：用户多次反馈 Agent 回复后无后续行动（`#58450`），或在长对话中表现变差（`#62505`），反映出 Agent 的执行意图跟踪和上下文管理存在缺陷。
- **稳定性是最大困扰**：内存泄漏（`#91588`、`#54155`）、配置解析失败（`#53628`）、备份工具 Bug（`#67417`）等问题让用户频繁重启或遭遇数据丢失，严重影响了日常使用的信心。
- **对新功能的态度**：社区对多智能体协作（`#35203`）、记忆架构增强（`#60572`）等功能需求热烈，但普遍希望 **先解决稳定性问题**。许多功能请求帖中，评论都指向了“请先修复现有的严重 Bug”。
- **中文社区的反馈**：用户 `buggiant-coder` 在 Issue `#51429` 中抱怨代码中硬编码了工作目录 `/Users/wangtao`，并嘲讽其被合并发布。这不仅是一个代码质量 Bug，更反映了对 **贡献审核流程松懈** 的不满。

---

### 8. 待处理积压

以下 Issue/PR 已停滞或等待维护者关注，对项目健康和社区信心影响较大：

- **P0/P1 级关键 Bug 待修复**：
    - [#91588](https://github.com/openclaw/openclaw/issues/91588): Gateway 内存泄漏 (P0)。
    - [#65161](https://github.com/openclaw/openclaw/issues/65161): 心跳隔离模式回归 (P1)。
    - [#62505](https://github.com/openclaw/openclaw/issues/62505): 编码 Agent 功能停滞 (P1)。
    - [#57326](https://github.com/openclaw/openclaw/issues/57326): CLI 后端绕过问题 (P1)。

- **长期未结、等待决策的功能请求**：
    - [#35203](https://github.com/openclaw/openclaw/issues/35203): 多 Agent 协作增强 **[RFC]**，已开放超过3个月，是社区讨论已久的重大功能。
    - [#60572](https://github.com/openclaw/openclaw/issues/60572): 多槽位记忆架构，已开放近3个月。

- **等待作者或维护者回应的 PR** (标记为 `status: ⏳ waiting on author` 或 `status: 📣 needs proof`)：
    - [#69346](https://github.com/openclaw/openclaw/issues/69346): 嵌入运行环境配置错误诊断。
    - [#69059](https://github.com/openclaw/openclaw/issues/69059): Windows 平台 sqlite-vec 加载修复。
    - [#68967](https://github.com/openclaw/openclaw/issues/68967): Google Chat 线程绑定功能。
    - [#67820](https://github.com/openclaw/openclaw/issues/67820): WhatsApp QR 复用与运行时警告保留。
    - **[PR #96625](https://github.com/openclaw/openclaw/issues/96625)**: 会话存储迁移至 SQLite，此 PR 能否被合并，将是评估项目架构演进决心的关键信号。
    - **[PR #14432](https://github.com/openclaw/openclaw/issues/14432)**: 系统提示中添加后台子代理指南，已停滞超过4个月，意味着这个简单的文档改进没有被优先处理。

**总结**：OpenClaw 社区活跃，用户热情高，但项目当前正被大量高优先级的 **稳定性 Bug** 所困扰。维护团队面临巨大的 PR 审查和 Bug 修复压力。当前最紧迫的任务应是集中资源解决内存泄漏和会话状态损坏等 P0/P1 级问题，否则长期将损害用户基数和项目口碑。

---

## 横向生态对比

好的，作为AI智能体与个人AI助手领域开源项目分析师，我将基于您提供的各项目动态日报，生成一份横向对比分析报告。

---

## 2026-06-28 个人AI智能体开源生态横向对比分析报告

### 1. 生态全景

今日，个人AI助手/自主智能体开源生态呈现出 **“核心项目陷入瓶颈，新兴项目加速追赶”** 的二元态势。**OpenClaw** 作为最受瞩目的参照项目，正受到日益增长的用户量带来的稳定性冲击，其“高输入、低产出”的状态是整个生态成熟度的一个预警信号。与此同时，**NanoBot、Hermes Agent、IronClaw** 等一批项目展现出了更快的迭代速度和更高的社区响应效率，尤其是在 **功能创新（如Agent协作、结构化审批流）与稳定性加固** 方面取得了扎实进展。这表明生态正从单一项目主导的“野蛮生长”，向多项目竞合、聚焦工程化与安全性的“精细化发展”阶段过渡。**安全性、跨平台兼容性、多Agent协作** 已成为所有项目共同关注的战略高地。

### 2. 各项目活跃度对比

| 项目名称 | 24h新/活跃Issue | 24h PR活跃数 | 今日发布 | 合并/关闭PR数 | **核心健康度评估** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 487+ | ~500 | 无 | ~41 | **预警**：社区活跃但维护者严重过载，P0/P1级Bug积压，修复速度远低于问题产生速度 |
| **NanoBot** | 1 | ~10 | 无 | 18 | **良好**：Bug修复与功能开发并行，维护者响应积极，社区贡献转化率高 |
| **Hermes Agent** | 50 | 50 | 无 | 众多 | **健康**：社区活跃，维护效率高，核心稳定性与平台兼容性修复取得显著进展 |
| **PicoClaw** | 2 | 2 | 无 | 2 | **稳定**：关键功能（Agent协作）成功落地，处于功能迭代与稳定性并重阶段 |
| **NanoClaw** | 2 | 8 | 无 | 0 | **观望**：虽然活动量大，但核心是大量待合并PR与未修复的严重Bug，存在开发与交付脱节风险 |
| **NullClaw** | 1 | 1 | 无 | 0 | **低活跃**：项目整体活跃度较低，核心构建问题长期未解决，存在用户流失风险 |
| **IronClaw** | 8+ (大量关闭) | 27+ | 无 | >10 | **健康/高活跃**：核心功能“能力策略”取得里程碑进展，开发效率高，项目处于功能突破期 |
| **LobsterAI** | 2 | 2 | 无 | 7 | **修复密集期**：集中清理历史技术债务，但新报告的高影响度Bug需警惕，项目度过蛰伏期 |
| **CoPaw** | 3 | 3 | 无 | 1 | **良好**：社区贡献活跃，但核心数据丢失Bug和模型兼容性问题是潜在风险 |
| **ZeroClaw** | 48 | 50 | 无 | 8 | **高活跃/规划期**：为版本迭代进行密集的规划与开发，安全架构和运行时稳定性是讨论焦点 |
| **TinyClaw** | 0 | 0 | 无 | 0 | **沉寂**：无任何活动 |
| **Moltis** | 1 | 2 | 无 | 0 | **低活跃**：项目活动量低，但专注解决小模型兼容性这一特定方向，有独特价值 |
| **ZeptoClaw** | 0 | 0 | 无 | 0 | **沉寂**：无任何活动 |

### 3. OpenClaw 在生态中的定位

- **优势**：**社区规模最大，品牌号召力强**。作为核心参照项目，其Issue和PR数量远超其他项目，用户基础和开发者生态是最大资产。其功能覆盖最全，是“全能型”选手。
- **劣势**：**“巨人症”初显**。过高的社区活跃度远超维护者处理能力，导致严重的PR积压和关键Bug修复滞后，正从“创新驱动”转向“维护驱动”，对用户体验和口碑构成实质威胁。
- **技术路线**：其庞大而灵活的架构赋予了极高的可扩展性，但也带来了复杂的配置和潜在的性能瓶颈。与其相比，NanoBot等更轻量的项目选择做减法，以快速迭代和易用性取胜。
- **社区对比**：从健康度看，OpenClaw的社区**量大但质不优**；而Hermes Agent、ZeroClaw等项目虽然规模较小，但**贡献者与维护者的互动更高效，Bug修复和功能落地的闭环速度更快**。

### 4. 共同关注的技术方向

1.  **Agent协作与任务编排**：**PicoClaw**（合并了Agent协作总线）、**OpenClaw**（#35203多Agent增强RFC）和**NanoBot**（spawn工具增强）均在不同层面探索Agent互联。这说明**从单Agent走向多Agent协同**是行业共识，是下一阶段能力竞争的制高点。
2.  **安全与权限控制**：**IronClaw**（能力策略里程碑）、**NanoBot**（`exec.allowPatterns`绕过修复）、**ZeroClaw**（`mcp_bundles`配置失效、供应链安全RFC）、**OpenClaw**（Outbound策略、敏感数据脱敏）普遍将安全视为核心议题，从**对话级到平台级**的权限模型正在构建。
3.  **跨平台与渠道兼容性**：**Hermes Agent**（修复Windows控制台闪烁）、**NanoBot**（新增Mattermost支持）、**PicoClaw**（Matrix加密支持）、**CoPaw**（Matrix渠道流式回复）都在持续扩展其平台连接能力。尤其是**非x86/非桌面环境**（如Android Termux）的构建支持成为新的关注点（NullClaw #868）。
4.  **记忆与上下文管理**：**OpenClaw**（会话存储重构、记忆架构升级）、**NanoBot**（记忆系统增强、缓存失效修复）、**ZeroClaw**（上下文预算超限Bug）都面临**会话状态管理与性能**的挑战。如何高效、持久地管理Agent的“记忆”是普遍的工程难题。

### 5. 差异化定位分析

| 维度 | OpenClaw | NanoBot/ Hermes Agent | IronClaw | ZeroClaw | PicoClaw |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **功能侧重** | 全能型，功能最全，但维护压力大 | **通用型**，注重易用性和快速迭代 | **企业级/平台化**，聚焦能力策略与权限控制 | **通用型**，注重安全性、架构演进 | **擅长平台集成**，注重新渠道（Simplex）和多Agent协作 |
| **目标用户** | 开发者、硬核用户 | 个人用户、中小开发者 | 企业、需要精细化权限管理的团队 | 对安全性和插件生态有要求的开发者 | 有特定平台对接需求的开发者、社区运维者 |
| **技术架构** | 大而全，高度模块化，重构成本高 | **轻型、响应式**，更注重开发效率 | **平台化、重型**，强调控制平面与数据隔离 | **面向未来**，探索WASM插件运行时，注重安全隔离 | 专注核心功能，扩展性好，与特定平台（Simplex）的绑定度可能更高 |

### 6. 社区热度与成熟度

- **高活跃/快速迭代阶段（0.8-1.0）**：**Hermes Agent、ZeroClaw、IronClaw**。这些项目社区活跃，PR流转快，维护者响应积极，正以较高频率推进功能开发和Bug修复，是生态中最具活力的部分。
- **中活跃/质量巩固阶段（1.x-2.x）**：**NanoBot、PicoClaw、CoPaw、LobsterAI**。社区活动适中，项目正从功能堆砌转向稳定性打磨和用户体验优化，在修复历史积压Bug的同时稳健推出新功能。
- **低活跃/瓶颈阶段（>2.x）**：**OpenClaw**。虽然用户基数最大，但巨大的维护压力导致项目处于“守成”状态，难以快速响应社区需求，亟待内部流程优化或增加维护力量。
- **沉寂/早期**：**NullClaw、Moltis、TinyClaw、ZeptoClaw**。这些项目活跃度极低，可能处于维护者主导的早期开发阶段，或社区已陷入停滞。

### 7. 值得关注的趋势信号

1.  **“小模型”生态正在崛起**：**Moltis** 的多个PR专门修复与Gemma 4等小型本地模型的兼容性问题。这一信号表明，**边缘计算、本地优先、隐私保护的Agent** 需求正在从理论走向实践，社区对在有限资源环境下运行Agent的兴趣日益浓厚。开发者应关注模型选择和工具调用对低算力环境的适配。

2.  **Agent“假承诺”引发信任危机**：**OpenClaw #58450** 指出Agent会口头承诺“我会回来检查”，但实际并无后续行动。这揭示了当前语言模型在**执行意图跟踪与任务持久化**方面的根本缺陷。这不仅是Bug，更是产品设计挑战：**如何建立用户与Agent之间的信任契约？** 开发者需要思考引入显式的任务队列、状态回执和可观察性机制。

3.  **“开箱即用”体验成为最大壁垒**：多个项目（ZeroClaw #5808, NanoClaw #2876）的用户反馈显示，**首次启动失败**或**默认配置无法工作** 是用户流失的主要原因。核心开发经验：**默认配置足够小，确保能在绝大多数环境下首次运行成功，比堆叠功能更重要。**

4.  **“数据安全”不再只是概念**：**CoPaw #5579** 用户明确表达了因服务崩溃导致对话记录丢失的焦虑。**LobsterAI #2214** 的“备份卡死”问题也指向同一痛点。用户的数据资产意识正在觉醒。**断点保存、增量备份、防崩溃恢复** 等能力将不再是“增强功能”，而将成为生产级Agent的**必备基础能力**。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

好的，作为 NanoBot 项目的 AI 智能体与个人 AI 助手领域开源项目分析师，我根据您提供的 2026-06-28 数据，为您生成了以下项目动态日报。

---

# NanoBot 项目动态日报 (2026-06-28)

## 1. 今日速览

今日 NanoBot 项目活动频繁，社区驱动力强劲，项目健康度表现出色。**PR 合并/关闭数（18）与全新提交（19）基本持平**，表明项目维护者正在积极处理社区贡献，同时新功能开发仍在持续推进。在 **Bug 修复与稳定性加固**方面取得了显著进展，尤其是在会话损坏、流式传输状态同步及AI交互的稳健性上。同时，社区对 `spawn`工具功能增强和性能优化（如缓存）的需求也得到了快速响应，反映项目具备良好的社区沟通与迭代循环。

## 2. 版本发布

无新版本发布。

## 3. 项目进展 (今日合并/关闭的重要 PR)

今日项目通过合并一批关键 PR，显著提升了系统的鲁棒性与功能完整性，主要进展包括：

- **AI Agent 调用链容错性增强**：PR #4510 合入后，系统现在能主动丢弃并修复由模型返回的**格式错误或名称无效的 Tool Call**，防止其污染历史记录并导致后续对话崩溃。这标志着 AI 交互稳定性的一个重大提升。
- **定时任务 (Cron) 功能完整化**：PR #4225 和 #4357 被合并，为定时任务引入了 `silent`（静默）和 `lock_recipient`（锁定接收者）模式。这使得后台监控等任务可以独立运行、只在需要时才通知用户，极大增强了定时任务的实用性和灵活性。
- **核心 Bug 修复清理**：由社区成员 hamb1y 报告并修复的一系列严重 Bug 得到确认和合并（PR #3712 关联 #4057, #4060, #4063, #4059），涉及**会话文件碰撞、Anthropic 与 OpenAI 兼容性等问题**，为项目奠定了更稳固的基础。

## 4. 社区热点

今日最受关注的讨论集中在两个议题上：

1.  **[#660] 关于“超轻量”宣称的质疑与讨论**：用户 `besoeasy` 指出项目自称“超轻量”，但 Dockerfile 中同时依赖 Python 和 Node.js，存在矛盾。该 Issue 由维护者关闭，但其获得 **14条评论和5个赞**，反映了社区对项目定位的认真审视和较高期望。([链接](https://github.com/HKUDS/nanobot/issues/660))

2.  **[#4500] WebUI 重启后“假死”与停止按钮失效**：用户 `zpljd258` 报告了一个影响用户体验的关键 Bug，即 WebUI 在自动重启后界面卡在“处理中”状态，且停止按钮失效。该 Issue 开放仅4天即获得2条评论，且在当天就有对应的修复 PR **[#4565]** 被提出，表明维护者对影响用户和操作体验的问题响应迅速。([链接](https://github.com/HKUDS/nanobot/issues/4500))

## 5. Bug 与稳定性

今日报告的 Bug 总体上已得到快速响应，多数已有对应的修复 PR 在推进，项目稳定性处于动态改善中。

| 严重程度 | Bug 描述 | 关联 Issue | 状态 (Fix PR) |
| :--- | :--- | :--- | :--- |
| **高** | **WebUI 重启后UI卡死 & 停止按钮失效** ([#4500](https://github.com/HKUDS/nanobot/issues/4500)) | #4500 | 已有修复 PR [#4565](https://github.com/HKUDS/nanobot/pull/4565) |
| **高** | **上下文管理导致前缀/提示缓存持续失效** ([#4222](https://github.com/HKUDS/nanobot/issues/4222))，影响性能 | #4222 | 已有修复 PR [#4568](https://github.com/HKUDS/nanobot/pull/4568) |
| **中** | **`exec.allowPatterns` 安全检查易被绕过** ([#4521](https://github.com/HKUDS/nanobot/issues/4521))，存在安全隐患 | #4521 | 已有修复 PR [#4562](https://github.com/HKUDS/nanobot/pull/4562) |
| **低** | **会话文件名清理导致键冲突** (已关闭) | #4057 | 已修复 (PR #3712) |
| **低** | **非流式解析器保留重复Tool Call ID** (已关闭) | #4059 | 已修复 (PR #3712) |

## 6. 功能请求与路线图信号

社区对功能扩展的需求清晰且具体，多个功能请求已快速转化为PR，有望纳入下一版本：

1.  **[#4231] 为 Subagent 指定不同模型**：用户 `jsapede` 提出 `spawn` 工具应支持 `model` 参数，以允许子代理使用不同的AI模型处理特定任务。当日即有 PR **[#4570](https://github.com/HKUDS/nanobot/pull/4570)** 提出并正在审查中，落地可能性极高。
2.  **Mattermost 频道支持**：PR **[#4459](https://github.com/HKUDS/nanobot/pull/4459)** 提出增加 Mattermost 即时通讯平台支持，这是扩展项目生态的重要信号。
3.  **会话级模型预设**：PR **[#4555](https://github.com/HKUDS/nanobot/pull/4555)** 提出允许为每个会话单独选择模型，以应对不同对话场景，这呼应了用户对个性化控制的深层需求。
4.  **记忆系统增强**：PR **[#4554](https://github.com/HKUDS/nanobot/pull/4554)** 和 **[#4556](https://github.com/HKUDS/nanobot/pull/4556)** 分别致力于防止自动学习（Dream）功能创建重复技能和添加模型覆盖能力，表明项目正持续优化其长期记忆模块。

## 7. 用户反馈摘要

- **核心痛点**：
    - **稳定性与可靠性**：WebUI 的“假死”和“停止”按钮失效是用户最直观的负面体验。`max_messages` 导致缓存失效是影响性能和成本的深层技术问题。
    - **功能性不对称**：用户期望 `spawn` 等高级工具具备与主代理同等的定制能力（如指定模型），当前限制阻碍了复杂工作流的构建。
    - **文档与实际不符**：“超轻量”的描述与添加 Node.js 依赖的现实存在矛盾，损害了项目承诺的可信度。

- **满意点**：
    - **社区响应速度**：对于严重的 Bug 和受欢迎的功能请求，社区能够快速提出修复或实现 PR，表明项目活力高。
    - **功能深度**：Cron 任务的精细化控制、Mattermost 集成等高级功能，满足了企业和进阶用户的需求。

## 8. 待处理积压

目前没有观察到长期未响应的关键 Issue 或 PR。新提出的功能和 Bug 修复 PR 都在创建后的 24 小时内获得了活动，显示了维护者高效的处理节奏。建议维护者持续跟踪以下 PR 的最终状态：

- PR **[#4565](https://github.com/HKUDS/nanobot/pull/4565)** (修复 WebUI 重启假死)
- PR **[#4568](https://github.com/HKUDS/nanobot/pull/4568)** (修复缓存失效问题)
- PR **[#4562](https://github.com/HKUDS/nanobot/pull/4562)** (修复安全检查绕过漏洞)

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

好的，这是为您生成的 Hermes Agent 项目动态日报。

---

# Hermes Agent 项目动态日报 | 2026-06-28

## 1. 今日速览

今日项目活动量显著，24小时内处理了50条 Issue和50个 PR，展现出较高的社区参与度和维护效率。主要进展集中在**稳定性和平台兼容性**修复上，尤其是 Windows 平台的伪控制台窗口闪烁问题以及核心代理层的流处理与凭证管理。尽管今日无新版本发布，但大量高优 Bug 的修复（特别是针对 Anthropic 流处理、网关服务和授权逻辑的修补）表明项目正在为下一版本的稳定性做重点打磨。社区对新功能的需求依然旺盛，特别是云同步功能和桌面端远程接入功能，但短期内的重心显然是修复既有问题。

## 2. 版本发布

*无。*

## 3. 项目进展

今日合并或关闭的重要 PR 和 Issue 总体呈现了项目在稳定性和功能上的坚实推进：

- **核心稳定性提升**：针对多个 P1 级别的 Bug 进行了修复并关闭，包括：
    - **Anthropic 流处理死锁**：修复了 Anthropic 流处理中的关键问题，解决了因 SDK 自动重试与速率限制导致的账户死锁（Issue #26293）。
    - **凭证池绕过**：修复了 `_restore_primary_runtime` 直接重用已吊销 API 密钥，绕过凭证池轮换的重要安全/稳定性漏洞（Issue #25205）。
    - **多网关服务冲突**：解决了多 profile 下 gateway 服务因 PID 文件冲突而导致的重启循环问题（Issue #29092）。
    - **Auth配置覆盖**：修复了 `auth.json` 中的`active_provider` 运行时覆盖用户 `config.yaml` 设置的问题（Issue #29285）。
- **门户与平台兼容性**：
    - **Discord 图像附件**：修复了 Discord 网关中，混合发送文档或非标准格式图像时导致 HTTP 400 错误的问题（Issue #25935）。
    - **Windows 控制台闪烁问题**：通过合并 PR #53962 和 #53961，修复了 Windows 上因调用 `gh` 子进程产生的伪控制台窗口闪烁问题，并提交了更全面的修复版本（#53957状态保持开放）。
- **新功能/特性落地**：合并了多个新特性 PR，包括：
    - **`/findout` 斜杠命令**：在 CLI、TUI 和所有网关上新增了硬编码的 `/findout` 斜杠命令（PR #53889）。
    - **配置压缩警告阈值**：新增可配置的 `warn_after_compressions` 选项，让用户可以调整会话压缩警告的触发频率（PR #53958）。
    - **全量测试套件修复**：修复了主分支上的全量测试套件崩溃和超时问题（Issue #27004），为未来代码合并提供了可靠的回归保护。

**综上所述，项目在过去24小时内显著提升了核心代理逻辑的鲁棒性和平台的跨系统兼容性，并引入了数个实用的小功能，整体项目健康度良好。**

## 4. 社区热点

- **#20510 - 云同步功能请求**：尽管该 issue 于5月创建，但今日仍有7条评论和14个👍，是社区最强烈的呼声之一。用户表达了对跨设备同步 `~/.hermes/` 下全部配置、技能、会话和记忆的迫切需求，这是从个人使用走向多设备工作流的关键痛点。
    [NousResearch/hermes-agent Issue #20510](https://github.com/NousResearch/hermes-agent/issue/20510)

- **#28161 - Anthropic 流处理Bug**：在已关闭的 Issue 中讨论热度最高（7条评论）。该问题揭示了特定清理路径错误地为 Anthropic 用户重建 OpenAI 客户端，导致流卡死15分钟。这反映了项目在支持多模型提供商时，代码分层和条件判断的复杂性，引发社区对代码抽象层的讨论。
    [NousResearch/hermes-agent Issue #28161](https://github.com/NousResearch/hermes-agent/issue/28161)

- **#36970 - 桌面端远程客户端集成**：该功能请求获得了5条评论和3个👍，社区对 macOS 桌面端作为现有 Hermes 实例的远程客户端有明确需求，当前安装流程被反馈“似乎是为了安装一个全新的独立实例”，用户体验有待优化。
    [NousResearch/hermes-agent Issue #36970](https://github.com/NousResearch/hermes-agent/issue/36970)

## 5. Bug 与稳定性

- **严重 (P1/Security)**
    - **Cross-User Session Hijacking (安全跟踪)**：Issue #29149 和 #29153 作为私有安全公告的跟踪问题，提及网关权限绕过。这是项目当前最严重的安全隐患，影响范围广，需优先审查和修复。
    - **网关无中断式重启循环 (修复中)**：Issue #29092 描述了多 profile 下 gateway 服务的 flap loop 问题。今日已有关闭记录，但建议确认修复是否彻底。
        [NousResearch/hermes-agent Issue #29149](https://github.com/NousResearch/hermes-agent/issue/29149)
- **高 (P1/P2)**
    - **Windows 桌面端控制台窗口闪烁 (部分修复)**：Issue #53957 为新打开问题。PR #53962 和 #53961 已合并，针对 `gh` 子进程做了修复，但根因问题可能更广泛，PR #53892 尝试进行更全面的修复但被回退，仍需跟踪。
        [NousResearch/hermes-agent Issue #53957](https://github.com/NousResearch/hermes-agent/issue/53957)
    - **Matrix 网关启动循环**：PR #53933 旨在修复 Matrix 适配器因未处理的房间邀请导致启动阻塞直至循环的 Bug，当前为开放状态。
        [NousResearch/hermes-agent PR #53933](https://github.com/NousResearch/hermes-agent/pull/53933)
    - **网关后台进程阻塞会话重置**：PR #53942 修复了因被遗忘的后台进程持续占用，导致用户无法重置或切换会话的问题，目前开放审查中。
        [NousResearch/hermes-agent PR #53942](https://github.com/NousResearch/hermes-agent/pull/53942)

- **中 (P2/P3)**
    - **`${HERMES_SKILL_DIR}` 路径解析错误**：PR #41561 正在修复当使用远程终端后端（Docker/Modal）时，技能目录路径被错误渲染成本地路径的问题。
    - **`auth remove` 命令误杀同源凭证**：PR #24395 修复了 `auth remove` 命令在移除某个凭证时，错误地抑制了来自同一来源的其他所有凭证。
    - **桌面端 Electron 构建脚本污染工作树**：Issue #53949 报告了 `npm run build` 会不可逆地覆盖源代码文件，影响开发者环境和代码审查。

## 6. 功能请求与路线图信号

- **高优先级信号：**
    1.  **跨设备云同步 (#20510)**：需求强烈。社区目前无相关 PR，预计将是下个周期路线图规划的重点考虑项。
    2.  **桌面端远程客户端集成 (#36970)**：需求明确，直接关系到桌面用户体验。当前无对应 PR。
- **中优先级信号：**
    1.  **MoA 推理努力度 (Reasoning Effort) 配置 (#53932)**：来自核心贡献者，希望在 MoA 框架中为参考模型槽位设置不同推理努力度，属于功能增强，有明确实现路径。
    2.  **插件系统扩展 (Olympus 看板)**：PR #53951 提出捆绑 Olympus 作为监控插件，显示社区正在探索 Hermes 的可扩展生态。

## 7. 用户反馈摘要

- **正向反馈**：
    - 用户对通过 `/findout` 斜杠命令快速调用硬编码管线持肯定态度 (#53929)。
    - 社区对配置化压缩警告阈值表示欢迎，解决了长会话中的使用痛点 (#53958)。
- **负向反馈**：
    - **“配置混乱”**：Issue #29285 描述了 `auth.json` 静默覆盖 `config.yaml` 的行为，用户表示“令人困惑且难以调试”，期望配置优先级更透明。
    - **“桌面端开发体验差”**：Issue #53949 指出构建脚本会损坏原始代码，开发者需要 `git checkout` 才能恢复，严重影响了开发和审查体验。
    - **“不稳定的工具执行流程”**：多条 Issue 提及工具调用无响应、错误结果污染对话流、中断重启时丢失用户输入（如 #27033, #28834, #27564），影响了用户对代理可靠性的信心。

## 8. 待处理积压

- **长期未响应的 PR/Issue 信号**：
    - **PR #23243 (TUI 国际化框架)**：于2026-05-10提交，至今已有近50天，且长期处于开放状态。该 PR 对提升 TUI 的可及性和多语言支持有战略意义，建议维护者关注其进度或被卡阻原因。
        [NousResearch/hermes-agent PR #23243](https://github.com/NousResearch/hermes-agent/pull/23243)
    - **PR #42568 (TTS 端点)**：提交于2026-06-09，距今已21天未合并。该功能对对接 OpenAI 格式的第三方客户端至关重要，是网关能力补齐的重要一环。
        [NousResearch/hermes-agent PR #42568](https://github.com/NousResearch/hermes-agent/pull/42568)

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，以下是为您生成的PicoClaw项目动态日报（2026-06-28）。

---

# PicoClaw 项目动态日报 | 2026-06-28

## 1. 今日速览

项目今日活跃度中等。过去24小时内，Issue和PR活动均出现，但数量不多。值得关注的是，一个关于**Matrix加密消息处理**的严重Bug被新报告（#3194），同时一个关于**Agent间协作**的大型功能PR（#2937）已被合并，标志着项目在多Agent底座能力上取得了关键进展。此外，一个**Simplex频道类型**的PR（#3193）提出，表明社区在拓展平台连接性方面持续发力。总体来看，项目处于**稳定迭代与关键功能合并**的健康状态。

## 2. 项目进展

今日合并/关闭了2个重要PR，项目在稳定性和功能特性上均有推进：

- **Agent协作总线功能落地**：PR [#2937](https://github.com/sipeed/picoclaw/pull/2937) [已合并] 成功合入了一个“第一公民级Agent协作总线”。该PR为PicoClaw引入了持久的Agent间通信机制，包括：每个Agent独立的邮箱、协作线程（带隔离的会话历史）、结构化消息信封与投递状态，以及基于权限的访问控制。这是实现复杂多Agent任务编排与协同的基础设施，标志着PicoClaw在智能体架构上向前迈进了一大步。

- **MCP命令参数解析修复**：PR [#3048](https://github.com/sipeed/picoclaw/pull/3048) [已合并] 修复了`mcp add`命令在处理`--no-color`等根级别持久化标志时的解析错误。该问题由于启用了`DisableFlagParsing: true`导致，现在将正确拒绝并报告这些无效的“前置位置”标志，提升了命令行工具的健壮性和用户体验。

## 3. 社区热点

- **Telegram渠道权限分级控制（#3114）**：该Issue虽已关闭，但在其生命周期内获得了社区关注。用户提出了一个非常清晰的使用场景：在Telegram的**私聊、群组、频道**三种对话类型中，应具有不同的权限边界。例如，群组内应限制`exec`、`write_file`等危险操作，而私聊可以开放全部能力。这反映了用户对**安全性与场景化权限控制**的迫切需求，是PicoClaw作为实际生产力工具的重要考量点。

- **Agent协作功能（#2937）的合并**：虽然没有高评论数，但该PR的合并是整个社区近期最值得关注的动态。它直接回应了社区对于“Agent互联”的长期期待，将是后续许多高级功能（如任务委托、信息聚合）的基础。

## 4. Bug 与稳定性

- **【严重】Matrix加密消息无法处理（#3194）**：用户报告在使用Matrix通道时，当收到加密消息，系统报错“Received encrypted message but crypto is not enabled”，导致消息无法处理。这涉及到核心消息通道的功能完整性，可能导致Matrix用户完全无法使用。**严重性：高。当前状态：无修复PR。**

- **【已解决】`list_dir`在Windows上因路径分隔符报错（#2472）**：该长期存在的Bug（4月报告）已于今日被标记为关闭。修复逻辑是将操作系统特定的反斜杠“\”转换为Go `fs.FS`/`os.Root`要求的正斜杠“/”。**严重性：中。当前状态：已关闭。**

## 5. 功能请求与路线图信号

- **Simplex频道类型（#3193）**：新提交的PR旨在添加“Simplex”频道支持。虽然具体细节未在摘要中详述，但这表明社区和贡献者对**支持更多元化、可能更轻量或特定用途的通信协议**感兴趣，未来可能扩大PicoClaw的集成生态。

- **Telegram对话类型级权限控制（#3114）**：虽然未达成，但这个**功能请求**（Future Request）清晰指明了PicoClaw在多渠道安全隔离方面的设计空白。结合近期社区对安全的关注，该功能很有可能被纳入下一版本的路线图规划，作为“安全边界”功能的增强。

- **Agent协作功能（#2937）**：已合并。这将成为**下一版本的核心能力**，为后续功能的开发（如任务分解、多角色对话等）铺平道路，预计将成为未来版本更新的主要亮点。

## 6. 用户反馈摘要

- **正面反馈/需求明确**：用户对于能明确描述**功能使用场景**（如Telegram群组vs私聊）提供了清晰的用例，这有助于开发者理解PicoClaw在实际部署中面临的安全和可用性挑战。
- **痛点明确**：**Windows用户路径分隔符问题**（#2472）的修复反映了跨平台兼容性是基础但关键的用户痛点；**Matrix加密消息**问题（#3194）则是某个特定渠道的致命缺陷，如果不解决将导致该渠道用户流失。
- **潜在期待**：尽管没有直接的“满意度”评论，但`Agent协作` PR的合并在社区层面得到了积极反馈（从其成功合并可推断），用户对PicoClaw从“单Agent工具”向“多Agent平台”演化的方向是认可和期待的。

## 7. 待处理积压

- **Matrix加密消息Bug（#3194）**：此Issue为新开，且无任何评论。由于是阻碍用户正常使用的严重问题，建议项目维护者**优先关注并分配**。如果此时没有相关开发活动，应尽快回应或标记为“需确认”。
- **Agent协作PR（#2937）**：刚合并，目前无积压状态。但建议项目团队迅速跟进，完善相关文档和配置示例，帮助社区快速上手这一重要新特性。

---

**分析师总结**：PicoClaw项目经历了平稳而关键的一天。最显著的成就是`Agent协作总线`的合并，这确立了项目在多Agent领域的技术前瞻性。同时，`Matrix加密Bug`的及时报告和`Telegram权限控制`的需求暴露了项目在特定平台纵深和安全性方面的待完善之处。项目整体健康状况良好，处于功能快速迭代与社区反馈驱动优化并行的阶段。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，这是为您生成的 NanoClaw 项目 2026-06-28 动态日报。

---

# NanoClaw 项目日报 | 2026-06-28

## 1. 今日速览

过去 24 小时，NanoClaw 项目活跃度**较高**，核心表现为 **Bug 修复 PR 激增**和**新功能孵化中**。社区反馈了两个关键问题：`/update-skills` 命令在更新已有频道时形同虚设，以及实验性特性 `--provider openai` 会在容器运行时崩溃。项目维护者积极响应，针对 `/update-skills` 问题已提交了修复 PR（#2873），同时有 3 个长期待合入的清理/修复 PR 在本日获得了更新。此外，社区贡献了在 Coolify 上的部署支持（#2875）以及两项针对 OpenCode 模型与仪表盘的新功能（#2871, #2872），显示出项目在功能扩展与生态整合方面的潜力。当前待合并 PR 数达 8 个，需要维护者重点审查。

## 2. 版本发布

无

## 3. 项目进展

今日无 PR 被合并，但以下 **8 个待合并 PR** 反映了项目的核心推进方向：

- **关键 Bug 修复就绪：**
    - **PR #2873** (Fix: `/update-skills` 修复)：由报告者 glifocat 提供的修复，旨在解决 Issue #2868。它将预检逻辑与凭证验证分离，确保 `/update-skills` 能正确刷新已有频道的代码和依赖。这是对 4.29 版本升级流程体验的关键修复。
    - **PR #2874** (Fix: Signal 频道稳定性)：修复了 Signal 频道适配器因服务启动抖动而反复崩溃的问题，提升了特定频道类型的稳定性。
- **长期清理与稳定性 PR 更新：**
    - **PR #2822** (Refactor：移除死挂载点)：清理容器运行器中无效的 `/workspace/global` 挂载，优化了容器环境。
    - **PR #2823** (Fix：移除被主机自动删除的 CLAUDE.md)：解决了宿主机会在每次启动时删除某个文件导致的配置不一致问题。
    - **PR #2824** (Fix：清除过时的内存指令)：从主提示词中移除了已失效的“全局记忆”指令，避免对 Agent 行为产生误导。
- **新功能孵化：**
    - **PR #2871** (功能：仪表盘推送器)：新增一个模块，可定时将 NanoClaw 的状态快照发送至外部仪表盘服务器，为项目监控和可视化奠定了基础。
    - **PR #2872** (功能：OpenCode 模型覆盖)：允许在 OpenCode Agent 组中配置不同的模型，通过 `container_configs.model` 注入环境变量实现，增强了多模型部署的灵活性。
- **社区集成：**
    - **PR #2875** (功能：Coolify 部署支持)：社区成员提交了在 Coolify 平台上的部署配置，降低了项目的自托管门槛。

**总结：** 项目正在积极修复影响用户升级和稳定性的关键 Bug，同时也在引入新的监控和模型管理功能，项目正朝着更加健壮和可观测的方向迈进。

## 4. 社区热点

**热帖：Issue #2868 - `/update-skills is a silent no-op for already-installed channels`**
- **链接：** [Issue #2868](https://github.com/nanocoai/nanoclaw/issues/2868)
- **热度：** 评论 1，创建者与修复者高度重合，是过去 24 小时最具“行动力”的讨论。
- **核心诉求：** 用户发现按照版本更新日志提示的“重新运行 `/add-<channel>`”操作通过 `/update-skills` 执行时，会**静默失败**。这直接导致用户无法通过预期路径完成技能和依赖的更新，是一个严重的可用性问题。
- **分析：** 该 Issue 精准地指出了 4.29 版本升级流程中的关键断裂点，社区对此关注度极高。好在 glifocat 迅速提交了关联的修复 PR（#2873），社区热点与修复行动高度同步，体现了良好的开发者响应。

## 5. Bug 与稳定性

报告了 2 个 Bug，均与配置和运行时环境相关。

- **[严重] Bug #2868：`/update-skills` 对已安装频道静默无操作**
    - **状态：** 已报告，有 Fix PR（#2873）
    - **影响：** 影响所有尝试通过 `/update-skills` 完成技能更新的用户，导致更新流程永远无法完成。这是对核心功能流程的严重破坏。
    - **链接：** [Issue #2868](https://github.com/nanocoai/nanoclaw/issues/2868)

- **[严重] Bug #2876：`--provider openai` 导致容器崩溃**
    - **状态：** 新报告，尚无 Fix PR
    - **影响：** 虽然 CLI 接受 `--provider openai` 配置，但在 Agent 实际接收消息启动容器时会立即崩溃。这完全阻止了用户使用 OpenAI 提供商，属于实验性功能的严重阻碍。
    - **分析：** 该 Bug 表明新加的 `provider` 配置项在容器生成和网络/认证初始化阶段存在缺失或逻辑错误，很可能是环境变量注入或依赖加载失败导致。
    - **链接：** [Issue #2876](https://github.com/nanocoai/nanoclaw/issues/2876)

## 6. 功能请求与路线图信号

1.  **多模型支持（路线图信号强烈）：** 用户在 Issue #2876 中尝试使用 OpenAI 模型，而 PR #2872 已实现 OpenCode 模型覆盖功能。这强烈表明社区对**多模型、多提供商并行部署**有着明确需求，预计该功能将在下一版本中被正式合入和宣传。
2.  **可观测性与监控：** PR #2871 (Dashboard Pusher) 的提出，虽然是一个内部功能，但反映出项目开始关注“**运行状态的可视化**”。这通常是项目进入成熟期的标志，也是社区运维人员所期待的。
3.  **部署生态扩展：** PR #2875 (Coolify 支持) 显示社区正在主动填补部署文档和脚本的空缺。虽然这是外部贡献，但它反映了用户对**简化自托管流程**的持续诉求。

## 7. 用户反馈摘要

- **正面反馈：** (无直接正面评论，但从贡献行为推断)
    - 社区开发者 (`glifocat`, `bogdano2`, `CutSnake01`) 自行发现并修复Bug，表明项目贡献者社区活跃且对代码库熟悉度高。
    - 社区成员 (`zczDief`) 贡献了非核心功能的部署支持，说明项目有一定吸引外部贡献者的价值。

- **负面/痛点反馈：**
    - **“更新体验断裂”**：用户无法通过标准命令 `/update-skills` 完成技能更新，必须另寻他法。Issue #2868 的标题和摘要直接点名了这种“静默失败”导致的困惑和挫败感。
    - **“功能启用即崩溃”**：用户在尝试使用 OpenAI 提供商时遭遇了启动崩溃（Issue #2876），这直接击穿了用户对新功能的信任，是冷启动体验不佳的典型案例。
    - **“升级流程不明确”**：Issue #2868 明确指出了 CHANGELOG 中建议的迁移步骤不可用，这表明版本的升级文档/迁移指南缺乏足够的自动化测试保障。

## 8. 待处理积压

本次日报中未发现长期未响应的重要 Issue。但以下 3 个由 `CutSnake01` 在 2026-06-20 提交的 PR 已经等待合并超过一周，它们不涉及新功能，而是关于清理和稳定性的重要补丁，建议维护者优先审查处理：

1.  **PR #2822** - Refactor: [移除无用的 `/workspace/global` 挂载](https://github.com/nanocoai/nanoclaw/pull/2822)
2.  **PR #2823** - Fix: [解决 `CLAUDE.md` 被主机自动删除的问题](https://github.com/nanocoai/nanoclaw/pull/2823)
3.  **PR #2824** - Fix: [清除过时的“全局记忆”指令](https://github.com/nanocoai/nanoclaw/pull/2824)

这些 PR 的长时间等待可能会增加后续合并时的冲突风险，且它们解决的都是在实际运行中可能引发困惑或小错误的问题。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，根据您提供的 NullClaw 项目数据，我为您生成了 2026年6月28日 的项目动态日报。

---

# NullClaw 项目动态日报 | 2026-06-28

## 今日速览

本周六，NullClaw 项目活跃度处于中等水平。过去24小时内，社区贡献主要体现在1个新开的Pull Request（PR）上，该PR旨在为智能体（Agent）引入结构化的审批流程。与此同时，一个关于Android/Termux环境下构建失败的老问题（Issue #868）仍在等待解决方案。项目暂无新版本发布，整体处于功能迭代推进与稳定性问题待解决的平衡状态。

## 版本发布

*无。过去24小时内无新版本发布。*

## 项目进展

- **功能推进**: 社区贡献者 `valonmulolli` 提交了 **PR #969**，实现了智能体工具调用的结构化审批流。
    - **内容**: 该PR为shell工具（及其他返回`ApprovalRequired`错误的工具）设计了一个“双轮”审批流程。工具向智能体发出审批请求，智能体捕获后通过SSE通道向用户界面发送事件，从而在UI层呈现审批界面，增强了人机交互的安全性和可控性。
    - **评估**: 这是一个重要的用户体验改进，将模糊的“需要批准”概念具体化为结构化的前后端交互流程，填补了当前Agent交互链路中的一个缺失环节。

## 社区热点

- **Issue #868: Android/Termux 构建失败问题**
    - **链接**: [nullclaw/nullclaw Issue #868](https://github.com/nullclaw/nullclaw/issues/868)
    - **状态**: 持续讨论中，已有4条评论。
    - **分析**: 该问题由用户在4月份提出，描述了在Android设备（aarch64）上的Termux环境中使用Zig编译工具链构建项目时，因文件系统权限（`AccessDenied on options.zig linkat`）导致失败。虽然并非新问题，但其在过去24小时内被更新，表明社区成员或维护者仍在关注此事。该问题反映了开源项目在非主流或受限环境（如移动终端）下部署的紧迫性。用户的核心诉求是“**在移动设备上也能顺利运行/开发NullClaw**”，这对项目拓展开发者用户群至关重要。

## Bug 与稳定性

- **严重**:
    - **Issue #868**: **Android/Termux 构建失败 (`AccessDenied`)**。该Bug阻塞了用户在Android平台上通过终端构建和使用NullClaw的能力。目前仍未关联任何修复PR（Fix PR）。由于涉及操作系统权限和Zig编译器的特定行为，属于平台兼容性难题，需要维护者深入调查或寻找变通方案。

## 功能请求与路线图信号

- **PR #969 (结构化审批流)**: 该PR提出的功能请求是构建安全、可控AI Agent的核心能力。它表明社区对**增强Agent工具调用过程中的安全性与用户控制权**有明确需求。考虑到其设计的优雅性和对现有架构的插件化影响，该特性有很大概率被纳入下一版本发布中。

## 用户反馈摘要

- **痛点**: 在非标准环境（如Android/Termux）下的构建体验是用户的主要痛点。用户`NOTJuangamer10`提供了详细的环境信息（系统、架构、依赖版本）和完整错误日志，显示了其高度的专业性和对解决问题的迫切需求。然而，该问题自4月提交以来未得到有效响应，这可能导致该用户对项目支持的缺失感到失望。
- **使用场景**: 用户尝试在移动端（Redmi Note 9）上进行构建，暗示了NullClaw可能在**移动设备或边缘计算场景**中存在潜在应用。

## 待处理积压

- **Issue #868**: 这是当前最值得关注且未解决的积压问题。
    - **理由**: 该问题已存在超过2个月，涉及核心的构建流程，且阻塞了在特定流行平台（移动Linux环境）上的使用。长期悬而未决会损害项目的声誉和开发者友好度。
    - **建议**: 建议维护者优先进行以下操作：
        1.  尝试在虚拟机或相关环境下复现该Bug。
        2.  在Issue中回复用户，解释根本原因（如是否Zig版本不兼容、Android文件系统限制等），并提供临时解决方案（如使用预编译的Nightly构建版本）。
        3.  如果短期内无法修复，应在项目文档中明确标注此限制。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，我为您呈现 IronClaw 项目在 2026-06-28 的日报。

---

### IronClaw 项目动态日报 — 2026-06-28

**项目名称:** IronClaw
**数据快照:** github.com/nearai/ironclaw
**分析日期:** 2026-06-28

---

### 1. 今日速览

今日项目活跃度极高，核心开发团队正通过一系列大尺寸 PR 和 Issue 推进 **“Reborn 能力策略 (Capability Policy)”** 这一史诗级功能。过去 24 小时内，该功能链条上的多个关键 Issue（如 `#5261`, `#5266`, `#5267`, `#5268`, `#5272`, `#5273`）均被关闭，标志着从模型设计到引擎实现、再到管理界面的核心链路已初步打通。同时，超过 10 个 Pull Request 被合并，开发效率显著。尽管有 **27 个待合并 PR** 显示出较大的积压，但大部分为功能或修复的后续迭代，整体项目健康度良好，正处于重要的功能突破期。

### 2. 版本发布

- **无新版本发布。** 截至报告期，项目尚未发布新的正式版本。

### 3. 项目进展

今日项目取得了里程碑式的进展，核心标志是 **“能力策略”** 功能开发进入了收尾阶段。

- **能力策略核心链路贯通：** 随着 PR `#5262`、`#5270`、`#5344`、`#5349` 的合并，以及顶层控制平面 PR `#5355` 的合并，整个能力策略功能的核心已完整实现。这包括：
    - **模型层（`#5262`）：** 定义了 `ironclaw_capability_policy` crate，实现了四维策略模型及其解析器。
    - **用户角色与管理门控（`#5270`）：** 在 WebChat-v2 栈中引入了数据库驱动的用户角色系统（Owner > Admin > Member），为权限管理奠定了基础。
    - **引擎层（`#5344`）：** 实现了持久化的增量存储和策略 `Resolver`，能够执行配置、身份和审批策略。
    - **可用性层（`#5349`）：** 实现了 `CapabilitySurfaceProfileResolver`，使针对用户的“可用性”授权能够影响模型可见的工具集。
    - **控制平面（`#5355`）：** 提供了 REST API，允许管理员创建本地用户并授予精细权限。这是实现手动测试和管理界面的前提。

- **集成测试框架上线：** PR `#5381` (已合并) 建立了 **“Reborn 集成测试框架”**。该框架允许在进程内运行整个 Reborn 的完整流程，仅伪造模型外部调用，为后续复杂功能的可靠性提供了保障。

- **用户体验与基础设施：**
    - **`#5365` (合并中):** 修复了 WebUI v2 聊天重试按钮的 bug，使其能够真正重新发送消息。
    - **`#5380` (打开中):** 正在扩展 Reborn WebUI v2 的质量保证矩阵，以覆盖更多场景。
    - **`#5384` (打开中):** 固定了 WebUI v2 前端的 Node.js 版本，确保构建环境一致性。
    - **`#5279` (打开中):** 正在修复消息队列和用户消息路由的逻辑。

- **测试框架具体推进：** 下图为 `#5381` 合并后，团队成员对测试框架各 slice 的推进情况。`slice 4` 和 `slice 9` 在今日被创建，`slice 9` 被判定为不可达（无需实现），显示了项目的高效执行。

### 4. 社区热点

今日社区讨论高度集中于 **“能力策略”** 功能的实现细节，虽然互动评论数不高，但其涉及多个 Issue 和 PR 的协作，是当前项目绝对的核心。

- **热点 Issue：** **`#5261 [EPIC] Reborn capability policy`** - 作为该功能的总体追踪 Issue，它的关闭标志着该项重大功能的开发阶段完成，是项目社区关注的焦点。[链接](https://github.com/nearai/ironclaw/issues/5261)
- **热点 PR：** **`#5355 [CLOSED] capability-policy control plane`** - 作为功能链的最上层 PR，它的合并是最终的落地动作，集成了前期所有工作。[链接](https://github.com/nearai/ironclaw/pull/5355)
- **活跃的新 Issue：** **`#5385 [OPEN] Add Capability Policy`** - 由核心开发者 `zetyquickly` 创建，以更工程化的语言描述了该功能的最终目标，即确保用户权限的精细化配置。这可能是功能的进一步说明或文档入口。[链接](https://github.com/nearai/ironclaw/issues/5385)

### 5. Bug 与稳定性

今日主要涉及以下 Bug 报告和修复：

- **[高] Google OAuth Token 刷新失败 (`#5378`，已关闭)**
    - **摘要：** 在 `hosted-single-tenant` 和 `local-dev` 配置下，Google OAuth 令牌刷新失败，导致用户约每小时需要重新认证一次。问题定位为 `BackendUnavailable`。
    - **状态：** 已被关闭，表明已发现并可能已修复或正在修复中。
    - **链接:** [Issue #5378](https://github.com/nearai/ironclaw/issues/5378)

- **[中] 持续失败的 Nightly E2E 测试 (`#4108`，仍开放)**
    - **摘要：** 一个持续超过一个月的 nightly 端到端测试任务失败。虽然被标记为 `OPEN`，但最后一次更新是 06-27，表明可能仍在排查中。
    - **链接:** [Issue #4108](https://github.com/nearai/ironclaw/issues/4108)

- **[中] 工具错误时显示模糊的 `invalid_input` 错误 (`#5338`，PR 打开中)**
    - **摘要：** 当工具调用失败时，用户会看到“driver protocol error”或“invalid_input”等模糊信息。PR `#5338` 计划在终端运行摘要和每个工具的 Activity 卡片中展示真实的失败原因。
    - **链接:** [PR #5338](https://github.com/nearai/ironclaw/pull/5338)

### 6. 功能请求与路线图信号

- **请求：** **“Always allow eligible tools” 默认启用 (`#5364`，已关闭)**
    - **概述：** 用户希望将“总是允许符合条件的工具”设置为默认选项，以避免每次调用工具时都弹出审批提示。
    - **信号：** 这个小的用户体验改动得到了快速响应（被关闭），表明项目团队对新用户开箱即用体验的重视。该功能很可能在下一版本中成为默认行为。
    - **链接:** [Issue #5364](https://github.com/nearai/ironclaw/issues/5364)

### 7. 用户反馈摘要

- **核心痛点：兼容性 & 部署错误。**
    - **OAuth 问题：** 用户 `thisisjoshford` 报告了在云端部署时 Google OAuth 频繁刷新失败的问题，这直接影响了使用 Google 相关能力（如 Gmail, Calendar）的稳定性和用户体验。
    - **回调 URL 错误：** 用户 `sunglow666` 指出 Notion MCP 授权在 Railway 部署时会生成无法访问的 `localhost` 回调 URL，这影响了第三方工具的集成，暴露了部署环境与回调机制之间的兼容性问题。

### 8. 待处理积压

- **长期存在的关键 Issue：**
    - **`#4108`：** Nightly E2E 测试持续失败超过一个月。尽管最后一次更新在昨天，但长期未解决会损害项目对 CI/CD 和自动化测试的信心。
    - **`#4841`：** 旨在消除“run-borking”终端错误的大 PR（size: XL），已开放两周。若被合并，将显著提升 Reborn 应用的健壮性，应优先关注。

- **依赖更新 PR：**
    - **`#5114`：** Dependabot 自动创建的 `tokio-ecosystem` 依赖更新 PR，已开放一周。虽然风险较低，但长期搁置可能引入安全问题或错失性能优化。
    - **链接:** [PR #5114](https://github.com/nearai/ironclaw/pull/5114)

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，以下是基于LobsterAI (netease-youdao/LobsterAI) 项目数据生成的2026年6月28日项目动态日报。

---

## LobsterAI 项目动态日报 | 2026-06-28

### 1. 今日速览

今日项目整体活跃度较高，主要集中在**历史Bug的批量修复与合并**。过去24小时内，共有7个Pull Request被关闭/合并，涵盖了从MCP支持、网关稳定性到国际化、快捷键等多项长期存在的缺陷修复，显示出项目团队正集中精力清理技术债务。Issues方面，用户报告了两个高影响度问题：**安装环境异常**和**数据备份功能导致主进程卡死**，均未得到解决。总体来看，项目正处于一个“修复密集期”，稳定性与用户体验的提升是当前主旋律。

### 2. 版本发布

*   **无**：过去24小时内没有发布新版本。

### 3. 项目进展

今日项目取得了显著进展，完成了7个PR的合并/关闭，这些PR均来自4月初的“stale”标签，现在被统一推进解决。这表明团队正在清理历史积压工作，提升代码库健康度。

*   **MCP 协议支持增强**：[PR #1001](https://github.com/netease-youdao/LobsterAI/pull/1001) 被关闭，增加了对SSE和流式HTTP传输类型MCP的支持。此前仅支持`stdio`类型，导致用户配置后不生效。
*   **核心稳定性修复**：
    *   [PR #1446](https://github.com/netease-youdao/LobsterAI/pull/1446) 修复了OpenClaw网关因竞态条件导致**无限重启循环**的严重Bug。
    *   [PR #1453](https://github.com/netease-youdao/LobsterAI/pull/1453) 修复了**已停用技能仍被注入对话**的逻辑漏洞。
*   **功能与体验优化**：
    *   [PR #1449](https://github.com/netease-youdao/LobsterAI/pull/1449) 优化了**定时任务历史记录**的展示，采用折叠分组方式，避免了侧边栏被大量重复记录刷屏。
    *   [PR #1448](https://github.com/netease-youdao/LobsterAI/pull/1448) 修复了Agent设置页面的**国际化遗漏**问题。
    *   [PR #1454](https://github.com/netease-youdao/LobsterAI/pull/1454) 修复了**定时任务创建表单**在某些情况下点击无响应的静默失败问题。
    *   [PR #1456](https://github.com/netease-youdao/LobsterAI/pull/1456) 为**快捷键设置**增加了重复检测功能，防止用户设置冲突快捷键导致功能失效。

### 4. 社区热点

今日社区讨论热度中等，热点集中在两个新提交的Bug报告，均来自用户 `woxinsj`，反映其在使用中遇到的严重问题。

*   [Issue #2215](https://github.com/netease-youdao/LobsterAI/issues/2215)：“安装LobsterAI，修复反复出现的「Resource extraction failed: could not start extractor process」错误”。用户详细记录了详尽的排查过程（10+步骤），从杀毒软件到解析NSIS安装包，将问题定位到真实安装路径和环境。这不仅是求助，更像是一份高质量的错误排查报告。背后诉求是**提升安装程序的鲁棒性和环境兼容性**。
*   [Issue #2214](https://github.com/netease-youdao/LobsterAI/issues/2214)：“桌面端‘数据备份’功能导致主进程卡死（未响应）”。该问题**100%可复现**，且发生在高频使用场景下（几百条消息/天），一旦触发，用户只能强制结束进程，风险极高。

### 5. Bug 与稳定性

今日提交了两个高严重性Bug，均未得到修复，需项目组重点关注。

*   **【紧急】主进程卡死**：[Issue #2214](https://github.com/netease-youdao/LobsterAI/issues/2214) - 用户执行“数据备份”功能时，应用主窗口白屏卡死。环境：Windows 11 24H2，数据库71.6MB。用户预估是大数据库或WAL模式下备份导致IO阻塞。**无对应FIX PR**。
*   **【高】安装失败**：[Issue #2215](https://github.com/netease-youdao/LobsterAI/issues/2215) - 安装过程中反复出现“Resource extraction failed: could not start extractor process”错误，错误码`ERROR_BAD_ENVIRONMENT`。用户已通过分析NSIS安装包脚本，发现其安装路径检测和日志处理逻辑可能存在问题。**无对应FIX PR**。
*   **【已修复】多个历史Bug**：今日关闭的7个PR（如#1446, #1453, #1454）均为历史遗留的稳定性或功能性Bug经长期搁置后被修复。这表明项目组正在系统地清理技术债务。

### 6. 功能请求与路线图信号

今日未直接提出新功能请求。但结合当前PR和Issue，可以捕捉到一些潜在的路线图信号：

*   **数据管理优化**：[Issue #2214]的用户场景（大数据库备份导致卡死）和[PR #2065]（修复Agent ID生成逻辑，解决数据“复活”问题）都指向了项目正在或需要加强**数据持久化与管理能力**。
*   **定时任务治理**：[PR #1449]（折叠分组展示）和[PR #1454]（表单无响应修复）的合并表明，**定时任务模块**是近期的优化重点，下一版本可能会对定时任务进行全面迭代。
*   **环境兼容性**：[Issue #2215]用户对安装程序的深入分析，暴露了NSIS打包脚本可能存在缺陷。这或将推动团队在下一版本**优化安装与启动流程**，特别是在Windows环境下的可靠性。

### 7. 用户反馈摘要

*   **痛点明确的报告**：用户 `woxinsj` 在[Issue #2215](https://github.com/netease-youdao/LobsterAI/issues/2215)中展现了极强的技术能力和耐心，其详细的排查方案（从清理残留到反编译安装包）反映出**安装流程的挫败感极高**。用户不只是抱怨，而是带着解决方案在求助。
*   **高影响度使用场景**：[Issue #2214](https://github.com/netease-youdao/LobsterAI/issues/2214)描绘了一个典型的**重度用户场景**：每天数百条消息、大数据库、频繁使用会话与网关。在这个场景下，一个核心功能的直接卡死，对用户的信任打击是巨大的。
*   **修复停滞的沉默**：今日有7个PR被关闭，但这7个PR自4月3日起就被标记为`stale`（过期），长达近3个月无人处理。虽然最终被解决，但修复周期过长可能会让部分受影响的社区用户感到被忽视。

### 8. 待处理积压

以下为长期未响应或未合并的重要Issue/PR，提醒维护者关注。

*   [PR #2065](https://github.com/netease-youdao/LobsterAI/pull/2065)：**修复Agent ID使用短UUID替代名称**。这是防止数据意外复活的关键修复，与[Issue #2214]的数据管理问题有间接关联，且已标记为`stale`。该PR若被合并，将是提升数据安全性的重要一步。已搁置整一个月，建议优先审阅。
*   今日反映的两个高影响度Bug：[Issue #2214](https://github.com/netease-youdao/LobsterAI/issues/2214)（主进程卡死）与[Issue #2215](https://github.com/netease-youdao/LobsterAI/issues/2215)（安装失败）目前均无对应的Fix PR或维护者回复，应迅速响应并分配人力处理，尤其是#2214，严重影响了核心功能的可用性。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

好的，这是为您生成的 Moltis 项目 2026-06-28 动态日报。

---

## Moltis 项目日报 | 2026-06-28

### 1. 今日速览

今日项目整体活跃度**中等偏低**。过去24小时内，Issues 与 PR 数量均较为有限，仅有1个新 Bug 报告和2个待合并的修复 PR，无新版本发布。值得关注的是，项目对小型本地模型（如 Gemma 4）的兼容性问题关注度持续上升，今日的 Bug 和 PR 均与此主题相关。虽然整体活动量不大，但显示出社区正在积极解决边缘情况下的稳定性问题，尤其是针对非主流模型生态的支持。

### 2. 版本发布

无新版本发布。

### 3. 项目进展

今日无任何 PR 被合并或关闭，项目里程碑未向前推进。目前有2个重要修复 PR 处于待合并状态，建议维护者优先关注：

- **[#1136] fix(agents): coerce stringified scalar tool args before validation**：此 PR 修复了一个针对较小模型（如 Gemma 4）的兼容性问题。这类模型在调用工具函数时，会将标量参数（如 `true`、`5000`）错误地格式化为 JSON 字符串（`"true"`、`"5000"`）。该 PR 在参数验证前增加了类型强制转换逻辑，可显著提升与这类模型的交互成功率。
- **[#1098] fix(browser): tolerate null optional params in browser tool calls**：处理另一个模型兼容性问题。部分模型在未使用浏览器工具的某些可选参数时，会显式传递 `null` 而非直接忽略。此 PR 修改了反序列化逻辑，使系统能够容忍这些显式的 `null` 值，从而避免因参数校验失败导致的工具调用中断。

### 4. 社区热点

今日无讨论特别活跃的话题。2个待合并的 PR 均未产生评论，而新开的 Bug #1137 也无人评论，整体社区讨论热度较低。

### 5. Bug 与稳定性

今日发现1个新的 Bug，严重程度中等。

- **[#1137] [Bug]: Apple Container ID exceeds name limit**
  - **严重程度**：中等
  - **描述**：用户报告在 Apple 平台上，Moltis 创建的容器 ID 长度超过了系统允许的名称长度限制。
  - **影响范围**：主要影响 Apple 生态（macOS/iOS）用户，可能导致容器创建或运行失败。
  - **修复状态**：**尚无关联的 fix PR**，等待维护者进一步调查复现步骤与解决方案。

### 6. 功能请求与路线图信号

今日未直接产生新的功能请求。然而，从今日活跃的2个 PR 和 Bug 来看，项目路线图的一个明确信号是：**强化对小型本地模型的支持**。`fix(agents)` 和 `fix(browser)` 两个 PR 都明确指向了改进与 Gemma 4、oMLX 等模型交互的鲁棒性。这反映出社区对在资源受限环境下运行 AI Agent 的兴趣日益增长，Moltis 项目正在主动响应这一趋势，这可能成为下一个版本的重点优化方向之一。

### 7. 用户反馈摘要

今日未从 Issues 或 PR 的评论中提炼出具体的用户反馈或痛点场景。现有的 Issues 和 PR 均为技术性报告或修复，缺乏社区讨论。项目目前的活跃贡献者（如 `resumeparseeval`）似乎更专注于解决与模型兼容性相关的技术债务。

### 8. 待处理积压

今日无长期未响应的重要 Issue 或 PR。PR #1098 自6月3日创建至今已近一个月仍未合并，可能因涉及核心逻辑改动需要更谨慎的审查，或维护者资源不足。建议项目维护者对此 PR 给予最终反馈或部署排期。

- **PR #1098**：[moltis-org/moltis PR #1098](https://github.com/moltis-org/moltis/pull/1098) - 已开放24天，无维护者评论。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，以下是根据您提供的CoPaw项目数据生成的2026年6月28日项目动态日报。

---

# CoPaw 项目动态日报 | 2026-06-28

## 今日速览

今日CoPaw项目活跃度**高**。社区提交活跃，产品迭代（特别是稳定性修复和UI体验优化）与质量保障（大规模单元测试覆盖）工作并行推进。值得关注的是，出现了一个关键的**对话记录丢失**Bug（#5579）以及由真实用户报告的**DeepSeek V4兼容性**问题（#5573），后者已完成修复PR。此外，一位新贡献者提交了首个PR，修复模型上下文压缩的覆盖优先级问题，社区贡献生态健康。

## 版本发布

- **无新版本发布。**

## 项目进展

今日有**1个PR被合入/关闭**，主要涉及UI布局层面的功能改进。

- **[已关闭] fix(console): improve MCP access policy layout (#5213)**
    - **内容**：优化了MCP客户端卡片在窄/宽视口下的布局对齐，提升了工具与权限模态框和规则行的响应式表现，并添加了基于MCP源的访问主体发现功能。
    - **意义**：完成了前端UI的一个功能改进，提升了MCP功能管理的易用性和视觉一致性。

## 社区热点

今日社区讨论焦点集中在 **“稳定性”与“兼容性”** 两大主题上，相关Issue和PR讨论热烈。

1.  **[Bug] DeepSeek V4 thinking 模式兼容性故障 (#5573)**
    - **热度**：2条评论，由真实用户详细描述并提供复现步骤。
    - **分析**：用户反馈在使用非官方OpenAI兼容端点连接DeepSeek V4模型时，因流式响应中`reasoning_content`字段缺失以及工具Schema中`null`类型未清洗导致400错误。这表明CoPaw在支持新兴模型（如DeepSeek V4）的特定模式（thinking）时，与第三方中转站的兼容性处理存在不足。好消息是，关联的Fix PR (#5582)已经提交，表明问题正在被积极解决。

2.  **[Bug] 对话记录在异常中断场景下丢失 (#5579)**
    - **热度**：1条评论。
    - **分析**：该问题直击用户核心体验——数据安全性。用户描述了在Agent执行`reboot`命令导致宿主机重启、或服务崩溃后，当前对话记录完全丢失。这表明当前系统缺乏断点保存机制，是严重的稳定性和数据可靠性问题。该Issue目前仅有用户诉求，尚未有维护者回复或修复方案，风险等级较高。

## Bug 与稳定性

今日汇报了**3个Bug**，按严重程度排列如下：

1.  **[严重] 对话记录在异常中断场景下丢失 (#5579)**
    - **描述**：Agent执行`reboot`或服务崩溃后，当前对话记录完全丢失。
    - **状态**：`[OPEN]`，无关联修复PR。**需要维护者紧急关注**。

2.  **[高] DeepSeek V4 thinking 模式400错误 (#5573)**
    - **描述**：使用非官方API端点时，因`reasoning_content`缺失和`null`类型Schema导致请求失败。
    - **状态**：`[OPEN]`，已有修复PR **#5582** 在审核中。

3.  **[中] 无法连接自定义ascend-vllm模型 (#5584)**
    - **描述**：新版本无法连接本地VLLM服务，旧版本（1.1.7）正常。报错为`APIConnectionError`，但VLLM后端日志无异常。
    - **状态**：`[OPEN]`，无关联修复PR。可能涉及连接逻辑或配置变更。

## 功能请求与路线图信号

- **对话中断断点保存机制**：用户对#5579的反馈实际上提出了一个强有力的功能请求——为对话系统增加“断点保存”或“快照”机制。这可能是未来提升系统健壮性的重要方向。
- **Matrix通道流式回复**：PR #5585 为Matrix通信渠道增加了类似Discord的流式模式，提升了跨平台聊天体验。这是一个明确的新功能点。
- **插件修复与扩展**：PR #5568 修复了QwenPaw 2.0上5个官方插件的安装问题，确保核心生态功能正常。同时，PR #4622 提交的“DataPaw”数据分析插件显示社区正在为CoPaw扩展新的应用领域。

## 用户反馈摘要

- **正面/功能反馈**：用户`Morxi`为Matrix渠道贡献了流式回复功能（PR #5585），表明开发者社区对提升跨平台体验有热情。
- **痛点反馈**：
    1.  **数据安全焦虑（#5579）**：用户 `tecgic` 强烈表达了因系统缺乏断点保存机制导致对话丢失的不满和焦虑，指出系统“非常脆弱”。
    2.  **兼容性期望高（#5573, #5584）**：普通用户期望CoPaw能无缝支持各种新兴模型（如DeepSeek V4）和自定义后端（如ascend-vllm）。兼容性问题，特别是与流行模型的集成问题，会严重影响用户采用率。
- **非开发者的贡献**：Issue #5573的作者 `Zhanyuan23333` 明确表示自己“非python程序员”，但仍然完成了复现、分析并尝试了修改方案。这表明CoPaw有很强的“高级用户”群体，他们对产品的参与度和贡献意愿高。

## 待处理积压

1.  **[长期未响应的PR] plugin(datapaw): add data-analysis plugin (PR #4622)**
    - **状态**：`[OPEN]`，超过一个月未更新，处于“待审核”（Under Review）状态。
    - **内容**：一个功能完备的数据分析插件，引入了12个BI技能。
    - **建议**：该PR代表了社区对新功能的深度贡献，长期悬而未决可能打击贡献者积极性。建议项目维护者尽快安排Review，明确是否合并或告知需要调整的方向。

2.  **[长期开放的关键Issue] [Bug] 对话记录丢失 (#5579)**
    - **状态**：`[OPEN]`，昨日刚刚创建，但问题严重，且目前无任何维护者介入。
    - **建议**：这是当前最紧急的问题，建议项目维护者优先处理，至少应确认问题并告知社区初步的排查方向和修复时间表。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，我将根据您提供的 ZeroClaw 项目数据，生成一份结构清晰、数据驱动的项目动态日报。

---

# ZeroClaw 项目动态日报 (2026-06-28)

## 1. 今日速览

ZeroClaw 项目近期保持着非常高的活跃度。24小时内有了近50条Issue和50个PR的更新，社区讨论和代码贡献均十分活跃。项目在**安全性、运行时稳定性、渠道(WASM)扩展和配置管理**四个维度上都有显著推进。尽管没有新版本发布，但大量的RFC和Tracker表明项目正为0.8.3和0.9.0版本进行密集的规划和开发。核心风险集中在**上下文预算耗尽**、**安全策略执行**和**插件架构设计**等关键问题上。

- **Issues**: 48条活跃更新，其中8条已被关闭。
- **PRs**: 50条活跃更新，其中8条已被合并或关闭。

## 2. 版本发布

24小时内无新版本发布。

## 3. 项目进展 (重要 PR 合并/关闭)

过去24小时，项目在修复关键Bug和提升代码健壮性方面取得了明确进展。以下是被合并的、与核心功能或稳定性相关的PR：

- **修复运行时循环检测器**: `fix(agent/loop-detector): do not count failed tool results as "no progress"`（[#8213](https://github.com/zeroclaw-labs/zeroclaw/pull/8213)）被合并。此项修复防止了代理在工具调用失败时被循环检测器错误地终止，提升了长期运行任务的稳定性。
- **修复原生工具调用后的叙述转发**: `fix(runtime): forward narration emitted after a native tool call`（[#8329](https://github.com/zeroclaw-labs/zeroclaw/pull/8329)）被合并。解决了调用原生工具后，代理的“内心独白”（narration）无法通过流式响应传递给用户的问题，改善了交互体验。
- **增强报告模板安全**: `test(tools): cover report template substitution safety and html escaping`（[#8270](https://github.com/zeroclaw-labs/zeroclaw/pull/8270)）被合并。通过增加测试，保障了报告模板替换的安全性，防止XSS攻击。
- **文档与标签规范化**: `docs(labels): document ACP channel label`（[#8406](https://github.com/zeroclaw-labs/zeroclaw/pull/8406)）被合并，改进了项目标签系统的维护指南。

这些合并的PR表明项目正在积极解决运行时的核心稳定性问题，并持续加固安全防线。项目向`v0.8.3`和`v0.9.0`的目标迈出了坚实的一步。

## 4. 社区热点

当前社区讨论的焦点高度集中在 **安全信任链** 和 **插件/扩展架构** 的顶层设计上。

- **RFC: 供应链安全 (Issue #8177)**: 获得 **10条评论**，是本周期最热门的话题。社区对在ZeroClaw中引入`硬件PGP密钥`、`确定性构建`和`SLSA provenance`等企业级供应链安全实践的方案进行了深入探讨。这反映了用户（尤其是企业用户）对软件发布流程安全性和可溯源性有极高的要求。

- **RFC: 基于WASM的插件运行时 (Issue #8135)**: 获得 **2条评论**，但作为一项架构层面的RFC，其讨论动向备受关注。社区正就如何将`WebAssembly`作为默认插件运行时进行论证，这预示着ZeroClaw可能将彻底与Node.js解耦，实现更安全、更轻量、语言无关的扩展生态。

- **Bug: 默认32K上下文预算总被超限 (Issue #5808)**: 尽管创建于两个月前，但仍在持续活跃讨论。这是一个**严重的P1级Bug**，因为系统提示词和工具定义在首轮对话就超过了预设的32K token预算，导致代理反复进行修剪。这是影响用户上手体验和任务复杂度的关键瓶颈。

社区的整体诉求是**构建一个安全、可扩展、适用于严肃场景的AI代理平台**，而非一个简单的玩具项目。用户正在推动ZeroClaw从“能用”走向“企业级可信”。

## 5. Bug 与稳定性

- **S1 - Workflow Blocked**
    - **[Bug]: 默认32k context budget被超限 (Issue #5808)**: 这是最严重的Bug。首次LLM迭代即超出预算约3.3倍，导致代理无法正常工作。
    - **[Bug]: mcp_bundles 配置未在运行时生效 (Issue #7733)**: 这是一个安全相关的无操作Bug。`mcp_bundles`配置被解析和展示，但实际并未在运行时限制Agent可见的MCP工具，导致安全隔离策略失效。**已有相关修复的PR (#8370) 正在排期。**

- **S2 - Degraded Behavior**
    - **[Bug]: 心跳引擎从错误目录读取任务文件 (Issue #8366)**: 心跳引擎从`data_dir`而非Agent专属的`workspace`读取任务文件，导致功能异常。这是一个配置管理上的回归问题。
    - **[Bug]: Cron和心跳任务仍发送NO_REPLY文字 (Issue #2128)**: 这是一个长期未修复的体验问题，当任务无需报告时，系统会向用户渠道发送“NO_REPLY”字样的噪音消息。

**稳定性小结**: 今天报告的Bug主要集中在运行时的配置错误和边界情况，尤其是`mcp_bundles`的失效问题，凸显了安全配置在实际执行层面的断裂。好消息是，已有PR专门针对`mcp_bundles`问题进行回归测试和修复。

## 6. 功能请求与路线图信号

社区提出的新功能请求主要集中在以下几个方向，对应项目规划的`v0.8.3`和`v0.9.0`里程碑：

- **明确路线图内功能**:
    - **[Feature]: 支持每Agent自定义环境变量 (Issue #8226)**: 被标记为`type:rfc`，旨在解决多租户场景下身份、参数和令牌隔离的问题。这与`v0.9.0`的`auth, security, gateway`目标高度吻合。
    - **[Feature]: 为WhatsApp Web群聊提供被动上下文 (Issue #8379)**: 对应的PR (#8389) 已于昨日提交。这表明ZeroClaw正在积极提升其在社交平台上的智能交互体验，增强对群聊环境的感知能力。
    - **[Feature]: 技能CRUD钩子/事件 (Issue #8348)**: 是对`skills`平台成熟度的补充，允许外部系统观测技能变更，是平台化的重要一步。

- **潜在下一版本信号**:
    - **RFC: 目标模式 (Issue #8303)**: 已获接受，对应的实现PR (#8393)也已提交。这表明`v0.8.3`之后，`Goal Mode`（有边界的自主任务执行）将成为下一个重要特性。
    - **RFC: 插件权限与机密模型 (Issue #8398)**: 对插件系统权限模型的深入探讨，直接关联到WASM插件运行时。该讨论将影响未来所有第三方扩展的安全性。

## 7. 用户反馈摘要

- **核心痛点**: 用户在 `#5808` 中强烈反映，默认的上下文窗口太小，导致首次对话就失败，**严重阻碍了项目的快速上手和测试**。这使得“开箱即用”的体验大打折扣。
- **配置困惑**: `#7733` 的提交者发现`mcp_bundles`配置没有真正生效，反馈了“**安全隔离功能是一个静默的无操作**”这一令人沮丧的发现，表明配置层面的文档和实现需要更加一致。
- **主动贡献**: 例如 `#6642` 中，贡献者 JordanTheJet 主动提出要将其在 **Micra-io下游分支** 中实现的功能（捕获LLM调用详情）上游到主分支。这表明社区中有一群非常深度和高质的用户，愿意推动项目向前发展。
- **明确使用场景**: `#7952` 请求发布“全渠道”预编译包，反映了用户在实际部署中，希望一次下载就能使用所有渠道（如Telegram, Slack等），避免因渠道缺失而二次编译的麻烦。

## 8. 待处理积压

- **长期未解决的P1 Bug**: `[Bug]: 默认32k context budget被超限` **(#5808)**。此Bug从4月创建至今，虽被标记为`accepted`且`in-progress`，但2个月仍未关闭，是当前项目最显著的可用性障碍，需优先处理。

- **高价值RFC缺乏执行**: `[Feature]: 为MCP添加资源和提示支持 (Issue #4467)`。此功能3月提出，点赞数高达4，社区呼声高，且能显著扩展ZeroClaw的互操作性。目前仍处于`in-progress`状态，希望维护者能推动其进入开发。

</details>

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*