
# 📝 Multi-LLM Article Generator

This project provides **three separate article generators**, each powered by a different LLM:
- 🦙 **LLaMA 2 (via GGUF and llama-cpp)**
- 🧠 **Phi-3 Mini**
- ✨ **Gemini (Google Generative AI)**

Each implementation runs on **Streamlit** with a public link using **ngrok**, and allows you to enter a topic and generate a well-structured, informative article.

---

## 🚀 Features

✅ LLaMA-based article generation using `llama-cpp-python` and GGUF models  
✅ Phi-3 Mini article generation using `transformers` (GPU-enabled)  
✅ Gemini article generation using `langchain-google-genai`  
✅ Runs on Google Colab with GPU/TPU  
✅ Streamlit UI with `ngrok` public URL  
✅ Separate helper scripts (`llama_helper.py`, `phi3_helper.py`, `gemini_helper.py`)  

---

## 📂 File Structure

```
├── llama_helper.py       # Helper for LLaMA
├── phi3_helper.py        # Helper for Phi-3 Mini
├── gemini_helper.py      # Helper for Gemini API
├── main.py               # Streamlit app (switch as needed)
├── requirements.txt      # Python dependencies
```

---

## 🛠️ Installation

Run these commands in **Google Colab**.

### Common Dependencies

```bash
!pip install -q streamlit pyngrok
```

---

### 🦙 LLaMA Article Generator

📥 Install LLaMA dependencies:
```bash
!pip install -q streamlit pyngrok langchain llama-cpp-python huggingface_hub langchain-community
!pip freeze > requirements.txt
```

📄 Download GGUF Model:
```python
from huggingface_hub import hf_hub_download

model_path = hf_hub_download(
    repo_id="TheBloke/Llama-2-7B-Chat-GGUF",
    filename="llama-2-7b-chat.Q4_K_M.gguf"
)
```

🧪 Helper:
- `llama_helper.py` contains:
  - LangChain LlamaCpp
  - Prompt template & chain

🌐 Run:
```bash
streamlit run main.py
```

---

### 🧠 Phi-3 Mini Article Generator

📥 Install Phi-3 dependencies:
```bash
!pip install -q streamlit pyngrok transformers accelerate bitsandbytes langchain huggingface_hub gpt4all
!pip freeze > requirements.txt
```

🧪 Helper:
- `phi3_helper.py` contains:
  - Transformers with `microsoft/phi-3-mini-4k-instruct`
  - GPU + bfloat16 inference
  - Generates up to 500 tokens

🌐 Run:
```bash
streamlit run main.py
```

---

### ✨ Gemini Article Generator

📥 Install Gemini dependencies:
```bash
!pip install -q streamlit pyngrok langchain langchain-community google-generativeai langchain-google-genai
!pip freeze > requirements.txt
```

🔐 Gemini API Key:
- You will be prompted to enter your Google Gemini API key when running the helper generation cell.

🧪 Helper:
- `gemini_helper.py` contains:
  - LangChain ChatGoogleGenerativeAI
  - Prompt template & chain

🌐 Run:
```bash
streamlit run main.py
```

---

## 📜 Notes

- **LLaMA**
  - Runs locally with `llama-cpp-python`
  - Requires GGUF model (downloaded from HF Hub)
  - Can leverage GPU layers if available

- **Phi-3**
  - Uses `transformers`
  - Runs on GPU (`torch_dtype=bfloat16`)
  - Outputs may be longer and more creative

- **Gemini**
  - Cloud-based (requires API key)
  - Fast and generally most coherent for general topics
  - No GPU required since it’s hosted

---

## ⚖️ Evaluation

| Feature                    | Best Choice |
|----------------------------|-------------|
| Quality & Reliability      | ✨ Gemini |
| Offline / No Cloud API     | 🦙 LLaMA |
| GPU-heavy Local Use        | 🧠 Phi-3 Mini |
