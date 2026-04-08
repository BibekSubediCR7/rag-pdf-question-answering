# PDF AI Assistant using RAG (LangChain + OpenAI)

## Overview

This project implements an end-to-end Retrieval-Augmented Generation (RAG) pipeline that allows users to query a PDF document using natural language.

The system processes a PDF, converts its content into embeddings, stores them in a FAISS vector database, retrieves relevant information, and generates context-aware answers using an OpenAI language model.

---

## Problem

Large Language Models (LLMs):
- do not have access to private documents  
- may generate incorrect or hallucinated answers  
- cannot efficiently process large documents  

---

## Solution

This project combines retrieval with generation to solve these issues.

Pipeline:

1. Load PDF using PyPDFLoader  
2. Split text into chunks (size: 500, overlap: 50)  
3. Convert chunks into embeddings  
4. Store embeddings in FAISS vector database  
5. Retrieve top 3 relevant chunks  
6. Pass retrieved context into prompt  
7. Generate answer using GPT-4o-mini  

---

## Architecture

### Document Processing
- PDF loading  
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
- FAISS  
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

- Chat with PDF using natural language  
- Semantic search using embeddings  
- Context-aware responses  
- Interactive CLI chat loop  
- Displays structured answers  

---

## Example Queries

- Summarize the document  
- Explain key concepts  
- Extract specific information  
- Provide code examples from content  

---

## Interactive Mode

- Continuous user input loop  
- Exit commands: `exit`, `quit`, `q`  
- Input validation for empty queries  

---

## Installation

```bash
pip install langchain-openai langchain-community langchain-text-splitters faiss-cpu pypdf
