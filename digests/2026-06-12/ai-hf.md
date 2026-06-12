# Hugging Face 热门模型日报 2026-06-12

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-12 01:24 UTC

---

好的，作为AI模型生态分析师，以下是基于您提供的2026-06-12数据生成的《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026-06-12**

#### **今日速览**

本周Hugging Face社区热度继续由DeepSeek和Google主导。DeepSeek-V4-Pro以压倒性的人气和下载量登顶，巩固了其在开源大模型领域的霸主地位。Google的Gemma-4系列生态持续爆发，不仅官方发布了多模态Any-to-Any模型，社区也涌现了大量量化（GGUF）和解禁（Abliterated）的衍生版本。值得关注的是，NVIDIA凭借LocateAnything-3B等新模型在视觉定位领域崭露头角，同时多模态和TTS领域的创新模型（如Higgs Audio、MisoTTS）也吸引了大量关注，表明AI生态正从纯文本向更丰富的多模态交互全面演进。

---

#### **热门模型分类解读**

##### 🧠 **语言模型（LLM、对话模型、指令微调）**

*   **DeepSeek-V4-Pro**
    *   **作者:** deepseek-ai | **点赞:** 4,781 | **下载:** 4,061,006
    *   **说明:** DeepSeek最新旗舰级MoE模型，凭借强大的推理能力和极高的开放性，本周稳坐热度与下载量双料冠军，是开源社区最受瞩目的“屠榜”模型。

*   **NVIDIA-Nemotron-3-Ultra-550B-A55B-BF16**
    *   **作者:** nvidia | **点赞:** 198 | **下载:** 59,066
    *   **说明:** NVIDIA发布的大规模MoE模型（550B参数，55B活跃），代表了其在通用文本生成领域的顶级实力，为超大规模推理场景提供了强大选择。

*   **NVIDIA-Nemotron-3-Ultra-550B-A55B-NVFP4**
    *   **作者:** nvidia | **点赞:** 168 | **下载:** 91,117
    *   **说明:** 同上模型的高效NVFP4量化版本，通过极致压缩，在不显著损失性能的前提下大幅降低显存占用和推理成本，适合企业级部署。

*   **LiquidAI/LFM2.5-8B-A1B**
    *   **作者:** LiquidAI | **点赞:** 594 | **下载:** 142,134
    *   **说明:** 一款极具效率的MoE模型（8B总参，1B活跃），证明了“小而美”的路线的可行性，为资源受限的场景提供了高性能的LLM选择。

*   **sapientinc/HRM-Text-1B**
    *   **作者:** sapientinc | **点赞:** 749 | **下载:** 134,752
    *   **说明:** 一个专为人力资源管理场景设计的1B参数文本生成模型，关注度极高，预示着垂直领域专业化模型的巨大潜力。

##### 🎨 **多模态与生成（图像、视频、音频、文本到X）**

*   **nvidia/LocateAnything-3B**
    *   **作者:** nvidia | **点赞:** 1,872 | **下载:** 131,794
    *   **说明:** NVIDIA推出的3B参数视觉定位模型，能够根据文本指令在图像中精确找到任何物体，是本周最亮眼的多模态新星。

*   **google/gemma-4-12B-it** & **google/gemma-4-12B**
    *   **作者:** google | **点赞:** 940 & 516 | **下载:** 675,936 & 140,221
    *   **说明:** Google Gemma-4系列的旗舰指令模型与基座模型，支持“Any-to-Any”多模态任务（文本、图像输入输出），是推动多模态AI普及的关键力量。

*   **google/diffusiongemma-26B-A4B-it**
    *   **作者:** google | **点赞:** 491 | **下载:** 0 （新模型）
    *   **说明:** Google发布的26B参数扩散模型（4B活跃），专注于图像到文本任务，代表了“扩散”与“自回归”模型融合的前沿方向，虽刚上线但热度极高。

*   **ideogram-ai/ideogram-4-fp8** & **ideogram-4-nf4**
    *   **作者:** ideogram-ai | **点赞:** 485 & 315 | **下载:** 7,170 & 6,124
    *   **说明:** Ideogram第四代文生图模型的不同量化版本，以其高质量的图像生成和精准的文字渲染能力闻名，持续受到设计师和创作者社区的追捧。

*   **ByteDance/Bernini-R**
    *   **作者:** ByteDance | **点赞:** 222 | **下载:** 305
    *   **说明:** 字节跳动推出的图像+文本到视频的渲染模型，专注于生成高质量的角色动画，为AIGC视频领域带来了新的可能性。

*   **stepfun-ai/Step-3.7-Flash**
    *   **作者:** stepfun-ai | **点赞:** 368 | **下载:** 50,187
    *   **说明:** 阶跃星辰发布的快速视觉语言模型，在性能和速度间取得了良好平衡，适合需要实时响应的多模态应用。

*   **google/magenta-realtime-2**
    *   **作者:** google | **点赞:** 178 | **下载:** 19,806
    *   **说明:** Google Magenta项目的最新成果，专为实时文本到音频生成设计，标志着AI音乐和音频内容创作进入新阶段。

*   **zai-org/SCAIL-2**
    *   **作者:** zai-org | **点赞:** 116 | **下载:** 0 （新模型）
    *   **说明:** 专注于姿态驱动的角色动画生成模型，能够根据图像和姿势序列生成流畅的视频，是轻量级AI动画工具的代表。

##### 🔧 **专用模型（代码、TTS、语音识别）**

*   **CohereLabs/North-Mini-Code-1.0**
    *   **作者:** CohereLabs | **点赞:** 308 | **下载:** 1,859
    *   **说明:** Cohere推出的专注于代码生成的MoE模型，旨在提升开发效率和代码质量，是开发者社区关注的热点。

*   **bosonai/higgs-audio-v3-tts-4b**
    *   **作者:** bosonai | **点赞:** 355 | **下载:** 19,948
    *   **说明:** 一款4B参数的高质量TTS模型，展示了多模态Qwen架构在语音合成领域的强大能力，有望成为下一代语音克隆和有声书制作工具。

*   **nvidia/nemotron-3.5-asr-streaming-0.6b**
    *   **作者:** nvidia | **点赞:** 372 | **下载:** 4,965
    *   **说明:** NVIDIA推出的0.6B参数流式语音识别模型，专为低延迟、高准确率的实时语音交互场景设计，助力AI语音助手发展。

*   **MisoLabs/MisoTTS**
    *   **作者:** MisoLabs | **点赞:** 194 | **下载:** 0 （新模型）
    *   **说明:** 一款全新的TTS模型，虽然刚发布无下载量，但高点赞数表明社区对高质量、新型语音合成技术的渴求。

##### 📦 **微调与量化（社区微调、GGUF、AWQ）**

*   **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive**
    *   **作者:** HauhauCS | **点赞:** 1,676 | **下载:** 3,057,541
    *   **说明:** 基于Qwen3.6的35B参数MoE模型的“无审查”版本，以其极强的“越狱”能力和极高的GGUF量化下载量位列社区改版模型人气榜首。

*   **unsloth/gemma-4-12b-it-GGUF** & **gemma-4-12B-it-qat-GGUF** 等
    *   **作者:** unsloth | **点赞:** 561+ | **下载:** 711,706+
    *   **说明:** 知名量化团队Unsloth持续为Gemma-4系列提供便捷、高效的GGUF版本，极大地推动了Google模型在消费级硬件（如个人电脑和Mac）上的本地部署。

*   **OBLITERATUS/Gemma-4-12B-OBLITERATED**
    *   **作者:** OBLITERATUS | **点赞:** 234 | **下载:** 14,838
    *   **说明:** 社区对Gemma-4-12B进行“解禁”处理后的版本，类似HauhauCS的“Uncensored”路线，反映了用户对模型能力边界探索的强烈需求。

*   **huihui-ai/Huihui-gemma-4-12B-it-abliterated**
    *   **作者:** huihui-ai | **点赞:** 143 | **下载:** 6,400
    *   **说明:** 另一个对Gemma-4进行“去审查”的社区版本（Abliterated），验证了该模型家族在安全性与创造力之间存在着可供社区探索的巨大空间。

---

#### **生态信号分析**

*   **模型家族势头：** **DeepSeek V4**和**Google Gemma-4**两大系列构成了本周的绝对核心。DeepSeek凭借其超强性能和极高的开放度持续引领；而Gemma-4则通过从官方到社区的密集生态协作，衍生出量化、解禁、多模态等多种版本，展现出惊人的社区活力和护城河潜力。NVIDIA的**Nemotron-3**和**LocateAnything**也在强力冲击，形成了“DeepSeek / Google / NVIDIA”三足鼎立的初步格局。

*   **开源权重 vs 闭源：** 本周趋势榜所有模型均为开源权重发布，再次证明了社区对于可自托管、可微调、可审计的开源模型的绝对偏好。Meta等公司的闭源模型/API对社区的影响力正在被这些重量级开源玩家显著稀释。

*   **值得注意的活动：** **量化（GGUF）**和**微调（Uncensored/Abliterated）**是本周最强的社区活动。Unsloth团队与Google的紧密合作，使得大模型在个人设备上运行成为现实。同时，以“Uncensored”和“Abliterated”为代表的社区安全机制探索，表明用户不仅想拥有模型，还想完全掌控和定义模型的行为边界，这是一个重要的文化信号。

---

#### **值得探索**

1.  **nvidia/LocateAnything-3B**（[https://huggingface.co/nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)）
    *   **理由：** 视觉定位是通往具身智能的关键技术之一。这个3B模型将图像理解与空间推理完美结合，是探索“万物图搜”和自动化视觉导航应用的绝佳起点。

2.  **google/diffusiongemma-26B-A4B-it**（[https://huggingface.co/google/diffusiongemma-26B-A4B-it](https://huggingface.co/google/diffusiongemma-26B-A4B-it)）
    *   **理由：** 这是一个具有里程碑意义的模型，它将“扩散模型”与“语言模型”结合。研究其在图像理解和生成上的独特能力，可以一窥未来多模态模型架构的演进方向。

3.  **unsloth/gemma-4-12b-it-GGUF**（[https://huggingface.co/unsloth/gemma-4-12b-it-GGUF](https://huggingface.co/unsloth/gemma-4-12b-it-GGUF)）
    *   **理由：** 对于任何希望在本机运行顶级多模态AI的开发者或爱好者而言，这是性价比最高的选择。无需昂贵GPU即可体验Any-to-Any能力，直接上手，感受未来。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*