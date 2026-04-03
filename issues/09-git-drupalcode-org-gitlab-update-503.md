# Note: 503 on git.drupalcode.org during planned GitLab maintenance

**Project:** [Drupal.org](https://www.drupal.org/project/drupalorg) / **infrastructure** (use only if filing a *status* or *comms* improvement—not a code bug)  
**Component:** GitLab / git.drupalcode.org (adjust to match taxonomy)  
**Priority:** Normal — *typically informational; see below*

## Summary

Users may see **503 Service Unavailable** with the message **“No server is available to handle this request.”** on **git.drupalcode.org** (for example on a merge request **Commits** tab such as  
`https://git.drupalcode.org/project/drupal/-/merge_requests/15332/commits`).

**Context (Slack):** Staff announced a **GitLab minor version update** (new features and **migrations**) with **planned downtime** that could be longer than the usual couple of minutes—**up to ~10 minutes**—as opposed to a typical short window.

**Internal reference:** [drupal-infrastructure Slack message](https://drupal.slack.com/archives/C51GNJG91/p1775153980583419) (channel **C51GNJG91**).

## Problem / distinction

- **503 during announced maintenance** is expected until the upgrade completes; retry after the window.
- If **503 persists** long after a published maintenance window ends, treat as a separate incident and report via usual **Drupal.org infrastructure** channels (Slack **#drupal-infrastructure**, **help@drupal.org**, etc.) with **time (UTC)**, **URL**, and **screenshot or response headers** if possible.

## Proposed resolution (optional doc follow-up)

1. **Status page / Slack:** Continue posting GitLab upgrade windows in **#drupal-infrastructure** (and any public status channel you use) with **expected duration** when migrations are involved.
2. **Contributor docs:** One line in GitLab contributor docs: during maintenance, **503** on **git.drupalcode.org** may appear; wait and retry.

## References

- Reported URL pattern: MR **commits** view on **git.drupalcode.org** (example path: `/project/drupal/-/merge_requests/15332/commits`).
- Staff note: minor GitLab update; downtime possibly **up to ~10 minutes**; [Slack link above](https://drupal.slack.com/archives/C51GNJG91/p1775153980583419).
