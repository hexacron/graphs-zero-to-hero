# Module 7: Building knowledge graphs from text

Goal: turn your unstructured corpus into graph facts you can trust and trace. Time: 10 to 12 hours. This is the hardest module.

## Learn

The pipeline has 5 stages. Each stage has its own failure mode.

1. **Entity extraction (NER):** find mentions of people, orgs, places. Use GLiNER or spaCy for speed, an LLM for quality.
2. **Relation extraction:** find what links the mentions. An LLM with a fixed schema (your Module 3 ontology) in structured output works best. Do not let the model invent relation types.
3. **Entity resolution (ER):** decide which mentions are the same real thing. "A. Petrov", "Alexei Petrov", and "Петров А." may be 1 person or 3. This is the core problem. Bad ER poisons every later step.
4. **Linking:** connect resolved entities to your existing graph and to outside IDs (Wikidata, OpenSanctions).
5. **Provenance:** every extracted fact keeps its source chunk, character span, model, prompt version, and confidence.

Key ideas for ER:

- **Blocking:** only compare candidates that share something (name key, birth year). Without it, comparisons grow as N squared.
- **Scoring:** combine name similarity, transliteration, shared attributes, and graph context (shared neighbours).
- **Clustering:** turn pairwise matches into entity clusters. Watch for chain errors (A=B, B=C, but A is not C).
- Keep the raw mentions. Store resolution as a separate, reversible layer. You will re-run it.

## Lab

1. Run NER and relation extraction on 100 articles. Use your ontology as the output schema.
2. Hand-label 30 articles. Measure precision and recall of extraction.
3. Run ER with Splink on the extracted people. Tune the match threshold against your labels.
4. Link resolved entities to your FtM graph. Count new entities, new edges, and conflicts.
5. Load everything with provenance. Write a query: "show every source for this edge."

## Done when

- [ ] You know your extraction precision and recall, with numbers.
- [ ] Every edge in the graph traces back to a chunk and a span.
- [ ] You can undo one bad merge without a full rebuild.

## Read

- Splink docs (the Fellegi-Sunter model section).
- GLiNER paper (2023).
- OpenSanctions blog posts on entity matching (practical, OSINT-specific).
