# Issue: End-to-end validation: mcp_server + simple_oauth_21 + Claude.ai (production)

**Project:** [mcp_server](https://www.drupal.org/project/mcp_server)  
**Component:** Support / QA (or Documentation once verified)  
**Priority:** Normal

## Summary

[George Kastanis](https://www.drupal.org/u/) committed to testing **mcp_server** with **simple_oauth_21** end-to-end against Claude.ai on a production site. Success means adopting the stack instead of maintaining a separate **mcp_remote** transport; **failure should produce concrete issue reports**, not a long-lived parallel module.

## Goal

Document (or fix) a reproducible path for:

1. **mcp_server** configured with Streamable HTTP and OAuth 2.1 as intended.
2. **simple_oauth_21** (or documented equivalent) wired for the MCP use case.
3. **Claude.ai** (or another remote MCP client) connecting successfully in a real deployment.

## Acceptance criteria

- Either:
  - **A)** A short “Production checklist” or handbook page on **mcp_server** (or **simple_oauth_21**) describing working configuration and known caveats, **or**
  - **B)** Filed child issues with **specific** failures (endpoint, error message, OAuth step, CORS if relevant, etc.).

## Out of scope (for this meta-issue)

- Maintaining **mcp_remote** as a competing product module; **mcp_remote** is to be reference-only with README pointing here (see `03-mcp_remote-reference-deprecation.md`).

## References

- George: “Success means I adopt the existing solution. Failure means I will file issues with concrete findings instead of maintaining a parallel module.”
