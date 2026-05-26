# 🦜🔗 LangChain Mastery — From Zero to Production

> A complete, hands-on course for building LLM-powered applications with LangChain — **100% free**, no OpenAI required.

---

## 📖 About This Course

This course takes you from the fundamentals of LangChain all the way to building production-ready AI applications. Every module is a self-contained Jupyter notebook packed with working code examples, clear explanations, and real-world patterns.

**You don't need an OpenAI API key.** This course is built entirely on free providers:
- 🚀 **[Groq](https://console.groq.com)** — Free API for Llama 3 & Mixtral (14,400 req/day)
- 🔵 **[Google Gemini](https://aistudio.google.com)** — Free Gemini 1.5 Flash tier
- 🦙 **[Ollama](https://ollama.com/download)** — 100% local, no API key, no cost
- 🤗 **HuggingFace** — Free local embeddings (no API key needed)

---

## 🚀 Quick Start

### 1. Clone & Set Up Environment

```bash
# Install dependencies
pip install langchain langchain-core langchain-community langchain-groq
pip install langchain-google-genai langchain-ollama langchain-huggingface
pip install sentence-transformers faiss-cpu chromadb langchain-text-splitters
pip install python-dotenv
```

### 2. Configure Your API Key

Create a `.env` file in the **parent directory** (`AI/.env`):

```env
# Groq — Recommended (free, fast)
GROQ_API_KEY=gsk_your_groq_key_here

# Google Gemini — Optional free alternative
GOOGLE_API_KEY=AIza_your_google_key_here

# LangSmith — Optional, for tracing & debugging
LANGCHAIN_API_KEY=ls__your_key_here
LANGCHAIN_TRACING_V2=true
LANGCHAIN_PROJECT=langchain-mastery
```

> **Get your free Groq key:** Go to [console.groq.com](https://console.groq.com) → Sign up → API Keys → Create new key.

### 3. Standard Setup Cell (Used in Every Notebook)

```python
from langchain_groq import ChatGroq
from langchain_huggingface import HuggingFaceEmbeddings

# Fast, free LLM for most tasks
llm = ChatGroq(model="llama-3.1-8b-instant", temperature=0.3)

# Higher quality when needed
llm_smart = ChatGroq(model="llama-3.3-70b-versatile", temperature=0)

# Free local embeddings — no API key required
embeddings = HuggingFaceEmbeddings(model_name="sentence-transformers/all-MiniLM-L6-v2")
```

---

## 📚 Course Curriculum

| # | Notebook | Topics Covered |
|---|----------|---------------|
| 00 | [🆓 Free Setup Guide](00_FREE_Setup_Guide.ipynb) | API keys, free providers, installation, connectivity tests |
| 00 | [🦜🔗 LangChain Overview](00_LangChain_Overview.ipynb) | Architecture, LCEL, core abstractions, course roadmap |
| 01 | [🤖 LLMs & Chat Models](01_LLMs_and_ChatModels.ipynb) | ChatGroq, Gemini, Ollama, streaming, batch, structured output |
| 02 | [📝 Prompt Templates](02_Prompt_Templates.ipynb) | PromptTemplate, ChatPromptTemplate, few-shot, partial variables |
| 03 | [🔄 Output Parsers](03_Output_Parsers.ipynb) | StrOutputParser, JSON, Pydantic, custom parsers |
| 04 | [⛓️ LCEL Chains](04_LCEL_Chains.ipynb) | Pipe operator, branching, parallel chains, fallbacks |
| 05 | [🧠 Memory & Conversations](05_Memory_and_Conversations.ipynb) | Message history, RunnableWithMessageHistory, SQLite persistence |
| 06 | [📄 Document Loaders](06_Document_Loaders.ipynb) | Text, CSV, PDF, web, directory loaders; text splitters |
| 07 | [🔢 Embeddings & Vector Stores](07_Embeddings_and_VectorStores.ipynb) | HuggingFace embeddings, FAISS, Chroma, retrievers |
| 08 | [🔍 RAG](08_RAG_Retrieval_Augmented_Generation.ipynb) | Simple RAG, citations, advanced techniques, conversational RAG |
| 09 | [🛠️ Tools & Agents](09_Tools_and_Agents.ipynb) | Custom tools, built-ins, ReAct agent, tool-calling, agent memory |
| 10 | [🕸️ LangGraph](10_LangGraph.ipynb) | State machines, multi-agent systems, human-in-the-loop |
| 11 | [🔭 LangSmith](11_LangSmith_Observability.ipynb) | Tracing, evaluation, custom evaluators, production monitoring |
| 12 | [🏭 Production Best Practices](12_Production_Best_Practices.ipynb) | Error handling, caching, async, cost optimization, security |

---

## 📋 Module Breakdown

### 📦 Module 00 — Setup & Overview
**Files:** `00_FREE_Setup_Guide.ipynb`, `00_LangChain_Overview.ipynb`

Get your environment running with free LLM providers. Understand the full LangChain architecture — what Runnables, chains, and LCEL are, and how all the pieces fit together.

**Key topics:** Free provider comparison table · Groq, Gemini, Ollama setup · HuggingFace embeddings · LCEL introduction

---

### 🤖 Module 01 — LLMs & Chat Models
**File:** `01_LLMs_and_ChatModels.ipynb`

Learn the four invocation methods (`invoke`, `stream`, `batch`, `async`) across all free providers, and use structured outputs with open-source models.

**Key topics:** `ChatGroq` · `ChatGoogleGenerativeAI` · `ChatOllama` · streaming · `with_structured_output()` · model selection guide

---

### 📝 Module 02 — Prompt Templates
**File:** `02_Prompt_Templates.ipynb`

Master reusable, parameterized prompts. Go from basic string templates to sophisticated few-shot prompting and the CRAFT framework for prompt engineering.

**Key topics:** `PromptTemplate` · `ChatPromptTemplate` · `MessagesPlaceholder` · `FewShotPromptTemplate` · partial variables · chain-of-thought prompting · CRAFT framework

---

### 🔄 Module 03 — Output Parsers
**File:** `03_Output_Parsers.ipynb`

Transform raw LLM responses into structured, usable data. Parse JSON, lists, Pydantic models, and implement robust error recovery.

**Key topics:** `StrOutputParser` · `JsonOutputParser` · `PydanticOutputParser` · `CommaSeparatedListOutputParser` · `OutputFixingParser` · streaming parsers

---

### ⛓️ Module 04 — LCEL Chains
**File:** `04_LCEL_Chains.ipynb`

Deep-dive into LangChain Expression Language. Build complex pipelines with branching, parallel execution, and fallback chains.

**Key topics:** Pipe operator `|` · `RunnableParallel` · `RunnableBranch` · `RunnableLambda` · `itemgetter` · `RunnablePassthrough` · fallbacks · debugging chains

---

### 🧠 Module 05 — Memory & Conversations
**File:** `05_Memory_and_Conversations.ipynb`

Build chatbots that remember. Learn the modern LangChain v0.3 memory API, manage long conversation histories, and persist state across sessions.

**Key topics:** `ChatMessageHistory` · `RunnableWithMessageHistory` · token trimming · SQLite persistence · multi-session chatbot patterns

---

### 📄 Module 06 — Document Loaders & Text Splitters
**File:** `06_Document_Loaders.ipynb`

Ingest any data format into LangChain. Learn to load, clean, and chunk text for downstream retrieval pipelines.

**Key topics:** `TextLoader` · `CSVLoader` · `PyPDFLoader` · `WebBaseLoader` · `DirectoryLoader` · `RecursiveCharacterTextSplitter` · `TokenTextSplitter` · chunking strategies

---

### 🔢 Module 07 — Embeddings & Vector Stores
**File:** `07_Embeddings_and_VectorStores.ipynb`

Turn text into vectors and search them efficiently. Learn both in-memory and persistent vector stores, free of cost.

**Key topics:** `HuggingFaceEmbeddings` · `FAISS` · `Chroma` · similarity vs. MMR search · vector store retrievers · embedding cost trade-offs

---

### 🔍 Module 08 — Retrieval-Augmented Generation (RAG)
**File:** `08_RAG_Retrieval_Augmented_Generation.ipynb`

Build the full RAG pipeline end-to-end. Add source citations, advanced retrieval, and make your RAG system conversational.

**Key topics:** Simple RAG pipeline · source citations · `MultiQueryRetriever` · contextual compression · `ParentDocumentRetriever` · conversational RAG with memory

---

### 🛠️ Module 09 — Tools & Agents
**File:** `09_Tools_and_Agents.ipynb`

Give your LLM the ability to take actions. Build ReAct agents, tool-calling agents, and agents that maintain memory across turns.

**Key topics:** `@tool` decorator · Pydantic tool schemas · built-in tools · `create_react_agent` · tool-calling agent loop · agent + memory integration · custom agent logic

---

### 🕸️ Module 10 — LangGraph
**File:** `10_LangGraph.ipynb`

Go beyond simple chains with stateful, graph-based workflows. Build multi-agent systems and add human oversight with interrupt/resume patterns.

**Key topics:** `StateGraph` · typed state · conditional edges · multi-agent orchestration · `interrupt()` for human-in-the-loop · graph visualization

---

### 🔭 Module 11 — LangSmith Observability
**File:** `11_LangSmith_Observability.ipynb`

Debug, evaluate, and monitor your LLM apps in production. Use the `@traceable` decorator and build automated evaluation pipelines.

**Key topics:** Automatic tracing · `@traceable` · metadata & tags · `evaluate()` · custom evaluators · production metrics · Prompt Hub · debugging best practices

---

### 🏭 Module 12 — Production Best Practices
**File:** `12_Production_Best_Practices.ipynb`

Everything you need to ship LLM apps to production: resilient error handling, caching strategies, async processing, cost control, and security.

**Key topics:** `.with_retry()` · `.with_fallbacks()` · `InMemoryCache` · `SQLiteCache` · async/concurrent processing · cost optimization · prompt injection defense · deployment checklist

---

## 🗺️ Learning Path

```
00_FREE_Setup_Guide   ──►  00_LangChain_Overview
                                    │
                           01_LLMs_and_ChatModels
                                    │
                           02_Prompt_Templates
                                    │
                           03_Output_Parsers
                                    │
                           04_LCEL_Chains
                                    │
                           05_Memory_and_Conversations
                                    │
                           06_Document_Loaders
                                    │
                           07_Embeddings_and_VectorStores
                                    │
                           08_RAG (Retrieval-Augmented Generation)
                                    │
                           09_Tools_and_Agents
                                    │
                           10_LangGraph
                                    │
                           11_LangSmith_Observability
                                    │
                           12_Production_Best_Practices
```

---

## 🆓 Free Model Reference

| Model | Provider | Best For | Speed |
|-------|----------|----------|-------|
| `llama-3.1-8b-instant` | Groq | Day-to-day tasks, classification, Q&A | ⚡⚡⚡ |
| `llama-3.3-70b-versatile` | Groq | Complex reasoning, coding, analysis | ⚡⚡ |
| `mixtral-8x7b-32768` | Groq | Long context (32K tokens) | ⚡⚡ |
| `gemma2-9b-it` | Groq | Compact, efficient tasks | ⚡⚡ |
| `gemini-1.5-flash` | Google | Multimodal (text + images) | ⚡⚡ |
| `llama3.2` (local) | Ollama | Privacy-sensitive, offline use | ⚡ (CPU-dependent) |
| `all-MiniLM-L6-v2` | HuggingFace | Embeddings (always free, local) | ⚡⚡⚡ |

---

## 📦 Dependencies

```
langchain
langchain-core
langchain-community
langchain-groq
langchain-google-genai
langchain-ollama
langchain-huggingface
langchain-text-splitters
sentence-transformers
faiss-cpu
chromadb
python-dotenv
pydantic
```

---

## 📝 Notes

- All notebooks load environment variables from `../.env` (the parent `AI/` directory).
- Restart the Jupyter kernel after installing new packages.
- If you see a `NotFoundError (404)` from Groq, make sure you are using a valid Groq model name (not an OpenAI model name like `gpt-4o-mini`).
- For the best experience, run notebooks in order — later modules build on concepts from earlier ones.
