# Module 11: Evaluation, provenance, and ops

Goal: run the system for months, not days, and prove its output. Time: 4 to 6 hours.

## Learn

- **Evaluate each layer alone:** chunking (recall), extraction (precision and recall), ER (pairwise precision and recall), retrieval (recall@k, nDCG), answer (faithfulness, citation accuracy). An end-to-end score hides which layer broke.
- **Golden sets** grow over time. Add every real failure you find as a new test case.
- **LLM-as-judge** is useful but biased. Calibrate it against 50 human labels before you trust it.
- **Provenance chain:** answer, to retrieved chunks and graph facts, to source documents, to collection time and method. If you cannot show this chain, the answer is not defensible.
- **Versioning:** version the ontology, the prompts, the extraction model, and the embedding model. When the embedding model changes, you must re-embed everything. Plan for it.
- **Drift:** new sources and new languages change extraction quality. Sample and re-check monthly.
- **Backup and rebuild:** you must be able to rebuild the graph from raw sources plus a resolution log. Test the rebuild.

## Lab

1. Put all your eval sets (Modules 4 to 8) into one test harness. Run it in CI.
2. Change one component (embedding model or chunker). Run the harness. Read the diff per layer.
3. Pick 5 answers from your agent. Trace each one back to source documents by query alone.
4. Delete the database. Rebuild from raw data. Compare counts.

## Done when

- [ ] One command runs every eval and prints a per-layer report.
- [ ] A full rebuild from raw sources works and matches.

## Read

- RAGAS and DeepEval docs (metric definitions).
- W3C PROV-O primer.
