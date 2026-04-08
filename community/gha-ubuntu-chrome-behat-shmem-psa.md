# GitHub Actions: Ubuntu runner update and Chrome / Behat failures (shared memory)

**Context:** Public service announcement from community chat (Alex Skrypnyk): **Chrome-based tests** (notably **Behat** with Chrome) may **fail suddenly** after GitHub Actions moved the **ubuntu-latest** (Ubuntu 24.04) runner image forward. The regression is tied to **how shared memory (`/dev/shm`) is handled**, alongside a **kernel** bump on the hosted image.

## What changed

| Runner image tag | Kernel (linux-azure) | Notes |
|------------------|----------------------|--------|
| [`ubuntu24/20260329.72`](https://github.com/actions/runner-images/releases/tag/ubuntu24/20260329.72) | `6.17.0-1008-azure` | Pre–April 6 baseline |
| [`ubuntu24/20260406.80`](https://github.com/actions/runner-images/releases/tag/ubuntu24/20260406.80) | `6.17.0-1010-azure` | Image associated with the reported breakage |

**Kernel package history (Ubuntu):** [linux-azure-6.17 changelog on Launchpad](https://launchpad.net/ubuntu/+source/linux-azure-6.17/+changelog)

Release announcements for those tags also note routine image updates (for example **Docker** / **Docker Compose** versions on a published schedule); the **practical symptom** called out here is **Chrome + Behat** instability linked to **`/dev/shm`** behavior on the newer stack.

## Scope

- **Affected:** Pipelines that run **Chrome** for end-to-end or browser tests (e.g. **Behat** with ChromeDriver / Selenium-style setups) on **GitHub-hosted** Ubuntu runners using the updated image.

## Workarounds

1. **Chrome flag (preferred for many projects)**  
   Add Chrome’s **`--disable-dev-shm-usage`** in your **Behat** / browser configuration (e.g. `behat.yml` or equivalent). That forces Chrome to use **`/tmp`** instead of **`/dev/shm`**, sidestepping the problematic shared-memory path on the runner.

2. **Pin the runner OS**  
   Pin the job to **`ubuntu-22.04`** (kernel **6.8.x** on the hosted image family), which **avoids** the **6.17.x** **azure** kernel path implicated in the PSA.

Choose based on whether you want a **minimal test-only change** (flag) vs **pinning the whole job** to an older runner label.

## Links

| Resource | URL |
|----------|-----|
| Runner image **20260329.72** (Ubuntu 24.04) | https://github.com/actions/runner-images/releases/tag/ubuntu24/20260329.72 |
| Runner image **20260406.80** (Ubuntu 24.04) | https://github.com/actions/runner-images/releases/tag/ubuntu24/20260406.80 |
| **linux-azure-6.17** source changelog | https://launchpad.net/ubuntu/+source/linux-azure-6.17/+changelog |

## Use

When **CI** starts failing **without application code changes**, and failures cluster around **headless Chrome** / **Behat**, check **runner image** and **kernel** drift first—then apply **`--disable-dev-shm-usage`** or **`ubuntu-22.04`** as appropriate. This file is **not** a Drupal.org issue template (see `issues/` for queue-ready drafts).
