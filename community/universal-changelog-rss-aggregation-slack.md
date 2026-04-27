# “**Universal changelog**” — **RSS**, **emergent** issues, and **dead feeds** on rebuilds (Slack)

**Context:** A thread that started with a wish for a **universal** way to track **changelogs** and **emergent** problems turned into a practical exchange about **RSS** (still used widely), **aggregators** for **frontend** and **JS**, and a recurring **ops** problem: **sites** that **relaunch** on a **new stack** and **drop** or **break** **RSS** even when the **site** remains.

**Thread:** **“What I want is a universal changelog”**

## The “problem” (sime)

| Point | Note |
|-------|------|
| **Public forums** are **less** used for **emergent** / **new** issues | Harder to tell if a problem is **novel** or already discussed |
| **Web search** often surfaces **happy-path** **documentation** | Less signal on **edge** cases, regressions, or fresh breakage |
| **Ideal (half-joking):** **grep** across **“every changelog in the universe”** | “**Magically** want **everything**” — **Karl** asked for more than a **vague** “**solve my problems**” **pie in the sky** |
| **RSS** can feel like **another** **firehose** | **sime** — *“another source of anxiety”* — but **pipe** **all** feeds into **`grep`** and *“I'd be stoked”* |

## What **larowlan** said on **RSS**

| Message | Implication |
|---------|-------------|
| **[RSS 0.9 spec](https://cyber.harvard.edu/rss/rss.html)** (Harvard reference) + **“rss still going strong”** | **Format** is **durable**; still a **viable** **distribution** layer |
| **Rebrands** / **rewrites** (e.g. to a “**shiny new**” stack) often **lose** **RSS** that **WordPress** / **Drupal** (and older CMS) **exposed** | **“Forgot about RSS”** in the **migration** |
| **OPML** from a **feed reader** shows many **feeds** **dead** while **the site** is **still up** | **URL** or **enclosure** path **churn** without a **permanent** **redirect** to a new feed |
| **Still** uses **RSS** for **most** updates: good **blog** → **subscribe** → slowly feeling *“plugged in”* | **Human**-curated **serendipity** vs only **reactive** search |
| **Examples that still have feeds:** **Drupal.org**, **GitHub** **issues** (but **not** **releases** “**unfortunately**”) | **Partial** **machine-readable** **surfaces** per **platform** |

## Other **links** (thread)

| Resource | Who / note |
|----------|------------|
| [**bytes.dev**](https://bytes.dev/) | **darvanen** — **JS** **ecosystem**; “**useful, and entertaining**” |
| [**Frontend Focus**](https://frontendfoc.us/) (newsletter) | **larowlan** — “**good too**” — **another** **aggregator** (with [**bytes.dev**](https://bytes.dev/)-style curation) |

## Use

- **Wishes** for a **“universal changelog”** map to: **no** **single** **public** **place** for **emergent** **bugs** (forums/queues fragment), **search** **bias** toward **docs**, and **desire** for **mechanical** **diff** / **search** over **release** and **advisory** **streams** — **RSS**/**Atom** and **per-project** **feeds** are **incomplete** but **real** **building blocks**; **GitHub** **releases** as **feeds** was called out as a **gap** vs **issues**.
- **For** **relaunches:** **preserve** or **redirect** **old** `/feed`, `/rss`, and **`atom.xml`** patterns; **treat** **RSS** as **part** of the **URL contract** the way **sitemap** and **mailto** are.
