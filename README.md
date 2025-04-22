# 🧠 SageLoRA

**SageLoRA** is a lightweight, document-aware chatbot powered by a 4-bit quantized DeepSeek-LLM-7B model, fine-tuned using LoRA on the SQuAD v1.1 dataset. It supports question-answering from uploaded documents and optionally integrates real-time Google search via SerpAPI developed for the 5-Day Intensive AI workshop with Google and Kaggle.

---

## 🚀 Features

- 🧩 Fine-tuned on SQuAD v1.1 with PEFT + LoRA
- 💾 Efficient 4-bit quantization (bitsandbytes)
- 📝 Document upload (PDF/TXT) & chunked reading
- 🌍 Optional live web search via SerpAPI
- 🔀 Smart input routing: greeting, QA, general
- 🎛️ Customizable generation (temperature, top-p, max tokens)
- 🖼️ Chat-style Gradio UI

---

## 📦 File Structure

```
SageLoRA/
│
├── train_sagelora.ipynb       # LoRA fine-tuning notebook
├── chatbot_interface.ipynb    # Gradio chatbot with document+web support
├── squad_chatbot_adapter/     # Saved model and tokenizer
├── squad_v1.1.csv             # Training dataset (converted from SQuAD JSON)
└── requirements.txt           # Python dependencies
```

---

## 🧪 Training Configuration

| Parameter        | Value                            |
| ---------------- | -------------------------------- |
| Base Model       | deepseek-ai/deepseek-llm-7b-base |
| Quantization     | 4-bit (bitsandbytes)             |
| LoRA Config      | r=8, α=16, dropout=0.05         |
| Dataset          | SQuAD v1.1                       |
| Max Token Length | 512 tokens                       |
| Epochs           | 5                                |
| Task Type        | Causal Language Modeling         |

---

## ⚙️ Installation

```bash
pip install bitsandbytes transformers accelerate peft datasets pandas fsspec==2025.3.2
```

To run the Gradio app:

```bash
pip install gradio PyPDF2 serpapi
```

---

## 💬 Usage

1. Upload a `.pdf` or `.txt` document
2. Ask a question about its content
3. (Optional) Enable **SerpAPI Search** for real-time web-enhanced answers
4. Adjust generation settings (temperature, top-p, etc.)

---

## 📉 Limitations

- No multi-turn memory across chat
- May truncate long context (limited to 512 tokens)
- Model can hallucinate if document content is vague
- LoRA adapter not inherently web-aware
- SerpAPI required for live search (needs API key)

---

## 🔮 Enhancement Roadmap

- Add memory / multi-turn context handling
- Integrate vector store for true RAG (FAISS or ChromaDB)
- Support longer context models (e.g., LongLoRA, Mistral)
- Deploy to Hugging Face Spaces
- Add voice input + TTS support

---

## 📜 License & Acknowledgements

- Model: [DeepSeek LLM 7B](https://huggingface.co/deepseek-ai/deepseek-llm-7b-base)
- Dataset: [SQuAD v1.1](https://rajpurkar.github.io/SQuAD-explorer/)
- Built with: 🤗 Transformers, PEFT, Gradio, SerpAPI
- License: Apache License 2.0
