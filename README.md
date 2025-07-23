# 🎙️ Colab-Local-LLM: Whisper + Ollama Local AI Pipeline

A full pipeline for **transcribing and translating speech using Whisper**, and **querying a local large language model (LLM) using Ollama**, all from **Google Colab**.

This repository demonstrates how to run **OpenAI Whisper** for audio transcription and translation, and use **Ollama** to run local LLMs like LLaMA2 or Onyx—all inside a Colab environment.

---

## 📂 Repository Contents

- Porsche+Macan+July+5+2018+(1).mp3 # Sample audio input
- Porsche+Macan+July+5+2018+(1).txt # Manual transcript (for comparison)
- Transcribe_and_Translate_with_OpenAI_Whisper.ipynb # Whisper notebook
- ollama.ipynb # Ollama LLM notebook
- README.md # This file


---

## 🚀 Features

- ✅ **Speech-to-text** transcription using OpenAI Whisper
- 🌍 **Multilingual translation**
- 🧠 **Local LLM chat** with Ollama (LLaMA2, Onyx, etc.)
- 🔄 **Colab-ready notebooks** to get started instantly
- 🔌 **No external API keys** needed for LLMs

---

## 🔧 Requirements

- Google Colab (GPU recommended for Whisper)
- Audio file (`.mp3`, `.wav`, etc.)
- Chrome (for Colab + local runtime if needed)

---

## 📝 Quick Start

### ▶️ Transcribe and Translate with Whisper

Open `Transcribe_and_Translate_with_OpenAI_Whisper.ipynb` and follow these steps:

#### 1. Install Whisper & FFmpeg

```bash
!pip install -q openai-whisper
!apt-get update && apt-get install -y ffmpeg
2. Load the Model & Transcribe

import whisper
model = whisper.load_model("llama3:latest")
result = model.transcribe("Porsche+Macan+July+5+2018+(1).mp3", task="translate")
print(result["text"])
💡 You can replace "base" with "tiny", "small", "medium", or "large" for different accuracy/speed trade-offs.

🤖 Query Local LLM with Ollama
Open ollama.ipynb and run the following steps:

1. Install Ollama CLI


!curl -fsSL https://ollama.com/install.sh | sh
🛠 If curl fails, you can try downloading from GitHub directly.

2. Pull and Run a Model
bash


!ollama pull llama3:latest
!nohup ollama serve llama3 --port 11434 &
3. Query the Local LLM via API

import requests

def query_ollama(prompt):
    response = requests.post(
        "http://localhost:11434/v1/chat/completions",
        json={
            "model": "llama2",
            "messages": [{"role": "user", "content": prompt}]
        }
    )
    return response.json()["choices"][0]["message"]["content"]

print(query_ollama("Summarize this transcript for me."))
📘 Example Workflow
Upload your .mp3 audio.

Run the Whisper notebook to generate a .txt transcript and translation.

Feed the transcript into the Ollama notebook to summarize, analyze, or chat.

Done! 🎉
---

📄 Sample Output
Transcription from Porsche+Macan+July+5+2018+(1).mp3:


"This is the audio log of July 5th, 2018, recorded during a test drive of the Porsche Macan..."
Compare with manual transcript in:
Porsche+Macan+July+5+2018+(1).txt

### ⚙️ Advanced Configuration
✅ Switch Whisper model sizes for speed/accuracy.

✅ Try different Ollama models like onix, mistral, or codellama.

✅ Add prompt engineering layers before sending to Ollama.

## 🧪 Validation Tips
Task	Validation Method
Whisper Transcription	Compare with Porsche+Macan+...txt
Translation Accuracy	Manual review / language checker tools
Ollama LLM Response	Check grammar, coherence, factuality

## 🧩 Troubleshooting
Problem	Solution
ffmpeg not installed	Run !apt-get install -y ffmpeg
Ollama port conflict	Use --port 11435 or kill old server
requests fails to connect	Restart Ollama server in Colab
Model load too slow	Use smaller models like tiny or onix

## 🛡 License
This project is licensed under the MIT License.
See the LICENSE file for details.

## 🤝 Contributing
Contributions are welcome! Please:

## Fork this repository.

Create a branch: feature/your-feature-name.

Open a Pull Request with your changes.

## 🙌 Acknowledgements
OpenAI Whisper
Ollama
Google Colab

## 📬 Contact
For feedback or questions, please open an issue or reach out via GitHub Discussions.

Enjoy building locally intelligent audio transcription pipelines!

---

Let me know if you'd like this exported as a `.md` file or if you'd like to add a `requirements.txt`, `LICENSE`, or GitHub Actions CI workflow to support it!
