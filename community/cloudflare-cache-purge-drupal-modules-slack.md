# Cloudflare cache purging — Drupal modules (community thread)

**Context:** Informal Drupal chat (Slack-style). Names and handles as in the original messages.

## Question

What **Drupal module** to use for **purging Cloudflare** assets? The [**cloudflare**](https://www.drupal.org/project/cloudflare) project looks like the obvious fit, but it still lacks a **stable** (security-supported) release, and the queue documents a structural problem: the **Cloudflare PHP SDK** is **no longer maintained**, so the module needs to move to **direct API** use—see [**#3572890**](https://www.drupal.org/project/cloudflare/issues/3572890) (*Cloudflare SDK is abandoned. We need a new plan.*) and related work such as [**#3362051**](https://www.drupal.org/project/cloudflare/issues/3362051) (remove SDK dependency). Other contrib options often show **very low install counts**, which makes choosing harder.

## Thread (paraphrased)

- **RoSk0** (maintainer, **cloudflare**): As far as they know, **that module is still the main option**. It **works**, and it is **slowly moving** toward a better future (SDK → APIs). **Help is welcome.** They speak as a maintainer.
- **pameeela:** They **used it** before switching to **Fastly**; it worked for them even **without** a stable release.
- **darvanen:** That module **integrates with [purge](https://www.drupal.org/project/purge)**—**purge** is what they would lean on architecturally.
- **Stew West:** Same line of thinking, and they point to [**cloudflare_purge**](https://www.drupal.org/project/cloudflare_purge).

## Links (canonical)

| Resource | URL |
|----------|-----|
| **cloudflare** (contrib) | https://www.drupal.org/project/cloudflare |
| Meta: SDK abandoned / new plan | https://www.drupal.org/project/cloudflare/issues/3572890 |
| Meta: remove SDK dependency | https://www.drupal.org/project/cloudflare/issues/3362051 |
| **purge** (cache invalidation framework) | https://www.drupal.org/project/purge |
| **cloudflare_purge** (Guzzle + Cloudflare Purge API; optional cache-tag automation) | https://www.drupal.org/project/cloudflare_purge |

## Use

When someone asks **“which module purges Cloudflare?”**: summarize **tradeoffs** (stable release / security coverage vs real-world use), link the **SDK meta issues**, and distinguish **cloudflare** + **purge** integration from standalone **cloudflare_purge** (direct v4 API, documented on the project page). This file is **not** a Drupal.org issue template (see `issues/` for those).
