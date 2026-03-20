<div align="center">

# 🤖 Build Your Own Custom Chatbot

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python" />
  <img src="https://img.shields.io/badge/OpenAI-GPT--3.5-412991?style=for-the-badge&logo=openai" />
  <img src="https://img.shields.io/badge/RAG-Architecture-FF6B35?style=for-the-badge" />
  <img src="https://img.shields.io/badge/pandas-Data-150458?style=for-the-badge&logo=pandas" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" />
</p>

<p align="center">
  <strong>A custom domain-expert chatbot built using Retrieval-Augmented Generation (RAG) — no fine-tuning required. Answers questions from a custom knowledge base with semantic search and LLM-powered responses.</strong>
</p>

</div>

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Architecture](#-architecture)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Configuration](#configuration)
  - [Running the App](#running-the-app)
- [How It Works](#-how-it-works)
- [Customization](#-customization)
- [Project Structure](#-project-structure)
- [License](#-license)
- [Author](#-author)

---

## 🧠 Overview

**Build Your Own Custom Chatbot** demonstrates how to create a domain-specific conversational AI agent using **Retrieval-Augmented Generation (RAG)** — without any model training or fine-tuning.

The key insight: rather than retraining an LLM on new data, RAG augments the model's prompt with dynamically retrieved, relevant context at inference time. This enables the chatbot to answer questions about any custom dataset accurately and up-to-date.

This project uses a custom knowledge base (e.g., sports statistics, company FAQs, product documentation) and builds a question-answering chatbot that stays grounded in real data rather than hallucinating.

---

## ✨ Features

- 📚 **Bring-your-own dataset** — plug in any CSV/text knowledge base
- 🔍 **Semantic search retrieval** — context-aware document matching via embeddings
- 💬 **Conversational Q&A** — multi-turn dialogue with context memory
- 🛡️ **Grounded responses** — answers sourced from real data, reducing hallucination
- ⚙️ **No fine-tuning required** — fully RAG-based, fast to set up
- 📓 **Notebook-first workflow** — clean, step-by-step Jupyter implementation

---

## 🏗️ Architecture

```
User Question
     │
     ▼
┌──────────────────────────┐
│  Query Embedding          │  ◄── OpenAI text-embedding-ada-002
└────────┬─────────────────┘
         │  Query Vector
         ▼
┌──────────────────────────┐
│  Semantic Search          │  ◄── Cosine similarity over document store
│  (Document Retrieval)     │       Top-K most relevant passages
└────────┬─────────────────┘
         │  Retrieved Context
         ▼
┌──────────────────────────┐
│  Prompt Construction      │  ◄── System prompt + context + user question
└────────┬─────────────────┘
         │  Augmented Prompt
         ▼
┌──────────────────────────┐
│  LLM (GPT-3.5 / GPT-4)  │  ◄── OpenAI Chat Completions API
└────────┬─────────────────┘
         │
         ▼
    Grounded Answer
```

---

## 🛠️ Tech Stack

| Category | Technology |
|---|---|
| Language | Python 3.10+ |
| LLM | OpenAI GPT-3.5-turbo / GPT-4 |
| Embeddings | OpenAI `text-embedding-ada-002` |
| Data Handling | pandas |
| Similarity Search | NumPy (cosine similarity) |
| API Client | `openai` Python SDK |
| Notebook | Jupyter |
| Environment | python-dotenv |

---

## 🚀 Getting Started

### Prerequisites

- `Python 3.10` or higher
- OpenAI API key
- pip or conda

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/YeshwanthrajG/Build-Your-Own-Custom-Chatbot.git
cd Build-Your-Own-Custom-Chatbot

# 2. Create a virtual environment
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt
```

**Core dependencies [`requirements`](./requirements.txt):**
```
openai>=1.0.0
pandas
numpy
python-dotenv
jupyter
tiktoken
scikit-learn
```

### Configuration

Create a `.env` file in the root directory:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

### Running the App

```bash
# Launch Jupyter Notebook
jupyter notebook

# Open: custom_chatbot.ipynb
# Run all cells in order
```

---

## 🔍 How It Works

**Step 1 — Dataset Preparation**
Load your custom knowledge base into a pandas DataFrame with a `text` column. Each row represents a document, fact, or passage the chatbot can draw from.

**Step 2 — Generate Embeddings**
Each document is passed through OpenAI's embedding API to produce a dense vector representation. These embeddings capture semantic meaning beyond keywords.

**Step 3 — Semantic Retrieval**
When a user asks a question, it is also embedded. Cosine similarity is computed between the query vector and all document vectors to retrieve the top-K most relevant passages.

**Step 4 — Augmented Prompt Construction**
The retrieved passages are injected into the system prompt, giving the LLM accurate, relevant context before generating a response.

**Step 5 — Response Generation**
GPT-3.5/GPT-4 generates a grounded, coherent answer based on the augmented context — significantly reducing hallucination and keeping responses factually accurate.

---

## 🔧 Customization

To use your own dataset:

1. Replace the data source in the notebook with your CSV/text file
2. Ensure your data has a `text` column (or rename accordingly)
3. Re-run the embedding generation step
4. The chatbot is instantly knowledgeable about your domain

**Use case ideas:**
- Customer support bot (product documentation)
- Sports/news domain Q&A
- Internal company knowledge assistant
- Research paper assistant

---

## 📁 Project Structure

```
Build-Your-Own-Custom-Chatbot/
├── Custom_Chatbot_RAW.ipynb        # Main project notebook
├── data/
│   └── dataset.csv      # Custom dataset (your domain data)
├── requirements.txt            # Python dependencies
├── .env.example                # Environment variable template
└── README.md                   # Project documentation
```

---

## 📄 License

This project is licensed under the [`LICENSE`](./LICENSE).

---

## 👤 Author

[@YeshwanthrajG](https://github.com/YeshwanthrajG)
