# **node_revision_delete** — missing `verbose_log` on upgrade, [#3586636](https://www.drupal.org/project/node_revision_delete/issues/3586636) (Slack)

**Context:** **alexpott** hit a **fatal** / **TypeError** in **node_revision_delete** tests after updating the module. **berdir** traced it to `node_revision_delete.settings:verbose_log` missing in saved config for sites updating from 8.x-1.x. The key was added in 2.x in [#3321626](https://www.drupal.org/project/node_revision_delete/issues/3321626) without a `hook_update_n()`, so `get('verbose_log')` is **null** where code expects a **boolean** (fails in update tests / upgrade paths first).

## Resolution (thread)

- **berdir:** For a patch release, **cast** to `(bool)` (or e.g. `?? false`) at the use site instead of immediately adding a config update hook—update hooks that rewrite config are a common source of follow-on bugs (pathauto was cited as precedent).
- **alexpott:** Shipped that minimal fix in **2.1.1**; may add a “proper” `hook_update_n()` in **2.2** because defaulting the key in config is still the **correct** long-term shape.

**Issue:** https://www.drupal.org/project/node_revision_delete/issues/3586636 (thread: **2.1.1** out with the cast fix).

## Use

- New config keys without `hook_update_n()` or schema defaults can break strict call sites on upgraded sites—guard reads in code and/or add updates deliberately.
- **Tests:** use config fixtures that omit new keys to mirror real upgrades.

**Related:** [`node_revision_delete-2.1.0-rc1-release.md`](node_revision_delete-2.1.0-rc1-release.md).
