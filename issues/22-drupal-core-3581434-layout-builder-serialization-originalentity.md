# Core [**#3581434**](https://www.drupal.org/project/drupal/issues/3581434) — **Layout Builder** + **content moderation**: **entity serialization** (**`originalEntity`**, **`serialize`**, **igbinary**)

**Project:** [Drupal core](https://www.drupal.org/project/drupal) (`drupal`)  
**Issue:** [**#3581434** — *Entity serialization issue in Layout Builder due to content moderation*](https://www.drupal.org/project/drupal/issues/3581434)  
**Priority:** Normal (adjust on queue)

## Summary

After upgrading **Drupal 10.5 → 11.3**, some sites hit **serialization** failures when **section storage** is stored to **layout temporary storage** in **`PrepareLayout::onPrepareLayout()`** (**Layout Builder**). Reported context: **large** entities (e.g. nodes with **many translations**, each with **its own layout**; **async** layouts)—in practice the payload can look **“too big”** to serialize **without** an obvious **memory limit** error. A further failure mode: the **resulting entity** can be **identical** to the **original**, which then **breaks** later **`serialize()`** calls (**fatal error**); **igbinary** can **segfault**. The **merge request** on the issue includes a **small test case**.

**Slack thread (with issue link):**

| Message | Who |
|---------|-----|
| **“I have not”** seen this before; **wouldn’t it be easier** to **`unset` the `originalEntity` property** in **`__serialize()`**? | **berdir** |
| **That would work**, but it means the **custom-built `originalEntity`** from **`ContentEntityStorageBase::createRevision()`** is **gone** | **webflo** |
| **Missed that.** Yes — **that would affect the runtime object** if it happens **during saving** | **berdir** |

## Proposed resolution (for issue queue / reviewers)

1. **Review** the **MR** + **test** on [**#3581434**](https://www.drupal.org/project/drupal/issues/3581434) with the above **tradeoff** in mind: **omitting `originalEntity`** from the **serialized** form **reduces** size / **identity** problems but may **remove** data **`createRevision()`** attached for **runtime** / **save**-path **behavior**.
2. **Confirm** **when** **temporary storage** serialization runs **relative to** **entity save** and **revision** handling so a fix does **not** **strip** **`originalEntity`** at the **wrong** **lifecycle** point.
3. Sites using **igbinary** for **cache** / **session** (if implicated): treat **segfaults** as **highest-severity** signals—collect **core** + **extension** **versions**, **repro** from the issue, and **avoid** ad hoc **`unset`**s without **core** guidance.

## References

- Issue: https://www.drupal.org/project/drupal/issues/3581434  
- Code touchpoint: `Drupal\layout_builder\EventSubscriber\PrepareLayout::onPrepareLayout()`  
- Related API: `\Drupal\Core\Entity\ContentEntityStorageBase::createRevision` (**`originalEntity`**)
