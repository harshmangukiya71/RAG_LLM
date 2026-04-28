# 🚀 Finance AI Agent (Advanced Version: RAG + ReAct + Query Optimization)

## 📌 Overview

This project is a **production-style Financial AI Agent** that combines:

* 🧠 LLM-based reasoning (ReAct)
* 📚 Retrieval-Augmented Generation (RAG)
* 🔍 Query normalization (handles typos automatically)
* ⚡ Smart routing + guardrails
* 📊 Financial tools (price, fundamentals, news)

👉 Designed to handle **real-world messy queries + financial analysis**.

---

## ✨ Features

### 📊 Financial Capabilities

* Real-time **stock price retrieval** (yfinance)
* Company **fundamentals (P/E, market cap, etc.)**
* Latest **financial news**

### 🧠 AI Capabilities

* **ReAct Agent (multi-step reasoning)**
* **LLM-based routing**
* **Query normalization (typo correction)**

Example:

```
currenly tesla traded at which price?
→ current Tesla stock price
```

### 📚 RAG (PDF Mode)

* Upload PDF
* Ask context-based questions
* Uses **FAISS + embeddings**

### 🔁 Mode Switching

* `pdf` → enter document mode
* `exitpdf` → exit document mode

---

## 🏗️ FULL ARCHITECTURE

## 🔷 High-Level Pipeline

```
User Query
   ↓
🧠 Query Normalization (LLM)
   ↓
📄 PDF Mode Check
   ↓
🔥 Guardrail Layer (price detection)
   ↓
🧠 LLM Router
   ↓
🤖 ReAct Agent
   ↓
🧰 Tools Layer
   ↓
📊 Final Response
```

---

## 🔍 Detailed Architecture

### 1️⃣ Query Normalization Layer

* Fixes typos and grammar
* Converts user query into structured form

Example:

```
apl share rate now
→ Apple stock price now
```

---

### 2️⃣ PDF / RAG Layer

Activated when:

```
pdf_mode = True
```

Flow:

```
Query → Embedding → FAISS → Top-k docs → LLM
```

---

### 3️⃣ Guardrail Layer (Soft Rules)

* Detects price-related queries using regex
* Prevents LLM hallucination
* Ensures correct tool usage

---

### 4️⃣ LLM Router

Classifies query into:

* price
* fundamentals
* news
* general

---

### 5️⃣ ReAct Agent (Core Intelligence)

Implements:

```
Thought → Action → Observation → Repeat
```

Example:

```
Compare Tesla vs Apple
→ Fetch Tesla data
→ Fetch Apple data
→ Compare
→ Answer
```

---

### 6️⃣ Tools Layer

#### 📈 Financial Tools

* `get_ticker()` → Yahoo Finance API
* `get_price()` → real-time stock price
* `get_fundamentals()` → company metrics

#### 🌐 News Tool

* DuckDuckGo Search

#### 🧠 LLM Fallback

* Handles edge cases

---

### 7️⃣ Response Layer

* Formats output
* Ensures concise answers

---

## ⚙️ Tech Stack

* Python
* LangChain
* NVIDIA LLM (LLaMA 3.3)
* FAISS (Vector DB)
* Sentence Transformers
* yfinance API
* DuckDuckGo Search

---

## 🚀 How to Run

### 1. Install dependencies

```
pip install langchain langchain-community langchain-nvidia-ai-endpoints yfinance duckduckgo-search requests sentence-transformers faiss-cpu pypdf
```

### 2. Set API key

```
os.environ["NVIDIA_API_KEY"] = "YOUR_API_KEY"
```

### 3. Run

```
python main.py
```

---

## 💬 Example Queries

### 📊 Finance

* "Tesla stock price"
* "Apple P/E ratio"
* "Latest news on Nvidia"

### 🧠 Complex

* "Compare Tesla vs Apple stock"

### 📚 PDF Mode

* "What is conclusion of this paper?"

---

## 🎯 Key Design Principles

* ✅ Hybrid system (LLM + tools + rules)
* ✅ Robust to noisy input (typos)
* ✅ Modular & scalable
* ✅ Fault-tolerant

---

## 🚀 Future Improvements

* Function calling agent (remove guardrails)
* LangGraph integration
* FastAPI deployment
* Streamlit UI

---


