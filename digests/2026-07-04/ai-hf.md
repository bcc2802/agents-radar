# Hugging Face 热门模型日报 2026-07-04

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-04 07:50 UTC

---

好的，作为AI模型生态分析师，这是为您整理的2026年7月4日Hugging Face热门模型日报。

---

# 🤗 Hugging Face 热门模型日报 2026-07-04

## 今日速览

本周Hugging Face社区呈现三大显著趋势：**大厂通用模型继续统治头部**，智谱的**GLM-5.2**与英伟达的**LocateAnything-3B**分别登顶文本生成与多模态任务的热度榜首，展示了在通用能力与专业视觉定位上的双重突破。**社区微调与量化生态极度活跃**，基于Qwen3.5/3.6和Gemma-4的各类GGUF量化版、无审查版（Uncensored）和Agent专用版模型大量涌现，下载量极高，例如`HauhauCS/Qwen3.6-35B-A3B-Uncensored-Aggressive`周下载量突破300万。此外，**多模态模型（特别是图像理解与OCR）持续升温**，百度`Unlimited-OCR`和英伟达`LocateAnything-3B`均展现了强大的应用潜力。

## 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

1.  **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** - 作者: zai-org | 点赞: 3,354 | 下载: 191,462
    - 💡 **一句话说明**: 由智谱AI（Zhipu AI）发布的全新MoE大模型，凭借原生多模态理解能力和强大的中文对话性能，成为当周热度最高的文本生成模型之一。
2.  **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** - 作者: deepreinforce-ai | 点赞: 692 | 下载: 322,780
    - 💡 **一句话说明**: Ornith系列35B模型的高效量化版，以其接近70B级别的推理能力但更小的体积广受本地部署用户欢迎。
3.  **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** - 作者: deepseek-ai | 点赞: 351 | 下载: 9,388
    - 💡 **一句话说明**: DeepSeek第四代模型的专业版，配合DSpark微调框架，在复杂推理和需要深度思考的任务上性能突出。
4.  **[deepreinforce-ai/Ornith-1.0-9B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-9B)** - 作者: deepreinforce-ai | 点赞: 368 | 下载: 64,051
    - 💡 **一句话说明**: Ornith系列的小尺寸版本（9B），在效率和性能间取得了平衡，是基于Qwen3.5架构的优质社区微调模型。
5.  **[deepreinforce-ai/Ornith-1.0-35B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B)** - 作者: deepreinforce-ai | 点赞: 324 | 下载: 211,406
    - 💡 **一句话说明**: Ornith系列35B的原始全精度版，作为Ornith家族的核心模型，是社区进行各种微调和量化的基础。
6.  **[deepreinforce-ai/Ornith-1.0-9B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-9B-GGUF)** - 作者: deepreinforce-ai | 点赞: 416 | 下载: 287,942
    - 💡 **一句话说明**: 9B Ornith模型的GGUF量化版，因其极低的硬件门槛和MIT开源协议，成为社区中最受欢迎的轻量级本地模型之一。
7.  **[deepreinforce-ai/Ornith-1.0-397B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-397B)** - 作者: deepreinforce-ai | 点赞: 201 | 下载: 8,079
    - 💡 **一句话说明**: Ornith系列的旗舰级MoE模型，总参数量达397B，代表社区微调在超大模型尺度的探索。
8.  **[nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)** - 作者: nvidia | 点赞: 216 | 下载: 189,970
    - 💡 **一句话说明**: 英伟达基于GLM-5.2优化的NVFP4精度版本，利用NVIDIA ModelOpt技术，在保证精度的同时极大提升了云端推理效率。
9.  **[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LiquidAI/LFM2.5-230M)** - 作者: LiquidAI | 点赞: 200 | 下载: 29,645
    - 💡 **一句话说明**: 液态网络架构的最新探索，230M参数的小模型在特定任务上展现出超越其参数规模的潜力，是前沿LLM架构研究的风向标。

### 🎨 多模态与生成（图像、视频、音频、文本到X）

1.  **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** - 作者: empero-ai | 点赞: 1,395 | 下载: 1,366,360
    - 💡 **一句话说明**: 集成了强大视觉理解能力（image-text-to-text）的9B级模型，被广泛认为是本地多模态应用的标杆，其GGUF版本下载量已超百万。
2.  **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** - 作者: baidu | 点赞: 1,697 | 下载: 885,040
    - 💡 **一句话说明**: 百度的通用OCR模型，能够处理几乎所有场景的文字识别，在文档数字化、图像信息提取领域表现出色，是实用型多模态的典范。
3.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** - 作者: nvidia | 点赞: 2,592 | 下载: 1,108,586
    - 💡 **一句话说明**: 英伟达发布的视觉定位基础模型，用户只需输入自然语言描述，即可在图像中精准定位任何物体，交互性强，下载量与热度双高。
4.  **[Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)** - 作者: Qwen | 点赞: 528 | 下载: 45,455
    - 💡 **一句话说明**: 通义千问出品，专为Agent场景优化的视觉模型，激活参数仅3B（总参35B），在理解图像内容并执行任务方面具有优异性能。
5.  **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** - 作者: krea | 点赞: 485 | 下载: 84,006
    - 💡 **一句话说明**: 新一代文本到图像生成模型Krea-2的Turbo加速版，在保持高质量输出的同时显著提升了生成速度，受到创意工作者的青睐。
6.  **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** - 作者: InternScience | 点赞: 215 | 下载: 3,530
    - 💡 **一句话说明**: 首个专注于Agent任务的基于Qwen3.5 MoE的多模态模型，代表着模型主动感知世界并与环境交互的趋势。
7.  **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** - 作者: yuxinlu1 | 点赞: 996 | 下载: 329,391
    - 💡 **一句话说明**: 基于Gemma-4的专为Agent与终端操作设计的微调模型，GGUF量化后非常适合作为本地“模型即终端”的核心引擎。
8.  **[Jackrong/Qwopus3.6-35B-A3B-Coder-MTP-GGUF](https://huggingface.co/Jackrong/Qwopus3.6-35B-A3B-Coder-MTP-GGUF)** - 作者: Jackrong | 点赞: 126 | 下载: 44,807
    - 💡 **一句话说明**: 结合了Qwen3.6的MoE架构与MTP（Multi-Turn Processing），专为编程与视觉问答设计，GGUF版本便于本地部署。
9.  **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** - 作者: HauhauCS | 点赞: 2,442 | 下载: 3,029,679
    - 💡 **一句话说明**: 社区最激进的无审查版模型之一，基于Qwen3.6，下载量一周内突破300万，反映了用户对高度开放与强风格化模型的需求。
10. **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)** - 作者: fal | 点赞: 152 | 下载: 0
    - 💡 **一句话说明**: 图像转视频领域的创新LoRA，能生成高度逼真且具有立体感的3D风格视频，预示了视频生成从“动起来”向“更真实”的进化。

### 🔧 专用模型（代码、数学、医疗、嵌入）

1.  **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** - 作者: yuxinlu1 | 点赞: 2,589 | 下载: 628,225
    - 💡 **一句话说明**: 基于Gemma-4的顶级编程模型，利用Fable和Composer技术优化，在代码生成与推理任务上表现极佳，GGUF量化版广受欢迎。
2.  **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** - 作者: google | 点赞: 156 | 下载: 450
    - 💡 **一句话说明**: Google官方发布的表格数据基础模型，支持零样本分类与回归，是AI在结构化数据分析领域的重要里程碑。
3.  **[BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6)** - 作者: BugTraceAI | 点赞: 127 | 下载: 11,444
    - 💡 **一句话说明**: 专注于网络安全领域的专用模型，擅长漏洞分析、代码审计和渗透测试，是网络安全从业者提效的利器。
4.  **[nationaldesignstudio/rampart](https://huggingface.co/nationaldesignstudio/rampart)** - 作者: nationaldesignstudio | 点赞: 117 | 下载: 1,149
    - 💡 **一句话说明**: 基于ONNX格式、可直接在浏览器中运行的BERT模型，专用于个人身份信息（PII）识别和脱敏，是隐私合规领域的轻量级解决方案。
5.  **[nvidia/Nemotron-Labs-TwoTower-30B-A3B-Base-BF16](https://huggingface.co/nvidia/Nemotron-Labs-TwoTower-30B-A3B-Base-BF16)** - 作者: nvidia | 点赞: 116 | 下载: 10,297
    - 💡 **一句话说明**: 英伟达推出的双塔架构检索模型，专为大规模知识库检索与检索增强生成（RAG）场景设计，性能强大。

### 📦 微调与量化（社区微调、GGUF、AWQ）

1.  **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** - 作者: empero-ai | 点赞: 1,395 | 下载: 1,366,360
    - 💡 **一句话说明**: 社区微调与llama.cpp量化结合最成功的案例之一，将强大的视觉模型压缩到可本地运行的程度。
2.  **[huihui-ai/Huihui-GLM-5.2-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-GLM-5.2-abliterated-GGUF)** - 作者: huihui-ai | 点赞: 148 | 下载: 3,683
    - 💡 **一句话说明**: 对GLM-5.2进行“去审查”（abliterated）处理后的GGUF版本，反映了社区对模型开放性和自由度的持续追求。
3.  **[nvidia/Qwen3.6-27B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-27B-NVFP4)** - 作者: nvidia | 点赞: 233 | 下载: 94,465
    - 💡 **一句话说明**: 英伟达为Qwen3.6定制的企业级量化方案，展示了硬件原厂如何通过模型压缩技术主导云端推理生态。

## 生态信号

本周生态呈现以下关键信号：

- **Qwen/Gemma 生态崛起，GLM 强势回归**：围绕Qwen3.5/3.6和Google Gemma-4的社区微调是绝对主流，众多衍生模型霸占了榜单。同时，智谱GLM-5.2的发布及其官方与英伟达的快速优化版本，表明其已重回第一梯队，尤其在中文多模态领域形成有力竞争。
- **“去审查”及“Agent化”是大趋势**：无论是`HauhauCS`的高强度无审查版模型，还是大量以`agentic`、`terminal`为标签的模型，都表明社区正积极推动模型从“通用对话”走向“特定领域工具”和“高度开放”。
- **量化是普及的关键杠杆**：GGUF格式持续主导本地部署，尤其以9B-35B区间为最。英伟达的NVFP4量化标准则瞄准云端，表明模型量化正演变为既服务个人电脑也服务企业级推理的重要生态层。多模态模型的量化部署（如Qwythos-9B）成为新的爆发点。

## 值得探索

1.  **nvidia/LocateAnything-3B**：作为视觉定位的基石模型，其与RAG、Agent的结合潜力巨大。尝试用它作为智能机器人的“眼睛”，或实现图片内精细信息的问答。
2.  **yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF**：对于开发者而言，这是当前周热度最高的本地编程助手模型之一。建议将其作为VS Code Copilot的本地替代方案进行测试。
3.  **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive**：如果你的研究方向或创意工作需要模型具有极高的创造性和极低的审查门槛，这个拥有超300万下载量的模型是绝佳的实验样本，但请注意伦理边界。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*