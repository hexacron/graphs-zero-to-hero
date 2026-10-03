# Module 9: Graph algorithms and graph ML

Goal: use the shape of the graph to find what nobody asked about. Time: 6 to 8 hours.

## Learn

| Algorithm family | Examples | OSINT question it answers |
| --- | --- | --- |
| Centrality | Degree, betweenness, PageRank, eigenvector | Who is the broker? Who is important but quiet? |
| Community detection | Louvain, Leiden, label propagation | Which groups act together? |
| Paths | Shortest path, all simple paths, k-shortest | How are A and B connected? |
| Similarity | Jaccard, node similarity | Who has the same contacts as this person? |
| Link prediction | Common neighbours, Adamic-Adar | Which relation probably exists but is not in the data? |
| Components | Weakly and strongly connected components | Which clusters are isolated? |
| Temporal | Snapshots, edge timestamps | What changed in the network last month? |

Graph ML, in order of practical value:

- **Node embeddings** (node2vec, FastRP): vectors that encode a node's position in the graph. Use them for similarity and as features.
- **Combine** text embeddings and node embeddings. Two entities with similar text and similar network position are strong merge or link candidates.
- **Graph neural networks** (GNNs: GCN, GraphSAGE): learn from features plus structure. Learn the concept. Use only if simpler methods fail and you have labels.

Warning: centrality on noisy data finds noise. Clean and resolve first (Module 7). Remove known hubs (registered agents, nominee directors) or weight them down.

## Lab

1. Run PageRank, betweenness, and Leiden on your resolved entity graph (Neo4j GDS or igraph).
2. List the top 10 by betweenness. Check each one by hand. Real broker or artefact?
3. Generate node2vec embeddings. Find the 5 nearest neighbours of 3 known entities. Judge the results.
4. Hide 10% of edges. Predict them with Adamic-Adar. Measure how many come back.

## Done when

- [ ] You found at least one non-obvious entity of interest from structure alone.
- [ ] You can explain why betweenness and PageRank give different top lists.

## Read

- Stanford CS224W (Machine Learning with Graphs, Leskovec) lectures 1 to 6. Free online.
- node2vec paper (Grover and Leskovec, 2016).
- Neo4j Graph Data Science docs, algorithm pages.
