# AI 开源趋势日报 2026-06-23

> 数据来源: GitHub Trending + GitHub Search API | 生成时间: 2026-06-23 03:31 UTC

---

好的，作为专注于 AI 开源生态的技术分析师，根据您提供的 2026-06-23 数据，我已完成了 AI 相关项目的筛选、分类和趋势分析，现为您呈上《AI 开源趋势日报》。

---

## AI 开源生态趋势日报 | 2026-06-23

### 1. 今日速览

今日 AI 开源社区呈现三大核心动向：**Agent 工具链（MCP/Agent Harness）持续爆发**，多个面向 Claude Code、Codex 等 CLI 的定制化技能包和内存上下文项目获得极高关注度；**AI 驱动的内容创作工具迎来生态级突破**，视频生成、语音克隆等成熟工具的开源版本迅速登顶热榜；**开源大模型应用落地加速**，超长周期 SuperAgent、金融智能体、轻量级推理等垂直场景项目百花齐放，标志着 AI 开源正从“基础框架”向“精细化应用”纵深演进。

### 2. 各维度热门项目

#### 🔧 AI 基础工具（框架、SDK、推理引擎、开发工具、CLI）

- **[ollama/ollama](https://github.com/ollama/ollama)** ⭐174,754 · 本地大模型运行工具，支持包括 Kimi、GLM、DeepSeek 等在内的最新模型快速部署与切换。
- **[vllm-project/vllm](https://github.com/vllm-project/vllm)** ⭐83,590 · 高性能大模型推理引擎，专为 LLM 推理和部署提供高吞吐、低内存占用，已成为业界事实标准。
- **[lyogavin/airllm](https://github.com/lyogavin/airllm)** ⭐ +193 today · 突破性推理项目，可在单张 4GB 显存 GPU 上运行 70B 大模型，极大降低大模型本地推理门槛。
- **[tursodatabase/turso](https://github.com/tursodatabase/turso)** ⭐ +540 today · 兼容 SQLite 的内存级 SQL 数据库，为 AI Agent 提供轻量、快速的状态持久化和数据管理方案。
- **[0xPlaygrounds/rig](https://github.com/0xPlaygrounds/rig)** ⭐7,716 · 用 Rust 构建模块化、可扩展的 LLM 应用框架，满足对性能和安全性有极致要求的 AI 应用场景。
- **[LancerLab/croqtile](https://github.com/LancerLab/croqtile)** ⭐34 today · 下一代 AI 原生内核编程 DSL，旨在通过新型语言设计最大化 AI 编程助手的开发效率。

#### 🤖 AI 智能体/工作流（Agent 框架、自动化、多智能体）

- **[Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT)** ⭐185,091 · AI Agent 的鼻祖，持续引领 “AI 赋能所有人” 的愿景，提供构建自主 Agent 的完整框架。
- **[NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent)** ⭐200,078 · 强调持续成长的 Agent 框架，为开发者提供了强大的智能体开发基座。
- **[langgenius/dify](https://github.com/langgenius/dify)** ⭐146,189 · 面向生产环境的 AI 应用开发平台，专注于 Agentic Workflow 的开发、运营与部署。
- **[bytedance/deer-flow](https://github.com/bytedance/deer-flow)** ⭐73,369 (+738 today) · 字节跳动开源的“SuperAgent”框架，能够处理从数分钟到数小时的超长周期复杂任务，集研究、编码、创造于一体，代表了 Agent 能力上限的突破。
- **[OpenHands/OpenHands](https://github.com/OpenHands/OpenHands)** ⭐78,045 · 智能体驱动的软件开发平台，标志着 AI 正向“自主编程”方向迈进。
- **[browser-use/browser-use](https://github.com/browser-use/browser-use)** ⭐100,153 · 让网站对 AI Agent 无障碍，推动 Web 自动化与 AI Agent 深度融合，是 Agent 获取线上服务的关键基础设施。
- **[zhayujie/CowAgent](https://github.com/zhayujie/CowAgent)** ⭐45,562 · 开源的超级 AI 助手与 Agent 框架，强调轻量级和易扩展性，支持多模型、多渠道接入。
- **[garrytan/gstack](https://github.com/garrytan/gstack)** ⭐ +573 today · 提供 Garry Tan（YC CEO）本人的 Claude Code 配置和 23 个 Agent 工具，将 Agent 的工作流从“编码助手”提升至“CEO、设计师、PM”的角色模拟，极具启发价值。

#### 📦 AI 应用（具体应用产品、垂直场景解决方案）

- **🎬 AI 视频/创作**
  - **[calesthio/OpenMontage](https://github.com/calesthio/OpenMontage)** ⭐ +2938 today · 世界首个开源、智能体驱动的视频制作系统，将任何 AI 编码助手变为全功能视频制作工作室，Agent 应用场景的重要扩展。
  - **[palmier-io/palmier-pro](https://github.com/palmier-io/palmier-pro)** ⭐ +2463 today · 专为 AI 设计的 macOS 视频编辑器，代表视频编辑软件与传统 AI 的深度融合新方向。
  - **[heygen-com/hyperframes](https://github.com/heygen-com/hyperframes)** ⭐ +395 today · 写 HTML 就能渲染视频，专为 Agent 设计，极大简化了视频内容的自动生成流程。
- **🎙️ AI 语音**
  - **[jamiepine/voicebox](https://github.com/jamiepine/voicebox)** ⭐ +529 today · 开源 AI 语音工作室，集声音克隆、听写与创作为一体，让复杂语音应用开发门槛降低。
- **📈 AI 金融**
  - **[TauricResearch/TradingAgents](https://github.com/TauricResearch/TradingAgents)** ⭐88,028 · 多智能体 LLM 金融交易框架，展示了 AI 在量化交易和策略研究中的巨大潜力。
  - **[ZhuLinsen/daily_stock_analysis](https://github.com/ZhuLinsen/daily_stock_analysis)** ⭐46,021 (+1557 today) · LLM 驱动的多市场股票智能分析系统，将大模型能力与实时金融数据结合，提供从数据到决策的自动化闭环。
- **🛡️ AI 安全**
  - **[mukul975/Anthropic-Cybersecurity-Skills](https://github.com/mukul975/Anthropic-Cybersecurity-Skills)** ⭐ +956 today · 为 AI Agent 提供 817 个结构化网络安全技能，映射至 6 个权威框架（MITRE ATT&CK 等），标志着 AI Agent 在专业安全领域的落地。
- **💼 AI 求职**
  - **[santifer/career-ops](https://github.com/santifer/career-ops)** ⭐55,258 · 基于 Claude Code 的 AI 求职系统，拥有 14 种技能模式，展示了 AI 在个人职业发展上的应用。
- **🎨 AI 设计**
  - **[penpot/penpot](https://github.com/penpot/penpot)** ⭐ +728 today · 开源的“Figma 替代品”，强调设计与代码协作，其开放性使其成为 AI 生图、AI 布局等设计 AI 应用的首选平台。

#### 🧠 大模型/训练（模型权重、训练框架、微调工具）

- **[huggingface/transformers](https://github.com/huggingface/transformers)** ⭐161,823 · 🤗 提供的模型定义框架，支持文本、视觉、音频等多模态领域的 SOTA 模型，是 AI 开发的基石。
- **[tensorflow/tensorflow](https://github.com/tensorflow/tensorflow)** ⭐195,840 · 面向所有人的开源机器学习框架，尽管面临挑战，但其生态系统依然庞大。
- **[pytorch/pytorch](https://github.com/pytorch/pytorch)** ⭐100,963 · 业界使用最广泛的深度学习框架，在研究和生产中占据绝对主导地位。
- **[scikit-learn/scikit-learn](https://github.com/scikit-learn/scikit-learn)** ⭐66,397 · 经典的 Python 机器学习库，是 AI/ML 从业者最基础、最可靠的“瑞士军刀”。
- **[open-compass/opencompass](https://github.com/open-compass/opencompass)** ⭐7,112 · 大模型评测平台，支持 100+ 数据集和主流模型，是客观衡量模型能力的“公平秤”。
- **[thinkwee/AgentsMeetRL](https://github.com/thinkwee/AgentsMeetRL)** ⭐1,630 · “Agent 强化学习”的 Awesome List，代表了 Agent 研究领域的最新范式。
- **[galilai-group/stable-pretraining](https://github.com/galilai-group/stable-pretraining)** ⭐266 · 专注于基础模型和世界模型的预训练库，力求可靠与可扩展，代表了基础模型训练的前沿探索。

#### 🔍 RAG/知识库（向量数据库、检索增强、知识管理）

- **[infiniflow/ragflow](https://github.com/infiniflow/ragflow)** ⭐83,380 · 将 RAG 与 Agent 能力结合，为 LLM 提供强大的上下文层，是构建企业级知识问答系统的标杆。
- **[run-llama/llama_index](https://github.com/run-llama/llama_index)** ⭐50,299 · 领先的文档 Agent 与 OCR 平台，将非结构化数据转化为可供 LLM 检索的知识。
- **[milvus-io/milvus](https://github.com/milvus-io/milvus)** ⭐44,902 · 高性能云原生向量数据库，是支撑大规模向量检索和 AI 应用的核心基础设施。
- **[PaddlePaddle/PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR)** ⭐83,346 · 将图片/PDF 转化为结构化数据的 OCR 工具包，是连接非结构化文档与 AI 系统的桥梁。
- **[mem0ai/mem0](https://github.com/mem0ai/mem0)** ⭐59,160 · AI Agent 的通用记忆层，实现跨会话的长期记忆，是 Agent 迈向“记忆体”世界的关键。
- **[thedotmack/claude-mem](https://github.com/thedotmack/claude-mem)** ⭐83,784 · 为每个 Agent 提供持久化上下文，通过记忆压缩和注入实现真正的跨会话上下文理解。
- **[DeusData/codebase-memory-mcp](https://github.com/DeusData/codebase-memory-mcp)** ⭐ +1185 today · 高性能代码智能 MCP 服务器，以知识图谱形式索引代码库，实现亚毫秒级查询，是 Agent 理解大型代码库的利器。

### 3. 趋势信号分析

- **Agent 工具链“技能化”与“模板化”爆发**：以 `garrytan/gstack`、`mattpocock/skills` 和 `santifer/career-ops` 为代表的项目，不再局限于开发 Agent 框架，而是提供现成的、高度定制化的 Agent **技能包或工作流模板**。这表明社区关注的焦点已从“如何搭建 Agent”转向“如何高效使用 Agent”，Agent 的“生产力工具”属性正在被深度挖掘。
- **MCP 协议成为连接 Agent 与外部世界的“新 USB”**：`DeusData/codebase-memory-mcp` 和 `zilliztech/claude-context` 等项目的火爆，证明 MCP（Model Context Protocol）正在成为构建 Agent 应用的事实标准。通过 MCP，Agent 可以无缝接入代码库、数据库、知识图谱等后端资源，将自身能力向外无限延伸。这标志着 Agent 生态正走向模块化和标准化。
- **多模态生成进入“AI 原生”阶段**：`OpenMontage`（视频）和 `hyperframes`（视频）的登顶，宣告了 AI 视频生成正式进入“AI 原生”阶段——不再仅仅是给传统工具加 AI 滤镜，而是从头构建一套服务于 Agent 的、全新的创作管线。这与 AI 语音领域的 `voicebox` 形成呼应，多模态 Agent 的应用场景正在快速落地。

### 4. 社区关注热点

- **`mattpocock/skills`**：⭐+2051 today。来自知名 TypeScript 教学者的 `.claude` 目录配置，提供了一个“真实工程师”的 Agent 技能集，是学习如何配置和驯服 AI 编码助手的绝佳范本。
- **`DeusData/codebase-memory-mcp`**：⭐+1185 today。极致的代码 MCP 服务器，将代码仓库瞬间转化为可查询的知识图谱。对于希望让 Agent 深入理解复杂代码库的开发者来说，这是不可多得的生产力工具。
- **`garrytan/gstack`**：⭐+573 today。YC CEO 亲自开源的 AI Agent 工作流配置。它不仅是一套工具，更是 AI 时代“一人公司”管理哲学的实践，对理解如何将 Agent 团队化、角色化有重要的启发意义。
- **`calesthio/OpenMontage`**：⭐+2938 today。今日 Trending 榜首。作为首个开源 Agent 视频制作系统，它预演了 AI Agent 从“写代码”到“拍电影”的能力跃迁。关注它，就是关注 Agent 能力的天花板。
- **`shareAI-lab/learn-claude-code`**：⭐67,931。从 0 到 1 教你用 Bash 构建一个简化版 Claude Code Agent。对于希望深入理解 Agent 内部运行机制，而非仅仅使用黑盒产品的开发者，这是一份内容翔实的“解剖学”教材。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*