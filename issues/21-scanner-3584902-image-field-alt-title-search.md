# **scanner** [**#3584902**](https://www.drupal.org/project/scanner/issues/3584902) — search **image** field **Alt** / **Title**; **WIP**; possible reuse for **body** context in results

**Project:** [Scanner](https://www.drupal.org/project/scanner) (`scanner`)  
**Issue:** [**#3584902** — *Search through node's image fields*](https://www.drupal.org/project/scanner/issues/3584902)  
**Priority:** Normal (adjust on queue)

## Summary

**[Scanner](https://www.drupal.org/project/scanner)** finds and replaces strings across entity fields. **Image** fields expose **Alt** and **Title** text that editors care about, but those sub-properties are **not** covered by the same search paths as plain text fields today.

**Proposed resolution (issue):** Allow searching (and, by extension, replace flows where appropriate) through **image** field **alternative text** and **title** values.

**Queue metadata:** Remaining tasks / UI / API / data model sections on the issue should be filled as the approach stabilizes.

## Community note (Slack)

A contributor **recently active** on **scanner** opened this issue as **work in progress**. Even while **WIP**, the patch or approach may be **useful reference** for a related enhancement: surfacing a **summary** or **excerpt** of the **body** (or other rich fields) alongside matches—i.e. the same kind of “search deeper than the primary matched string” work may inform **result presentation**, not only **image** metadata.

Cross-link MRs and comments on [**#3584902**](https://www.drupal.org/project/scanner/issues/3584902) when stealing patterns for another issue.

## References

- Issue: https://www.drupal.org/project/scanner/issues/3584902  
- Project: https://www.drupal.org/project/scanner
