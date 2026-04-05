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

This repository is a **public workflow**: versioned narratives, cross-linked topics, and a single index you can open when someone asks, *“What did we agree about mcp_server?”*, *“What was the Fastly / Firefox story on api.drupal.org?”*, *“Why does everyone want a Drupal Laravel Boost?”*, or *“Why is my 2.x series not marked Supported on Drupal.org?”*

It is **not** an official Drupal Association project—it's a disciplined notebook that happens to read like a **map of how serious Drupal practitioners think**.

---

## Why this matters if you hire Drupal developers

Organizations rarely see *how* their partners work upstream. This repo is a window into habits that separate **maintenance mode** from **platform partnership**:

| Signal | What you see here |
|--------|-------------------|
| **Upstream citizenship** | Issue text drafted for real project queues—respectful tone, reproducible problems, concrete next steps. |
| **Modern Drupal + AI** | Active tracking of **MCP** consolidation (**mcp_server**, **mcp_remote**), **AI providers** positioning, **agent tooling**, **Surge** / **Boost-shaped** DX, and the **AI Best Practices** initiative—not buzzwords, filed work. |
| **Operational realism** | Notes on **Drupal.org infrastructure** (CDN / browser edge cases, GitLab maintenance, change-record workflow) because production sites depend on that glue. |
| **Release literacy** | Community-sourced context (e.g. **OpenTelemetry** semver tradeoffs, security-driven releases) that informs upgrade planning. |

If you need **Drupal 10/11**, **contrib architecture**, **OAuth and API integrations**, **observability**, or **AI-assisted development done responsibly**, maintainers who **write issues before they rant** are the ones who **reduce your risk**.

---

## Start here

| Location | Purpose |
|----------|---------|
| [`issues/INDEX.md`](issues/INDEX.md) | Master table: target project, filename, one-line intent, and encoded chat takeaways |
| [`issues/`](issues/) | Numbered drafts (`01-…` through `10-…`)—retitle, set component/priority, add `@mentions`, then file |
| [`community/`](community/) | Short-lived or multi-project context: releases, ecosystem news, chat paraphrases—not always one issue |

**Before filing on Drupal.org:** align with each project's taxonomy, link real user profiles, and strip anything that was only for your own notes.

---

## Issue drafts at a glance

Themes covered in [`issues/INDEX.md`](issues/INDEX.md) (full list and links live there):

- **MCP & agents** — `mcp_server` accuracy and E2E testing, `mcp_remote` deprecation path, `ai_agents_canvas_direct_edit` migration, contribution coordination after sponsorship.
- **AI module landscape** — `ai_providers_api` positioning, contributor expectations, and documentation gaps vs the **AI Best Practices** / Agent Skills effort (**Claude Code**, **OpenCode**). Community map: **Laravel Boost** comparisons → **Surge**, [AI Initiative #3541110](https://www.drupal.org/project/ai_initiative/issues/3541110), **ai_best_practices** (see [`community/laravel-boost-drupal-ecosystem-slack.md`](community/laravel-boost-drupal-ecosystem-slack.md)).
- **Drupal.org & tooling** — `api.drupal.org` / Fastly interstitial behavior (e.g. Firefox), duplicate change records, `git.drupalcode.org` maintenance windows, **release series** / **Supported** checkbox semantics ([`community/drupalorg-release-series-supported-slack.md`](community/drupalorg-release-series-supported-slack.md), [infrastructure #3436596](https://www.drupal.org/project/project/issues/3436596)).

Each numbered file is written to be **paste-ready** after project-specific edits.

---

## Community notes

| File | Topic |
|------|--------|
| [`community/dxpr-builder-28-ai-release.md`](community/dxpr-builder-28-ai-release.md) | DXPR Builder **2.8** — AI + layout; summary for newsletters, Slack, or events |
| [`community/opentelemetry-1.0.0-beta7-release-context.md`](community/opentelemetry-1.0.0-beta7-release-context.md) | **OpenTelemetry** beta release — protobuf upgrade, CI unblock, log-format caveat |
| [`community/em-dash-cms-chat.md`](community/em-dash-cms-chat.md) | Lightweight chat capture (naming, April 1 context)—**not** a product review |
| [`community/laravel-boost-drupal-ecosystem-slack.md`](community/laravel-boost-drupal-ecosystem-slack.md) | **Laravel Boost** praise, **Surge**, **ai_best_practices**, [AI Initiative #3541110](https://www.drupal.org/project/ai_initiative/issues/3541110)—fragmentation → puzzle pieces |
| [`community/drupalorg-release-series-supported-slack.md`](community/drupalorg-release-series-supported-slack.md) | **Supported** vs **`-dev`** / beta, **`2.0.*`** series label, [project #3436596](https://www.drupal.org/project/project/issues/3436596)—**drumm** / **penyaskito** |

Use these when you need **citable paraphrases** without opening a full issue.

Screenshots for select notes live under [`assets/`](assets/).

---

## License

If you fork this pattern for your own drafts, license your content however you like. No license is asserted here for prose you add unless you state otherwise.

---

*Built for issue queues, merge requests, and the conversations that should survive them.*
