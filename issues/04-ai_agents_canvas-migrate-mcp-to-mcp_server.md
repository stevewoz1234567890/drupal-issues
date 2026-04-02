# Issue: Evaluate migrating MCP transport to mcp_server (shared layer)

**Project:** [ai_agents_canvas_direct_edit](https://www.drupal.org/project/ai_agents_canvas_direct_edit) (submodule: MCP-related pieces)  
**Component:** Architecture / Integration  
**Priority:** Normal

## Summary

The **ai_agents_canvas_direct_edit_mcp** submodule (or equivalent) uses a **custom JSON-RPC transport** similar in spirit to what **mcp_remote** implemented on top of **mcp**. [George Kastanis](https://www.drupal.org/u/) suggested reviewing **[mcp_server](https://www.drupal.org/project/mcp_server)** as a **shared transport layer** instead of maintaining bespoke transport code.

[alexua](https://www.drupal.org/u/alexua) indicated willingness to move MCP parts to **mcp_server** once project messaging and fit are clear, and noted **Zivtech** has several client projects using MCP where team contribution to **mcp_server** could align with work streams.

## Goal

1. Compare current canvas MCP JSON-RPC wiring with **mcp_server**’s HTTP/Streamable HTTP and OAuth story.
2. Identify gaps (if any) between canvas needs and **mcp_server**; file upstream issues on **mcp_server** for missing hooks or docs rather than duplicating transport.
3. Plan a migration path that preserves the “try-able” Driesnote-style workflow without unnecessary LLM round-trips for simple edits.

## Non-goals

- Replacing the canvas product goal (deterministic prop edits from SDC schemas, cost/latency savings vs routing everything to an LLM)—only the **MCP plumbing** is in scope for consolidation.

## References

- [AI Agents Canvas Direct Edit](https://www.drupal.org/project/ai_agents_canvas_direct_edit) project page.
- Community thread: George → alexua on reviewing **mcp_server** as shared transport; alexua on moving MCP parts and Zivtech contributing where overlap exists.
