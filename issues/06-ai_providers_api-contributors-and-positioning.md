# Issue: Document positioning and invite contributors (simplicity, no black-box prompts)

**Project:** [AI Providers API](https://www.drupal.org/project/ai_providers_api)  
**Component:** Documentation / Community  
**Priority:** Normal

## Summary

The project aims for **simplicity** and hands **prompt building in full** to **integration authors**, without **black box** APIs—offering an alternative mental model to the **AI** package. It is intended as a **base module for integrations** with **no bundled sub-modules**. Development is **passion-driven with no budget**; maintainers welcome others who want to help.

## Problem / opportunity

Potential contributors and site builders may not discover:

- That integrations own prompts end-to-end (no opaque “magic” API surface).
- How this compares to **drupal/ai** for their use case.
- That the module is lean (base only, no required sub-modules) and that **volunteer help** is wanted.

## Proposed resolution

1. **README / project page:** Add a short “Why this module” section: explicit prompt ownership, contrast with black-box flows, pointer to **AI** package when users want that stack instead.
2. **Developer docs:** One page or README subsection for integration authors (hook points or plugin API, how prompts are assembled and passed through—whatever the code actually exposes).
3. **Contributing:** A “Get involved” blurb (issue queue, MR/Drupal.org workflow, non-code help welcome if applicable).
4. **Expectations:** Optionally one line that the initiative is unfunded so response times depend on volunteers—sets expectations without sounding apologetic.

## References

- Maintainer note (paraphrased): simplicity; full prompt building for integration authors; no black box APIs; alternative to the AI package; base module without sub-modules; passion-driven, zero budget; contact if interested in contributing.
