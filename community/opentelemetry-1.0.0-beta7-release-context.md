# OpenTelemetry Drupal — 1.0.0-beta7 release context (maintainer thread)

**Release:** [opentelemetry 1.0.0-beta7](https://www.drupal.org/project/opentelemetry/releases/1.0.0-beta7)

## What shipped

- **google/protobuf** updated from **3.x** to **4.x** (addresses advisory; see [GHSA-p2gh-cfq4-4wjc](https://github.com/advisories/GHSA-p2gh-cfq4-4wjc)); constraint **^4.33.6** where the fix exists.
- Other bug fixes and minor improvements.
- **Log format** may change; details in [drupal.org issue #3505594](https://www.drupal.org/project/opentelemetry/issues/3505594).

## Maintainer discussion (paraphrased)

- One maintainer **had planned** to tag a **new minor** mainly because of **logging-related** changes, but accepted shipping as the **current** pre-1.0 line given **beta** status and alignment with others.
- **Alexey Murz Korepov** had to **ship urgently** because [protobuf / pipeline blocker](https://www.drupal.org/project/opentelemetry/issues/3581743) was affecting **many CI pipelines**. On the **1.x** branch it was **hard to isolate** that fix from **other work already merged**.
- After **review**, other bundled changes were seen as **non-breaking**, so they **kept the same minor** version number while still in **beta**.

## Use

Context for release notes, upgrade planning (especially **log consumers**), and why version semantics looked like a tradeoff between semver intent and emergency unblock.
