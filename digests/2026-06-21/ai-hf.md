# Hugging Face 热门模型日报 2026-06-21

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-21 04:10 UTC

---

好的，这是为您生成的《Hugging Face 热门模型日报》。

---

## 📰 Hugging Face 热门模型日报 (2026-06-21)

### 今日速览

本周 Hugging Face 生态最显著的信号是 **DeepSeek-V4-Pro** 以近5000点赞断层领先，确立了其作为新一代开源基座模型的地位。与此同时，**GLM-5.2**、**Gemma-4** 和 **Qwen3.6** 三大模型家族全面开花，从基座到量化微调版本形成了完整的生态链。**多模态模型（图像-文本-语音）** 成为绝对主流，榜单中超过一半的模型具备视觉理解能力。值得注意的是，**GGUF** 量化社区异常活跃，大量针对最新大模型的量化版本在发布首周即获得数千下载。此外，**NVIDIA** 和 **Microsoft** 的专用模型（如定位、长上下文）也显示出特定场景下的强大吸引力。

---

### 🔥 热门模型分类盘点

#### 🧠 语言模型（LLM、对话模型、指令微调）

*   **DeepSeek-V4-Pro** ([链接](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro))
    *   **作者:** deepseek-ai | **点赞:** 4,987 | **下载:** 2,797,050
    *   **说明:** DeepSeek 最新旗舰对话模型，凭借强大的通用能力和极高的人气，稳居本周热度榜首。
*   **zai-org/GLM-5.2** ([链接](https://huggingface.co/zai-org/GLM-5.2))
    *   **作者:** zai-org | **点赞:** 1,705 | **下载:** 19,683
    *   **说明:** GLM 家族最新 MoE 架构模型，热度极高，吸引了大量社区开发者进行微调与量化。
*   **microsoft/FastContext-1.0-4B-SFT** ([链接](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT))
    *   **作者:** microsoft | **点赞:** 246 | **下载:** 1,998
    *   **说明:** 微软推出的专注于超长上下文处理的轻量级（4B）模型，体现了大模型在特定效率任务上的精进方向。
*   **nex-agi/Nex-N2-Pro** ([链接](https://huggingface.co/nex-agi/Nex-N2-Pro))
    *   **作者:** nex-agi | **点赞:** 340 | **下载:** 7,724
    *   **说明:** 基于 Qwen3.5 MoE 架构优化的商业级对话模型，主打高性能与多模态融合。

#### 🎨 多模态与生成（图像、视频、音频、文本到X）

*   **google/diffusiongemma-26B-A4B-it** ([链接](https://huggingface.co/google/diffusiongemma-26B-A4B-it))
    *   **作者:** google | **点赞:** 1,025 | **下载:** 673,464
    *   **说明:** Google 发布的 Diffusion + Gemma 混合架构模型，兼顾图像理解与生成，下载量极高，代表新范式。
*   **MiniMaxAI/MiniMax-M3** ([链接](https://huggingface.co/MiniMaxAI/MiniMax-M3))
    *   **作者:** MiniMaxAI | **点赞:** 1,164 | **下载:** 85,771
    *   **说明:** MiniMax 新一代多模态大模型，视觉理解与对话能力出色，热度延续。
*   **moonshotai/Kimi-K2.7-Code** ([链接](https://huggingface.co/moonshotai/Kimi-K2.7-Code))
    *   **作者:** moonshotai | **点赞:** 932 | **下载:** 317,963
    *   **说明:** 月之暗面推出的代码视觉多模态模型，专注代码场景，获得了极高的下载量。
*   **ostris/ideogram_4_turbotime_lora** ([链接](https://huggingface.co/ostris/ideogram_4_turbotime_lora))
    *   **作者:** ostris | **点赞:** 83 | **下载:** 1,679
    *   **说明:** 基于 Ideogram 4 的 LoRA 微调模型，展示了顶级文本到图像模型社区微调的热度。
*   **bosonai/higgs-audio-v3-tts-4b** ([链接](https://huggingface.co/bosonai/higgs-audio-v3-tts-4b))
    *   **作者:** bosonai | **点赞:** 499 | **下载:** 72,225
    *   **说明:** 结合 Qwen3 的多模态 TTS 模型，将语音合成能力提升到新高度，代表“文本+语音”融合趋势。
*   **zai-org/SCAIL-2** ([链接](https://huggingface.co/zai-org/SCAIL-2))
    *   **作者:** zai-org | **点赞:** 241 | **下载:** 0
    *   **说明:** 专注于角色动画生成的图像到视频模型，在创意生成领域引起关注。

#### 🔧 专用模型（代码、数学、医疗、嵌入）

*   **nvidia/LocateAnything-3B** ([链接](https://huggingface.co/nvidia/LocateAnything-3B))
    *   **作者:** nvidia | **点赞:** 2,219 | **下载:** 235,606
    *   **说明:** NVIDIA 推出的视觉定位模型（3B），能识别并定位图像任意物体，在机器人、自动驾驶领域潜力巨大。
*   **WeiboAI/VibeThinker-3B** ([链接](https://huggingface.co/WeiboAI/VibeThinker-3B))
    *   **作者:** WeiboAI | **点赞:** 516 | **下载:** 16,270
    *   **说明:** 一个专注数学推理的3B模型，展示了小参数模型在垂直领域推理能力的突破。
*   **LiquidAI/LFM2.5-Embedding-350M** ([链接](https://huggingface.co/LiquidAI/LFM2.5-Embedding-350M))
    *   **作者:** LiquidAI | **点赞:** 81 | **下载:** 6,128
    *   **说明:** 新一代高效文本嵌入模型，表征能力强劲，是 RAG 和搜索场景的理想选择。

#### 📦 微调与量化（社区微调、GGUF、AWQ）

*   **yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF** ([链接](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF))
    *   **作者:** yuxinlu1 | **点赞:** 1,994 | **下载:** 312,332
    *   **说明:** `gemma-4` 代码模型的高人气GGUF量化版，专为本地部署优化，下载量惊人。
*   **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive** ([链接](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive))
    *   **作者:** HauhauCS | **点赞:** 2,046 | **下载:** 3,812,636
    *   **说明:** 社区对 `Qwen3.6` 的“无审查”激进微调版GGUF，极其受欢迎，显示了用户对模型“自由度”的追求。
*   **DavidAU/Qwen3.6-40B-Claude-4.6-Opus-(...)-GGUF** ([链接](https://huggingface.co/DavidAU/Qwen3.6-40B-Claude-4.6-Opus-Deckard-Heretic-Uncensored-Thinking-NEO-CODE-Di-IMatrix-MAX-GGUF))
    *   **作者:** DavidAU | **点赞:** 412 | **下载:** 587,521
    *   **说明:** 一个名字极具风格的社区融合微调模型，融合多模型特性，展示了社区创新的极致。
*   **unsloth/GLM-5.2-GGUF** ([链接](https://huggingface.co/unsloth/GLM-5.2-GGUF))
    *   **作者:** unsloth | **点赞:** 207 | **下载:** 22,586
    *   **说明:** 知名量化团队 Unsloth 对 GLM-5.2 的GGUF版本，为本地部署热门新模型提供便利。

---

### 📈 生态信号

本周生态呈现出明显的“头部大模型带动社区生态”特征。**Qwen3.6** 和 **Gemma-4** 的微调与量化版本（特别是GGUF）占据了榜单半壁江山，表明社区已迅速围绕这些新基座模型构建工具链。**GLM-5.2** 作为国产MoE黑马，其生态也在快速成形。开源权重模型的霸主地位进一步巩固，**DeepSeek-V4-Pro** 和 **MiniMax-M3** 的高赞意味着开发者社区对高性能、可自由获取的模型极度渴求。闭源大模型的影响力正在被开源社区的同人作品和量化版本稀释。值得关注的是，NVIDIA 和 Microsoft 等巨头不再局限于发布巨型模型，而是推出 **LocateAnything** 和 **FastContext** 这类“小而美”的专用模型，这代表了模型从“通用大”向“专业强”的精细化发展方向。

---

### 💡 值得探索

1.  **google/diffusiongemma-26B-A4B-it**: 这是目前少见的将扩散模型与 LLM 深度融合的工作，代表了“理解+生成”一体化的新范式。对于研究多模态底层架构的同行来说，这是必须尝试的模型。
2.  **nvidia/LocateAnything-3B**: 如果你对机器人、自动化或任何需要视觉交互的应用感兴趣，这个模型值得深入研究。它展示了“视觉基座模型”在具体任务（定位）上的巨大潜力，而且体量适中。
3.  **WeiboAI/VibeThinker-3B**: 在算力受限场景下追求强大推理能力的最佳选择之一。这个小模型在数学推理上的表现，证明了通过高质量数据训练，小模型也能在特定领域接近或达到大模型的水平。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*