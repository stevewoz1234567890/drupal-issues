# Core [**#3092424**](https://www.drupal.org/project/drupal/issues/3092424) — **ProxyBuilder** `@see` docblocks; fork missing **`main`**; clean **MR** via upstream sync + **rebase**

**Project:** [Drupal core](https://www.drupal.org/project/drupal) (`drupal`)  
**Issue:** [**#3092424** — *Drupal.orgProxyBuilder generates incorrect @see reference*](https://www.drupal.org/project/drupal/issues/3092424)  
**Priority:** Normal (adjust on queue)

## Summary (issue)

**`ProxyBuilder`** generated **`@see`** lines that point at a **blob URL without the class name**, producing **broken references** in many core and contrib **proxy** classes (example from the issue: [`ProxyBuilder.php` @ 8.8.0-alpha1](https://git.drupalcode.org/project/drupal/blob/8.8.0-alpha1/core/lib/Drupal/Component/ProxyBuilder/ProxyBuilder.php#L78)).

**Proposed resolution (issue):** Fix the reference generator, **regenerate** all **proxy** classes in core.

**Remaining tasks (issue queue):** Investigate **PHPStan** on the generated file **`core/lib/Drupal/Core/ProxyClass/File/MimeType/MimeTypeGuesser.php`** (noted in issue discussion).

## GitLab / fork problem (Slack)

Contributor could not open a **clean merge request**: the **existing branch** was **stale** / **broken**, and the **MR** showed **unwanted changes** from **other issues**. Creating a **new branch from `main`** failed with:

> **Failed to create branch** `3092424-ProxyBuilder-Main`: **invalid reference name `main`**

**Diagnosis (Sivaji Ganesh):** The **personal fork** had **no `main` branch** (or not the same refs as canonical), so GitLab could not use **`main`** as a base. Branches created from **`11.x`** could still drag **unrelated commits** if history on the fork diverged.

## Recommended workflow (**dimitriskr**, Slack)

1. **Push `main` from the canonical Drupal project to your fork** so the fork has a valid **`main`** ref that matches upstream (same idea if your integration branch is only **`11.x`**: ensure that ref exists on the fork and tracks upstream—see note below).
2. **Rebase** the **existing issue branch** onto **`main`** (or onto the correct upstream integration branch).
3. **Push** the **issue branch** and **refresh** the **MR** so the diff is scoped to this issue only.

### Local git sketch (adapt remotes / branch names)

Replace **`drupal`** with whatever you named the **canonical** remote and verify branch names with **`git ls-remote drupal`** (upstream may use **`main`**, **`11.x`**, or both).

```bash
git remote add drupal https://git.drupalcode.org/project/drupal.git   # once, if missing
git fetch drupal

# Populate fork on GitLab (example: push upstream main to origin main)
git push origin drupal/main:main

# On your issue branch
git checkout 3092424-ProxyBuilder-Main   # or your branch name
git rebase main                          # or: git rebase drupal/main
git push --force-with-lease origin HEAD
```

If canonical core does **not** use **`main`** as the default integration branch, use **`11.x`** (or the branch the issue targets) instead of **`main`** in both the **push** and **rebase** steps—**the point is to align the fork’s refs with `git.drupalcode.org/project/drupal`**, then **rebase** so the MR does not include stray commits.

## References

- Issue: https://www.drupal.org/project/drupal/issues/3092424  
- Slack: **Sivaji Ganesh** (fork / MR noise, no **`main`**); **dimitriskr** (push upstream **`main`**, **rebase**, **push**).
