# Hugging Face 热门模型日报 2026-07-02

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-02 08:14 UTC

---

好的，作为 AI 模型生态分析师，以下是根据您提供的 2026-07-02 数据整理的《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026-07-02**

#### **1. 今日速览**

本周 Hugging Face 生态呈现 **“巨头博弈、百花齐放”** 的态势。**百度** 发布的通用 OCR 模型 `Unlimited-OCR` 以绝对下载量优势登顶，展示了多模态基础模型的落地潜力。**GLM-5.2** 家族（包括 `zai-org` 和 `nvidia` 版本）集体爆发，印证了 MoE（混合专家）路线在开源社区的强势地位。同时，**Qwen 3.5/3.6** 系列衍生出大量针对 **Agent**（如 `Qwen-AgentWorld`）和 **Coding**（如 `Qwopus3.6-Coder`）的专用微调版与量化版，社区微调与二次创作空前活跃。此外，**NVIDIA** 凭借 `LocateAnything-3B` 在视觉定位任务上展现了强大的基础模型能力，而 **DeepSeek V4** 系列也开始进入测试阶段。

#### **2. 热门模型分类整理**

##### 🧠 **语言模型（LLM、对话模型、指令微调）**

-   **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** | 点赞: 3,193 | 下载: 159,967
    -   **说明**: 智谱 AI 发布的 MoE 架构旗舰模型。本周点赞数最高，社区对其强大生成与对话能力给予了极高期待。
-   **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** | 点赞: 284 | 下载: 7,629
    -   **说明**: DeepSeek 最新版的旗舰模型（带“DSpark”加速），作为国产开源顶级模型的最新迭代，是技术圈关注焦点。
-   **[deepreinforce-ai/Ornith-1.0-35B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B)** & **[9B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-9B)** | 点赞: 296 (35B)
    -   **说明**: 基于 Qwen 3.5 微调的大模型家族，从其庞大的 GGUF 版本下载量可知，社区广泛将其用于本地化部署和私有化场景。
-   **[Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)** | 点赞: 499 | 下载: 34,371
    -   **说明**: 通义千问团队发布的**世界模型** Agent，开启了 LLM 从“对话”到“行动与模拟”的新范式，代表了 Agent 领域的重大进展。

##### 🎨 **多模态与生成（图像、视频、音频、文本到X）**

-   **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** | 点赞: 1,601 | 下载: 630,246
    -   **说明**: 百度发布的全能 OCR 模型（Image-Text-to-Text），以其极高的下载量成为本周“应用之王”，证明了通用文字识别仍是刚需。
-   **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** | 点赞: 2,555 | 下载: 896,058
    -   **说明**: NVIDIA 发布的高效视觉定位模型，在图像中定位和理解万物。在点赞和下载量上均表现亮眼，是视觉基础模型的重要进展。
-   **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** | 点赞: 441 | 下载: 56,953
    -   **说明**: 新一代文生图模型，主打高速生成（Turbo），在上游模型 `Krea-2-Raw` 基础上大幅提升了推理速度。
-   **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)** | 点赞: 138 | 下载: 0
    -   **说明**: 一个用于视频生成的 LoRA 模块，专注于将通用视频模型转化为高质量 3D 风格，体现了生成式 AI 向特定风格发展的趋势。

##### 🔧 **专用模型（代码、数学、安全、嵌入）**

-   **[BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6)** | 点赞: 113 | 下载: 3,377
    -   **说明**: 专注于网络安全（Offensive Security）的专用模型，结合了 Qwen 3 底座的强大能力，预示了垂直领域模型的商业化潜力。
-   **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** | 点赞: 2,556 | 下载: 597,090
    -   **说明**: 基于 Google Gemma-4 微调的高性能代码模型，社区量化版本下载量巨大，成为本周“程序员最爱”。
-   **[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LiquidAI/LFM2.5-230M)** | 点赞: 183 | 下载: 21,935
    -   **说明**: 小型高效的文本生成模型，适合在边缘设备或资源受限环境下运行，代表了“小模型”路线的持续演进。

##### 📦 **微调与量化（社区微调、GGUF、AWQ、NVFP4）**

-   **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** | 点赞: 2,384 | 下载: 3,055,962
    -   **说明**: **本周下载榜冠军**。基于 Qwen 3.6 的“无审查 + 激进风格”微调版，反映了社区对模型风格控制和安全边界的直接需求。
-   **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** | 点赞: 1,185 | 下载: 1,113,871
    -   **说明**: 模仿 Claude 风格的精调模型，提供量化版本。下载量超百万，证明市场对“优秀对话体验”的量化刚需。
-   **[unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)** | 点赞: 490 | 下载: 212,201
    -   **说明**: Unsloth 团队将 GLM-5.2 快速处理成 GGUF 格式，极大降低了社区使用门槛，是连接前沿技术与本地部署的关键一环。
-   **[nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)** | 点赞: 200 | 下载: 136,933
    -   **说明**: NVIDIA 与智谱合作，利用 `Model Optimizer` 将 GLM-5.2 压缩为 NVFP4 精度，代表了从模型到硬件的联合优化趋势。

#### **3. 生态信号**

1.  **MoE 与 Qwen 双雄争霸**: **GLM-5.2** 与 **Qwen 3.5/3.6** 家族是本周绝对的主角。MoE 架构因其卓越的性价比（用更少参数激活，获得更大模型能力）成为社区新宠。Qwen 系列则凭借丰富的生态和微调潜力，正在形成类似 Linux 内核一样的“模型集市”。
2.  **量化与本地化是主流**: 榜单上超过一半的模型提供 **GGUF** 版本，且下载量远超原始权重。这表明开源社区第一需求已从“能不能跑”变为“如何在本地跑得快、吃内存少”。**HauhauCS** 的 uncensored 模型下载量突破 300 万次，是这一趋势的极致体现。
3.  **Agent 与工具使用成为新竞赛**: **Qwen-AgentWorld** 的入榜，预示着下一代模型的竞争不仅仅是问答，而是 **“理解世界、执行任务”** 的能力。Agent 模型将推动模型与应用场景的深度结合。
4.  **闭源优势正在被社区微调稀释**: 本周多个模型（如 Qwythos）明确标注“模仿 Claude / Mythos”，并获得了极高关注和下载量。这表明，当高质量的通用基础模型（如 Qwen 3.5）开源后，社区通过微调可以“复现”甚至“超越”某些闭源模型的体验，开源的力量正在重塑生态价值分配。

#### **4. 值得探索**

-   **1. [Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)**: **强烈推荐**。这不仅是模型，更是一种新范式。研究它的 Agent 能力、工具调用和世界模拟机制，对于理解 AI 的下一个发展方向至关重要。
-   **2. [nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**: 如果你对多模态和计算机视觉感兴趣，这个模型值得一试。它证明了 3B 大小模型在复杂视觉定位任务上的潜力，代表了从“看图说话”到“精准定位”的进化。
-   **3. [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**: 作为本周点赞王，它代表了国内大模型技术力的最高水平。如果你是 LLM 性能评估或 MoE 架构研究者，这是必读（必试）的模型。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*