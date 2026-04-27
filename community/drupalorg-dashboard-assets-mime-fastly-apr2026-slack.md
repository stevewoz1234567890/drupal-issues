# Drupal.org dashboard — static assets served as `text/html` (Fastly / WAF, Apr 2026)

**Context (Apr 21, 2026, from thread / screenshots):** The www.drupal.org user dashboard looked unstyled. jacobupal and rhovland saw aggregated CSS and JS under paths like `/files/advagg_css/…css` blocked by the browser: the MIME type was `text/html` (not `text/css`) with `X-Content-Type-Options: nosniff`, so the client refused to apply styles or run scripts. Many similar asset URLs failed the same way. A follow-on issue: header/branding images returned an HTML body with the same size signature as the broken CSS; in some cases the browser did not even attempt a normal image fetch.

## Infra response (drumm, thread)

- **Diagnosis in thread:** Maybe transient rollout (hitting the page before a browser interstitial), bad caching, or config — but reload did not fix for reporters, so it was not only “caught mid-enablement.”
- **Mitigation:** drumm shipped several **edge / WAF** rule updates in stages so static assets (CSS, JS, then images/fonts/icons) regained correct `Content-Type`. drumm noted that layering anti-abuse measures can lead to unexpected results, and that residential proxies in current attacks have gotten very good.
- **Verification:** rhovland confirmed after the last pass that fonts, SVG, JPEG, PNG, and ICO all looked correct. Some users still saw occasional Fastly re-challenge; drumm expected that to settle. jacobupal noted that with JavaScript off the site could not complete the challenge (expected); with JS on, assets looked good.

**Off-topic tail (same Slack):** Longer discussion of long-term viability of CDN-level bot defense, facet scraping on personal sites, and a link to [Drew DeVault — *Stop externalizing your costs on me*](https://drewdevault.com/blog/Stop-externalizing-your-costs-on-me/) for background (not DA policy).

## Use

- Triage “broken CSS on d.o”: inspect the actual response for `.css` / `.js` URLs (and images). If the body is HTML (challenge page, error, or WAF) while the path looks like a static file, treat it as an edge / WAF / anti-abuse issue, not only as AdvAgg or app misconfiguration.
- Related memos: [`drupalorg-cdn-timeout-redis-keys-apr2026-slack.md`](drupalorg-cdn-timeout-redis-keys-apr2026-slack.md), [`drupalorg-ddos-waf-git-mastodon-accounts-apr2026-slack.md`](drupalorg-ddos-waf-git-mastodon-accounts-apr2026-slack.md), [`drupalorg-429-fastly-rate-limit-apr2026-slack.md`](drupalorg-429-fastly-rate-limit-apr2026-slack.md); PerimeterX vs Fastly: [`../issues/12-drupal-org-perimeterx-challenge-browsers.md`](../issues/12-drupal-org-perimeterx-challenge-browsers.md).
