# Fine-Tuned DistilGPT-2 (100 MB)

This repository contains a **DistilGPT-2 model fine-tuned on 100 MB of text data** for simple text generation and chat. It supports **CPU and GPU inference** and lightweight training on small datasets.

---

## Features

* Fine-tuned **DistilGPT-2 (~82M parameters)**
* Works on **macOS, Windows, and Linux**
* CPU and GPU compatible
* Supports **interactive chat** and scripted generation

---

## File Structure

```
llm_100mb/
├─ config.json
├─ generation_config.json
├─ model.safetensors
├─ tokenizer.json
├─ tokenizer_config.json
├─ vocab.json
├─ merges.txt
├─ cpu.py        # CPU inference script
├─ gpu.py        # GPU inference script
├─ requirements.txt
└─ README.md
```

---

## Setup Instructions

### 1️⃣ macOS

**Requirements:** macOS 13+, Python 3.12+

```bash
# Install Homebrew if needed
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Python
brew install python

# Navigate to project folder
cd ~/Projects/llm_100mb

# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Upgrade pip
pip install --upgrade pip

# Install CPU PyTorch + Transformers
pip install torch --index-url https://download.pytorch.org/whl/cpu
pip install -r requirements.txt
```

**Run inference:**

```bash
python cpu.py
```

> GPU on macOS uses Metal backend; CPU is usually sufficient for DistilGPT-2.

---

### 2️⃣ Windows

**Requirements:** Python 3.13+ from [python.org](https://www.python.org/downloads/windows/)

```powershell
# Open PowerShell and navigate to project folder
cd C:\path\to\llm_100mb

# Create virtual environment
python -m venv venv
.\venv\Scripts\activate

# Upgrade pip
python -m pip install --upgrade pip

# Install CPU PyTorch + Transformers
pip install torch --index-url https://download.pytorch.org/whl/cpu
pip install -r requirements.txt

# GPU (optional, replace cu121 with your CUDA version)
pip install torch --index-url https://download.pytorch.org/whl/cu121
```

**Run inference:**

```powershell
python cpu.py      # CPU
python gpu.py      # GPU
```

---

### 3️⃣ Linux (Ubuntu / Arch / Others)

**Requirements:** Python 3.12+, pip, virtualenv

```bash
# Update system and install dependencies (Ubuntu example)
sudo apt update && sudo apt install -y python3 python3-venv python3-pip git wget build-essential

# Navigate to project folder
cd ~/Projects/llm_100mb

# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Upgrade pip
pip install --upgrade pip

# Install CPU PyTorch + Transformers
pip install torch --index-url https://download.pytorch.org/whl/cpu
pip install -r requirements.txt

# GPU (optional, adjust CUDA version)
pip install torch --index-url https://download.pytorch.org/whl/cu121
```

**Run inference:**

```bash
python cpu.py
python gpu.py
```

> For Arch Linux, system Python may be externally managed — virtualenv is required.

---

## Usage

* Launch the scripts:

```
Type 'exit' to quit.

You:
```

* Type your prompt → the model generates a response.

---

## Training / Fine-Tuning (Optional)

* GPU recommended (T4 / RTX 2060+)
* Prepare ~100 MB of raw text data
* Tokenize using `AutoTokenizer`
* Fine-tune with `Trainer` from `transformers`:

```python
from transformers import AutoModelForCausalLM, Trainer, TrainingArguments

model = AutoModelForCausalLM.from_pretrained("distilgpt2")
# ... setup dataset and trainer ...
trainer.train()
```

---

## Notes

* Model size: ~82M parameters, FP32 ~350 MB
* CPU inference is slower but works fine
* GPU inference requires CUDA-compatible NVIDIA GPU
* Use a virtual environment to avoid Python conflicts

---

## License

For **research and personal projects only**.
