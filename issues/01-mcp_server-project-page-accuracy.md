# Issue: Align project page with current capabilities and maintainer status

**Project:** [mcp_server](https://www.drupal.org/project/mcp_server)  
**Component:** Documentation / Project information  
**Priority:** Normal

## Summary

Potential contributors and adopters may skip **mcp_server** if the project page suggests it is unmaintained or understates what the module already provides. At least one contributor ([alexua](https://www.drupal.org/u/alexua)) chose a parallel path for a PoC partly because of messaging on the page.

## Problem

- The module already implements Streamable HTTP (via the official MCP SDK), OAuth 2.1 (e.g. via `simple_oauth_21`), `.well-known` endpoints (RFC 8414, 9728, 7591), and server-to-server use cases such as Claude.ai.
- If the **mcp_server** project page does not clearly state this, comparisons and module selection discussions will keep mischaracterizing it (as happened in community chat when **mcp_server** was listed as lacking Streamable HTTP / OAuth2 in a comparison table).

## Proposed resolution

1. Review the short description, README, and any “maintenance” or roadmap notices so they match the codebase.
2. Add a concise “What this module provides” (transports, auth integration points, remote vs browser clients) so people evaluating **mcp_remote**, **webmcp_connect**, or custom transports can see overlap and when to standardize on **mcp_server**.
3. If sponsorship or dedicated maintenance is coming ([e0ipso](https://www.drupal.org/u/e0ipso)), update the maintainer/status section when appropriate so the community knows the module is actively invested in.

## References

- Community thread: George Kastanis corrected the comparison after reviewing **mcp_server** source; **mcp_server** was more capable than the table suggested.
- [alexua](https://www.drupal.org/u/alexua): avoided **mcp_server** initially due to “not being maintained” messaging; willing to move **ai_agents_canvas_direct_edit** MCP pieces to **mcp_server** once messaging and fit are clear.

## Related

- See `02-mcp_server-e2e-remote-client-testing.md` for validation of remote-client flows.
