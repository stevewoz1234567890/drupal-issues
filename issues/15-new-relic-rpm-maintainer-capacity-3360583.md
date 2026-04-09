# Note: **new_relic_rpm** — release ask for [#3360583](https://www.drupal.org/project/new_relic_rpm/issues/3360583); maintainer capacity

**Project:** [New Relic RPM](https://www.drupal.org/project/new_relic_rpm) (`new_relic_rpm`)  
**Issue:** [Watchdog messages are not forwarding to New Relic](https://www.drupal.org/project/new_relic_rpm/issues/3360583) (**#3360583**, opened **May 2023**)

## Summary

A contributor asked whether someone could **commit and release** a fix for **#3360583** so it lands in a **stable** branch—the thread describes **Watchdog** / **dblog** messages not being forwarded to **New Relic** despite module settings and **`settings.php`** trials on **Acquia Cloud** with the **New Relic PHP** extension (deployments visible in New Relic, log forwarding not).

[**berdir**](https://www.drupal.org/u/berdir), listed **first** on the **maintainer** list, replied that their **last commit** to that project was in **2015**, they have **no** active project using **New Relic**, **no** practical way to **test** changes, and **no plans** to commit or cut releases for the project **in general**.

## Problem / opportunity

- **Expectations:** Names at the top of a **maintainers** list are often assumed to be an active **release** path; for thinly used **contrib**, that may not hold.
- **Gap:** **Observability** integrations need **runtime** validation (extension version, agent behavior, hosting constraints). Without a maintainer who runs the stack, **patches** can sit even when they look “simple.”
- **Paths forward:** **Co-maintainers** or **adopters** with **New Relic** in CI or staging; **sponsored** test environments; or **fork** / **replace** with a supported integration—coordinate on the issue queue rather than relying on a single historical maintainer.

## Proposed resolution (for the ecosystem, not a single patch)

1. **On [#3360583](https://www.drupal.org/project/new_relic_rpm/issues/3360583):** Offer **repro** steps, **PHP** / **NR** versions, and a **minimal** patch with tests if possible; ask for **review** from anyone using **New Relic** + **Drupal** in production.
2. **Project page:** If maintainers agree, clarify **support** expectations (archived vs seeking co-maintainers) so release asks are directed usefully.
3. **This file:** Encodes **chat context** so release requests are understood against **real maintainer capacity**.

## References

- Issue: [drupal.org/project/new_relic_rpm/issues/3360583](https://www.drupal.org/project/new_relic_rpm/issues/3360583).
- Slack (paraphrase): request to **commit and release** to **stable**; **berdir** — first on maintainer list but **last commit 2015**, **no New Relic** environment, **cannot test**, **no intention** to commit or release.
