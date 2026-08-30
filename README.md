# CampusQuery

> **Your AI-Powered IIITDMJ Knowledge Companion**

CampusQuery is a **Retrieval-Augmented Generation (RAG)** based AI assistant for answering questions about **Indian Institute of Information Technology, Design and Manufacturing Jabalpur (IIITDMJ)**.

The application retrieves relevant information from a local **FAISS vector database** and provides the retrieved context to an LLM hosted through **Groq**. The interface is built with **Streamlit** and the RAG pipeline is implemented using **LangChain**.

## ✨ Features

* 🤖 AI-powered question answering about IIITDMJ
* 📚 Retrieval-Augmented Generation (RAG)
* 🔎 Semantic search using FAISS
* 🧠 `all-MiniLM-L6-v2` embeddings through HuggingFace
* ⚡ LLM inference through Groq
* 💬 Interactive Streamlit chat interface
* 🔄 Session-based conversation history
* 🎯 Responses grounded in retrieved context
* 🔐 API key loaded through environment variables
* ✍️ Typing animation for assistant responses

## 🏗️ How It Works

CampusQuery uses the following RAG pipeline:

```text
User Question
      ↓
HuggingFace Embedding Model
      ↓
FAISS Similarity Search
      ↓
Top 3 Relevant Documents
      ↓
Retrieved Context
      ↓
Prompt + Context + Question
      ↓
Groq LLM
      ↓
Generated Response
      ↓
Streamlit Chat Interface
```

The application retrieves the **top 3 relevant documents** from the FAISS vector store and includes their content in the prompt sent to the LLM.

The prompt instructs the model to answer using the retrieved context and avoid making unsupported assumptions when the required information is not available.

## 🛠️ Tech Stack

| Component              | Technology                     |
| ---------------------- | ------------------------------ |
| Language               | Python                         |
| Frontend / UI          | Streamlit                      |
| LLM                    | `openai/gpt-oss-20b`           |
| LLM Provider           | Groq                           |
| RAG Framework          | LangChain                      |
| Embeddings             | HuggingFace `all-MiniLM-L6-v2` |
| Vector Store           | FAISS                          |
| Environment Management | Environs                       |

## 📸 Interface

![CampusQuery Interface](screenshot.png)

## 📁 Project Structure

```text
CampusQuery/
├── app.py                 # Main Streamlit application
├── main.ipynb             # Development / experimentation notebook
├── requirements.txt       # Python dependencies
├── README.md              # Project documentation
├── LICENSE               # MIT License
├── screenshot.png         # Application screenshot
├── photo/                 # Application assets
├── vectorDB/              # FAISS vector store
└── .gitignore             # Git ignore rules
```

> `.env`, `.venv/`, `__pycache__/`, and other local/generated files are excluded from version control.

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/iamshreeyyy/campusquerry.git
cd campusquerry
```

### 2. Create a virtual environment

#### Linux / macOS

```bash
python -m venv .venv
source .venv/bin/activate
```

#### Windows

```bash
python -m venv .venv
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure the Groq API key

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key_here
```

**Do not commit your `.env` file or expose your API key publicly.**

### 5. Run the application

```bash
streamlit run app.py
```

The application will normally be available at:

```text
http://localhost:8501
```

## 🔑 Environment Variables

The application currently requires:

```text
GROQ_API_KEY
```

The key is loaded from `.env` using `environs`.

## 🧠 RAG Implementation

The RAG pipeline works as follows:

1. The user submits a question through the Streamlit interface.
2. The question is embedded using HuggingFace's `all-MiniLM-L6-v2` model.
3. FAISS performs a similarity search against the stored document embeddings.
4. The application retrieves the top **3** relevant documents.
5. The retrieved document content is combined into a context string.
6. The context and user's question are passed into a LangChain prompt.
7. The prompt is sent to `openai/gpt-oss-20b` through Groq.
8. The generated response is displayed in the Streamlit chat interface.
9. The conversation is stored in Streamlit session state for the current session.

## 💬 Example Queries

You can ask questions such as:

```text
Tell me about the CSE branch.

What programs are offered at IIITDMJ?

Tell me about the academic programs.

What information is available about IIITDMJ?
```

The answers depend on the information available in the underlying FAISS knowledge base.

## 🔒 Security

API credentials are loaded through environment variables rather than being hard-coded into the application.

Make sure files such as the following remain excluded from Git:

```text
.env
.venv/
__pycache__/
```

Before pushing changes, verify that your API key has not been accidentally staged:

```bash
git status
```

## 🔮 Future Improvements

Some potential improvements for the project include:

* Improved document ingestion and preprocessing
* Automatic updating of the knowledge base
* Better retrieval and document reranking
* Persistent conversation storage
* User authentication
* Query analytics and monitoring
* Automated RAG evaluation
* Cloud deployment
* Response streaming
* More scalable vector/database architecture

## 🤝 Contributing

Contributions are welcome.

1. Fork the repository.
2. Create a feature branch:

```bash
git checkout -b feature/AmazingFeature
```

3. Make your changes.
4. Commit your changes:

```bash
git commit -m "Add AmazingFeature"
```

5. Push your branch:

```bash
git push origin feature/AmazingFeature
```

6. Open a Pull Request.

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Shrey K**

GitHub: [@iamshreeyyy](https://github.com/iamshreeyyy)

---

Made with ❤️ using Python, LangChain, FAISS, HuggingFace, Groq, and Streamlit.
