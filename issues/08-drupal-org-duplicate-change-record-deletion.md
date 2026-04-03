# Issue: (Resolved in chat) Duplicate Change Record after form submit failure — staff removed dupe

**Project:** [Drupal.org](https://www.drupal.org/project/drupalorg) (documentation / webmasters / change record workflow—pick what fits)  
**Component:** Change records / editorial workflow (adjust to match taxonomy)  
**Priority:** Normal — *this specific duplicate was already handled; use as template or doc follow-up*

## Summary

A contributor accidentally created a **duplicate Change Record** after a **form submit failure** on Drupal.org. The duplicate node ([**3576782**](https://www.drupal.org/node/3576782)) was the extra copy; the **real** Change Record remained in the **published** state. They asked whether the duplicate could be **deleted** so it would not keep confusing them when browsing or searching.

**Outcome (Slack):** Drupal Association staff confirmed which node was the duplicate and **removed** it (“Done”).

## Problem

- Failed submits can leave authors unsure whether a Change Record was created; a second attempt may create a **duplicate**.
- Duplicates add noise in listings and search and can mislead future readers if not clearly marked or removed.
- It may not be obvious from the UI whether **self-service deletion** exists for Change Records or that **staff** can help.

## Proposed resolution (for a *new* filing, if you want product/docs work)

1. **Documentation (short):** On the Change Record creation or help path, add one line: if you suspect a duplicate after a failed submit, contact **support** or ask in **Drupal Slack** (appropriate channel) with links to the suspected duplicate and the **canonical published** node.
2. **Product (optional):** Explore idempotency or clearer post-submit confirmation to reduce duplicate creates after transient errors (separate, larger issue).

## References

- Duplicate node discussed: [node/3576782](https://www.drupal.org/node/3576782) (removed after confirmation; link may **404** or redirect—keep nid for historical search).
- Slack thread: reporter confirmed the linked node was the dupe; staff verified the real CR was published; staff completed removal.
