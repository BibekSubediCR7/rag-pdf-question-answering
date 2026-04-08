# PDF AI Assistant using RAG (LangChain + OpenAI)

## Overview

This project implements an end-to-end Retrieval-Augmented Generation (RAG) pipeline that allows users to query a PDF document using natural language.

The system is built using a **Python Handbook (~100 pages)** as the source document. It processes the PDF, converts its content into embeddings, stores them in a FAISS vector database, retrieves relevant information, and generates context-aware answers using an OpenAI language model.

---

## Problem

Large Language Models (LLMs):
- do not have access to private or custom documents  
- may generate incorrect or hallucinated answers  
- cannot efficiently process large documents (e.g., 100-page PDFs)  

---

## Solution

This project combines retrieval with generation to solve these issues.

Pipeline:

1. Load Python Handbook PDF (~100 pages)  
2. Split text into chunks (size: 500, overlap: 50)  
3. Convert chunks into embeddings  
4. Store embeddings in FAISS vector database  
5. Retrieve top 3 relevant chunks  
6. Pass retrieved context into prompt  
7. Generate answer using GPT-4o-mini  

---

## Architecture

### Document Processing
- PDF loading (Python handbook)  
- Text extraction  
- Chunking (RecursiveCharacterTextSplitter)  
- Embedding generation  
- FAISS indexing  

### Query Processing
- User query input  
- Similarity search (top-k = 3)  
- Context injection into prompt  
- Response generation  

---

## Tech Stack

- Python  
- LangChain  
- OpenAI API  
- FAISS (vector database)  
- PyPDFLoader  

---

## Key Implementation Details

### Chunking Strategy
- Chunk size: 500  
- Overlap: 50  

### Embedding Model
- text-embedding-3-small  

### Retrieval
- FAISS vector store  
- Top-k: 3  

### LLM
- gpt-4o-mini  
- Temperature: 0  

### Prompt Design
- Uses only retrieved context  
- Avoids hallucination  
- Structured outputs (bullet points, headers)  
- Handles missing answers  

---

## Features

- Chat with a 100-page Python handbook PDF  
- Semantic search using embeddings  
- Context-aware responses  
- Interactive CLI chat loop  
- Structured answers (clean formatting)  

---

## Example Queries

- "Summarize Python basics from the document"  
- "Explain tuples in Python with examples"  
- "List Python data types"  
- "Give code examples for loops"  

---
