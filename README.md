```
    ██████╗ ██████╗ ██╗   ██╗██████╗ █████╗ ██╗
    ██╔══██╗██╔══██╗██║   ██║██╔══██╗██╔══██╗██║
    ██║  ██║██████╔╝██║   ██║██║  ██║███████║██║
    ██║  ██║██╔══██╗██║   ██║██║  ██║██╔══██║██║
    ██████╔╝██║  ██║╚██████╔╝██████╔╝██║  ██║███████╗
    ╚═════╝ ╚═╝  ╚═╝ ╚═════╝ ╚═════╝ ╚═╝  ╚═╝╚══════╝
         issues · drafts · straight from the hive
```

# Drupal contribution intelligence

**Polished, queue-ready issue drafts and curated community context** for the Drupal ecosystem—so decisions from Slack, IRC, and maintainer threads become **clear, actionable work** on [Drupal.org](https://www.drupal.org), not lost chat scrollback.

This repository is a **public workflow**: versioned narratives, cross-linked topics, and a single index you can open when someone asks, *“What did we agree about mcp_server?”*, *“What was the Fastly / Firefox story on api.drupal.org?”*, *“Why am I blocked by PerimeterX on Drupal.org?”*, *“Where is `node_list` invalidated in core?”*, *“How do we do multi-tenant RAG with Search API?”*, *“Which Drupal module should I use to purge Cloudflare cache?”*, *“Why does everyone want a Drupal Laravel Boost?”*, *“Why is my 2.x series not marked Supported on Drupal.org?”*, *“Why did Chrome tests start failing on GitHub Actions?”*, *“Who maintains new_relic_rpm?”*, or *“Where is the civicrm_entity MR for that autocomplete?”*

It is **not** an official Drupal Association project—it's a disciplined notebook that happens to read like a **map of how serious Drupal practitioners think**.

---

## Why this matters if you hire Drupal developers

Organizations rarely see *how* their partners work upstream. This repo is a window into habits that separate **maintenance mode** from **platform partnership**:

| Signal | What you see here |
|--------|-------------------|
| **Upstream citizenship** | Issue text drafted for real project queues—respectful tone, reproducible problems, concrete next steps. |
| **Modern Drupal + AI** | Active tracking of **MCP** consolidation (**mcp_server**, **mcp_remote**), **AI** / **ai_search** / **RAG** patterns, **AI providers** positioning, **agent tooling**, **Surge** / **Boost-shaped** DX, and the **AI Best Practices** initiative—not buzzwords, filed work. |
| **Operational realism** | Notes on **Drupal.org infrastructure** (CDN / **Fastly**, **PerimeterX**, browser edge cases, GitLab maintenance, change-record workflow) and **hosted CI** (e.g. **GitHub Actions** runner images affecting **Chrome** / **Behat**) because production sites and pipelines depend on that glue. |
| **Core and contrib reality** | **Cache API** / entity list tags, **controller** autowiring, **admin theme** tooling, and **maintainer capacity** on long-tail modules (e.g. observability integrations)—what docs often omit. |
| **Release literacy** | Community-sourced context (e.g. **OpenTelemetry** semver tradeoffs, security-driven releases) that informs upgrade planning. |

If you need **Drupal 10/11**, **contrib architecture**, **OAuth and API integrations**, **observability**, or **AI-assisted development done responsibly**, maintainers who **write issues before they rant** are the ones who **reduce your risk**.

---

## Start here

| Location | Purpose |
|----------|---------|
| [`issues/INDEX.md`](issues/INDEX.md) | Master table: target project, filename, one-line intent, and encoded chat takeaways |
| [`issues/`](issues/) | Numbered drafts (`01-…` through `16-…`)—retitle, set component/priority, add `@mentions`, then file |
| [`community/`](community/) | Short-lived or multi-project context: releases, ecosystem news, chat paraphrases—not always one issue |

**Before filing on Drupal.org:** align with each project's taxonomy, link real user profiles, and strip anything that was only for your own notes.

---

## Issue drafts at a glance

Themes below map to **16** numbered files in [`issues/`](issues/). The authoritative table (targets, filenames, one-line intent, chat takeaways) is [`issues/INDEX.md`](issues/INDEX.md).

| Range | Themes |
|-------|--------|
| **01–06** | **MCP & agents** — `mcp_server` accuracy and E2E testing, `mcp_remote` deprecation, `ai_agents_canvas_direct_edit` migration, contribution coordination, `ai_providers_api` positioning. |
| **07–09, 12** | **Drupal.org & infra** — `api.drupal.org` / Fastly interstitial (Firefox), duplicate change records, `git.drupalcode.org` **503**, **PerimeterX** on login / **accounts.d.o** ([`issues/12-drupal-org-perimeterx-challenge-browsers.md`](issues/12-drupal-org-perimeterx-challenge-browsers.md)). |
| **10** | **AI + handbook** — `ai_best_practices` / Agent Skills vs **Development tools overview** ([`issues/10-ai-best-practices-project-drupal-docs-landscape.md`](issues/10-ai-best-practices-project-drupal-docs-landscape.md)). |
| **11** | **Admin themes** — [`theming_tools`](https://www.drupal.org/project/theming_tools) (non-production test modules; **Olivero** / **default_admin** context) ([`issues/11-theming-tools-admin-theme-development.md`](issues/11-theming-tools-admin-theme-development.md)). |
| **13–14** | **Drupal core** — entity **list** cache tags ([`issues/13-entity-list-cache-tags-core-invalidation.md`](issues/13-entity-list-cache-tags-core-invalidation.md)); **controller** autowiring, change record **3395716** ([`issues/14-drupal-core-controller-autowiring.md`](issues/14-drupal-core-controller-autowiring.md)). |
| **15** | **Contrib maintainership** — [`new_relic_rpm`](https://www.drupal.org/project/new_relic_rpm) and [**#3360583**](https://www.drupal.org/project/new_relic_rpm/issues/3360583) ([`issues/15-new-relic-rpm-maintainer-capacity-3360583.md`](issues/15-new-relic-rpm-maintainer-capacity-3360583.md)). |
| **16** | **Multi-tenant RAG** — **Search API** + **ai**, tenant filters, [**#3584010**](https://www.drupal.org/project/ai/issues/3584010) ([`issues/16-ai-rag-multi-tenancy-search-api-ragtool-3584010.md`](issues/16-ai-rag-multi-tenancy-search-api-ragtool-3584010.md)). |

**Cross-cutting (community + issues)**

- **AI module landscape** — `ai_providers_api`, **AI Best Practices** / Agent Skills (**Claude Code**, **OpenCode**). **Laravel Boost** → **Surge**, [AI Initiative #3541110](https://www.drupal.org/project/ai_initiative/issues/3541110) — [`community/laravel-boost-drupal-ecosystem-slack.md`](community/laravel-boost-drupal-ecosystem-slack.md).
- **Drupal.org release semantics** — **Supported** vs **`-dev`**, series labels — [`community/drupalorg-release-series-supported-slack.md`](community/drupalorg-release-series-supported-slack.md), [infrastructure #3436596](https://www.drupal.org/project/project/issues/3436596).

**Also in [`community/`](community/)** (not always one issue queue): **Cloudflare** cache purge vs **purge** / **cloudflare_purge** ([`community/cloudflare-cache-purge-drupal-modules-slack.md`](community/cloudflare-cache-purge-drupal-modules-slack.md)); **CI** runner changes vs **Chrome** / **Behat** ([`community/gha-ubuntu-chrome-behat-shmem-psa.md`](community/gha-ubuntu-chrome-behat-shmem-psa.md)); **contrib** branching and **core** constraints ([`community/same_page_preview-d11-2.1-3.0-slack.md`](community/same_page_preview-d11-2.1-3.0-slack.md)); **maintainer review** link bundles ([`community/civicrm_entity-3580224-review-nudge-slack.md`](community/civicrm_entity-3580224-review-nudge-slack.md)); **mega menu** **`h2`/`h3` in `<nav>`** vs audits ([`community/mega-menu-nav-headings-a11y-slack.md`](community/mega-menu-nav-headings-a11y-slack.md)); **unpublished** nodes vs **bundle class** in preprocess ([`community/unpublished-node-bundle-class-slack.md`](community/unpublished-node-bundle-class-slack.md)); **malicious traffic** / **edge blocking** vs **AI** narrative, **scale** (**5×–20×**, **residential proxies**), **hobby bot** reassurance (**drumm** / **nnewton**) + [**Hojtsy** blog (Claude Code + d.o.)](https://www.hojtsy.hu/blog/2026-apr-10/solving-small-drupal-issue-plenty-added-tests-most-basic-claude-code-setup-without) ([`community/drupalorg-malicious-traffic-blocking-slack.md`](community/drupalorg-malicious-traffic-blocking-slack.md)); **core** **child issues** [**#3529510**](https://www.drupal.org/project/drupal/issues/3529510), **`@see`** spacing [**#3578091**](https://www.drupal.org/project/drupal/issues/3578091), **autowire** map [**#3578361**](https://www.drupal.org/project/drupal/issues/3578361) / [**#3295751**](https://www.drupal.org/project/drupal/issues/3295751), **`contact_storage`** attributes vs uninstall [**#3039906**](https://www.drupal.org/project/contact_storage/issues/3039906) ([`community/drupal-core-child-issues-see-docblock-autowire-contact-storage-slack.md`](community/drupal-core-child-issues-see-docblock-autowire-contact-storage-slack.md)).

Each numbered file is written to be **paste-ready** after project-specific edits.

---

## Community notes

| File | Topic |
|------|--------|
| [`community/cloudflare-cache-purge-drupal-modules-slack.md`](community/cloudflare-cache-purge-drupal-modules-slack.md) | **Cloudflare** cache purge: **cloudflare** vs **purge** + **cloudflare_purge**; SDK meta [**#3572890**](https://www.drupal.org/project/cloudflare/issues/3572890) / [**#3362051**](https://www.drupal.org/project/cloudflare/issues/3362051) |
| [`community/civicrm_entity-3580224-review-nudge-slack.md`](community/civicrm_entity-3580224-review-nudge-slack.md) | **civicrm_entity** **#3580224** (multilingual **Views** autocomplete); **MR !11** / **GitHub #546**; **`QueryHooks.php`** |
| [`community/drupalorg-release-series-supported-slack.md`](community/drupalorg-release-series-supported-slack.md) | **Supported** vs **`-dev`** / beta, **`2.0.*`** series label, [project #3436596](https://www.drupal.org/project/project/issues/3436596)—**drumm** / **penyaskito** |
| [`community/dxpr-builder-28-ai-release.md`](community/dxpr-builder-28-ai-release.md) | DXPR Builder **2.8** — AI + layout; summary for newsletters, Slack, or events |
| [`community/em-dash-cms-chat.md`](community/em-dash-cms-chat.md) | Lightweight chat capture (naming, April 1 context)—**not** a product review |
| [`community/gha-ubuntu-chrome-behat-shmem-psa.md`](community/gha-ubuntu-chrome-behat-shmem-psa.md) | **GHA** Ubuntu **24.04** image bump (**Apr 2026**): **Chrome** / **Behat** failures; **`/dev/shm`**; **`--disable-dev-shm-usage`** or **`ubuntu-22.04`** |
| [`community/laravel-boost-drupal-ecosystem-slack.md`](community/laravel-boost-drupal-ecosystem-slack.md) | **Laravel Boost** praise, **Surge**, **ai_best_practices**, [AI Initiative #3541110](https://www.drupal.org/project/ai_initiative/issues/3541110)—fragmentation → puzzle pieces |
| [`community/mega-menu-nav-headings-a11y-slack.md`](community/mega-menu-nav-headings-a11y-slack.md) | **Mega menu**: **`h2`/`h3` in `<nav>`** — semantic headings vs “no **`h*`** outside **`<main>`**”; **MDN `<nav>`** example; avoid **`div`**-only “headings” (chat) |
| [`community/opentelemetry-1.0.0-beta7-release-context.md`](community/opentelemetry-1.0.0-beta7-release-context.md) | **OpenTelemetry** beta release — protobuf upgrade, CI unblock, log-format caveat |
| [`community/same_page_preview-d11-2.1-3.0-slack.md`](community/same_page_preview-d11-2.1-3.0-slack.md) | **same_page_preview**: **D11** dropped from **2.1.x**; **3.0.0-beta1** vs **2.1.5** / **`^10.1`**; merge-up **#3461334** |
| [`community/unpublished-node-bundle-class-slack.md`](community/unpublished-node-bundle-class-slack.md) | **`preprocess_node`** / route **`node`**: not **bundle class** — **unpublished** content; **`hook_entity_bundle_info_alter`** OK; not a **recent core** change (chat) |
| [`community/drupalorg-malicious-traffic-blocking-slack.md`](community/drupalorg-malicious-traffic-blocking-slack.md) | **Drupal.org** **flood** / **WAF**-style blocking (**red** blocked, **green** allowed); **nnewton**: **not AI scraping**, **malicious**, **~5×–20×** normal via **residential-proxy DDoS**; **drumm**: **not** **hobby bot** traffic without **paid proxy** mesh; [**Hojtsy** post](https://www.hojtsy.hu/blog/2026-apr-10/solving-small-drupal-issue-plenty-added-tests-most-basic-claude-code-setup-without); **Fastly** vs **Cloudflare** challenge (chat) |
| [`community/drupal-core-child-issues-see-docblock-autowire-contact-storage-slack.md`](community/drupal-core-child-issues-see-docblock-autowire-contact-storage-slack.md) | **smustgrave**: hold **child issues** for [**#3529510**](https://www.drupal.org/project/drupal/issues/3529510); **`@see`** [**#3578091**](https://www.drupal.org/project/drupal/issues/3578091) — **quietone**: **Twig** standards, not new **coding_standards** issue; **autowire** [**#3578361**](https://www.drupal.org/project/drupal/issues/3578361) + [**#3295751**](https://www.drupal.org/project/drupal/issues/3295751) / [**#3578374**](https://www.drupal.org/project/drupal/issues/3578374); **`contact_storage`** [**#3039906**](https://www.drupal.org/project/contact_storage/issues/3039906) — **berdir**: **uninstall validator** vs **deprecation** noise |

Use these when you need **citable paraphrases** without opening a full issue.

Screenshots for select notes live under [`assets/`](assets/).

---

## Example snippets

Illustrative only—adapt names, versions, and Selenium endpoints to your project. For **Chrome** / **`/dev/shm`** on hosted runners, see [`community/gha-ubuntu-chrome-behat-shmem-psa.md`](community/gha-ubuntu-chrome-behat-shmem-psa.md).

### GitHub Actions — pin Ubuntu 22.04 on the job

Avoids the **Ubuntu 24.04** / **linux-azure-6.17** path some pipelines hit with headless Chrome; use when a runner-image bump breaks browser tests and you need a quick isolation step.

```yaml
jobs:
  phpunit:
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v4
```

### Behat (Mink) — Chrome flag `--disable-dev-shm-usage`

Makes Chrome use **`/tmp`** instead of **`/dev/shm`**, which sidesteps shared-memory issues on CI. Your `behat.yml` structure may differ; this matches common **MinkExtension** + **selenium2** setups.

```yaml
default:
  extensions:
    Behat\MinkExtension:
      browser_name: chrome
      selenium2:
        wd_host: 'http://127.0.0.1:4444/wd/hub'
        capabilities:
          browserName: chrome
          chromeOptions:
            args:
              - '--disable-dev-shm-usage'
```

### Drupal module — `core_version_requirement`

Example of declaring **Drupal 10** and **11** in a single extension (adjust lower bound to match APIs you use):

```yaml
name: 'Example module'
type: module
description: 'Illustrative core_version_requirement only.'
package: Custom
core_version_requirement: ^10.3 || ^11
```

---

## License

If you fork this pattern for your own drafts, license your content however you like. No license is asserted here for prose you add unless you state otherwise.

---

*Built for issue queues, merge requests, and the conversations that should survive them.*
