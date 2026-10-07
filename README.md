# Graphs for Agentic Engineering: Zero to Hero

A hands-on course on knowledge graphs, RDF, embeddings, chunking, and GraphRAG for people who build agentic systems.

12 modules and 1 capstone. Each module has a goal, the concepts, a lab, and an exit check. About 60 to 80 hours.

**Read the course:** https://hexacron.github.io/graphs-zero-to-hero/

## Start

```bash
git clone https://github.com/YOUR-USER/graphs-zero-to-hero
cd graphs-zero-to-hero
docker compose up -d        # Neo4j, Oxigraph, Ollama on localhost
```

Then open Module 0.

## Edit the course

The site source is in `docs/`. Preview it on your machine:

```bash
pip install -r requirements-docs.txt
mkdocs serve                # http://127.0.0.1:8000
```

A push to `main` builds and deploys the site to GitHub Pages.

## Licence

- Code: MIT (see `LICENSE`).
- Course text: CC BY 4.0 (see `LICENSE-CONTENT`).
