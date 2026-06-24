# Hugging Face 热门模型日报 2026-06-24

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-24 03:32 UTC

---

好的，作为 AI 模型生态分析师，以下是 2026-06-24 基于 Hugging Face 热门榜生成的模型日报。

---

### 《Hugging Face 热门模型日报》2026-06-24

#### 1. 今日速览

本周 Hugging Face 榜单由国产大模型 **DeepSeek-V4-Pro** 的正式发布强势领跑，展现了开源社区的强大号召力。与此同时，**Google** 的 **Gemma 4** 家族与 **MiniMax-M3** 等前沿多模态模型热度不减，表明“统一模型”正在成为主流。值得注意的是，量化社区活动异常活跃，基于 **Qwen3.6** 和 **Gemma-4** 的 GGUF 或微调版本占据了榜单大量席位，证明了开发者对模型本地化部署和定制化的迫切需求。此外，**NVIDIA** 等大厂在细分领域（OCR、语音）的新模型也引发了广泛关注。

#### 2. 热门模型

##### 🧠 语言模型（LLM、对话模型、指令微调）

- **deepseek-ai/DeepSeek-V4-Pro** (deepseek-ai | 点赞: 5,031 | 下载: 2.2M)
  - **说明**: 本周最重磅的发布，DeepSeek最新的旗舰开源模型。凭借强大的性能和极高的社区期待，上线即登顶，并带动了大规模的下载。
  - **链接**: [https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)

- **zai-org/GLM-5.2** (zai-org | 点赞: 2,209 | 下载: 40K)
  - **说明**: 智谱AI推出的新一代MoE架构模型，其独特的“DSA”稀疏注意力机制备受关注，是本周技术讨论的焦点之一。
  - **链接**: [https://huggingface.co/zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)

- **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive** (HauhauCS | 点赞: 2,161 | 下载: 3.9M)
  - **说明**: 社区微调的Qwen3.6模型，极高的下载量反映了对“无审查”和高性能小型MoE模型的巨大需求量。
  - **链接**: [https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)

- **moonshotai/Kimi-K2.7-Code** (moonshotai | 点赞: 977 | 下载: 447K)
  - **说明**: 月之暗面发布的Kimi系列代码模型，采用压缩张量技术，表明其在高性能与经济效益之间寻求平衡，是专业编码领域的强劲选手。
  - **链接**: [https://huggingface.co/moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code)

- **microsoft/FastContext-1.0-4B-SFT** (microsoft | 点赞: 323 | 下载: 4K)
  - **说明**: 微软推出的“快速上下文”模型，专注于长上下文处理优化并引入代理能力，代表了LLM在专业工作流中的应用方向。
  - **链接**: [https://huggingface.co/microsoft/FastContext-1.0-4B-SFT](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT)

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **google/gemma-4-12B-it** (google | 点赞: 1,156 | 下载: 1.9M)
  - **说明**: Google最新的“任意到任意”多模态模型，能处理和生成文本与图像，代表了前沿的通用模型范式，下载量极高。
  - **链接**: [https://huggingface.co/google/gemma-4-12B-it](https://huggingface.co/google/gemma-4-12B-it)

- **nvidia/LocateAnything-3B** (nvidia | 点赞: 2,322 | 下载: 274K)
  - **说明**: 英伟达推出的高效物体定位与分割模型，在图像理解任务上表现出色，展现了“大公司做小模型，解决特定问题”的趋势。
  - **链接**: [https://huggingface.co/nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)

- **MiniMaxAI/MiniMax-M3** (MiniMaxAI | 点赞: 1,222 | 下载: 131K)
  - **说明**: MiniMax的第三代旗舰多模态模型，延续了其在长语境和多模态理解上的技术优势，是国内开源生态的重要力量。
  - **链接**: [https://huggingface.co/MiniMaxAI/MiniMax-M3](https://huggingface.co/MiniMaxAI/MiniMax-M3)

- **baidu/Unlimited-OCR** (baidu | 点赞: 507 | 下载: 8K)
  - **说明**: 百度开源的通用OCR模型，旨在解决各类复杂场景下的文字识别问题，正式拉开了AI在垂直行业应用的又一战场。
  - **链接**: [https://huggingface.co/baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)

- **nvidia/nemotron-3.5-asr-streaming-0.6b** (nvidia | 点赞: 659 | 下载: 41K)
  - **说明**: 英伟达的流式语音识别模型，专门优化了边缘设备上的性能，是实时语音AI应用的重要基石。
  - **链接**: [https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)

##### 🔧 专用模型（代码、数学、医疗、嵌入）

- **yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF** (yuxinlu1 | 点赞: 2,246 | 下载: 456K)
  - **说明**: 基于Gemma-4的代码优化模型，通过新的合成数据集“Fable5”和“Composer 2.5”技术实现推理能力飞跃，是本周社区量化版的“明星”。
  - **链接**: [https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)

- **LiquidAI/LFM2.5-Embedding-350M** (LiquidAI | 点赞: 115 | 下载: 10K)
  - **说明**: Liquid AI推出的第二代嵌入模型，其高效的架构和350M的轻量级参数，为RAG（检索增强生成）等应用提供了新的基础设施选择。
  - **链接**: [https://huggingface.co/LiquidAI/LFM2.5-Embedding-350M](https://huggingface.co/LiquidAI/LFM2.5-Embedding-350M)

##### 📦 微调与量化（社区微调、GGUF、AWQ）

- **unsloth/GLM-5.2-GGUF** (unsloth | 点赞: 307 | 下载: 55K)
  - **说明**: Unsloth团队为GLM-5.2提供的官方量化版本，极大地降低了该尖端模型的部署门槛，体现了社区与模型原始团队的紧密合作。
  - **链接**: [https://huggingface.co/unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)

- **huihui-ai/Huihui-gemma-4-12B-coder-fable5-composer2.5-v1-abliterated** (huihui-ai | 点赞: 114 | 下载: 3K)
  - **说明**: 在Gemma-4代码模型基础上进行“去审查”的移植尝试，虽然下载量不高，但“Abliterated”技术持续成为社区争议和实验的焦点。
  - **链接**: [https://huggingface.co/huihui-ai/Huihui-gemma-4-12B-coder-fable5-composer2.5-v1-abliterated](https://huggingface.co/huihui-ai/Huihui-gemma-4-12B-coder-fable5-composer2.5-v1-abliterated)

#### 3. 生态信号

本周生态呈现三大趋势：**第一，模型家族权力更迭**。DeepSeek-V4和GLM-5.2的爆发性增长，挑战了Llama与Qwen的传统主导地位，表明中国开源模型力量正在崛起。**第二，“开源即标准”的趋势持续深化**。榜单中几乎所有头部模型均为开源权重（如DeepSeek, Gemma, GLM），闭源模型在社区讨论中难觅踪影。**第三，量化社区进入“军备竞赛”**。围绕Gemma-4和Qwen3.6，多个社区成员发布精心调优的GGUF版本（如`yuxinlu1`的版本下载量极高），这预示着未来基础模型的竞争力将部分取决于其微调和部署的生态活力。

#### 4. 值得探索

- **deepseek-ai/DeepSeek-V4-Pro**: **强烈推荐**。作为本周的“王者”，应当第一时间下载试用，体验其对话和推理能力的新高度，并关注其相比V3的架构创新。
- **nvidia/LocateAnything-3B**: **强烈推荐**。如果你想探索高效的图像理解工具，这个模型非常值得研究。它展示了在特定任务上，精悍的小模型也能有很高的商业和学术价值。
- **google/gemma-4-12B-it**: **值得尝试**。这是“统一模型”（Any-to-Any）的先驱之一。建议用它处理同时包含文本和图像的任务，评估其跨模态理解和生成能力，这对未来AI应用形态有重要启发。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*