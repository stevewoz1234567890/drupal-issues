# GitLab CI — `OPT_IN_…` variants manual by default (`#gitlab`, Apr 2026)

**Context:** A [**#gitlab** thread](https://drupal.slack.com/archives/CGKLP028K/p1776767636777989) (Apr 21, 2026) pointed to a merged **change record**: **non-`current`** pipeline **variants** (including names like **`OPT_IN_…`**) **default to manual** unless configured otherwise. The variant marked **`current`** **still runs automatically** on normal **push**/**MR** events, so the default green/red path for day-to-day work is **intended** to stay the same. **Rationale** from the thread: **CI** **runner** time is a **large** line item in the **Drupal Association** budget; **not** **fanning** **out** every optional **job** on every **push** **saves** **cycles** — maintainers are asked to **manually** **trigger** **broader** **matrices** when an **MR** is **close** to **merge** **(end** of **lifecycle** **coverage**)**.  

**Slack (canonical):** https://drupal.slack.com/archives/CGKLP028K/p1776767636777989  

## Use

- Optional jobs still show in the pipeline; **non-`current`** pipeline variants (including `OPT_IN_…` name patterns) do not auto-run by default.
- Update team onboarding and pre-merge checklists: manually start opt-in jobs when you need the full matrix before merge.
- For exact **job** / **variable** **names** and **the** **merged** **change** **record**, use the **#gitlab** thread and **`gitlab_templates`** on **the** **main** **branch** **(Apr** **2026** **)**.
