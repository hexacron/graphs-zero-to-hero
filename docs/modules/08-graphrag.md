# Module 8: GraphRAG

Goal: combine the graph and the vectors so retrieval can follow relations, not only text similarity. Time: 8 to 10 hours.

## Learn

"GraphRAG" means several different patterns. Know them apart.

| Pattern | How it works | Good for |
| --- | --- | --- |
| Entity-anchored | Find entities in the query, look them up in the graph, expand N hops, return linked chunks | "Tell me about X and its network" |
| Vector-then-graph | Vector search finds chunks, chunks link to entities, expand from those entities | Vague questions that touch known entities |
| Text-to-query | LLM writes Cypher or SPARQL, runs it, answers from rows | Precise structured questions (counts, paths) |
| Community summaries | Cluster the graph (Leiden), LLM summarizes each cluster, search the summaries | "What are the main themes across all of this?" |
| Personalized PageRank | Seed with query entities, rank nodes by random walk, return top chunks | Multi-hop recall (HippoRAG style) |

Key points:

- **Microsoft GraphRAG** made community summaries famous. It is expensive to build and best for global questions. It is weak for precise lookup.
- **Text-to-Cypher** is precise but brittle. Give the model the schema, 10 to 20 example queries, and a read-only user. Validate the query before you run it.
- **Subgraph to text:** how you serialize the retrieved subgraph into the prompt matters. Test triples, short sentences, and small tables.
- Most good systems route: a classifier or the agent picks the pattern per question.

## Lab

1. Link every chunk to the entities it mentions (from Module 7). Store chunk nodes in the graph with a `MENTIONS` edge.
2. Build entity-anchored retrieval: extract query entities, expand 2 hops, collect chunks, rerank.
3. Build text-to-Cypher with schema and examples. Run it read-only.
4. Run Leiden on the entity graph. Write a summary per community with an LLM.
5. Run your 10 multi-hop questions from Module 6 against each pattern. Compare with plain hybrid RAG.

## Done when

- [ ] You have a results table: question by pattern, pass or fail.
- [ ] You can say which pattern to use for which question type, from your own results.

## Read

- "From Local to Global: A Graph RAG Approach to Query-Focused Summarization" (Edge and others, Microsoft, 2024).
- HippoRAG paper (2024).
- LightRAG paper (2024), for a lighter-weight build.
