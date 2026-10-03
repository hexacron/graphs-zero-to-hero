# Module 0: Graph fundamentals

Goal: think in nodes and edges, and know what questions a graph answers that a table does not. Time: 4 to 6 hours.

## Learn

- A graph is a set of **nodes** (things) and **edges** (relations between things).
- Edges are **directed** (A funds B) or **undirected** (A met B). Edges can have a **weight** (amount, confidence, count).
- **Degree** is the number of edges on a node. In a directed graph, use in-degree and out-degree.
- A **path** is a chain of edges. **Shortest path** is the minimum number of hops. Most OSINT link questions are path questions.
- A **bipartite** graph has two node types, and edges only go between types (people and companies). You can **project** it to one type (people linked by shared companies).
- **Adjacency list** and **adjacency matrix** are the two ways to store a graph. Know why sparse graphs use lists.
- **Multigraph:** more than one edge between the same two nodes. Real intelligence data is almost always a multigraph.

## Lab

1. Load your FtM slice into NetworkX as a directed multigraph. Use entity IDs as node keys.
2. Print node count, edge count, and the 20 nodes with the highest degree.
3. Find the shortest path between two entities you choose.
4. Project the person-company graph to a person-person graph. Compare the edge counts.
5. Draw a 2-hop neighbourhood of one entity. Use Gephi or pyvis.

## Done when

- [ ] You can explain why the projected graph has many more edges than the source graph.
- [ ] You can say which high-degree nodes are real hubs and which are data noise (registered agents, mass-registration addresses).

## Read

- *Networks, Crowds, and Markets* (Easley and Kleinberg), chapters 2 and 3. Free online.
- NetworkX tutorial (official docs).
