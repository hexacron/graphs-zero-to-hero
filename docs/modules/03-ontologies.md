# Module 3: Ontologies and schemas

Goal: design the vocabulary your graph uses, and check data against it. Time: 6 to 8 hours.

## Learn

- An **ontology** defines the types of things, the types of relations, and the rules between them. It is the contract that lets agents and humans read the same graph.
- **RDFS:** classes, subclasses, `domain` and `range`. Small and useful.
- **OWL:** adds logic (inverse, transitive, disjoint, cardinality). A **reasoner** can infer new triples. Powerful, but slow and easy to get wrong. Use a small part of it.
- **SKOS:** for taxonomies and controlled vocabularies (topic lists, threat categories). Not for entities.
- **SHACL:** validation shapes. "Every Company must have exactly one jurisdiction." This is the most practical tool in the stack. Use it like a test suite for data.
- **Open world versus closed world:** OWL assumes a missing fact is unknown, not false. Your SHACL checks and your SQL brain assume the opposite. Know which mode you are in.
- Reuse first. Relevant vocabularies for your work: **FollowTheMoney** (people, companies, ownership, sanctions), **STIX 2.1** (threat intelligence), **schema.org** (general web entities), **PROV-O** (provenance).
- Rule: invent a new class only when no existing vocabulary covers it. Then map it to the closest existing class.

## Lab

1. Write a small ontology (10 to 20 classes and relations) for your running dataset. Extend FtM. Do not replace it.
2. Add `PROV-O` terms so every fact can point to its source document and extraction run.
3. Write 5 SHACL shapes. Run them with pySHACL against your Module 2 data. Fix or flag what fails.
4. Add one inference rule (for example, `ownsShareOf` is transitive for control). Compare query results with and without it.

## Done when

- [ ] Your SHACL report runs in CI and fails on bad data.
- [ ] Every fact in the graph can answer "where did this come from?"
- [ ] You can say why you did not use full OWL reasoning.

## Read

- *Semantic Web for the Working Ontologist* (Allemang, Hendler, Gandon), chapters on RDFS and SHACL.
- W3C SHACL specification, sections 1 to 4.
- FtM schema explorer and STIX 2.1 object reference.
