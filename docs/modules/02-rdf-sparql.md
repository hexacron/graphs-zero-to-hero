# Module 2: RDF, triples, and SPARQL

Goal: understand the other graph model, and know when to use it. Time: 8 to 10 hours.

## Learn

- RDF stores facts as **triples**: subject, predicate, object. `ex:Alice ex:directorOf ex:AcmeLtd .`
- Every thing and every relation has a **URI** (IRI). This is the key idea. Two datasets that use the same URI talk about the same thing. That is how RDF joins data across sources with no import mapping.
- Objects are URIs or **literals** (strings, dates, numbers with a datatype).
- **Blank nodes** are things with no URI. Avoid them in your own data. They make merges and diffs hard.
- Serializations: **Turtle** (read and write by hand), **N-Triples** (one triple per line, good for streams), **JSON-LD** (JSON that is also RDF).
- **Named graphs** (quads) add a 4th field: which graph the triple is in. Use this for provenance: one named graph per source.
- **RDF-star** lets you make statements about a triple (confidence, source). This closes most of the gap with property graphs.
- **SPARQL** is the query language. It matches triple patterns. Learn `SELECT`, `OPTIONAL`, `FILTER`, property paths (`ex:owns+`), and `CONSTRUCT`.

## RDF versus property graph

| Need | Better fit |
| --- | --- |
| Join with outside data (Wikidata, sanctions lists) | RDF |
| Formal meaning and inference | RDF |
| Fast traversal and graph algorithms | Property graph |
| Properties on edges, simple for developers | Property graph |
| Provenance per source | Both (named graphs or edge properties) |

Most production systems use an LPG for the working graph and RDF-style URIs for identity. Use stable URIs even in Neo4j.

## Lab

1. Write 20 triples about 3 entities in Turtle, by hand.
2. Convert your FtM slice to RDF. Load it into Oxigraph. Put each source in its own named graph.
3. Write the same 10 queries from Module 1 in SPARQL. Note which ones were easier and which were harder.
4. Query the public Wikidata endpoint. Find your entities there. Link them with `owl:sameAs`.
5. Run one federated query that joins your local data with Wikidata.

## Done when

- [ ] You can explain why URIs make cross-source joins cheap.
- [ ] You can write a SPARQL property path query.
- [ ] You can say, for your own systems, which model you will use and why.

## Read

- W3C RDF 1.1 Primer.
- W3C SPARQL 1.1 Query Language, sections 2 to 9.
- Wikidata Query Service examples page (best free SPARQL practice ground).
