# Module 5: Chunking

Goal: cut documents into pieces that retrieve well and still make sense alone. Time: 4 to 6 hours.

## Learn

A chunk is the unit you embed and retrieve. Too big: the vector blurs many topics, and you waste context. Too small: the chunk loses the facts it needs to make sense ("He resigned in 2019": who?).

| Strategy | How it cuts | Use when |
| --- | --- | --- |
| Fixed size with overlap | Every N tokens, overlap M | Baseline only |
| Recursive | Split on paragraphs, then sentences, then words, until under size | Good default for prose |
| Structure-aware | Split on headings, list items, table rows, code blocks | Reports, HTML, Markdown, PDFs with structure |
| Semantic | Split where embedding similarity between sentences drops | Long text with no structure (transcripts) |
| Parent-child | Retrieve small chunks, return the larger parent | You need precise match and full context |
| Contextual | Add a short LLM-written summary of the whole document to each chunk before embedding | Chunks that lose their subject when cut |
| Late chunking | Embed the whole document with a long-context model, then pool per chunk | Long documents, when the model supports it |

Other rules:

- Keep metadata on every chunk: document ID, source, date, position, heading path. You will filter on it later.
- Chunk size must fit the embedding model's best input length, not its maximum.
- Tables and lists need special handling. A split table row is useless.
- For entity extraction (Module 7), chunk by meaning. For retrieval, chunk by query shape. These can be different chunk sets.

## Lab

1. Chunk your corpus 4 ways: fixed 512, recursive, structure-aware, and contextual.
2. Embed each set with your Module 4 winner.
3. Run your eval set against each. Record recall@10 and the average tokens returned.
4. Read 20 random chunks from each set. Mark the chunks that do not make sense alone.

## Done when

- [ ] You have a table of recall and token cost per strategy, on your own data.
- [ ] You picked a default and can say why.

## Read

- Anthropic engineering post on Contextual Retrieval (2024).
- Jina AI post and paper on late chunking (2024).
- "Lost in the Middle" (Liu and others, 2023): why more context is not free.
