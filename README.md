Fine-Tuned DistilGPT-2 (100 MB)

This repository contains a DistilGPT-2 model fine-tuned on 100 MB of text data for simple text generation and chat. It supports CPU and GPU inference and lightweight training on small datasets.

Features

Fine-tuned DistilGPT-2 (~82M parameters)

Works on Windows, CPU or GPU

100 MB training corpus for fast experimentation

Supports interactive chat and scripted generation

File Structure
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

Setup Instructions
1️⃣ macOS
Requirements

macOS 13+

Python 3.12+ (via python.org
 or Homebrew)

Steps
# Install Homebrew (if not installed)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Python & pip
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


GPU Notes:

macOS has Metal backend for PyTorch.

For small DistilGPT-2, CPU is usually sufficient.

Run inference:

python cpu.py

2️⃣ Windows
Requirements

Python 3.13+ from python.org

NVIDIA GPU + CUDA (optional)

Steps
# Open PowerShell and go to project folder
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


Run inference:

python cpu.py      # CPU
python gpu.py      # GPU

3️⃣ Linux (Ubuntu / Arch / Others)
Requirements

Python 3.12+

pip, virtualenv

Steps (Ubuntu example)
# Update system
sudo apt update && sudo apt install -y python3 python3-venv python3-pip git wget build-essential

# Go to project folder
cd ~/Projects/llm_100mb

# Create venv
python3 -m venv venv
source venv/bin/activate

# Upgrade pip
pip install --upgrade pip

# Install CPU PyTorch + Transformers
pip install torch --index-url https://download.pytorch.org/whl/cpu
pip install -r requirements.txt

# GPU (optional, adjust CUDA version)
pip install torch --index-url https://download.pytorch.org/whl/cu121


Run inference:

python cpu.py
python gpu.py

✅ Notes Across Platforms

Use virtual environments to avoid system conflicts.

DistilGPT-2 (~82M params) runs fine on CPU; GPU only accelerates inference.

cpu.py and gpu.py handle the device automatically.

For Arch Linux, system Python may be externally managed → virtualenv required.
