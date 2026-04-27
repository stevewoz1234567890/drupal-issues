# **Chrome** extensions as **supply chain** risk — **JSON Formatter**, **Firefox**, **“Tab Tweaks”** (Slack + Pixelite)

**Context:** A [Pixelite article by **Sean Hamlin**](https://www.pixelite.co.nz/article/chrome-extensions-are-a-supply-chain-risk-build-your-own-instead/) (**21 Apr 2026**, tags: **chrome**, **security**, **claude-code**) argues that the **Chrome Web Store** model makes **extensions** a **supply chain** risk: **JSON Formatter** was noted as **injecting ads**; the author **replaced** it with a **self-built** extension in **under an hour** using **Claude**. A **Drupal Slack** thread tied that to **Firefox**’s **built-in** **JSON** UX, a general **app-store** pattern, and a **first-party** “**Tab Tweaks**” popup that now **replaces** **seven** prior extensions.

**Article (canonical):** https://www.pixelite.co.nz/article/chrome-extensions-are-a-supply-chain-risk-build-your-own-instead/

## What the thread added

| Point | Who / note |
|-------|------------|
| **Firefox** **out of the box** has strong **JSON** viewing and **filtering** (e.g. **jq**-like); *“god tier”* per colleague **Scott** | **wiifm** |
| Community often **bends** workflows to **avoid** using **Firefox** for tasks **Firefox already solves** (built-in **JSON** vs **store** extensions) | **Chat** (emoji aside) |
| *“Anytime you have an app store in an ecosystem”* — same **incentive** / **upgrade** / **abuse** dynamics generalize | **sime** |
| **One** custom extension (**Tab Tweaks**) now **replaced** **7** existing **extensions**; small **QOL** surface kept **growing**; *“surprised how easy it is”* | **wiifm** (popup: **Request Headers** e.g. **`Fastly-Debug`**: **`1`**, **Actions**, **YouTube Tweaks**, **Tab Reloader**, **JSON Formatter**) |

## Use

- **Triage** “**I need a JSON extension**” on **Chromium** against **product** **risk** (**ads**, **broad** **host permissions**); **Firefox**’s **viewer** is a **zero-install** **baseline** for **comparison**.
- **Security** **talks** with devs: **first-party** or **minimized**-permission **helpers** (article path + **AI-assisted** **scaffold**) can **shrink** **third-party** **surface** **area**.
- **Stores** (browser **extensions**, **mobile** **apps**): same **thread** as **sime**—**distribution** **concentration** + **update** **channel** = **recurring** **supply chain** **reviews** for **teams** that **block** on **it**.

**Related in repo:** **Fastly**-adjacent **debug** header **`Fastly-Debug: 1`** in the **Tab Tweaks** example overlaps **CDN** / **edge** **discussions** (e.g. [`../issues/07-api-drupal-org-fastly-interstitial-firefox.md`](../issues/07-api-drupal-org-fastly-interstitial-firefox.md))—not the same **problem**, but **shared** **tooling** for **verifying** **requests**.
