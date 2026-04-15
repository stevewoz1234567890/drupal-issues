# Drupal core — April 2026 security window (**SA-CORE-2026-001** … **-003**)

**Date (Security Team advisories):** 15 April 2026  
**Project:** [Drupal core](https://www.drupal.org/project/drupal)  
**Risk scale (how Drupal scores advisories):** [Security risk levels](https://www.drupal.org/security-team/risk-levels)

## Advisories (read the canonical pages)

| ID | Severity (d.o) | Topic | Official page |
|----|----------------|-------|---------------|
| **SA-CORE-2026-001** | **Critical** | **Cross-site scripting (XSS)** — insufficient handling of user-influenced data on **AJAX modal / dialog** button options (`OpenDialogCommand`); mitigated by **restricting allowed button keys** and **filtering string values** before the command is rendered. | [SA-CORE-2026-001](https://www.drupal.org/sa-core-2026-001) |
| **SA-CORE-2026-002** | **Moderately critical** | **Gadget chain / unsafe deserialization hardening** — tightens **`ViewExecutable` unserialization** (expected shape of serialized state) and **`Attribute::__toString()`** so non-attribute values cannot be rendered through that path. Exploitability is framed as **chaining** with **other** weaknesses (see advisory text). | [SA-CORE-2026-002](https://www.drupal.org/sa-core-2026-002) |
| **SA-CORE-2026-003** | **Moderately critical** | **Stored XSS** — **CKEditor 5** “complete entity suggestions” for internal links (feature in **Drupal 11.3+**): suggestion **labels** were not escaped for use in JSON/HTML contexts; fixed by escaping the entity **label** in **`EntityLinkSuggestionsController`**. | [SA-CORE-2026-003](https://www.drupal.org/sa-core-2026-003) |

Authentication / complexity nuances (anonymous vs admin vs authenticated) belong in each advisory’s risk breakdown—**do not rely on this table alone** for severity.

## Patched core versions (same security release batch)

These tags exist on the **[drupal/drupal](https://github.com/drupal/drupal)** mirror and correspond to the **15 April 2026** security releases:

- **10.5.9**, **10.6.7**, **11.2.11**, **11.3.7**

**Branch reality:** **SA-CORE-2026-003** touches code that exists on the **11.3** line (CKEditor 5 entity link suggestions); older supported branches still pick up **-001** and **-002** in their own tags—confirm **affected / fixed version lists** on each SA page and on **[Drupal core releases](https://www.drupal.org/project/drupal/releases)**.

## Use

Paste into **Slack**, **status/incident** notes, or **customer comms** when you need a **single memo** pointing at the three advisories and the **Composer / tarball** upgrade targets—this file is **not** a Drupal.org issue template (see [`issues/`](../issues/) for those). For **CVE IDs** and **CVSS**, use the **published advisory** and your **scanner vendor** once they have caught up.
