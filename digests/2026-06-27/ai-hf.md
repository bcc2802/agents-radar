# Hugging Face 热门模型日报 2026-06-27

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-27 03:23 UTC

---

好的，作为AI模型生态分析师，这是根据您提供的2026年6月27日数据生成的《Hugging Face 热门模型日报》。

---

# 🤗 Hugging Face 热门模型日报 | 2026-06-27

## 📰 今日速览

本周Hugging Face社区生态异常活跃，**GLM-5.2** 和 **Gemma-4-12B** 两大模型家族成为众人瞩目的焦点。**GLM-5.2** 凭借其巨大的参数量和MoE架构，在未量化版本和由Unsloth、NVIDIA提供的量化版本中均表现强劲，显示了其作为新一代基座模型的潜力。与此同时，**Qwen 3.5/3.6** 系列模型在社区微调版本（如Qwythos、Ornith）中持续衍生，尤其在视觉理解领域表现突出。值得注意的是，**NVIDIA** 和 **微软** 等大厂积极推动模型优化，如NVFP4量化工具和FastContext长上下文技术，推动模型走向实用化。此外，“Uncensored”（去审查）和“Agentic”（智能体）方向的社区模型热度不减，揭示了用户对模型自由度和工具使用能力的强烈需求。

## 🏆 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

- **[GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** | 作者: zai-org | 👍 2,608 | ⬇️ 83,589
  - **一句话**：基于MoE-DSA架构的巨型语言模型，以极高的社区关注度成为本周的现象级模型。
- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** | 作者: empero-ai | 👍 597 | ⬇️ 486,810
  - **一句话**：Qwen 3.5的社区优化版GGUF量化模型，下载量巨大，是社区对“类Claude”风格推理模型偏好的体现。
- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** | 作者: yuxinlu1 | 👍 2,402 | ⬇️ 516,333
  - **一句话**：基于Gemma-4-12B的代码优化版GGUF模型，结合了“Fable5”等先进微调技术，是代码领域的热门选择。
- **[WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)** | 作者: WeiboAI | 👍 735 | ⬇️ 54,638
  - **一句话**：基于Qwen2的3B参数轻量级模型，专注于数学推理，以出色的性能和效率在中小模型中脱颖而出。
- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** | 作者: HauhauCS | 👍 2,266 | ⬇️ 3,453,492
  - **一句话**：Qwen 3.6的“去审查”社区版本，下载量惊人，反映了用户对无限制对话模型的强烈需求。
- **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)** | 作者: nvidia | 👍 709 | ⬇️ 56,434
  - **一句话**：NVIDIA推出的流式语音识别模型，专注于低延迟实时转录场景，为语音交互提供了新选择。
- **[microsoft/FastContext-1.0-4B-SFT](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT)** | 作者: microsoft | 👍 356 | ⬇️ 5,735
  - **一句话**：微软发布的长上下文模型，解决了长文本处理中的效率瓶颈，具备成为“Agent”大脑的潜力。
- **[deepreinforce-ai/Ornith-1.0-397B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-397B)** | 作者: deepreinforce-ai | 👍 107 | ⬇️ 126
  - **一句话**：基于Qwen 3.5 MoE的巨型模型，尽管参数巨大，但获得了核心开发者的关注，预示着超大模型竞争的新方向。
- **[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LFM2.5-230M)** | 作者: LiquidAI | 👍 114 | ⬇️ 8,286
  - **一句话**：Liquid AI推出的230M超小参数模型，在资源受限场景下展现了不俗的语言能力。

### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** | 作者: baidu | 👍 1,052 | ⬇️ 134,146
  - **一句话**：百度的通用OCR模型，在图像转文字任务上表现出色，解决了大量场景下的文字识别需求。
- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** | 作者: krea | 👍 287 | ⬇️ 8,721
  - **一句话**：Krea公司推出的第二代文本到图像模型Turbo版，在生成速度和美学质量上取得平衡。
- **[MiniMaxAI/MiniMax-M3](https://huggingface.co/MiniMaxAI/MiniMax-M3)** | 作者: MiniMaxAI | 👍 1,247 | ⬇️ 169,951
  - **一句话**：MiniMax公司的第三代多模态大模型，支持图文理解，展示了其在视觉-语言领域的强大竞争力。
- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** | 作者: nvidia | 👍 2,386 | ⬇️ 494,756
  - **一句话**：NVIDIA推出的3B参数视觉定位模型，能精准定位图像中的任何物体，是视觉Agent的关键技术。

### 🔧 专用模型（代码、数学、医疗、嵌入）

- **(分类交叉) [yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**
  - **一句话**：尽管归类在语言模型，其专业性极强，专为代码生成和推理优化。
- **[WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)**
  - **一句话**：专注于数学领域的轻量级专用模型。

### 📦 微调与量化（社区微调、GGUF、AWQ）

- **[unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)** | 作者: unsloth | 👍 413 | ⬇️ 107,553
  - **一句话**：Unsloth团队为GLM-5.2推出的GGUF量化版，极大降低了该巨型模型的本地部署门槛。
- **[nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)** | 作者: nvidia | 👍 89 | ⬇️ 441
  - **一句话**：NVIDIA官方使用其Model Optimizer工具对GLM-5.2进行4-bit浮点量化，代表了最先进的工业级模型压缩方向。
- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)**
  - **一句话**：Qwen 3.5的优秀社区量化版本，高下载量印证了其出色的社区适配性。
- **[HauhauCS/Gemma4-12B-QAT-Uncensored-HauhauCS-Balanced](https://huggingface.co/HauhauCS/Gemma4-12B-QAT-Uncensored-HauhauCS-Balanced)** | 作者: HauhauCS | 👍 93 | ⬇️ 23,772
  - **一句话**：对Gemma-4-12B进行QAT（量化感知训练）并去审查的平衡版本，展现了社区微调的深度。

## 📈 生态信号

1.  **GLM系列与Gemma-4系列并驾齐驱**：GLM-5.2以其庞大的MoE规模和中文能力，与Google的Gemma-4-12B（尤其在代码和智能体领域）形成了最强竞争态势。两者不同的侧重点（通用vs专用）预示着未来基座模型的分化。
2.  **Qwen家族衍生模型“百花齐放”**：Qwen 3.5/3.6已成为最热门的“社区微调基座”。从去审查版本（HauhauCS）到融合多种SOTA技术的创意模型（Qwythos、Ornith），Qwen生态的繁荣程度无人能及。
3.  **量化成为“必选项”，工业界与社区工具齐飞**：GGUF和NVIDIA的NVFP4模型同时登榜，说明从个人开发者的本地化部署到企业的生产级优化，模型压缩和量化已不再是附加功能，而是模型发布的标配。

## 🔭 值得探索

1.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**：视觉定位是构建真正的多模态Agent的基石。这个模型体量适中、性能强大，是研究视觉理解、RPA（机器人流程自动化）和多模态交互的绝佳起点。
2.  **[microsoft/FastContext-1.0-4B-SFT](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT)**：长上下文是当前LLM的核心难题。微软的这个模型有望在保持小参数的同时解决效率问题，对于需要处理长文档、长对话的开发者来说，这是一个值得优先研究的解。
3.  **[WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)**：在追求“大而全”的潮流中，这个“小而美”的数学专用模型提供了一个重要的范式：在特定领域，精巧的设计和训练比堆砌参数更有效。它非常适合作为教育、金融等垂直领域的基座模型。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*