# Hugging Face 热门模型日报 2026-07-07

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-07 08:27 UTC

---

好的，作为AI模型生态分析师，以下是基于2026年7月7日数据生成的《Hugging Face 热门模型日报》。

---

### Hugging Face 热门模型日报 | 2026年7月7日

#### 1. 今日速览

本周 Hugging Face 生态呈现出几个核心趋势：**多模态模型**与**深度思考/推理能力**成为竞争焦点。以 Qwen 3.5/3.6 和 Gemma 4 为基础的社区微调与量化模型占据了榜单半壁江山，其中针对“智能体”和“代码”领域的专用模型尤其火爆。值得注意的是，**NVIDIA 的 LocateAnything** 在视觉定位任务上异军突起，展示了大型科技公司在特定垂直领域的强大影响力。同时，**模型量化（GGUF）** 依然是社区参与的主旋律，推动了高性能模型在消费级硬件上的落地。

#### 2. 热门模型

##### 🧠 语言模型（LLM、对话模型、指令微调）

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**
  - 作者: zai-org | 点赞: 3,547 | 下载: 231,218
  - 说明: 智谱AI的下一代开源MoE大模型，凭借强悍的对话能力和MoE架构的高效性，获得了本周最高点赞数。

- **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)**
  - 作者: deepseek-ai | 点赞: 414 | 下载: 14,276
  - 说明: DeepSeek 最新的V4专业版本，专注于推理和深度思考（DSpark），代表了顶尖开源模型在复杂推理上的突破。

- **[nvidia/Nemotron-Labs-TwoTower-30B-A3B-Base-BF16](https://huggingface.co/nvidia/Nemotron-Labs-TwoTower-30B-A3B-Base-BF16)**
  - 作者: nvidia | 点赞: 128 | 下载: 10,936
  - 说明: NVIDIA 推出的“双塔”架构基础模型，探索了新的模型结构，为未来的高效推理和表征学习提供了新思路。

- **[meituan-longcat/LongCat-2.0](https://huggingface.co/meituan-longcat/LongCat-2.0)**
  - 作者: meituan-longcat | 点赞: 122 | 下载: 43
  - 说明: 美团发布的长文本对话模型，专注于处理超长上下文，是企业级应用在长文档理解领域的代表。

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**
  - 作者: nvidia | 点赞: 2,641 | 下载: 1,424,958
  - 说明: 本周最大黑马。一个3B参数的视觉定位模型，能够根据自然语言描述定位图像中任意物体，性能与下载量双高。

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**
  - 作者: HauhauCS | 点赞: 2,533 | 下载: 2,910,241
  - 说明: 基于Qwen3.6的“激进”去审查版本，下载量巨大，反映了社区对“无审查”和更富创造力的多模态模型有强烈需求。

- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)**
  - 作者: krea | 点赞: 532 | 下载: 109,470
  - 说明: Krea 推出的图像生成 Turbo 版，代表了开源文生图模型向高速、高质量方向演进的最新成果。

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**
  - 作者: baidu | 点赞: 1,806 | 下载: 1,070,230
  - 说明: 百度发布的通用OCR大模型，号称“无限制”OCR，下载量超过百万，证明其在文档数字化领域的巨大实用价值。

##### 🔧 专用模型（代码、数学、医疗、嵌入）

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**
  - 作者: yuxinlu1 | 点赞: 2,624 | 下载: 664,319
  - 说明: 基于Gemma 4的顶级代码模型，结合了“fable”和“composer”技术，是针对代码生成和推理的垂直优化精品。

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)**
  - 作者: google | 点赞: 263 | 下载: 7,036
  - 说明: Google推出的首个面向表格数据的通用基础模型（TabFM），支持零样本分类和回归，开创了非语言/图像领域的新赛道。

- **[nationaldesignstudio/rampart](https://huggingface.co/nationaldesignstudio/rampart)**
  - 作者: nationaldesignstudio | 点赞: 137 | 下载: 3,821
  - 说明: 一个用于PII（个人身份信息）识别的专有模型，支持ONNX和Transformers.js，体现了模型在数据安全和隐私保护方面的专业应用。

##### 📦 微调与量化（社区微调、GGUF、AWQ）

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)**
  - 作者: empero-ai | 点赞: 1,681 | 下载: 1,617,508
  - 说明: 融合Claude风格与Qwen3.5的超长上下文（1M）模型量化版，下载量极高的“缝合怪”模型，代表了社区对混合能力和大上下文的需求。

- **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)**
  - 作者: unsloth | 点赞: 980 | 下载: 2,818,499
  - 说明: 几乎最新的Qwen3.6模型被Unsloth团队光速量化，下载量接近300万，证明了量化能力是推动模型普及的关键环节。

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)**
  - 作者: yuxinlu1 | 点赞: 1,061 | 下载: 370,884
  - 说明: 面向Agent的Gemma 4模型量化版，是社区探索LLM作为智能体（Agentic）核心能力的前沿实践。

- **[huihui-ai/Huihui-GLM-5.2-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-GLM-5.2-abliterated-GGUF)**
  - 作者: huihui-ai | 点赞: 180 | 下载: 6,660
  - 说明: 对GLM-5.2进行“abliterated”（移除安全护栏）处理的量化版，反映了社区对模型控制力和自由度边界探索的持续兴趣。

#### 3. 生态信号

- **Qwen 家族与 Gemma 4 双雄争霸**：模型生态正非常明显地围绕 **Qwen 3.5/3.6** 和 **Google Gemma 4** 两大基座展开。社区几乎在基座模型发布的同一天就产出了针对代码、智能体、多模态任务的大量微调版本，形成了强大的技术飞轮。
- **开源权重的速度优势**：闭源模型（如Claude）的影响力主要体现在风格/数据的蒸馏上，而**开源权重模型（Qwen、Gemma、GLM）** 则直接通过量化、微调（如Ornith、Hy3）实现了高速迭代和广泛部署，巩固了开源生态的领先地位。
- **量化是最活跃的基础设施**：Unsloth、Llama.cpp 等技术栈已成为社区的标准配置。模型是否提供高质量的 **GGUF** 版本，直接决定了其下载量和应用广度。MTP（多令牌预测）等高效量化技术正在成为流行词，暗示未来模型在保持性能的同时将进一步“瘦身”。

#### 4. 值得探索

1.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**：如果你想探索AI的前沿应用，这个模型值得一试。它将视觉定位能力压缩到3B参数，性能强大，是构建视觉Agent、智能检索等应用的基础工具。其独特的“Locate Anything”概念，预示着人机交互的新范式。

2.  **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**：对于开发者和AI研究者，这是本周最值得细品的代码模型。它展示了在12B参数级别，通过精细的微调技术（如作曲家模式）可以达到的编码推理高度。如果你想寻找一个能在本地运行的最佳代码助手，这是首选。

3.  **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**：如果你对国产大模型的全球竞争力感兴趣，GLM-5.2 是必看的标杆。它不仅代表了智谱在MoE架构上的成熟应用，其微调版本（如Huihui的Abliterated版）还展示了社区对其强大的基础能力的认可和再创造。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*