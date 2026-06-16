# Hugging Face 热门模型日报 2026-06-16

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-16 04:03 UTC

---

好的，作为AI模型生态分析师，以下是为你整理的2026年6月16日《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026-06-16**

#### **今日速览**

今日Hugging Face生态呈现“巨头领跑、社区狂欢”的态势。**DeepSeek-V4-Pro** 凭借近5000点赞的断层优势登顶，标志着开源大模型进入新的竞争阶段。同时，**Gemma 4** 系列生态持续爆发，从官方基础版到社区微调、量化版本（GGUF）全面开花。多模态模型成为绝对主流，**image-text-to-text** 任务占据榜单半壁江山，而 **nvidia/LocateAnything-3B** 凭借其强大的图像定位能力成为黑马。量化与微调活动异常活跃，尤其是 **Unsloth** 团队贡献了多个高下载量的GGUF版本。

---

#### **热门模型**

##### 🧠 语言模型（LLM、对话模型、指令微调）

- **[deepseek-ai/DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)**
  - 作者: deepseek-ai | 点赞: 4,868 | 下载: 2,934,763
  - **一句话说明**: DeepSeek的最新旗舰模型，以绝对优势成为本周关注度最高的模型，代表了当前开源社区对顶尖文本生成能力的渴望。

- **[CohereLabs/North-Mini-Code-1.0](https://huggingface.co/CohereLabs/North-Mini-Code-1.0)**
  - 作者: CohereLabs | 点赞: 392 | 下载: 11,145
  - **一句话说明**: Cohere推出的MoE架构代码专用小模型，兼顾性能与效率，是代码助手领域的强力竞争者。

- **[microsoft/FastContext-1.0-4B-SFT](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT)**
  - 作者: microsoft | 点赞: 109 | 下载: 13
  - **一句话说明**: 微软新推出的专注长上下文处理的小模型，虽然刚发布，但“FastContext”概念潜力巨大。

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **[google/diffusiongemma-26B-A4B-it](https://huggingface.co/google/diffusiongemma-26B-A4B-it)**
  - 作者: google | 点赞: 886 | 下载: 311,788
  - **一句话说明**: Google推出的稀疏激活多模态模型，首次将Diffusion与Gemma架构融合，引领了对话式图像生成新范式。

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**
  - 作者: nvidia | 点赞: 2,059 | 下载: 86,968
  - **一句话说明**: NVIDIA推出的强大图像定位模型，能通过文本指令精准定位图像中的任意物体，是本周的黑马。

- **[Zyphra/ZONOS2](https://huggingface.co/Zyphra/ZONOS2)**
  - 作者: Zyphra | 点赞: 90 | 下载: 414
  - **一句话说明**: 新一代文本转语音模型，音质与自然度表现优异，为语音交互应用提供了新选择。

- **[ideogram-ai/ideogram-4-fp8](https://huggingface.co/ideogram-ai/ideogram-4-fp8)**
  - 作者: ideogram-ai | 点赞: 548 | 下载: 10,748
  - **一句话说明**: Ideogram最新版本的FP8量化版，在保持高质量图像生成的同时大幅降低了推理成本。

- **[bosonai/higgs-audio-v3-tts-4b](https://huggingface.co/bosonai/higgs-audio-v3-tts-4b)**
  - 作者: bosonai | 点赞: 445 | 下载: 38,429
  - **一句话说明**: 基于Qwen架构的4B参数TTS模型，体现了多模态大模型在语音领域的应用深化。

- **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)**
  - 作者: nvidia | 点赞: 422 | 下载: 5,200
  - **一句话说明**: 首个具备缓存感知的流式语音识别模型，专为低延迟实时场景设计。

##### 🔧 专用模型（代码、数学、医疗、嵌入）

- **[moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code)**
  - 作者: moonshotai | 点赞: 750 | 下载: 56,750
  - **一句话说明**: 月之暗面推出的代码版Kimi模型，采用压缩张量技术，在代码理解和生成上表现突出。

##### 📦 微调与量化（社区微调、GGUF、AWQ）

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**
  - 作者: HauhauCS | 点赞: 1,859 | 下载: 2,697,882
  - **一句话说明**: 基于Qwen3.6的社区“无审查”微调版，下载量极高，反映了社区对开放性和自由度的强烈需求。

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**
  - 作者: yuxinlu1 | 点赞: 678 | 下载: 20,207
  - **一句话说明**: Gemma-4的社区代码微调+GGUF量化版本，是社区将官方模型进行二次开发并部署的典范。

- **[unsloth/gemma-4-12b-it-GGUF](https://huggingface.co/unsloth/gemma-4-12b-it-GGUF)**
  - 作者: unsloth | 点赞: 618 | 下载: 980,781
  - **一句话说明**: Unsloth团队为Gemma-4提供的GGUF量化版，极大降低了本地部署门槛，是实用主义的代表。

- **[DavidAU/Qwen3.6-40B-Claude-4.6-Opus-Deckard-Heretic-Uncensored-Thinking-NEO-CODE-Di-IMatrix-MAX-GGUF](https://huggingface.co/DavidAU/Qwen3.6-40B-Claude-4.6-Opus-Deckard-Heretic-Uncensored-Thinking-NEO-CODE-Di-IMatrix-MAX-GGUF)**
  - 作者: DavidAU | 点赞: 359 | 下载: 369,526
  - **一句话说明**: 一个充满实验性的社区“缝合怪”模型，融合了多个模型特性，反映了社区的探索精神。

---

#### **生态信号**

1.  **模型家族格局：** **DeepSeek V4** 和 **Gemma 4** 是目前最强势的两大家族。DeepSeek V4 Pro凭借顶尖性能占据技术高地，而Gemma 4则通过官方和社区的共同推动，形成了从基础权重到量化、微调的完整生态拼图。
2.  **开源与闭源：** 榜单显示，完全开源的模型（如DeepSeek, Gemma）和社区二次开发版本占据了绝对主导权。虽然闭源API模型仍在发展，但社区通过微调和量化，正在将这些最强开源权重变为任何人都可运行的实际工具。
3.  **量化与微调活动：** **GGUF** 格式已成为社区部署的事实标准，几乎所有热门模型都有对应的GGUF版本。微调活动百花齐放，特别是以“Uncensored”和特定任务（如代码）为导向的模型，下载量非常惊人，说明社区用户不仅追求性能，也看重开放性和实用性。

---

#### **值得探索**

1.  **[google/diffusiongemma-26B-A4B-it](https://huggingface.co/google/diffusiongemma-26B-A4B-it)**: 如果你想了解多模态大模型的下一个前沿方向，这个将扩散模型与LLM结合的模型不容错过。它不仅仅是看图说话，更在探索新的交互范式。
2.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**: 如果你的工作涉及任何“视觉定位”或“基于文本的视觉搜索”，这是一个必须上手的工具。3B的参数量级使其在性能和效率之间取得了绝佳平衡。
3.  **[unsloth/gemma-4-12b-it-GGUF](https://huggingface.co/unsloth/gemma-4-12b-it-GGUF)**: 如果你希望在实际场景中体验Gemma 4的强大能力，这个GGUF版本无疑是最佳选择。它是连接前沿研究模型与本地化、私有化应用的桥梁，也是量化技术的典范之作。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*