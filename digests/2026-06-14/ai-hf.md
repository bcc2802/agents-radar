# Hugging Face 热门模型日报 2026-06-14

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-14 04:01 UTC

---

好的，作为AI模型生态分析师，以下是为你准备的《Hugging Face 热门模型日报》。

---

## Hugging Face 热门模型日报 | 2026-06-14

### 📰 今日速览

本周 Hugging Face 生态呈现三大亮点：**DeepSeek-V4-Pro** 凭借卓越的综合能力，以绝对优势登顶周榜，单周点赞近5000，下载量突破320万，成为社区“真香”定律的完美体现。**Gemma 4** 系列生态持续繁荣，Google 官方版本及其海量的社区微调、量化版本（如 Unsloth、OBLITERATUS 系列）在榜单上占据了超过1/3的席位，显示出其在基础模型领域的强大统治力。此外，以 **Nex-N2** 系列为代表的 MoE 架构轻量级模型，以及 **Ideogram 4** 的高质量图像生成模型表现抢眼，标志着高效多模态与专业生成模型的深度融合成为主流趋势。

### 🏆 热门模型分类整理

#### 🧠 语言模型（LLM、对话模型、指令微调）

- **[deepseek-ai/DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)**
  - 作者：deepseek-ai | 点赞：4,813 | 下载：3,250,404
  - 说明：DeepSeek 的最新旗舰版聊天模型，性能强大，在推理、代码和长上下文任务上表现卓越，凭借其极高的“性价比”成为本周社区最受欢迎的模型。
- **[CohereLabs/North-Mini-Code-1.0](https://huggingface.co/CohereLabs/North-Mini-Code-1.0)**
  - 作者：CohereLabs | 点赞：356 | 下载：6,533
  - 说明：Cohere 推出的专注于代码生成的 MoE 语言模型，是“North”系列的小型版本，旨在提供高效的代码辅助能力。
- **[nex-agi/Nex-N2-Pro](https://huggingface.co/nex-agi/Nex-N2-Pro)**
  - 作者：nex-agi | 点赞：238 | 下载：3,092
  - 说明：基于 Qwen3.5 MoE 架构的高性能语言模型，专注于通用对话和文本生成，是社区对“小而美”模型追求的代表。
- **[nex-agi/Nex-N2-mini](https://huggingface.co/nex-agi/Nex-N2-mini)**
  - 作者：nex-agi | 点赞：195 | 下载：3,760
  - 说明：Nex-N2 系列的迷你版，在更小的参数量下保持了优秀的对话能力，适合资源受限的部署场景。
- **[XiaomiMiMo/MiMo-V2.5-Pro-FP4-DFlash](https://huggingface.co/XiaomiMiMo/MiMo-V2.5-Pro-FP4-DFlash)**
  - 作者：XiaomiMiMo | 点赞：106 | 下载：3,590
  - 说明：小米推出的 MiMo 系列模型，采用 FP4 量化技术，主打 Agent 能力，体现了在端侧智能体领域的探索。

#### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **[google/diffusiongemma-26B-A4B-it](https://huggingface.co/google/diffusiongemma-26B-A4B-it)**
  - 作者：google | 点赞：722 | 下载：92,080
  - 说明：Google 发布的“扩散版 Gemma”，26B-A4B 意味着它是一个 MoE 架构的图像-文本到文本模型，支持多轮图像对话等复杂任务。
- **[google/gemma-4-12B-it](https://huggingface.co/google/gemma-4-12B-it)**
  - 作者：google | 点赞：995 | 下载：1,005,883
  - 说明：Gemma 4 系列的核心指令微调模型，具有 Any-to-Any 能力（处理任意输入，生成任意输出），是理解与生成的多模态全能选手。
- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**
  - 作者：nvidia | 点赞：1,967 | 下载：69,443
  - 说明：NVIDIA 推出的目标定位模型，能够根据文本指令在图像中定位任何物体，被广泛应用于视觉内容分析，是本周最高赞的专用模型。
- **[ideogram-ai/ideogram-4-fp8](https://huggingface.co/ideogram-ai/ideogram-4-fp8)**
  - 作者：ideogram-ai | 点赞：518 | 下载：6,535
  - 说明：Ideogram 4 的 FP8 量化版本，在保持高质量图像生成能力的同时，大幅降低了推理成本，成为文生图领域的焦点。
- **[ByteDance/Bernini-R](https://huggingface.co/ByteDance/Bernini-R)**
  - 作者：ByteDance | 点赞：235 | 下载：426
  - 说明：字节跳动发布的“图像-文本到视频”模型，可以根据图片和文本生成视频，展示了视频生成模型的前沿进展。
- **[bosonai/higgs-audio-v3-tts-4b](https://huggingface.co/bosonai/higgs-audio-v3-tts-4b)**
  - 作者：bosonai | 点赞：414 | 下载：32,162
  - 说明：一款高性能的文本转语音（TTS）模型，4B 参数规模，专注于生成自然、逼真的语音。
- **[zai-org/SCAIL-2](https://huggingface.co/zai-org/SCAIL-2)**
  - 作者：zai-org | 点赞：155 | 下载：0
  - 说明：基于姿态驱动的角色动画生成模型，可以将图像转换为动画视频，是 AI 视频生成在特定领域深度应用的案例。

#### 🔧 专用模型（代码、数学、医疗、嵌入）

- **[moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code)**
  - 作者：moonshotai | 点赞：524 | 下载：1,689
  - 说明：月之暗面推出的专为代码任务优化的视觉语言模型，结合了图像特征提取与代码理解，是数字助理的升级版。
- **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)**
  - 作者：nvidia | 点赞：403 | 下载：3,975
  - 说明：NVIDIA 开发的流式自动语音识别（ASR）模型，支持缓存感知的实时转录，对低延迟场景（如直播、会议）至关重要。
- **[google/magenta-realtime-2](https://huggingface.co/google/magenta-realtime-2)**
  - 作者：google | 点赞：189 | 下载：7,331
  - 说明：Google Magenta 项目的最新实时音频生成模型（TFLite格式），专注于文本到音频/音乐的生成，展现了 AI 在艺术创作领域的实时性突破。

#### 📦 微调与量化（社区微调、GGUF、AWQ）

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**
  - 作者：HauhauCS | 点赞：1,763 | 下载：2,411,202
  - 说明：社区基于 Qwen3.6 的激进风格、无审查微调版本，MoE 架构兼顾性能与效率，下载量极高，反映了社区对“有个性”模型的强烈需求。
- **[OBLITERATUS/Gemma-4-12B-OBLITERATED](https://huggingface.co/OBLITERATUS/Gemma-4-12B-OBLITERATED)**
  - 作者：OBLITERATUS | 点赞：279 | 下载：50,289
  - 说明：社区对 Gemma-4 进行“不可描述”风格微调的版本，热度高，是社区对模型进行特定风格定制的典型案例。
- **[Jiunsong/supergemma4-26b-uncensored-gguf-v2](https://huggingface.co/Jiunsong/supergemma4-26b-uncensored-gguf-v2)**
  - 作者：Jiunsong | 点赞：820 | 下载：98,892
  - 说明：社区对 Gemma-4-26B 的无审查微调 + GGUF 量化版本，专注于“快速”和“本地运行”，是量化社区的集大成者。
- **[unsloth/diffusiongemma-26B-A4B-it-GGUF](https://huggingface.co/unsloth/diffusiongemma-26B-A4B-it-GGUF)**、**[unsloth/gemma-4-12b-it-GGUF](https://huggingface.co/unsloth/gemma-4-12b-it-GGUF)**、**[unsloth/gemma-4-12B-it-qat-GGUF](https://huggingface.co/unsloth/gemma-4-12B-it-qat-GGUF)**、**[unsloth/gemma-4-26B-A4B-it-qat-GGUF](https://huggingface.co/unsloth/gemma-4-26B-A4B-it-qat-GGUF)**
  - 作者：unsloth | 点赞：列表内 | 下载：列表内
  - 说明：Unsloth 团队贡献了 Gemma 4 全系列（包括Diffusion版）的 GGUF / QAT GGUF 量化版本，极大降低了模型部署门槛，推动了本地化推理的普及。

### 📈 生态信号

- **Gemma 4 生态一枝独秀**：Google 的 Gemma 4 系列已成为开源世界的“安卓”，其官方版本、社区微调版（无审查、风格化）、量化版（GGUF、QAT）几乎覆盖了榜单的半壁江山。这表明一个强大、开放的基础模型能催生出极其繁荣和多样化的第三方生态系统。
- **MoE 与混合专家架构成主流**：无论是 DeepSeek-V4-Pro 还是 Nex-N2、Gemma 4 系列，MoE 架构已成为高效率模型的标配。社区普遍认可“用更少的激活参数获得更大的模型容量”这一理念。
- **量化技术（GGUF）与社区定制（Uncensored）双轮驱动**：Unsloth 等团队提供了便捷的量化工具，而“无审查”和“特定风格”微调则满足了用户的个性化需求。两者结合（如 `supergemma4-26b-uncensored-gguf-v2`），推动了模型的本地化、私有化部署浪潮。

### 🔍 值得探索

1.  **[deepseek-ai/DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)**：作为本周“顶流”模型，其卓越的综合能力和极高的社区认可度使它成为任何AI从业者都应体验的基准模型，代表了当前开源LLM的顶尖水平。
2.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**：该模型在“图像-文本到文本”任务中精准定位的能力，使其在智能安防、自动驾驶、医疗影像分析等垂直领域具有极高的应用潜力，值得深入研究其架构和代码。
3.  **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**：尽管模型名称看起来有些“狂野”，但背后体现了社区在模型个性化、风格控制上的深度探索。如果你想了解社区生态的活力和多样性，这是一个非常典型的案例，且其下载量也证明了市场需求所在。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*