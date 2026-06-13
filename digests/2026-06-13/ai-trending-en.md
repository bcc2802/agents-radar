# AI Open Source Trends 2026-06-13

> Sources: GitHub Trending + GitHub Search API | Generated: 2026-06-13 03:40 UTC

---

# AI Open Source Trends Report — 2026-06-13

## 1. Today's Highlights

Today's data reveals an explosive surge in **agent skill ecosystems** and **productivity-focused AI tools**. The trending list is dominated by repositories like `addyosmani/agent-skills` (+2,656 stars today) and `obra/superpowers` (+1,275), indicating a paradigm shift from building general AI agents to assembling specialized, reusable agent capabilities. Apple's release of `container` (+3,504 stars) for Linux containers on Mac silicon adds infrastructure support for AI development workflows. Meanwhile, the topic search confirms continued dominance of agent frameworks (Dify, OpenHands, AutoGPT) and vector databases (Milvus, Qdrant, LanceDB), with RAG and agent memory systems (Mem0, cognee) maturing rapidly. Notably, several repositories crossing 100k+ stars suggest AI open-source projects are reaching new adoption milestones.

## 2. Top Projects by Category

### 🔧 AI Infrastructure

- [LangChain](https://github.com/langchain-ai/langchain) — ⭐139,155 — The agent engineering platform for building LLM-powered applications with composable primitives.
- [vLLM](https://github.com/vllm-project/vllm) — ⭐82,725 — High-throughput inference and serving engine for LLMs, now essential for production deployments.
- [Ollama](https://github.com/ollama/ollama) — ⭐173,984 — Simplifies running local LLMs including Kimi, DeepSeek, Qwen, and Gemma on any hardware.
- [LMCache](https://github.com/LMCache/LMCache) — ⭐0 (+28 today) — Supercharges LLM inference with the fastest KV cache layer for reduced latency.
- [Rig](https://github.com/0xPlaygrounds/rig) — ⭐7,602 — Building modular and scalable LLM applications in Rust with type-safe primitives.

### 🤖 AI Agents / Workflows

- [Dify](https://github.com/langgenius/dify) — ⭐145,008 — Production-ready platform for developing agentic workflows with visual builder.
- [OpenHands](https://github.com/OpenHands/OpenHands) — ⭐76,677 — AI-driven development environment for code generation and software engineering.
- [AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) — ⭐184,917 — Vision for accessible AI: autonomous agents for everyone to use and build upon.
- [Flowise](https://github.com/FlowiseAI/Flowise) — ⭐53,526 — Build AI agents visually with drag-and-drop workflow designer.
- [Nanobot](https://github.com/HKUDS/nanobot) — ⭐44,124 — Lightweight open-source AI agent for tools, chats, and workflows.
- [atomic-agents](https://github.com/Eigenwise/atomic-agents) — ⭐5,978 — Building AI agents atomically with composition-first design.

### 📦 AI Applications

- [Cherry Studio](https://github.com/CherryHQ/cherry-studio) — ⭐47,251 — AI productivity studio with smart chat, autonomous agents, and 300+ assistants.
- [CowAgent](https://github.com/zhayujie/CowAgent) — ⭐45,261 — Open-source super AI assistant with planning, tools, and self-evolving memory.
- [Open WebUI](https://github.com/open-webui/open-webui) — ⭐141,290 — User-friendly AI interface supporting Ollama and OpenAI API for local-first usage.
- [PowerToys](https://github.com/microsoft/PowerToys) — ⭐0 (+103 today) — Windows utilities collection, increasingly integrating AI features for productivity.
- [ScrapeGraphAI](https://github.com/ScrapeGraphAI/Scrapegraph-ai) — ⭐27,143 — Python scraper based on AI, automating web data extraction.

### 🧠 LLMs / Training

- [Hugging Face Transformers](https://github.com/huggingface/transformers) — ⭐161,549 — State-of-the-art ML model framework supporting text, vision, audio, and multimodal models.
- [LlamaFactory](https://github.com/hiyouga/LlamaFactory) — ⭐72,122 — Unified efficient fine-tuning for 100+ LLMs and VLMs (ACL 2024).
- [OpenCompass](https://github.com/open-compass/opencompass) — ⭐7,081 — LLM evaluation platform supporting 100+ datasets across major models.
- [Tiny-LLM](https://github.com/skyzh/tiny-llm) — ⭐4,272 — Educational course for learning LLM inference serving on Apple Silicon.
- [Picollm](https://github.com/Picovoice/picollm) — ⭐312 — On-device LLM inference powered by X-Bit quantization for edge deployment.

### 🔍 RAG / Knowledge

- [RAGFlow](https://github.com/infiniflow/ragflow) — ⭐82,586 — Leading open-source RAG engine fusing retrieval-augmented generation with agent capabilities.
- [AnythingLLM](https://github.com/Mintplex-Labs/anything-llm) — ⭐61,507 — Complete local-first agent experience for owning your AI intelligence.
- [LlamaIndex](https://github.com/run-llama/llama_index) — ⭐50,099 — Document agent and OCR platform for building RAG systems.
- [Milvus](https://github.com/milvus-io/milvus) — ⭐44,753 — High-performance cloud-native vector database for scalable ANN search.
- [Qdrant](https://github.com/qdrant/qdrant) — ⭐32,066 — Massive-scale vector database optimized for next-gen AI workloads.
- [Mem0](https://github.com/mem0ai/mem0) — ⭐58,458 — Universal memory layer for AI agents enabling persistent context.
- [Cognee](https://github.com/topoteretes/cognee) — ⭐17,803 — Open-source AI memory platform with self-hosted knowledge graph for agents.
- [LEANN](https://github.com/StarTrail-org/LEANN) — ⭐11,913 — MLsys2026 paper: 97% storage savings for accurate, private RAG on personal devices.

## 3. Trend Signal Analysis

The most explosive community attention today centers on **agent skill ecosystems** — curated collections of reusable, production-grade capabilities that AI coding agents can invoke. `addyosmani/agent-skills` (+2,656 stars) and `obra/superpowers` (+1,275 stars) both propose structured methodologies for skill composition, suggesting the community is moving beyond single-agent architectures toward modular, composable agent systems. This is reinforced by `agency-agents` (+1,026 stars) and `pm-skills` (+827 stars), which package domain-specific agent abilities (from frontend development to project management) as installable plugins.

A new direction emerging today is the **convergence of agent memory and knowledge graphs**. Projects like `cognee` (17,803 stars) and `graphify` (66,341 stars) combine persistent long-term memory with knowledge graph structures, enabling agents to maintain coherent context across sessions and understand relational data. This addresses a critical bottleneck: current LLM agents suffer from context window limits and session amnesia.

The appearance of `LMCache` (today trending) signals growing emphasis on **inference optimization infrastructure** beyond traditional model serving. KV cache management is becoming a first-class concern for production deployments, alongside vLLM's continued dominance.

Apple's `container` (+3,504 stars) — while not directly AI — provides lightweight Linux VM containers on Mac silicon, directly benefiting AI developers who run model training/inference locally. This aligns with the broader trend of local-first AI development.

**Connection to recent events**: The topic search includes references to Kimi-K2.6, GLM-5.1, MiniMax, and DeepSeek in Ollama's description, indicating rapid model release cycles. The hundreds of AI-related repos with 50k+ stars suggest the open-source AI ecosystem has reached critical mass, with infrastructure projects now competing on production readiness rather than novelty.

## 4. Community Hot Spots

- **Agent Skill Marketplaces** — `addyosmani/agent-skills` and `obra/superpowers` represent a new paradigm: treat agent capabilities as installable packages. Worth watching for how skill interoperability standards evolve.
- **Agent Memory Systems** — `mem0ai/mem0` and `topoteretes/cognee` are solving context persistence. As agents become more autonomous, reliable long-term memory is the next frontier.
- **Browser Automation for AI** — `browser-use/browser-use` (98,530 stars) and `firecrawl/firecrawl` (132,025 stars) enable agents to interact with the web at scale. Critical for data collection and automated workflows.
- **Fine-Tuning Democratization** — `hiyouga/LlamaFactory` at 72,122 stars shows the hunger for accessible fine-tuning tools. Combined with `vllm-project/vllm` for serving, the full training-to-production pipeline is becoming plug-and-play.
- **Code-First Agent Development** — Repos like `OpenHands/OpenHands`, `shareAI-lab/learn-claude-code` (66,310 stars), and `Gitlawb/openclaude` (28,647 stars) emphasize CLI-first, code-centric agent workflows over GUI tools — ideal for developer adoption.

---
*This digest is auto-generated by [agents-radar](https://github.com/bcc2802/agents-radar).*