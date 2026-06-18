# ArXiv AI 研究日报 2026-06-18

> 数据来源: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 共 50 篇论文 | 生成时间: 2026-06-18 03:55 UTC

---

好的，作为AI研究分析师，以下是基于您提供的2026-06-18 ArXiv论文列表生成的《ArXiv AI 研究日报》。

---

### ArXiv AI 研究日报 — 2026年6月18日

#### 今日速览

今日投稿呈现出三个清晰的方向：**推理模型的优化与解释**成为焦点，涵盖从扩散模型进行长链推理（DreamReasoner-8B）到利用强化学习进行后训练（STARE）及尝试移除特定推理能力（MAST）；**智能体的交互与评估**走向深化，不仅关注多智能体博弈（Fictitious Play）和用户模拟（Turing Rewards），还开始探索可信度修复（Self-Correction）等社会性挑战；此外，**神经符号与可解释性**方法再次受到关注，如用程序合成解释注意力机制（Explaining Attention）和实现统一的神经符号语义框架（NeSyCat Torch）。

#### 重点论文

##### 🧠 大语言模型（架构、训练、对齐、评估）

1.  **[DreamReasoner-8B: Block-Size Curriculum Learning for Diffusion Reasoning Models](http://arxiv.org/abs/2606.19257v1)**
    *   作者: Zirui Wu et al.
    *   **一句话说明**：首个开源的大规模块状扩散语言模型，通过创新的“块大小课程学习”策略，成功让非自回归的扩散模型可靠地执行长链思维（CoT）推理。

2.  **[STARE: Surprisal-Guided Token-Level Advantage Reweighting for Policy Entropy Stability](http://arxiv.org/abs/2606.19236v1)**
    *   作者: Haipeng Luo et al.
    *   **一句话说明**：针对基于可验证奖励的强化学习（如GRPO）训练LLM时常见的策略熵坍塌问题，提出了一种基于惊异度的token级优势重加权方法，稳定了训练过程，提升了推理能力。

3.  **[Mechanism-Guided Selective Unlearning for RLVR-Induced Reasoning](http://arxiv.org/abs/2606.19222v1)**
    *   作者: Chenyu Zhou et al.
    *   **一句话说明**：提出MAST方法，首次实现了对模型通过强化学习获得的特定“推理”能力进行精准“遗忘”，且对其他能力损伤极小，为模型的能力控制提供了新工具。

4.  **[Confidence is Not Reliability: Rethinking MC Dropout in Brain Tumour Segmentation](http://arxiv.org/abs/2606.19300v1)**
    *   作者: Xin Ci Wong et al.
    *   **一句话说明**：一项深刻的实证研究，揭示了在关键的医学图像分割任务中，模型输出的置信度与可靠性之间存在巨大鸿沟，对当前不确定性估计方法的有效性提出了根本性质疑。

##### 🤖 智能体与推理（规划、工具使用、多智能体、思维链）

5.  **[Enhancing Decision-Making with Large Language Models through Multi-Agent Fictitious Play](http://arxiv.org/abs/2606.19308v1)**
    *   作者: Leyang Shen et al.
    *   **一句话说明**：将博弈论中的经典算法“虚构博弈”引入多智能体LLM系统，使智能体能在决策任务中通过模拟对手策略来优化自身行为，而不仅仅是简单的任务分解。

6.  **[Learning User Simulators with Turing Rewards](http://arxiv.org/abs/2606.19336v1)**
    *   作者: Yingshan Susan Wang et al.
    *   **一句话说明**：提出“图灵奖励”机制来训练LLM用户模拟器，目标是模拟出无法被真实人类与一个理想算法区分的行为，为更真实的智能体评估和个性化系统训练提供了新范式。

7.  **[Correct Yourself, Keep My Trust: How Self-Correction and Social Connection Shape Credibility in Social Chatbots](http://arxiv.org/abs/2606.19286v1)**
    *   作者: Biswadeep Sen, Yi-Chieh Lee
    *   **一句话说明**：研究了社交聊天机器人犯错后如何恢复用户信任，发现单纯的自我纠错不如强化社交连接有效，为构建更具弹性的社交AI提供了关键设计洞见。

##### 🔧 方法与框架（新技术、基准测试、效率优化）

8.  **[Explaining Attention with Program Synthesis](http://arxiv.org/abs/2606.19317v1)**
    *   作者: Amiri Hayes, Belinda Li, Jacob Andreas
    *   **一句话说明**：提出用可执行的程序（如决策树）来近似并解释注意力头的行为，将可解释AI从可视化提升到符号化描述的新高度，可能成为理解Transformer的新标准工具。

9.  **[NeSyCat Torch: A Differentiable Tensor Implementation of Categorical Semantics for Neurosymbolic Learning](http://arxiv.org/abs/2606.19279v1)**
    *   作者: Daniel Romero Schellhorn et al.
    *   **一句话说明**：基于范畴论，提供了一个统一、可微分的PyTorch实现，能将经典的、模糊的、概率的和神经网络的语义统一到一个框架下，极大简化了神经符号系统的开发与对比。

10. **[A Multi-Domain Benchmark for Detecting AI-Generated Text-Rich Images from GPT-Image-2](http://arxiv.org/abs/2606.19259v1)**
    *   作者: Yijin Wang et al.
    *   **一句话说明**：针对最新多模态生成模型（如GPT-Image-2）生成的、包含文字的图像，推出了首个跨领域基准测试，直面金融、医疗等领域中文字伪造的风险。

11. **[UBP2: Uncertainty-Balanced Preference Planning for Efficient Preference-based Reinforcement Learning](http://arxiv.org/abs/2606.19328v1)**
    *   作者: Mohamed Nabail et al.
    *   **一句话说明**：提出了一种新的基于偏好的强化学习范式，通过主动查询最具有信息量的偏好数据（平衡不确定性和偏好冲突），显著提高了样本效率。

##### 📊 应用（垂直领域、多模态、代码生成）

12. **[Freeing the Law with LOCUS: A Local Ordinance Corpus for the United States](http://arxiv.org/abs/2606.19334v1)**
    *   作者: Denis Peskoff et al.
    *   **一句话说明**：发布了首个大规模、可机读的美国地方法规语料库LOCUS，填补了法律AI在地方性法规层面的关键数据空白，价值巨大。

13. **[Does VLA Even Know the Basics? Measuring Commonsense and World Knowledge Retention in Vision-Language-Action Models](http://arxiv.org/abs/2606.19297v1)**
    *   作者: Nikita Kachaev et al.
    *   **一句话说明**：对“视觉-语言-行动”模型（VLA）进行了一次“知识体检”，发现它们在微调为机器人策略后，原有的常识和世界知识严重丢失，为未来具身智能模型的训练方式敲响警钟。

14. **[Data Intelligence Agents: Interpreting, Modeling, and Querying Enterprise Data via Autonomous Coding Agents](http://arxiv.org/abs/2606.19319v1)**
    *   作者: Anoushka Vyas et al.
    *   **一句话说明**：提出一个由三个自主编码智能体组成的系统（DIA），可以自动化完成从解读数据、建模到查询的全流程，有望彻底改变企业数据协作的效率。

#### 研究趋势信号

今日论文显示，**AI研究的重心正从“生成能力”向“认知与交互智能”转移**。一方面，研究者不再满足于模型“能说会道”，而是深入其内部机制，尝试解释（程序合成）、重组（块扩散）、甚至精确移除（选择性遗忘）特定能力。另一方面，智能体的研究进入了“社会博弈”阶段，开始关注模拟真实用户、策略互动以及在复杂社会情境中维护用户信任等高级认知与社交行为。这预示着一个更严谨、更可解释、更具社会性智能的AI发展新时代。

#### 值得精读

1.  **[Explaining Attention with Program Synthesis](http://arxiv.org/abs/2606.19317v1)**
    *   **理由**：这项工作在可解释AI领域迈出了关键一步。它用具体、可执行的程序替代了模糊的热力图解释，为理解和调试Transformer模型提供了前所未有的精确性和透明度，是所有关注模型可解释性研究者必读的文献。

2.  **[Does VLA Even Know the Basics? Measuring Commonsense and World Knowledge Retention in Vision-Language-Action Models](http://arxiv.org/abs/2606.19297v1)**
    *   **理由**：这是一篇“泼冷水”式的优秀研究。它指出了一个普遍存在但被忽视的严重问题：大模型微调为具身智能体时会导致知识灾难性遗忘。其发现对机器人、自动驾驶等领域的从业者具有极高的警示和指导意义。

3.  **[DreamReasoner-8B: Block-Size Curriculum Learning for Diffusion Reasoning Models](http://arxiv.org/abs/2606.19257v1)**
    *   **理由**：该工作将非自回归（扩散）生成模型成功应用于长链推理，挑战了当前自回归模型在该领域的统治地位。其提出的课程学习方法为构建更快、更高效的推理模型开辟了全新道路，代表了架构创新的前沿。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*