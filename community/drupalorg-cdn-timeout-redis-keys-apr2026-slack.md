# Drupal.org — **slow pages**, **timeouts vs “500””**, **Redis `KEYS`** (**Apr 2026**)

**Context:** Informal **Drupal Slack** thread (**#drupal-infrastructure** family; exact date not preserved in the capture). **Not** an official incident postmortem.

## What people saw

- **Very slow** page loads (on the order of **~20 seconds** to open an **issue** link).
- **Intermittent failures** while doing **bulk work** (e.g. **closing D7 issues**): started **slow**, then **errors**; pacing work reduced failures (**japerry**).
- **`/admin/content?status=0`** — **greggles**: **5xx**, then **refresh succeeded**.
- **Sporadic errors on node edits** — **xjm** (via **greggles**): often **cleared on retry**.

## What infra said (nnewton)

- Early read: **nothing ongoing**, **slowness not reproduced**, **no** matching **logged 500** volume — **regional network** suggested as one hypothesis when another similar report appeared.
- **Reproduction found** shortly after.
- **Timeouts at the CDN**, **not** true **application 500** storms: the **CDN maintenance / error page can read like a 500** after a **long wait**, which matches a **timeout** pattern (**greggles** concurred).
- **Mitigation in flight:** **scale** to get past the spike; **possibly replace object cache** again until **fabian** can supply a **new patch** — **intermittent** behaviour made it hard to trace without reports.
- **Root cause (later same thread):** tied to **changes the previous day**; **rolled some back**. Under the hood: **`KEYS`** against a **large Redis** instance **locking it up** (“in essence”).

## Takeaways for contributors

- When **d.o** “**500**” after **tens of seconds**, capture **time**, **URL**, and **headers** — it may be a **timeout / edge** path rather than PHP fatals.
- **Retries** sometimes succeed because the failure is **load / cache / edge** shaped, not deterministic app logic.

## Related notes

- **Apr 2026** **429** / **Fastly** rate limiting — [`drupalorg-429-fastly-rate-limit-apr2026-slack.md`](drupalorg-429-fastly-rate-limit-apr2026-slack.md).  
- **DDoS / git / WAF / Mastodon** window — [`drupalorg-ddos-waf-git-mastodon-accounts-apr2026-slack.md`](drupalorg-ddos-waf-git-mastodon-accounts-apr2026-slack.md).  
- **Public status** / comms expectations — [`../issues/18-drupal-org-public-status-page-infrastructure-3372242.md`](../issues/18-drupal-org-public-status-page-infrastructure-3372242.md).

## Use

Explaining **perceived 500** vs **CDN timeout**, **Redis `KEYS`** risk on **large** instances, and why **Drupal.org** can feel **fragile** during **infra changes** even when **error logs** look quiet.
