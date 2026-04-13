# Public **Drupal.org** status / incident visibility — third-party status page

**Project:** [Drupal.org infrastructure](https://www.drupal.org/project/infrastructure) (`infrastructure`)  
**Related:** [**#3372242**](https://www.drupal.org/project/infrastructure/issues/3372242) — follow, comment, or revive rather than opening a duplicate unless the queue needs a **fresh** meta issue.  
**Component:** Operations / communications (adjust per queue)  
**Priority:** Normal

## Summary

There is **no** dedicated, vendor-style **public status page** for **Drupal.org** today. Contributors often learn about outages by **hitting errors** (e.g. **500**), **refreshing**, then checking **Slack** ([**#drupal-infrastructure**](https://drupal.slack.com/archives/C51GNJG91)) or [**@drupalinfra** on Mastodon](https://mastodon.social/@drupalinfra)—which may **lag** an active incident while staff are **fixing** the platform first.

Community expectation (especially from **enterprise**-adjacent users): many **SaaS** and **open** ecosystems expose a **single** URL for **availability / incidents** (compare e.g. **WordPress**’s public status story). **Manual** social posts are **not** a substitute for a **subscribed** incident feed for everyone who does **not** live in Slack.

## Problem / opportunity

- **Discoverability:** During **drupal.org** errors, there is **no** first-party place to confirm “**known incident**” vs “**local** / **client** problem.”
- **Trust and noise:** Repeated **refresh** and **guesswork** waste time; **silent** windows feel worse than **acknowledged** degradation.
- **Resource reality:** The **Association** does **not** run a **24/7 SRE** bench; **on-call** staff may be **few** and **busy remediating** before **comms** go out—any solution should stay **lightweight** and **honest** about coverage.

## Current channels (as of community chat)

- **Slack:** **#drupal-infrastructure** — best **real-time** signal for those already in Slack.
- **Mastodon:** [**@drupalinfra**](https://mastodon.social/@drupalinfra) — public, but not a **structured** uptime/history page.
- **Existing issue:** [**#3372242**](https://www.drupal.org/project/infrastructure/issues/3372242) — **penyaskito** pointed here as the **canonical** d.o. thread for this topic.

## Proposed resolution

1. **Confirm** with **infrastructure** maintainers whether [**#3372242**](https://www.drupal.org/project/infrastructure/issues/3372242) remains the right **home**; if **stale**, **summarize** scope in a **new** issue and **cross-link**.
2. **Evaluate** a **free** or **low-cost** **third-party status** product (or **self-hosted** minimal page) that staff can update **quickly** during incidents and leave **historical** entries for **postmortems**.
3. **Surface** the URL during incidents: e.g. **banner** on **drupal.org**, **footer** link, or a **single** “**Status**” page that lists **official** channels (**Mastodon**, **Slack** invite note, **help@**).
4. **Set expectations:** Document that **status** reflects **public-facing** services staff choose to scope—not a **full** internal observability dashboard.

## References

- Slack thread: “Does drupal.org have a third-party status page?” — **penyaskito** (channels + **#3372242**), **duckydan** (enterprise / **WordPress** comparison, **500** UX), **drumm** (staff **incident** response).
- Mastodon: [Drupal Infra (@drupalinfra@mastodon.social)](https://mastodon.social/@drupalinfra).
- Drupal.org: [infrastructure **#3372242**](https://www.drupal.org/project/infrastructure/issues/3372242).
