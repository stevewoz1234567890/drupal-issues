# Drupal core — April 2026 security window (**SA-CORE-2026-001** … **-003**)

**Date (Security Team advisories):** 15 April 2026  
**Project:** [Drupal core](https://www.drupal.org/project/drupal)  
**Risk scale (how Drupal scores advisories):** [Security risk levels](https://www.drupal.org/security-team/risk-levels)

## Advisories (read the canonical pages)

| ID | Severity (d.o) | Topic | Official page |
|----|----------------|-------|---------------|
| **SA-CORE-2026-001** | **Critical** | **Cross-site scripting (XSS)** — insufficient handling of user-influenced data on **AJAX modal / dialog** button options (`OpenDialogCommand`); mitigated by **restricting allowed button keys** and **filtering string values** before the command is rendered. | [SA-CORE-2026-001](https://www.drupal.org/sa-core-2026-001) |
| **SA-CORE-2026-002** | **Moderately critical** | **Gadget chain / unsafe deserialization hardening** — tightens **`ViewExecutable` unserialization** (expected shape of serialized state) and **`Attribute::__toString()`** so non-attribute values cannot be rendered through that path. Exploitability is framed as **chaining** with **other** weaknesses (see advisory text). | [SA-CORE-2026-002](https://www.drupal.org/sa-core-2026-002) |
| **SA-CORE-2026-003** | **Moderately critical** | **Stored XSS** — **CKEditor 5** “complete entity suggestions” for internal links (feature in **Drupal 11.3+**): suggestion **labels** were not escaped for use in JSON/HTML contexts; fixed by escaping the entity **label** in **`EntityLinkSuggestionsController`**. | [SA-CORE-2026-003](https://www.drupal.org/sa-core-2026-003) |

Authentication / complexity nuances (anonymous vs admin vs authenticated) belong in each advisory’s risk breakdown—**do not rely on this table alone** for severity.

## Patched core versions (same security release batch)

These tags exist on the **[drupal/drupal](https://github.com/drupal/drupal)** mirror and correspond to the **15 April 2026** security releases:

- **10.5.9**, **10.6.7**, **11.2.11**, **11.3.7**

**Branch reality:** **SA-CORE-2026-003** touches code that exists on the **11.3** line (CKEditor 5 entity link suggestions); older supported branches still pick up **-001** and **-002** in their own tags—confirm **affected / fixed version lists** on each SA page and on **[Drupal core releases](https://www.drupal.org/project/drupal/releases)**.

## Composer `audit`, Packagist, and GitLab CI (why pipelines “broke” overnight)

After the advisories above were published, **Packagist** began advertising **Drupal core** versions **older than the security tags** as affected by **`SA-CORE-2026-001`** … **`-003`**. **Composer 2.7+** applies **version blocking** when **`audit.block-insecure`** is **`true`** (the default): resolver passes **discard** insecure versions **before** solving the graph, so **`composer update`** / **`composer install`** can fail even when **`composer.json` did not change**.

Typical log shape (paraphrased from contrib **GitLab CI** jobs):

```text
No composer.lock file present. Updating dependencies to latest instead of installing from lock file.
…
Your requirements could not be resolved to an installable set of packages.
  Problem 1
    - Root composer.json requires drupal/core-recommended 11.3.6 -> satisfiable by drupal/core-recommended[11.3.6].
    - drupal/core-recommended 11.3.6 requires drupal/core 11.3.6 -> found drupal/core[11.3.6] but these were not loaded,
      because they are affected by security advisories ("SA-CORE-2026-001", "SA-CORE-2026-003", "SA-CORE-2026-002").
      Go to https://packagist.org/security-advisories/ …
```

**This is Composer’s security behaviour**, not a random **GitLab** outage—community triage: [**#drupal-infrastructure** thread](https://drupal.slack.com/archives/C51GNJG91/p1776284936514579) (**cmlara**, **godotislate**, **fjgarlin**).

### What to do (in order of preference)

1. **Upgrade constraints** to the **patched** **`drupal/core-recommended` / `drupal/core`** lines for your supported branch (see **Patched core versions** above), run **`composer update`**, and **commit** the resulting **`composer.lock`** so CI installs from a **known-good** lock.
2. **Align CI templates** with **[`gitlab_templates`](https://www.drupal.org/project/gitlab_templates)** on **GitLab**—upstream adjusted hidden CI variables for the **15 April 2026** security window; see commit [**`9b08ae608cebc00c57d1af3271b731d2112e5651`**](https://git.drupalcode.org/project/gitlab_templates/-/commit/9b08ae608cebc00c57d1af3271b731d2112e5651) (*“Edit `include.drupalci.hidden-variables.yml` for the April 15, 2026 security releases…”* linking the three SAs). **fjgarlin** noted the fix was **rolled out to contrib** after that landed.
3. **Last resort / exceptional cases only:** relax blocking via **`composer.json`** **`audit`** (e.g. per-advisory **`ignore`**, or **`block-insecure`: `false`**) — see **[Composer config: `audit`](https://getcomposer.org/doc/06-config.md#audit)**. Prefer **updating core**, not silencing advisories.

**Why “it works in DDEV”:** often a **newer Composer**, a **different** **`composer.lock`**, or **cached** **`vendor/`** locally—compare **`composer --version`**, lock presence, and CI **artifacts**.

## Use

Paste into **Slack**, **status/incident** notes, **GitLab CI** triage, or **customer comms** when you need a **single memo** for the **three SAs**, **Composer / tarball** upgrade targets, and **Packagist-driven CI** failures—this file is **not** a Drupal.org issue template (see [`issues/`](../issues/) for those). For **CVE IDs** and **CVSS**, use the **published advisory** and your **scanner vendor** once they have caught up.
