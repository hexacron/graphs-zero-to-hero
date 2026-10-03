# Module 10: Graphs as agent memory and tools

Goal: give agents the graph as a tool and as memory, with safe limits. Time: 6 to 8 hours.

## Learn

An agent uses the graph in 3 ways:

- **As a tool:** the agent calls functions like `find_entity`, `expand(entity, hops, types)`, `shortest_path(a, b)`, `run_readonly_query(cypher)`. Narrow tools beat one open query tool. They are easier to test, log, and limit.
- **As memory:** the agent writes what it learns back to the graph. Episodic memory (what happened in this run) and semantic memory (facts about entities) go in different layers.
- **As shared state:** many agents read and write one graph. The graph is the blackboard. Provenance tells you which agent wrote which fact.

Design rules:

- Agent writes go to a **staging layer** with confidence and source. Promote to the main graph by rule or by a human. Never let an agent overwrite curated facts.
- **Bitemporal facts:** store when a fact was true in the world and when the system learned it. Agents need both to reason about change. (Graphiti and Zep use this pattern.)
- Return small results. A 2-hop expand on a hub can return 10,000 nodes. Cap, rank, and summarize before the result goes into context.
- Expose the tools through **MCP**. Then any agent framework or Claude Code can use the same graph tools.
- Log every tool call and query. This is your audit trail and your eval data.

## Lab

1. Build an MCP server with 5 to 7 narrow graph tools over your Neo4j instance. Read-only first.
2. Connect it to Claude Code or a local agent. Ask your 10 multi-hop questions. Read the tool-call traces.
3. Add a `propose_fact` write tool that writes to staging with provenance.
4. Add bitemporal fields to one relation type. Ask "who was director of X in 2021?"
5. Add result caps and a hub warning. Test it against your biggest hub.

## Done when

- [ ] An agent answers multi-hop questions through your MCP tools, with a full trace.
- [ ] No agent write can reach the curated graph without promotion.

## Read

- Model Context Protocol specification (tools section).
- Graphiti docs and the Zep temporal knowledge graph paper (2025).
- Anthropic engineering post "Building effective agents" (2024), for tool design.
