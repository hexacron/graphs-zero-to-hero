# Module 6: Retrieval and RAG

Goal: build a retrieval pipeline that beats plain vector search, and measure it. Time: 6 to 8 hours.

## Learn

- **RAG** (retrieval-augmented generation): find relevant text, put it in the prompt, let the model answer from it. The retrieval step decides most of the quality.
- **BM25** is classic keyword search. It is strong on names, IDs, and rare terms: the exact places where vectors fail.
- **Hybrid search** runs BM25 and vector search, then merges the lists. **Reciprocal rank fusion (RRF)** is the simple, strong default for the merge.
- **Reranking:** take the top 50 to 100 from hybrid search. Score each one with a cross-encoder. Keep the top 5 to 10. This is often the single biggest quality gain.
- **Query rewriting:** let an LLM expand or split the query before search. HyDE (embed a fake answer, then search) is one form.
- **Metadata filters** (date, source, language) before the vector search. Do not ask vectors to do the job of a WHERE clause.
- **Metrics:** recall@k (did the right chunk come back), MRR and nDCG (how high was it), and answer faithfulness (did the answer use only the retrieved text).
- The limit of all of this: chunk retrieval answers "find the passage." It cannot answer "what connects A to C" when no single passage says it. That gap is why the graph comes back in Module 8.

## Lab

1. Add BM25 (SQLite FTS5 or Tantivy) next to your vector index.
2. Build hybrid search with RRF.
3. Add a local reranker.
4. Run your eval set at each stage: vector only, BM25 only, hybrid, hybrid plus rerank. Make a results table.
5. Write 10 multi-hop questions ("Which directors of companies owned by X also appear in Y?"). Test them. Record the failures. Keep them for Module 8.

## Done when

- [ ] You have a 4-stage results table on your own eval set.
- [ ] You have 10 multi-hop questions that plain RAG fails.

## Read

- Original RAG paper (Lewis and others, 2020), for vocabulary.
- RRF paper (Cormack and others, 2009). Short.
- RAGAS docs, for eval metric definitions.
