# **Workbench Moderation** → **Content Moderation** (core) — **8.x-2.x** path, **maintainer** note, **history** caveat (Slack)

**Context:** A **Drupal Slack** thread asked whether anyone had run a **Workbench Moderation** (**WBM**) **migration** to **core** **Content Moderation** (**CM**). **Maintainers** and **sponsors** weighed in on the **official** **upgrade** **branch**, **operational** **reality** on **legacy** **sites**, and **data** **model** **gotchas**.

**Thread:** *“Out of curiosity anyone ever done a workbench moderation migration to content moderation?”*

## Technical path (larowlan)

| Point | Detail |
|-------|--------|
| **8.x-2.x** **line** includes an **update** path from **WBM** **8.x-1.x** toward **Content Moderation** (historically **positioned** as the **bridge** when **CM** landed in **core**) | See [**workbench_moderation** **8.x-2.x-dev** release notes](https://www.drupal.org/project/workbench_moderation/releases/8.x-2.x-dev) |
| **May** need **refresh** for **current** **Drupal** (e.g. **11**) | **Verify** **update** **hooks** / **MRs** **before** **production** |
| **Works** *“ok-ish”* | **Downside:** **workflow** **machine** **name** can end up **randomly** **generated** — **plan** **exports**, **config** **depends**, and **integrations** that **key** on **workflow** **ID** |

> **Drupal.org** (**Jul 2016**, **8.x-2.x-dev**): *“The **8.x-2.x** release will then become an upgrade path from **WBM** **8.x-1.x** to **Content Moderation**.”* — **historical** copy only; **validate** on **current** **core**.

## People & intent

| Message | Who |
|---------|-----|
| **Keep** the **lights** on; open to **grant** **write** **access**; **one** **8.1**-era **WBM** **site** **left** — **decommissioning**; after that, **likely** **mark** [**workbench_moderation**](https://www.drupal.org/project/workbench_moderation) **abandoned** | **larowlan** |
| **Major** **lift** to **land** on **CM**; **stumbled** on the **2.x** **path** (a *“**gem**”*) while **setting** **up** [**scheduled_transitions**](https://www.drupal.org/project/scheduled_transitions) to **move** off **scheduled_updates** | **smustgrave** — may **co**-**maintain** if a **client** **drags** **feet**; **asked** **larowlan** for a **heads**-**up** when a **firm** **deadline** **(e.g.** **abandon**)** **exists** |
| **Original** **sponsor** / **author** of **WBM** — has **wanted** people **off** **WBM** **since** **CM** **shipped** in **core**; *“I approve this push”* | **agentrickard** |
| **IIRC** (years ago) **data** **model** **differences** could mean **losing** **some** **history**; *possibly* **one** **revision** with **multiple** **WBM** **transitions** **vs** **core** **CM** **shape** — **revalidate** for **current** code | **mstrelan** |

## Anecdote (planning / stakeholders)

- **Client** **timeline** **slip:** **~two** **years** into a **six**-**month** **migration**; **executive** **bought** another **vendor**’s **CMS** **story** without **mapping** **Drupal**’s **deep** **integrations** — **larowlan** (emoji aside). In **reply** to **smustgrave**’s **ask** for a **maintainer** / **abandon** **deadline:** *the deadline keeps moving* because **stakeholder** **plans** **shifted**.

## Use

- **Planning:** Treat **WBM** → **CM** as a **project**, not a **module** **toggle** — **workflow** **naming**, **config** **exports**, and **translation** / **scheduling** stacks (**scheduled_transitions**, legacy **scheduled_updates**) need **their** own **checklists**.
- **Risk:** If **mstrelan**’s **history** point **still** **applies** on a **site**, **run** a **rehearsal** **copy** and **compare** **revision** / **log** **tables** before **committing** a **cutover** **date**.
- **Ecosystem:** If **workbench_moderation** is **abandoned**, **document** **migration** **links** in **internal** **runbooks** and **favor** **core** **CM** for **new** **builds**.
