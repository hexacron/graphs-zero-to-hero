# Capstone: a graph-backed monitoring layer

Build a working component you can drop into real infrastructure, for example the knowledge layer under your own monitoring system. Time: 15 to 20 hours.

## Scope

1. **Ingest:** a live feed (RSS, Telegram export, or your own collector). New documents arrive daily.
2. **Process:** chunk, embed, extract entities and relations, resolve against the existing graph, write with provenance and bitemporal fields.
3. **Retrieve:** hybrid search plus graph expansion, with a router that picks the pattern per question.
4. **Detect:** a daily job that reports new entities, new edges between known entities, community changes, and centrality jumps.
5. **Serve:** an MCP server with narrow tools. An agent writes a daily brief with citations to source chunks.
6. **Prove:** one command runs all evals. One query traces any brief claim to its source.

## Constraints

- Fully local. No telemetry. Runs on one box.
- Rebuild from raw data must work.
- Agent writes go to staging only.

## Done when

- [ ] It runs unattended for 7 days.
- [ ] The daily brief flags at least one change you did not already know.
- [ ] Every claim in the brief traces to a source.
- [ ] You can explain each design choice in one sentence, with a number from your own evals behind it.
