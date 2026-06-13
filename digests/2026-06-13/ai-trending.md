# AI 开源趋势日报 2026-06-13

> 数据来源: GitHub Trending + GitHub Search API | 生成时间: 2026-06-13 03:40 UTC

---

好的。作为一名专注于 AI 开源生态的技术分析师，以下是根据您提供的 2026-06-13 数据的《AI 开源趋势日报》。

---

### AI 开源趋势日报 | 2026-06-13

### 第一步：AI 相关性筛选

从 **Trending 榜单** 和 **主题搜索** 结果中，筛选出与 AI/ML 明确相关的项目。

**Trending 榜单已过滤的非 AI 项目：**
- music-assistant/server
- mattermost/mattermost
- apple/container
- iptv-org/iptv
- refactoringhq/tolaria
- masterking32/MasterDnsVPN
- microsoft/PowerToys

**筛选后的 AI 相关项目如下：**
- **Trending 榜单（共 6 个）**：
  - addyosmani/agent-skills
  - obra/superpowers
  - maziyarpanahi/openmed
  - LMCache/LMCache
  - phuryn/pm-skills
  - msitarzewski/agency-agents

- **主题搜索结果（<80> 个中保留绝大部分具有强 AI 属性的项目）**：此处列出所有 `topic` 为 `rag`，`llm`，`vector-db`，`ml`，`llm-model`，`ai-agent` 的项目，这些均被视为 AI 相关。

### 第二步：分类

将筛选后的项目按以下维度分类。

#### 🔧 AI 基础工具 (框架、SDK、推理引擎、开发工具、CLI)
- `langchain-ai/langchain`
- `ollama/ollama`
- `vllm-project/vllm`
- `huggingface/transformers`
- `pytorch/pytorch`
- `tensorflow/tensorflow`
- `scikit-learn/scikit-learn`
- `keras-team/keras`
- `0xPlaygrounds/rig`
- `picovoice/picollm`
- `LMCache/LMCache`

#### 🤖 AI 智能体/工作流 (Agent 框架、自动化、多智能体)
- `langgenius/dify`
- `Significant-Gravitas/AutoGPT`
- `OpenHands/OpenHands`
- `flowiseai/Flowise`
- `browser-use/browser-use`
- `CopilotKit/CopilotKit`
- `NousResearch/hermes-agent`
- `Eigenwise/atomic-agents`
- `addyosmani/agent-skills`
- `obra/superpowers`
- `phuryn/pm-skills`
- `msitarzewski/agency-agents`

#### 📦 AI 应用 (具体应用产品、垂直场景解决方案)
- `open-webui/open-webui`
- `CherryHQ/cherry-studio`
- `zhayujie/CowAgent`
- `HKUDS/nanobot`
- `iOfficeAI/AionUi`
- `maziyarpanahi/openmed`
- `hugohe3/ppt-master`
- `ZhuLinsen/daily_stock_analysis`
- `openbb-finance/OpenBB`
- `scrapegraphai/scrapegraph-ai`

#### 🧠 大模型/训练 (训练框架、微调工具)
- `ollama/ollama` (偏推理，但作为模型运行引擎归入此类)
- `vllm-project/vllm` (偏推理)
- `hiyouga/LlamaFactory`
- `open-compass/opencompass`
- `skyzh/tiny-llm`

#### 🔍 RAG/知识库 (向量数据库、检索增强、知识管理)
- `infiniflow/ragflow`
- `run-llama/llama_index`
- `milvus-io/milvus`
- `qdrant/qdrant`
- `weaviate/weaviate`
- `lancedb/lancedb`
- `mem0ai/mem0`
- `NirDiamant/RAG_Techniques`
- `thedotmack/claude-mem`
- `safishamsi/graphify`

---

### 第三步：输出报告

#### 1. 今日速览

今日 AI 开源领域呈现 **“智能体技能市场”爆发** 的趋势。Trending 榜单上，`agent-skills`、`pm-skills`、`agency-agents` 等项目凭借极高的日增星数，标志着“Agent Skills”作为一种可交换、可复用的 AI 能力单元正受到社区狂热追捧。与此同时，基础设施层面，`LMCache` 聚焦 KV Cache 加速，为 LLM 推理性能提升提供了新思路；`openmed` 则代表医疗 AI 垂直应用的持续探索。总体而言，开源社区正从构建“通用 Agent”转向“定制化、专业化的 Agent 技能”分发与生态建设。

#### 2. 各维度热门项目

**🔧 AI 基础工具**
- **[vllm-project/vllm](https://github.com/vllm-project/vllm)** ⭐82,725 | LLM 推理和服务引擎的标杆项目，持续在吞吐量和内存效率上优化。
- **[LMCache/LMCache](https://github.com/LMCache/LMCache)** ⭐0 (+28 today) | 宣称是“最快的 KV 缓存层”，专注于提升 LLM 推理速度，是基础设施优化的重要信号。
- **[huggingface/transformers](https://github.com/huggingface/transformers)** ⭐161,549 | 机器学习模型的事实标准库，持续迭代，是任何 AI 开发者的必备工具。
- **[pytorch/pytorch](https://github.com/pytorch/pytorch)** ⭐100,700 | 深度学习框架的绝对主力，社区活跃度极高。
- **[0xPlaygrounds/rig](https://github.com/0xPlaygrounds/rig)** ⭐7,602 | 用 Rust 构建 LLM 应用的模块化框架，代表了从 Python 向更高性能语言扩展的趋势。

**🤖 AI 智能体/工作流**
- **[langgenius/dify](https://github.com/langgenius/dify)** ⭐145,008 | 最流行的 Agentic 工作流开发平台之一，提供了从原型到生产的完整能力，专注于 RAG 与 Agent 结合。
- **[addyosmani/agent-skills](https://github.com/addyosmani/agent-skills)** ⭐0 (+2656 today) | **今日最大亮点**。由知名工程师创建的生产级“智能体技能”集合，标志着AI编码技能的可复用性和标准化。
- **[obra/superpowers](https://github.com/obra/superpowers)** ⭐0 (+1275 today) | 同样是 Agent Skills 框架，强调与软件开发方法论结合，与 `agent-skills` 形成双雄局面。
- **[phuryn/pm-skills](https://github.com/phuryn/pm-skills)** ⭐0 (+827 today) | “项目经理技能” AI Agent，覆盖从发现到增长的完整产品生命周期，代表了 Agent 向特定职业角色的渗透。
- **[msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents)** ⭐0 (+1026 today) | 将多 Agent 落地为“AI 代理机构”，包含多个具备不同专业技能的 Agent，展现了多 Agent 协作的实用化场景。

**📦 AI 应用**
- **[maziyarpanahi/openmed](https://github.com/maziyarpanahi/openmed)** ⭐0 (+515 today) | 开源医疗 AI，专注于垂直场景，其今日热度显示社区对医疗 AI 的关注度在提升。
- **[CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio)** ⭐47,251 | 集成聊天、自主 Agent 和 300+ 助手的 AI 生产力工作室，是“超级应用”方向的探索。
- **[OpenBB-finance/OpenBB](https://github.com/OpenBB-finance/OpenBB)** ⭐69,028 | 金融数据平台，明确支持 AI Agent，是金融科技与 AI 融合的典范。
- **[ScrapeGraphAI/Scrapegraph-ai](https://github.com/ScrapeGraphAI/Scrapegraph-ai)** ⭐27,143 | 基于 AI 的网页爬虫，直接解决了 Agent 获取实时数据的核心痛点。

**🧠 大模型/训练**
- **[hiyouga/LlamaFactory](https://github.com/hiyouga/LlamaFactory)** ⭐72,122 | 高效微调框架，支持 100+ LLM 与 VLM，是定制定向大模型的标准工具。
- **[open-compass/opencompass](https://github.com/open-compass/opencompass)** ⭐7,081 | 全面的 LLM 评测平台，对于衡量模型性能至关重要。
- **[skyzh/tiny-llm](https://github.com/skyzh/tiny-llm)** ⭐4,272 | 教你用 Apple Silicon 构建 mini vLLM + Qwen 的学习项目，降低了 LLM 推理学习门槛。

**🔍 RAG/知识库**
- **[infiniflow/ragflow](https://github.com/infiniflow/ragflow)** ⭐82,586 | 领先的开源 RAG 引擎，融合了 Agent 能力，是 RAG 领域的热门选择。
- **[milvus-io/milvus](https://github.com/milvus-io/milvus)** ⭐44,753 | 高性能、云原生的向量数据库，是构建大规模 RAG 应用的支柱。
- **[mem0ai/mem0](https://github.com/mem0ai/mem0)** ⭐58,458 | “AI Agent 的通用记忆层”，解决了 Agent 的长期记忆问题，与当前 Agent 热潮紧密相关。
- **[thedotmack/claude-mem](https://github.com/thedotmack/claude-mem)** ⭐82,019 | 专注于跨会话上下文保持，与多种主流 Agent 工具集成，是 Agent 记忆管理的明星项目。
- **[StarTrail-org/LEANN](https://github.com/StarTrail-org/LEANN)** ⭐11,913 | 最新学术论文项目，宣称在实现 97% 存储节省的同时，在个人设备上运行高速、准确的私有 RAG 应用。

#### 3. 趋势信号分析

今日最强烈的信号是 **“Agent Skills”成为社区爆发性关注点**。`agent-skills`、`superpowers`、`pm-skills` 三个项目合计日增超过 4700 颗星，这在单一主题上是现象级的。这表明社区需求已从“如何构建一个 Agent”转向了“如何让 Agent 变得有用、专业且易于扩展”。“Skills”作为一种模块化、可交换的能力单元，正试图成为 AI Agent 领域的“App Store”或“插件生态”。这与 `mem0` 或 `claude-mem` 等记忆项目的火爆相辅相成，共同指向一个更成熟、更具生态潜力的 Agent 范式。

第二个信号是 **AI 基础设施的精细化优化**。`LMCache` 今天的入榜，以及 `vllm` 的持续热门，说明在应用层繁荣的背后，社区对推理性能、成本、延迟的关注从未减弱。KV Cache 优化是当前推理优化的关键战场，`LMCache` 的出现暗示了新的技术突破点。

此外，**医疗 AI** 通过 `openmed` 强势登榜，以及 **AI 在金融 (`OpenBB`)、求职 (`career-ops`)、销售 (`pm-skills`)** 等垂直领域的深化应用，表明 AI 正加速在细分行业落地。特别是 `pm-skills` 这类项目，模糊了“Agent 框架”和“具体职业工具”的界限，预示着未来可能出现更多针对特定岗位的 AI 封装方案。

#### 4. 社区关注热点

- **🔥 `addyosmani/agent-skills`、`obra/superpowers` 和 `phuryn/pm-skills`**: **强烈关注**。它们是“Agent Skills”浪潮的领头羊。如果你正在构建 AI Agent，如何利用或贡献这些“技能”将直接影响 Agent 的能力边界和应用广度。
- **🔍 `mem0ai/mem0` 和 `thedotmack/claude-mem`**: 解决 Agent 关键短板——记忆。随着 Agent 被赋予更长周期、更复杂任务的能力，持久化和上下文相关的记忆系统将成为必需品。
- **⚡️ `LMCache/LMCache`**: 关注 LLM 推理性能优化的开发者需要研究。它可能成为降低企业 LLM 推理成本和提升用户体验的下一代关键技术。
- **🏥 `maziyarpanahi/openmed`**: 对于关注 AI 垂直应用的开发者而言，这是一个值得研究的方向。其技术栈（Python）和快速增长的星数，预示着医疗领域开源的潜力。
- **🧑‍💻 `msitarzewski/agency-agents`**: 提供了“多 Agent 公司”的实用化案例。该项目的组织和协作模式，可能成为未来复杂自动化系统的设计蓝本。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*