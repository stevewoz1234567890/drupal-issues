# **gizmo** — Twig-templated C, per-function precompiled binaries (community note)

**Source:** [**symfonicat/gizmo**](https://github.com/symfonicat/gizmo) (GitHub)

## What it is

- **Twig** drives **templates for C source**, which is then **generated and compiled** into **binaries** tuned for a **specific function** on a **per-parameter** basis — a **precompute** / specialization pipeline rather than a single generic build.
- The author positions it as a **concept** (“precomputer” of compiled C), not a polished product line.

## Drupal-shaped idea (not a module; a prompt for contributors)

Someone with stronger **C / build-system** and **Drupal** extension experience could explore a bridge such as:

- **PHP `Reflection*`** over a **service method** or **pure function** (signature + doc intent) to derive a **stable description** of inputs/outputs.
- **Code generation**: emit **C** (or another compile target) from that description using the same **template** idea as **gizmo**, then **ship artifacts** (or build in CI) **per specialization** where hot paths justify it.

That would sit alongside normal **PHP** execution — useful only where **measurement** proves a win (I/O-bound Drupal requests rarely need custom native microkernels). Treat as **research / contrib experiment**, not core material.

## Use

Point people at **gizmo** when discussing **Twig beyond HTML**, **compile-time specialization**, or **“could Drupal ever…”** tooling — this file is **not** a Drupal.org issue template (see [`issues/`](../issues/) for those).
