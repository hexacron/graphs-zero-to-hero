# Graphs for Agentic Engineering: Zero to Hero

A hands-on course on graphs, RDF, embeddings, chunking, and GraphRAG for people who build agentic systems.

## How to use this course

This course has 12 modules and 1 capstone. Each module gives you a goal, the concepts, a lab, and an exit check. Do the lab. Do not only read.

The course has three tracks that join at the end:

- **Graph track (Modules 0 to 3):** structure. How to model entities and relations.
- **Vector track (Modules 4 to 6):** meaning. How to find text by similarity.
- **Fusion track (Modules 7 to 11):** how to build graphs from text, retrieve with both, and give the result to agents.

Pace: about 60 to 80 hours total. Move fast through what you know. Stop and go deep where a lab breaks.

## The running dataset

Use one dataset in all modules. Then each lab builds on the last one.

- **Structured side:** a slice of OpenSanctions data in FollowTheMoney (FtM) format. Pick 1 country or 1 sanctions program. Target 2,000 to 10,000 entities.
- **Unstructured side:** 200 to 500 news articles or reports about the same entities. Use your own collection if you have one.

This pair is the real OSINT problem: a known graph plus a pile of text that partly describes it.

!!! warning "Data licence"
    OpenSanctions data is free for non-commercial use only. For commercial work, get a licence or use the ICIJ Offshore Leaks database (ODbL) plus Wikidata. Do not commit data to this repo.

## Lab stack (local-first)

| Job | Default | Alternative |
| --- | --- | --- |
| Code | Python 3.12, Jupyter | Claude Code for scaffolding |
| Graph analysis in memory | NetworkX | igraph (faster) |
| Property graph database | Neo4j Community in Docker | Memgraph, FalkorDB |
| RDF store and SPARQL | Oxigraph (pyoxigraph) | Apache Jena Fuseki, rdflib |
| Embeddings | Ollama with nomic-embed-text or bge-m3 | sentence-transformers |
| Vector store | sqlite-vec or LanceDB | Qdrant, pgvector |
| Reranker | bge-reranker (local) | none for first labs |
| LLM for extraction | Local model via Ollama | Claude API for quality baseline |

Start the services with `docker compose up -d` from the repo root. All ports bind to localhost only.

Rule for the whole course: you must be able to see the data. Every lab ends with a query result or a picture you can check by eye.
