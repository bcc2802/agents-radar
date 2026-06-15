# Hugging Face Trending Models Digest 2026-06-15

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-06-15 04:13 UTC

---

# 🤗 Hugging Face Trending Models Digest — 2026-06-15

## 1. Today's Highlights

The Hugging Face ecosystem this week is dominated by the explosive launch of **DeepSeek-V4-Pro**, which tops the charts with nearly 5,000 likes and over 3 million downloads, signaling a major leap in open-weight conversational AI. **Google's Gemma-4 family** continues to build momentum, with the 12B any-to-any model crossing 1 million downloads, while **NVIDIA's LocateAnything-3B** emerges as the sleeper hit — a compact 3B vision model with over 2,000 likes. A notable trend is the surge of **Mixture-of-Experts (MoE) architectures** from Qwen3.5/3.6 derivatives and the new DiffusionGemma line, reflecting the industry's pivot toward efficient, multimodal-capable models. Community fine-tuning remains hyperactive, particularly around uncensored and code-optimized variants of Qwen and Gemma.

## 2. Trending Models by Category

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)** — deepseek-ai | 4,836 likes | 3.07M downloads  
  The week's undisputed leader: a massive 4th-gen conversational LLM pushing open-weight boundaries with record-breaking community engagement.

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — nvidia | 2,009 likes | 75.2K downloads  
  A remarkably compact 3B image-text-to-text model that punches far above its weight class for visual grounding and localization tasks.

- **[MiniMaxAI/MiniMax-M3](https://huggingface.co/MiniMaxAI/MiniMax-M3)** — MiniMaxAI | 508 likes | 6.6K downloads  
  A fresh multimodal MoE model from MiniMax, gaining traction for its strong vision-language performance in a relatively accessible size.

- **[prefeitura-rio/Rio-3.5-Open-397B](https://huggingface.co/prefeitura-rio/Rio-3.5-Open-397B)** — prefeitura-rio | 278 likes | 112K downloads  
  A massive 397B MoE model based on Qwen3.5, notable for its open release by an institutional contributor (city of Rio de Janeiro).

- **[nex-agi/Nex-N2-Pro](https://huggingface.co/nex-agi/Nex-N2-Pro)** — nex-agi | 261 likes | 3.4K downloads  
  Qwen3.5-MoE-based chat model optimized for conversational quality, drawing attention in the emerging "Nex" family.

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[google/gemma-4-12B-it](https://huggingface.co/google/gemma-4-12B-it)** — google | 1,010 likes | 1.08M downloads  
  Google's flagship any-to-any model: a unified 12B transformer handling text, image, and video inputs/outputs — the most downloaded Gemma-4 variant.

- **[google/gemma-4-12B](https://huggingface.co/google/gemma-4-12B)** — google | 545 likes | 213K downloads  
  The base pretrained version of Gemma-4-12B, providing a foundation for fine-tuning across modalities.

- **[google/diffusiongemma-26B-A4B-it](https://huggingface.co/google/diffusiongemma-26B-A4B-it)** — google | 804 likes | 198K downloads  
  A diffusion-based multimodal model (26B total, 4B active) combining Gemma's language backbone with latent diffusion — a new architectural paradigm.

- **[ideogram-ai/ideogram-4-fp8](https://huggingface.co/ideogram-ai/ideogram-4-fp8)** — ideogram-ai | 535 likes | 8.3K downloads  
  FP8 quantized version of Ideogram-4 text-to-image model, making high-quality generation accessible on consumer hardware.

- **[bosonai/higgs-audio-v3-tts-4b](https://huggingface.co/bosonai/higgs-audio-v3-tts-4b)** — bosonai | 429 likes | 35.1K downloads  
  A 4B text-to-speech model built on Qwen3 architecture, representing growing convergence of LLM and audio generation pipelines.

- **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)** — nvidia | 412 likes | 4.5K downloads  
  A streaming ASR model with cache-aware design — tiny 0.6B footprint optimized for real-time speech recognition.

- **[ideogram-ai/ideogram-4-nf4](https://huggingface.co/ideogram-ai/ideogram-4-nf4)** — ideogram-ai | 337 likes | 3.8K downloads  
  NF4 quantized variant of Ideogram-4, offering even lower memory requirements than the FP8 version.

- **[zai-org/SCAIL-2](https://huggingface.co/zai-org/SCAIL-2)** — zai-org | 176 likes | 0 downloads  
  An image-to-video diffusion model specialized in character animation with pose-driven generation — early-stage but novel.

- **[Comfy-Org/Ideogram-4](https://huggingface.co/Comfy-Org/Ideogram-4)** — Comfy-Org | 150 likes | 0 downloads  
  ComfyUI-native packaging of Ideogram-4, optimizing the model for the popular node-based workflow tool.

### 🔧 Specialized Models (code, math, medical, embeddings)

- **[moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code)** — moonshotai | 645 likes | 15.1K downloads  
  Moonshot AI's code-specialized variant of the Kimi K2.7 model, gaining attention for compressed-tensor techniques applied to programming tasks.

- **[CohereLabs/North-Mini-Code-1.0](https://huggingface.co/CohereLabs/North-Mini-Code-1.0)** — CohereLabs | 371 likes | 9.9K downloads  
  A compact MoE code model from Cohere's North line, designed for efficient code generation in resource-constrained environments.

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — yuxinlu1 | 194 likes | 6.2K downloads  
  Community fine-tune of Gemma-4-12B for code and reasoning, blending multiple coding datasets into a GGUF package.

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — HauhauCS | 1,809 likes | 2.52M downloads  
  The most viral community model this week: an uncensored, aggressive-style Qwen3.6 MoE fine-tune (35B total, 3B active) with massive adoption.

- **[unsloth/gemma-4-12b-it-GGUF](https://huggingface.co/unsloth/gemma-4-12b-it-GGUF)** — unsloth | 599 likes | 926K downloads  
  Unsloth's GGUF quantization of Gemma-4-12B-it, enabling CPU and edge inference — a critical bridge for local deployment.

- **[DavidAU/Qwen3.6-40B-Claude-4.6-Opus-Deckard-Heretic-Uncensored-Thinking-NEO-CODE-Di-IMatrix-MAX-GGUF](https://huggingface.co/DavidAU/Qwen3.6-40B-Claude-4.6-Opus-Deckard-Heretic-Uncensored-Thinking-NEO-CODE-Di-IMatrix-MAX-GGUF)** — DavidAU | 339 likes | 376K downloads  
  An maximalist community fine-tune blending multiple uncensored and code datasets into one Qwen3.6 GGUF — trending for its ambition and name alone.

- **[unsloth/diffusiongemma-26B-A4B-it-GGUF](https://huggingface.co/unsloth/diffusiongemma-26B-A4B-it-GGUF)** — unsloth | 262 likes | 80.1K downloads  
  First GGUF quant of Google's DiffusionGemma, bringing diffusion-based multimodal to llama.cpp-compatible runtimes.

- **[Jackrong/Qwopus3.6-27B-Coder-MTP-GGUF](https://huggingface.co/Jackrong/Qwopus3.6-27B-Coder-MTP-GGUF)** — Jackrong | 185 likes | 33.7K downloads  
  Code-optimized GGUF of Qwopus3.6 with Multi-Token Prediction, appealing to developers running local coding assistants.

- **[Jackrong/Qwopus3.6-27B-v2-MTP-GGUF](https://huggingface.co/Jackrong/Qwopus3.6-27B-v2-MTP-GGUF)** — Jackrong | 304 likes | 175K downloads  
  The general-purpose sibling of the coder above; v2 shows strong community demand for Qwopus3.6 in GGUF format.

- **[OBLITERATUS/Gemma-4-12B-OBLITERATED](https://huggingface.co/OBLITERATUS/Gemma-4-12B-OBLITERATED)** — OBLITERATUS | 305 likes | 60.9K downloads  
  A notably uncensored fine-tune of Gemma-4-12B, riding the "uncensored model" trend alongside Qwen3.6 variants.

---

## 3. Ecosystem Signal

**Model Family Momentum:** The **Gemma-4** ecosystem is the week's dominant family — spanning base pretrained, instruction-tuned, diffusion-variant, and dozens of community fine-tunes, with over 2.5 million collective downloads. **Qwen3.5/3.6 MoE** models represent the second major cluster, with the Qwen architectural line powering everything from Rio's 397B behemoth to compact fine-tunes. **Ideogram-4** leads the diffusion image generation space with multiple quantization variants gaining traction.

**Open-Weight vs Proprietary:** This week marks a decisive advance for open-weight models. DeepSeek-V4-Pro's open release at 5K likes suggests the open ecosystem now competes at frontier scale. Meanwhile, Google's Gemma-4 release strategy — offering multiple sizes, base/instruct/diffusion variants, and permissive licensing — is redefining how major labs engage with open-source AI.

**Quantization & Fine-tuning Activity:** The GGUF ecosystem is exploding. Unsloth has quantized the entire Gemma-4 line and DiffusionGemma, while the "uncensored" subculture continues to generate viral downloads — HauhauCS's Qwen3.6 uncensored variant secured 2.5 million downloads in its first week. The trend toward longer model names (symptomatic of compositional fine-tuning) signals a maturation of community remixing culture, though discoverability remains a challenge. The emergence of **Multi-Token Prediction (MTP)** in Qwopus3.6 variants points to a new quantization-aware architecture optimization gaining traction in the GGUF community.

---

## 4. Worth Exploring

1. **[google/diffusiongemma-26B-A4B-it](https://huggingface.co/google/diffusiongemma-26B-A4B-it)** — This model represents a genuine architectural innovation: combining autoregressive language modeling (Gemma) with latent diffusion for multimodal understanding. At only 4B active parameters, it achieves remarkable efficiency and points to how future unified models might work. Researchers and practitioners interested in the next generation of image-text-to-text architectures should study this closely.

2. **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — With 2,009 likes and a tiny 3B parameter count, this model punches far above its weight. It demonstrates that specialized vision-language tasks (grounding, localization) can be handled by surprisingly small models, with implications for edge deployment, robotics, and real-time applications. A must-try for anyone needing visual understanding without massive compute.

3. **[zai-org/SCAIL-2](https://huggingface.co/zai-org/SCAIL-2)** — While it has zero downloads (likely very recent), this pose-driven image-to-video diffusion model for character animation represents an emerging generation of controllable video generation. For researchers tracking the video generation frontier — especially in the character animation subfield — this is an important early release to test and study.

---
*This digest is auto-generated by [agents-radar](https://github.com/bcc2802/agents-radar).*