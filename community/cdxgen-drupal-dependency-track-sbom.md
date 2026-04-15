# **cdxgen** (CycloneDX) + **Drupal 10** + **Dependency-Track** — SBOM and “invalid schema” triage

**Audience:** Engineering / security / compliance (e.g. “Does our Drupal site work with CDX for Dependency-Track?”)  
**Tools:** [cdxgen](https://github.com/cdxgen/cdxgen) ([`@cyclonedx/cdxgen`](https://www.npmjs.com/package/@cyclonedx/cdxgen)), [Dependency-Track](https://dependencytrack.org/), CycloneDX JSON BOMs.

## Short answer

Yes, **cdxgen can produce an SBOM for a Composer-based Drupal site** by reading **`composer.json` / `composer.lock`** (PHP support is lockfile-driven). Run it from the **Composer project root** (the directory that contains those files—typically the same root as `web/index.php` in **drupal/recommended-project** layouts).

**“Invalid schema” on upload** is most often a **CycloneDX spec version mismatch**: current **cdxgen defaults to CycloneDX 1.6**, while many **Dependency-Track** deployments only fully accept **1.4** or **1.5** until upgraded. Align **`--spec-version`** with what your server supports, then re-validate locally before upload.

## Generate a BOM from a Drupal codebase

Prerequisites:

- A **checked-out** site with an up-to-date **`composer.lock`** (commit lockfiles in CI; run `composer install --no-dev` or include dev only if policy allows).
- Node **≥ 20** if you use the published npm package (cdxgen is **ESM**).

Example (recursive scan from project root, explicit spec for older Dependency-Track):

```bash
cd /path/to/drupal-project   # directory containing composer.json
npx --yes @cyclonedx/cdxgen@latest -r -o bom.json --spec-version 1.5 .
```

Adjust **`--spec-version`** to **`1.4`** if your Dependency-Track release predates solid **1.5** support; use **`1.5`** or **`1.6`** only if your server version documents support for that CycloneDX version.

**Tips:**

- Prefer scanning the **same tree** you deploy (profile **`require-dev`** vs production-only if IT only wants runtime deps).
- Custom code under **`web/modules/custom`** without Composer packages may appear only indirectly; the **main supply-chain signal** for Drupal is still **`composer.lock`** plus any other ecosystems you add (npm in themes, etc.—cdxgen can pick those up when manifest files exist).

## When Dependency-Track says “invalid schema”

Work in this order:

1. **Check CycloneDX version** in the BOM: top-level **`specVersion`** (e.g. `"1.6"`). If the server is older, regenerate with **`cdxgen --spec-version 1.4`** or **`1.5`**.
2. **Validate locally** with the official validator ([CycloneDX CLI](https://github.com/CycloneDX/cyclonedx-cli) or equivalent) so the error message is tool-native, not only the DT UI.
3. **Upgrade Dependency-Track** if policy allows—newer releases track newer CycloneDX specs (community threads often mention **1.5** / **1.6** support by server version).
4. **Duplicates / odd components:** some **cdxgen** releases have produced BOMs that fail validation for **duplicate** or **unusual component types**; if a known-good **spec version** still fails, try an **older cdxgen** patch release or inspect the BOM for duplicate **`bom-ref`** / component identity (see [cdxgen#1622](https://github.com/cdxgen/cdxgen/issues/1622)–class reports).

## What to tell IT / auditors

- **Standard:** CycloneDX JSON SBOM, generated from the **Composer lockfile** that defines Drupal core, contrib, and PHP libraries.
- **Provenance:** Document **cdxgen version**, **`--spec-version`**, and **Dependency-Track version** so schema support is explicit.
- **CI:** Run cdxgen on **tagged releases** or **main** with a **frozen lockfile**, attach **`bom.json`** as a build artifact, and **upload** (or use cdxgen’s **API submission** flow if you automate it—see cdxgen README for `submitBom` / server integration patterns).

## References

- **cdxgen:** https://github.com/cdxgen/cdxgen  
- **Default spec 1.6 and `--spec-version`:** cdxgen README (`--spec-version` defaults to **1.6**; override for **1.5** / **1.4**).  
- **Dependency-Track** + CycloneDX support: release notes / issues for your installed version (e.g. ingestion and schema support threads on [DependencyTrack/dependency-track](https://github.com/DependencyTrack/dependency-track/issues)).  
- **Validation:** [cyclonedx-cli](https://github.com/CycloneDX/cyclonedx-cli) `validate`.
