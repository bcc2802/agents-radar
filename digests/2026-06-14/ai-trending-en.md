# AI Open Source Trends 2026-06-14

> Sources: GitHub Trending + GitHub Search API | Generated: 2026-06-14 04:01 UTC

---

# AI Open Source Trends Report — 2026-06-14

## 1. Today's Highlights

The AI open-source ecosystem today is dominated by a massive surge in **agent skill frameworks and security tooling**, reflecting the maturation of AI coding agents into production-grade workflows. **addyosmani/agent-skills** (+1,514 today) and **obra/superpowers** (+924 today) both address the critical need for standardized, reusable skill libraries that make AI agents truly useful beyond toy demos. Meanwhile, **NVIDIA/SkillSpector** (+804 today) introduces a much-needed security scanner for agent skills, signaling that the community is moving from "can it work?" to "is it safe to run?" On the infrastructure side, **apple/container** (+1,487 today) and **LMCache** (+238 today) push the boundaries of LLM serving efficiency — Apple with lightweight Linux container runtime optimized for AI workloads on Silicon, and LMCache with breakthrough KV cache optimization that can dramatically reduce inference latency and cost.

## 2. Top Projects by Category

### 🔧 AI Infrastructure

- **[addyosmani/agent-skills](https://github.com/addyosmani/agent-skills)** ⭐0 (+1,514 today) — Production-grade engineering skills for AI coding agents, providing a curated library of battle-tested capabilities that agents can leverage in real-world development workflows.
- **[apple/container](https://github.com/apple/container)** ⭐0 (+1,487 today) — A Swift-based tool for creating and running Linux containers using lightweight VMs on Mac, optimized for Apple Silicon and ideal for running AI inference workloads locally with minimal overhead.
- **[LMCache/LMCache](https://github.com/LMCache/LMCache)** ⭐0 (+238 today) — The fastest KV cache layer for LLMs, enabling dramatic reductions in memory usage and latency for large-scale inference serving.
- **[andrewyng/aisuite](https://github.com/andrewyng/aisuite)** ⭐0 (+127 today) — A simple, unified interface to multiple Generative AI providers, making it easy to switch between or combine different LLM backends without changing code.
- **[kenn-io/agentsview](https://github.com/kenn-io/agentsview)** ⭐0 (+190 today) — Local-first session intelligence and analytics for coding agents, supporting Claude Code, Codex, and 20+ other agents — positioned as a 100x faster replacement for ccusage.

### 🤖 AI Agents / Workflows

- **[obra/superpowers](https://github.com/obra/superpowers)** ⭐0 (+924 today) — An agentic skills framework and software development methodology that "works," providing a structured approach to building and deploying AI agent capabilities in production.
- **[NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent)** ⭐192,852 — "The agent that grows with you" — a highly-starred open-source agent framework emphasizing continuous learning and adaptation.
- **[CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio)** ⭐47,288 — AI productivity studio with smart chat, autonomous agents, and 300+ assistants, providing unified access to frontier LLMs.
- **[zhayujie/CowAgent](https://github.com/zhayujie/CowAgent)** ⭐45,281 — Open-source super AI assistant and agent harness that plans tasks, runs tools and skills, and self-evolves with memory and knowledge — lightweight and extensible.
- **[Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT)** ⭐184,932 — The pioneering autonomous agent framework, continuing to evolve as the vision of accessible AI for everyone.

### 📦 AI Applications

- **[TauricResearch/TradingAgents](https://github.com/TauricResearch/TradingAgents)** ⭐85,876 — Multi-agent LLM financial trading framework that coordinates multiple specialized agents for sophisticated market analysis and trading decisions.
- **[nvidia/SkillSpector](https://github.com/NVIDIA/SkillSpector)** ⭐0 (+804 today) — Security scanner for AI agent skills, detecting vulnerabilities, malicious patterns, and security risks — a critical tool for production agent deployments.
- **[CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio)** ⭐47,288 — AI productivity studio bridging chat, autonomous agents, and 300+ assistants into a unified interface.
- **[HKUDS/nanobot](https://github.com/HKUDS/nanobot)** ⭐44,165 — Lightweight, open-source AI agent designed for tools, chats, and workflows — emphasizing minimal resource footprint.

### 🧠 LLMs / Training

- **[ollama/ollama](https://github.com/ollama/ollama)** ⭐174,077 — The leading local LLM runner, now supporting Kimi-K2.6, GLM-5.1, MiniMax, DeepSeek, and more — making frontier models accessible on consumer hardware.
- **[huggingface/transformers](https://github.com/huggingface/transformers)** ⭐161,571 — The foundational model-definition framework supporting state-of-the-art ML models across text, vision, audio, and multimodal domains.
- **[vllm-project/vllm](https://github.com/vllm-project/vllm)** ⭐82,788 — High-throughput, memory-efficient inference and serving engine for LLMs, essential for production deployments.
- **[open-compass/opencompass](https://github.com/open-compass/opencompass)** ⭐7,083 — Comprehensive LLM evaluation platform supporting 100+ datasets and major models (Llama, Mistral, GPT-4, Claude, Qwen, etc.).
- **[skyzh/tiny-llm](https://github.com/skyzh/tiny-llm)** ⭐4,274 — Educational course on LLM inference serving on Apple Silicon, building a tiny vLLM + Qwen — excellent for systems engineers learning AI infrastructure.

### 🔍 RAG / Knowledge

- **[infiniflow/ragflow](https://github.com/infiniflow/ragflow)** ⭐82,663 — Leading open-source RAG engine that fuses cutting-edge RAG with agent capabilities for a superior LLM context layer.
- **[run-llama/llama_index](https://github.com/run-llama/llama_index)** ⭐50,113 — The leading document agent and OCR platform, enabling sophisticated retrieval and document understanding.
- **[mem0ai/mem0](https://github.com/mem0ai/mem0)** ⭐58,495 — Universal memory layer for AI agents, providing persistent, self-hosted long-term memory across sessions.
- **[milvus-io/milvus](https://github.com/milvus-io/milvus)** ⭐44,764 — High-performance, cloud-native vector database for scalable ANN search, crucial for production RAG systems.
- **[qdrant/qdrant](https://github.com/qdrant/qdrant)** ⭐32,182 — High-performance vector database built in Rust, offering massive-scale search for next-generation AI applications.
- **[thedotmack/claude-mem](https://github.com/thedotmack/claude-mem)** ⭐82,155 — Persistent context across sessions for every agent, compressing session data and injecting relevant context into future agent interactions.

## 3. Trend Signal Analysis

The most explosive community attention today is centered on **agent skill ecosystems** and the **security implications of running AI agents in production**. The simultaneous rise of `addyosmani/agent-skills` (+1,514), `obra/superpowers` (+924), and NVIDIA's `SkillSpector` (+804) tells a clear story: the community has moved beyond "can I build an agent?" to "how do I build, share, and safely deploy agent capabilities at scale?" This is a maturation signal similar to what happened in the npm/PyPI ecosystems — standardized skill packages with security scanning.

A new tech stack direction appearing prominently is the **"local-first agent session intelligence"** approach exemplified by `kenn-io/agentsview` (+190 today) and `thedotmack/claude-mem` (82,155 total). Rather than relying on cloud-based telemetry, these tools capture, compress, and re-inject agent context entirely locally — a privacy-preserving alternative that also works offline. This aligns with the broader push toward self-hosted AI infrastructure.

The Apple ecosystem continues to be a focal point: `apple/container` (+1,487) brings Linux container support optimized for AI workloads on Mac Silicon, while `skyzh/tiny-llm` provides educational pathways for running LLMs on Apple hardware. This suggests Apple is investing seriously in making macOS a viable AI development and inference platform, not just a consumer OS.

Finally, the connection to recent LLM releases is visible in `ollama`'s updated model support list (Kimi-K2.6, GLM-5.1, MiniMax) — the rapid pace of open-weight model releases continues to fuel the infrastructure layer, with Ollama acting as the universal "driver" for running these models locally.

## 4. Community Hot Spots

- **Agent Skill Security (NVIDIA/SkillSpector)** — As agents increasingly execute code, scan files, and access networks, security scanning of agent skills becomes as critical as npm audit or PyPI safety checks. This is a new but rapidly essential category.
- **Agent Session Memory (thedotmack/claude-mem, kenn-io/agentsview)** — Persistent, local-first context across agent sessions is the "killer feature" that makes agents genuinely useful for ongoing development work. Watch for this becoming a standard component of agent toolchains.
- **KV Cache Optimization (LMCache)** — With LLM inference costs dominated by KV cache memory, any breakthrough that reduces cache footprint or latency (LMCache claims "fastest" status) directly impacts production deployment economics.
- **Multi-Provider Abstraction (andrewyng/aisuite)** — As the number of LLM providers explodes, unified interfaces that let developers switch between backends without code changes become infrastructure staples. Andrew Ng's involvement adds credibility.
- **Apple Silicon AI Infrastructure (apple/container, skyzh/tiny-llm)** — Running AI workloads on Mac hardware is transitioning from hobbyist to serious consideration, with Apple providing official tooling and educational resources. Developers on macOS should explore these for local development and testing.

---
*This digest is auto-generated by [agents-radar](https://github.com/bcc2802/agents-radar).*