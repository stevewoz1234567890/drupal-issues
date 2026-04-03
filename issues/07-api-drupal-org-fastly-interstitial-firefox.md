# Issue: Fastly browser verification loop on api.drupal.org (Firefox; 401 on challenge POST)

**Project:** [Drupal.org](https://www.drupal.org/project/drupalorg) (or the appropriate infrastructure / web ops queue)  
**Component:** Infrastructure / CDN / api.drupal.org (adjust to match taxonomy)  
**Priority:** Normal

## Summary

Some users see a **“Fastly is verifying your browser”** interstitial on **api.drupal.org** that does not complete: the flow appears to **loop**, with a **401** on **POST** to a challenge URL such as `https://api.drupal.org/_fs-ch-.../pat?token=...`. **Google Chrome** on the same desktop may work; **Firefox** (including with extensions and Enhanced Tracking Protection **disabled**) can still reproduce. Staff noted a **DDoS mitigation–related change** around the same time that may be implicated.

## Problem

- **Symptom:** Interstitial does not settle; challenge POST returns **401**, blocking normal API/site use from affected clients.
- **Browsers / env:** Reported on **Firefox** (desktop); **Firefox Mobile** also observed by staff; **Chrome** on desktop reported **without** issues. **uBlock Origin**, **Privacy Badger**, and **Enhanced Tracking Protection** were ruled out as the sole cause when disabling them did not fix Firefox.
- **Related signal:** Separate reports of **5xx** on Drupal.org around a **load alert** window (timing correlated by staff in chat—not necessarily the same root cause as the Fastly challenge loop).

## Information useful for operators (from thread)

- **Contact:** **help@drupal.org** with a reference to the support thread; include **client IP** so staff can check server-side. DMs to individuals are discouraged (availability).
- **Artifacts:** **HAR** from Firefox Network tab (share privately if concerned about cookies); **full response headers** from the interstitial/challenge responses.
- **Cookies:** Interstitial should set cookie(s) named like **`_fs_ch_*`**; include whether those appear and persist as expected.

## Proposed resolution

1. **Operations / Fastly:** Review challenge configuration for **api.drupal.org** (and related properties) after recent mitigation changes; confirm **401** on `/_fs-ch-.../pat` is expected for failing clients or indicates a misconfiguration / client-class bug.
2. **Documentation:** If behavior is expected for certain clients, publish a short **status or FAQ** entry (or extend existing DDoS/mitigation comms) so contributors know whether to escalate vs wait.
3. **Follow-up:** If **5xx** spikes persist, treat as separate incident tracking unless root-caused to the same change.

## References

- Community Slack thread: Fastly verification loop, **401 POST** to `api.drupal.org/_fs-ch-.../pat`, Firefox vs Chrome, extension troubleshooting, **help@drupal.org** + IP/HAR/cookies **`_fs_ch_*`**, correlation with **load alert** and **5xx** for another reporter.
