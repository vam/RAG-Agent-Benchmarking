# Architecture

## Overview

This project implements a Retrieval-Augmented Generation (RAG) pipeline that combines document retrieval with language model generation to answer questions.

---

## System Pipeline

User Query  
↓  
Embedding Model (SentenceTransformers)  
↓  
FAISS Retrieval (Top-K documents)  
↓  
Reranking (Similarity scoring)  
↓  
Context Construction  
↓  
Prompt Engineering  
↓  
LLM (FLAN-T5 / DistilGPT2)  
↓  
Generated Answer  

---

## Detailed Flow

### 1. Input
- User provides a natural language query

### 2. Embedding
- Query is converted into vector representation using SentenceTransformers

### 3. Retrieval
- FAISS is used to retrieve top-K similar documents based on embedding similarity

### 4. Reranking
- Retrieved documents are re-scored using similarity with the query
- Documents are sorted to improve relevance

### 5. Context Creation
- Top documents are combined to form a context passage

### 6. Prompt Engineering
- Context + Query are formatted into structured prompts

### 7. Generation
- LLM generates the final answer:
  - Small Model: DistilGPT2
  - Large Model: FLAN-T5

### 8. Output
- Final answer is returned to the user

---

## Key Components

### Retrieval
- FAISS for efficient similarity search

### Embedding Model
- SentenceTransformers for semantic encoding

### Generator Models
- FLAN-T5 Large (primary model)
- DistilGPT2 (baseline)

### Evaluation
- Quantitative metrics: EM, F1, Retrieval Accuracy, Faithfulness, Latency
- Qualitative: LLM-as-a-Judge

---

## Design Highlights

- Modular pipeline (retrieval + generation)
- Configurable prompts, retrieval strategies, and models
- Reranking improves context quality
- Fully reproducible experimentation setup

---

## Key Insight

The system demonstrates how combining retrieval with generation improves answer accuracy while maintaining contextual grounding.
