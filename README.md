# 🔍 Source Code Analyzer

A web-based application that allows users to analyze and query source code from any public GitHub repository using natural language. Built using **LangChain**, **OpenAI**, **ChromaDB**, and **Flask**.

---

## 🚀 Features

- 🔗 Clone any public Python GitHub repository.
- 📄 Parse and split source code into manageable chunks.
- 🧠 Create vector embeddings using OpenAI.
- 🗃️ Store and retrieve vectors using ChromaDB.
- 💬 Ask natural language questions about the code and receive intelligent responses.

---

## 🛠️ Tech Stack

- Python
- Flask
- LangChain
- OpenAI API
- ChromaDB
- GitPython
- python-dotenv

---

## 📁 Project Structure

```
.
├── app.py                # Main Flask application
├── store_index.py        # Script to process repo and store vectors
├── src/
│   └── helper.py         # Helper functions (clone, load, split, embed)
├── templates/
│   └── index.html        # Web frontend (not included here)
├── repo/                 # Cloned repositories
├── db/                   # Persistent ChromaDB vector store
├── .env                  # Environment file for API key
└── README.md             # Project documentation
```

---

## ⚙️ Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/your-username/source-code-analyzer.git
cd source-code-analyzer
```

### 2. Create a virtual environment

```bash
python -m venv venv
source venv/bin/activate  # For Windows: venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Set your OpenAI API Key

Create a `.env` file in the root directory:

```
OPENAI_API_KEY=your_openai_api_key_here
```

---

## 💡 How It Works

1. User inputs a GitHub repo URL via the web interface.
2. The repo is cloned locally using `repo_ingestion()`.
3. Python files are loaded and split into chunks with `load_repo()` and `text_splitter()`.
4. Text chunks are embedded via OpenAI's embedding model.
5. Embeddings are stored in ChromaDB (`store_index.py`).
6. Users can chat with the code using LangChain's `ConversationalRetrievalChain`.

---

## 🧪 Running the Application

### Step 1: Run the vector store indexing script

```bash
python store_index.py
```

### Step 2: Launch the Flask app

```bash
python app.py
```

Navigate to `http://localhost:8080` in your browser.

---

## 📬 Endpoints

- `/` → Renders homepage with form
- `/chatbot` → Accepts GitHub repo URL and ingests repo
- `/get` → Accepts a message and returns model-generated answer

---

## 📌 Example Use Case

- Enter: `https://github.com/entbappy/End-to-end-Medical-Chatbot-Generative-AI`
- Ask: *"What does the main function do?"* or *"Which model is being used for intent classification?"*

---

## 🤖 Powered By

- [LangChain](https://www.langchain.com/)
- [OpenAI](https://openai.com/)
- [Chroma](https://www.trychroma.com/)

---

## 📄 License

MIT License. Feel free to fork, enhance, and use.