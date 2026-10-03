# Module 4: Embeddings and vector search

Goal: understand what an embedding is, what it can and cannot capture, and how vector search works. Time: 6 to 8 hours.

## Learn

- An **embedding** is a list of numbers (a vector) that a model makes from text. Texts with similar meaning get vectors that point in similar directions.
- **Cosine similarity** measures the angle between two vectors. If vectors are normalized, cosine and dot product give the same ranking.
- **Bi-encoder:** embed the query and the document separately. Fast, because you embed documents once. This is what vector search uses.
- **Cross-encoder:** read the query and the document together. Slow but more accurate. This is what a reranker uses (Module 6).
- Embeddings are bad at: exact names, IDs, numbers, negation ("not sanctioned" is close to "sanctioned"), and rare terms. This matters a lot for OSINT. Never use vectors alone for entity lookup.
- **Dimensions:** more is not always better. Some models (Matryoshka-trained) let you cut the vector short with small loss.
- **Multilingual models** (bge-m3 and others) put many languages in one space. Useful for cross-language monitoring.
- **Approximate nearest neighbour (ANN)** search: **HNSW** is the common index. Know its 3 settings (`M`, `ef_construction`, `ef_search`) and the speed-versus-recall trade-off.
- **Quantization** (int8, binary) cuts memory a lot. Test recall before you use it.
- Pick a model by testing on your own data. Public leaderboards (MTEB) are a start, not an answer.

## Lab

1. Embed 500 sentences from your corpus with 2 local models. Store them in sqlite-vec or LanceDB.
2. Make 30 test queries. For each one, mark the correct results by hand. This is your **eval set**. Keep it for the full course.
3. Measure recall@10 for each model. Pick the winner on numbers.
4. Test the failure cases: search for an exact company name, a passport number, and a negated phrase. Record what breaks.
5. Plot a 2D projection (UMAP) of the vectors, coloured by source or topic. Look for clusters.

## Done when

- [ ] You have a hand-labelled eval set of at least 30 queries.
- [ ] You can explain, with your own test results, why vector search alone fails for named entities.

## Read

- Sentence-BERT paper (Reimers and Gurevych, 2019).
- HNSW paper (Malkov and Yashunin), section on parameters.
- MTEB leaderboard (as a shortlist only).
