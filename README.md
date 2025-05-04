
# F5-TTS

**Generative AI Model to Replicate Voices**

---

## Download Checkpoints / Data

👉 Download model checkpoints and dataset here:  
https://drive.google.com/drive/folders/1ZT0oLTuWPCjDKslDX7_tg-E0izpnKZV4?usp=drive_link

---

## Prerequisites

- Python 3.11
- Git
- ffmpeg
- Nvidia GPU with more than 8GB of VRAM

---

## Installation (using venv)

```bash
# Create a virtual environment (Python 3.10 or 3.11)
python -m venv venv

# Activate the virtual environment
# (Windows)
venv\Scripts\activate
# (Mac/Linux)
source venv/bin/activate

# Upgrade pip inside venv (recommended)
pip install --upgrade pip

# Install dependencies
pip install -r requirements.txt
```

---

## Inference

### 1. Gradio App

Supported features:

- Basic TTS with Chunk Inference
- Multi-Style / Multi-Speaker Generation
- Voice Chat

Run:

```bash
f5-tts_infer-gradio
```

Optional flags:

```bash
f5-tts_infer-gradio --port 7860 --host 0.0.0.0
f5-tts_infer-gradio --share
```

---

### 2. CLI Inference

```bash
f5-tts_infer-cli --model "F5-TTS" --ref_audio "ref_audio.wav" --ref_text "The content, subtitle or transcription of reference audio." --gen_text "Some text you want the TTS model to generate."
```

Run with default settings:

```bash
f5-tts_infer-cli
```

Run with a custom configuration:

```bash
f5-tts_infer-cli -c custom.toml
```

---

## Training

Start training via Gradio interface:

```bash
f5-tts_finetune-gradio
```

## Acknowledgements

This project builds on contributions and resources from:

- E2-TTS
- Emilia
- WenetSpeech4TTS
- lucidrains
- bfs18
- SD3
- Hugging Face diffusers
- torchdiffeq
- Vocos
- FunASR
- faster-whisper
- UniSpeech
- ctc-forced-aligner
- mrfakename
- f5-tts-mlx
- F5-TTS-ONNX
- JarodMica

---

## License

This code is released under the MIT License. Pre-trained models may be subject to additional licensing restrictions depending on their source datasets.
