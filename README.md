
# F5-TTS

**Generative AI Model to Replicate Voices**

---

## 📦 Repository and Manual

This project is hosted at [GitHub Repository](https://github.com/Jeremoot/F5-TTS).  
Please refer to the **README on GitHub** for the most up-to-date user manual and installation instructions.

👉 If you downloaded this project directly as a ZIP or via Moodle, visit the repository page for updates and clarifications.

---

## Download Checkpoints / Data

👉 Download model checkpoints and dataset here:  
https://drive.google.com/drive/folders/1ZT0oLTuWPCjDKslDX7_tg-E0izpnKZV4?usp=drive_link

Place them into the F5-TTS folder.

---

## Prerequisites

- Python 3.11
- Git
- ffmpeg
- Nvidia GPU with more than 8GB of VRAM
- **CUDA 11.8 or compatible installed (required for GPU acceleration)**

💡 If using a different CUDA version, adjust installation commands accordingly.

---

## Installation (using venv)

```bash
# Create a virtual environment (Python 3.10 or 3.11)
py -3.11 -m venv venv

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

👉 By default, `requirements.txt` assumes CUDA 11.8. If your system uses another CUDA version, you may need to reinstall PyTorch manually:

```bash
pip install torch==2.4.0 torchvision==0.19.0 torchaudio==2.4.0 --index-url https://download.pytorch.org/whl/cu118
```

Replace `cu118` with `cu117` / `cu121` if needed.

---

## User Manual: Using the Gradio Interface

This project uses the **Gradio interface** for training a text-to-speech model.

### 1️⃣ **Transcribe Data Tab**
Upload or place your `wavs` folder and `metadata.csv` inside the `{project_name}` directory.  
Select **Audio from Path** and click **Transcribe** to prepare the transcriptions.

![Transcribe Data Tab](https://i.imgur.com/wkR1Zzo.png)

### 2️⃣ **Vocab Check Tab**
Click **Check Vocab** to validate if the dataset uses any unknown tokens.

![Vocab Check Tab](https://i.imgur.com/d1aXlHu.png)

### 3️⃣ **Prepare Data Tab**
Click **Prepare** to process your dataset. This step filters out clips shorter than 1 second or longer than 25 seconds.

![Prepare Data Tab](https://i.imgur.com/1nuL40R.png)

### 4️⃣ **Train Data Tab**
Fill in the training parameters and click **Start Training**.

![Train Data Tab](https://i.imgur.com/1CNl7QM.png)

### 5️⃣ **Test Model Tab**
After training, you can load a checkpoint model, select one of the Test References or use a random sample, and generate synthesized audio.  
**Note:** You may need to adjust the **Speed** slider based on the length of the generated text.  
Shorter clips (e.g. 2–3s) perform better with a higher speed; longer clips (e.g. 10s) use lower speed.

![Test Model Tab](https://i.imgur.com/iJaeS7F.png)

---

## ✅ **Training Parameters Used with the LJSpeech Dataset**

The following parameters were used to start **training from scratch**:

```json
{
    "exp_name": "F5TTS_Base",
    "learning_rate": 1e-05,
    "batch_size_per_gpu": 3200,
    "batch_size_type": "frame",
    "max_samples": 64,
    "grad_accumulation_steps": 1,
    "max_grad_norm": 1,
    "epochs": 300,
    "num_warmup_updates": 1184,
    "save_per_updates": 200000,
    "last_per_steps": 50000,
    "finetune": false,
    "file_checkpoint_train": "",
    "tokenizer_type": "pinyin",
    "tokenizer_file": "",
    "mixed_precision": "bf16",
    "logger": "tensorboard"
}
```

Notes:
- **Training started from scratch (no preloaded checkpoint)**
- Used **bf16 mixed precision** and **TensorBoard** for logging
- Planned training for **300 epochs**, saving checkpoint every 200,000 updates

---

## License

This code is released under the MIT License. Pre-trained models may be subject to additional licensing restrictions depending on their source datasets.
