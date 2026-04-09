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
| 10 | `10-ai-best-practices-project-drupal-docs-landscape.md` | ai_best_practices / handbook | Docs gap: overview has short AI Assistants blurb; **webchick** project = Agent Skills (Claude Code, OpenCode) |
| 11 | `11-theming-tools-admin-theme-development.md` | theming_tools | Test modules for **admin theme** dev; **not for production**; ties to **Olivero** / **default_admin** (Gin-lineage, a11y); no Figma baseline for default_admin |
| 12 | `12-drupal-org-perimeterx-challenge-browsers.md` | drupalorg / infra | **PerimeterX** blocks (Chrome/Safari); login + **accounts.d.o**; **Reference ID** for logs; avoid clearing cookies mid-triage; not Fastly `/_fs-ch` |
| 13 | `13-entity-list-cache-tags-core-invalidation.md` | drupal (core) / docs | **`node_list`** is dynamic **`{type}_list`**; invalidation in **`EntityBase::postSave()`**; **`EntityType`** list/bundle list tag APIs; [mglaman](https://mglaman.dev/blog/leveraging-list-cache-tag-entity-types) |
| 14 | `14-drupal-core-controller-autowiring.md` | drupal (core) / docs | **Controller** autowiring; **`create()`** not always required; change record [**3395716**](https://www.drupal.org/node/3395716); context [**#3577774**](https://www.drupal.org/project/drupal/issues/3577774) |
| 15 | `15-new-relic-rpm-maintainer-capacity-3360583.md` | new_relic_rpm | **#3360583** Watchdog→**New Relic**; release ask; **berdir**: listed maintainer, last commit **2015**, no NR stack, won’t test/release |
| 16 | `16-ai-rag-multi-tenancy-search-api-ragtool-3584010.md` | ai / ai_search | Multi-tenant **RAG**: **`client_id`** metadata + **`QUERY_PRE_EXECUTE`**; **RagTool** dynamic filters [**#3584010**](https://www.drupal.org/project/ai/issues/3584010); prompt-safety on sensitive filters |

**Chat takeaways encoded above**

- The original comparison table undervalued **mcp_server** (corrected by e0ipso and by George after source review).
- **mcp_remote** is being positioned as reference-only; **mcp_server** is the consolidation target.
- **ai_agents_canvas_direct_edit** MCP pieces may move to **mcp_server**; Zivtech may contribute upstream.
- Sponsorship on **mcp_server** should be reflected in project visibility when appropriate.
- **ai_providers_api:** explicit prompt ownership for integrators (no black box), lean base module, unfunded—document and invite contributors.
- **api.drupal.org / Fastly:** interstitial loop with **401** on challenge **POST** (`_fs-ch`…`/pat`); Firefox affected, Chrome often fine; share **IP**, **HAR**, **`_fs_ch_*`** cookies with **help@drupal.org**; timing near DDoS mitigation change; separate **5xx**/load-alert reports in chat.
- **Drupal.org / PerimeterX:** bot challenge on **various pages** (including **login** / **accounts.drupal.org**); **Chrome** and **Safari**; capture **Reference ID** for staff logs (may lag **minutes**); **don’t clear session/cookies** while support clears an ID or you may get a **new** ID; distinct from **Fastly** `/_fs-ch` on **api.d.o**.
- **Change records:** duplicate node after **failed submit**; confirm **published** canonical vs dupe; **DA staff** can delete dupe (example resolved in Slack; nid **3576782** was the extra copy).
- **git.drupalcode.org:** **503** / “no server available” during **GitLab** maintenance; staff announced minor upgrade with migrations—downtime **up to ~10 min**; see **#drupal-infrastructure** Slack ([example message](https://drupal.slack.com/archives/C51GNJG91/p1775153980583419)).
- **AI + Drupal docs:** Handbook **Development tools overview** has a brief **Artificial Intelligence Assistants** section (e.g. Codeium)—not a full AI workflow guide. **[ai_best_practices](https://www.drupal.org/project/ai_best_practices)** ([webchick](https://www.drupal.org/u/webchick)): Agent Skills for **Claude Code** / **OpenCode** (modules, themes, config, hooks, plugins)—coordinate there to avoid duplicating a big new guide.
- **Admin themes:** **[theming_tools](https://www.drupal.org/project/theming_tools)** — test modules for **admin theme** development, **not for production**; chat notes usefulness with **Olivero** and **default_admin**; **default_admin** described as **Gin**-like, less cruft, more **accessible**; **no Figma** for default_admin; **a11y “ONE”** may apply to **default_admin** when accessibility issues are lined up (**experimental**).
- **Core cache tags:** **`node_list`** / **`{entity_type_id}_list`** (and e.g. **`node_list:article`**) are **not** always findable as literal strings; **invalidation** runs via **`EntityBase::postSave()`**; use **`EntityType`** **`getListCacheContexts()`**, **`getListCacheTags()`**, **`getBundleListCacheTags()`**, etc.; **mglaman** posts on list and bundle list tags.
- **Core controllers:** **Autowired** controllers can use **constructor injection** without always implementing static **`create()`**; see change record [**3395716**](https://www.drupal.org/node/3395716) (example thread: [**#3577774**](https://www.drupal.org/project/drupal/issues/3577774)).
- **Contrib / new_relic_rpm:** Release request for [**#3360583**](https://www.drupal.org/project/new_relic_rpm/issues/3360583) (Watchdog→**New Relic**); **berdir** (first on maintainer list) — **last commit 2015**, **no** New Relic environment to test, **no plans** to commit or release.
- **AI / multi-tenant RAG:** **Filterable** index attributes (e.g. **`client_id`**) + **`SearchApiEvents::QUERY_PRE_EXECUTE`** to enforce **tenant** bounds; same idea on **Azure** VDB with **multiple** filters; **LLM-supplied** RAG filters need **care** (no prompt trick to other tenants); [**#3584010**](https://www.drupal.org/project/ai/issues/3584010) — **RagTool** + dynamic metadata / `context_definitions`.
