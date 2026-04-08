# civicrm_entity — multilingual Views autocomplete (#3580224), maintainer review nudge (Slack)

**Context:** Short **Slack ping** asking **maintainers** for a **code review** on a **ready fix** for **multilingual CiviCRM** setups where **Views-based entity reference autocomplete** breaks (wrong column name for translated title fields).

## Message (paraphrased)

> Gentle nudge on **[#3580224](https://www.drupal.org/project/civicrm_entity/issues/3580224)** — **autocomplete** failing on **multilingual CiviCRM event** configurations.  
> The fix is implemented in **`QueryHooks.php`**. **GitLab MR [!11](https://git.drupalcode.org/project/civicrm_entity/-/merge_requests/11)** and **GitHub PR [#546](https://github.com/eileenmcnaughton/civicrm_entity/pull/546)** are both open. **[@markusa](https://www.drupal.org/u/markusa)** and **[@dsdeiz](https://www.drupal.org/u/dsdeiz)** have already been looped in — requesting a **maintainer review** when possible.

## Problem (from the issue)

On **multilingual** Drupal + **CiviCRM**, a **CiviCRM Event** entity reference using a **Views** reference plugin can throw an SQL error: the query still references **`civicrm_event.title`** while the select list uses a **language-specific** column (e.g. **`title_en_US`**), producing **“Unknown column 'civicrm_event.title'”** in the `WHERE` clause during autocomplete.

## Where to review

| Artifact | URL |
|----------|-----|
| **Drupal.org issue** | https://www.drupal.org/project/civicrm_entity/issues/3580224 |
| **GitLab merge request** !11 | https://git.drupalcode.org/project/civicrm_entity/-/merge_requests/11 |
| **GitHub pull request** #546 (`eileenmcnaughton/civicrm_entity`, target **4.0.x**) | https://github.com/eileenmcnaughton/civicrm_entity/pull/546 |

**Changed file (per MR/PR):** `civicrm_entity/src/Hook/QueryHooks.php`

## Use

**Reviewers** and **release managers** for **[civicrm_entity](https://www.drupal.org/project/civicrm_entity)** can use this note as a **single link bundle** for the **3580224** fix pipeline. Status of MR/PR may change after this note was written — **Drupal.org** and **GitLab** are the canonical review surfaces for Drupal contrib. This file is **not** a Drupal.org issue template (see `issues/` for queue-ready drafts).
