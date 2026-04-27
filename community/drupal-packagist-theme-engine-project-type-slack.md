# Drupal Packagist — **Theme Engine** project type vs **module** (Slack)

**Context:** After shipping [**mjml_render_engine** `1.0.0-alpha1**](https://www.drupal.org/project/mjml_render_engine/releases/1.0.0-alpha1), **voleger** saw **no Composer package** on Drupal’s Packagist and asked whether **Theme Engine** projects flow to [**packages.drupal.org**](https://packages.drupal.org/) (or **Packagist.org**), and whether the project should be converted back to a **module**.

## Staff / maintainer guidance (from chat — **drumm**)

- **Theme Engine projects are not published** on **packages.drupal.org** **or** **Packagist.org**. A release under that **project type** will not generate the usual Drupal Packagist artifact—**not** a bug in your `composer.json` **metadata** alone in the sense of “fix the type string and it appears.”
- **Since Drupal 11.3**, theme engines are **implemented as services inside the module** (see core direction / change record [**#3547356**](https://www.drupal.org/node/3547356)). If the extension is **just a module** (and declares **`"type": "drupal-module"`** in **`composer.json`**), the **Drupal.org project type** should be **module**, not **theme engine**, so packaging matches reality.
- **Do not rely on Slack** for **project-type conversion**: open an issue on the [**infrastructure** project](https://www.drupal.org/project/infrastructure/) for **record-keeping** and any **follow-ups** / **side effects**.

## Example request (filed from this thread)

| Item | Detail |
|------|--------|
| **Issue** | [**infrastructure #3587236**](https://www.drupal.org/project/infrastructure/issues/3587236) — *Please change existing "Theme Engine project" to "Module project" for mjml_render_engine* |
| **Project** | [**mjml_render_engine**](https://www.drupal.org/project/mjml_render_engine) |
| **Rationale (reporter)** | Theme engines are not on Drupal Packagist; D11.3+ model aligns with publishing as a **module**. |

**nicxvan** (in thread) offered help with the **engine** implementation and noted **mjml_render_engine** is among the **few** projects using the **new** theme-engine-as-service system—useful context for contributors debugging **early adoption** friction.

## Use

**Maintainers** shipping **Composer-installable** Drupal code: if the **d.o project** is still classified as **Theme Engine** but the codebase is a **standard module** (especially post-**11.3** engine architecture), expect **no** **packages.drupal.org** entry until **staff** **reclassifies** the project—**request that via [infrastructure](https://www.drupal.org/project/infrastructure/issues)**. This memo does not replace **Drupal.org** documentation or **d.o** staff decisions on a given ticket.
