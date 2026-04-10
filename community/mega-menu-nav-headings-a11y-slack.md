# Mega menu — headings (`h2`, `h3`) inside `<nav>` vs audits (community Slack)

**Context:** Drupal Slack thread about **mega menus** and whether **section headings** inside **navigation** should use real **`h2` / `h3`** elements or be avoided for accessibility tooling.

## Thread (paraphrased)

- **Opening:** Is it acceptable to use **`h2`**, **`h3`**, etc. for headings inside a mega menu — is that a problem?

- **philipnorton42:** It depends what else is on the page; as long as the **document follows a sensible `h1` → `h2` → `h3` order**, it should be fine — **semantic markup** matters.

- **rachel_norfolk:** Keep **one `h1`** on the page. An **audit** reported that there must be **no heading elements outside `<main>`** — that struck them as **wrong**. Follow-on: the advice they were given was to **remove the `h2`s and use styled `<div>`s** instead (harmful for semantics).

- **ekes:** **MDN** explicitly shows an **`h2` inside `<nav>`** in an example.

- **rachel_norfolk:** Confirmed the **MDN `<nav>` examples** (they had been looking at **MDN’s own live page source** earlier, not the reference examples).

## Practitioner takeaway

- **Real headings** for **visible labels** that structure groups of links are usually **better than `div` text** for users who rely on **headings navigation** and **semantics**.
- **Automated audits** and **vendor rules** that forbid **any** **`h*` outside `<main>`** are **not** a universal HTML requirement — **push back** with **spec / MDN** and **human review**.
- **Document-wide heading order** still needs to make sense alongside **`main`** (typically **one `h1`** for the primary page topic).

## Links

| Resource | URL |
|----------|-----|
| MDN — **`<nav>`** (examples include **`h2` in `<nav>`**) | https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/nav#examples |

## Use

**Triage note** for **mega menu** markup and **a11y audit** arguments — **not** a Drupal.org issue template (see `issues/` for queue-ready drafts). WCAG interpretation can still depend on **full page structure**; when in doubt, test with **assistive tech** and **user journeys**, not only **rule packs**.
