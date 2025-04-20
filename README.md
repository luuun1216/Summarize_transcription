# Summarize_transcription
## 🔍 Project: Transcription Summarizer with LLM model

This project is a lightweight transcription summarization tool that extracts content from online speech transcripts and uses a local language model to generate structured summaries. It is designed to run in a Google Colab environment using a Hugging Face-hosted language model.

---

## 📦 Requirements
- Python 3.9+
- Google Colab or local Linux machine (Ubuntu 20/22)
- Hugging Face Transformers
- Qwen/Qwen1.5-1.8B-Chat model (public, no auth required)

---

## ⚙️ Setup Instructions

1. Clone the repo or copy the code into a Colab notebook.
2. Install dependencies in the colab:
```bash
!pip install transformers accelerate beautifulsoup4 requests
```
3. Make sure you're running in a GPU-enabled runtime (for faster inference).

---

## 🚀 How to Run

```python
# Replace with your desired transcript URL
url = "https://sayit.archive.tw/2025-02-02-bbc-%E6%8E%A1%E8%A8%AA"
text = extract_transcription_text(url)
result = summarize_transcription(text)
print(result)
```

The output is a dictionary with two keys:
```json
{
  "summary": "...",
  "conclusion": "..."
}
```
If you want to modify something, you can also check this code block.


---

## 📂 Output Format

Each summary result is saved as a `.json` file with timestamp in filename:
```json
{
  "summary": "主要內容摘要...",
  "conclusion": "總結性觀點..."
}
```

---

## 🧠 Model Info

This project uses the [Qwen/Qwen1.5-1.8B-Chat](https://huggingface.co/Qwen/Qwen1.5-1.8B-Chat) model hosted on Hugging Face. It supports multi-turn Chinese/English conversation and is suitable for summarization and instruction-following tasks.

---

## 📌 Notes/Future works
- Currently only `.speech__content p` blocks are parsed.
- Can be extended to support speaker roles or multilingual detection in the future.

---

## 📜 Reference
- Hugging face docs：https://huggingface.co/docs/transformers/main_classes/pipelines
- Hugging face tutorial：https://transformers.run/c2/2021-12-08-transformers-note-1/
- Web scrap tutorial：https://www.geeksforgeeks.org/python-web-scraping-tutorial/

## 📬 Contact
Feel free to open issues or suggestions if you want enhancements!

