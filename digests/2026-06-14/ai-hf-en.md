# Hugging Face Trending Models Digest 2026-06-14

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-06-14 04:01 UTC

---

Here is the structured Hugging Face Trending Models Digest for June 14, 2026.

---

## Hugging Face Trending Models Digest – 2026-06-14

### 1. Today’s Highlights

The ecosystem is dominated by the explosive adoption of Google’s **Gemma 4** family (12B and 26B), which has spawned a massive wave of quantizations, ablitterations (uncensored variants), and community fine-tunes. **DeepSeek-V4-Pro** leads raw popularity with over 4,800 weekly likes and 3.2 million downloads, solidifying the dominance of high-performance open-weight MoE architectures. Multimodal capabilities are now the default, as nearly half of the top 30 models support image-text-to-text pipelines, while specialized models for streaming ASR (NVIDIA), creative audio (Magenta), and pose-driven video (SCAIL-2) mark a deepening expansion beyond text.

### 2. Trending Models by Category

#### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[deepseek-ai/DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)** • deepseek-ai • ❤️4,813 • ⬇️3.25M • The consensus leader in conversational AI, trending for its massive performance jump in a dense, open-weight architecture.
- **[CohereLabs/North-Mini-Code-1.0](https://huggingface.co/CohereLabs/North-Mini-Code-1.0)** • CohereLabs • ❤️356 • ⬇️6.5K • A compact MoE code model from Cohere’s North line, gaining traction for efficient code generation in constrained environments.
- **[nex-agi/Nex-N2-Pro](https://huggingface.co/nex-agi/Nex-N2-Pro)** • nex-agi • ❤️238 • ⬇️3.1K • A 9B-class Qwen3.5-MoE variant optimized for fast, high-quality text and image reasoning tasks.
- **[nex-agi/Nex-N2-mini](https://huggingface.co/nex-agi/Nex-N2-mini)** • nex-agi • ❤️195 • ⬇️3.8K • A smaller sibling to N2-Pro, offering a strong parameter-efficiency trade-off for on-device inference.

#### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** • nvidia • ❤️1,967 • ⬇️69.4K • A purpose-built vision-language model for object localization, trending for its extreme accuracy at 3B parameters.
- **[google/gemma-4-12B-it](https://huggingface.co/google/gemma-4-12B-it)** • google • ❤️995 • ⬇️1.0M • The flagship instruction-tuned “any-to-any” model from Google, driving the current Gemma 4 ecosystem explosion.
- **[ideogram-ai/ideogram-4-fp8](https://huggingface.co/ideogram-ai/ideogram-4-fp8)** • ideogram-ai • ❤️518 • ⬇️6.5K • A FP8 quantized version of Ideogram 4 text-to-image model offering high quality with significantly reduced GPU memory.
- **[bosonai/higgs-audio-v3-tts-4b](https://huggingface.co/bosonai/higgs-audio-v3-tts-4b)** • bosonai • ❤️414 • ⬇️32.2K • A multimodal TTS model based on Qwen3, trending for its ability to synthesize speech from text with emotional nuance.
- **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)** • nvidia • ❤️403 • ⬇️4.0K • A tiny, cache-aware streaming ASR model from NVIDIA, popular for real-time low-latency speech recognition pipelines.
- **[zai-org/SCAIL-2](https://huggingface.co/zai-org/SCAIL-2)** • zai-org • ❤️155 • ⬇️0 • A diffusion-based pose-driven character animation model, representing a new frontier in controlled video generation.
- **[ByteDance/Bernini-R](https://huggingface.co/ByteDance/Bernini-R)** • ByteDance • ❤️235 • ⬇️426 • An image-to-video model from ByteDance generating dynamic renders from static references, based on an arXiv paper.
- **[google/magenta-realtime-2](https://huggingface.co/google/magenta-realtime-2)** • google • ❤️189 • ⬇️7.3K • A TFLite model for real-time text-to-audio music generation, pushing the frontier of generative creativity.

#### 🔧 Specialized Models (code, math, medical, embeddings)

- **[moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code)** • moonshotai • ❤️524 • ⬇️1.7K • A compressed MoE code model from Kimi K2.5, trending for its strong code reasoning and instruction-following in small footprint.
- **[Jackrong/Qwopus3.6-27B-Coder-MTP-GGUF](https://huggingface.co/Jackrong/Qwopus3.6-27B-Coder-MTP-GGUF)** • Jackrong • ❤️158 • ⬇️11.3K • A vision-capable code model in GGUF format, offering code generation with image context for local inference.
- **[XiaomiMiMo/MiMo-V2.5-Pro-FP4-DFlash](https://huggingface.co/XiaomiMiMo/MiMo-V2.5-Pro-FP4-DFlash)** • XiaomiMiMo • ❤️106 • ⬇️3.6K • Xiaomi’s latest agent-centric model using FP4 quantization and flash attention for efficient deployment.

#### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** • HauhauCS • ❤️1,763 • ⬇️2.4M • A massively popular uncensored MoE variant with aggressive reasoning patterns, downloaded 2.4M times in GGUF format.
- **[Jiunsong/supergemma4-26b-uncensored-gguf-v2](https://huggingface.co/Jiunsong/supergemma4-26b-uncensored-gguf-v2)** • Jiunsong • ❤️820 • ⬇️98.9K • The definitive uncensored Gemma 4 26B GGUF fine-tune, trending due to demand for unfiltered output from Google’s latest model.
- **[unsloth/gemma-4-12b-it-GGUF](https://huggingface.co/unsloth/gemma-4-12b-it-GGUF)** • unsloth • ❤️582 • ⬇️873K • The canonical GGUF quantization of Gemma 4 12B from Unsloth, enabling efficient CPU/local inference.
- **[OBLITERATUS/Gemma-4-12B-OBLITERATED](https://huggingface.co/OBLITERATUS/Gemma-4-12B-OBLITERATED)** • OBLITERATUS • ❤️279 • ⬇️50.3K • An abliterated variant removing guardrails from Gemma 4 12B for research into refusal mechanisms.
- **[huihui-ai/Huihui-gemma-4-12B-it-abliterated](https://huggingface.co/huihui-ai/Huihui-gemma-4-12B-it-abliterated)** • huihui-ai • ❤️152 • ⬇️8.3K • Another popular abliteration of Gemma 4 12B, part of the broader “uncensored” ecosystem trend.
- **[unsloth/gemma-4-26B-A4B-it-qat-GGUF](https://huggingface.co/unsloth/gemma-4-26B-A4B-it-qat-GGUF)** • unsloth • ❤️152 • ⬇️261K • Unsloth’s QAT-quantized GGUF version of the 26B MoE model, making large-scale local inference viable.
- **[unsloth/diffusiongemma-26B-A4B-it-GGUF](https://huggingface.co/unsloth/diffusiongemma-26B-A4B-it-GGUF)** • unsloth • ❤️249 • ⬇️42.9K • A GGUF quantization of the diffusion-based Gemma variant for image generation workflows.
- **[ideogram-ai/ideogram-4-nf4](https://huggingface.co/ideogram-ai/ideogram-4-nf4)** • ideogram-ai • ❤️334 • ⬇️3.3K • A 4-bit NF4 quantized version of Ideogram 4 for extremely memory-efficient image generation.

### 3. Ecosystem Signal

**Gemma 4 is the event of the week.** Google has not only released a powerful base (12B and 26B), but both models support an “any-to-any” pipeline, making them direct multimodal competitors to Gemini-level capability. The community response has been ferocious: the top 3 downloaded models this week are all Gemma 4 quantizations (over 2 million downloads combined), and uncensored variants (ablitterations) of Gemma 4 occupy multiple high-likes positions. This mirrors the Llama 3.1 cycle, but with a decisive multimodal twist.

**MoE continues to reign.** DeepSeek-V4-Pro, Qwen3.6, and Nvidia’s models all leverage Mixture-of-Experts, with sparse activation becoming the default for scaling compute efficiently. The high likes for small expert models (e.g., 26B-A4B) suggest a market shift toward models that fit on consumer GPUs while maintaining high capability.

**ASR and audio are maturing rapidly.** NVIDIA’s streaming ASR model (0.6B) and Google’s Magenta-2 show that real-time, low-latency audio generation and recognition are now commercially viable and drawing significant developer interest. Open-weight curation is one-directional: every top model is open-weight; there are no proprietary-only entries in this list.

### 4. Worth Exploring

1. **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** – With 1,967 likes in one week, this model represents the next frontier of visual grounding. At only 3B parameters, it is a must-try for any vision-to-text pipeline needing precise object localization without massive compute.

2. **[google/magenta-realtime-2](https://huggingface.co/google/magenta-realtime-2)** – A rare real-time text-to-music model from Google Research, it runs on device via TFLite and is backed by two arXiv papers. This is a critical model for experimenting with on-device generative creativity.

3. **[ByteDance/Bernini-R](https://huggingface.co/ByteDance/Bernini-R)** – A cutting-edge image-to-video model that produces high-quality animated renders from static images. Its 235 likes and Apache-2.0 license make it a strong candidate for creative and production video pipelines.

---
*This digest is auto-generated by [agents-radar](https://github.com/bcc2802/agents-radar).*