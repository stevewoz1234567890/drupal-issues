# Drupal.org — **429 Too Many Requests** (**54113**), **Varnish** / **Fastly** rate limiting (**Apr 2026**)

**Context:** Informal **Drupal Slack** thread (**14 Apr 2026**). Multiple reporters; **not** an official incident postmortem.

## What people saw

- **HTTP 429** — *Too Many Requests*, with **Error 54113** and a **Varnish cache server** line (example identifier in thread: **`cache-hel1410027-HEL`** — **Helsinki**-style edge naming).
- Browsers (**Chrome**, mobile) on ordinary page loads to **Drupal.org**.
- **fjgarlin** asked for **URL**, **time**, **headers**, and **screenshots** to triage.

## Scope (chat consensus)

- **dimitriskr**, **Prafful Nagwani:** Reproduced across **many** **d.o** URLs.
- **Rajab Natshah:** Example **`https://www.drupal.org/project/drupal`**.
- **Antti:** Described as **Fastly rate limiting** (edge policy), not application logic.
- **Rajab** (refined): Failures clustered on the **legacy** **`https://drupal.org` / `https://www.drupal.org`** host; **`https://new.drupal.org/`** seemed **less** affected in their checks (**edited** in thread).

## Downstream impact

- **dpi:** **CI** jobs **failing** because **patches** (or other assets) were **not reachable** from **d.o** during the window.

## Resolution signal

- **dimitriskr:** After the spike, service **“seems it’s back”** (informal recovery note in thread).

## Related notes

- **Same window (Apr 2026):** **git** hook declines, **WAF** work, **@drupalinfra** posts, **accounts.d.o** upgrade, **2FA** UX — [`drupalorg-ddos-waf-git-mastodon-accounts-apr2026-slack.md`](drupalorg-ddos-waf-git-mastodon-accounts-apr2026-slack.md).  
- Broader **flood** / **DDoS** / **edge** discussion — [`drupalorg-malicious-traffic-blocking-slack.md`](drupalorg-malicious-traffic-blocking-slack.md).  
- **Public status** / comms expectations — [`../issues/18-drupal-org-public-status-page-infrastructure-3372242.md`](../issues/18-drupal-org-public-status-page-infrastructure-3372242.md), [`drupalorg-software-page-new-drupalorg-3584626-slack.md`](drupalorg-software-page-new-drupalorg-3584626-slack.md) (**Mastodon** / **@drupalinfra**).

## Use

Explaining **429** + **54113** during **edge rate-limit** events; **CI** flake when **patch** URLs return **429**; **www** vs **new** behaviour during stress.
