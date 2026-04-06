# RAG Agent Benchmarking

## Overview
This project implements a Retrieval-Augmented Generation (RAG) system and benchmarks it across different prompts, retrieval strategies, and model sizes.

---

## Agent Setup

### Input
User question (natural language query)

### Output
Generated short answer

### Tools Used
- FAISS (retrieval)
- SentenceTransformers (embeddings)
- FLAN-T5 Large (generation)
- DistilGPT2 (baseline small model)

### System Flow
Query → Retrieval → Reranking → Context → LLM → Answer

---

## Dataset

- Source: SQuAD dataset  
- Size: ~1500 samples (subset used for experimentation)  
- Preprocessing:
  - Extracted context and QA pairs
  - Removed duplicates
  - Limited dataset for faster evaluation

---

## Experiment Setup

We evaluated the system across:

- Prompts: Prompt1, Prompt2  
- Retrieval Strategies: Top-3, Top-5  
- Models: Small, Large  

Total Configurations: **8**

---

## Metrics

### Quantitative
- Exact Match (EM)
- F1 Score
- Retrieval Accuracy
- Faithfulness
- Latency

### Qualitative (LLM-as-a-Judge)
- Correctness
- Completeness
- Reasoning

---

## Results

Best Configuration: **prompt1_top3_large**

-EM: 0.17
-F1: 0.27
-Retrieval: 0.97
-Faithfulness: 0.966666 

---

## Insights

- Large models significantly outperform small models  
- Top-3 retrieval performs better than top-5 due to reduced noise  
- Prompt design has a strong impact on performance  
- There is a clear trade-off between accuracy and latency  

---

## How to Run

### Option 1: Run on Google Colab (Recommended)

1. Open the notebook in Google Colab  
2. Run all cells sequentially  

---

### Option 2: Run Locally

1. Install dependencies:

```bash
pip install -r requirements.txt
