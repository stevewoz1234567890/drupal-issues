# Note: Drupal.org docs vs new “AI tools” guides — **ai_best_practices** project

**Project:** [AI Best Practices for Drupal](https://www.drupal.org/project/ai_best_practices) (`ai_best_practices`)  
**Component:** Documentation / community coordination (adjust per queue)  
**Priority:** Normal

## Summary

When checking whether a **new AI-assisted development guide** would **duplicate** existing Drupal.org documentation, the landscape looks roughly like this:

- **Existing:** The handbook page [**Development tools overview**](https://www.drupal.org/docs/develop/development-tools/development-tools-overview) includes a **small** [**Artificial Intelligence Assistants**](https://www.drupal.org/docs/develop/development-tools/development-tools-overview#s-artificial-intelligence-assistants-ai-assistants) section (for example **Codeium**)—but there is **not** a full, end-to-end **guide to AI-assisted Drupal workflows** on Drupal.org at that level of scope.
- **New community home:** The [**AI Best Practices for Drupal**](https://www.drupal.org/project/ai_best_practices) project, created by [**webchick**](https://www.drupal.org/u/webchick), is building **Agent Skills** aimed at **Claude Code** and **OpenCode**, covering Drupal-specific patterns (for example **module** and **theme** work, **configuration management**, **hooks**, and **plugins**).

Anyone drafting a broad “how to use AI with Drupal” doc should **coordinate with that project** and **link** the handbook section above rather than re-inventing the same narrative in multiple places.

## Problem / opportunity

- **Duplication risk:** Multiple blog posts, chats, and one-off guides can diverge; a **single** curated place on Drupal.org helps contributors and reviewers.
- **Discoverability:** Handbook readers who only see the short “AI Assistants” blurb may not find **ai_best_practices** unless we **cross-link** explicitly.

## Proposed resolution

1. **Authors:** Before publishing a large new guide, open an issue on [**ai_best_practices**](https://www.drupal.org/project/ai_best_practices) (or offer a merge to its docs/skills) and summarize overlap with the Development tools overview.
2. **Handbook:** Optionally add one sentence under [**Development tools overview**](https://www.drupal.org/docs/develop/development-tools/development-tools-overview#s-artificial-intelligence-assistants-ai-assistants) → Artificial Intelligence Assistants pointing to **ai_best_practices** for **skills / agent workflows** (when the project’s content is ready—coordinate with maintainers).
3. **Keep scope honest:** The handbook blurb stays a **light** pointer; the project carries **deep** Drupal + agent patterns.

## References

- Screenshot / chat thread: “Drupal AI Best Practices / AI tools guide for Drupal development” — user asked an LLM to check for duplication; response summarized **overview page** scope vs **ai_best_practices**.
- Project: [drupal.org/project/ai_best_practices](https://www.drupal.org/project/ai_best_practices) — **webchick**, Agent Skills for **Claude Code** & **OpenCode**.
