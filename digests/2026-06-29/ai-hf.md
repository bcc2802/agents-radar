# Hugging Face 热门模型日报 2026-06-29

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-29 03:52 UTC

---

好的，作为AI模型生态分析师，这是为您生成的2026年6月29日Hugging Face热门模型日报。

---

### 《Hugging Face 热门模型日报》—— 2026年6月29日

#### 今日速览

本周Hugging Face社区呈现三大趋势：**头部大厂MoE架构模型成为绝对主流**，GLM-5.2和Qwen3.5/3.6系列的多版本、多量化形式霸榜；**社区微调与量化生态异常活跃**，尤其是GGUF格式的“无审查（Uncensored）”变体下载量惊人，显示出对高度定制化模型的需求；**从文字到多模态的扩展加速**，OCR、图像生成、视频生成和语音识别模型均有亮眼表现，其中百度的Unlimited-OCR和nvidia的ASR模型颇受关注。

#### 热门模型

##### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型名称 | 作者 | 点赞 | 下载 | 一句话说明 |
| :--- | :--- | :--- | :--- | :--- |
| [**GLM-5.2**](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 2,835 | 118,651 | 点赞数第一的MoE大模型，代表着国产大模型在开源社区的强劲势头。 |
| [**HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive**](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 2,303 | 3,248,724 | Qwen3.6的无审查“激进”版本，凭借超高的下载量成为本周社区最活跃的模型。 |
| [**empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF**](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 811 | 831,529 | 基于Qwen3.5的社区微调模型，其GGUF量化版本因高性能和易部署性而广受欢迎。 |
| [**deepreinforce-ai/Ornith-1.0-35B-GGUF**](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF) | deepreinforce-ai | 419 | 79,630 | 35B参数级别的Ornith模型，多尺寸策略（9B、35B、397B）显示了向不同场景提供差异化模型的趋势。 |
| [**Qwen/Qwen-AgentWorld-35B-A3B**](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B) | Qwen | 403 | 23,697 | 阿里巴巴推出的Agent专用世界模型，标志着LLM开始向具身智能和复杂任务规划深入。 |
| [**deepreinforce-ai/Ornith-1.0-9B**](https://huggingface.co/deepreinforce-ai/Ornith-1.0-9B) | deepreinforce-ai | 237 | 5,814 | Ornith系列9B参数的基础版本，与量化版配合形成完整的产品线。 |
| [**WeiboAI/VibeThinker-3B**](https://huggingface.co/WeiboAI/VibeThinker-3B) | WeiboAI | 743 | 59,337 | 仅3B参数的微博AI模型，在“数学”任务上表现突出，证明了小模型的潜力。 |
| [**microsoft/FastContext-1.0-4B-SFT**](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT) | microsoft | 369 | 6,779 | 微软推出的4B参数模型，专注于长上下文处理，可能对RAG和文档分析领域产生影响。 |

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型名称 | 作者 | 点赞 | 下载 | 一句话说明 |
| :--- | :--- | :--- | :--- | :--- |
| [**baidu/Unlimited-OCR**](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 1,249 | 295,064 | 百度推出的全能OCR模型，在图文理解任务上达到新高度，应用场景极为广泛。 |
| [**krea/Krea-2-Turbo**](https://huggingface.co/krea/Krea-2-Turbo) | krea | 359 | 27,631 | Krea推出的快速版文生图模型，与Raw版形成速度与质量的互补。 |
| [**nvidia/LocateAnything-3B**](https://huggingface.co/nvidia/LocateAnything-3B) | nvidia | 2,437 | 646,451 | 英伟达发布的“指哪打哪”的目标定位模型，在图像特征提取任务上表现惊艳。 |
| [**nvidia/nemotron-3.5-asr-streaming-0.6b**](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b) | nvidia | 734 | 67,419 | 专注于流式语音识别的0.6B小模型，为实时语音应用提供了高效的解决方案。 |
| [**fal/LTX-2.3-3DREAL-LoRA**](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA) | fal | 97 | 0 | 专注于文生视频垂直领域的LoRA，展示了社区对视频生成模型的持续探索。 |

##### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型名称 | 作者 | 点赞 | 下载 | 一句话说明 |
| :--- | :--- | :--- | :--- | :--- |
| [**yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF**](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF) | yuxinlu1 | 2,477 | 549,926 | 社区基于Google Gemma微调的代码模型，下载量极高，验证了Gemma开源策略的成功。 |
| [**Chunjiang-Intelligence/DeepSeek-v4-Fable**](https://huggingface.co/Chunjiang-Intelligence/DeepSeek-v4-Fable) | Chunjiang-Intelligence | 124 | 1,409 | 基于DeepSeek-V4的网络安全专用模型，代表着大模型在垂直安全领域的深度定制。 |
| [**nvidia/GLM-5.2-NVFP4**](https://huggingface.co/nvidia/GLM-5.2-NVFP4) | nvidia | 155 | 45,762 | 英伟达为GLM-5.2提供的NVFP4低精度优化版，代表了云端大模型部署的硬件-软件协同生态。 |

##### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型名称 | 作者 | 点赞 | 下载 | 一句话说明 |
| :--- | :--- | :--- | :--- | :--- |
| [**empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF**](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 811 | 831,529 | 结合了Claude对话风格的“神话”微调，并以GGUF形式发布，是量化+风格定制模式的范例。 |
| [**yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF**](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF) | yuxinlu1 | 802 | 225,822 | 另一款基于Gemma的代码模型GGUF版，与coder版形成“代码”和“代理”的细分。 |
| [**unsloth/GLM-5.2-GGUF**](https://huggingface.co/unsloth/GLM-5.2-GGUF) | unsloth | 444 | 146,023 | unsloth为GLM-5.2提供的量化版，表明社区量化工具与最新大模型的适配速度极快。 |
| [**HauhauCS/Gemma4-12B-QAT-Uncensored-HauhauCS-Balanced**](https://huggingface.co/HauhauCS/Gemma4-12B-QAT-Uncensored-HauhauCS-Balanced) | HauhauCS | 101 | 40,820 | 另一款“无审查”Gemma变体，使用QAT方法量化，反映了社区对“自由度”和“可控性”的追求。 |
| [**nvidia/Qwen3.6-35B-A3B-NVFP4**](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4) | nvidia | 371 | 5,235,413 | 下载量最高的模型之一，英伟达自研的NVFP4量化格式正在成为云端MoE模型部署的新标准。 |

#### 生态信号

1.  **模型家族“军备竞赛”白热化**。本周最重要信号是**GLM-5.2**和**Qwen 3.x**两大系列在多个维度（原版、量化、微调）上激烈竞争。它们与**DeepSeek-V4**共同构成了当前开源大模型的“三国杀”格局。
2.  **量化是社区活力的命脉。GGUF和NVFP4是两大赢家**。GGUF在个人开发者和消费级显卡生态中无可撼动，而英伟达的NVFP4凭借其针对特定硬件的极强优化和惊人的下载量，正在云端部署生态中建立起新的事实标准。
3.  **“无审查 (Uncensored)”与“高度定制”需求强劲**。HauhauCS发布的多个“Uncensored”模型，尤其是Qwen3.6版本，其百万级的下载量远超大部分官方模型，说明社区对内容限制和模型行为控制有着强烈且多样的诉求。

#### 值得探索

1.  **nvidia/LocateAnything-3B** ([链接](https://huggingface.co/nvidia/LocateAnything-3B))：它不仅仅是“寻物”。高点赞和下载量表明，这种**视觉定位能力**是构建机器人、自动驾驶和工业检测等具身智能应用的关键组件，非常值得研究其技术细节。
2.  **Qwen/Qwen-AgentWorld-35B-A3B** ([链接](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B))：这是本周最引人注目的“概念模型”。它标志着LLM正在从“对话聊天”转向 **“构建世界模拟器”** ，为未来的智能体和游戏AI提供了全新的技术范式。推荐开发者深入探索其论文和应用场景。
3.  **microsoft/FastContext-1.0-4B-SFT** ([链接](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT))：在所有模型都在追求更大、更强时，微软反其道而行之，用4B小模型挑战长上下文。这非常符合**边缘计算**和**效率导向**的趋势。如果你在关注RAG、文档分析等对上下文窗口要求高的任务，这个模型值得一试。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*