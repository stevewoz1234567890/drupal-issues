# same_page_preview — Drupal 11 support, 2.1.x vs 3.0.x (community Slack)

**Context:** Drupal Slack thread about **[same_page_preview](https://www.drupal.org/project/same_page_preview)** branching and **Drupal 11** support after recent **2.1.x** releases.

## Thread (paraphrased)

- **Thread opener:** The latest **2.1.x** release **removed support for Drupal 11**, but they are **not seeing an error report** on the project (for maintainers and users to track intent and migration). They suggest it might be **better to bump the 10.x branch `core_version_requirement` to `^10.3`** (or similar) **instead of removing D11 support** from that line of releases—depending on maintainer goals for semver and supported cores.

- **Same opener:** The **3.0.x** branch **appears to be missing** some **bug fixes** that landed elsewhere—example commit: [`ceac745c`](https://git.drupalcode.org/project/same_page_preview/-/commit/ceac745c6c2c0997b25ea2f561d474647ef4e0bd) (**Issue [#3461334](https://www.drupal.org/project/same_page_preview/issues/3461334)** — parameter passed to `samePagePreviewRenderPreview` should be the entity **UUID**). Worth verifying **merge-up / cherry-pick** status on **3.0.x**.

- **sokru:** **[`3.0.0-beta1`](https://git.drupalcode.org/project/same_page_preview/-/tags/3.0.0-beta1)** **looks effectively the same** as **[`2.1.5`](https://git.drupalcode.org/project/same_page_preview/-/tags/2.1.5)** — i.e. **there is still no tagged release that clearly targets Drupal 11** for adopters who were pointed at **3.0.x**. They linked [`same_page_preview.info.yml` on the `3.0.0-beta1` tag](https://git.drupalcode.org/project/same_page_preview/-/blob/3.0.0-beta1/same_page_preview.info.yml?ref_type=tags): at that tag, **`core_version_requirement` remains `^10.1`**, not `^10 || ^11` (or similar). **Interpretation:** **D11** users still lack a **stable (or clearly labeled) 3.x** artifact on Drupal.org that matches the “D11 lives on 3.0.x” story unless constraints and releases are updated in lockstep.

## Maintainer-facing checklist (neutral)

| Topic | Question to resolve on the issue queue |
|--------|----------------------------------------|
| **Communication** | Was **D11 removal** from **2.1.x** documented in a **change record**, **release notes**, and/or a **dedicated issue** so sites on **D11 + same_page_preview** know to move to **3.0.x** and when? |
| **2.1.x vs 10.3** | Does tightening **Drupal 10** to **`^10.3`** (if required by code) satisfy support policy **without** surprising **D11** installs on the **2.1** series? |
| **3.0.x completeness** | Are fixes such as **#3461334** / **`ceac745c`** present on **3.0.x**? Any other **2.1.x-only** commits to merge up? |
| **3.0.x packaging** | When **3.0.x** is ready for **D11**, will **`core_version_requirement`** and **tagged releases** on Drupal.org **match** (so **beta** tags are not mistaken for **D11-ready** when `info.yml` still says **^10** only)? |

## Links

| Resource | URL |
|----------|-----|
| Project page | https://www.drupal.org/project/same_page_preview |
| Example fix commit (**#3461334**, UUID parameter) | https://git.drupalcode.org/project/same_page_preview/-/commit/ceac745c6c2c0997b25ea2f561d474647ef4e0bd |
| Issue **#3461334** | https://www.drupal.org/project/same_page_preview/issues/3461334 |
| `same_page_preview.info.yml` — tag **3.0.0-beta1** | https://git.drupalcode.org/project/same_page_preview/-/blob/3.0.0-beta1/same_page_preview.info.yml?ref_type=tags |

## Use

For **Drupal 11** upgrades and **contrib** dependency planning: confirm **which branch** carries **D11**, whether **release notes** and **`info.yml`** agree, and whether **3.0.x** contains **2.1.x** fixes before relying on a given tag. This file is **not** a Drupal.org issue template (see `issues/` for queue-ready drafts).
