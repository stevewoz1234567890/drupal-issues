# Node not the bundle class in preprocess / route — unpublished content (community Slack)

**Context:** Drupal Slack thread about **`THEME_preprocess_node()`**, **`$variables['node']`**, **`hook_entity_bundle_info_alter()`**, and whether `\Drupal::routeMatch()->getParameter('node')` still returns the **bundle-specific** entity class.

## Thread (paraphrased)

- **Opening (sime):** Is it possible that code no longer gets the **bundle class** from `\Drupal::routeMatch()->getParameter('node')`?

- **sime:** The problem is more general — in **`function THEME_preprocess_node(&$variables)`**, **`$node = $variables['node']`** is **not** the bundle class anymore. **`hook_entity_bundle_info_alter()`** **is** running, **before** preprocess, and the class is set **the same as the documentation**.

- **darvanen:** **Name mismatch?** (hypothesis.)

- **sime:** It was **working code** they had not changed. They found the behavior only on **unpublished** content (rare on their site) and that the **bug was already present ~six months ago** — so **not** attributed to a **recent Drupal core** change.

## Practitioner takeaway

When **`$variables['node']`** or the route **`node`** parameter **does not** match expectations for a **bundle-specific** PHP class, verify whether the affected pages are **unpublished** nodes and whether that matches historical behavior on the site — before assuming a **core regression** or a misconfiguration of **`hook_entity_bundle_info_alter()`**.

## Use

**Triage note** for theme / entity-class debugging — **not** a Drupal.org issue template (see `issues/` for queue-ready drafts). Confirm with core and project issue queues if behavior should be documented or changed.
