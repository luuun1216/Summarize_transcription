# 🧾 REPORT.md

## 🧪 Technical Report: Transcription Summarizer

### 🧭 Project Goal
- Summarize online transcription content from speech archives using a locally hosted LLM model. Reduce the need for manually reading lengthy transcripts by extracting a high-level summary and conclusion.

---

### 🔧 Technical Decisions

#### Model Choice
- **Qwen1.5-1.8B-Chat**: Selected for its balance between capability and resource usage. Unlike 7B models, it can run on Colab GPUs and still generate fluent summaries in Traditional Chinese.
- We initially tested `Qwen 0.5B` and `Taiyi-1.3B`, but found Qwen 1.8B gave the best fluency + feasibility.

#### Input Format
- HTML transcripts are scraped using BeautifulSoup from `.speech__content p`.
- Cleaned and truncated to ~1000 characters to stay within model context window.

#### Prompt Design
We used an instruction-style prompt to guide structured output:
```text
請你根據這段內容，簡單寫出摘要和結論。
摘要：
結論：
```

#### Output Format
- Output is parsed using string-based split on "摘要：" and "結論："
- Output is stored as `.json` file with timestamp

---

### ⚠️ Challenges & Insights
- **Model hallucination**: Smaller models like Qwen 0.5B often echo prompts or give empty outputs.
- **Prompt robustness**: Adding "請輸出內容" improves generation reliability. I try a lot of prompt, but many of them cannot get good result.
- **Selector tuning**: Parsing `.speech__content p` yields better results than `.speech .content` or `.main .content`
- **Text number choose**: I try many number for input text, 5000, 2000, 1000, 500, I find that 500 is the most stable number for model. If we use bigger number, model will out of memory sometime.

---

### ✅ Future Improvements
- Add support for action items / next steps generation
- Speaker role tagging & multi-language support
- Switch to chat-based conversation API for richer interaction

---

### 📌 Summary
- This project demonstrates how to build a functional, lightweight transcript summarizer using an open-source LLM. With proper prompt tuning and preprocessing, even 1~2B models can produce usable summaries efficiently on cloud platforms like Google Colab.
- Since this is my first time working on a project related to LLMs, I chose to use Colab and Hugging Face to help me quickly implement it, and I also spent some time learning how to use these tools. In addition to testing the LLM model, I also needed to use web scraping to extract content from the target website. Fortunately, I’ve had experience with web scraping before, so that part wasn’t a problem. In the future, I may need to gain a deeper understanding of the underlying concepts and technologies behind LLMs.
