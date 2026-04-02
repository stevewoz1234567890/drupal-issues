# Issue: Contribution coordination and roadmap visibility (sponsorship)

**Project:** [mcp_server](https://www.drupal.org/project/mcp_server)  
**Component:** Community / Roadmap  
**Priority:** Minor (meta)

## Summary

[e0ipso](https://www.drupal.org/u/e0ipso) indicated an upcoming **sponsorship** to allow **significant dedication** to the MCP Server module, with **many changes** expected soon.

Several parties expressed interest in **contributing upstream** instead of maintaining parallel modules or transports:

- George Kastanis: **mcp_remote** → contribute to **mcp_server**; file concrete issues from production testing.
- **alexua** / **Zivtech**: migrate canvas MCP integration; contribute where MCP work overlaps client projects.

## Suggested actions for maintainers

1. When ready, publish a short **roadmap** or **contributors’ guide** (issue tags, coding standards, OAuth/transport extension points) so new contributors know where to plug in.
2. Pin or document **how to test** remote MCP clients (Claude.ai, etc.) so contributions don’t regress Streamable HTTP or OAuth flows.
3. Optionally open a **meta-issue** listing known follow-ups from the **mcp_remote** reference implementation (CORS for browser-originated clients vs server-to-server only—if still a product gap).

## References

- e0ipso: “Expect many changes very very soon.”
- George: will follow **mcp_server** development after deciding to consolidate efforts.
