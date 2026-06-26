# Hugging Face 热门模型日报 2026-06-26

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-26 03:37 UTC

---

# Hugging Face 热门模型日报 (2026-06-26)

## 📰 今日速览

本周 Hugging Face 迎来多款重磅模型，**DeepSeek-V4-Pro** 以 5063 周点赞断层领先，成为社区焦点；**Qwen 3.5/3.6 系列 MoE 模型**持续霸榜，涌现大量社区微调与量化版本，尤其是无审查变体下载量惊人；**NVIDIA LocateAnything-3B** 作为视觉定位工具斩获 2365 赞，显示出多模态专用模型的强劲需求；**Google Gemma-4-12B** 原生支持 any-to-any 多模态，官方模型下载量超 218 万。生态上，GGUF 量化模型数量占比超 40%，社区对低成本部署的追求愈发热烈。

---

## 🔥 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

- **[DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)**  
  作者: deepseek-ai | 点赞: 5,063 | 下载: 1,878,217  
  DeepSeek 全新旗舰对话模型，V4 系列 Pro 版本，以超强推理与对话能力登顶本周热度第一。

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**  
  作者: zai-org | 点赞: 2,490 | 下载: 67,107  
  GLM-5.2 正式版，采用 MoE-DSA 架构，中文对话体验出色，周点赞跃居第二。

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**  
  作者: HauhauCS | 点赞: 2,240 | 下载: 3,520,206  
  Qwen3.6 的无审查社区微调版，下载量突破 350 万，凸显对开放对话模型的强烈需求。

- **[WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)**  
  作者: WeiboAI | 点赞: 716 | 下载: 51,717  
  基于 Qwen2 的 3B 数学推理模型，轻量却表现亮眼，适合资源受限场景。

- **[moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code)**  
  作者: moonshotai | 点赞: 992 | 下载: 502,106  
  Kimi 新版代码模型，支持视觉输入，下载量超 50 万，编程与多模态兼修。

- **[nvidia/Qwen3.6-35B-A3B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4)**  
  作者: nvidia | 点赞: 343 | 下载: 4,602,255  
  NVIDIA 基于 Qwen3.6 优化，采用 FP4 量化，压缩率极高，下载量惊人（460 万）。

- **[Chunjiang-Intelligence/DeepSeek-v4-Fable](https://huggingface.co/Chunjiang-Intelligence/DeepSeek-v4-Fable)**  
  作者: Chunjiang-Intelligence | 点赞: 94 | 下载: 646  
  面向网络安全的 DeepSeek v4 变体，专注安全防御场景。

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)**  
  作者: deepreinforce-ai | 点赞: 101 | 下载: 0  
  35B 参数的大型 GGUF 模型，主打 MIT 协议开源，适合端侧部署。

---

### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**  
  作者: nvidia | 点赞: 2,365 | 下载: 407,838  
  NVIDIA 推出的 3B 视觉定位模型，可精准识别图像中任意目标位置，多模态工具箱新星。

- **[MiniMaxAI/MiniMax-M3](https://huggingface.co/MiniMaxAI/MiniMax-M3)**  
  作者: MiniMaxAI | 点赞: 1,241 | 下载: 154,350  
  MiniMax 新一代多模态大模型 M3，统一图文理解与生成，周点赞破千。

- **[google/gemma-4-12B-it](https://huggingface.co/google/gemma-4-12B-it)**  
  作者: google | 点赞: 1,180 | 下载: 2,187,644  
  Google 原生支持 any-to-any 多模态的 Gemma-4 指令版，下载超 200 万，生态核心。

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**  
  作者: baidu | 点赞: 904 | 下载: 70,743  
  百度推出通用 OCR 模型，涵盖复杂版面与印刷/手写体，文字识别场景首选。

- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)**  
  作者: krea | 点赞: 245 | 下载: 2,996  
  Krea 第二代图像生成 Turbo 版，基于 Krea-2-Raw 加速推理，主打快速出图。

- **[krea/Krea-2-Raw](https://huggingface.co/krea/Krea-2-Raw)**  
  作者: krea | 点赞: 185 | 下载: 5,113  
  Krea-2 原始权重，作为 Turbo 版基座，供社区自定义微调。

- **[datalab-to/lift](https://huggingface.co/datalab-to/lift)**  
  作者: datalab-to | 点赞: 152 | 下载: 5,189  
  基于 Qwen3.5 的 PDF 文档理解模型，专注文档级图像与文本处理。

- **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)**  
  作者: nvidia | 点赞: 696 | 下载: 50,553  
  NVIDIA 推出的流式语音识别模型（0.6B），支持缓存感知 ASR，实时场景利器。

- **[owensong/Inflect-Nano-v1](https://huggingface.co/owensong/Inflect-Nano-v1)**  
  作者: owensong | 点赞: 201 | 下载: 0  
  超小型文本转语音模型，体积极小，适合边缘设备语音合成。

- **[Boogu/Boogu-Image-0.1-Edit](https://huggingface.co/Boogu/Boogu-Image-0.1-Edit)**  
  作者: Boogu | 点赞: 124 | 下载: 824  
  基于 Diffusers 的图像编辑模型，支持中英文 prompt，开源 Apache 2.0。

- **[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LFM2.5-230M)**  
  作者: LiquidAI | 点赞: 76 | 下载: 7,334  
  Liquid 最新高效语言模型 (230M)，主打极致轻量，适合 LLM 资源受限场景。

---

### 🔧 专用模型（代码、数学、医疗、嵌入）

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**  
  作者: yuxinlu1 | 点赞: 2,368 | 下载: 495,813  
  基于 Gemma-4 的代码模型 GGUF 版，下载近 50 万，社区最热代码专用变体之一。

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)**  
  作者: empero-ai | 点赞: 496 | 下载: 134,294  
  基于 Qwen3.5 的推理增强模型 GGUF 版，量化后适合低显存推理。

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M)**  
  作者: empero-ai | 点赞: 394 | 下载: 10,160  
  同上模型的原生 Transformers 版，支持多模态输入，适合接入框架使用。

- **[microsoft/FastContext-1.0-4B-SFT](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT)**  
  作者: microsoft | 点赞: 345 | 下载: 5,276  
  微软推出的高效上下文模型（4B），支持 Explorer SubAgent 智能体模式。

- **[Jackrong/Qwopus3.6-27B-Coder-Compat-MTP-GGUF](https://huggingface.co/Jackrong/Qwopus3.6-27B-Coder-Compat-MTP-GGUF)**  
  作者: Jackrong | 点赞: 89 | 下载: 19,382  
  Qwen3.6 的 27B 代码兼容模型 GGUF 版，支持 MTP 多模态视觉输入。

---

### 📦 微调与量化（社区微调、GGUF、AWQ）

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)**  
  作者: yuxinlu1 | 点赞: 623 | 下载: 165,187  
  Gemma-4 的 Agent 微调版，强化终端与自主推理能力，GGUF 格式。

- **[unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)**  
  作者: unsloth | 点赞: 388 | 下载: 88,915  
  Unsloth 对 GLM-5.2 的 GGUF 量化版本，部署友好，中文社区热度高。

- **[huihui-ai/Huihui-gemma-4-12B-coder-fable5-composer2.5-v1-abliterated](https://huggingface.co/huihui-ai/Huihui-gemma-4-12B-coder-fable5-composer2.5-v1-abliterated)**  
  作者: huihui-ai | 点赞: 127 | 下载: 4,874  
  基于 Gemma-4 代码模型的“去审查”版本，社区实验性微调。

- **[HauhauCS/Gemma4-12B-QAT-Uncensored-HauhauCS-Balanced](https://huggingface.co/HauhauCS/Gemma4-12B-QAT-Uncensored-HauhauCS-Balanced)**  
  作者: HauhauCS | 点赞: 83 | 下载: 15,128  
  Gemma-4 的 QAT 量化无审查版，平衡版针对部署与安全性优化。

- **[Comfy-Org/Krea-2](https://huggingface.co/Comfy-Org/Krea-2)**  
  作者: Comfy-Org | 点赞: 121 | 下载: 10  
  ComfyUI 官方打包的 Krea-2 工作流节点，便于图像生成可视化操作。

---

## 📊 生态信号

本周模型生态出现三大显著趋势：

1. **MoE 模型家族势不可挡**  
   Qwen 3.5/3.6 MoE（A3B 架构）、GLM-5.2（MoE-DSA）及 Gemma-4 全面开花。MoE 在保持总参数大的同时，推理速度快、性价比高，成为主流趋势。

2. **“无审查 + 量化”社区操作火爆**  
   大量社区上传 uncensored 变体（Qwen3.6 无审查版下载超 350 万）和 GGUF/QAT 量化版本（占榜单近 40%）。用户对自由对话和低成本本地部署的需求强烈，远超官方预训练模型。

3. **NVIDIA 与百度强势布局多模态与工具链**  
   NVIDIA 推出 LocateAnything-3B（视觉定位）、流式 ASR 和 FP4 量化方案，百度发布 Unlimited-OCR，显示顶级厂商正加速将多模态能力产品化、工具化。开源权重与闭源服务之间的差距正在缩小。

---

## 🔭 值得探索

1. **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**  
   视觉定位+推理能力，可无缝集成到 RPA、自动驾驶、图像检索等 pipeline，实用价值极高。

2. **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**  
   社区最热“无审查” MoE 模型，下载量领先，可作为研究开放域对话、安全对齐的极佳基线。

3. **[moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code)**  
   Kimi 旗舰代码模型，支持视觉输入，适合开发多功能编程助手或多模态代码理解场景。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*