# Hugging Face 热门模型日报 2026-06-28

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-28 03:43 UTC

---

好的，作为AI模型生态分析师，以下是基于您提供的数据生成的《Hugging Face 热门模型日报》。

---

### 《Hugging Face 热门模型日报》— 2026年6月28日

#### 1. 今日速览

本周Hugging Face榜单呈现出“**模型大战与量化狂欢**”的态势。首先，**GLM-5.2**系列强势回归，多版本（基础版、GGUF版、NVIDIA优化版）同时上榜，表明开源社区对高能效MoE架构的持续追捧。其次，**DeepSeek-V4-Pro-DSpark**与NVIDIA的**Qwen3.6-35B-A3B-NVFP4**等超大规模模型开始提供FP4量化等极限压缩方案，标志着推理优化的军备竞赛进入新阶段。最后，社区微调异常活跃，**HauhauCS**推出的“Uncensored”系列模型获得极高下载量，反映了用户对“无审查”能力的刚性需求。

#### 2. 热门模型

**🧠 语言模型（LLM、对话模型、指令微调）**

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** | 作者: zai-org | 👍 2,690 | ⬇️ 98,994
  - **说明**: 基于MoE和DSA架构的GLM系列主力模型，凭借高效的参数量和高性能，迅速成为本周社区最受关注的通用语言模型之一。
- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** | 作者: HauhauCS | 👍 2,279 | ⬇️ 3,331,475
  - **说明**: Qwen3.6的社区无审查微调版，以极其夸张的下载量登顶，反映了用户对于“不设限”助手模型的巨大需求，“Aggressive”风格暗示了更激进的回复策略。
- **[WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)** | 作者: WeiboAI | 👍 742 | ⬇️ 57,521
  - **说明**: 一个基于Qwen2的3B级轻量级模型，专注于数学与推理，适合在资源受限场景下进行特定任务部署。
- **[microsoft/FastContext-1.0-4B-SFT](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT)** | 作者: microsoft | 👍 366 | ⬇️ 6,447
  - **说明**: 微软出品的小参数长上下文模型，专为长文档处理设计，并集成了“Explorer SubAgent”功能，为智能体应用提供了新思路。
- **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** | 作者: deepseek-ai | 👍 132 | ⬇️ 0
  - **说明**: DeepSeek-V4的旗舰Pro版本，附带DSpark推理优化。尽管下载量暂无（可能刚发布），但作为顶级开源模型的代表，其技术论文arXiv:2606.19348值得关注。
- **[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LFM2.5-230M)** | 作者: LiquidAI | 👍 130 | ⬇️ 9,791
  - **说明**: Liquid AI推出的极小型语言模型，证明了在小参数规模下也能实现有竞争力的性能，适合边缘部署。

**🎨 多模态与生成（图像、视频、音频、文本到X）**

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** | 作者: baidu | 👍 1,144 | ⬇️ 212,760
  - **说明**: 百度发布的“无限OCR”模型，定位为图像到文本的通用特征提取器，在文档分析、票据识别等场景具有巨大应用潜力。
- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** | 作者: nvidia | 👍 2,409 | ⬇️ 570,466
  - **说明**: NVIDIA推出的通用目标定位/检测模型，能通过文本或视觉提示在图像中找到任意物体，是计算机视觉领域的“全能选手”。
- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** | 作者: krea | 👍 311 | ⬇️ 17,445
  - **说明**: 图像生成模型Krea-2的Turbo加速版，基于Raw模型优化，在保持画质的同时显著提升生成速度。
- **[MiniMaxAI/MiniMax-M3](https://huggingface.co/MiniMaxAI/MiniMax-M3)** | 作者: MiniMaxAI | 👍 1,253 | ⬇️ 182,714
  - **说明**: MiniMax的最新一代多模态模型M3，延续了其在视频生成方面的技术积累，是目前视觉理解与生成任务的热门选择。
- **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)** | 作者: nvidia | 👍 719 | ⬇️ 61,857
  - **说明**: NVIDIA发布的流式语音识别模型，0.6B的参数量即可实现高精度实时转录，是语音交互应用的重要组件。

**🔧 专用模型（代码、数学、医疗、嵌入）**

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** | 作者: yuxinlu1 | 👍 2,430 | ⬇️ 536,130
  - **说明**: 基于Gemma 4打造的专用代码模型，经过“fable5”和“composer2.5”等高质量代码数据微调，是目前社区最热门的代码助手模型之一。
- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** | 作者: empero-ai | 👍 680 | ⬇️ 712,627
  - **说明**: 一个融合了Claude/Mythos风格的Qwen3.5变体，通过大量合成数据训练（5-1M），强调推理和角色扮演能力，量化版下载量极高。

**📦 微调与量化（社区微调、GGUF、AWQ）**

- **[unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)** | 作者: unsloth | 👍 426 | ⬇️ 125,230
  - **说明**: 知名训练加速框架Unsloth提供的GLM-5.2的GGUF量化版，方便用户在llama.cpp等本地推理框架中高效运行。
- **[nvidia/Qwen3.6-35B-A3B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4)** | 作者: nvidia | 👍 367 | ⬇️ 5,022,254
  - **说明**: NVIDIA对Qwen3.6的FP4量化版本，将175B模型压缩到极高效率，下载量冠绝全场，标志着企业级极限推理优化正式开源。
- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** | 作者: yuxinlu1 | 👍 736 | ⬇️ 206,828
  - **说明**: 专门为Agent（智能体）和终端操作微调的Gemma 4模型，量化后方便在自动化脚本和DevOps场景中本地部署。

#### 3. 生态信号

本周生态趋势明确：**MoE（混合专家）模型成为绝对主流**，GLM-5.2、Qwen3.6、DeepSeek-V4等顶尖模型均采用此架构，极好地平衡了性能与推理成本。**开源模型权重与闭源模型的差距进一步缩小**，DeepSeek-V4-Pro等旗舰模型直接对标闭源竞品。值得注意的是，**量化活动的繁荣已从“能不能用”转向“谁更好用”**，NVIDIA的FP4量化、社区的各种GGUF微调版下载量超过了基座模型，表明用户更关注在消费级硬件上的实际运行效果。此外，“**无审查（Uncensored）**”社区生态持续壮大，HauhauCS系列的成功验证了这一需求的旺盛。

#### 4. 值得探索

- **deepseek-ai/DeepSeek-V4-Pro-DSpark**: 作为目前最顶尖的开源模型之一，它代表了开源模型能力的尖端水平。研究者应关注其技术报告，探索其DSpark推理框架对长文本和复杂推理任务的支持。
- **nvidia/LocateAnything-3B**: 这是一个“即插即用”的视觉基础模型。通用性极强，如果你有图像搜索、目标跟踪或视觉问答的需求，直接拿来用可能会取得非常好的效果，值得研究其少样本定位能力。
- **nvidia/Qwen3.6-35B-A3B-NVFP4**: 它是目前“大模型平民化”的极致代表。强烈建议有本地部署需求的开发者和企业尝试，它证明了在消费级硬件上运行175B级别模型的可能性，是模型量化技术的里程碑。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*