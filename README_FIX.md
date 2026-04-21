# Viterbox TTS - Python 3.12 Fix

## Changes

- Updated `numpy>=1.26.0` (was `<1.26.0`) for Python 3.12 compatibility
- Updated `setuptools>=68` in build-system

## Install

```bash
git clone https://github.com/YOUR_USERNAME/viterbox-tts.git
cd viterbox-tts
uv pip install -r requirements.txt
uv pip install -e .
```

## Colab Usage

```python
# Mount Google Drive
from google.colab import drive
drive.mount('/content/drive')

# Set cache to Drive
import os
os.environ['HF_HOME'] = '/content/drive/MyDrive/huggingface'
os.environ['HUGGINGFACE_HUB_CACHE'] = '/content/drive/MyDrive/huggingface'

# Install dependencies
!pip install -q uv
!uv pip install --system torch==2.6.0 torchaudio==2.6.0
!uv pip install --system -r requirements.txt

# Install viterbox
!git clone https://github.com/YOUR_USERNAME/viterbox-tts.git
%cd viterbox-tts
!uv pip install -e .

# Use
from viterbox import Viterbox
import torch

device = "cuda" if torch.cuda.is_available() else "cpu"
tts = Viterbox.from_pretrained(device)
audio = tts.generate(text="Xin chào", language="vi")
tts.save_audio(audio, "output.wav")
```
