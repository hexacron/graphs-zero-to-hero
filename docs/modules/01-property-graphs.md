# Module 1: Property graphs and Cypher

Goal: model and query a graph in a database, not in memory. Time: 6 to 8 hours.

## Learn

- The **labelled property graph (LPG)** model: nodes have labels (`Person`, `Company`). Nodes and edges have key-value properties.
- Edges have one type and a direction. Put facts about the relation on the edge (`role`, `start_date`, `source`).
- **Cypher** (and the ISO standard **GQL**, which is close to Cypher) uses ASCII-art patterns: `(p:Person)-[:DIRECTOR_OF]->(c:Company)`.
- Variable-length paths: `-[:OWNS*1..4]->`. This is where graphs beat SQL joins.
- Indexes and constraints: a uniqueness constraint on the entity ID stops duplicate nodes on import.
- Modelling rule: if you query it as a hop, make it an edge. If you only filter on it, make it a property.
- The classic modelling trap: an event (a payment, a meeting) with more than 2 parties. Make the event a node.

## Lab

1. Run Neo4j Community in Docker. Bind it to localhost only.
2. Write an importer for your FtM slice. Use `MERGE` on entity ID. Make it idempotent: run it twice, get the same counts.
3. Write 10 queries. Include: all directors of a company, all companies 1 to 3 ownership hops from a person, people who share an address, and the shortest path between two people.
4. Remodel one relation as an event node (for example, an ownership stake with percent and dates). Rewrite the queries that touch it.
5. Run `EXPLAIN` and `PROFILE` on your slowest query. Add an index. Measure again.

## Done when

- [ ] Your importer is idempotent.
- [ ] You can write a variable-length path query from memory.
- [ ] You can defend each of your node-versus-edge-versus-property choices.

## Read

- *Graph Databases* (Robinson, Webber, Eifrem), chapters on data modelling.
- Neo4j Cypher manual: patterns and path sections.
- OpenSanctions FtM schema docs (to see a mature OSINT model).
