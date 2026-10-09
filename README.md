# 📖 Project Overview

**AI Personal Tutor** is a Retrieval-Augmented Generation (RAG) study assistant that turns your own lecture notes into an interactive learning session. You upload a PDF, type a topic, and the tutor teaches you that topic **using only the content of your document**: a clear explanation, a real-world example, and a multiple-choice quiz to check your understanding.

Everything runs with open-source models served locally through Hugging Face, so no paid API is required. The app is built with Streamlit and is designed to run in a Kaggle notebook, exposed through an ngrok public URL.

---

# 🚀 [Tips Hindawi](https://www.tipshindawi.com/) Internship (August–October) 2026

> 🎓 This project was built during the [ **Tips Hindawi** ](https://www.tipshindawi.com/) **Internship (August–October) 2026**.

## 👤 Participant

| Field            | Value                                |
| ---------------- | ------------------------------------ |
| Full Name        | `<Your Full Name>`                   |
| Project Name     | AI Personal Tutor                    |
| GitHub Username  | `<your-github-username>`             |
| Internship Batch | August–October 2026                  |
| Training Program | Large Language Models (LLMs) Program |
| Organization     | [**Edrak for Ai**](https://edrak4ai.com/en)                         |

---

# ✨ Features

* 📄 **PDF study material upload**: index your lecture notes into a FAISS vector store.
* 🔍 **Semantic search with a relevance filter**: only chunks that closely match the requested topic are used; off-topic searches are rejected.
* 📘 **Structured tutorials**: each topic gets an explanation, a practical example, and a first quiz question, generated as validated JSON.
* 🧠 **Document-grounded answers**: the model is instructed to use only the retrieved context and to return a "not in document" signal otherwise.
* 📝 **Interactive quiz and scoring**: submit answers, get instant feedback with explanations, and track a running total score.
* ➕ **Generate more questions**: create new, non-repeating questions on the same topic on demand.
* 💬 **Tutor Memory Log**: a session history tab showing every topic covered, its tutorial, questions, and scores.
* 🤖 **Multiple local models**: choose between Qwen2.5 (1.5B / 7B), Mistral-7B-Instruct, and Llama-3-8B-Instruct from the sidebar.
* 🔁 **Robust output handling**: JSON extraction, Pydantic validation, answer-matching (handles "B", "B)", case differences), and automatic retries.

---

# 🛠️ Technologies Used

| Category | Tools |
| --- | --- |
| Language | Python |
| Web UI | Streamlit |
| RAG framework | LangChain (`langchain`, `langchain-community`, `langchain-huggingface`) |
| Vector store | FAISS (`faiss-cpu`) |
| Embeddings | `sentence-transformers/all-MiniLM-L6-v2` (normalized) |
| LLMs | Hugging Face Transformers: Qwen2.5-1.5B/7B-Instruct, Mistral-7B-Instruct-v0.3, Meta-Llama-3-8B-Instruct |
| PDF parsing | PyPDF |
| Data validation | Pydantic |
| Deployment | Kaggle Notebook + pyngrok |
| Deep learning | PyTorch, Accelerate |

---

# ⚙️ Installation

The project is a single notebook (`ai-personal-tutor.ipynb`) that writes and launches the Streamlit app.

1. **Open the notebook in Kaggle** and enable a **GPU accelerator** (recommended for the 7B/8B models; the 1.5B model also works on CPU).
2. **Add your ngrok token** as a Kaggle secret named `NGROK_TOKEN` (*Add-ons → Secrets*). You can get a free token from [ngrok.com](https://ngrok.com/).
3. *(Optional)* Get a Hugging Face access token if you want to use gated models such as Llama-3.
4. **Run the cells in order**:
   * **Cell 1** installs the dependencies:
     ```bash
     pip install -q streamlit pyngrok langchain langchain-community langchain-huggingface \
       sentence-transformers faiss-cpu pypdf pydantic transformers accelerate
     ```
   * **Cell 2** writes the Streamlit application to `app.py`.
   * **Cell 3** starts Streamlit and prints the public ngrok URL.

---

# 🚀 Usage

1. Open the public URL printed by the last cell (`🚀 AI Personal Tutor live at: ...`).
2. In the sidebar, choose a model (and paste a Hugging Face token if the model is gated).
3. Upload your lecture notes as a **PDF** and click **Index Document**.
4. In the **Learn & Practice** tab, enter a topic from your notes (for example, *Backpropagation*) and click **Generate Tutorial**.
5. Read the explanation and example, then answer the quiz question and click **Submit Answer**.
6. Click **➕ Generate More Questions** to keep practicing the same topic.
7. Open the **Tutor Memory Log** tab to review all topics, questions, and scores from the session.

> 💡 **Tip:** full phrases such as "how does virtualization work" usually match better than a single word. If valid topics are rejected, lower the `MIN_SIMILARITY` value in `app.py` (the default is `0.8`, the strictest setting; values around `0.4–0.5` are a good middle ground).

---

# 📸 Demo

Add your screenshots or demo video here, for example:

* Document upload and indexing
* A generated tutorial with its example
* The quiz with scoring and feedback
* The Tutor Memory Log tab
* An off-topic search being rejected (e.g., "biology" on a cloud computing PDF)

```md
![Tutorial screen](screenshots/tutorial.png)
![Quiz screen](screenshots/quiz.png)
```

---

# 📈 Results

* Built a complete end-to-end RAG tutoring application running entirely on open-source models.
* Fixed a hallucination problem where off-topic searches (such as "biology" on a cloud computing PDF) returned general-knowledge answers. The fix combines a **similarity-based relevance filter** with **grounded prompts** that tell the model to refuse when the context does not cover the topic.
* Produced reliable structured output (explanation, example, quiz) through JSON parsing, Pydantic validation, and retry logic.
* Delivered an interactive learning loop with scoring, repeated question generation, and a per-session memory log.

---

# 🔮 Future Improvements

* Support more file types (DOCX, PPTX, TXT, web pages) and multiple documents at once.
* Add hybrid search (keyword + semantic) and a re-ranking step for more precise retrieval.
* Show the source page numbers used for each explanation, to make answers verifiable.
* Add difficulty levels, different question types (true/false, short answer), and spaced repetition.
* Save progress and the memory log permanently with user accounts and a database.
* Support Arabic and other languages with a multilingual embedding model.

---

# 📚 About the Internship

This project was developed as part of the [**Tips Hindawi**](https://www.tipshindawi.com/) **Internship (August–October) 2026**, and it will be showcased on the official [Tips Hindawi](https://www.tipshindawi.com/) website.

[Tips Hindawi](https://www.tipshindawi.com/) is the internships department of [**Edrak for Ai**](https://edrak4ai.com/en), and the internship encourages participants to build real-world projects, apply practical skills, and showcase their work through GitHub.

For more information about the internship, training programs, and upcoming batches, visit the official [Tips Hindawi](https://www.tipshindawi.com/) website.

---

# 📄 License

This project is shared for educational and portfolio purposes.
