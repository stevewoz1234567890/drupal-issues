# Drupal core & contrib — child issues, `@see` spacing, autowire map, `contact_storage` (community thread)

**Context:** Informal Drupal chat (Slack-style). Names and handles as in the original messages. Multiple short threads from one capture.

## Child issues for [#3529510](https://www.drupal.org/project/drupal/issues/3529510)

A contributor asked whether they may **create child issues** for [**#3529510**](https://www.drupal.org/project/drupal/issues/3529510) **as indicated in comment #36’s grouping**.

- **smustgrave:** They’ll **set a reminder** to **follow up** if **no one answers** in **a few weeks**; please **refrain from starting** those child issues **for now**.
- **smustgrave:** **Thanks for asking** — they know the person is **looking for ways to help** and want it to stay **constructive**.

## `@see` spacing in Twig docblocks — [#3578091](https://www.drupal.org/project/drupal/issues/3578091)

**Problem (issue summary):** Some **Twig** template docblocks use **`@see`** **without a space** before the reference (e.g. `@see\Drupal\…`), which breaks **API module** parsing; the expected form is **`@see \Drupal\…`**.

- **Pierre Rudloff:** Could a **PHPCS** rule **enforce** the **space**? (Asked **everyone**; suggested a **follow-up issue** for a rule so the mistake **does not recur**.)
- **Sivaji Ganesh:** Clarified whether Pierre meant **other contributors** or **widening** the **current** issue’s scope.
- **longwave:** Core may already have **PHPCS** that bans wrong-case **`inheritDoc`** — **maybe** something **similar** could ban **`@see\`** (no space).
- **nicxvan:** New work often starts at [**coding_standards**](https://www.drupal.org/project/coding_standards), then a **follow-up** in [**coder**](https://www.drupal.org/project/coder); warned the process can feel **slow** even for **clear** changes.
- **quietone:** A **coding_standards** issue is **not required** for this **`@see`** problem — it is **already** covered in the **Twig coding standards**. See their comment on the issue: [**#3578091-16545898**](https://www.drupal.org/project/drupal/issues/3578091#comment-16545898).
- **quietone (on “slow”):** Many issues **stall** because they need an **MR**, **change record**, or similar — **not** because the **standards process** is inherently broken. The process aims to be **thorough**; improvements belong in **#coding_standards**. **Committee** members wear **many hats**; **quietone** had been **most available** but **family** needs and **COVID** cut their time (**still recovering**).
- **nicxvan:** **Apologized** — intent was **not** to **discourage**.
- **quietone:** **No worries**; understood.

## Autowire work — meta for forms, services, modules, controllers? — [#3578361](https://www.drupal.org/project/drupal/issues/3578361)

Someone asked whether [**#3578361**](https://www.drupal.org/project/drupal/issues/3578361) (*Autowire all forms*) has **siblings** or a **meta** for **controllers**, **services**, **tests**, etc.

- **nicxvan:** **Services:** [**#3295751**](https://www.drupal.org/project/drupal/issues/3295751) (*Autowire core services that do not require explicit configuration*). **Modules with explicit config:** [**#3578374**](https://www.drupal.org/project/drupal/issues/3578374). **Controllers:** **no** obvious grouped issue — search open core issues for **“Autowire”**: [filtered issue list](https://www.drupal.org/project/issues/drupal?text=Autowire&status=Open&priorities=All&categories=All&version=All&component=All).
- **smustgrave:** If there is **no** controller batch issue, it may make sense to **group controllers in one pass**; [**#3577774**](https://www.drupal.org/project/drupal/issues/3577774) was somewhat an **outlier** (**security**-fix context).
- **Sivaji Ganesh:** A **meta** that **lists related issues** would **help**.
- **smustgrave:** A **single hub** for the **list** **nicxvan** surfaced would be **useful**.

*Related repo note:* controller autowiring docs / change record context — [`issues/14-drupal-core-controller-autowiring.md`](../issues/14-drupal-core-controller-autowiring.md).

## `contact_storage` uninstall vs annotations — [#3039906](https://www.drupal.org/project/contact_storage/issues/3039906), [#3584151](https://www.drupal.org/project/contact_storage/issues/3584151)

- **Reporter (in thread):** Uninstall blocked ([**#3039906**](https://www.drupal.org/project/contact_storage/issues/3039906)); tests noisy around [**annotation → attributes**](https://www.drupal.org/node/3395575); inferred fix: **add Attributes** and **keep** annotations **too**.
- **nicxvan:** **CC** maintainer (**wrong John** first, then corrected); filed / pointed to [**#3584151**](https://www.drupal.org/project/contact_storage/issues/3584151) (*Add attributes for plugins*).
- **berdir:** **CI** shows **deprecations** when tests fail, but the **actual** failure is usually **above** that noise — e.g. **`ModuleUninstallValidatorException`**: field type still **in use** (**Options** email on **`contact_message.field_category`**).
- **nicxvan:** Fixing **deprecations** anyway to **surface** the **real** error more clearly.
- **berdir:** Agreed that motivation **makes sense**; wording **“tests fail due to annotation deprecation”** was **not accurate**.
- **berdir:** **Keeping annotations** alongside **attributes** is **fine**; **most** plugin **attributes** exist from **10.3+**, so **raising** the **minimum** could allow **cleanup** (**entity** types and **migrate** are common **exceptions**).

## Links (canonical)

| Topic | URL |
|--------|-----|
| Parent issue (child-issue question) | https://www.drupal.org/project/drupal/issues/3529510 |
| `@see` space / Twig docblocks | https://www.drupal.org/project/drupal/issues/3578091 |
| **quietone** comment (Twig standards already cover `@see`) | https://www.drupal.org/project/drupal/issues/3578091#comment-16545898 |
| **coding_standards** (process / proposals) | https://www.drupal.org/project/coding_standards |
| **coder** (sniffs) | https://www.drupal.org/project/coder |
| Autowire all forms | https://www.drupal.org/project/drupal/issues/3578361 |
| Autowire services (no explicit config) | https://www.drupal.org/project/drupal/issues/3295751 |
| Autowire module services (explicit `#[Autowire]`) | https://www.drupal.org/project/drupal/issues/3578374 |
| Core search: `Autowire` (open) | https://www.drupal.org/project/issues/drupal?text=Autowire&status=Open&priorities=All&categories=All&version=All&component=All |
| Controller autowire (chat: security-context outlier) | https://www.drupal.org/project/drupal/issues/3577774 |
| **contact_storage** uninstall | https://www.drupal.org/project/contact_storage/issues/3039906 |
| Plugin attributes change record | https://www.drupal.org/node/3395575 |
| **contact_storage** add plugin attributes | https://www.drupal.org/project/contact_storage/issues/3584151 |

## Use

**Citable paraphrases** for **core contribution etiquette** (wait on **child issues** when a maintainer asks), **`@see`** formatting (**Twig** standards vs extra **PHPCS**), **autowire** issue **landscape** and **meta** wish, and **`contact_storage`** triage (**uninstall validator** vs **deprecation** noise). Not a single Drupal.org issue template.
