# Issue: README: reference-only status, recommend mcp_server, no maintenance commitment

**Project:** [mcp_remote](https://www.drupal.org/project/mcp_remote)  
**Component:** Documentation  
**Priority:** Normal

## Summary

**mcp_remote** was built to add Streamable HTTP transport, OAuth 2.1 discovery, and CORS on top of the **mcp** base module. After review, **mcp_server** already covers Streamable HTTP, OAuth 2.1 (e.g. via **simple_oauth_21**), and `.well-known` endpoints; for many setups, extra CORS work in **mcp_remote** adds little over server-to-server remote MCP.

The maintainer intends to **contribute to mcp_server** rather than maintain a separate module long-term.

## Proposed README changes

1. State clearly: **no stable release commitment**, **no tests**, **no ongoing maintenance** as a primary solution.
2. **Recommend [mcp_server](https://www.drupal.org/project/mcp_server)** for production and collaboration.
3. Position this repository as a **reference implementation** only: others may copy useful code (transport glue, CORS patterns, discovery wiring) into **mcp** or **mcp_server** as appropriate.
4. Link to **mcp_server** issue queue for bugs and features going forward.

## Optional

- Archive or mark the project “unsupported” on Drupal.org when policy allows, if the goal is purely historical reference—coordinate with **mcp_server** maintainers first.

## References

- George Kastanis: plans to upload code for reference; README note recommending **mcp_server**.
