# Awesome-Speech-Recognition-Synthesis-API

# Top Speech Recognition & Synthesis API Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Speech-to-Text, Text-to-Speech & Real-Time Voice AI Pipelines*  
**Last updated: October 2026**

This repository tracks notable **commercial speech APIs** and **open-source projects** that convert speech to text, synthesize natural-sounding audio, and orchestrate complete voice agent pipelines. These tools power transcription services, voice assistants, accessibility features, and conversational AI applications.

**Examples** include Microsoft Speech Service, Google Cloud Speech-to-Text, AWS Transcribe, Deepgram, AssemblyAI, ElevenLabs, Speechmatics, Rev.ai, PlayHT, and Whisper API (the category leaders).

**Open-source emphasis**: Speech processing is one of the strongest open-source domains. **Whisper** (MIT), **Kyutai STT/TTS**, **Kokoro**, and **Pipecat** collectively enable fully local voice pipelines with production-grade latency, while **Fish Speech**, **Chatterbox**, and **Sesame CSM** push TTS quality to commercial parity. This section is heavily expanded.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Deepgram](https://deepgram.com/)**  
  Leading speech-to-text API with **Nova-3** achieving sub-300ms streaming latency and strong accuracy across multiple languages . Offers **self-hosted deployment** for enterprise compliance, bundled voice agent stack with Flux end-of-turn detection, and transparent per-minute pricing ($0.0077/min for Nova-3 Monolingual streaming) . **The go-to STT API for production voice agents** where latency matters .

- **[AssemblyAI](https://www.assemblyai.com/)**  
  Speech AI platform with **Universal-3.5 Pro Realtime** for streaming and strong batch accuracy. Offers **self-hosted containers** (one instance handles 48 concurrent streams) for data sovereignty, GovCloud support, and documented Kubernetes/ECS deployment . **Best for regulated industries** needing on-premises STT with enterprise compliance .

- **[ElevenLabs](https://elevenlabs.io/)**  
  The **gold standard for voice quality and cloning fidelity**, with the most natural-sounding TTS voices and emotional range . Flash v2.5 delivers ~75ms inference latency for real-time applications . Pricing at $0.30/1k characters for premium tiers . **Best when voice quality is the brand** — character voices, premium consumer products, audiobooks .

- **[Microsoft Speech Service](https://azure.microsoft.com/en-us/products/ai-services/speech-to-text)**  
  Azure's enterprise speech platform with **100+ language support**, custom model training, and strong compliance credentials . STT pricing around $1/hour; TTS at $4-16/1M characters . **Best for enterprise applications** already invested in Azure infrastructure .

- **[Google Cloud Speech-to-Text](https://cloud.google.com/speech-to-text)**  
  Google's speech API supporting **125+ languages** with speaker diarization, automatic punctuation, and integration with Google Cloud services . **Best for multi-language applications** and Google Cloud-native deployments .

- **[AWS Transcribe](https://aws.amazon.com/transcribe/)**  
  AWS's speech-to-text service with streaming and batch modes, custom vocabulary, and speaker diarization. **Best for AWS-native applications** needing integrated transcription .

- **[Speechmatics](https://www.speechmatics.com/)**  
  Enterprise speech recognition with strong accuracy across accents and dialects, available as cloud API or self-hosted .

- **[Rev.ai](https://www.rev.ai/)**  
  Speech-to-text API with high accuracy and human transcription services for critical use cases .

- **[PlayHT](https://play.ht/)**  
  AI voice platform with voice cloning, real-time streaming, and conversational AI capabilities. Pricing from $31/month for 50k characters .

## Open-Source GitHub Projects

### Speech-to-Text (STT / ASR)

- **[OpenAI Whisper](https://github.com/openai/whisper)**  
  **The most widely adopted open-source ASR model**, MIT licensed with 80,000+ GitHub stars . Multilingual (~99 languages) with `large-v3` achieving ~7.4% average WER — **the accuracy reference everything else is measured against** . Weights and code are fully MIT, making it **commercially safe** . Original PyTorch implementation is slow; **large-v3-turbo** (809M params) is the practical default, running ~8× faster . **The de facto open-source STT baseline** — every pipeline either uses it or distills from it .

- **[whisper.cpp](https://github.com/ggml-org/whisper.cpp)**  
  **C/C++ port of Whisper** built on the ggml tensor library, MIT licensed . **Runs CPU-only** — no Python, no GPU required . Builds for ARM, Apple Silicon with Core ML acceleration . **The lightweight baseline for offline dictation** — powers many desktop apps .

- **[faster-whisper](https://github.com/SYSTRAN/faster-whisper)**  
  **CTranslate2-powered Whisper** that is **up to 4× faster than reference implementation** at the same accuracy, with lower memory usage . MIT licensed . **The sweet spot for Python users** wanting a drop-in library call .

- **[Kyutai STT](https://github.com/kyutai-labs/delayed-streams-modeling)**  
  **Streaming STT with semantic VAD built in** — detects end-of-turn by sentence meaning, not silence . Native French/English support with ~500ms latency after word completion . **~400 concurrent streams on an H100** — cost per call collapses with scale . Only ~2.5 GB VRAM . **Best for real-time French/English voice agents** where turn-taking detection is critical .

- **[NVIDIA Parakeet TDT](https://github.com/NVIDIA/NeMo)**  
  **State-of-the-art English ASR** — Parakeet TDT 0.6B v2 topped Open ASR Leaderboard at 6.05% average WER, beating Whisper large-v3 on English . CC-BY-4.0 licensed (commercial OK with attribution) . **v3 supports 25 European languages** including French with auto-detect . **10× faster than Whisper turbo on English** . **Best accuracy-per-watt for batch transcription** .

- **[WhisperX](https://github.com/m-bain/whisperX)**  
  **Whisper + pyannote diarization + wav2vec2 alignment** in one pipeline, BSD-2-Clause licensed . **Word-level timestamps and speaker labels** — the shortest path from audio to "who said what" . ~70× realtime batched on GPU . **Best for meeting transcripts and subtitles** .

- **[sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx)**  
  **The most "runs everywhere" option** — Apache-2.0 licensed, built on ONNX Runtime . Does **streaming and offline ASR, TTS, speaker recognition, and VAD** with no internet . Prebuilt models for dozens of languages targeting servers, desktops, mobile, and embedded devices . **Best for real-time, multilingual, fully offline recognition** .

### Text-to-Speech (TTS)

- **[Kokoro-82M](https://github.com/hexgrad/kokoro)**  
  **The practical choice for English narration on CPU** — Apache-2.0 licensed with only **82M parameters** . Runs without GPU on any device . Dropped from #1 on TTS Arena on quality but remains **the best license-clean option for English** . **Kokoro-FastAPI** (5k stars) adds weighted voice mixing for voice design . **Best for commercial-safe, lightweight TTS** .

- **[Fish Speech S2 Pro](https://github.com/fishaudio/fish-speech)**  
  **Leads TTS Arena at Elo 1128** with 5B parameters, fine-grained prosody/emotion control via 15,000+ tags, and 80+ languages . **RTF 0.195 with 100ms TTFA streaming** . **Caveat: non-commercial license** — requires paid license for commercial use . **Best when quality outranks license cleanliness** .

- **[Chatterbox (Resemble AI)](https://github.com/resemble-ai/chatterbox)**  
  **MIT-licensed voice cloning with paralinguistic tags** — laugh, sigh, etc. . **Voice clone in under 200ms** with Turbo variant . 23+ languages supported . **The best commercially-safe voice cloning option** . **Best for voice cloning where MIT licensing matters** .

- **[Sesame CSM-1B](https://github.com/SesameAILabs/csm)**  
  **Real-time conversational TTS** built on Llama + Mimi backbone, Apache-2.0 licensed . **Best for conversational voice agents** needing natural turn-taking .

- **[Kyutai TTS 1.6B](https://github.com/kyutai-labs/delayed-streams-modeling)**  
  **Delayed streams modeling** — synthesis starts while LLM is still writing . ~450-750ms TTFA, 100+ community voices . ~5.3 GB VRAM . **Pocket TTS (100M)** variant runs **real-time on CPU** with voice cloning — enables GPU-free pilots . **Best for French TTS and low-latency streaming** .

- **[F5-TTS](https://github.com/SWivid/F5-TTS)**  
  Popular voice cloning model with 14.7k stars . **Trap: code is MIT but pre-trained weights are CC-BY-NC** — commercial use requires license . **Best for non-commercial voice cloning experiments** .

- **[Orpheus-TTS](https://github.com/canopyai/Orpheus-TTS)**  
  Apache-2.0 licensed 3B TTS model with natural narration quality . **Best for commercially-safe narration** with larger model quality .

### Voice Agent Orchestration

- **[Pipecat](https://github.com/pipecat-ai/pipecat)**  
  **Open-source Python framework for voice agents** with end-to-end latency **800-950ms** across community reports . Strong adapter ecosystem for STT, LLM, and TTS providers . **Best for building custom voice pipelines** with Python/FastAPI backends .

- **[LiveKit Agents](https://github.com/livekit/agents)**  
  **Voice agent framework on LiveKit's WebRTC infrastructure** with ~750-900ms E2E latency . **The same infrastructure Future AGI's simulation SDK uses** . **Best for cloud-native voice agents** needing scalable WebRTC .

- **[Unmute (Kyutai)](https://github.com/kyutai-labs/unmute)**  
  **Reference implementation** assembling Kyutai STT → any OpenAI-compatible LLM → Kyutai TTS . **Latency < 1s (~450ms TTFA)** deployable with 16 GB VRAM total . MIT licensed . **Caveats: no function calling, no telephony** — reference architecture, not a product .

- **[Speaches](https://github.com/speaches-ai/speaches)**  
  **"Ollama for audio"** — dynamic model auto-load/unload per request . MIT licensed, portable . **OpenAI Realtime-API emulation** for third-party client compatibility . **Best for multi-engine VRAM juggling** and API compatibility .

- **[omnivoice](https://github.com/plexusone/omnivoice-core)**  
  **Go framework with unified interfaces** for STT, TTS, realtime providers, and voice agent orchestration . Includes mock providers for testing without API keys, barge-in detection, MCP server, and subtitle generation (SRT/WebVTT) . **Best for Go-based voice applications** .

### Additional Strong Open-Source Options

- **Distil-Whisper** — 6× faster than large-v3, within ~1% WER on English. English-only limit .
- **Voxtral Mini 3B** — Mistral AI's speech understanding model (transcribe + summarize + answer). Apache-2.0 .
- **Moonshine** — ~5× faster than Whisper equivalents on short clips, runs on Raspberry Pi. MIT licensed, English-only .
- **Vosk** — True streaming with partial results on weakest hardware. Apache-2.0, pre-transformer, worse WER than Whisper .
- **pyannote.audio** — De facto open-source diarization toolkit. MIT, CC-BY-4.0 pipeline .
- **S1-mini (Superwhisper)** — 484 MB, 0.6B parameter model for **cleaning raw ASR transcripts** — fixes filler words, self-corrections, formatting. Runs completely locally .
- **TTS-WebUI** — 40+-model local audio hub with per-extension venv isolation .

**Frameworks for building custom speech solutions**: Choose based on latency, licensing, and deployment. For **commercial-safe STT**, use **Whisper** (MIT weights) or **Parakeet TDT** (CC-BY-4.0 with attribution) . For **real-time French/English**, **Kyutai STT** provides semantic VAD and streaming . For **commercial-safe TTS**, **Kokoro-82M** (Apache-2.0, CPU-capable) and **Chatterbox** (MIT, voice cloning) are the license-clean picks . For **maximum quality without commercial constraints**, **Fish Speech S2 Pro** leads TTS Arena . For **full voice pipelines**, **Pipecat** + Whisper + Kokoro + any LLM delivers sub-1s latency with zero API costs . For **Go applications**, **omnivoice** provides unified provider interfaces .

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Speech APIs process sensitive audio data. Self-hosted solutions require proper security hardening and compliance with data privacy regulations (GDPR, CCPA, HIPAA). **Commercial APIs may use data for model improvement** — review terms before processing sensitive content.
- **License traps exist**: F5-TTS code is MIT but weights are CC-BY-NC . Fish Speech is non-commercial . Verify all licenses before commercial deployment.
- **Latency claims are vendor-isolated figures** — real-world deployment adds network transit and p50 variance. Test with your own audio and accents before committing .
- **Self-hosting crosses over at scale**: A $588/month GPU pays for itself at ~76,000 minutes of STT or ~7,800 minutes of voice agent usage . Below those volumes, managed platforms often win on total cost of ownership due to engineering time saved .

---

**Made for voice AI engineers, speech researchers, and developers building conversational applications.**  
Let's make speech recognition and synthesis more open, transparent, and accessible.
