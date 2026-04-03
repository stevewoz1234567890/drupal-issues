# Drupal.org issue drafts (community chat and project notes)

These drafts are ready to paste into [Drupal.org issue queues](https://www.drupal.org/node/add/project-issue). Adjust titles, components, and user links to match each project’s taxonomy.

| # | File | Target project | Intent |
|---|------|----------------|--------|
| 1 | `01-mcp_server-project-page-accuracy.md` | mcp_server | Fix understating / maintenance messaging; accurate capability list |
| 2 | `02-mcp_server-e2e-remote-client-testing.md` | mcp_server | E2E Claude.ai + simple_oauth_21 + concrete follow-up issues |
| 3 | `03-mcp_remote-reference-deprecation.md` | mcp_remote | README: reference-only, recommend mcp_server |
| 4 | `04-ai_agents_canvas-migrate-mcp-to-mcp_server.md` | ai_agents_canvas_direct_edit | Migrate custom MCP transport to mcp_server |
| 5 | `05-mcp_server-contribution-coordination.md` | mcp_server | Roadmap/contributor visibility after sponsorship |
| 6 | `06-ai_providers_api-contributors-and-positioning.md` | ai_providers_api | Positioning vs AI package; no black-box prompts; base-only; call for contributors |
| 7 | `07-api-drupal-org-fastly-interstitial-firefox.md` | drupalorg / infra | Fastly interstitial loop on api.d.o (401 on `_fs-ch` POST); Firefox; mitigation change; help@ + HAR/IP |
| 8 | `08-drupal-org-duplicate-change-record-deletion.md` | drupalorg / CR workflow | Duplicate CR after failed submit; staff removed dupe ([node/3576782](https://www.drupal.org/node/3576782)); doc/process template |
| 9 | `09-git-drupalcode-org-gitlab-update-503.md` | drupalorg / infra | **503** on git.d.o during GitLab upgrade; ~10 min downtime possible; [#drupal-infrastructure](https://drupal.slack.com/archives/C51GNJG91/p1775153980583419) |

**Chat takeaways encoded above**

- The original comparison table undervalued **mcp_server** (corrected by e0ipso and by George after source review).
- **mcp_remote** is being positioned as reference-only; **mcp_server** is the consolidation target.
- **ai_agents_canvas_direct_edit** MCP pieces may move to **mcp_server**; Zivtech may contribute upstream.
- Sponsorship on **mcp_server** should be reflected in project visibility when appropriate.
- **ai_providers_api:** explicit prompt ownership for integrators (no black box), lean base module, unfunded—document and invite contributors.
- **api.drupal.org / Fastly:** interstitial loop with **401** on challenge **POST** (`_fs-ch`…`/pat`); Firefox affected, Chrome often fine; share **IP**, **HAR**, **`_fs_ch_*`** cookies with **help@drupal.org**; timing near DDoS mitigation change; separate **5xx**/load-alert reports in chat.
- **Change records:** duplicate node after **failed submit**; confirm **published** canonical vs dupe; **DA staff** can delete dupe (example resolved in Slack; nid **3576782** was the extra copy).
- **git.drupalcode.org:** **503** / “no server available” during **GitLab** maintenance; staff announced minor upgrade with migrations—downtime **up to ~10 min**; see **#drupal-infrastructure** Slack ([example message](https://drupal.slack.com/archives/C51GNJG91/p1775153980583419)).
