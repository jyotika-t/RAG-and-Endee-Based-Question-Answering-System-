# RAG-based Document Question Answering System

This project implements a **Retrieval Augmented Generation (RAG)–based Document Question Answering System** using **Endee**, a high-performance open-source vector database.

The system allows users to ask questions in natural language and retrieves **semantically relevant information from indexed documents** using vector similarity search.

---

## Problem Statement

Traditional keyword-based search fails to capture semantic meaning in documents. This project solves that problem by using **vector embeddings and semantic search**, enabling accurate question answering from unstructured text data.

---

## System Design / Technical Approach

1. Documents are split into smaller text chunks  
2. Each chunk is converted into a vector embedding  
3. Embeddings are stored in **Endee vector database**  
4. User queries are embedded and searched against stored vectors  
5. Relevant document chunks are retrieved and returned as answers (RAG workflow)

## How Endee Is Used

Endee is the **core vector database** in this project.

- Stores vector embeddings of document chunks
- Performs fast semantic similarity search
- Returns the most relevant document content for a given query
- Acts as the retrieval layer for the RAG pipeline

This demonstrates a real-world use case where **vector search is central**.

---

## Features
- Semantic search
- RAG pipeline
- Agentic AI logic

## Setup

## (OPTIONAL) Create Virtual Environment 

```bash
python -m venv venv
venv\Scripts\activate
```

**1. Start Endee Database (required)**
```bash
docker compose up -d
```
```bash
docker ps
```
Ensure the Endee container is running on port 8080 before proceeding.

**2. Install Dependencies**
```bash
pip install -r requirements.txt
```

**3. Ingest Documents**
```bash
python scripts/ingest.py or python -m scripts.ingest
```

**4. Run the API Server**
```bash
uvicorn backend.app:app --reload
```

Visit `http://127.0.0.1:8000/docs` to test.

## Troubleshooting

- **Internal Server Error / 503**: Ensure Endee Docker is running (`docker compose up -d`) and documents are ingested (`python scripts/ingest.py`).
- **Connection refused**: The Endee database must be running at `localhost:8080` before the API can respond.

