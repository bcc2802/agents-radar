# Hugging Face 热门模型日报 2026-06-19

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-19 04:15 UTC

---

好的，作为 AI 模型生态分析师，以下是我基于 2026-06-19 数据生成的《Hugging Face 热门模型日报》。

---

## Hugging Face 热门模型日报 | 2026-06-19

### 📰 今日速览

本周 Hugging Face 生态呈现三大核心趋势：**“去中心化”的模型微调与合并**与**巨头官方发布**分庭抗礼。DeepSeek-V4-Pro 以近 5,000 点赞和近 300 万下载量稳固其“社区霸主”地位。同时，英伟达的 `LocateAnything-3B` 凭借高点赞数成为视觉领域的现象级产品。值得注意的是，社区对 **Qwen3.6** 和 **Gemma-4** 系列的热情持续高涨，大量基于它们的微调版（特别是 GGUF 量化版）占据了榜单的半壁江山，表明社区正从“追新”转向“精调与部署”。此外，以 `zai-org` 发布的 `GLM-5.2` 和 `SCAIL-2` 为代表的国产模型在大模型和多模态生成领域正获得广泛关注。

### 🏆 热门模型

#### 🧠 语言模型（LLM、对话模型、指令微调）

- **[deepseek-ai/DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)**
  - 作者: deepseek-ai | 点赞: 4,957 | 下载: 2,948,726
  - 一句话：DeepSeek 的最新旗舰 Pro 版，凭借极强的推理与对话能力，成为了目前社区最炙手可热的大模型。
- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**
  - 作者: zai-org | 点赞: 1,362 | 下载: 4,307
  - 一句话：智谱 AI 推出的 MoE 架构大模型，展示了国产模型在开源社区中的强劲影响力。
- **[WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)**
  - 作者: WeiboAI | 点赞: 410 | 下载: 6,589
  - 一句话：一个在数学和推理任务上表现出色的小型模型（3B），验证了小参数模型在垂直领域的潜力。
- **[microsoft/FastContext-1.0-4B-SFT](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT)**
  - 作者: microsoft | 点赞: 207 | 下载: 957
  - 一句话：微软出品，专注于长上下文处理的 4B 模型，为解决长文本任务提供了高效新选择。

#### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**
  - 作者: nvidia | 点赞: 2,166 | 下载: 183,093
  - 一句话：英伟达的零样本目标检测/定位模型，凭借极高的识别精度和通用性，成为本周视觉领域的明星。
- **[google/diffusiongemma-26B-A4B-it](https://huggingface.co/google/diffusiongemma-26B-A4B-it)**
  - 作者: google | 点赞: 1,005 | 下载: 527,080
  - 一句话：Google 将 Gemma 与扩散模型结合的产物，是“文本到多模态生成”的重要尝试，下载量极高。
- **[MiniMaxAI/MiniMax-M3](https://huggingface.co/MiniMaxAI/MiniMax-M3)**
  - 作者: MiniMaxAI | 点赞: 1,103 | 下载: 56,162
  - 一句话：MiniMax 的最新多模态模型，主打图文理解，是国产多模态模型的代表之一。
- **[moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code)**
  - 作者: moonshotai | 点赞: 889 | 下载: 229,156
  - 一句话：月之暗面推出的代码专用多模态版本，具备强大的图像内代码理解和生成能力。
- **[google/gemma-4-12B-it](https://huggingface.co/google/gemma-4-12B-it)**
  - 作者: google | 点赞: 1,085 | 下载: 1,309,625
  - 一句话：Gemma-4 的官方指令微调版，支持“any-to-any”多模态，是 Google 布局开源多模态的关键模型。
- **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)**
  - 作者: nvidia | 点赞: 545 | 下载: 13,033
  - 一句话：英伟达为流式语音识别场景定制的小型高效模型，展示了专用 ASR 模型的重要性。
- **[bosonai/higgs-audio-v3-tts-4b](https://huggingface.co/bosonai/higgs-audio-v3-tts-4b)**
  - 作者: bosonai | 点赞: 489 | 下载: 57,380
  - 一句话：一个基于多模态模型的高质量文本转语音（TTS）模型，代表了“音频内容生成”的趋势。
- **[zai-org/SCAIL-2](https://huggingface.co/zai-org/SCAIL-2)**
  - 作者: zai-org | 点赞: 228 | 下载: 0
  - 一句话：智谱推出的“图片到视频”生成模型，专注于角色动画，是视频生成领域的新生力量。

#### 🔧 专用模型（代码、数学、医疗、嵌入）

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**
  - 作者: yuxinlu1 | 点赞: 1,725 | 下载: 211,424
  - 一句话：基于 Gemma-4 的代码专用微调版，并通过 GGUF 量化，是社区开发者进行编码任务的首选。
- **[CohereLabs/North-Mini-Code-1.0](https://huggingface.co/CohereLabs/North-Mini-Code-1.0)**
  - 作者: CohereLabs | 点赞: 450 | 下载: 15,285
  - 一句话：Cohere 推出的代码专用 MoE 小型模型，展示了专用模型的效率优势。

#### 📦 微调与量化（社区微调、GGUF、AWQ）

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**
  - 作者: HauhauCS | 点赞: 1,973 | 下载: 3,420,052
  - 一句话：基于 Qwen3.6 进行激进风格微调的版本，下载量惊人，代表了社区对“解禁”和高个性比模型的需求。
- **[unsloth/gemma-4-12b-it-GGUF](https://huggingface.co/unsloth/gemma-4-12b-it-GGUF)**
  - 作者: unsloth | 点赞: 653 | 下载: 918,431
  - 一句话：Unsloth 为 Gemma-4 官方版提供的量化版本，是本地部署多模态模型的标杆。
- **[OBLITERATUS/Gemma-4-12B-OBLITERATED](https://huggingface.co/OBLITERATUS/Gemma-4-12B-OBLITERATED)**
  - 作者: OBLITERATUS | 点赞: 351 | 下载: 96,805
  - 一句话：社区对 Gemma-4 进行极端风格或功能调整的产物，反映了开源模型的高度可塑性。
- **[DavidAU/Qwen3.6-40B-Claude-4.6-Opus-Deckard-Heretic-Uncensored-Thinking-NEO-CODE-Di-IMatrix-MAX-GGUF](https://huggingface.co/DavidAU/Qwen3.6-40B-Claude-4.6-Opus-Deckard-Heretic-Uncensored-Thinking-NEO-CODE-Di-IMatrix-MAX-GGUF)**
  - 作者: DavidAU | 点赞: 397 | 下载: 529,069
  - 一句话：极具社区特色的“缝合怪”模型，集众多明星模型名称为一身，主打高参数下的“解禁”与强力推理。

### 🔍 生态信号

1.  **家族效应明显**：**Gemma-4** 和 **Qwen3.6** 构成了本周的两大模型“护城河”。Google 和阿里通过开放权重，吸引了社区开发者在其基础上进行大量微调（代码版、解禁版）和量化（GGUF），形成了“官方发布 + 社区繁荣”的正向飞轮。DeepSeek-V4-Pro 作为单一模型，其影响力则更像一个独立的“恒星”。
2.  **多模态是绝对主旋律**：榜单中超过一半的模型与“image-text-to-text”或图像、视频、音频任务相关。这表明，仅仅能“聊天”的模型已很难吸引社区眼球，理解和生成更丰富媒介内容的能力，正成为衡量模型价值的核心标准。
3.  **“量化即服务”**：`unsloth` 几乎为所有热门模型提供了 GGUF 量化版，大大降低了部署门槛。这说明社区对模型的需求正从“在线体验”快速转向“本地部署”。同时，`yuxinlu1` 和 `HauhauCS` 等个人开发者的高质量微调模型，其影响力甚至超过了部分官方版本，标志着社区创新能力的成熟。

### 💡 值得探索

1.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**: 如果你对“视觉定位”和“开放世界目标检测”感兴趣，这个模型是本周的必读项。它以 3B 的小参数实现了高效且效果惊艳的零样本定位能力，是研究如何将视觉能力注入小模型的绝佳案例。
2.  **[zai-org/SCAIL-2](https://huggingface.co/zai-org/SCAIL-2)**: 作为榜单中唯一的“image-to-video”模型，它代表了一个新兴且极具潜力的方向。虽然目前下载量为零（可能刚刚发布），但其“角色动画”的定位非常精准，值得所有关注视频生成和可控生成技术的研究者跟进尝试。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*