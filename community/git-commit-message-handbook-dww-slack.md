# Git commit message format — dww handbook (PSA, Apr 2026)

**Context:** In **`#gitlab`**, **dww** shared a **handbook** page meant as a **canonical** **reference** for the **“**new**”** **Drupal.org** **Git** **commit** **message** **format** (aligned with **Conventional** **Commits**-style **structure**; **summary** first line, **credits** as **trailers** **—** see **the** **page** for **the** **exact** **template** and **as**-**of** **dates** **including** **~Nov** **2025** **core** **adoption**).  

**Handbook:** https://www.drupal.org/docs/develop/git/git-for-drupal-project-maintainers/the-format-of-the-git-commit-message  

## Why the PSA matters

- Explains how **commit** text maps to the right issue when IDs or GitLab vs Drupal.org numbering diverge during migrations.
- Includes a **table** of **suggested** **commit** **type** **strings** **(type** in **Conventional** **style**).  
- **dww** **asked** for **edits** if anything is unclear **(Apr** **~22** **2026**).  

## Use

- **Everyone** **pushing** to **git.drupalcode.org** should **read** the page **(maintainers** **especially**)**.  
- **CI** and **automation** that parse **commit** messages: treat the page as the source of truth for trailers and issue linking.
