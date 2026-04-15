# **ai_eval** — how we test AI agents in Drupal (community note)

**Project:** [AI Eval (`ai_eval`)](https://www.drupal.org/project/ai_eval) on Drupal.org  
**Narrative title (community writeup):** *How We Test AI Agents in Drupal*

## Why it matters

- The same question to a **Drupal AI agent** can return **different answers** on repeat runs.
- **System prompt** tweaks can **fix one scenario** and **break another** that used to pass.
- **Swapping models** often looks fine on the surface while **tool use and behaviour** shift materially.

## Summary (TL;DR from the writeup)

- **YAML datasets**, **pluggable graders**, and **quality gates in Drush** form the evaluation spine—repeatable runs instead of eyeballing chat transcripts.
- Early **tool-use benchmark** (community numbers): **four models**, **24** tool-use questions.
  - **Qwen 3 32B:** about **88%** pass rate at about **EUR 0.03** (as reported in the writeup).
  - **Sonnet:** about **89%** pass rate at about **EUR 4.00** — **partial run** (**9 / 24** questions) before credits ran out.
  - **Smaller models:** about **37%** of runs **silently skipped** expected **tool calls** (failure mode called out in the writeup: easy to miss without automated grading).

## Events

- **Drupal Developer Days Athens** — **Thursday / Friday** track: BoF **“Grading AI Agents: Live Testing with ai_eval.”** Bring an **agent config**; goal is to **draft eval questions** for it **live**.

## Use

Paste into **newsletters**, **Slack**, **event schedules**, or **forum** threads when you want a **short, citable** pointer to **agent evaluation in Drupal**—this file is **not** a Drupal.org issue template (see [`issues/`](../issues/) for those). Add a **permalink** to the full article once it has a stable public URL.
