#Medical RAG System

System Overview

Architecture: Retrieval-Augmented Generation for medical Q&A
Pipeline: Query, Embedding, FAISS Search, Cross-Encoder Rerank,  LLM Generation and metrics
Models: all-mpnet-base-v2 embeddings, ms-marco cross-encoder, Llama3 generation
Data: Medical Q&A pairs chunked at 1200 chars with 200 overlap

Current Performance

BLEU Score: 0.16
ROUGE-1: 0.46
ROUGE-2: 0.29
ROUGE-L: 0.34
semantic_similarity: 0.88
bertscore_f1: 0.50

Key Assumptions

Medical Safety: Conservative generation (temp=0.05) prevents misinformation
Semantic Over Syntactic: High semantic similarity (88%) more important than exact word overlap

Model Choices & Rationale

Embeddings: all-mpnet-base-v2 - Best general semantic understanding
Vector DB: FAISS IndexFlatIP - Fast cosine similarity for normalized embeddings
Reranker: Cross-encoder ms-marco - Proven passage ranking performance
Generator: Llama3 - Strong reasoning for medical content
BERTScore: bert-base-uncased works better than roberta-base for medical eval

Strengths

High semantic relevance (88%) - answers are medically appropriate
Scalable architecture - FAISS handles large document collections efficiently

Weaknesses

Low ROUGE/BLEU scores - generated text differs from reference phrasing
Generic embeddings - not optimized for medical terminology

Top 2 Future Improvements

Medical embeddings: Use BioBERT/ClinicalBERT for better medical terminology understanding
Specialized fine-tuning: Train Llama3 on medical datasets for improved domain reasoning
