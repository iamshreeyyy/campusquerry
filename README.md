# CampusQuery

> Your AI-Powered IIITDMJ Knowledge Companion

CampusQuery is a **Retrieval-Augmented Generation (RAG)** based AI assistant designed to answer questions about **Indian Institute of Information Technology, Design and Manufacturing Jabalpur (IIITDMJ)**.

It combines semantic search over a FAISS vector database with an LLM to generate answers grounded in the retrieved institutional information.

![CampusQuery Interface](screenshot.png)

## ✨ Features

* 🤖 AI-powered conversational question answering
* 📚 **RAG-based retrieval** from IIITDMJ information
* 🔎 Semantic similarity search using FAISS
* 🧠 HuggingFace `all-MiniLM-L6-v2` embeddings
* ⚡ Fast inference through Groq
* 💬 Interactive Streamlit chat interface
* 🔄 Persistent chat history during the session
* 🎯 Context-grounded responses designed to reduce hallucinations
* 🔐 API keys managed through environment variables

## 🏗️ How It Works

CampusQuery follows a simple RAG pipeline:

```text
User Question
      ↓
Query Processing
      ↓
HuggingFace Embeddings
      ↓
FAISS Vector Search
      ↓
Relevant IIITDMJ Context
      ↓
Prompt + Retrieved Context
      ↓
Groq LLM
      ↓
Grounded Response
      ↓
Streamlit Chat UI
```

The application retrieves relevant information from the vector database and provides that context to the language model before generating a response.

The system is also instructed to avoid making assumptions when the required information is not present in the retrieved context.

## 🛠️ Tech Stack

| Component              | Technology                     |
| ---------------------- | ------------------------------ |
| Frontend / UI          | Streamlit                      |
| LLM                    | `openai/gpt-oss-20b`           |
| LLM Provider           | Groq                           |
| Embeddings             | HuggingFace `all-MiniLM-L6-v2` |
| Vector Database        | FAISS                          |
| RAG Framework          | LangChain                      |
| Language               | Python                         |
| Environment Management | Environs                       |

## 📁 Project Structure

```text
CampusQuery/
├── app.py                 # Main Streamlit application
├── main.ipynb             # Notebook used during development
├── requirements.txt       # Python dependencies
├── README.md              # Project documentation
├── LICENSE               # MIT License
├── screenshot.png         # Application screenshot
├── photo/                 # Application assets
├── vectorDB/              # Local FAISS vector database
└── vectorDB1/             # Additional local vector database
```

> `.env`, `.venv/`, Python cache files, and other local/generated files are excluded from version control through `.gitignore`.

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/iamshreeyyy/campusquerry.git
cd campusquerry
```

### 2. Create a virtual environment

Linux / macOS:

```bash
python -m venv .venv
source .venv/bin/activate
```

Windows:

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

**Never commit your `.env` file or expose your API key publicly.**

### 5. Run the application

```bash
streamlit run app.py
```

The application will be available at:

```text
http://localhost:8501
```

## 🔑 Environment Variables

CampusQuery currently requires:

```text
GROQ_API_KEY
```

The key is loaded from `.env` using `environs`.

## 🧠 RAG Architecture

CampusQuery uses Retrieval-Augmented Generation instead of relying solely on the language model's internal knowledge.

The process is:

1. The user submits a question.
2. The question is converted into an embedding using `all-MiniLM-L6-v2`.
3. FAISS performs similarity search against the stored document embeddings.
4. Relevant information is retrieved from the vector database.
5. The retrieved information is inserted into the prompt.
6. The Groq-hosted LLM generates the final response.
7. The response is displayed through the Streamlit interface.

This approach helps the assistant provide answers based on the available IIITDMJ information rather than freely generating unsupported facts.

## 🎯 Example Queries

You can ask questions such as:

```text
Tell me about the CSE branch.

What programs are offered at IIITDMJ?

What information is available about the institute?

Tell me about the academic programs.
```

The quality of the response depends on the information available in the underlying knowledge base.

## 🔒 Security

API credentials should always be stored locally using environment variables.

The following files/directories should **not** be committed:

```text
.env
.venv/
__pycache__/
```

Make sure your `.gitignore` contains the appropriate entries before pushing changes to GitHub.

## 🔮 Future Improvements

Potential improvements include:

* 📌 Better document ingestion and preprocessing
* 🔄 Automatic document updates
* 🗃️ Scalable database architecture
* 🔍 Improved retrieval and reranking
* 📊 Query analytics and monitoring
* 👤 User authentication
* 💾 Persistent conversation storage
* ☁️ Cloud deployment
* ⚡ Streaming LLM responses
* 🧪 Automated evaluation of RAG responses

## 🤝 Contributing

Contributions are welcome.

1. Fork the repository.
2. Create a feature branch:

```bash
git checkout -b feature/AmazingFeature
```

3. Commit your changes:

```bash
git commit -m "Add AmazingFeature"
```

4. Push the branch:

```bash
git push origin feature/AmazingFeature
```

5. Open a Pull Request.

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Shrey K**

GitHub: [@iamshreeyyy](https://github.com/iamshreeyyy)

---

Made with ❤️ using Python, LangChain, FAISS, HuggingFace, Groq, and Streamlit.
