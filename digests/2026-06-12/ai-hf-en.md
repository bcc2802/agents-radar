# Hugging Face Trending Models Digest 2026-06-12

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-06-12 01:24 UTC

---

Here is the structured **Hugging Face Trending Models Digest** for **2026-06-12**.

---

## 1. Today's Highlights

This week is defined by the explosive scaling of open-weight models, led by **DeepSeek-V4-Pro** which has amassed over 4 million downloads and nearly 5,000 likes, re-asserting DeepSeek’s dominance in large-scale conversational AI. **NVIDIA** and **Google** continue to battle for leadership in multimodal and enterprise-grade systems: NVIDIA's 550B-parameter Nemotron-3 Ultra (available in both BF16 and NVFP4 formats) and Google’s Gemma-4-12B family (including its "any-to-any" variants) signal a market shift toward massive, flexible architectures. The community is also highly active in quantizing these models, with Unsloth and other groups producing GGUF versions of Gemma-4 and DiffusionGemma models, while abliterated and uncensored fine-tunes (e.g., Huihui-gemma-4 and Qwen3.6-35B) remain among the most popular downloads.

---

## 2. Trending Models by Category

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[DeepSeek-V4-Pro](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)** – deepseek-ai | Likes: 4,781 | Downloads: 4,061,006  
  The latest flagship from DeepSeek, a massive conversational model that has rapidly become the most popular release on Hugging Face this week.

- **[NVIDIA-Nemotron-3-Ultra-550B-A55B-BF16](https://huggingface.co/nvidia/NVIDIA-Nemotron-3-Ultra-550B-A55B-BF16)** – nvidia | Likes: 198 | Downloads: 59,066  
  NVIDIA's premier 550B-parameter MoE model (55B active) for text generation, pushing the frontier of open-weight LLM scale.

- **[NVIDIA-Nemotron-3-Ultra-550B-A55B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3-Ultra-550B-A55B-NVFP4)** – nvidia | Likes: 168 | Downloads: 91,117  
  The 4-bit NVFP4 quantized variant of Nemotron-3 Ultra, balancing massive scale with practical memory footprint.

- **[LiquidAI/LFM2.5-8B-A1B](https://huggingface.co/LiquidAI/LFM2.5-8B-A1B)** – LiquidAI | Likes: 594 | Downloads: 142,134  
  A compact but efficient 8B MoE model (1B active) from Liquid AI, gaining traction as a lightweight yet capable alternative.

- **[CohereLabs/North-Mini-Code-1.0](https://huggingface.co/CohereLabs/North-Mini-Code-1.0)** – CohereLabs | Likes: 308 | Downloads: 1,859  
  A code-focused MoE model from Cohere, designed for code generation and conversational coding.

- **[OBLITERATUS/Gemma-4-12B-OBLITERATED](https://huggingface.co/OBLITERATUS/Gemma-4-12B-OBLITERATED)** – OBLITERATUS | Likes: 234 | Downloads: 14,838  
  An uncensored community fine-tune of Gemma-4-12B, popular for removing safety constraints.

- **[huihui-ai/Huihui-gemma-4-12B-it-abliterated](https://huggingface.co/huihui-ai/Huihui-gemma-4-12B-it-abliterated)** – huihui-ai | Likes: 143 | Downloads: 6,400  
  Another abliterated Gemma-4 variant, demonstrating strong community interest in uncensored instruction-tuned models.

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** – nvidia | Likes: 1,872 | Downloads: 131,794  
  An image-text-to-text model specialized in visual grounding and object localization, trending for its high performance on "locate anything" tasks.

- **[google/gemma-4-12B-it](https://huggingface.co/google/gemma-4-12B-it)** – google | Likes: 940 | Downloads: 675,936  
  Google's flagship "any-to-any" model, handling text, image, and mixed inputs; the most downloaded multimodal model this week.

- **[google/diffusiongemma-26B-A4B-it](https://huggingface.co/google/diffusiongemma-26B-A4B-it)** – google | Likes: 491 | Downloads: 0  
  A 26B diffusion-based multimodal model (4B active) from Google, exploring diffusion for image-text-to-text generation.

- **[ideogram-ai/ideogram-4-fp8](https://huggingface.co/ideogram-ai/ideogram-4-fp8)** – ideogram-ai | Likes: 485 | Downloads: 7,170  
  Ideogram's latest text-to-image model in FP8 precision, pushing efficient image generation.

- **[ideogram-ai/ideogram-4-nf4](https://huggingface.co/ideogram-ai/ideogram-4-nf4)** – ideogram-ai | Likes: 315 | Downloads: 6,124  
  The NF4 quantized variant of Ideogram-4, offering further compression for image generation.

- **[stepfun-ai/Step-3.7-Flash](https://huggingface.co/stepfun-ai/Step-3.7-Flash)** – stepfun-ai | Likes: 368 | Downloads: 50,187  
  A vision-language model from Stepfun, combining image understanding with text generation in a flash inference format.

- **[ByteDance/Bernini-R](https://huggingface.co/ByteDance/Bernini-R)** – ByteDance | Likes: 222 | Downloads: 305  
  A novel image-text-to-video model from ByteDance, enabling video generation from mixed image and text inputs.

- **[zai-org/SCAIL-2](https://huggingface.co/zai-org/SCAIL-2)** – zai-org | Likes: 116 | Downloads: 0  
  An image-to-video model specialized in character animation and pose-driven video generation.

- **[google/magenta-realtime-2](https://huggingface.co/google/magenta-realtime-2)** – google | Likes: 178 | Downloads: 19,806  
  A real-time text-to-audio model from Google's Magenta team, supporting low-latency music and sound generation.

- **[bosonai/higgs-audio-v3-tts-4b](https://huggingface.co/bosonai/higgs-audio-v3-tts-4b)** – bosonai | Likes: 355 | Downloads: 19,948  
  A 4B text-to-speech model based on Qwen3, optimized for high-quality audio synthesis.

- **[MisoLabs/MisoTTS](https://huggingface.co/MisoLabs/MisoTTS)** – MisoLabs | Likes: 194 | Downloads: 0  
  A lightweight TTS model with a focus on speech synthesis quality and voice variety.

- **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)** – nvidia | Likes: 372 | Downloads: 4,965  
  A cache-aware streaming ASR model from NVIDIA, designed for low-latency speech recognition.

### 🔧 Specialized Models (code, math, medical, embeddings)

- **[sapientinc/HRM-Text-1B](https://huggingface.co/sapientinc/HRM-Text-1B)** – sapientinc | Likes: 749 | Downloads: 134,752  
  A 1B text generation model specialized in Human Resource Management (HRM) tasks, gaining traction for enterprise HR text generation.

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** – HauhauCS | Likes: 1,676 | Downloads: 3,057,541  
  The most downloaded model this week (3M+), an uncensored, aggressive fine-tune of Qwen3.6 MoE with vision capabilities.

- **[unsloth/gemma-4-12b-it-GGUF](https://huggingface.co/unsloth/gemma-4-12b-it-GGUF)** – unsloth | Likes: 561 | Downloads: 711,706  
  Unsloth's GGUF quant of Gemma-4-12B-it, making it accessible for CPU and edge inference.

- **[unsloth/gemma-4-12B-it-qat-GGUF](https://huggingface.co/unsloth/gemma-4-12B-it-qat-GGUF)** – unsloth | Likes: 200 | Downloads: 148,252  
  A QAT (quantization-aware training) version of Gemma-4-12B-it in GGUF format, for higher quality compression.

- **[google/gemma-4-12B-it-qat-q4_0-gguf](https://huggingface.co/google/gemma-4-12B-it-qat-q4_0-gguf)** – google | Likes: 129 | Downloads: 96,749  
  Official Google QAT GGUF variant, quantized to Q4_0 for broad deployment.

- **[unsloth/gemma-4-26B-A4B-it-qat-GGUF](https://huggingface.co/unsloth/gemma-4-26B-A4B-it-qat-GGUF)** – unsloth | Likes: 142 | Downloads: 129,110  
  Quantized version of the larger 26B DiffusionGemma model, enabling large-scale multimodal inference on consumer hardware.

- **[unsloth/diffusiongemma-26B-A4B-it-GGUF](https://huggingface.co/unsloth/diffusiongemma-26B-A4B-it-GGUF)** – unsloth | Likes: 180 | Downloads: 0  
  GGUF version of Google's DiffusionGemma, though currently with zero downloads, suggesting it was just released.

- **[Comfy-Org/Ideogram-4](https://huggingface.co/Comfy-Org/Ideogram-4)** – Comfy-Org | Likes: 135 | Downloads: 0  
  ComfyUI integration package for Ideogram-4, designed for node-based image generation workflows.

- **[nex-agi/Nex-N2-Pro](https://huggingface.co/nex-agi/Nex-N2-Pro)** – nex-agi | Likes: 206 | Downloads: 1,185  
  A community fine-tune based on Qwen3.5 MoE, optimized for text generation with vision capabilities.

- **[nex-agi/Nex-N2-mini](https://huggingface.co/nex-agi/Nex-N2-mini)** – nex-agi | Likes: 163 | Downloads: 1,222  
  Smaller variant of Nex-N2, targeting edge deployment for image-text-to-text tasks.

---

## 3. Ecosystem Signal

The ecosystem is witnessing a **tectonic shift toward MoE (Mixture-of-Experts) architectures** across all scales. Major players like NVIDIA (Nemotron-3 Ultra at 550B), Google (Gemma-4 at 12B & DiffusionGemma at 26B), and DeepSeek (V4 Pro) are all leveraging MoE to maximize capability per parameter. **Open-weight competition is intensifying**, with DeepSeek leading the pack in both downloads and likes, followed closely by Google's Gemma-4 family. The community is heavily focused on **quantization and accessibility**: Unsloth and Google are shipping multiple GGUF/QAT formats (FP8, NF4, Q4_0, NVFP4) for nearly every major release, enabling deployment on consumer and edge hardware. **Uncensored and abliterated fine-tunes remain a strong trend**, as evidenced by the Qwen3.6-35B and Gemma-4 abliterated variants, suggesting ongoing demand for models without safety alignment. Finally, **multimodality is now the norm** — most top models support image-text-to-text or any-to-any pipelines, and specialized generation models (text-to-image, text-to-video, TTS, ASR) are diversifying rapidly.

---

## 4. Worth Exploring

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** – With nearly 1,900 likes and strong download numbers, this model is a standout for visual grounding tasks. Its 3B parameter size makes it practical for deployment, and NVIDIA’s backing suggests enterprise-quality performance.

- **[unsloth/gemma-4-12b-it-GGUF](https://huggingface.co/unsloth/gemma-4-12b-it-GGUF)** – As the most downloaded Gemma-4 variant (711k downloads), this GGUF quantization by Unsloth is the definitive way to run Gemma-4 on consumer hardware. It’s the perfect entry point for experimenting with Google’s state-of-the-art multimodal model.

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** – With over 3 million downloads, this model represents the community’s overwhelming appetite for uncensored, MoE-based vision-language models. It’s a must-study for anyone tracking fine-tuning culture and the demand for unaligned models.

---
*This digest is auto-generated by [agents-radar](https://github.com/bcc2802/agents-radar).*