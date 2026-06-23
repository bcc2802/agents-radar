# Hugging Face 热门模型日报 2026-06-23

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-23 03:31 UTC

---

好的，作为AI模型生态分析师，这是为您整理的2026年6月23日《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026年6月23日**

#### **今日速览**

今日Hugging Face榜单巨头争锋，**DeepSeek-V4-Pro** 以绝对优势登顶，展现中国大模型的强劲实力。**谷歌的Gemma-4系列**与**英伟达的LocateAnything-3B**等多模态模型备受青睐，标志着行业焦点正加速向“全能感知”模型转移。此外，社区围绕**Qwen3.6**和**GLM-5.2**的量化微调活动异常活跃，显示出开源生态的强大生命力。值得关注的是，混合专家模型（MoE）架构已成为主流，从顶尖模型到社区微调版本均普遍采用。

---

### **热门模型分类整理**

#### 🧠 语言模型（LLM、对话模型、指令微调）

- **[deepseek-ai/DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)**
  - 作者: deepseek-ai | 点赞: 5,015 | 下载: 2,421,858
  - 一句话说明：DeepSeek最新旗舰级对话模型，以绝对领先的点赞数成为本周最受关注的模型，延续了其在语言理解和生成上的顶尖水平。

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**
  - 作者: zai-org | 点赞: 2,049 | 下载: 33,589
  - 一句话说明：智谱AI推出的新一代GLM模型，采用MoE架构（`glm_moe_dsa`），代表了国内模型在效率与性能平衡上的前沿探索。

- **[google/gemma-4-12B-it](https://huggingface.co/google/gemma-4-12B-it)**
  - 作者: google | 点赞: 1,139 | 下载: 1,912,198
  - 一句话说明：谷歌的Gemma-4指令微调版，支持“any-to-any”多种输入输出模态，是全能型开源模型的标杆。

- **[microsoft/FastContext-1.0-4B-SFT](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT)**
  - 作者: microsoft | 点赞: 290 | 下载: 3,498
  - 一句话说明：微软推出的小参数高效长上下文模型，定位为“探索者子代理”，暗示了未来Agent应用中对轻量级推理模型的需求。

#### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**
  - 作者: nvidia | 点赞: 2,294 | 下载: 247,517
  - 一句话说明：英伟达推出的通用物体定位模型，3B参数实现高效的图像特征提取和目标定位，是计算机视觉领域的明星项目。

- **[MiniMaxAI/MiniMax-M3](https://huggingface.co/MiniMaxAI/MiniMax-M3)**
  - 作者: MiniMaxAI | 点赞: 1,209 | 下载: 119,967
  - 一句话说明：MiniMax的第三代多模态模型（`image-text-to-text`），在图像理解与文本生成结合方面表现出色。

- **[google/diffusiongemma-26B-A4B-it](https://huggingface.co/google/diffusiongemma-26B-A4B-it)**
  - 作者: google | 点赞: 1,050 | 下载: 874,368
  - 一句话说明：谷歌结合扩散模型与Gemma的语言能力，26B总参数但仅激活4B的MoE模型，为多模态生成设立了新方向。

- **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nvidia/nemotron-3.5-asr-streaming-0.6b)**
  - 作者: nvidia | 点赞: 631 | 下载: 34,860
  - 一句话说明：英伟达推出的流式语音识别模型，针对实时语音处理场景进行了缓存优化，小巧高效。

#### 🔧 专用模型（代码、数学、医疗、嵌入）

- **[moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code)**
  - 作者: moonshotai | 点赞: 964 | 下载: 412,778
  - 一句话说明：月之暗面推出的Kimi代码专用模型，虽是多模态架构，但聚焦于代码理解和生成，下载量巨大。

- **[WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)**
  - 作者: WeiboAI | 点赞: 616 | 下载: 32,385
  - 一句话说明：微博AI团队推出的专注于数学推理的小模型，证明了在特定领域小参数模型也能取得高质量成果。

- **[CohereLabs/North-Mini-Code-1.0](https://huggingface.co/CohereLabs/North-Mini-Code-1.0)**
  - 作者: CohereLabs | 点赞: 482 | 下载: 21,078
  - 一句话说明：Cohere推出的代码专用MoE迷你模型，专注于提升编码任务的效率。

- **[LiquidAI/LFM2.5-Embedding-350M](https://huggingface.co/LiquidAI/LFM2.5-Embedding-350M)**
  - 作者: LiquidAI | 点赞: 101 | 下载: 8,822
  - 一句话说明：Liquid AI推出的文本嵌入模型，用于句子相似度计算，是构建RAG（检索增强生成）系统的重要组件。

#### 📦 微调与量化（社区微调、GGUF、AWQ）

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**
  - 作者: yuxinlu1 | 点赞: 2,176 | 下载: 414,734
  - 一句话说明：基于谷歌Gemma-4-12B的社区代码增强版GGUF量化模型，是本周社区微调和量化活动中最成功的案例之一。

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**
  - 作者: HauhauCS | 点赞: 2,118 | 下载: 4,078,305
  - 一句话说明：基于Qwen3.6的35B模型MoE（激活3B）的无审查版GGUF量化包，其极高的下载量反映了社区对“强能力+轻量部署”的强烈需求。

- **[impero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)**
  - 作者: empero-ai | 点赞: 142 | 下载: 6,633
  - 一句话说明：基于Qwen3.5、融合了Claude风格对话数据的社区微调GGUF模型，展现了LLM风格迁移的社区实践。

---

### **生态信号**

1.  **模型家族双雄争霸**：**Qwen (阿里巴巴)** 和 **Gemma (谷歌)** 两大模型家族生态最为繁荣。前者以Qwen3.6为核心，涌现出大量社区微调版（如`Qwable`、`Qwythos`）；后者则通过`gemma-4-12B-it`及其衍生微调版（如`gemma-4-12B-coder`）展现了强大的统治力。

2.  **开源权重主导社区**：本周榜单前15名中，绝大多数为开源模型。闭源模型（如某些多模态工具的LoRA）仅出现在榜单末端。这表明**开源模型与权重开放**依然是Hugging Face社区活力的核心驱动力。

3.  **MoE + GGUF = 大众化**：几乎所有热门模型（DeepSeek-V4-Pro, GLM-5.2, Gemma-4, Qwen3.6系列）都采用或衍生了**混合专家（MoE）** 架构，以实现高性能与低激活参数的平衡。同时，**GGUF**量化版本因其极强的本地部署便利性，成为社区微调的主要分发格式，下载量动辄数十万甚至上百万。

---

### **值得探索**

1.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**
    - **理由**：英伟达官方支持，小而美的通用物体定位模型。对于从事CV、机器人或自动驾驶领域的研究者，这是极佳的即用型基础模型，其高效性值得深入研究。

2.  **[microsoft/FastContext-1.0-4B-SFT](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT)**
    - **理由**：微软定义的新模型类别“Explorer SubAgent”。这表明未来的AI应用将从单一大模型转向由多个小型、高效、专业化的“Agent”模型协同工作。理解这个模型的思路对构建下一代AI系统至关重要。

3.  **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**
    - **理由**：这是社区微调能力的绝佳案例。它基于最新的谷歌Gemma-4模型，并通过精细的数据配比（`fable5-composer2.5`）和高效的GGUF量化，达到了超高的点赞和下载。如果你想学习最新的模型微调与量化范式，这个项目是最好的起点。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*