# Hugging Face 热门模型日报 2026-06-20

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-20 03:37 UTC

---

好的，作为 AI 模型生态分析师，为您呈现 2026 年 6 月 20 日的《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026-06-20**

#### **今日速览**

本周 Hugging Face 生态呈现出明显的“巨模型对抗与社区微调并行”格局。**DeepSeek-V4 Pro** 以近 5000 点赞登顶，证明社区对新一代顶级开源基座的渴望。**多模态**成为绝对主流，榜单中近半数模型为 `image-text-to-text` 任务，Google 的 `DiffusionGemma` 和 `Gemma-4-12B` 系模型生态繁荣。同时，**GGUF 量化模型**下载量惊人，尤其是社区对 `Qwen3.6` 系列的各种魔改和量化版本，显示出中小企业和个人开发者对本地化部署的旺盛需求。此外，**代码与推理**专用模型持续获得高关注度。

#### **热门模型**

##### 🧠 语言模型（LLM、对话模型、指令微调）

*   **[deepseek-ai/DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)**
    *   作者: deepseek-ai | 👍 4,969 | ⬇️ 3,015,772
    *   **一句话说明**: DeepSeek 的最新旗舰级对话模型，凭借顶尖的性能和开源策略，成为本周无可争议的焦点。
*   **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**
    *   作者: yuxinlu1 | 👍 1,858 | ⬇️ 268,102
    *   **一句话说明**: 基于 Google Gemma-4 的代码微调版，融合了多种训练技巧，是本周最热门的编程专用模型之一。
*   **[WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)**
    *   作者: WeiboAI | 👍 464 | ⬇️ 12,148
    *   **一句话说明**: 一个专注于数学推理的 3B 小模型，在保持较小规模的同时展现了不错的推理能力，适合在资源受限场景部署。

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

*   **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**
    *   作者: nvidia | 👍 2,195 | ⬇️ 228,669
    *   **一句话说明**: 英伟达推出的目标定位基础模型，能够通过文本或图像提示精准定位场景中的任何物体，在视觉应用领域潜力巨大。
*   **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**
    *   作者: HauhauCS | 👍 2,010 | ⬇️ 3,730,978
    *   **一句话说明**: 基于 Qwen3.6 的 MoE 模型，经过“脱敏”和“激进”风格微调，虽然内容争议性强，但下载量惊人，反映了社区对个性化模型的需求。
*   **[google/diffusiongemma-26B-A4B-it](https://huggingface.co/google/diffusiongemma-26B-A4B-it)**
    *   作者: google | 👍 1,011 | ⬇️ 601,208
    *   **一句话说明**: Google 的扩散语言模型，仅 4B 激活参数即可处理图像与文本，是探索新一代多模态架构的里程碑。
*   **[google/gemma-4-12B-it](https://huggingface.co/google/gemma-4-12B-it)**
    *   作者: google | 👍 1,096 | ⬇️ 1,590,882
    *   **一句话说明**: Google Gemma-4 系列的官方指令微调版，支持 `any-to-any` 多模态任务，下载量证明了其作为开源基座的受欢迎程度。
*   **[bosonai/higgs-audio-v3-tts-4b](https://huggingface.co/bosonai/higgs-audio-v3-tts-4b)**
    *   作者: bosonai | 👍 493 | ⬇️ 69,143
    *   **一句话说明**: 一个 4B 参数的高质量文本转语音模型，标志着 AI 语音合成领域也进入了“大模型”时代。

##### 🔧 专用模型（代码、数学、医疗、嵌入）

*   **[moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code)**
    *   作者: moonshotai | 👍 910 | ⬇️ 274,865
    *   **一句话说明**: 月之暗面推出的代码专用模型，具备图像特征提取能力，能处理代码截图等视觉输入，是新一代的“可看代码”的大模型。
*   **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)**
    *   作者: nvidia | 👍 564 | ⬇️ 18,809
    *   **一句话说明**: 英伟达的流式语音识别模型，仅 0.6B 参数，主打低延迟和缓存感知，非常适合实时语音交互场景。

##### 📦 微调与量化（社区微调、GGUF、AWQ）

*   **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**
    *   作者: zai-org | 👍 1,547 | ⬇️ 11,871
    *   **一句话说明**: 智谱 GLM 系列的最新版本，采用了 MoE-DSA 稀疏架构，是在国内开源社区引发广泛关注的重量级模型。
*   **[Jackrong/Qwopus3.6-27B-Coder-MTP-GGUF](https://huggingface.co/Jackrong/Qwopus3.6-27B-Coder-MTP-GGUF)**
    *   作者: Jackrong | 👍 261 | ⬇️ 148,525
    *   **一句话说明**: 基于 Qwen3.6 的代码量化版，高下载量证明了社区对“可本地运行”的高性能代码模型的强烈需求。
*   **[DavidAU/Qwen3.6-40B-Claude-4.6-Opus-Deckard-Heretic-Uncensored-Thinking-NEO-CODE-Di-IMatrix-MAX-GGUF](https://huggingface.co/DavidAU/Qwen3.6-40B-Claude-4.6-Opus-Deckard-Heretic-Uncensored-Thinking-NEO-CODE-Di-IMatrix-MAX-GGUF)**
    *   作者: DavidAU | 👍 406 | ⬇️ 588,753
    *   **一句话说明**: 名字超长的社区实验性微调模型，融合了多种风格，虽然名称怪异，但巨大的下载量体现了社区对“缝合怪”模型和极端风格模型的好奇与探索。

#### **生态信号**

本周生态信号明确：**“Qwen 宇宙”正在形成**。围绕 `Qwen3_5` 和 `Qwen3.6` 的社区魔改、量化（GGUF）和专用化微调模型占据了榜单近半数席位，显示出 Alibaba Qwen 系列已成为当前最活跃的开源基座之一。**MoE (混合专家) 架构**全面开花，从 Google 的 `DiffusionGemma` 到智谱的 `GLM-5.2` 再到多家厂商的 `Qwen3_5_moe`，高效的大模型架构已成为主流。**开源 vs 闭源**方面，开源权重模型（如 DeepSeek-V4）依然统治榜单，但社区微调与量化活动的活跃度已超越官方发布，形成“官方造车，社区改装”的繁荣生态。

#### **值得探索**

1.  **[deepseek-ai/DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)**: 毫无疑问的榜首，应作为评估当前开源 LLM 性能天花板的基准模型，也是很多下游应用的基石。
2.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**: 代表了计算机视觉领域从“分类/检测”到“任意目标定位”的范式转变。其 3B 的小巧体积和强大能力，使其非常适合嵌入到复杂的 AI Agent 和机器人系统中。
3.  **[google/diffusiongemma-26B-A4B-it](https://huggingface.co/google/diffusiongemma-26B-A4B-it)**: 如果你想了解 AI 的下一个前沿，这个模型不容错过。它打破了传统自回归模型的限制，展示了“扩散”在语言多模态领域的潜力，值得深入研究其推理和生成机制。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*