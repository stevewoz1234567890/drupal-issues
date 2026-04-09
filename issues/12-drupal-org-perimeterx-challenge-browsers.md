# Issue: **PerimeterX** challenge blocking Drupal.org pages (Chrome / Safari)

**Project:** [Drupal.org](https://www.drupal.org/project/drupalorg) (or the appropriate infrastructure / web ops queue)  
**Component:** Bot mitigation / edge / WAF (adjust to match taxonomy)  
**Priority:** Normal

## Summary

Some users are **blocked on various Drupal.org pages** (including the **login flow** and **accounts.drupal.org**) by a **PerimeterX, Inc.** browser challenge, with **JavaScript enabled**, across **Chrome** and **Safari**, with and without VPN, and after clearing cache/cookies. This is **distinct** from the **Fastly** interstitial loop on **api.drupal.org** documented in [`07-api-drupal-org-fastly-interstitial-firefox.md`](07-api-drupal-org-fastly-interstitial-firefox.md)—different vendor, different symptoms.

## Problem

- **Symptom:** Full-page or embedded challenge from **PerimeterX**; user cannot complete normal browsing or login until the block is cleared or the challenge succeeds.
- **Scope:** Reported on **multiple pages**; **login** affected; **accounts.drupal.org** may show the same behavior. **Press & hold** (when offered) may still return **“Please try again.”**
- **Browsers:** **Chrome** and **Safari** both reported; one thread noted **Safari** eventually working via **accounts.drupal.org** with **press & hold** while **Chrome** remained blocked—patterns can diverge by profile, extensions, and session state.
- **False starts:** **Ad blockers** and **content blockers** can interfere; community guidance includes checking those. **Logging in** may avoid the challenge for some paths once a session is established—but not always when the login page itself is blocked.

## Information useful for operators (from thread)

- **Reference ID:** Users see a **Reference ID** (UUID-style) on the block page. **Staff need that ID** to find and clear the corresponding event in **logs**. IDs may **not appear in logs immediately**—sometimes **a few minutes** delay.
- **Clearing blocks:** When staff **clear** a block for a given ID, the user may immediately hit a **new** block with a **new Reference ID** (especially if they **cleared cookies/session** in between—creating a new client story). Advice from operators: **avoid clearing session/cookies** while iterating with support, because it can **mint a new ID** and complicate log correlation.
- **Contact:** Use normal **Drupal.org infrastructure / abuse** support paths (e.g. **help@drupal.org** or the channel your team designates)—include **Reference ID**, **browser + version**, **approximate time**, and **whether VPN** was in use.

## Proposed resolution

1. **Operations:** Confirm **PerimeterX** tuning and false-positive handling when **legitimate humans** are blocked on **login** and **accounts** flows; reduce **whack-a-mole** cycles (clear ID → new ID) where configuration allows.
2. **User-facing:** If stable, add a short **FAQ or status** note (or extend existing bot-mitigation messaging) so contributors know to **capture Reference ID** and **not churn cookies** mid-triage.
3. **Differentiate incidents:** Keep **PerimeterX** reports separate from **Fastly** `/_fs-ch` / **api.d.o** threads to avoid mixing remediation steps.

## References

- Community Slack thread (paraphrase): **PerimeterX** on Drupal.org; **Chrome** / **Safari**; **login** and **accounts.drupal.org**; **JS** on; VPN/cache/cookies trials; **fjgarlin** — try **login** to skip challenge where possible, check **blockers**; **Reference IDs** **#195330cf-3409-11f1-b313-7dcd5b6213c5** and later **#ed19a3f3-340a-11f1-9d86-ea5654e01ffa**; delays until IDs **show in logs**; staff **cleared** blocks when visible; **don’t clear cookies** while support is correlating IDs; reporter eventually **able to login**.
