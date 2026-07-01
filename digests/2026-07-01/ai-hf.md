# Hugging Face 热门模型日报 2026-07-01

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-01 03:49 UTC

---

好的，作为AI模型生态分析师，以下是根据您提供的2026年7月1日Hugging Face数据生成的《Hugging Face热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026年7月1日**

#### **今日速览**

本周Hugging Face生态呈现三足鼎立态势：**百度**发布的通用OCR模型`Unlimited-OCR`意外登顶，显示出多模态文档理解需求的爆发；**GLM-5.2**系列（由智谱开源、NVIDIA和Unsloth量化）成为本周最热门的语言模型家族，MoE架构与量化版本齐飞；在生成式AI领域，**Qwen 3.6** 和 **DeepSeek V4** 的社区微调与量化版本持续涌现，而NVIDIA的精准定位模型`LocateAnything-3B`下载量惊人，暗示着Agent与视觉基础模型的结合正在成为新热点。

---

#### **热门模型分类解析**

##### 🧠 **语言模型（LLM、对话模型、指令微调）**

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**  
  **作者**: zai-org | **点赞**: 3,068 | **下载**: 142,547  
  **说明**: 智谱AI开源的MoE架构通用大模型，本周纯语言模型中热度最高，体现了市场对高效MoE结构的强烈兴趣。

- **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)**  
  **作者**: deepseek-ai | **点赞**: 255 | **下载**: 6,939  
  **说明**: DeepSeek V4系列的专业版，配合其DSpark优化技术，代表了顶级闭源模型的开源权重趋势。

- **[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LFM2.5-230M)**  
  **作者**: LiquidAI | **点赞**: 169 | **下载**: 17,839  
  **说明**: Liquid AI推出的超小尺寸模型，证明了小型化、高效能模型在特定场景下的潜力。

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**  
  **作者**: HauhauCS | **点赞**: 2,364 | **下载**: 3,017,678  
  **说明**: Qwen 3.6的社区“无审查”微调版，周下载量破300万，显示出用户对特定风格化或未审查模型的巨大需求。

##### 🎨 **多模态与生成（图像、视频、音频、文本到X）**

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**  
  **作者**: baidu | **点赞**: 1,502 | **下载**: 429,056  
  **说明**: 百度的通用OCR模型，支持图像到文本的转换，凭借其广泛的应用场景和强大的识别能力登顶本周榜单。

- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)**  
  **作者**: krea | **点赞**: 423 | **下载**: 45,668  
  **说明**: Krea的图像生成加速版模型，基于Krea-2-Raw进行优化，追求更快生成速度与更高质量。

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**  
  **作者**: nvidia | **点赞**: 2,525 | **下载**: 800,597  
  **说明**: NVIDIA推出的通用目标定位模型，下载量极高，反映了视觉定位在机器人、自动驾驶等领域的巨大潜力。

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)**  
  **作者**: empero-ai | **点赞**: 1,065 | **下载**: 970,663  
  **说明**: 结合Qwen 3.5与Claude风格数据的微调模型，专注于图像-文本-文本任务，量化版下载量极高。

- **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)**  
  **作者**: fal | **点赞**: 128 | **下载**: 0  
  **说明**: 专门用于图像转视频的LoRA模块，专注于生成逼真的3D风格视频，代表了视频生成领域的细分化创新。

##### 🔧 **专用模型（代码、数学、医疗、嵌入）**

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**  
  **作者**: yuxinlu1 | **点赞**: 2,532 | **下载**: 575,255  
  **说明**: 基于Gemma 4微调的代码专用模型，点赞数极高，表明开发者社区对高质量编程助手模型的需求依然旺盛。

- **[Chunjiang-Intelligence/DeepSeek-v4-Fable](https://huggingface.co/Chunjiang-Intelligence/DeepSeek-v4-Fable)**  
  **作者**: Chunjiang-Intelligence | **点赞**: 134 | **下载**: 1,519  
  **说明**: DeepSeek V4在网络安全领域的专用微调版本，展示了通用大模型向垂直领域渗透的趋势。

##### 📦 **微调与量化（社区微调、GGUF、AWQ）**

- **[nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)**  
  **作者**: nvidia | **点赞**: 184 | **下载**: 104,746  
  **说明**: NVIDIA使用其ModelOpt工具对GLM-5.2进行的4-bit浮点量化（FP4）版本，是顶级模型与先进量化技术结合的典范。

- **[unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)**  
  **作者**: unsloth | **点赞**: 486 | **下载**: 180,394  
  **说明**: 由知名量化团队Unsloth为GLM-5.2制作的GGUF格式版本，极大地方便了开发者使用llama.cpp在本地部署。

- **[nvidia/Qwen3.6-35B-A3B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4)**  
  **作者**: nvidia | **点赞**: 391 | **下载**: 5,495,402  
  **说明**: NVIDIA对Qwen 3.6 MoE模型的FP4量化版，是本周下载量最高的模型，证明了NVFP4量化技术在社区的广泛应用。

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)**  
  **作者**: deepreinforce-ai | **点赞**: 557 | **下载**: 157,418  
  **说明**: Ornith系列模型的35B量化版，该系列有9B、35B、397B等多个尺寸，展示了社区对“全家桶”模型的量化需求。

- **[huihui-ai/Huihui-GLM-5.2-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-GLM-5.2-abliterated-GGUF)**  
  **作者**: huihui-ai | **点赞**: 102 | **下载**: 65  
  **说明**: 对GLM-5.2进行“abliterated”（移除安全限制）处理的GGUF版本，反映了社区对模型控制与个性化的探索。

---

#### **生态信号**

1.  **模型家族化与MoE浪潮**：本周最引人注目的趋势是**Qwen 3.6**、**GLM-5.2**、**DeepSeek V4**和**Ornith**四大模型家族霸榜。它们都普遍采用**MoE（混合专家）** 架构，如`Qwen3.6-35B-A3B`，表明高效激活参数的大模型已成为主流。
2.  **开源与量化生态深度绑定**：所有热门基础模型几乎都伴随着**NVIDIA（NVFP4）** 和**Unsloth（GGUF）** 等团队的量化版本。这反映出开源大模型的价值越来越倚重于下游量化与部署工具链的成熟度。`Qwen3.6-35B-A3B-NVFP4`周下载量超500万，是基础模型的数倍，说明社区更倾向于使用“即拿即用”的量化模型。
3.  **应用场景驱动热度**：本次榜单的头部模型中，`Unlimited-OCR`和`LocateAnything-3B`均为非聊天类应用模型，其高热度表明，在生成式AI之外，**视觉理解、文档处理**等更落地的任务正在成为新的增长点。同时，`gemma-4-12B-coder`系列表现突出，验证了代码生成是LLM最确定性的杀手级应用之一。

---

#### **值得探索**

1.  **🏆 [nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**  
    **理由**：作为本周下载量最高的模型之一，它代表了通用视觉定位技术的巨大进步。对于任何需要Agent与现实世界交互、图像编辑或物体识别的项目，这是一个绝佳的起点。其3B的参数量也使其具备本地部署的潜力。

2.  **🏆 [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**  
    **理由**：这是一个极具社区代表性的实验性模型。它在MOE架构上进行了大胆的取消审查和风格调整，周下载量高达300万。对于研究人员和高级用户，值得分析其在安全性、创造力及对齐性能上的取舍，这将是理解未来模型个性化发展的重要样本。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*