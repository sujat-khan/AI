# AI, LLM & RAG Exploration Repository

A comprehensive collection of Jupyter Notebooks dedicated to learning, experimenting, and implementing modern AI techniques — from LLM fundamentals to advanced Retrieval-Augmented Generation, Agentic workflows, Fine-Tuning, and LangChain mastery.

> 📄 The primary dataset used across RAG experiments is the seminal paper *"Attention Is All You Need"* ([`NIPS-2017-attention-is-all-you-need-Paper.pdf`](NIPS-2017-attention-is-all-you-need-Paper.pdf)).

---

## 📂 Repository Structure

```
AI/
├── 📓 RAG & Vector Search Notebooks
├── 📓 Agents & Advanced RAG Notebooks
├── 📓 Fine-Tuning & Evaluation Notebooks
├── 📁 LangChain/          ← Full LangChain course (13 notebooks)
├── 📁 Huggingface/        ← HuggingFace NLP Course (6 modules)
├── 📁 Hands-On-Large-Language-Models/  ← LLM internals (5 chapters)
├── 📁 lora_pirate_model/  ← LoRA fine-tune output
├── 📁 pirate_lora_adapter/ ← LoRA adapter weights
└── 📁 archived/           ← Older ML/DL notebooks
```

---

## 🧠 RAG & Vector Search

### `embedding.ipynb`
An exploration into **text embeddings** — how to convert text into high-dimensional vector representations using embedding models. A crucial prerequisite for all Vector RAG pipelines.

### `RAG.ipynb` & `RAG_pdf.ipynb` — Traditional Vector RAG
Complete pipelines implementing **Vector-based RAG** over plain text and PDF documents.
- **Workflow:** Load PDF → Chunk text → Generate embeddings → Store in `ChromaDB` → Retrieve semantic matches → Generate answers with local LLMs
- **Strengths:** Broad semantic search and similarity matching

### `Hybrid_Search_RAG.ipynb` — Hybrid Search RAG
Combines traditional keyword-based (BM25) search with semantic vector search to improve retrieval accuracy and reduce failure modes of pure embedding-based retrieval.

### `Graph_RAG.ipynb` — Vector-less Graph RAG
An alternative RAG approach that abandons embeddings in favor of a **Knowledge Graph**.
- **Workflow:** LLM extracts `(Subject, Relation, Object)` triplets → builds a directed graph with `networkx` → finds exact node matches → retrieves 1-hop subgraph
- **Strengths:** High precision, 100% explainability, excellent multi-hop reasoning

---

## 🤖 Agents & Advanced RAG

### `Function_Calling.ipynb`
Foundation for Agentic workflows. Demonstrates how to give an LLM access to external Python functions (tools), enabling it to take actions rather than just generating text.

### `ReAct_Agent.ipynb`
Builds an AI Agent from scratch using the **ReAct (Reason + Act)** pattern — a `while` loop lets the LLM think, execute a tool, observe the result, and decide when to stop.

### `Agentic_RAG_Tutorial.ipynb`
Introduces Agentic RAG routing using **LangGraph** and **LlamaIndex Workflows**. The LLM acts as a router deciding whether to query a vector database or perform a web search.

### `Self_RAG.ipynb` — Self-Reflective RAG
Advanced pipeline using **LangGraph** with a built-in "Grader" step that evaluates whether retrieved documents actually answer the question and automatically rewrites the query if retrieval was poor.

---

## 🏋️ Fine-Tuning & Evaluation

### `LoRA_PEFT_Tutorial.ipynb`
Demonstrates **Parameter-Efficient Fine-Tuning (PEFT)** using **LoRA (Low-Rank Adaptation)** and QLoRA for memory-efficient training. Fine-tunes an LLM to adopt a "sarcastic pirate" persona using `SFTTrainer`.
- Output artifacts: `lora_pirate_model/` and `pirate_lora_adapter/`

### `RAGAS_Tutorial.ipynb`
Evaluates RAG pipelines using the **RAGAS** framework — programmatically assesses retrieval accuracy, generation quality, and answer relevance using the Gemini API.

---

## 🦜🔗 LangChain — From Zero to Production (`LangChain/`)

A complete hands-on course for building LLM-powered applications — **100% free**, no OpenAI required. Uses Groq, Google Gemini, Ollama, and HuggingFace.

| # | Notebook | Topics |
|---|----------|--------|
| 00 | `00_FREE_Setup_Guide.ipynb` | Free providers, API keys, connectivity tests |
| 00 | `00_LangChain_Overview.ipynb` | Architecture, LCEL, core abstractions |
| 01 | `01_LLMs_and_ChatModels.ipynb` | ChatGroq, Gemini, Ollama, streaming, structured output |
| 02 | `02_Prompt_Templates.ipynb` | PromptTemplate, few-shot, CRAFT framework |
| 03 | `03_Output_Parsers.ipynb` | StrOutputParser, JSON, Pydantic, OutputFixingParser |
| 04 | `04_LCEL_Chains.ipynb` | Pipe operator, parallel chains, branching, fallbacks |
| 05 | `05_Memory_and_Conversations.ipynb` | Message history, SQLite persistence, multi-session chatbot |
| 06 | `06_Document_Loaders.ipynb` | PDF, CSV, web, directory loaders; text splitters |
| 07 | `07_Embeddings_and_VectorStores.ipynb` | HuggingFace embeddings, FAISS, Chroma, retrievers |
| 08 | `08_RAG_Retrieval_Augmented_Generation.ipynb` | Full RAG pipeline, citations, conversational RAG |
| 09 | `09_Tools_and_Agents.ipynb` | Custom tools, ReAct agent, tool-calling, agent memory |
| 10 | `10_LangGraph.ipynb` | StateGraph, multi-agent systems, human-in-the-loop |
| 11 | `11_LangSmith_Observability.ipynb` | Tracing, evaluation, custom evaluators, production monitoring |
| 12 | `12_Production_Best_Practices.ipynb` | Retry, caching, async, cost optimization, security |

📖 See [`LangChain/README.md`](LangChain/README.md) for full module breakdowns and the sequential learning path.

---

## 🤗 Hugging Face NLP Course (`Huggingface/`)

Hands-on exploration of the Hugging Face ecosystem, adapted from the official HuggingFace NLP Course.

| Module | Content |
|--------|---------|
| `1_Transformer_Models/` | `Transformers.ipynb` — High-level Transformer architecture overview and pipeline API |
| `2_Using_Transformers/` | `Behind the pipeline (PyTorch).ipynb`, `Models (PyTorch).ipynb`, `Tokenizers.ipynb`, attention masking, batching |
| `3_Fine_tuning/` | `Fine-tune_TrainerAPI.ipynb`, full native training loop (`section3`), learning curve analysis |
| `4_Sharing_Models/` | `sharing_models.ipynb`, using pretrained models from the Hub |
| `5_Dataset_Library/` | `dataset_lib.ipynb`, `data_preprocessing.ipynb`, `dataset_creation.ipynb`, `Semantic_Search_FAISS.ipynb`, bigdata preprocessing |
| `6_Tokenizer_Library/` | `Byte-Pair_Encoding.ipynb`, `WordPiece_Tokenization.ipynb`, `Unigram_tokenization.ipynb`, `Fast_Tokenizer.ipynb`, `Fast_Tokenizer_QA.ipynb`, `training_tokenizer.ipynb` |

---

## 📚 Hands-On LLMs (`Hands-On-Large-Language-Models/`)

Structured walkthrough of core LLM concepts with interactive notebooks:

| Chapter | Topic |
|---------|-------|
| Chapter 1 | Introduction to Language Models |
| Chapter 2 | Tokens and Token Embeddings |
| Chapter 3 | Looking Inside LLMs |
| Chapter 4 | Text Classification |
| Chapter 5 | Text Clustering and Topic Modeling |

---



## 🛠️ Technology Stack

| Category | Tools |
|----------|-------|
| **Local LLMs** | [Ollama](https://ollama.com/) — `llama3.2:3b`, `qwen2.5:7b-instruct` |
| **Cloud LLMs (Free)** | Groq (`llama-3.1-8b-instant`, `llama-3.3-70b-versatile`), Google Gemini Flash |
| **Orchestration** | `langchain`, `langgraph`, `llama-index` |
| **Hugging Face** | `transformers`, `datasets`, `evaluate`, `peft`, `trl` |
| **Vector Database** | `chromadb`, `faiss-cpu` |
| **Graph Database** | `networkx` (in-memory) |
| **Embeddings** | `sentence-transformers` (`all-MiniLM-L6-v2`) |
| **Evaluation** | `ragas` |

---

## 🚀 Getting Started

### 1. Create a virtual environment

```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate
```

### 2. Install dependencies

```bash
# Core RAG & Agents
pip install langchain langchain-community langchain-ollama langchain-groq langchain-google-genai
pip install chromadb faiss-cpu sentence-transformers pypdf networkx matplotlib jupyter
pip install langgraph llama-index-core llama-index-llms-ollama

# Fine-tuning
pip install transformers datasets evaluate peft trl

# Evaluation
pip install ragas

# LangChain course extras
pip install langchain-huggingface langchain-text-splitters python-dotenv
```

### 3. Configure API keys

Create a `.env` file in the project root (`AI/.env`):

```env
# Groq — free, fast (recommended)
GROQ_API_KEY=gsk_your_key_here

# Google Gemini — free alternative
GOOGLE_API_KEY=AIza_your_key_here

# LangSmith — optional, for tracing
LANGCHAIN_API_KEY=ls__your_key_here
LANGCHAIN_TRACING_V2=true
LANGCHAIN_PROJECT=ai-exploration
```

### 4. Install Ollama (for local notebooks)

```bash
# Download from https://ollama.com and then pull models:
ollama run llama3.2:3b
ollama run qwen2.5:7b-instruct
```

### 5. Launch Jupyter

```bash
jupyter notebook
```

---

## 📋 Recommended Learning Path

```
Embeddings → RAG → Hybrid Search → Graph RAG
                ↓
     Function Calling → ReAct Agent
                ↓
     Agentic RAG → Self RAG
                ↓
     LoRA Fine-Tuning → RAGAS Evaluation
                ↓
     LangChain/ course (00 → 12)
                ↓
     Huggingface/ NLP course (1 → 6)
                ↓
     Hands-On-Large-Language-Models/ (Ch. 1 → 5)
```
