# **node_revision_delete** **2.1.0-rc1** — maintainer FYI (Slack / release highlights)

**Release:** [node_revision_delete 2.1.0-rc1](https://www.drupal.org/project/node_revision_delete/releases/2.1.0-rc1)  
**Project:** [node_revision_delete](https://www.drupal.org/project/node_revision_delete)

## Summary (maintainer announcement)

People involved with **node_revision_delete** were pointed at a new **release candidate**: **more performant**, **more tests**, and **feedback welcome**.

## What shipped (highlights)

- **Multilingual / translation safety:** Revisions that are the **active revision for a translation** can **no longer be deleted accidentally**, reducing risk of **translation data loss** on multilingual sites.
- **Performance:** The **queue worker** and **batch** paths use **entity queries** instead of loading **full revision entities**, which **cuts memory and database load** on sites with **many** revisions.

## Use

Newsletters, Slack, upgrade notes, or “should we test this on staging?” threads—**not** a Drupal.org issue template (see [`issues/`](../issues/) for queue drafts).
