# Olivero — sticky menu toggle bound twice (no `Drupal.behaviors` in `navigation-utils.js`) (Slack)

**Context (Apr 2026):** A pro-bono site had two group-based sections, each with its own subtheme, both **Olivero** starterkit derivatives with only minor overrides. In one section the mobile menu worked; in the other the sticky header menu toggle’s click path ran twice (e.g. show then hide), so the menu stayed hidden when scrolled (pinned header behavior). The themer had not found a config diff between the two.

## Core theme (mherchel)

- [core `navigation-utils.js` (main)](https://git.drupalcode.org/project/drupal/-/blob/main/core/themes/olivero/js/navigation-utils.js) does not use `Drupal.behaviors`, so core Olivero does not idempotently guard against a second `attach` pass when the front-end pipeline re-runs (for example with **BigPipe** and related changes since the theme was first written in early D9).
- Suggested follow-up: open or find a **drupal** core issue to bind this logic with `Drupal.behaviors` and `once` (or equivalent) so listeners are not duplicated.

## Thread (simohell, ksenzee)

- Two very similar Olivero subthemes, one site section fine and one broken — the thread does not document a single smoking-gun difference (could be order of assets, group layout, block placement, cache/pipeline, etc.).
- **ksenzee** asked how the script works without an explicit “DOM ready” wait. **mherchel**: the library is included at the **bottom** of the page, so in the common case the header markup already exists when the IIFE runs — **fragile** for other embed or fragment contexts, not a general guarantee.

## Workaround (themer)

- Register the sticky header toggle **once**: e.g. a file/module-level flag, or `once` per element, before `addEventListener`. (Slack showed a one-off guard; any flag must live in the correct scope so a second script execution still sees it.)

## Use

- **Triage** “double toggle / menu always closed”: confirm duplicate listeners in DevTools; two identical `click` handlers on the same node point to re-executed or double-attached code without `behaviors`/`once`.
- **Durable** fix is in **core** Olivero (`navigation-utils.js` or a shared pattern), not only in a custom subtheme.
