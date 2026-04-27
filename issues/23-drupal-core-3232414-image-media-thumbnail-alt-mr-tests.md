# Core [**#3232414**](https://www.drupal.org/project/drupal/issues/3232414) — **Image** **media** **thumbnail** **alt** out of sync with **source** **field**; **MR**, **tests**, **fork** **`main`**

**Project:** [Drupal core](https://www.drupal.org/project/drupal) (`drupal`)  
**Issue:** [**#3232414** — *Image Media thumbnail alt text cannot be changed without reuploading the image*](https://www.drupal.org/project/drupal/issues/3232414)  
**Priority:** Normal (adjust on queue)

## Summary

For **media** types whose **source** is an **image** (e.g. default **Image** type), **alt** (and related attributes) for the **source** **field** and for the **thumbnail** **base field** can live in **different** **database** **tables** while pointing at the **same** **file**. **Updating** **alt** on the **source** **without** **reuploading** the **file** may **not** **propagate** to the **thumbnail**, so **editing** **alt** in the **UI** appears **broken** for the **thumb**.

Contributors in **Slack** wanted a **small** **core** **fix** **soon**; the **favourite** **patch** **shape** in thread was a **minimal** **change** (e.g. a **tighter** **`if`**) with **no** **unrelated** **refactors**. **Reality check:** **d.o** **patch** **queues** are **not** a **substitute** for a **merge request** with **CI**—**KentR** and **greg-boggs** note **failing** **tests** / **no** **automated** **runs** on **raw** **patches** the way **reviewers** need; **patches** should **land** as **MRs**. **smustgrave**: **patches** **belong** in **MRs** for **review**; **suspect** the **open** **MR** may read like an **AI**-**generated** **solution**; **core** should have **(or** **extend**)** **tests** for **alt** **edit** **behavior**—often **a few** **asserts** on an **existing** **kernel** test.

| Topic | Who / note |
|--------|------------|
| **“More than review”** — **failing** **tests** | **KentR** (vs **comment** **#48** only) |
| **Convert** to **MR**; **earlier** **MR** **diff** **≠** what **actually** **fixed** the **bug** in **practice** | **greg-boggs** |
| **Two** **problems** **folded** into **one** **issue?**; **latest** **patch** **mostly** an **`if`** **change** | **greg-boggs** |
| **Validate** on **clean** **install**; **non**-**translation** **setups** | **greg-boggs** |
| **Workflow** **snags** opening a **second** **MR** / **branch** — **404**, **`invalid reference name 'main'`** on **fork**; **workaround:** **local** **branch** + **`git push`**, or ensure **fork** has **`main`** (see [`20-drupal-core-3092424-proxybuilder-fork-main-rebase.md`](20-drupal-core-3092424-proxybuilder-fork-main-rebase.md)) | **greg-boggs**, **KentR** |

**CI (thread):** after a **pushed** **approach**, **`MediaSourceTest`** still **failed** on **Thumbnail** — *“Item was not removed from the queue”* (**assertion** at **`MediaSourceTest.php`**: **~364**). **KentR** treated that as **Progress!** (a **concrete** **failing** **assertion** instead of **no** **test** **signal** from **patches** **alone**).

## Proposed resolution (for issue queue / MR authors)

1. **Single** **MR** with the **smallest** **correct** **fix** and **targeted** **test** **updates** (or **new** **asserts**) so **core** **fails** **before** the **patch** and **passes** **after**—**smustgrave** + **greg-boggs** **alignment**.
2. **Rationale** in the **issue** if the **bug** is **split** (e.g. **follow**-**up** **issue** for a **second** **root** **cause**).
3. **Fork** **hygiene** before using **GitLab** **“Create new branch**” (when an issue already has an MR) — see [`20-drupal-core-3092424-proxybuilder-fork-main-rebase.md`](20-drupal-core-3092424-proxybuilder-fork-main-rebase.md).

## References

- Issue: https://www.drupal.org/project/drupal/issues/3232414  
- **Kernel** test: `Drupal\Tests\media\Kernel\MediaSourceTest` (**Thumbnail**)

**Related in repo (image / alt elsewhere):** [**#3584902**](https://www.drupal.org/project/scanner/issues/3584902) **Scanner** and **search** on **image** **alt**/**title** — [`21-scanner-3584902-image-field-alt-title-search.md`](21-scanner-3584902-image-field-alt-title-search.md).
