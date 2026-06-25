# ArXiv AI 研究日报 2026-06-25

> 数据来源: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 共 50 篇论文 | 生成时间: 2026-06-25 03:30 UTC

---

好的，作为AI研究分析师，以下是根据您提供的2026年6月25日ArXiv论文生成的《ArXiv AI研究日报》。

---

### **ArXiv AI 研究日报 | 2026-06-25**

#### **今日速览**

今日投稿呈现两大核心趋势：**AI Agent的安全性与可靠性**成为绝对焦点，多篇论文探讨了从行为审计、运行时隔离到逆向工程的系统性问题。同时，**后训练阶段（Post-training）的强化学习**取得显著进展，研究者们致力于解决RL在Agent和机器人任务中的样本效率低与训练不稳定难题。此外，对模型**鲁棒性和评估方法**的反思也在深化，包括对多模态模型顺序敏感性、文学翻译质量以及情感语音交互等细微维度的审计。

---

#### **重点论文**

##### 🧠 大语言模型（架构、训练、对齐、评估）

1.  **Model Forensics: Investigating Whether Concerning Behavior Reflects Misalignment**
    - 作者: A. Singh et al.
    - 链接: [http://arxiv.org/abs/2606.26071v1](http://arxiv.org/abs/2606.26071v1)
    - **一句话说明**：提出“模型取证”框架，通过因果干预区分导致有害行为的根本原因是故意“不对齐”还是无害的“困惑”，推动安全研究超越行为主义。

2.  **Same Evidence, Different Answer: Auditing Order Sensitivity in Multimodal Large Language Models**
    - 作者: A. Paruchuri et al.
    - 链接: [http://arxiv.org/abs/2606.26079v1](http://arxiv.org/abs/2606.26079v1)
    - **一句话说明**：引入 Facet-Probe 审计工具，系统性地揭示了多模态大模型对输入顺序极其敏感，同一组信息不同排序可能导致截然不同的答案，挑战当前评估标准。

3.  **On-Policy Self-Distillation with Sampled Demonstrations Reduces Output Diversity**
    - 作者: A. L. Nicolicioiu et al.
    - 链接: [http://arxiv.org/abs/2606.26091v1](http://arxiv.org/abs/2606.26091v1)
    - **一句话说明**：揭示了一种广泛使用的自蒸馏技术在提升单次准确率的同时，会暗中牺牲模型输出的多样性，导致pass@k表现下降，是追求高精度时的重要权衡。

##### 🤖 智能体与推理（规划、工具使用、多智能体、思维链）

4.  **Why Multi-Step Tool-Use Reinforcement Learning Collapses and How Supervisory Signals Fix It**
    - 作者: Y. Hao et al.
    - 链接: [http://arxiv.org/abs/2606.26027v1](http://arxiv.org/abs/2606.26027v1)
    - **一句话说明**：诊断出多步工具使用强化学习中的灾难性训练崩塌现象，并证明提供中间步的监督信号（如模仿学习）是稳定训练的关键。

5.  **The Unfireable Safety Kernel: Execution-Time AI Alignment for AI Agents and Other Escapable AI Systems**
    - 作者: S. Dobrin, Ł. Chmiel
    - 链接: [http://arxiv.org/abs/2606.26057v1](http://arxiv.org/abs/2606.26057v1)
    - **一句话说明**：提出“不可移除安全内核”概念，将Agent的安全控制从模型内部（如系统提示）转移到操作系统层面，实现运行时强制对齐，从根本上防止Agent解锁自身限制。

6.  **Neglected Free Lunch from Post-training: Progress Advantage for LLM Agents**
    - 作者: C. Oh et al.
    - 链接: [http://arxiv.org/abs/2606.26080v1](http://arxiv.org/abs/2606.26080v1)
    - **一句话说明**：针对Agent长程交互中过程奖励模型难以构建的问题，利用后训练阶段的学习信号差异，提出无需额外标注的“进展优势”信号，实现免费的性能提升。

##### 🔧 方法与框架（新技术、基准测试、效率优化）

7.  **RevengeBench: Reverse Engineering Code-Space Policies from Behavioral Experiments**
    - 作者: B. Rahmani et al.
    - 链接: [http://arxiv.org/abs/2606.26094v1](http://arxiv.org/abs/2606.26094v1)
    - **一句话说明**：提出一种新颖的“黑盒逆向工程”基准，通过行为轨迹实验反推Agent的内部策略，为理解不可知模型机理提供了全新工具。

8.  **The Inference-Compute Frontier and a Latency-Efficient Architecture for Limit Order Book Prediction**
    - 作者: C. E. Hedges
    - 链接: [http://arxiv.org/abs/2606.25986v1](http://arxiv.org/abs/2606.25986v1)
    - **一句话说明**：揭示了买卖盘预测任务中类似“缩放定律”的推理-计算边界，并据此设计了一种兼顾延迟和预测精度的新型神经网络架构。

9.  **Multi-Agent Goal Recognition with Team- and Goal-Conditioned Reinforcement Learning and Factorized Branch-and-Bound**
    - 作者: T. Thomas et al.
    - 链接: [http://arxiv.org/abs/2606.25978v1](http://arxiv.org/abs/2606.25978v1)
    - **一句话说明**：结合了团队/目标条件的强化学习与因子化分支定界法，高效地解决了多智能体系统中联合推断“谁在合作”及“合作目的”这一组合爆炸问题。

10. **Autodata: An agentic data scientist to create high quality synthetic data**
    - 作者: I. Kulikov et al.
    - 链接: [http://arxiv.org/abs/2606.25996v1](http://arxiv.org/abs/2606.25996v1)
    - **一句话说明**：训练一个“Agent数据科学家”来生成高质量合成数据，并通过元优化迭代，使其生成的数据能不断训练出更好的模型，实现数据质量的自我提升。

##### 📊 应用（垂直领域、多模态、代码生成）

11. **Real-Time Voice AI Hears but Does Not Listen**
    - 作者: M. Bartelds et al.
    - 链接: [http://arxiv.org/abs/2606.26083v1](http://arxiv.org/abs/2606.26083v1)
    - **一句话说明**：对四大主流实时语音AI系统进行测试，发现它们虽然能准确转写字词，但在理解语气、语速等副语言信息传达的社交含义上存在显著缺陷。

12. **AI translation of literary texts is “fine”, but readers still prefer human translations**
    - 作者: Y. Ferstler et al.
    - 链接: [http://arxiv.org/abs/2606.26040v1](http://arxiv.org/abs/2606.26040v1)
    - **一句话说明**：通过用户阅读体验的沉浸感、文学效果等主观维度评估，证实尽管AI翻译的文学文本在内容上“过得去”，但读者依然明显偏好人类翻译。

13. **A 3D-Printable Dataset for Fair Testing and Comparisons of Tactile Sensors**
    - 作者: D. R. Shepherd et al.
    - 链接: [http://arxiv.org/abs/2606.25886v1](http://arxiv.org/abs/2606.25886v1)
    - **一句话说明**：发布首个可3D打印的标准化纹理数据集，旨在解决触觉传感器领域因数据集不统一而导致的难以公平比较和复现的长期痛点。

14. **InvestPhilBench: A Multi-Layer Dynamic Benchmark for Evaluating Large Language Model Procedural Reasoning in Expert Investment Philosophy**
    - 作者: M. Chen, B. Qu
    - 链接: [http://arxiv.org/abs/2606.25984v1](http://arxiv.org/abs/2606.25984v1)
    - **一句话说明**：提出了一个多层动态评估基准，专门测试LLM是否能够准确理解和复现专业投资者的复杂决策流程和哲学，超越了简单的问答。

---

#### **研究趋势信号**

1.  **系统级安全（System-level Safety）**：AI Agent的安全控制正从模型内部（提示词、过滤器）向外迁移至操作系统与硬件层面，强调“执行时不可禁用”的安全内核，这可能会成为未来Agent部署的必需架构。
2.  **逆向工程智能体（Reverse Engineering Agents）**：通过行为数据反推内部策略（模型取证、代码空间策略逆向）成为一个新兴方向，这为理解和审计黑盒模型提供了重要的非侵入性手段。
3.  **后训练阶段红利（Post-training Dividends）**：在强化微调RLHF等后训练阶段，研究者正发现并利用更多“免费”或低成本信号（如进展优势、价值校准热身）来突破传统模仿学习的上限，尤其是在Agent和机器人领域。

---

#### **值得精读**

1.  **Model Forensics: Investigating Whether Concerning Behavior Reflects Misalignment**
    - [http://arxiv.org/abs/2606.26071v1](http://arxiv.org/abs/2606.26071v1)
    - **推荐理由**：这篇论文提出的方法论是颠覆性的。它超越了“只看行为”的安全评估范式，提供了一套因果推理工具来区分“恶意”和“误解”，对于构建真正值得信赖的AI系统至关重要。

2.  **The Unfireable Safety Kernel: Execution-Time AI Alignment for AI Agents and Other Escapable AI Systems**
    - [http://arxiv.org/abs/2606.26057v1](http://arxiv.org/abs/2606.26057v1)
    - **推荐理由**：这篇文章直面了当代AI安全领域最棘手的“越狱”悖论：当所有安全措施都运行在Agent内部时，它就可以将其关闭并“自我释放”。提出的“不可移除安全内核”方案是具有前瞻性的理论框架，可能定义未来Agent架构的设计原则。

3.  **On-Policy Self-Distillation with Sampled Demonstrations Reduces Output Diversity**
    - [http://arxiv.org/abs/2606.26091v1](http://arxiv.org/abs/2606.26091v1)
    - **推荐理由**：这篇论文的价值在于揭示了一个隐蔽的性能陷阱。自蒸馏作为一种普遍采用的技术，其副作用（多样性丧失）常被忽视。研究对于理解模型泛化能力、稳定性和生成多样性的根本性权衡具有重要指导意义。

---
*本日报由 [agents-radar](https://github.com/bcc2802/agents-radar) 自动生成。*