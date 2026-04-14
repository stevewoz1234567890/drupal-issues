# Drupal.org — **`usage_data`** project page redirect loop (**www** ↔ **new**) (Slack)

**Context:** Contributors could not load the **[usage_data](https://www.drupal.org/project/usage_data)** project on **`www.drupal.org`**: browser reported **“The page isn’t redirecting properly”** — an **infinite redirect** between **`www.drupal.org`** and **`new.drupal.org`**. Thread timing aligns with **usage** UI living on **`new.drupal.org`** (e.g. [project usage for `usage_data`](https://new.drupal.org/project/usage/usage_data)).

## What people saw

| Observation | Who / note |
|---------------|------------|
| **Redirect loop** on `https://www.drupal.org/project/usage_data` | Multiple reporters |
| **Worked** when **logged in** on **both** `drupal.org` and **`new.drupal.org`** | **FeyP** (hypothesis: session / cookie path) |
| **Incognito:** **“blocked … automation tools”** (bot / WAF-style interstitial), then **hold-to-continue** led **back** to **redirect loop** | **kpaxman** — overlaps thematically with **PerimeterX** / edge challenges (see [`12-drupal-org-perimeterx-challenge-browsers.md`](../issues/12-drupal-org-perimeterx-challenge-browsers.md)) |

## Resolution (in thread)

- **drumm:** **Misconfiguration** — **“Fixed now, sorry for the misconfiguration.”**
- **kpaxman:** **Confirmed** fixed.

## Follow-on (contrib maintainer)

- **bryan:** Suspected tie to **moving usage** to **`new.drupal.org`**; **[usage_data](https://www.drupal.org/project/usage_data)** maintainers were **blocked from release** work (**Drupal 11** update) while the project URL was unusable for some.

## URLs (reference)

| Surface | URL |
|---------|-----|
| **Project** (canonical `www`) | https://www.drupal.org/project/usage_data |
| **Usage** on **`new`** (chat example) | https://new.drupal.org/project/usage/usage_data |

## Use

**Incident note** for **Apr 2026**-era **Drupal.org** routing between **`www`** and **`new`**; **staff** corrected config **same day** in Slack. If loops return, compare **logged-in vs anonymous**, **cookies**, and **#drupal-infrastructure** — and capture **HAR** / **Reference ID** if a **challenge** page appears (see PerimeterX note above).
