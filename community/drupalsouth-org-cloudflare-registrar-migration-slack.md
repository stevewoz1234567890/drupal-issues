# drupalsouth.org — **Cloudflare “registrar suspended / ToS”** interstitial during migration (Slack)

**Context:** During a **planned migration**, **drupalsouth.org** briefly showed a **Cloudflare** error page whose wording suggested **registrar** problems or a **Terms of Service** action. Organizers and community clarified that the **underlying issue was migration-related** and that the **copy was more alarming than the situation**—the **domain** had effectively **“gone walkabout”** before being **recovered** the same evening.

**Thread:** **“Any help needed?”** (Slack) · screenshot referenced as **4624.png**

## What people saw

| Observation | Who / note |
|-------------|------------|
| **Event URL** (example) not loading: `https://drupalsouth.org/events/drupalsouth-wellington-2026` | — |
| **Cloudflare** page stating that **“The registrar services for this domain have been suspended by Cloudflare for a Terms of Service violation”** (or equivalent registrar / ToS framing) | Screenshot in thread |
| **Site had worked** within about **~15 minutes** of an earlier check | **pameeela** — surprising regression |

## What organizers said (in thread)

| Message | Who |
|---------|-----|
| **Planned migration**; the **error text made the situation look worse** than it was | **richo** |
| **Should be working again** (later that evening) | **p_stampy** |
| **“Domain went walkabout. We caught it in the end. Thanks all.”** | **VladimirAus** |

**Ping** for attention: **Karl** → **@VladimirAus**.

## Use

**Incident note** for **event / camp sites** on **Cloudflare** during **DNS or registrar / migration** work: **edge error pages** may use **stock “suspension / ToS”** language that does **not** match a **benign** cutover. For **attendees and social**, pair **status updates** (or a short post) with the fix so **alarming** interim pages do not spread out of context.

**Related theme (Drupal.org):** **CDN**/**edge** error pages that read **worse** than the operational reality — see [`drupalorg-cdn-timeout-redis-keys-apr2026-slack.md`](drupalorg-cdn-timeout-redis-keys-apr2026-slack.md) (misleading vs root cause).
