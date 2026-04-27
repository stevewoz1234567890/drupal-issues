# Load testing tools — k6, Goose (Slack)

**Context:** A contributor (smaz) wanted “easy to use” online load testing. They could use Azure and JMeter but wanted something simpler for defining scenarios, running tests, and reading reports; part of the workload would target a Drupal site, and they had not used this class of tool in a long time.

## Suggestions (thread)

- **k6** ([k6.io](https://k6.io/)) — **jbloomfield** pointed to k6, noting an open-source edition as well as Grafana k6 Cloud. They had not used the OSS build personally; at work they use the cloud product. smaz asked about the OSS k6 and local capacity at roughly tens of thousands of users/requests; they set that line of inquiry aside in-thread (“ignore that then”), so the thread does not record a concrete k6 capacity answer for that scale.
- **Goose** — **catch** recommended [tag1consulting/goose](https://github.com/tag1consulting/goose) as **100% FOSS** (Rust), [Locust](https://locust.io/)-inspired, with what they consider **excellent** HTML reports. They did **not** frame it as the easiest on-ramp (“from my $dayjob”) but highlighted reporting quality. Book: [Getting started — creating a test](https://book.goose.rs/getting-started/creating.html).

**Aside:** smaz on Goose’s tagline: *“Why Choose Goose? Have you ever been attacked by a goose?”*

## Use

- The only first-hand “hosted / easy” pointer in the thread was **Grafana k6 Cloud**; **OSS k6** is still a reasonable script-based line to compare with JMeter or Azure’s load products.
- For self-hosted, air-gapped, or zero-SaaS budget, **Goose** is a solid FOSS option with strong reports; expect more engineering setup than a guided SaaS wizards, not a direct “same ease as k6 Cloud” trade.
- **Drupal:** model like any stateful web app: cookies/sessions, form build IDs and tokens on POSTs, cache/CDN behavior on static assets, and any rate limits or bot/edge rules on the path under test.
- **Not in the thread (common alternatives):** Locust (Python), Artillery, Playwright or Cypress for journey smoke (not sustained load), Azure Load Testing if you are already in that stack.
