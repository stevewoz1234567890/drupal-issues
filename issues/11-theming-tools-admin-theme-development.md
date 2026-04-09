# Note: **theming_tools** — admin theme development helpers (non-production)

**Project:** [Theming Tools](https://www.drupal.org/project/theming_tools) (`theming_tools`)  
**Component:** Documentation / maintainer messaging (adjust per queue)  
**Priority:** Normal

## Summary

[**Theming Tools**](https://www.drupal.org/project/theming_tools) is described as a **suite of test modules** aimed at **Drupal admin theme** development. It is **not intended for production** use—think **local / dev** scaffolding and experiments when building or refactoring admin UIs.

Maintainer chat positions it as **especially useful** alongside:

- **Olivero** (prior art in the conversation).
- **default_admin** (experimental admin theme direction—**Gin**-lineage in spirit, with effort to **remove cruft** and improve **accessibility**).

There is **no Figma** baseline called out for **default_admin**, so expectations around “match the mock” tickets may stay looser than for some design-led initiatives. Separately, contributors discussed eventually applying the **accessibility “ONE”** framing **specifically to default_admin** once **accessibility issues are lined up**—with more room to experiment because the theme is **experimental**.

## Problem / opportunity

- **Expectations:** Newcomers may install **theming_tools** on a staging site without realizing it is **dev-oriented**; the project page and README should keep the **non-production** signal **visible** (for example near the top, consistent with maintainer guidance in community chat).
- **Discoverability:** People working on **default_admin** or **Claro**-adjacent admin UX may not know this project exists as a **sandbox** for theme work.

## Proposed resolution

1. **Project page / README:** Keep a clear **“not for production”** (or equivalent) callout; optionally add one line tying the suite to **admin theme** development and **Olivero** / **default_admin** as **related context** (without over-claiming roadmap ownership—verify with maintainers).
2. **Issue queue:** If users file “production bug” reports, triage with a short **template response** pointing at intended use.
3. **Handbook:** Only if maintainers agree—optional cross-link from admin-theming docs; otherwise **this repo’s index** remains the paraphrase.

## References

- Project: [drupal.org/project/theming_tools](https://www.drupal.org/project/theming_tools)
- Slack (paraphrase): **smustgrave** — not for production; **mherchel** — useful with **Olivero**, will be useful with **default_admin**; **default_admin** described as **Gin**-like with cruft removal and accessibility focus; **no Figma** for default_admin; **a11y “ONE”** may target **default_admin** when accessibility work is queued (**experimental** theme).
