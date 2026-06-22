# Hugging Face 热门模型日报 2026-06-22

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-22 04:10 UTC

---

好的，作为AI模型生态分析师，为您呈上2026年6月22日的《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026-06-22**

#### **今日速览**

本周Hugging Face生态呈现出三大核心趋势：**顶尖闭源模型利用量化与微调“曲线救国”登陆开源社区**，其中DeepSeek-V4-Pro以惊人的点赞数领跑；**MoE架构与超长上下文成为新一代基座模型标配**，从GLM-5.2到Qwen3.6家族无不体现此趋势；**多模态能力（尤其是图像理解）正快速渗透至语言模型**，大部分新晋热门模型都具备或多或少的视觉处理能力。值得注意的是，开源社区的“二创”热度不减，GGUF量化版本依然是用户下载的主力。

---

#### **热门模型**

##### 🧠 **语言模型（LLM、对话模型、指令微调）**

*   **[DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)** — 作者: deepseek-ai | 点赞: **4,999** | 下载: 2,611,991
    *   **一句话说明**：DeepSeek的新一代旗舰模型，凭借顶级的推理性能与对话体验，成为本周社区绝对焦点，点赞数断层式领先。
*   **[Qwen3.6-35B-A3B](https://huggingface.co/Qwen/Qwen3.6-35B-A3B)** — 作者: Qwen | 点赞: 2,198 | 下载: **5,148,673**
    *   **一句话说明**：Qwen家族的最新MoE模型，参数规模35B但推理仅需激活3B，在极致性价比的同时具备多模态能力，下载量惊人，是社区首选基准之一。
*   **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — 作者: zai-org | 点赞: 1,854 | 下载: 27,413
    *   **一句话说明**：智谱AI开源的最新基座模型，采用MoE-DSA架构，主打高效推理与强大对话能力，是国产模型的扛鼎之作。
*   **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — 作者: yuxinlu1 | 点赞: 2,095 | 下载: 358,677
    *   **一句话说明**：基于Google Gemma-4的精调“缝合怪”模型，专为代码与推理优化，其GGUF版本在本周下载量爆棚，是社区整合与量化能力的体现。
*   **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — 作者: HauhauCS | 点赞: 2,082 | 下载: **3,966,691**
    *   **一句话说明**：基于Qwen3.6的“无审查+激进人格”社区微调版，凭借其独特的交互风格吸引了海量用户下载，反映了开源社区对“去对齐”模型的旺盛需求。
*   **[google/gemma-4-12B-it](https://huggingface.co/google/gemma-4-12B-it)** — 作者: google | 点赞: 1,129 | 下载: 1,815,370
    *   **一句话说明**：Google官方的Gemma-4指令微调版，支持“Any-to-Any”的多模态输入输出，是目前最强的开放权重多模态模型之一。

##### 🎨 **多模态与生成（图像、视频、音频、文本到X）**

*   **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — 作者: nvidia | 点赞: **2,250** | 下载: 241,845
    *   **一句话说明**：NVIDIA推出的3B参数视觉定位模型，能够识别并定位图像中任意物体，在细分领域树立了新标杆，是本周非LLM模型中的最大黑马。
*   **[google/diffusiongemma-26B-A4B-it](https://huggingface.co/google/diffusiongemma-26B-A4B-it)** — 作者: google | 点赞: 1,037 | 下载: 762,861
    *   **一句话说明**：Google将扩散架构与语言模型结合的创新尝试，专精于图像-文本多模态理解与生成，代表了视觉语言模型的技术前沿。
*   **[moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code)** — 作者: moonshotai | 点赞: 946 | 下载: 363,308
    *   **一句话说明**：月之暗面推出的代码专用多模态模型，具备强大的代码理解和图像特征提取能力，是AI编程助手的强力竞争者。

##### 🔧 **专用模型（代码、数学、医疗、嵌入）**

*   **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)** — 作者: nvidia | 点赞: 614 | 下载: 27,275
    *   **一句话说明**：NVIDIA推出的超小型流式语音识别模型，专为边缘设备与实时场景设计，推动了语音AI的轻量化与实用化。
*   **[CohereLabs/North-Mini-Code-1.0](https://huggingface.co/CohereLabs/North-Mini-Code-1.0)** — 作者: CohereLabs | 点赞: 475 | 下载: 19,551
    *   **一句话说明**：Cohere发布的小型专业代码模型，采用MoE架构，意在提供高性能的同时降低部署门槛。
*   **[LiquidAI/LFM2.5-Embedding-350M](https://huggingface.co/LiquidAI/LiquidAI/LFM2.5-Embedding-350M)** — 作者: LiquidAI | 点赞: 94 | 下载: 7,726
    *   **一句话说明**：基于新型LFM架构的嵌入模型，为检索和语义相似度任务提供了新的高性能选择。

##### 📦 **微调与量化（社区微调、GGUF、AWQ）**

*   **[unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)** — 作者: unsloth | 点赞: 229 | 下载: 32,260
    *   **一句话说明**：知名量化团队Unsloth推出的GLM-5.2的GGUF版本，极大降低了这款旗舰模型的部署门槛。
*   **[Jackrong/Qwopus3.6-27B-Coder-MTP-GGUF](https://huggingface.co/Jackrong/Qwopus3.6-27B-Coder-MTP-GGUF)** — 作者: Jackrong | 点赞: 276 | 下载: 190,993
    *   **一句话说明**：社区成员对Qwen3.6-27B的代码增强版进行量化，融合了多模态视觉输入，是“魔改+量化”的典型案例。

---

#### **生态信号**

本周生态呈现出“**三大头部家族竞速，社区二创全面开花**”的格局：
1.  **模型家族**：**Qwen家族（3.6）** 凭借其强大的MoE架构和全面的多模态支持，生态影响力无出其右，几乎所有相关变体都获得了极高的热度。**Google Gemma-4** 紧随其后，展示了大型科技公司开源顶级模型的决心。**DeepSeek-V4-Pro** 的王者归来，证明其推理赛道地位依然稳固。
2.  **开源 vs 闭源**：闭源模型（如Kimi K2、部分Gemma/DeepSeek变体）通过社区微调、GGUF/AWQ等格式加速“渗透”至开源生态，这一“**间接开源**”趋势愈发明显。直接进行权重硬开源的模型已不再是唯一流量密码。
3.  **量化与微调**：**GGUF格式**依然是落地部署的绝对王者，几乎所有高下载量模型都包含其量化版本。社区微调活动极度活跃，尤其是在“**去审查**”和“**特定角色人格**”方向，反映了用户对个性化、定制化模型的迫切需求。

---

#### **值得探索**

1.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**：强烈推荐你**尝试其视觉定位能力**。它证明了在特定垂域任务上，小模型也能通过精准设计达到SOTA水平，极具研究和部署价值。
2.  **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** (或其GGUF版)：若你是**架构探索者**，这款采用MoE-DSA架构的模型值得深入研究，它代表了类MoE架构的最新演进方向，且原生支持中文，效果优异。
3.  **[microsoft/FastContext-1.0-4B-SFT](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT)**：虽然热度不高，但作为微软推出的**专注超长上下文和Agent行为的小模型**，它在工程落地和Agent应用中极具潜力，值得专业的RAG/Agent开发者深入挖掘。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*