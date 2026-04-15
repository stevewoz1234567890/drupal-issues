# Drupal.org — **Apr 2026** DDoS wave: **git** hooks, **WAF** / backend work, **Mastodon**, **accounts.d.o** upgrade, **2FA** login UX (Slack)

**Context:** Informal **Drupal Slack** (**infra** / community), **14–15 Apr 2026**. Paraphrase for triage and contributor expectations—not a DA postmortem.

**Related:** Same stress window as **429** / edge limits — [`drupalorg-429-fastly-rate-limit-apr2026-slack.md`](drupalorg-429-fastly-rate-limit-apr2026-slack.md); broader **flood** narrative — [`drupalorg-malicious-traffic-blocking-slack.md`](drupalorg-malicious-traffic-blocking-slack.md).

## **Git** push blocked — “Unable to contact Drupal.org”

Pushes to **`git.drupal.org`** failed with a **pre-receive hook** decline, e.g.:

```text
remote: Unable to contact Drupal.org, please try again soon
remote: error: hook declined to update refs/heads/2.0.x
 ! [remote rejected] 2.0.x -> 2.0.x (hook declined)
```

- **fjgarlin:** Treated as **the same incident family** as **web** / **edge** instability (**“It’s all related”**).

## **5xx** returns and **attack** cadence

- **drumm:** Situation **tentatively** stable; team still seeking **more durable** mitigations.
- **godotislate**, **b_man**, **Natalie Cainaru:** **5xx** on **`https://www.drupal.org/`** returned; **b_man** described **“limit testing waves”** and confirmed staff **aware** and **mitigating**.

## **WAF** + backend changes — planned instability

- **nnewton:** **Morning** (**US-oriented**; see **Timezones** below) could include **change-related** instability while **WAF** rules and **backend** changes roll out; later gave short **“next 10 min”** heads-up, then **“Complete, thanks”**.
- **nicxvan:** Asked whether attackers are identifiable.
- **nnewton:** **No** identifying information; traffic from **hundreds of thousands** of **IPs** via **residential proxies** globally. One wave **resembled** a **prior** pattern hitting **groups**—**personal assumption** of similarity, **not** proof.

## Team **timezones** (for “this morning”)

- **hestenet:** **Narayan**, **Max** (**Tag1**), and **hestenet** — **Pacific**; **Fran** — **Spain**; **Neil** — **US East**; **Brendan** — **US West** but often **East-coast hours**. Changes may land over **hours**, plus **Fastly** support dependency.
- **penyaskito** / **nnewton:** Clarified **“this morning”** was **not** “right now” for **penyaskito**’s ping—**timezone** / **phrasing** mix-up; thread thanked staff (**no 24/7** expectation).

## **Mastodon** (@drupalinfra) — caching + **where to report**

- **b_man** shared a **@drupalinfra** post: **caching** changes to **reduce DDoS impact**, **monitoring** continues — [Mastodon (caching / DDoS)](https://mastodon.social/@drupalinfra/116404651816856735).
- **drumm:** Because changes touch **caching**, subtle regressions are possible—report with **detail** on the [**infrastructure** project](https://www.drupal.org/project/infrastructure).

## **accounts.drupal.org** maintenance (**15 Apr 2026**)

**drumm** linked **@drupalinfra** for the **upgrade** window (**scheduled**, **in progress**, **complete**):

- [Upgrade notice (~2h)](https://mastodon.social/@drupalinfra/116408283787742681) — **13:00 UTC**, up to **~1 h** unavailable; **existing sessions** not interrupted; **new sign-ins** / some **account updates** affected.
- [In progress](https://mastodon.social/@drupalinfra/116408912433846716)
- [Complete](https://mastodon.social/@drupalinfra/116409084651611421)

## **2FA** UI after **accounts** upgrade (**drumm**, pinned note)

After upgrade, login sometimes surfaced **recovery codes** before the usual **device** second factor. **Mitigation:**

- Use **“Try another way”** to reach **device** authentication.
- Under the hood, the UI shows the **first-configured** method first—not a policy change.
- Optional cleanup: [**Signing in** security settings](https://accounts.drupal.org/auth/realms/main/account/account-security/signing-in) — remove / reset **recovery codes** if you want the form to prefer another method.

## **Issue fork** — **`main`** missing (**stBorchert**)

**stBorchert** could not create a branch from **`main`** on an **issue fork** ([**`drupal-3376163`**](https://git.drupalcode.org/issue/drupal-3376163) for [**#3376163**](https://www.drupal.org/project/drupal/issues/3376163)) because **`main`** was **absent**. Same class of problem as **personal forks** without upstream default refs — use **`git ls-remote`** on **canonical** **`drupal`**, push the needed integration branch (**`11.x`**, **`main`**, etc.) to the **fork**, or branch from the ref that **exists** on the fork. See draft [`../issues/20-drupal-core-3092424-proxybuilder-fork-main-rebase.md`](../issues/20-drupal-core-3092424-proxybuilder-fork-main-rebase.md).

## Use

When **git push** fails with **hook declined** during **d.o** incidents; when **5xx** **return** during **WAF** work; for **@drupalinfra** **Mastodon** pointers; **accounts** maintenance; **2FA** **recovery-code-first** confusion; **issue forks** without **`main`**.
