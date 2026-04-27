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

This repository is a **public workflow**: versioned narratives, cross-linked topics, and [`issues/INDEX.md`](issues/INDEX.md) as the running ledger when someone asks, *“What did we agree about mcp_server?”*, *“What was the Fastly / Firefox story on api.drupal.org?”*, *“Why am I blocked by PerimeterX on Drupal.org?”*, *“Where is `node_list` invalidated in core?”*, *“How do we do multi-tenant RAG with Search API?”*, *“Which Drupal module should I use to purge Cloudflare cache?”*, *“Why does everyone want a Drupal Laravel Boost?”*, *“Why is my 2.x series not marked Supported on Drupal.org?”*, *“Why did Chrome tests start failing on GitHub Actions?”*, *“Who maintains new_relic_rpm?”*, *“Where is the civicrm_entity MR for that autocomplete?”*, *“What’s the process for a seeking-maintainer project namespace?”*, *“Why was a project page redirecting forever between www and new.drupal.org?”*, *“What did Community Health say when an #ai thread escalated?”*, *“I tagged a theme engine release—why is there no package on packages.drupal.org?”*, or *“Can Drupal send early hints for hero images?”* Recent memos add context on **edge cases** that look like *“Drupal.org CSS/JS is `text/html`”* (WAF/anti-abuse with **`nosniff`**), *“k6 vs Goose for load tests?”*, *“Why does Olivero’s mobile menu fire twice on one subtheme but not the other?”*, *“Theme Engine vs `drupal-module` on Composer”*, and *“HTTP 103 vs responsive `<picture>` / preload.”*

It is **not** an official Drupal Association project—it's a disciplined notebook that happens to read like a **map of how serious Drupal practitioners think**.

---

## Why this matters if you hire Drupal developers

Organizations rarely see *how* their partners work upstream. This repo is a window into habits that separate **maintenance mode** from **platform partnership**:

| Signal | What you see here |
|--------|-------------------|
| **Upstream citizenship** | Issue text drafted for real project queues—respectful tone, reproducible problems, concrete next steps. |
| **Modern Drupal + AI** | Active tracking of **MCP** consolidation (**mcp_server**, **mcp_remote**), **AI** / **ai_search** / **RAG** patterns, **AI providers** positioning, **agent tooling**, **Surge** / **Boost-shaped** DX, and the **AI Best Practices** initiative—not buzzwords, filed work. |
| **Operational realism** | Notes on **Drupal.org infrastructure** (CDN / **Fastly**, **PerimeterX**, **`www` vs `new.drupal.org`** routing edge cases, browser quirks, GitLab maintenance, change-record workflow), **`packages.drupal.org`** / **Composer** (which **project types** get mirrored, **`audit.block-insecure`** vs SA day), and **hosted CI** (e.g. **GitHub Actions** runner images affecting **Chrome** / **Behat**) because production sites and pipelines depend on that glue. |
| **Core and contrib reality** | **Cache API** / entity list tags, **controller** autowiring, **admin theme** tooling, **theme** subsystem churn (**theme engines** as **injectable services** from **Drupal 11.3** onward), and **maintainer capacity** on long-tail modules (e.g. observability integrations)—what docs often omit. |
| **HTTP + perceived performance** | Where **Symfony** / core **early hints** ([**#3563782**](https://www.drupal.org/project/drupal/issues/3563782)), **image preload** ([**#3309016**](https://www.drupal.org/node/3309016)), **`fetchpriority`**, and **responsive** markup meet **BigPipe**, **placeholder** timing, and **CDN** ordering—so you do not mistake a missing Composer package for a bug in `composer.json` when the issue is **project metadata**, or a **103** gap for a theming bug when the constraint is **layout**. See [`community/frontend-early-hints-hero-images-preload-slack.md`](community/frontend-early-hints-hero-images-preload-slack.md) and [`community/drupal-packagist-theme-engine-project-type-slack.md`](community/drupal-packagist-theme-engine-project-type-slack.md). |
| **Release literacy** | Community-sourced context (e.g. **OpenTelemetry** semver tradeoffs, security-driven releases) that informs upgrade planning. |
| **Community health** | When Slack threads spike: **CWG** / **Community Health** framing, **[Values & Principles](https://www.drupal.org/about/values-and-principles)**, and **constructive** escalation—so policy links survive the scrollback. |

If you need **Drupal 10/11**, **contrib architecture**, **OAuth and API integrations**, **observability**, or **AI-assisted development done responsibly**, maintainers who **write issues before they rant** are the ones who **reduce your risk**.

---

## Start here

| Location | Purpose |
|----------|---------|
| [`issues/INDEX.md`](issues/INDEX.md) | Master table: target project, filename, one-line intent, and encoded chat takeaways |
| [`issues/`](issues/) | Numbered drafts (`01-…` through `23-…`)—retitle, set component/priority, add `@mentions`, then file on Drupal.org |
| [`community/`](community/) | Short-lived or multi-project context: releases, **infra** / **Packagist** policy, performance threads, ecosystem news, chat paraphrases—not always one issue |

**Before filing on Drupal.org:** align with each project's taxonomy, link real user profiles, and strip anything that was only for your own notes.

---

## Issue drafts at a glance

Themes below map to **23** numbered files in [`issues/`](issues/). The authoritative table (targets, filenames, one-line intent, chat takeaways) is [`issues/INDEX.md`](issues/INDEX.md).

| Range | Themes |
|-------|--------|
| **01–06** | **MCP & agents** — `mcp_server` accuracy and E2E testing, `mcp_remote` deprecation, `ai_agents_canvas_direct_edit` migration, contribution coordination, `ai_providers_api` positioning. |
| **07–09, 12, 18** | **Drupal.org & infra** — `api.drupal.org` / Fastly interstitial (Firefox), duplicate change records, `git.drupalcode.org` **503**, **PerimeterX** on login / **accounts.d.o** ([`issues/12-drupal-org-perimeterx-challenge-browsers.md`](issues/12-drupal-org-perimeterx-challenge-browsers.md)), no public **status page** + [**#3372242**](https://www.drupal.org/project/infrastructure/issues/3372242) ([`issues/18-drupal-org-public-status-page-infrastructure-3372242.md`](issues/18-drupal-org-public-status-page-infrastructure-3372242.md)). |
| **10** | **AI + handbook** — `ai_best_practices` / Agent Skills vs **Development tools overview** ([`issues/10-ai-best-practices-project-drupal-docs-landscape.md`](issues/10-ai-best-practices-project-drupal-docs-landscape.md)). |
| **11** | **Admin themes** — [`theming_tools`](https://www.drupal.org/project/theming_tools) (non-production test modules; **Olivero** / **default_admin** context) ([`issues/11-theming-tools-admin-theme-development.md`](issues/11-theming-tools-admin-theme-development.md)). |
| **13–14, 19–20, 22–23** | **Drupal core** — entity **list** cache tags ([`issues/13-entity-list-cache-tags-core-invalidation.md`](issues/13-entity-list-cache-tags-core-invalidation.md)); **controller** autowiring, change record **3395716** ([`issues/14-drupal-core-controller-autowiring.md`](issues/14-drupal-core-controller-autowiring.md)); **PHP 8.5** + Views **`FieldViewsDataProvider`** [**#3582171**](https://www.drupal.org/project/drupal/issues/3582171) ([`issues/19-drupal-core-3582171-php85-views-fieldviewsdata-test.md`](issues/19-drupal-core-3582171-php85-views-fieldviewsdata-test.md)); **ProxyBuilder** **`@see`** [**#3092424**](https://www.drupal.org/project/drupal/issues/3092424), fork **`main`** + **rebase** MR cleanup ([`issues/20-drupal-core-3092424-proxybuilder-fork-main-rebase.md`](issues/20-drupal-core-3092424-proxybuilder-fork-main-rebase.md)); **Layout Builder** + moderation, temp storage **`serialize`**, `originalEntity` / **`__serialize()`** / **igbinary** [**#3581434**](https://www.drupal.org/project/drupal/issues/3581434) ([`issues/22-drupal-core-3581434-layout-builder-serialization-originalentity.md`](issues/22-drupal-core-3581434-layout-builder-serialization-originalentity.md)); **Image** **media** **thumbnail** **alt** **≠** **source** [**#3232414**](https://www.drupal.org/project/drupal/issues/3232414), **MR** + **tests** ([`issues/23-drupal-core-3232414-image-media-thumbnail-alt-mr-tests.md`](issues/23-drupal-core-3232414-image-media-thumbnail-alt-mr-tests.md)). |
| **15** | **Contrib maintainership** — [`new_relic_rpm`](https://www.drupal.org/project/new_relic_rpm) and [**#3360583**](https://www.drupal.org/project/new_relic_rpm/issues/3360583) ([`issues/15-new-relic-rpm-maintainer-capacity-3360583.md`](issues/15-new-relic-rpm-maintainer-capacity-3360583.md)). |
| **21** | **Scanner** — **image** field **alt**/**title** search [**#3584902**](https://www.drupal.org/project/scanner/issues/3584902), **WIP**, possible patterns for **body** summary in results ([`issues/21-scanner-3584902-image-field-alt-title-search.md`](issues/21-scanner-3584902-image-field-alt-title-search.md)). |
| **16** | **Multi-tenant RAG** — **Search API** + **ai**, tenant filters, [**#3584010**](https://www.drupal.org/project/ai/issues/3584010) ([`issues/16-ai-rag-multi-tenancy-search-api-ragtool-3584010.md`](issues/16-ai-rag-multi-tenancy-search-api-ragtool-3584010.md)). |
| **17** | **AI provider CLI + DDEV** — `ai_provider_cli` alpha, **ddev-cli-relay**, **Linux** / `host.docker.internal`, **`--print`** vs tools ([`issues/17-ai-provider-cli-alpha-ddev-relay-linux.md`](issues/17-ai-provider-cli-alpha-ddev-relay-linux.md)). |

**Cross-cutting (community + issues)**

- **AI module landscape** — `ai_providers_api`, **AI Best Practices** / Agent Skills (**Claude Code**, **OpenCode**). **Laravel Boost** → **Surge**, [AI Initiative #3541110](https://www.drupal.org/project/ai_initiative/issues/3541110) — [`community/laravel-boost-drupal-ecosystem-slack.md`](community/laravel-boost-drupal-ecosystem-slack.md).
- **Drupal.org release semantics** — **Supported** vs **`-dev`**, series labels — [`community/drupalorg-release-series-supported-slack.md`](community/drupalorg-release-series-supported-slack.md), [infrastructure #3436596](https://www.drupal.org/project/project/issues/3436596).
- **Seeking maintainer / namespace** — **process** + **maintainer outreach**; **~2 weeks** rule of thumb in chat (**verify** on d.o.); **friction by design**; **[annotations](https://www.drupal.org/project/annotations)** — [`community/drupalorg-seeking-maintainer-namespace-process-slack.md`](community/drupalorg-seeking-maintainer-namespace-process-slack.md).
- **`www` ↔ `new` redirect loop** — **[usage_data](https://www.drupal.org/project/usage_data)**; **drumm** fixed **misconfiguration**; **usage** on **[new.drupal.org/…/usage/…](https://new.drupal.org/project/usage/usage_data)** — [`community/drupalorg-usage-data-www-new-redirect-loop-slack.md`](community/drupalorg-usage-data-www-new-redirect-loop-slack.md).
- **new.drupal.org / Software page / social** — maintainer **proud** of module on **new** (public); **dww** **[Software](https://www.drupal.org/drupalorg/software)** link + **fine** to mention; [**#3584626**](https://www.drupal.org/project/drupalorg/issues/3584626) **update** stale page + **new** stack; **Mastodon** during **5xx**/**DDoS** (**mxr576**) — [`community/drupalorg-software-page-new-drupalorg-3584626-slack.md`](community/drupalorg-software-page-new-drupalorg-3584626-slack.md).
- **Drupal.org 429 / Fastly** — **14 Apr 2026**: **429** + **54113**, **Varnish** (**HEL** PoP); **Antti**: **Fastly** **rate limiting**; **www** worse than **new**; **CI** **patch** fetch failures; **dimitriskr**: **back** — [`community/drupalorg-429-fastly-rate-limit-apr2026-slack.md`](community/drupalorg-429-fastly-rate-limit-apr2026-slack.md).
- **Drupal.org CDN / timeouts / Redis** — **Apr 2026**: **slow** pages, **timeouts** misread as **500**; **nnewton**: **CDN** maint page **misleading**; root cause **Redis `KEYS`** on **large** instance + **roll back** **changes** — [`community/drupalorg-cdn-timeout-redis-keys-apr2026-slack.md`](community/drupalorg-cdn-timeout-redis-keys-apr2026-slack.md).
- **Drupal.org dashboard static assets (Apr 2026)** — **`advagg`** / **`/files/…`** **CSS**/**JS**/**images** served as **`text/html`** (**WAF**/**edge** + **`X-Content-Type-Options: nosniff`**); **drumm** **staged** **rules** — [`community/drupalorg-dashboard-assets-mime-fastly-apr2026-slack.md`](community/drupalorg-dashboard-assets-mime-fastly-apr2026-slack.md).
- **Load testing (Slack)** — **k6** (**Grafana** **k6** **Cloud** vs **OSS**), **Goose** (**Tag1** **FOSS**), **Drupal** **targets** — [`community/load-testing-tools-k6-goose-slack.md`](community/load-testing-tools-k6-goose-slack.md).
- **Olivero** — **`navigation-utils.js`** **no** **`Drupal.behaviors`**/**`once`**, **double** **sticky** **menu** **toggle** on some **subthemes** (**mherchel** — file **core** **issue**) — [`community/olivero-navigation-double-toggle-behaviors-slack.md`](community/olivero-navigation-double-toggle-behaviors-slack.md).
- **HTTP 103 / preload / responsive heroes** — **Early hints** for **CSS** first ([**#3563782**](https://www.drupal.org/project/drupal/issues/3563782)); **image** **`rel=preload`** ([**#3309016**](https://www.drupal.org/node/3309016), [**MR !14009**](https://git.drupalcode.org/project/drupal/-/merge_requests/14009)); same limits for **103** as for **head** preload when **`<picture>`** / **`sizes: auto`** need **layout** — [`community/frontend-early-hints-hero-images-preload-slack.md`](community/frontend-early-hints-hero-images-preload-slack.md).
- **Drupal Packagist + Theme Engine project type** — **Theme Engine** projects are **not** on **packages.drupal.org** / **Packagist.org**; **D11.3+** engines belong in **modules** ([**#3547356**](https://www.drupal.org/node/3547356)); staff **reclassify** via [**infrastructure**](https://www.drupal.org/project/infrastructure/issues) (e.g. [**#3587236**](https://www.drupal.org/project/infrastructure/issues/3587236) — **mjml_render_engine**) — [`community/drupal-packagist-theme-engine-project-type-slack.md`](community/drupal-packagist-theme-engine-project-type-slack.md).
- **Drupal.org Apr 2026 DDoS follow-through** — **git** **hook declined** / “Unable to contact Drupal.org”; **WAF**/**backend** instability windows (**nnewton**); **residential proxies**; **@drupalinfra** **caching** + **accounts** upgrade; **2FA** “recovery codes first” (**drumm**); **issue fork** **`main`** — [`community/drupalorg-ddos-waf-git-mastodon-accounts-apr2026-slack.md`](community/drupalorg-ddos-waf-git-mastodon-accounts-apr2026-slack.md).
- **`#ai` Slack escalation** — **CWG** / **AmyJune** **Community Health** reminder + **[Values & Principles](https://www.drupal.org/about/values-and-principles#seek-first-to-understand-then-to-be-understood)** — [`community/drupal-slack-ai-channel-cwg-health-reminder.md`](community/drupal-slack-ai-channel-cwg-health-reminder.md).
- **Drupal Slack / feedback etiquette** — **GitHub** link + “does this **qualify** for **DrupalCon**?” in **wrong** channel → **Jeremy Chinquist**: use **`#support`**, clarify ask; **sponsor** showcase vs **BoF**; [**actoolsDrupal**](https://github.com/actools-pl/actoolsDrupal) context — [`community/drupalcon-github-feedback-channel-support-slack.md`](community/drupalcon-github-feedback-channel-support-slack.md).

**Also in [`community/`](community/)** (not always one issue queue): **early hints** / **preload** / **responsive** images ([`community/frontend-early-hints-hero-images-preload-slack.md`](community/frontend-early-hints-hero-images-preload-slack.md)); **Packagist** / **Theme Engine** vs **module** project type ([`community/drupal-packagist-theme-engine-project-type-slack.md`](community/drupal-packagist-theme-engine-project-type-slack.md)); **dashboard** **MIME**/**WAF** ([`community/drupalorg-dashboard-assets-mime-fastly-apr2026-slack.md`](community/drupalorg-dashboard-assets-mime-fastly-apr2026-slack.md)); **k6**/**Goose** **load** **testing** ([`community/load-testing-tools-k6-goose-slack.md`](community/load-testing-tools-k6-goose-slack.md)); **Olivero** **menu** **toggle**/**`behaviors`** ([`community/olivero-navigation-double-toggle-behaviors-slack.md`](community/olivero-navigation-double-toggle-behaviors-slack.md)); **Cloudflare** cache purge vs **purge** / **cloudflare_purge** ([`community/cloudflare-cache-purge-drupal-modules-slack.md`](community/cloudflare-cache-purge-drupal-modules-slack.md)); **new.drupal.org** **Software** page / **social** / [**#3584626**](https://www.drupal.org/project/drupalorg/issues/3584626) / **Mastodon** incidents ([`community/drupalorg-software-page-new-drupalorg-3584626-slack.md`](community/drupalorg-software-page-new-drupalorg-3584626-slack.md)); **cdxgen** / **CycloneDX** SBOM for **Drupal** + **Dependency-Track** ([`community/cdxgen-drupal-dependency-track-sbom.md`](community/cdxgen-drupal-dependency-track-sbom.md)); **CI** runner changes vs **Chrome** / **Behat** ([`community/gha-ubuntu-chrome-behat-shmem-psa.md`](community/gha-ubuntu-chrome-behat-shmem-psa.md)); **contrib** branching and **core** constraints ([`community/same_page_preview-d11-2.1-3.0-slack.md`](community/same_page_preview-d11-2.1-3.0-slack.md)); **maintainer review** link bundles ([`community/civicrm_entity-3580224-review-nudge-slack.md`](community/civicrm_entity-3580224-review-nudge-slack.md)); **mega menu** **`h2`/`h3` in `<nav>`** vs audits ([`community/mega-menu-nav-headings-a11y-slack.md`](community/mega-menu-nav-headings-a11y-slack.md)); **node_revision_delete** **2.1.0-rc1** — **multilingual** revision safety + **entity query** perf ([`community/node_revision_delete-2.1.0-rc1-release.md`](community/node_revision_delete-2.1.0-rc1-release.md)); **unpublished** nodes vs **bundle class** in preprocess ([`community/unpublished-node-bundle-class-slack.md`](community/unpublished-node-bundle-class-slack.md)); **429** / **Fastly** **rate limit** (**Apr 2026**), **www** vs **new**, **CI** **patches** ([`community/drupalorg-429-fastly-rate-limit-apr2026-slack.md`](community/drupalorg-429-fastly-rate-limit-apr2026-slack.md)); **CDN** **timeouts** vs **500**, **Redis `KEYS`** (**nnewton**) ([`community/drupalorg-cdn-timeout-redis-keys-apr2026-slack.md`](community/drupalorg-cdn-timeout-redis-keys-apr2026-slack.md)); **DDoS** **git**/**WAF**/**Mastodon**/**accounts**/**2FA** ([`community/drupalorg-ddos-waf-git-mastodon-accounts-apr2026-slack.md`](community/drupalorg-ddos-waf-git-mastodon-accounts-apr2026-slack.md)); **malicious traffic** / **edge blocking** vs **AI** narrative, **scale** (**5×–20×**, **residential proxies**), **hobby bot** reassurance (**drumm** / **nnewton**) + [**Hojtsy** blog (Claude Code + d.o.)](https://www.hojtsy.hu/blog/2026-apr-10/solving-small-drupal-issue-plenty-added-tests-most-basic-claude-code-setup-without) ([`community/drupalorg-malicious-traffic-blocking-slack.md`](community/drupalorg-malicious-traffic-blocking-slack.md)); **seeking maintainer** / **namespace** handover ([`community/drupalorg-seeking-maintainer-namespace-process-slack.md`](community/drupalorg-seeking-maintainer-namespace-process-slack.md)); **`usage_data`** **`www`↔`new`** redirect loop ([`community/drupalorg-usage-data-www-new-redirect-loop-slack.md`](community/drupalorg-usage-data-www-new-redirect-loop-slack.md)); **`#ai`** **CWG** / **Community Health** reminder ([`community/drupal-slack-ai-channel-cwg-health-reminder.md`](community/drupal-slack-ai-channel-cwg-health-reminder.md)); **DrupalCon** / **GitHub** feedback → **`#support`** (**Jeremy Chinquist**) ([`community/drupalcon-github-feedback-channel-support-slack.md`](community/drupalcon-github-feedback-channel-support-slack.md)); **core** **child issues** [**#3529510**](https://www.drupal.org/project/drupal/issues/3529510), **`@see`** spacing [**#3578091**](https://www.drupal.org/project/drupal/issues/3578091), **autowire** map [**#3578361**](https://www.drupal.org/project/drupal/issues/3578361) / [**#3295751**](https://www.drupal.org/project/drupal/issues/3295751), **`contact_storage`** attributes vs uninstall [**#3039906**](https://www.drupal.org/project/contact_storage/issues/3039906) ([`community/drupal-core-child-issues-see-docblock-autowire-contact-storage-slack.md`](community/drupal-core-child-issues-see-docblock-autowire-contact-storage-slack.md)).

Each numbered file is written to be **paste-ready** after project-specific edits.

---

## Community notes

| File | Topic |
|------|--------|
| [`community/cloudflare-cache-purge-drupal-modules-slack.md`](community/cloudflare-cache-purge-drupal-modules-slack.md) | **Cloudflare** cache purge: **cloudflare** vs **purge** + **cloudflare_purge**; SDK meta [**#3572890**](https://www.drupal.org/project/cloudflare/issues/3572890) / [**#3362051**](https://www.drupal.org/project/cloudflare/issues/3362051) |
| [`community/civicrm_entity-3580224-review-nudge-slack.md`](community/civicrm_entity-3580224-review-nudge-slack.md) | **civicrm_entity** **#3580224** (multilingual **Views** autocomplete); **MR !11** / **GitHub #546**; **`QueryHooks.php`** |
| [`community/cdxgen-drupal-dependency-track-sbom.md`](community/cdxgen-drupal-dependency-track-sbom.md) | **cdxgen** / **CycloneDX** SBOM for **Drupal 10** (Composer **`composer.lock`**); **Dependency-Track** upload; **invalid schema** → **`--spec-version`** (**1.6** default vs server **1.4**/**1.5**), local **cyclonedx-cli** validate |
| [`community/drupal-packagist-theme-engine-project-type-slack.md`](community/drupal-packagist-theme-engine-project-type-slack.md) | **packages.drupal.org** / **Packagist.org**: **Theme Engine** **projects** not mirrored; **D11.3+** **`drupal-module`** + **Module** type on d.o; [**infrastructure #3587236**](https://www.drupal.org/project/infrastructure/issues/3587236) (**mjml_render_engine**); [**#3547356**](https://www.drupal.org/node/3547356) |
| [`community/drupalorg-429-fastly-rate-limit-apr2026-slack.md`](community/drupalorg-429-fastly-rate-limit-apr2026-slack.md) | **14 Apr 2026** — **429** / **54113**, **Varnish** (**HEL**); **Fastly** **rate limiting** (**Antti**); **www** vs **new**; **CI** **patch** URLs; **dimitriskr**: service **back** |
| [`community/drupalorg-cdn-timeout-redis-keys-apr2026-slack.md`](community/drupalorg-cdn-timeout-redis-keys-apr2026-slack.md) | **Apr 2026** — **d.o** **slow** / **timeouts** misread as **500**; **CDN** page **misleading**; **nnewton**: **Redis `KEYS`** on **large** instance + **roll back** infra **changes** |
| [`community/drupalorg-dashboard-assets-mime-fastly-apr2026-slack.md`](community/drupalorg-dashboard-assets-mime-fastly-apr2026-slack.md) | **Apr 2026** — **d.o** **dashboard** **unstyled**; **`/files/`** **advagg** **CSS/JS**/**images** **`text/html`** + **`nosniff`**; **WAF**/**edge** **rules** (**drumm**) |
| [`community/drupalorg-ddos-waf-git-mastodon-accounts-apr2026-slack.md`](community/drupalorg-ddos-waf-git-mastodon-accounts-apr2026-slack.md) | **Apr 2026** — **git** hook **declined**; **5xx** waves + **WAF**; **nnewton** **proxies**; **@drupalinfra** **cache**/**accounts**; **2FA** UX (**drumm**); **issue fork** **`main`** (**stBorchert**) |
| [`community/drupalorg-release-series-supported-slack.md`](community/drupalorg-release-series-supported-slack.md) | **Supported** vs **`-dev`** / beta, **`2.0.*`** series label, [project #3436596](https://www.drupal.org/project/project/issues/3436596)—**drumm** / **penyaskito** |
| [`community/drupalorg-seeking-maintainer-namespace-process-slack.md`](community/drupalorg-seeking-maintainer-namespace-process-slack.md) | **Seeking maintainer**: **no fast track**; **contact** + **wait** (**~2 weeks** in chat, **verify**); **takeover** friction; **[annotations](https://www.drupal.org/project/annotations)** |
| [`community/drupalorg-software-page-new-drupalorg-3584626-slack.md`](community/drupalorg-software-page-new-drupalorg-3584626-slack.md) | **new.drupal.org** stack on **logged-out** UI — **OK to post socially?** **dww** → **[Software](https://www.drupal.org/drupalorg/software)**; **fjgarlin** [**#3584626**](https://www.drupal.org/project/drupalorg/issues/3584626) refresh + **new** stack; **5xx**/**DDoS** thread — **mxr576**: **Mastodon** updates |
| [`community/drupalorg-usage-data-www-new-redirect-loop-slack.md`](community/drupalorg-usage-data-www-new-redirect-loop-slack.md) | **[usage_data](https://www.drupal.org/project/usage_data)**: **redirect loop** **www**↔**new**; **automation** interstitial in **incognito**; **drumm** **fixed**; **[new usage URL](https://new.drupal.org/project/usage/usage_data)** |
| [`community/dxpr-builder-28-ai-release.md`](community/dxpr-builder-28-ai-release.md) | DXPR Builder **2.8** — AI + layout; summary for newsletters, Slack, or events |
| [`community/ai-eval-how-we-test-agents-drupal-devdays-athens.md`](community/ai-eval-how-we-test-agents-drupal-devdays-athens.md) | **[ai_eval](https://www.drupal.org/project/ai_eval)** — YAML datasets + graders + **Drush** gates; model/tool-call benchmark notes; **Dev Days Athens** BoF (**Grading AI Agents: Live Testing with ai_eval**) |
| [`community/em-dash-cms-chat.md`](community/em-dash-cms-chat.md) | Lightweight chat capture (naming, April 1 context)—**not** a product review |
| [`community/frontend-early-hints-hero-images-preload-slack.md`](community/frontend-early-hints-hero-images-preload-slack.md) | **HTTP 103** / **early hints** vs **hero** / **responsive** images; [**#3563782**](https://www.drupal.org/project/drupal/issues/3563782), [**#3309016**](https://www.drupal.org/node/3309016), [**MR !14009**](https://git.drupalcode.org/project/drupal/-/merge_requests/14009); **BigPipe** / **preload** timing |
| [`community/gizmo-symfonicat-twig-c-precompute.md`](community/gizmo-symfonicat-twig-c-precompute.md) | [**gizmo**](https://github.com/symfonicat/gizmo) — **Twig** → **C** templates, **precompiled** binaries per function/params; **Drupal** angle: **Reflection** → codegen (**research / contrib experiment**, not filed work) |
| [`community/gha-ubuntu-chrome-behat-shmem-psa.md`](community/gha-ubuntu-chrome-behat-shmem-psa.md) | **GHA** Ubuntu **24.04** image bump (**Apr 2026**): **Chrome** / **Behat** failures; **`/dev/shm`**; **`--disable-dev-shm-usage`** or **`ubuntu-22.04`** |
| [`community/laravel-boost-drupal-ecosystem-slack.md`](community/laravel-boost-drupal-ecosystem-slack.md) | **Laravel Boost** praise, **Surge**, **ai_best_practices**, [AI Initiative #3541110](https://www.drupal.org/project/ai_initiative/issues/3541110)—fragmentation → puzzle pieces |
| [`community/load-testing-tools-k6-goose-slack.md`](community/load-testing-tools-k6-goose-slack.md) | **k6** (**Grafana** **k6** **Cloud** vs **OSS**), **Goose** (**Tag1**, **Rust**, **Locust**-like); **Drupal** **target**; **smaz**/**jbloomfield**/**catch** |
| [`community/mega-menu-nav-headings-a11y-slack.md`](community/mega-menu-nav-headings-a11y-slack.md) | **Mega menu**: **`h2`/`h3` in `<nav>`** — semantic headings vs “no **`h*`** outside **`<main>`**”; **MDN `<nav>`** example; avoid **`div`**-only “headings” (chat) |
| [`community/olivero-navigation-double-toggle-behaviors-slack.md`](community/olivero-navigation-double-toggle-behaviors-slack.md) | **Olivero** **`navigation-utils.js`**: **no** **`Drupal.behaviors`**/**`once`**, **double** **sticky** **menu** **bind**; **BigPipe**-era risk; **mherchel**/**ksenzee** |
| [`community/node_revision_delete-2.1.0-rc1-release.md`](community/node_revision_delete-2.1.0-rc1-release.md) | **node_revision_delete** **2.1.0-rc1** — **translation**-safe deletes, **entity query** perf in queue/batch, more **tests**; maintainer **FYI** |
| [`community/opentelemetry-1.0.0-beta7-release-context.md`](community/opentelemetry-1.0.0-beta7-release-context.md) | **OpenTelemetry** beta release — protobuf upgrade, CI unblock, log-format caveat |
| [`community/same_page_preview-d11-2.1-3.0-slack.md`](community/same_page_preview-d11-2.1-3.0-slack.md) | **same_page_preview**: **D11** dropped from **2.1.x**; **3.0.0-beta1** vs **2.1.5** / **`^10.1`**; merge-up **#3461334** |
| [`community/unpublished-node-bundle-class-slack.md`](community/unpublished-node-bundle-class-slack.md) | **`preprocess_node`** / route **`node`**: not **bundle class** — **unpublished** content; **`hook_entity_bundle_info_alter`** OK; not a **recent core** change (chat) |
| [`community/drupalorg-malicious-traffic-blocking-slack.md`](community/drupalorg-malicious-traffic-blocking-slack.md) | **Drupal.org** **flood** / **WAF**-style blocking (**red** blocked, **green** allowed); **nnewton**: **not AI scraping**, **malicious**, **~5×–20×** normal via **residential-proxy DDoS**; **drumm**: **not** **hobby bot** traffic without **paid proxy** mesh; [**Hojtsy** post](https://www.hojtsy.hu/blog/2026-apr-10/solving-small-drupal-issue-plenty-added-tests-most-basic-claude-code-setup-without); **Fastly** vs **Cloudflare** challenge (chat) |
| [`community/drupalcon-github-feedback-channel-support-slack.md`](community/drupalcon-github-feedback-channel-support-slack.md) | **DrupalCon** “qualifies?” + **GitHub** feedback — wrong channel; **Jeremy Chinquist** → **`#support`**; **sponsor** stage vs **BoF**; [**actoolsDrupal**](https://github.com/actools-pl/actoolsDrupal) |
| [`community/drupal-core-child-issues-see-docblock-autowire-contact-storage-slack.md`](community/drupal-core-child-issues-see-docblock-autowire-contact-storage-slack.md) | **smustgrave**: hold **child issues** for [**#3529510**](https://www.drupal.org/project/drupal/issues/3529510); **`@see`** [**#3578091**](https://www.drupal.org/project/drupal/issues/3578091) — **quietone**: **Twig** standards, not new **coding_standards** issue; **autowire** [**#3578361**](https://www.drupal.org/project/drupal/issues/3578361) + [**#3295751**](https://www.drupal.org/project/drupal/issues/3295751) / [**#3578374**](https://www.drupal.org/project/drupal/issues/3578374); **`contact_storage`** [**#3039906**](https://www.drupal.org/project/contact_storage/issues/3039906) — **berdir**: **uninstall validator** vs **deprecation** noise |
| [`community/drupal-core-sa-april-2026-001-002-003.md`](community/drupal-core-sa-april-2026-001-002-003.md) | **15 Apr 2026** — [**SA-CORE-2026-001**](https://www.drupal.org/sa-core-2026-001) (**Critical** XSS / dialog buttons), [**-002**](https://www.drupal.org/sa-core-2026-002) (**Moderately critical** gadget chain / deserialization hardening), [**-003**](https://www.drupal.org/sa-core-2026-003) (**Moderately critical** XSS / CKEditor 5 entity suggestions); tags **10.5.9**, **10.6.7**, **11.2.11**, **11.3.7**; **Composer** **`audit.block-insecure`** + [**Packagist**](https://packagist.org/security-advisories/) → **GitLab** composer jobs; [**gitlab_templates** `9b08ae60`](https://git.drupalcode.org/project/gitlab_templates/-/commit/9b08ae608cebc00c57d1af3271b731d2112e5651) |
| [`community/drupal-slack-ai-channel-cwg-health-reminder.md`](community/drupal-slack-ai-channel-cwg-health-reminder.md) | **`#ai`** thread: **external video** → **escalation**; **AmyJune** (**CWG** / **Community Health**); **[Values & Principles](https://www.drupal.org/about/values-and-principles#seek-first-to-understand-then-to-be-understood)** |

Use these when you need **citable paraphrases** without opening a full issue.

Screenshots for select notes live under [`assets/`](assets/).

---

## Example snippets

Illustrative only—adapt names, versions, and Selenium endpoints to your project. For **Chrome** / **`/dev/shm`** on hosted runners, see [`community/gha-ubuntu-chrome-behat-shmem-psa.md`](community/gha-ubuntu-chrome-behat-shmem-psa.md).

The blocks below map to **numbered issues** in [`issues/`](issues/) and a few [`community/`](community/) notes so you can jump from narrative to code.

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

### List entity cache tags — don’t grep only for `node_list` ([`issues/13`](issues/13-entity-list-cache-tags-core-invalidation.md))

**List** tags are built as **`{entity_type_id}_list`** (and bundle variants). Use **`EntityTypeInterface`** instead of assuming a literal **`node_list`** string. Invalidation on save runs through **`EntityBase::postSave()`**—see the issue note for pointers.

```php
<?php

declare(strict_types=1);

use Drupal\Core\Entity\EntityTypeInterface;

/** @var \Drupal\Core\Entity\EntityTypeManagerInterface $etm */
$etm = \Drupal::entityTypeManager();
$node_type = $etm->getDefinition('node');
assert($node_type instanceof EntityTypeInterface);
// Dynamic list tags for this entity type (e.g. ['node_list']).
$list_tags = $node_type->getListCacheTags();
// When debugging invalidation, start at EntityBase::postSave(), not a hard-coded tag string.
// Avoid ad-hoc Cache::invalidateTags($list_tags) unless you own the invalidation contract.
```

### Autowired route controller — optional `create()` ([`issues/14`](issues/14-drupal-core-controller-autowiring.md))

Align with the change record [**Controllers can be autowired…**](https://www.drupal.org/node/3395716) and your module’s routing. Constructor type-hints resolve from the container when the controller is registered as a service with **`autowire: true`**.

`my_module.services.yml`:

```yaml
services:
  my_module.example_controller:
    class: Drupal\my_module\Controller\ExampleController
    autowire: true
```

`my_module.routing.yml`:

```yaml
my_module.example:
  path: '/my-module/example'
  defaults:
    _title: 'Example'
    _controller: 'my_module.example_controller:build'
  requirements:
    _permission: 'access content'
```

`src/Controller/ExampleController.php` (constructor only—no `create()` when autowiring covers it):

```php
<?php

declare(strict_types=1);

namespace Drupal\my_module\Controller;

use Drupal\Core\Controller\ControllerBase;
use Drupal\Core\Datetime\DateFormatterInterface;

final class ExampleController extends ControllerBase {

  public function __construct(
    protected DateFormatterInterface $dateFormatter,
  ) {}

  public function build(): array {
    return ['#markup' => $this->t('Illustrative autowired controller.')];
  }

}
```

### Search API — tenant filter in `QUERY_PRE_EXECUTE` ([`issues/16`](issues/16-ai-rag-multi-tenancy-search-api-ragtool-3584010.md))

**Server-side** conditions belong here (e.g. **`client_id`**)—not only in whatever the LLM sends to **RagTool**. Requires **search_api**; class names match the **`search_api`** module.

```php
<?php

declare(strict_types=1);

namespace Drupal\my_module\EventSubscriber;

use Drupal\search_api\Event\QueryPreExecuteEvent;
use Drupal\search_api\Event\SearchApiEvents;
use Symfony\Component\EventDispatcher\EventSubscriberInterface;

final class TenantSearchApiSubscriber implements EventSubscriberInterface {

  public static function getSubscribedEvents(): array {
    return [
      SearchApiEvents::QUERY_PRE_EXECUTE => 'onQueryPreExecute',
    ];
  }

  public function onQueryPreExecute(QueryPreExecuteEvent $event): void {
    $query = $event->getQuery();
    // $allowed = … derive from current user / request, never trust model output alone.
    // $query->addCondition('client_id', $allowed);
  }

}
```

Register in **`my_module.services.yml`** with `tags: - { name: event_subscriber }`.

### Sync fork refs + rebase issue branch ([`issues/20`](issues/20-drupal-core-3092424-proxybuilder-fork-main-rebase.md))

When **GitLab** says **`invalid reference name 'main'`** (or your integration branch is missing on the fork), push the **canonical** ref to **`origin`**, then **rebase**. Replace **`11.x`** / **`main`** with whatever **`git ls-remote https://git.drupalcode.org/project/drupal.git`** shows.

```bash
git remote add drupal https://git.drupalcode.org/project/drupal.git 2>/dev/null || true
git fetch drupal
git push origin drupal/11.x:11.x
git checkout my-issue-branch
git rebase 11.x
git push --force-with-lease origin HEAD
```

### Image field **alt** / **title** (Scanner [#3584902](https://www.drupal.org/project/scanner/issues/3584902) — [`issues/21`](issues/21-scanner-3584902-image-field-alt-title-search.md))

Illustrates the subfields **Scanner** aims to include in search/replace flows:

```php
<?php

declare(strict_types=1);

use Drupal\node\NodeInterface;

function mymodule_collect_image_text(NodeInterface $node, string $field_name): array {
  $out = [];
  if (!$node->hasField($field_name) || $node->get($field_name)->isEmpty()) {
    return $out;
  }
  foreach ($node->get($field_name) as $item) {
    $out[] = [
      'alt' => (string) ($item->alt ?? ''),
      'title' => (string) ($item->title ?? ''),
    ];
  }
  return $out;
}
```

### Unpublished nodes vs bundle class expectations ([`community/unpublished-node-bundle-class-slack.md`](community/unpublished-node-bundle-class-slack.md))

When debugging **`getParameter('node')`** or **`$variables['node']`** type, compare **published** vs **unpublished** before assuming **`hook_entity_bundle_info_alter()`** failed:

```php
<?php

declare(strict_types=1);

$node = \Drupal::routeMatch()->getParameter('node');
if ($node instanceof \Drupal\node\NodeInterface) {
  $bundle_class = $node::class;
  $published = $node->isPublished();
  // If behaviour differs only when !$published, see the community note above.
}
```

### CycloneDX SBOM with **cdxgen** ([`community/cdxgen-drupal-dependency-track-sbom.md`](community/cdxgen-drupal-dependency-track-sbom.md))

From the **Composer project root**; **`--spec-version 1.5`** (or **`1.4`**) avoids **Dependency-Track** schema errors when the server does not accept **1.6** yet.

```bash
cd /path/to/drupal-project
npx --yes @cyclonedx/cdxgen@latest -r -o bom.json --spec-version 1.5 .
```

---

## License

If you fork this pattern for your own drafts, license your content however you like. No license is asserted here for prose you add unless you state otherwise.

---

*Built for issue queues, merge requests, and the conversations that should survive them.*
