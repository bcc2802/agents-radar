# Hugging Face 热门模型日报 2026-07-06

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-06 09:04 UTC

---

好的，作为AI模型生态分析师，这是为您整理的2026年7月6日《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026-07-06**

#### **1. 今日速览**

本周 Hugging Face 社区最显著的趋势是 **“后Qwen时代”的生态爆发**。基于 Qwen 3.5/3.6 系列（尤其是其MoE变体）的微调、量化和应用模型占据了榜单半壁江山，显示了该家族在社区中无可撼动的基建地位。其次，**GGUF量化格式**已从“工具”进化为“标准”，几乎所有热门基座模型（Qwen、Gemma-4、GLM-5.2）都伴随着高下载量的GGUF版本，这表明本地部署和推理效率已成为社区核心诉求。此外，NVIDIA的**4位浮点（NVFP4）量化技术**开始在多款模型中落地，标志着模型压缩领域的新一轮技术竞赛。值得注意的是，来自中国的团队（百度、腾讯、美团及多家个人开发者）在视觉、OCR、MoE和专用Agent模型上持续输出，展现了强大的开源力量。

#### **2. 热门模型分类榜单**

##### 🧠 **语言模型（LLM、对话模型、指令微调）**

*   **zai-org/GLM-5.2**
    *   链接：[https://huggingface.co/zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)
    *   作者：zai-org | 点赞：3,485 | 下载：231,218
    *   说明：智谱最新一代MoE大语言模型，以最高点赞数登顶，代表了国内顶尖开源LLM的最新进展，推理和对话能力强劲。
*   **deepseek-ai/DeepSeek-V4-Pro-DSpark**
    *   链接：[https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)
    *   作者：deepseek-ai | 点赞：397 | 下载：14,276
    *   说明：DeepSeek V4 的专业推理优化版，“DSpark”可能指代新的稀疏激活或推理加速架构，是高端推理任务的强力竞争者。
*   **meituan-longcat/LongCat-2.0**
    *   链接：[https://huggingface.co/meituan-longcat/LongCat-2.0](https://huggingface.co/meituan-longcat/LongCat-2.0)
    *   作者：meituan-longcat | 点赞：78 | 下载：43
    *   说明：美团出品的长上下文模型“长猫”2.0版本，专注于处理超长文本，是长对话和文档分析领域的潜力股。

##### 🎨 **多模态与生成（图像、视频、音频、文本到X）**

*   **baidu/Unlimited-OCR**
    *   链接：[https://huggingface.co/baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)
    *   作者：baidu | 点赞：1,764 | 下载：1,070,230
    *   说明：百度发布的“无限OCR”模型，凭借强大的通用文字识别能力和高下载量，成为本周最受欢迎的专业多模态工具。
*   **nvidia/LocateAnything-3B**
    *   链接：[https://huggingface.co/nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)
    *   作者：nvidia | 点赞：2,621 | 下载：1,340,559
    *   说明：NVIDIA推出的“定位一切”模型，3B参数实现高效、精准的图像中目标定位，是视觉理解和交互任务的基础设施。
*   **krea/Krea-2-Turbo**
    *   链接：[https://huggingface.co/krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)
    *   作者：krea | 点赞：518 | 下载：109,470
    *   说明：Krea公司推出的最新文生图模型Turbo版，在生成速度和图像质量上取得平衡，代表了文本到图像领域的快速迭代。

##### 🔧 **专用模型（代码、数学、医疗、嵌入）**

*   **google/tabfm-1.0.0-pytorch**
    *   链接：[https://huggingface.co/google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)
    *   作者：google | 点赞：235 | 下载：7,036
    *   说明：Google官方的表格基础模型（TabFM），旨在零样本解决表格分类与回归问题，是结构化数据机器学习领域的重要里程碑。
*   **nationaldesignstudio/rampart**
    *   链接：[https://huggingface.co/nationaldesignstudio/rampart](https://huggingface.co/nationaldesignstudio/rampart)
    *   作者：nationaldesignstudio | 点赞：130 | 下载：3,821
    *   说明：专用于PII（个人身份信息）检测的BERT模型，已被转换为ONNX格式并支持浏览器端推理，对于数据脱敏和隐私保护有重要实用价值。

##### 📦 **微调与量化（社区微调、GGUF、AWQ）**

*   **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive**
    *   链接：[https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)
    *   作者：HauhauCS | 点赞：2,505 | 下载：2,910,241
    *   说明：基于Qwen3.6-35B的社区MoE量化版，同时兼具“无审查”和“激进”风格，下载量近300万，是社区共创与效率优化的极致体现。
*   **yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF**
    *   链接：[https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)
    *   作者：yuxinlu1 | 点赞：2,612 | 下载：664,319
    *   说明：Gemma-4-12B的专精编程的GGUF版本，结合了“fable”和“composer”等优化技术，兼顾推理与代码能力，下载量极高。

#### **3. 生态信号**

*   **Qwen 家族统治力不减，MoE 架构成主流**：围绕 Qwen 3.5/3.6（尤其是其 MoE 变体）的社区微调（如 Ornith、AgentWorld）和量化（如 Qwythos、Unsloth Qwen3.6）模型占据了榜单的大部分流量。这表明 Qwen 不仅是强大的基础模型，更成为了新一代社区创新的“操作系统”。
*   **量化技术赛道上演“三国杀”**：除了经典的 GGUF 继续保持统治地位外，NVIDIA 的 NVFP4 (如 `nvidia/Qwen3.6-27B-NVFP4`) 和 Unsloth 的 MTP 量化（如 `unsloth/Qwen3.6-27B-MTP-GGUF`）开始频繁出现。前者代表了硬件厂商对模型精度的新压缩方案，后者则体现了社区工具在量化效率上的极致追求。
*   **Agent / 工具使用模型涌现**：`Qwen-AgentWorld-35B-A3B`, `Agents-A1` 以及 `gemma-4-12B-agentic-*` 等系列模型的上榜，标志着社区关注点从单纯的“对话”转向了“行动”。模型正被训练用于调用工具、编写代码和执行终端命令，这预示着 Agent 原生的开源模型将成为下一波增长点。

#### **4. 值得探索**

1.  **google/tabfm-1.0.0-pytorch**: 强烈推荐给所有从事数据分析、推荐系统或金融风控的团队。它开创性地将基础模型范式引入表格数据，有望颠覆传统的GBDT方法，开启零样本表格预测的新时代。
2.  **nvidia/LocateAnything-3B**: 对计算机视觉和机器人领域的开发者极具价值。它以轻量级模型实现了极强的开放词汇目标定位能力，是构建视觉Agent或自动化标注管线的理想基石。
3.  **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive**: 对于希望进行本地部署、探索模型创造力边界的“硬核”玩家，这个模型是绝佳选择。它完美展示了如何在社区微调中平衡模型性能、量化效率与内容边界，其极高的下载量也证明了其社区影响力。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*