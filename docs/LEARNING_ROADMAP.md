# RAG/AI Learning Roadmap

> Personal learning plan. Goal: master AI/RAG by building a Personal Knowledge RAG on
> this repo → portfolio → Toronto AI Engineer role + own product.
> Started 2026-05. Learning notes & this doc are in English on purpose (portfolio reuse).

## Why this project

Learn AI/RAG **deeply** by building a "second brain" over my own study notes, on top of
this existing `enterprisellm` codebase. I am the perfect ground-truth evaluator of my own
notes — tightest possible feedback loop. Writing the notes IS the learning (Feynman style).

This repo already contains production-grade RAG (hybrid dense+BM25, RRF, bi-encoder
reranking, semantic chunking, query expansion). The learning is to **understand each piece
by measuring it**, then fill the gaps.

## Learning principles

1. One concept at a time — don't move on until I can explain it back.
2. Every concept grounded in this repo's real code, not abstract theory.
3. Measure before claiming done. No unsupported numbers.
4. Keep momentum: 1-2h/day, small steps compound.

## The 5 core files (the RAG engine)

| File | Role |
|------|------|
| `app/core/vector_store.py` | The engine — hybrid search, RRF, reranking |
| `app/core/document_loader.py` | Semantic chunking |
| `app/core/bm25_store.py` | BM25 keyword index + Korean tokenizer |
| `app/services/rag_service.py` | Orchestration + query expansion |
| `app/llm_client.py` | OpenAI-compatible LLM call (swap base_url) |

## Gaps to fill (the learning targets)

- [ ] Evaluation framework (biggest gap — none exists yet)
- [ ] Citation enforcement in answers
- [ ] NLI entailment verification (answer grounded in sources?)
- [ ] "I don't know" / confidence routing
- [ ] Per-stage cost & latency tracking
- [ ] Ablation framework (toggle reranker/BM25/expansion, compare)
- [ ] Obsidian vault connector (auto-sync notes)
- [ ] Recency boosting for time-aware queries

## 7-Module curriculum

### Module 0 — Foundations (CURRENT)
Feel the 3 primitives in real code: LLM, Embedding, Vector DB.
- 0.1 LLM as a probabilistic text→text function (`app/llm_client.py`, temp 0 vs 1)
- 0.2 Embeddings — text→vector, cosine similarity (queue/큐/대기열 vs Oracle/오라클)
- 0.3 Vector DB — semantic index vs Oracle B-tree (`vector_store.py` search())
- 0.4 First retrospective note

### Module 1 — Naive RAG
Build the simplest possible RAG, then break it. See the failure modes firsthand.

### Module 2 — Retrieval
BM25 (keyword) vs semantic (embeddings) vs hybrid (RRF) vs reranker. Why each exists.

### Module 3 — Document processing
Chunking strategies, document types, metadata. Why semantic chunking.

### Module 4 — Evaluation + measurement ★
The real differentiator for hiring. Build an eval set, get a baseline number,
run ablations. "How do you measure your AI?" is the interview question that matters.

### Module 5 — Production patterns
Citation enforcement, NLI verification, confidence-based refusal.

### Module 6 — Personal-RAG specifics
Obsidian sync, recency boosting, backlink graph (mini GraphRAG).

## 3 parallel tracks

- **Main learning** — the modules above, 1-2h/day
- **Build log** — one English blog post per module (journey + measured results)
- **Portfolio** — polish this repo's README in English, publish eval results, demo video

## Tooling

- Notes: Obsidian (local markdown)
- Embeddings: BGE-M3 (Korean + English)
- Learning LLM: OpenAI gpt-4o-mini (cheap) or Ollama local
- Everything in English

## Current position

**Module 0, Task 0.1** — read `app/llm_client.py`, call `chat_completion` at
temperature 0 vs 1, observe (non-)determinism, write the first English note.
Tasks 0.1–0.4 tracked in the session task list.
