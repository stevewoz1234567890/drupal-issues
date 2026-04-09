# Note: Where **`node_list`** / **`{entity_type_id}_list`** cache tags are invalidated (Drupal core)

**Project:** [Drupal core](https://www.drupal.org/project/drupal) — **developer reference** (Slack thread + links). Use for onboarding, docs, or debugging cache invalidation—not a default bug report unless you have a concrete regression.

**Component:** Entity / Cache API (if you turn this into a documentation issue)

## Summary

Grepping the codebase for the literal string **`node_list`** often **fails** because the tag is **built dynamically** as **`{entity_type_id}_list`** (and bundle-scoped variants such as **`node_list:article`**). **Invalidation** of entity-type **list** tags is wired through **entity save**: **`Drupal\Core\Entity\EntityBase::postSave()`** runs the **cache invalidation** path that includes **list** tags for the entity type (see **`EntityBase`** for the `Cache::invalidateTags()` / invalidator calls).

For **how** tags are named and exposed, use **`EntityTypeInterface`** / **`EntityType`**: **`getListCacheContexts()`**, **`getListCacheTags()`**, **`getBundleListCacheTags()`** (where applicable), and related helpers—rather than searching for a hard-coded **`node_list`** string.

## Details

| Topic | Pointer |
|--------|---------|
| **List tag invalidation on save** | **`EntityBase::postSave()`** — invalidates list tags for the entity type as part of save-side cache handling. |
| **Tag shape** | **`your_entity_type_id . '_list'`**; bundle-specific tags such as **`node_list:article`** when using bundle list tags. |
| **API surface** | **`EntityTypeInterface`** — list cache contexts/tags and bundle list cache tag helpers (**bundle list** helpers landed in newer **11.x**—check your branch’s interface). |

Line-number anchors in GitLab **drift** across releases; prefer opening **`EntityBase::postSave()`** on your branch. Historical Slack pointers: [around `postSave` in `EntityBase.php` on **11.x**](https://git.drupalcode.org/project/drupal/-/blob/11.x/core/lib/Drupal/Core/Entity/EntityBase.php) (e.g. **`#L429`** and **`#L484`** cited in chat—verify).

## Proposed resolution (if this becomes a docs issue)

1. **Handbook / API docs:** Add a short cross-link from cache tag documentation to **`EntityBase::postSave()`** and **`EntityType`** list-tag helpers so developers stop grepping for **`node_list`** alone.
2. **No core change** required for the behavior described above—this note records **where to look**.

## References

- Core: [`core/lib/Drupal/Core/Entity/EntityBase.php`](https://git.drupalcode.org/project/drupal/-/blob/11.x/core/lib/Drupal/Core/Entity/EntityBase.php) — **`postSave()`**.
- Core: [`core/lib/Drupal/Core/Entity/EntityType.php`](https://git.drupalcode.org/project/drupal/-/blob/11.x/core/lib/Drupal/Core/Entity/EntityType.php) / **`EntityTypeInterface`** — list cache contexts and tags.
- **Matt Glaman:** [Leveraging the list cache tag for entity types](https://mglaman.dev/blog/leveraging-list-cache-tag-entity-types), [Using bundle-specific list cache tags for entity types](https://mglaman.dev/blog/using-bundle-specific-list-cache-tag-entity-types).
- Slack (paraphrase): **sjpeters79** — search **entity save** / **cache invalidators**; **godotislate** — list tags invalidated from **`EntityBase::postSave()`**; **Mile23** — literal **`node_list`** search misses dynamic **`yourEntityHere_list`**; **penyaskito** — **`EntityType::getListCacheContexts`**, **`getBundleListCacheTags`**, etc.; **mglaman** — blog links above.
