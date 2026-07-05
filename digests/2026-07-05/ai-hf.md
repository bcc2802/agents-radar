# Hugging Face 热门模型日报 2026-07-05

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-05 08:06 UTC

---

好的，作为AI模型生态分析师，为您呈上2026年7月5日的Hugging Face热门模型日报。

---

### **Hugging Face 热门模型日报 | 2026-07-05**

#### **1. 今日速览**

本周Hugging Face生态呈现出“多模态落地”与“极致量化”双轨并行的态势。**NVIDIA**凭借`LocateAnything-3B`在多模态定位任务上取得现象级关注，而**百度**推出的`Unlimited-OCR`则展示了工业级OCR的极限能力。在语言模型领域，**DeepSeek**正式发布其V4系列的两个变体（Pro/Fash），定义新一代大模型技术路线。同时，**Qwen3.5/3.6**系列模型生态极度繁荣，大量社区微调与量化版本（如GGUF、Uncensored变体）霸榜，显示出其作为新一代基础模型的核心地位。

---

#### **2. 热门模型**

##### 🧠 语言模型（LLM、对话模型、指令微调）

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** | 作者: zai-org | 👍 3,414 | 📥 208,920
  - **说明**：智谱GLM-5.2的完整基础版本，是本周点赞数最高的模型，凭借MoE架构和强大的对话能力成为社区焦点。
- **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** | 作者: deepseek-ai | 👍 374 | 📥 10,306
  - **说明**：DeepSeek V4系列的专业版（Pro），支持高强度的Spark推理加速，展现了前沿大模型的技术突破。
- **[deepseek-ai/DeepSeek-V4-Flash-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-DSpark)** | 作者: deepseek-ai | 👍 158 | 📥 40,271
  - **说明**：V4系列的快速版（Flash），在保持性能的同时优化推理速度，通常用于对延迟敏感的在线服务。
- **[mistralai/Leanstral-1.5-119B-A6B](https://huggingface.co/mistralai/Leanstral-1.5-119B-A6B)** | 作者: mistralai | 👍 103 | 📥 4
  - **说明**：Mistral推出的超大规模MoE模型（119B总参/6B激活），专注于极致效率，目前下载量小但关注度高。
- **[Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)** | 作者: Qwen | 👍 537 | 📥 50,188
  - **说明**：阿里通义千问推出的Agent专用模型，在智能体任务上进行了专项优化，是Agent生态的重要补充。

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** | 作者: nvidia | 👍 2,607 | 📥 1,247,265
  - **说明**：NVIDIA推出的零样本目标定位模型，能以极小的参数量实现“找万物”能力，下载量与点赞量双高。
- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** | 作者: empero-ai | 👍 1,480 | 📥 1,464,047
  - **说明**：基于Qwen3.5微调并获得Claude风格推理能力的多模态模型量化版，下载量巨大，是社区微调与量化结合的典范。
- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** | 作者: baidu | 👍 1,718 | 📥 988,379
  - **说明**：百度发布的“无限制”OCR模型，在各类复杂场景下表现优异，极大降低了OCR应用门槛。
- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** | 作者: krea | 👍 500 | 📥 89,384
  - **说明**：Krea公司推出的第二代文生图模型加速版（Turbo），在生成速度与质量之间取得平衡。
- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** | 作者: HauhauCS | 👍 2,460 | 📥 2,993,053
  - **说明**：社区对Qwen3.6的极致魔改版，取消内容审查（Uncensored）并采用激进微调，下载量近300万，反映了对开放型多模态模型的巨大需求。
- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** | 作者: yuxinlu1 | 👍 2,596 | 📥 641,260
  - **说明**：Gemma-4的代码优化变体量化版，结合了“fable”与“composer”架构，在代码生成和推理任务上评价极高。

##### 🔧 专用模型（代码、数学、医疗、嵌入）

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** | 作者: google | 👍 205 | 📥 1,177
  - **说明**：Google推出的表格数据基础模型，支持零样本的分类与回归，是“基础模型+结构化数据”领域的重大突破。
- **[nationaldesignstudio/rampart](https://huggingface.co/nationaldesignstudio/rampart)** | 作者: nationaldesignstudio | 👍 124 | 📥 1,881
  - **说明**：专为PII（个人可识别信息）检测优化的BERT模型，经过ONNX转换，适用于浏览器端敏感信息识别。
- **[BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6)** | 作者: BugTraceAI | 👍 132 | 📥 12,001
  - **说明**：专注于网络安全与渗透测试的模型，展示了LLM在垂直安全领域的深度应用。

##### 📦 微调与量化（社区微调、GGUF、AWQ）

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** | 作者: deepreinforce-ai | 👍 714 | 📥 359,659
  - **说明**：Ornith系列35B模型量化版，基于Qwen3.5 MoE架构，是高性能低成本部署的优选。
- **[huihui-ai/Huihui-GLM-5.2-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-GLM-5.2-abliterated-GGUF)** | 作者: huihui-ai | 👍 163 | 📥 4,701
  - **说明**：对GLM-5.2进行“去审查化”（Abliterated）处理后的GGUF版本，专门面向需要高自由度内容生成的用户。
- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** | 作者: yuxinlu1 | 👍 1,015 | 📥 342,752
  - **说明**：Gemma-4的Agent化微调版量化模型，专为终端Agent任务设计，标志着小型代理模型时代的到来。

---

#### **3. 生态信号**

1.  **模型家族动态：** **Qwen3.5/3.6** 已取代Qwen2成为社区最活跃的基础模型，衍生出数十种MoE变体。**DeepSeek V4** 的发布标志着大模型技术进入“架构+推理优化”双轮驱动阶段。**Gemma-4** 则在Agent和编程任务上展现了极强的可塑性。
2.  **开源权重趋势：** 顶级模型的权重已完全实现开源，且社区在“去审查化”（Abliterated）实践上愈发激进，反映出用户对模型自由度的需求超越了对安全边界的保守考量。
3.  **量化生态成熟：** **GGUF** 格式仍是本地部署的绝对主流，几乎每个热门模型都会配套推出GGUF版本。NVIDIA通过`NVFP4`格式主导了数据中心级别的超低精度部署方案。量化正从“能用”走向“好用”，社区更关注量化后的推理速度、幻觉率下降和IQ保持度。

---

#### **4. 值得探索**

1.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**：强烈推荐。它用一个3B小模型就解决了传统CV中的视觉定位难题，是“小模型大能力”的完美例证，值得在多模态应用和机器人领域深入挖掘。
2.  **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)**：技术前沿者必看。作为今年最具冲击力的模型家族，结合V4架构与DSpark推理加速，代表了当前开源大模型性能的顶流水平。
3.  **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)**：数据科学从业者必试。如果它能将零样本表格分类达到理想效果，将颠覆传统ML工作流，是连接大模型与结构化数据世界的桥梁。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*