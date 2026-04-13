# Alpha testing **ai_provider_cli** — DDEV, Linux networking, **ddev-cli-relay**

**Project:** [AI Provider CLI](https://www.drupal.org/project/ai_provider_cli) (`ai_provider_cli`)  
**Component:** Documentation / support / ecosystem (adjust per queue)  
**Priority:** Normal

## Summary

Community alpha feedback from a **Linux host + DDEV + Drupal 11 + PostgreSQL** setup: the **CLI Provider** module works well for **plain chat** (e.g. **`cli__claude`** with **`--print`**) and integrations such as an **eval judge** in **ai_eval**, but **DDEV relay** onboarding and **Linux Docker** routing to the host need attention. A **Unix socket + socat sidecar** approach for **ddev-cli-relay** is proposed in an upstream PR to avoid **`host.docker.internal`** traffic being dropped by **iptables** on Linux.

## What worked

- Module **installs cleanly**; **CLI tools** configuration UI is **clear** (presets for **claude**, **codex**, **gemini**, **ollama**, **llm**, **lms**, **opencode**; optional **binary path** and **extra flags**).
- **Claude** via **`cli__claude`** works **end-to-end** as a Drupal AI provider.
- **Plain chat** (no tools) — e.g. as an **eval judge** in **ai_eval** — works **reliably**.

## Issues encountered

1. **ddev-cli-relay** — **`ddev add-on get Performant-Labs/ddev-cli-relay`** failed because there was **no GitHub release** yet; testers **cloned the repo** manually. Maintainer intent: **cut a release** and eventually submit as a **recognized DDEV plugin** (per Slack thread).
2. **Linux + Docker** — Relay listens on **`0.0.0.0:8765`** and **`host.docker.internal`** resolves (e.g. to **`172.17.0.1`**) inside the container, but **firewall / iptables** on many Linux setups **drops** traffic from **DDEV’s custom bridge networks** to **host-bound** ports. **macOS** (Docker Desktop VM) is **less affected**.

## Upstream fix (relay)

- **Pull request:** [Performant-Labs/ddev-cli-relay#2](https://github.com/Performant-Labs/ddev-cli-relay/pull/2) — adds a **Unix socket** under shared **`.ddev/`** volume and an **`alpine/socat`** sidecar so **container-to-container** HTTP (e.g. **`http://cli-relay-proxy:8765`**) bridges to the socket; **host and container** communicate via the **filesystem** instead of relying on **host TCP** from the web container. **TCP listener** remains for **host-side** testing and **macOS** compatibility.
- Ruled out for portability: **`network_mode: host`** (breaks DDEV routing), **LAN IP** mapping (firewalls still an issue), **sudo iptables** tweaks.

## Limitation to document

- **`cli__claude`** in typical **`--print`**-style **text-only** invocation suits **plain chat** and **judging** but **not** **`chat_with_tools`** / **function calling**. Worth a **short README or handbook** note so integrators set expectations.

## Proposed resolution (module / docs)

1. **README** (or project page): Link **ddev-cli-relay**, note **Linux** vs **macOS** behavior, and point to **#2** above until a **release** ships; mention **`composer require drupal/ai_provider_cli:1.0.x-dev`** for alpha testers.
2. **User guide:** Clarify **text-only** vs **tools** modes per CLI preset (at least **Claude** **`--print`**).
3. **Coordinate** with **ddev-cli-relay** maintainers on **releases** and **DDEV add-on** install path once tagged.

## References

- Slack: alpha announcement, **George Kastanis** feedback, **André Angelantoni** maintainer replies (release + PR welcome).
- Relay PR: [fix: add Unix socket + socat sidecar for Linux Docker support](https://github.com/Performant-Labs/ddev-cli-relay/pull/2).
- Screenshot (CLI tools table): local workspace copy at `C:\Users\kk\.cursor\projects\d-work-drupal-issues\assets\c__Users_kk_AppData_Roaming_Cursor_User_workspaceStorage_d7e1ff1385266c00dfa8f760485d15d0_images_image-fe4298d7-3eca-4ab4-bed9-1fc8c299fee1.png`.
