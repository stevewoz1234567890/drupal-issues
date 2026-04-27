# Drupal.org project logo — `git.drupalcode.org/.../-/avatar` load failure (Apr 2026)

**Context:** **stBorchert** reported that the **repository logo** on **www.drupal.org** project pages did not load. The **`<img>`** points at **GitLab** (`…/project/NAME/-/avatar`), not a **d.o**-proxied file. **Example:** [twig_tweak](https://www.drupal.org/project/twig_tweak) → `https://git.drupalcode.org/project/twig_tweak/-/avatar`. **fjgarlin** clarified wording (“repository logo”), raised with **infra**.

| Who | Note |
|-----|------|
| **fjgarlin** | Cross-linked [**#drupal-infrastructure**](https://drupal.slack.com/archives/C51GNJG91/p1776700179527269) — same period as expanded **proof-of-work** / **edge**-**challenge** tuning (report unexpected blocks, including legitimate automation). |
| **drumm** | *That should be fixed now.* |
| **stBorchert** | Thanks. |

## Use

- **d.o** pages that hot-link **git.d.o** avatars inherit **GitLab** **edge** / **WAF** / **bot** behavior — not only **GraphQL** / **API** traffic. See also [`git-drupalcode-org-slow-503-timeouts-apr2026-slack.md`](git-drupalcode-org-slow-503-timeouts-apr2026-slack.md).
